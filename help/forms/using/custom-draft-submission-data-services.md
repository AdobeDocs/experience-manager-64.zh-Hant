---
title: 自訂草稿和提交資料服務
seo-title: Customizing Draft and Submission data services
description: AEM Forms依預設會將草稿和提交的最適化表單儲存在「發佈」例項的預設節點中。 不過，您可以設定AEM Forms的草稿和提交資料服務，以自訂草稿和已提交最適化表單的儲存。
seo-description: AEM Forms, by default, stores draft and submitted adaptive forms in a default node on the Publish instance. However, you can configure the draft and submission data services of AEM Forms to customize the storage of draft and submitted adaptive forms.
uuid: c3ec1708-3b11-4142-93f0-1cffb6643f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 602fd6a9-9a65-411c-8475-a4082a3fdee0
exl-id: c6243a1f-8f8f-48dc-af3b-b165f451ce73
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 2%

---

# 自訂草稿和提交資料服務 {#customizing-draft-and-submission-data-services}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

AEM Forms可讓使用者將最適化表單儲存為草稿。 草稿功能可讓使用者選擇維護進行中表單。 然後，使用者可以隨時從任何裝置填妥並提交表單。

依預設，AEM Forms會儲存與發佈執行個體上草稿和提交相關聯的使用者資料，位於 `/content/forms/fp` 節點。

不過，AEM Forms入口網站元件提供的資料服務可讓您自訂為草稿和提交儲存使用者資料的實作。 例如，您可以將資料儲存在貴組織目前實作的資料存放區中。

若要自訂使用者資料的儲存，您必須實作 [草稿資料](/help/forms/using/custom-draft-submission-data-services.md#p-draft-data-service-p) 和 [提交資料](/help/forms/using/custom-draft-submission-data-services.md#p-submission-data-service-p) 服務。

## 必備條件 {#prerequisites}

* 啟用 [Forms入口網站元件](/help/forms/using/enabling-forms-portal-components.md)
* 建立 [表單入口網頁](/help/forms/using/creating-form-portal-page.md)
* 啟用 [forms portal適用性表單](/help/forms/using/draft-submission-component.md)
* 學習 [自訂儲存的實作詳細資訊](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## 草稿資料服務 {#draft-data-service}

若要自訂使用者草稿資料的儲存，您必須提供 `DraftAFDataService` 介面。

介面的下列程式碼範例中提供方法及其引數的說明：

```java
public interface DraftAFDataService {
 
 /**
  * Deletes the user data stored against the ID passed as the argument
  * 
  * @param draftDataID
  * @return status for the just occurred delete draft UserData operation 
  * @throws FormsPortalException
  */
 public Boolean deleteAFDraftUserData (String draftDataID) throws FormsPortalException;
 
 /**
  * Saves user data provided in the argument map
  * 
  * @param draftUserDataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID") in case of update
  * @return userData ID would be returned which needs to be saved in metadata node 
  * @throws FormsPortalException
  */
 public String saveAFUserData (Map<String, Object> draftUserDataMap) throws FormsPortalException;
 
 /**
  * Gets the user data stored against the ID passed as the argument
  * 
  * @param Draft DataID
  * @return guideState (which would then be populated in adaptive form to reload the draft) which is stored against draftDataID
  * @throws FormsPortalException
  */
 public byte[] getAFDraftUserData(String draftDataID) throws FormsPortalException;
 
 /**
  * Saves the attachments for current adaptive form instance 
  * 
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later)
  * @throws FormsPortalException
  */
 public String saveAttachments(byte[] attachmentBytes) throws FormsPortalException;
}
```

## 提交資料服務 {#submission-data-service}

若要自訂使用者提交資料的儲存，您必須提供 `SubmittedAFDataService` 介面。

介面的下列程式碼範例中提供方法及其引數的說明：

```java
public interface SubmittedAFDataService {
 
 /**
  * Submits the user data passed in argument map
  * 
  * @param submittedAFUserdataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID")
  * @return userData ID is returned that needs to be saved in the metadata node
  * @throws FormsPortalException
  */
 public String submitAFUserData (Map<String, Object> submittedAFUserdataMap) throws FormsPortalException;
 
 /**
  * Gets the user data stored against the ID passed as argument
  * 
  * @param submitDataID
  * @return guideState which would be used to open DOR
  * @throws FormsPortalException
  */
 public byte[] getSubmittedAFUSerData(String submitDataID) throws FormsPortalException;
 
 /**
  * Deletes user data stored against the ID passed as argument
  * 
  * @param Submit DataID
  * @return status of the delete operation on Submitted User data
  * @throws FormsPortalException
  */
 
 public Boolean deleteSubmittedAFUserData(String submitDataID) throws FormsPortalException;
 
 /**
  * Submits the attachment bytes passed as argument
  * 
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later) 
  * @throws FormsPortalException
  */
 public String submitAttachments(Object attachmentBytes) throws FormsPortalException;

}
```
