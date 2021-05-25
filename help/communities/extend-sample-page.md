---
title: 將注釋添加到示例頁
seo-title: 將注釋添加到示例頁
description: 將自訂備注新增至頁面
seo-description: 將自訂備注新增至頁面
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# 將注釋添加到示例頁{#add-comment-to-sample-page}

現在，自定義注釋系統的元件已位於應用程式目錄(/app)中，因此可以使用擴展元件。 要受影響的網站中評論系統的例項必須將其resourceType設定為自訂評論系統，並包含所有必要的用戶端程式庫。

## 識別所需的Clientlib {#identify-required-clientlibs}

對於擴展注釋，也需要預設注釋的樣式和功能所需的客戶端庫。

[社群元件指南](components-guide.md)識別所需的用戶端程式庫。 瀏覽至「元件指南」並檢視「註解」元件，例如：

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

請注意，注釋必須有三個用戶端程式庫才能正常呈現和運作。 在引用擴展注釋時需要包括這些注釋，以及[擴展注釋的客戶端庫](extend-create-components.md#create-a-client-library-folder)(`apps.custom.comments`)。

![chlimage_1-47](assets/chlimage_1-47.png)

## 將自訂備注新增至頁面{#add-custom-comments-to-a-page}

由於每頁只能有一個注釋系統，因此建立範例頁面更簡單，如簡短的[建立範例頁面](create-sample-page.md)教學課程所述。

建立後，進入「設計」模式，並使「自定義」元件組可用，以允許將`Alt Comments`元件添加到頁面中。

為了讓注釋顯示並正常運作，必須將注釋的客戶端庫添加到頁的clientlibslist（請參閱[Clientlibs for Communities Components](clientlibs.md)）。

### 範例頁面{#comments-clientlibs-on-sample-page}上的註解用戶端

![範例頁面上的Comments Clientlibs](assets/chlimage_1-48.png)

### 作者：範例頁面{#author-alt-comment-on-sample-page}上的替代註解

![範例頁面上的替代註解](assets/chlimage_1-49.png)

### 作者：範例頁面註解節點{#author-sample-page-comments-node}

您可以在`/content/sites/sample/en/jcr:content/content/primary/comments`查看範例頁面的注釋節點屬性，以驗證CRXDE中的resourceType。

![chlimage_1-50](assets/chlimage_1-50.png)

### 發佈範例頁面{#publish-sample-page}

將自訂元件新增至頁面後，也必須(re)[發佈頁面](sites-console.md#publishing-the-site)。

### 發佈：範例頁面{#publish-alt-comment-on-sample-page}上的替代註解

發佈自訂應用程式和範例頁面後，應可輸入註解。 登入時，若使用[示範使用者](tutorials.md#demo-users)或管理員，應可張貼意見。

以下是aaron.mcdonald@mailinator.com發佈評論：

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

現在，擴展元件在預設外觀中工作正常，是時候修改外觀了。
