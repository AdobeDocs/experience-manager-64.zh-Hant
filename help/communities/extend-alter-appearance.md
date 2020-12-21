---
title: 變更外觀(HBS)
seo-title: 改變外觀
description: 修改HBS指令碼
seo-description: 修改HBS指令碼
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# 變更外觀(HBS){#alter-the-appearance-hbs}

現在，應用程式目錄(/apps)中自訂註解系統的元件已就緒，resourceSuperType會參照預設註解系統，並註冊自訂模型／檢視，因此可修改實施。

若要進行簡單展示，會移除張貼評論之已登入使用者所顯示的視覺功能。

>[!NOTE]
>
>若要使用擴充功能，要影響之網站(/content)中之留言系統的例項必須將其resourceType設為自訂留言系統。

## 修改HBS指令碼{#modify-the-hbs-scripts}

使用[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 開啟[/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * 注釋掉包含評論貼文（~行21）之頭像的標籤：

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* 開啟[/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * 注釋掉包含頭像的標籤，以供下一個注釋項目使用(~ line 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* 選擇&#x200B;**全部保存**

## 複製自訂應用程式{#replicate-custom-app}

修改應用程式後，必須重新複製自訂元件。

一種方法是

* 從主菜單

   * 選擇&#x200B;**[!UICONTROL 工具>操作>複製]**
   * 選取 `Activate Tree`
   * 設定`Start Path`:至`/apps/custom`
   * 取消選中`Only Modified`
   * 選擇`Activate`按鈕

## 在已發佈範例頁面上檢視已修改的註解{#view-modified-comment-on-published-sample-page}

[繼續發](extend-sample-page.md#publish-sample-page) 布例項的體驗，仍以相同使用者的身分登入，現在可以在發佈環境中重新整理頁面，以檢視修改以移除頭像：

![chlimage_1-81](assets/chlimage_1-81.png)

## 注釋擴展包{#sample-comment-extension-package}示例

附加是本教學課程中建立的自訂註解應用程式套件。

[取得檔案](assets/sample-comment-extension-6-1-fp3.zip)