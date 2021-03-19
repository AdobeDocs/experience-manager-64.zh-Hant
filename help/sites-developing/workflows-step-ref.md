---
title: 工作流程步驟參考
seo-title: 工作流程步驟參考
description: 工作流程步驟參考
seo-description: 'null'
uuid: 72a64495-d1b1-49e7-8257-d6b2ed36961c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 25f0e0f7-9570-4748-81cb-ccec6492c0b4
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2833'
ht-degree: 2%

---


# 工作流程步驟參考{#workflow-step-reference}

工作流模型由各種類型的一系列步驟組成。 根據類型，這些步驟可以配置並擴展參數和指令碼，以提供所需的功能和控制。

>[!NOTE]
>
>本節介紹標準的「工作流」步驟。
>
>有關模組特定步驟，另請參閱：
>
>* [AEM Forms工作流程步驟參考](/help/forms/using/aem-forms-workflow-step-reference.md)
>* [使用媒體處理常式和工作流程處理資產](/help/assets/media-handlers.md)

>



## 步驟屬性 {#step-properties}

每個步驟元件都有一個&#x200B;**[!UICONTROL 步驟屬性]**&#x200B;對話框，用於定義和編輯所需屬性。

### 步驟屬性——公共頁籤{#step-properties-common-tab}

在屬性對話框的&#x200B;**[!UICONTROL Common]**&#x200B;頁籤上，大多數工作流步驟元件都可以使用以下屬性組合：

* **[!UICONTROL 標題]**

   步驟的標題。

* **[!UICONTROL 說明]**

   步驟的說明。

* **[!UICONTROL 工作流程分段]**

   將[舞台](/help/sites-developing/workflows.md#workflow-stages)套用至步驟的下拉式選擇器。

* **[!UICONTROL 逾時]**

   步驟將在此時段後「逾時」。

   您可以選擇：**[!UICONTROL Off]**、**[!UICONTROL Immediate]**、**[!UICONTROL 1h]**、**[!UICONTROL 6h]**、**[!UICONTROL 12h]**、**[!UICONTROL 24h]**。

* **[!UICONTROL 逾時處理常式]**

   當步驟逾時時，控制工作流程的處理程式；例如：

   `Auto Advancer`

* **[!UICONTROL 處理常式前進]**

   選擇此選項可自動將工作流推進到執行後的下一個步驟。 如果未選取，實施指令碼必須處理工作流程的進階。

#### 步驟屬性——用戶／組頁籤{#step-properties-user-group-tab}

屬性對話框的&#x200B;**[!UICONTROL User/Group]**&#x200B;頁籤上的許多工作流步驟元件可以使用以下屬性：

* **[!UICONTROL 透過電子郵件通知使用者]**

   * 當工作流程到達步驟時，您可以傳送電子郵件通知參與者。
   * 如果啟用，則會傳送電子郵件給&#x200B;**[!UICONTROL User/Group]**&#x200B;屬性所定義的使用者，或如果已定義群組，則傳送電子郵件給群組的每個成員。

* **[!UICONTROL 使用者/群組]**

   * 下拉式選取方塊可讓您導覽並選取使用者或群組。
   * 如果您將步驟指派給特定使用者，則只有此使用者可對步驟採取動作。
   * 如果您將步驟指派給整個群組，則當工作流程到達此步驟時，此群組中的所有使用者都會在其「工作流程收件匣」中執行動作。****
   * 如需詳細資訊，請參閱[參與工作流程](/help/sites-authoring/workflows-participating.md)。

## AND 拆分 {#and-split}

**[!UICONTROL AND Split]**&#x200B;會在工作流中建立拆分，之後兩個分支都將處於活動狀態。 您可以視需要將工作流程步驟新增至每個分支。 此步驟可讓您在工作流程中引入多個處理路徑。 例如，您可以允許同時執行某些審核步驟，以節省時間。

![wf-26](assets/wf-26.png)

### AND Split —— 配置{#and-split-configuration}

* 編輯&#x200B;**[!UICONTROL AND Split]**&#x200B;屬性：

   * **[!UICONTROL 拆分名稱]**:指定名稱以供說明。
   * 選擇所需的分支數；2、3、4或5。

* 視需要將工作流程步驟新增至分支。

   ![wf-27](assets/wf-27.png)

## 容器步驟 {#container-step}

**[!UICONTROL 容器]**&#x200B;步驟會啟動另一個以子工作流程執行的工作流程模型。

此&#x200B;**[!UICONTROL 容器]**&#x200B;可讓您重複使用工作流程模型，以實作一般的步驟順序。 例如，翻譯工作流程模型可用於多個編輯工作流程。

![wf-28](assets/wf-28.png)

### 容器步驟——設定{#container-step-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* **[!UICONTROL 容器]**

   * **[!UICONTROL 子工作流]**:選擇要啟動的工作流。

## 移至步驟 {#goto-step}

**[!UICONTROL 轉至步驟]**&#x200B;允許您根據ECMAScript的結果指定要執行的工作流模型中的下一個步驟：

* `true`:「轉 **[!UICONTROL 至步]** 驟完成」(Goto Stepcompletes)和工作流引擎執行指定步驟。

* `false`:Goto步 **[!UICONTROL 驟完]** 成和常規路由邏輯決定要執行的下一步。

**[!UICONTROL 轉至步驟]**&#x200B;可讓您在工作流模型中實施高級路由結構。 例如，要實施循環，可以定義&#x200B;**[!UICONTROL Goto步驟]**&#x200B;以在工作流中執行前一步驟，指令碼將評估循環條件。

### Goto Step - Configuration {#goto-step-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* **[!UICONTROL 程序]**

   * **[!UICONTROL 轉至]**:選擇要執行的步驟。
   * **[!UICONTROL 指令碼路徑]**:ECMAScript的路徑，用於確定是否執行 **[!UICONTROL Goto步驟]**。
   * **[!UICONTROL 指令碼]**:確定是否執行「轉至步驟」的ECMAScript ****。

>[!CAUTION]
>
>指定&#x200B;**[!UICONTROL 指令碼路徑]**&#x200B;或&#x200B;**[!UICONTROL 指令碼]**。 兩個選項不能同時使用。 如果您為這兩個屬性指定值，則步驟會使用&#x200B;**[!UICONTROL 指令碼路徑]**。

#### 模擬循環{#simulating-a-for-loop}

模擬for循環需要您保持已發生循環迭代次數的計數：

* 計數通常表示在工作流中操作的項的索引。
* 計數會評估為循環的退出准則。

例如，要實施對多個JCR節點執行操作的工作流，可以使用循環計數器作為節點的索引。 若要保存計數，請將`integer`值儲存在工作流程例項的資料地圖中。 使用&#x200B;**[!UICONTROL Goto Step]**&#x200B;的指令碼來增加計數，並比較計數與退出標準。

```
function check(){
   var count=0;
   var keyname="loopcount"
   try{
      if (workflowData.getMetaDataMap().containsKey(keyname)){ 
        log.info("goto script: found loopcount key");
        count= parseInt(workflowData.getMetaDataMap().get(keyname))+1;
      } 
 
     workflowData.getMetaDataMap().put(keyname,count);
 
     }catch(err) {
         log.info(err.message);
         return false;
    }
   if (parseInt(count) <7){
       return true;
   } else {
      return false;
   }
}
```

## OR 拆分 {#or-split}

**[!UICONTROL OR Split]**&#x200B;會在工作流中建立拆分，之後只有一個分支處於活動狀態。 此步驟可讓您將條件式處理路徑引入工作流程。 您可以視需要將工作流程步驟新增至每個分支。

>[!NOTE]
>
>有關建立OR分割的其他資訊，請參閱：[https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html](https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html)

![wf-29](assets/wf-29.png)

### OR Split —— 配置{#or-split-configuration}

* 編輯&#x200B;**[!UICONTROL OR Split]**&#x200B;屬性：

   * **[!UICONTROL 常見]**

      * 選擇所需的分支數；2、3、4或5。
   * **[!UICONTROL 分支： *x*>]**

      * **[!UICONTROL 指令碼路徑]**:包含指令碼的檔案的路徑。
      * **[!UICONTROL 指令碼]**:在方塊中新增指令碼。
      * **[!UICONTROL 預設路由]**:當多個分支評估為true時，會遵循預設分支。您只能指定一個分支作為預設值。

   >[!NOTE]
   >
   >每個分支都有一個單獨的頁籤：
   >
   >* 每個分支的指令碼一次評估一個。
   >* 分支由左至右計算。
   >* 會執行評估為true的第一個指令碼。
   >* 如果沒有分支評估為true，則工作流程不會前進。


   >[!CAUTION]
   >
   >指定&#x200B;**[!UICONTROL 指令碼路徑]**&#x200B;或&#x200B;**[!UICONTROL 指令碼]**。 兩個選項不能同時使用。 如果您為這兩個屬性指定值，則步驟會使用&#x200B;**[!UICONTROL 指令碼路徑]**。

   >[!NOTE]
   >
   >請參閱[定義OR分割的規則](/help/sites-developing/workflows-models.md#example-defining-a-rule-for-an-or-split)。

* 視需要將工作流程步驟新增至分支。

## 參與者步驟和選擇器{#participant-steps-and-choosers}

### 參與者步驟 {#participant-step}

**[!UICONTROL 參與者步驟]**&#x200B;可讓您為特定動作指派所有權。 只有當使用者已手動確認步驟時，工作流程才會繼續。 當您希望某人對工作流程採取動作時，就會使用此功能；例如，審核步驟。

雖然不直接相關，但在指派動作時必須考慮使用者授權；使用者必須擁有工作流程裝載之頁面的存取權。

#### 參與者步驟——配置{#participant-step-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* [**[!UICONTROL 使用者/群組]**](#step-properties-user-group-tab)

>[!NOTE]
>
>當出現以下情況時，始終會通知工作流啟動器：
>
>* 工作流程已完成（完成）。
>* 工作流被中止（終止）。

>



>[!NOTE]
>
>必須設定某些屬性，才能啟用電子郵件通知。 您也可以自訂電子郵件範本，或新增新語言的電子郵件範本。 請參閱[設定電子郵件通知](/help/sites-administering/notification.md)以設定中的電子郵件通知AEM。

### 對話方塊參與者步驟 {#dialog-participant-step}

使用&#x200B;**[!UICONTROL 對話參與者步驟]**&#x200B;從指派工作項目的使用者收集資訊。 此步驟對於收集稍後在工作流程中使用的少量資料非常有用。

完成步驟後，**[!UICONTROL 「完成工作項目」(Complete Work Item)]**&#x200B;對話框將包含您在對話框中定義的欄位。 在欄位中收集的資料會儲存在工作流程裝載的節點中。 隨後的工作流步驟可以從儲存庫讀取值。

要配置步驟，請指定要將工作項指定給的組或用戶，以及對話框的路徑。

#### 對話方塊參與者步驟——配置{#dialog-participant-step-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* [**[!UICONTROL 使用者/群組]**](#step-properties-user-group-tab)
* **[!UICONTROL 對話方塊]**

   * **[!UICONTROL 對話路徑**]:建立的[對話框的對話框節點的路徑。](#dialog-participant-step-creating-a-dialog)

#### 對話方塊參與者步驟——建立對話框{#dialog-participant-step-creating-a-dialog}

要建立對話框：

* 確定結果資料將儲存在裝載](#dialog-participant-step-storing-data-in-the-payload)中的位置。[
* [定義對話框；這包括定義用於收集（和儲存）資料的欄位](#dialog-participant-step-dialog-definition)。

#### 對話方塊參與者步驟——將資料儲存在裝載{#dialog-participant-step-storing-data-in-the-payload}

您可以將介面工具集資料儲存在工作流程裝載或工作項目中繼資料中。 介面工具集節點的`name`屬性格式決定資料的儲存位置。

* **[!UICONTROL 將資料與裝載一起儲存]**

   * 要將Widget資料儲存為工作流裝載的屬性，請對Widget節點的name屬性值使用以下格式：

      `./jcr:content/nodename`

   * 資料儲存在裝載節點的`nodename`屬性中。 如果節點不包含該屬性，則會建立該屬性。
   * 當與裝載一起儲存時，後續使用相同裝載的對話方塊會覆寫屬性的值。

* **[!UICONTROL 將資料與工作項目一起儲存]**

   * 要將Widget資料儲存為工作項目元資料的屬性，請對name屬性的值使用以下格式：

      `nodename`

   * 資料儲存在工作項`metadata`的`nodename`屬性中。 如果對話方塊隨後與相同的裝載搭配使用，則會保留資料。

#### 對話框參與者步驟——對話框定義{#dialog-participant-step-dialog-definition}

1. **[!UICONTROL 對話框結構]**

   「對話方塊參與者步驟」(Dialog Participant Steps)對話框與您為編寫元件而建立的對話框類似。 它們儲存在：

   `/apps/myapp/workflow/dialogs`

   標準觸控式UI的對話方塊具有下列節點結構：

   ```xml
   newComponent (cq:Component)
     |- cq:dialog (nt:unstructured)
       |- content 
         |- layout 
           |- items 
             |- column 
               |- items 
                 |- component0
                 |- component1
                 |- ...
   ```

   >[!NOTE]
   >
   >有關詳細資訊，請參閱[建立和配置對話框](/help/sites-developing/developing-components.md#creating-and-configuring-a-dialog)。

1. **[!UICONTROL 對話框路徑屬性]**

   **[!UICONTROL 對話參與者步驟]**&#x200B;具有&#x200B;**[!UICONTROL 對話路徑]**&#x200B;屬性（以及[參與者步驟](#participant-step)的屬性）。 **[!UICONTROL 對話路徑]**&#x200B;屬性的值是對話框`dialog`節點的路徑。

   例如，該對話框包含在儲存在節點中名為`EmailWatch`的元件中：

   `/apps/myapp/workflows/dialogs`

   對於啟用觸控的UI,**[!UICONTROL 對話路徑]**&#x200B;屬性會使用下列值：

   `/apps/myapp/workflow/dialogs/EmailWatch/cq:dialog`

   ![wf-30](assets/wf-30.png)

1. **示例對話框定義**

   以下XML代碼片段代表一個對話框，該對話框將`String`值儲存在裝載內容的`watchEmail`節點中。 標題節點表示[TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/textfield/index.html)元件：

   ```xml
   jcr:primaryType="nt:unstructured" 
       jcr:title="Watcher Email Address Dialog" 
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout jcr:primaryType="nt:unstructured" 
               margin="false" 
               sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
           />
           <items jcr:primaryType="nt:unstructured">
               <column jcr:primaryType="nt:unstructured"
                   sling:resourceType="granite/ui/components/foundation/container">
                   <items jcr:primaryType="nt:unstructured">
                       <title jcr:primaryType="nt:unstructured" 
                           fieldLabel="Notification Email Address" 
                           name="./jcr:content/watchEmails"
                           sling:resourceType="granite/ui/components/foundation/form/textfield"
                       />
                   </items>
               </column>
           </items>
       </content>
   </cq:dialog>
   ```

   此範例會在啟用觸控功能的UI中產生對話方塊，例如：

   ![chlimage_1-177](assets/chlimage_1-177.png)

### 動態參與者步驟 {#dynamic-participant-step}

**[!UICONTROL 動態參與者步驟]**&#x200B;元件與&#x200B;**[!UICONTROL 參與者步驟]**&#x200B;類似，其差異是在運行時自動選擇參與者。

要配置步驟，請選擇&#x200B;**[!UICONTROL 參與者選擇器]**，該選擇器標識要將工作項目分配給的參與者，以及對話框。

#### 動態參與者步驟——配置{#dynamic-participant-step-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* **[!UICONTROL 參與者選擇器]**

   * **[!UICONTROL 參與者選擇器]**:您建立的參 [與者選擇器名稱](#dynamic-participant-step-developing-the-participant-chooser)。
   * **[!UICONTROL 引數]**:任何必要引數。
   * **[!UICONTROL 電子郵件]**:是否應將電子郵件通知傳送給使用者。

* **[!UICONTROL 對話方塊]**

   * **[!UICONTROL 對話路徑]**:您所建立對話框的對話框節 [點的路徑(與「對話 **參與者步驟**」一樣)](#dialog-participant-step-creating-a-dialog)。

#### 動態參與者步驟——開發參與者選擇器{#dynamic-participant-step-developing-the-participant-chooser}

您會建立參與者選擇器。 因此，您可以使用任何選擇邏輯或標準。 例如，您的參與者選擇器可以選取工作項目最少的使用者（在群組內）。 您可以建立任意數量的參與者選擇器，以便用於工作流模型中&#x200B;**動態參與者步驟**&#x200B;元件的不同實例。

建立OSGi服務或ECMAScript，以選擇使用者將工作項目指派給。

* **[!UICONTROL ECMAscript]**

   指令碼必須包含名為getParticipant的函式，其會傳回使用者ID為`String`值。 將自訂指令碼儲存在`/apps/myapp/workflow/scripts`資料夾或子資料夾中。

   標準例項中包含範例指令AEM碼：

   `/libs/workflow/scripts/initiator-participant-chooser.ecma`

   >[!CAUTION]
   >
   >您&#x200B;*必須*&#x200B;不要變更`/libs`路徑中的任何項目。
   >
   >
   >這是因為下次升級實例時會覆寫`/libs`的內容（當您套用修補程式或功能套件時可能會覆寫）。

   此指令碼選擇工作流啟動器作為參與者：

   ```
   function getParticipant() {
       return workItem.getWorkflow().getInitiator();
   }
   ```

   >[!NOTE]
   >
   >**[!UICONTROL 工作流啟動器參與者選擇器]**&#x200B;元件擴展&#x200B;**[!UICONTROL 動態參與者步驟]**&#x200B;並使用此指令碼作為步驟實施。

* **[!UICONTROL OSGi服務]**

   服務必須實作[com.day.cq.workflow.exec.ParticipantStepChooser](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/ParticipantStepChooser.html)介面。 介面定義以下成員：

   * `SERVICE_PROPERTY_LABEL` 欄位：使用此欄位指定參與者選擇器的名稱。名稱會出現在&#x200B;**[!UICONTROL 動態參與者步驟]**&#x200B;屬性中的可用參與者選擇器清單中。
   * `getParticipant` 方法：將動態解析的承擔者ID返回 `String` 值。

   >[!CAUTION]
   >
   >`getParticipant`方法返回動態解析的承擔者ID。 這可以是群組ID或使用者ID。
   >
   >
   >但是，在返回參與者清單時，組ID只能用於&#x200B;**[!UICONTROL 參與者步驟]**。 對於&#x200B;**[!UICONTROL 動態參與者步驟]**，會傳回空白清單，這無法用於委派。

   若要將實作提供給&#x200B;**[!UICONTROL 動態參與者步驟]**&#x200B;元件，請將Java類別新增至匯出服務的OSGi套件，並將套件部署至伺AEM服器。

   >[!NOTE]
   >
   >**[!UICONTROL 隨機參與]** 者選擇是選擇隨機使用者( `com.day.cq.workflow.impl.process.RandomParticipantChooser`)的範例服務。**[!UICONTROL 隨機參與者選擇器]**&#x200B;步驟元件示例擴展&#x200B;**[!UICONTROL 動態參與者步驟]**&#x200B;並使用此服務作為步驟實施。

#### 動態參與者步驟——參與者選擇器服務示例{#dynamic-participant-step-example-participant-chooser-service}

以下Java類實現`ParticipantStepChooser`介面。 類返回啟動工作流的參與者的名稱。 程式碼使用的邏輯與範例指令碼(`initator-participant-chooser.ecma`)使用的邏輯相同。

`@Property`注釋將`SERVICE_PROPERTY_LABEL`欄位的值設定為`Workflow Initiator Participant Chooser`。

```java
package com.adobe.example;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.osgi.framework.Constants;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.adobe.granite.workflow.WorkflowException;
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.ParticipantStepChooser;
import com.adobe.granite.workflow.exec.WorkItem;
import com.adobe.granite.workflow.metadata.MetaDataMap;

@Component
@Service
@Properties({
        @Property(name = Constants.SERVICE_DESCRIPTION, value = "An example implementation of a dynamic participant chooser."),
        @Property(name = ParticipantStepChooser.SERVICE_PROPERTY_LABEL, value = "Workflow Initiator Participant Chooser (service)") })
public class InitiatorParticipantChooser implements ParticipantStepChooser {

 private Logger logger = LoggerFactory.getLogger(this.getClass());

 public String getParticipant(WorkItem arg0, WorkflowSession arg1,
   MetaDataMap arg2) throws WorkflowException {

  String initiator = arg0.getWorkflow().getInitiator();
  logger.info("Assigning Dynamic Participant Step work item to {}",initiator);

  return initiator;
 }
}
```

在&#x200B;**[!UICONTROL 動態參與者步驟]**&#x200B;屬性對話方塊中，**[!UICONTROL 參與者選擇器]**&#x200B;清單包含代表此服務的項目`Workflow Initiator Participant Chooser (script)`。

「啟動工作流模型時，日誌會指出啟動工作流的用戶的ID，以及分配了工作項的用戶。 在此示例中，`admin`用戶啟動了工作流。

`13.09.2015 15:48:53.037 *INFO* [10.176.129.223 [1347565733037] POST /etc/workflow/instances HTTP/1.1] com.adobe.example.InitiatorParticipantChooser Assigning Dynamic Participant Step work item to admin`

### 表單參與者步驟 {#form-participant-step}

**[!UICONTROL 表單參與者步驟]**&#x200B;在開啟工作項目時顯示表單。 當用戶填寫並提交表單時，欄位資料被儲存在工作流負載的節點中。

要配置步驟，請指定要將工作項目分配給的組或用戶，以及表單的路徑。

>[!CAUTION]
>
>本節介紹Foundation Components for Page Authoring的[Forms部分。](/help/sites-authoring/default-components-foundation.md#form)

#### 表單參與者步驟——配置{#form-participant-step-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* [**[!UICONTROL 使用者/群組]**](#step-properties-user-group-tab)
* **[!UICONTROL 表單]**

   * **[!UICONTROL 表單路徑]**:您建立的表 [單路徑](#form-participant-step-creating-the-form)。

#### 表單參與者步驟——建立表單{#form-participant-step-creating-the-form}

建立表單，以便正常使用&#x200B;**[!UICONTROL 表單參與者步驟]**。 但是，表單參與者步驟的表單必須具備下列組態：

* **[!UICONTROL Start of Form]**&#x200B;元件必須將&#x200B;**[!UICONTROL Action Type]**&#x200B;屬性設定為`Edit Workflow Controlled Resource(s)`。

* **[!UICONTROL Start of Form]**&#x200B;元件必須具有`Form Identifier`屬性的值。

* 表單元件必須將&#x200B;**元素名稱**&#x200B;屬性設定為儲存欄位資料的節點的路徑。 路徑必須在工作流裝載內容中找到節點。 值使用下列格式：

   `./jcr:content/path_to_node`

* 表單必須包含&#x200B;**[!UICONTROL Workflow Submit Button(s)]**&#x200B;元件。 不要配置元件的任何屬性。

工作流程的需求會決定您應將欄位資料儲存在何處。 例如，欄位資料可用來設定頁面內容的屬性。 **[!UICONTROL 元素名稱]**&#x200B;屬性的下列值將欄位資料儲存為`jcr:content`節點的`redirectTarget`屬性的值：

`./jcr:content/redirectTarget`

在以下示例中，欄位資料用作裝載頁上&#x200B;**[!UICONTROL Text]**&#x200B;元件的內容：

`./jcr:content/par/text_3/text`

&quot;第一個示例可用於`cq:Page`元件呈現的任何頁。 第二個範例僅在裝載頁面包含ID為`text_3`的&#x200B;**Text**&#x200B;元件時才可使用。

表單可以位於儲存庫的任意位置，但工作流用戶必須獲得讀取表單的授權。

### 隨機參與者選擇器 {#random-participant-chooser}

**[!UICONTROL 隨機參與者選擇器]**&#x200B;步驟是參與者選擇器，用於將生成的工作項目指派給從清單中隨機選擇的用戶。

![wf-31](assets/wf-31.png)

#### 隨機參與者選擇器——配置{#random-participant-chooser-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* **[!UICONTROL 引數]**

   * **[!UICONTROL 參與者]**:指定可供選擇的用戶清單。要將用戶添加到清單中，請按一下&#x200B;**[!UICONTROL 添加項目]** ，然後鍵入用戶節點或用戶ID的主路徑。 使用者的順序不會影響指派工作項目的可能性。

### 工作流程發起人參與者選擇器 {#workflow-initiator-participant-chooser}

**[!UICONTROL 工作流啟動器參與者選擇器]**&#x200B;步驟是參與者選擇器，用於將生成的工作項目分配給啟動工作流的用戶。 除了&#x200B;**[!UICONTROL Common]**&#x200B;屬性外，沒有其他屬性可進行配置。

#### 工作流啟動器參與者選擇器——配置{#workflow-initiator-participant-chooser-configuration}

若要設定步驟，請使用下列標籤進行編輯：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)

## 程序步驟 {#process-step}

**[!UICONTROL 處理步驟]**&#x200B;會執行ECMAScript或呼叫OSGi服務以執行自動處理。

![wf-32](assets/wf-32.png)

### 流程步驟——配置{#process-step-configuration}

若要設定步驟，請編輯並使用下列標籤：

* [**[!UICONTROL 常見]**](#step-properties-common-tab)
* **[!UICONTROL 程序]**

   * **[!UICONTROL 流程]**:要執行的進程實施。使用下拉式選單來選取ECMAScript或OSGi服務。 關於後述資訊：:

      * 標準的ECMAScript和OSGi服務，請參見[內置流程步驟](/help/sites-developing/workflows-process-ref.md)。
      * 為&#x200B;**[!UICONTROL Process]**&#x200B;步驟建立ECMAScript，請參閱[使用ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript)實施流程步驟。
      * 為&#x200B;**[!UICONTROL Process]**&#x200B;步驟建立OSGi服務，請參閱[使用Java類](/help/sites-developing/workflows-customizing-extending.md#implementing-a-process-step-with-a-java-class)實現流程步驟。
   * **[!UICONTROL 處理常式進階]**:選擇此選項可自動將工作流推進到執行後的下一個步驟。如果未選取，實施指令碼必須處理工作流程的進階。
   * **[!UICONTROL 引數]**:要傳遞給進程的參數。


