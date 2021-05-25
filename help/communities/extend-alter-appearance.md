---
title: 更改外觀(HBS)
seo-title: 更改外觀
description: 修改HBS指令碼
seo-description: 修改HBS指令碼
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# 更改外觀(HBS){#alter-the-appearance-hbs}

現在，應用程式目錄(/apps)中的自訂註解系統元件已就緒，resourceSuperType參考預設註解系統和已註冊的自訂模型/檢視，便可修改實施。

對於簡單的示範，會移除張貼評論之已登入使用者的顯示頭像視覺功能。

>[!NOTE]
>
>若要使用擴充功能，要受影響之網站(/content)中之留言系統的例項必須將其resourceType設為自訂留言系統。

## 修改HBS指令碼{#modify-the-hbs-scripts}

使用[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 開啟[/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * 對標籤加上註解貼文（~第21行）的顯示圖片進行註解：

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* 開啟[/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * 註解標籤，其中包含下一個註解項目的頭像（~第44行）:

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* 選擇&#x200B;**保存全部**

## 複製自定義應用{#replicate-custom-app}

修改應用程式後，必須重新複製自訂元件。

一種方法是

* 從主功能表

   * 選擇&#x200B;**[!UICONTROL 工具>操作>複製]**
   * 選取 `Activate Tree`
   * 設定`Start Path`:至`/apps/custom`
   * 取消選中`Only Modified`
   * 選擇`Activate`按鈕

## 在已發佈的範例頁面{#view-modified-comment-on-published-sample-page}上檢視已修改的註解

[繼續在](extend-sample-page.md#publish-sample-page) 發佈例項上（仍以相同使用者身分登入）體驗，現在可以重新整理發布環境中的頁面，以檢視要移除頭像的修改：

![chlimage_1-81](assets/chlimage_1-81.png)

## 注釋擴展包示例{#sample-comment-extension-package}

附加是在本教學課程中建立的自訂註解應用程式套件。

[取得檔案](assets/sample-comment-extension-6-1-fp3.zip)
