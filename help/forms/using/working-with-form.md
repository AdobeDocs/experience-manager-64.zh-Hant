---
title: 使用表單
seo-title: Working with a Form
description: 檢視並更新AEM Forms應用程式中與任務或起始點相關聯的表單
seo-description: View and update the form associated with a task or Startpoint in the AEM Forms app
uuid: 7481ca5c-a2c0-4697-9008-1e51bce2012e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 8a5e038e-b39a-41de-88a0-47642e5bd5bf
exl-id: ae565dbd-2631-4364-89f7-675700b43320
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---

# 使用表單 {#working-with-a-form}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

如果表單已啟用於表單應用程式中同步，表單即會下載，您可以直接使用。

表單會下載到您的應用程式中，且可離線使用。 例如，您經營的是銀行，而客戶填寫了您網站上的應用程式。 此應用程式是最適化表單，可接受客戶提供的資訊並儲存以供審核。 管理員會檢閱表單，並在AEM製作例項中建立驗證表單。 管理員可啟用表單與AEM Forms應用程式的同步。 如果驗證表單可在AEM Forms應用程式中使用，您的現場代理可以使用行動裝置驗證客戶的詳細資訊。 行動裝置與伺服器同步，驗證表單會載入應用程式中。 您的現場代理可以訪問客戶、驗證詳細資訊、將資料另存為草稿或提交驗證表。 每次應用程式上線時，表單都會與伺服器同步。

若要在AEM Forms應用程式中同步表單：

1. 在製作例項中，選取表單，然後按一下 **檢視屬性**.

1. 在屬性頁面中，按一下 **進階。**
1. 在「進階」下，啟用選項： **與AEM Forms應用程式同步**，然後點選 **儲存**.

若要同步多個表單，請在製作執行個體中，在forms manager中選取多個表單，然後點選 **與AEM Forms應用程式同步**. 表單發佈後，AEM Forms應用程式可連線至發佈伺服器並擷取表單。

>[!NOTE]
>
>支援的表單：
>
>* 適用性表單（不延遲載入）
>* 行動表單
>
>與AEM Forms OSGi伺服器同步的AEM Forms應用程式中擷取的適用性表單中，不支援表單層級附件。 如果作者在編寫表單時已啟用欄位層級附件，則使用者可以在欄位中附加檔案。

**開啟和更新表單**

1. 若要開啟表單，請點選主畫面中的表單。
1. 您可以更新表單的欄位、新增附件、另存為草稿及提交。
