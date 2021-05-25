---
title: 更改外觀
seo-title: 更改外觀
description: 修改指令碼
seo-description: 修改指令碼
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# 更改外觀{#alter-the-appearance}

## 修改指令碼{#modify-the-script}

comment.hbs指令碼負責為每個注釋建立整體HTML。

若要不在每個已張貼留言旁顯示頭像：

1. 將`comment.hbs`從`libs`複製到`apps`
   1. 選取 `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. 選擇&#x200B;**[!UICONTROL 複製]**
   1. 選取 `/apps/social/commons/components/hbs/comments/comment`
   1. 選擇&#x200B;**[!UICONTROL 貼上]**
1. 開啟覆蓋的`comment.hbs`
   * 按兩下`/apps/social/commons/components/hbs/comments/comment folder`中的節點`comment.hbs`
1. 找到以下行，然後刪除或注釋這些行：

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

刪除線，或用「&lt;！」括住線 — 」和「 — >」來注釋掉它們。 此外，會新增字元「xxx」，作為顯示頭像原本會變成何處的視覺指標。

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## 複製覆蓋{#replicate-the-overlay}

使用復寫工具將重疊的註解元件推送至發佈執行個體。

>[!NOTE]
>
>更強健的復寫形式是在套件管理器中建立套件，並[啟用](../../help/sites-administering/package-manager.md#replicating-packages)它。 可匯出和封存套件。

從全局導航中，選擇&#x200B;**[!UICONTROL 工具>部署>複製]**，然後選擇&#x200B;**[!UICONTROL 激活樹]**。

對於起始路徑，請輸入`/apps/social/commons`並選擇&#x200B;**[!UICONTROL 激活]**。

![chlimage_1-42](assets/chlimage_1-42.png)

## 查看結果{#view-results}

如果您以管理員身分登入發佈執行個體(例如，以管理員/管理員身分登入http://localhost:4503/crx/de)，即可驗證覆蓋的元件是否位於該處。

如果您登出並重新登入為`aaron.mcdonald@mailinator.com/password`，然後重新整理頁面，您會看到張貼的留言不再以頭像顯示，而是顯示簡單的「xxx」。

![chlimage_1-43](assets/chlimage_1-43.png)
