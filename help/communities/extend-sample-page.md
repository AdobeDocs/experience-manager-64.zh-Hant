---
title: 將注釋添加到示例頁
seo-title: Add Comment to Sample Page
description: 將自訂備注新增至頁面
seo-description: Add Custom Comments to a page
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 1%

---

# 將注釋添加到示例頁 {#add-comment-to-sample-page}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

現在，自定義注釋系統的元件已位於應用程式目錄(/app)中，因此可以使用擴展元件。 要受影響的網站中評論系統的例項必須將其resourceType設定為自訂評論系統，並包含所有必要的用戶端程式庫。

## 識別所需的Clientlib {#identify-required-clientlibs}

對於擴展注釋，也需要預設注釋的樣式和功能所需的客戶端庫。

此 [社群元件指南](components-guide.md) 標識所需的客戶端庫。 瀏覽至「元件指南」並檢視「註解」元件，例如：

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

請注意，注釋必須有三個用戶端程式庫才能正常呈現和運作。 在參考擴充注釋時，需要納入這些注釋，以及 [擴展注釋的客戶端庫](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`)。

![chlimage_1-47](assets/chlimage_1-47.png)

## 將自訂備注新增至頁面 {#add-custom-comments-to-a-page}

由於每頁只能有一個「注釋」系統，因此建立範例頁面較簡單，如 [建立範例頁面](create-sample-page.md) 教學課程。

建立後，進入「設計」模式，並使「自訂」元件群組可供使用 `Alt Comments` 要新增至頁面的元件。

為了讓注釋顯示並正常運作，必須將注釋的客戶端庫添加到頁的clientlibslist(請參見 [Communities元件的Clientlibs](clientlibs.md))。

### 範例頁面上的Comments Clientlibs {#comments-clientlibs-on-sample-page}

![範例頁面上的Comments Clientlibs](assets/chlimage_1-48.png)

### 作者：範例頁面上的替代註解 {#author-alt-comment-on-sample-page}

![範例頁面上的替代註解](assets/chlimage_1-49.png)

### 作者：範例頁面註解節點 {#author-sample-page-comments-node}

您可以檢視範例頁面之註解節點的屬性，以驗證CRXDE中的resourceType `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### 發佈範例頁面 {#publish-sample-page}

將自訂元件新增至頁面後，也必須(re) [發佈頁面](sites-console.md#publishing-the-site).

### 發佈：範例頁面上的替代註解 {#publish-alt-comment-on-sample-page}

發佈自訂應用程式和範例頁面後，應可輸入註解。 登入時，使用 [示範使用者](tutorials.md#demo-users) 或管理員，您應可以張貼意見。

以下是aaron.mcdonald@mailinator.com發佈評論：

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

現在，擴展元件在預設外觀中工作正常，是時候修改外觀了。
