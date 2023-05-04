---
title: 在AEM Forms工作區中整合協力廠商應用程式
seo-title: Integrating third-party applications in AEM Forms workspace
description: 如何整合第三方應用程式，例如AEM Forms工作區中的通信管理。
seo-description: How-to integrate third-party apps like Correspondence Management in AEM Forms workspace.
uuid: 9649157c-fe28-43bf-a7d3-52ed55a0bf4f
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: f2bde2e8-da95-48ac-a652-85ead87f2cd3
exl-id: 4df9a16c-0853-4bbf-81bb-1856ab55c5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# 在AEM Forms工作區中整合協力廠商應用程式 {#integrating-third-party-applications-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Forms工作區支援管理表單和檔案的任務指派和完成活動。 這些表單和檔案可以是XDP Forms、Flex®表單，或已以XDP、PDF、HTML或Flex格式轉譯的指南（已淘汰）。

這些功能已進一步增強。 AEM Forms現在支援與支援類似AEM Forms工作區功能的協力廠商應用程式共同作業。 此功能的一個常見部分是任務分配和後續批准的工作流。 AEM Forms為AEM Forms企業使用者提供單一統一體驗，讓受支援應用程式的所有這類任務指派或核准都能透過AEM Forms工作區處理。

例如，我們將通信管理視為與AEM Forms工作區整合的候選範例。 通信管理的概念是「信函」，可轉譯並允許動作。

## 建立通信管理資產 {#create-correspondence-management-assets}

首先，建立在AEM Forms工作區中轉譯的範例通信管理範本。 如需詳細資訊，請參閱 [建立信函範本](/help/forms/using/create-letter.md).

在其URL存取通信管理範本，以驗證通信管理範本是否可成功轉譯。 URL的模式類似於 `https://[server]:[port]/lc/content/cm/createcorrespondence.html?cmLetterId=encodedLetterId&cmUseTestData=1&cmPreview=0;`

where `encodedLetterId` 是URL編碼的字母Id。 在Workbench中定義工作區任務的演算程式時，請指定相同的信函ID。

## 建立要在AEM Workspace中轉譯及提交信函的工作 {#create-a-task-to-render-and-submit-a-letter-in-aem-workspace}

執行這些步驟之前，請確定您是下列群組的成員：

* cm-agent-users
* 工作區使用者

如需詳細資訊，請參閱 [新增和設定使用者](/help/forms/using/admin-help/adding-configuring-users.md).

使用下列步驟建立要在AEM Workspace中轉譯及提交信函的任務：

1. 啟動Workbench。 以管理員身分登入localhost 。
1. 按一下「檔案」>「新建」>「應用程式」。 在「應用程式名稱」欄位中，輸入 `CMDemoSample` 然後按一下「完成」。
1. 選擇 `CMDemoSample/1.0` 並按一下滑鼠右鍵 `NewProcess`. 在名稱欄位中，輸入 `CMRenderer` 然後按一下「完成」。
1. 拖曳Start Point活動選擇器並加以設定：

   1. 在簡報資料中，選取使用CRX資產。

      ![useacrxasset](assets/useacrxasset.png)

   1. 瀏覽資產。 在「選擇表單資產」對話框中，「信函」頁簽列出伺服器上的所有信函。

      ![字母標籤](assets/lettertab.png)

   1. 選取適當的信函，然後按一下 **確定**.

1. 按一下管理動作設定檔。 此時將顯示管理操作配置檔案對話框。 確保正確選擇「渲染流程」和「提交流程」。
1. 要使用資料XML檔案開啟信函，請瀏覽並在準備資料處理中選擇適當的資料檔案。
1. 按一下「確定」。
1. 定義起始點輸出和任務附件的變數。 定義的變數將包含起始點輸出和任務附件資料。
1. （可選）若要在工作流程中新增其他使用者，請拖曳活動選擇器、進行設定，然後指派給使用者。 撰寫自訂包裝函式（如下所示）或下載並安裝DSC（如下所示）以擷取信函範本、起始點輸出和工作附件。

   自訂包裝函式範例如下：

   ```java
   public LetterInstanceInfo getLetterInstanceInfo(Document dataXML) throws Exception {
   try {
   if(dataXML == null)
   throw new Exception("dataXML is missing");
   
   CoreService coreService = getRemoteCoreService();
   if (coreService == null)
   throw new Exception("Unable to retrive service. Please verify connection details.");
   Map<String, Object> result = coreService.getLetterInstanceInfo(IOUtils.toString(dataXML.getInputStream(), "UTF-8"));
   LetterInstanceInfo letterInstanceInfo = new LetterInstanceInfo();
   
   List<Document> attachmentDocs = new ArrayList<Document>();
   List<byte[]> attachments = (List<byte[]>)result.get(CoreService.ATTACHMENT_KEY);
   if (attachments != null){
   for (byte[] attachment : attachments)
   { attachmentDocs.add(new Document(attachment)); }
   
   }
   letterInstanceInfo.setLetterAttachments(attachmentDocs);
   
   byte[] updateLayout = (byte[])result.get(CoreService.LAYOUT_TEMPLATE_KEY);
   if (updateLayout != null)
   { letterInstanceInfo.setLetterTemplate(new Document(updateLayout)); }
   
   else
   { throw new Exception("template bytes missing while getting Letter instance Info."); }
   
   return letterInstanceInfo;
   } catch (Exception e)
   { throw new Exception(e); }
   
   }
   ```

   [取得檔案](assets/dscsample.zip)
下載DSC:範例DSC可於 `DSCSample.zip` 檔案。 下載並解壓縮 `DSCSample.zip` 檔案。 使用DSC服務前，您需先加以設定。 如需詳細資訊，請參閱 [配置DSC服務](/help/forms/using/add-action-button-in-create-correspondence-ui.md#p-configure-the-dsc-service-p).

   在「定義活動」對話方塊中，選取適當的活動，例如getLetterInstanceInfo，然後按一下 **確定**.

1. 部署應用程式。 如果系統提示簽入並儲存資產。
1. 登入AEM Forms工作區，網址為 `https://[server]:[port]/lc/content/ws`.
1. 開啟您添加的任務，CMRenderer。 通信管理信函隨即出現。

   ![cminworkspace](assets/cminworkspace.png)

1. 填寫所需資料並提交信函。 窗口關閉。 在此過程中，任務將分配給步驟9中在工作流中指定的用戶。

   >[!NOTE]
   >
   >填入信函中所有必要的變數後，「提交」按鈕才會啟用。
