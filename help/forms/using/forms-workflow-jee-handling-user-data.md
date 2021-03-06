---
title: Forms JEE工作流程 |處理用戶資料
seo-title: Forms JEE工作流程 |處理用戶資料
description: AEM Forms JEE工作流程提供設計、建立和管理業務流程的工具。 了解更多如何訪問和刪除用戶資料、在工作流啟動器或參與者已知時識別進程實例ID、在用戶資料儲存在基元變數中時識別進程實例ID、根據進程實例ID從工作流實例中清除用戶資料，以及處理孤立任務。
seo-description: AEM Forms JEE工作流程提供設計、建立和管理業務流程的工具。 了解更多如何訪問和刪除用戶資料、在工作流啟動器或參與者已知時識別進程實例ID、在用戶資料儲存在基元變數中時識別進程實例ID、根據進程實例ID從工作流實例中清除用戶資料，以及處理孤立任務。
uuid: 3b06ef19-d3c4-411e-9530-2c5d2159b559
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5632a8df-a827-4e38-beaa-18b61c2208a3
role: Admin
exl-id: 8cbace00-c354-4f37-a781-04cadd441419
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 0%

---

# Forms JEE工作流程 |處理用戶資料 {#forms-jee-workflows-handling-user-data}

AEM Forms JEE工作流程提供設計、建立和管理業務流程的工具。 工作流進程由一系列按指定順序執行的步驟組成。 每個步驟都會執行特定動作，例如指派任務給使用者或傳送電子郵件訊息。 程式可與資產、使用者帳戶和服務互動，並可使用下列任何方法觸發：

* 從AEM Forms Workspace啟動程式
* 使用SOAP或RESTful服務
* 提交最適化表單
* 使用監看資料夾
* 使用電子郵件

如需建立AEM Forms JEE工作流程程式的詳細資訊，請參閱[Workbench說明](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/pdf/WorkbenchHelp.pdf)。

## 使用者資料和資料儲存 {#user-data-and-data-stores}

當進程被觸發並隨著進行，它將捕獲有關進程參與者的資料、參與者在與進程關聯的表單中輸入的資料以及添加到表單的附件。 資料會儲存在AEM Forms JEE伺服器資料庫中，若已設定，某些資料（例如附件）會儲存在全域檔案儲存(GDS)目錄中。 GDS目錄可在共用檔案系統或資料庫上配置。

## 存取和刪除使用者資料 {#access-and-delete-user-data}

觸發進程時，將生成唯一的進程實例ID和長期調用ID，並與進程實例關聯。 您可以根據長期調用ID訪問和刪除進程實例的資料。 您可以推斷已提交其任務的進程啟動器或進程參與者的用戶名的進程實例的長期調用ID。

但是，在以下情況下，您無法標識啟動器的進程實例ID:

* **透過已監看資料夾觸發的程式**:如果進程是由監視的資料夾觸發，則無法使用其啟動器來標識進程實例。在這種情況下，用戶資訊被編碼在儲存的資料中。
* **從發佈AEM例項啟動的程式**:從AEM發佈例項觸發的所有程式例項不會擷取啟動器的相關資訊。但是，用戶資料可以以與流程相關聯的形式捕獲，該過程儲存在工作流變數中。
* **通過電子郵件啟動的流程**:發件者的電子郵件ID在資料庫表的不透明blob列中被捕 `tb_job_instance` 獲為屬性，無法直接查詢。

### 在已知工作流啟動器或參與者時標識進程實例ID {#initiator-participant}

執行以下步驟來標識工作流啟動器或參與者的進程實例ID:

1. 在AEM Forms伺服器資料庫中執行以下命令，從`edcprincipalentity`資料庫表中檢索工作流啟動器或參與者的主ID。

   ```sql
   select id from edcprincipalentity where canonicalname='user_ID'
   ```

   查詢返回指定`user_ID`的主體ID。

1. （**對於工作流啟動器**）執行以下命令，從`tb_task`資料庫表中檢索與啟動器的主ID相關的所有任務。

   ```sql
   select * from tb_task where start_task = 1 and create_user_id= 'initiator_principal_id'
   ```

   查詢返回由指定的`initiator`_ `principal_id`啟動的任務。 任務分為兩種類型：

   * **已完成的任務**:已提交這些任務，並在欄位中顯示英數字 `process_instance_id` 元值。請記下所有提交任務的流程實例ID，並繼續執行步驟。
   * **已啟動但未完成的任務**:這些任務已啟動，但尚未提交。這些任務的`process_instance_id`欄位中的值為&#x200B;**0**（零）。 在這種情況下，請注意相應的任務ID，並參閱[使用孤立任務](#orphan)。

1. （**對於工作流參與者**）執行以下命令，從`tb_assignment`資料庫表中檢索與啟動器的進程參與者的主體ID相關聯的進程實例ID。

   ```sql
   select distinct a.process_instance_id from tb_assignment a join tb_queue q on a.queue_id = q.id where q.workflow_user_id='participant_principal_id'
   ```

   查詢返回與參與者關聯的所有進程的實例ID，包括參與者未提交任何任務的進程。

   請記下所有提交任務的流程實例ID，並繼續執行步驟。

   對於`process_instance_id`為0（零）的孤立任務或任務，請注意相應的任務ID，並參閱[使用孤立任務](#orphan)。

1. 按照[根據流程實例ID從工作流實例中清除用戶資料](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge)部分中的說明，刪除已標識的流程實例ID的用戶資料。

### 在原始變數中儲存使用者資料時識別程式例項ID {#primitive}

可以設計工作流，以便用戶資料被捕獲到變數中，該變數儲存為資料庫中的blob。 在這種情況下，只有當使用者資料儲存在下列原始類型變數之一時，才可以查詢該資料：

* **字串**:直接包含用戶ID或作為子字串，並可使用SQL查詢。
* **數值**:直接包含使用者ID。
* **XML**:在儲存為資料庫中文本列的文本內，將用戶ID作為子字串，可以像字串一樣查詢。

執行下列步驟以確定以基元類型變數儲存資料的工作流程是否包含使用者的資料：

1. 執行以下資料庫命令：

   ```sql
   select database_table from omd_object_type where name='pt_<app_name>/<workflow_name>'
   ```

   查詢返回指定應用程式(`app_name`)和工作流(`workflow_name`)的`tb_<number>`格式的表名。

   >[!NOTE]
   >
   >如果工作流嵌套在應用程式內的子資料夾中，`name`屬性的值可能會很複雜。 請確定您指定可從`omd_object_type`資料庫表獲取的工作流的確切完整路徑。

1. 查看`tb_<number>`表架構。 該表包含用於儲存指定工作流的用戶資料的變數。 表格中的變數對應至工作流程中的變數。

   識別並記下與包含使用者ID的工作流程變數相對應的變數。 如果識別的變數為基元類型，您可以執行查詢以判斷與使用者ID相關聯的工作流程例項。

1. 執行以下資料庫命令。 在此命令中，`user_var`是包含用戶ID的基元類型變數。

   ```sql
   select process_instance_id from <tb_name> where <user_var>=<user_ID>
   ```

   查詢返回與指定的`user_ID`關聯的所有進程實例ID。

1. 按照[根據流程實例ID從工作流實例中清除用戶資料](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge)部分中的說明，刪除已標識的流程實例ID的用戶資料。

### 根據流程實例ID從工作流實例中清除用戶資料 {#purge}

現在您已識別與使用者相關聯的處理例項ID，請執行下列動作，從個別的處理例項刪除使用者資料。

1. 執行以下命令，從`tb_process_instance`表檢索進程實例的長期調用ID和狀態。

   ```sql
   select long_lived_invocation_id, status from tb_process_instance where id='process_instance_id'
   ```

   查詢返回指定`process_instance_id`的長期調用ID和狀態。

1. 使用具有正確連接設定的`ServiceClientFactory`實例建立公用`ProcessManager`客戶端(`com.adobe.idp.workflow.client.ProcessManager`)的實例。

   有關詳細資訊，請參閱[類ProcessManager](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/com/adobe/idp/workflow/client/ProcessManager.html)的Java API參考。

1. 檢查工作流實例的狀態。 如果狀態不是2(COMPLETE)或4(TERMINATED)，請先呼叫以下方法以終止實例：

   `ProcessManager.terminateProcess(<long_lived_invocation_id>)`。

1. 呼叫下列方法以清除工作流程例項：

   `ProcessManager.purgeProcessInstance(<long_lived_invocation_id>)`

   `purgeProcessInstance`方法會從AEM Forms伺服器資料庫和GDS（如果已配置）中完全刪除指定調用ID的所有資料。

### 使用孤立任務 {#orphan}

孤立任務是指其包含進程已啟動但尚未提交的任務。 在這種情況下，`process_instance_id`是&#x200B;**0**（零）。 因此，您不能使用進程實例ID跟蹤為孤立任務儲存的用戶資料。 但是，您可以使用孤立任務的任務ID來跟蹤它。 如[當工作流啟動器或參與者為](/help/forms/using/forms-workflow-jee-handling-user-data.md#initiator-participant)時標識進程實例ID中所述，可以從`tb_task`表中標識用戶的任務ID。

擁有任務ID後，請執行以下操作，從GDS和資料庫中清除具有孤立任務的關聯檔案和資料。

1. 在AEM Forms伺服器資料庫上執行以下命令，以檢索所標識任務ID的ID。

   ```sql
   select id from tb_form_data where task_id=<task_id>
   ```

   查詢會傳回ID清單。 對於結果中傳回的每個ID(`fd_id`)，建立工作階段ID字串清單，如下所示：

   * _ `wfattach<task_id>`
   * `_wftask<fd_id>`
   * `_wftaskformid<fd_id>`

1. 根據GDS指向檔案系統還是資料庫，執行以下步驟之一：

   1. **檔案系統中的GDS**

      在GDS檔案系統中：

      1. 搜尋副檔名為以下工作階段ID字串的檔案：
      * `_wfattach<task_id>`
      * `_wftask<fd_id>`
      * `_wftaskformid<fd_id>`

         具有這些副檔名的檔案是標籤檔案。 檔案名稱會以下列格式儲存：

         `<file_name_guid>.session<session_id_string>`
      1. 從檔案系統中刪除檔案名完全為`<file_name_guid>`的所有標籤檔案和其他檔案。
   1. **資料庫中的GDS**

      對每個會話ID執行以下命令：

      ```sql
      delete from tb_dm_chunk where documentid in (select documentid from tb_dm_session_reference where sessionid=<session_id>)
      delete from tb_dm_session_reference where sessionid=<session_id>
      delete from tb_dm_deletion where sessionid=<session_id>
      ```




1. 執行以下命令以從AEM Forms伺服器資料庫中刪除任務ID的資料：

   ```sql
   delete from tb_task_acl where task_id=<task_id>
   delete from tb_task_attachment where task_id=<task_id>
   delete from tb_form_data where task_id=<task_id>
   delete from tb_assignment where task_id=<task_id>
   delete from tb_task where id=<task_id>
   ```
