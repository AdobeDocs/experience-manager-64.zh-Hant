---
title: 改變外觀
seo-title: 改變外觀
description: 修改指令碼
seo-description: 修改指令碼
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
translation-type: tm+mt
source-git-commit: 1ae2d7f99286e0b958d343778159e2d35095510e
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# 更改外觀{#alter-the-appearance}

## 修改指令碼{#modify-the-script}

comment.hbs指令碼負責建立每個註解的整體HTML。

若要不在每個張貼的留言旁顯示頭像：

1. 將`comment.hbs`從`libs`複製到`apps`
   1. 選取 `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. 選擇&#x200B;**[!UICONTROL Copy]**
   1. 選取 `/apps/social/commons/components/hbs/comments/comment`
   1. 選擇&#x200B;**[!UICONTROL 貼上]**
1. 開啟覆蓋的`comment.hbs`
   * 按兩下`/apps/social/commons/components/hbs/comments/comment folder`中的節點`comment.hbs`
1. 查找以下行並刪除或注釋它們：

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

刪除線條，或用&#39;&lt;!—&#39;和&#39;—>&#39;來注釋掉它們。 此外，字元「xxx」也會加入，作為頭像原本所在位置的視覺指標。

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## 複製覆蓋{#replicate-the-overlay}

使用複製工具將覆蓋的注釋元件推送到發佈實例。

>[!NOTE]
>
>更強穩的複製形式是在「包管理器」中建立包，並[activate](../../help/sites-administering/package-manager.md#replicating-packages)。 可以導出和歸檔包。

在全局導航中，選擇&#x200B;**[!UICONTROL 工具>部署>複製]**，然後選擇&#x200B;**[!UICONTROL 激活樹]**。

對於開始路徑，輸入`/apps/social/commons`並選擇&#x200B;**[!UICONTROL 激活]**。

![chlimage_1-42](assets/chlimage_1-42.png)

## 查看結果{#view-results}

如果您以管理員身分登入發佈例項，例如以管理員／管理員身分登入http://localhost:4503/crx/de，則可驗證覆蓋的元件是否在此。

如果您登出並重新登入為`aaron.mcdonald@mailinator.com/password`並重新整理頁面，您會發現張貼的留言不再顯示為頭像，而是顯示簡單的「xxx」。

![chlimage_1-43](assets/chlimage_1-43.png)

