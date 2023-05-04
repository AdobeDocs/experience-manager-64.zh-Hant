---
title: 更改外觀
seo-title: Alter the Appearance
description: 修改指令碼
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 3%

---

# 更改外觀 {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 修改指令碼 {#modify-the-script}

comment.hbs指令碼負責為每個注釋建立整體HTML。

若要不在每個已張貼留言旁顯示頭像：

1. 複製 `comment.hbs`從 `libs`to `apps`
   1. 選取 `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. 選擇 **[!UICONTROL 複製]**
   1. 選取 `/apps/social/commons/components/hbs/comments/comment`
   1. 選擇 **[!UICONTROL 貼上]**
1. 開啟覆蓋物 `comment.hbs`
   * 按兩下節點  `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. 找到以下行，然後刪除或注釋這些行：

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

刪除這些行，或用「&lt;!> — 」和「 — >」來注釋掉它們。 此外，會新增字元「xxx」，作為顯示頭像原本會變成何處的視覺指標。

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## 復寫覆蓋 {#replicate-the-overlay}

使用復寫工具將重疊的註解元件推送至發佈執行個體。

>[!NOTE]
>
>更強大的複製形式是在Package Manager中建立包，並 [啟用](../../help/sites-administering/package-manager.md#replicating-packages) 它。 可匯出和封存套件。

在全域導覽中，選取 **[!UICONTROL 工具>部署>復寫]** 然後 **[!UICONTROL 激活樹]**.

對於起始路徑，請輸入 `/apps/social/commons` 選取 **[!UICONTROL 啟動]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## 查看結果 {#view-results}

如果您以管理員身分登入發佈執行個體(例如，以管理員/管理員身分登入http://localhost:4503/crx/de)，即可驗證覆蓋的元件是否位於該處。

如果您登出並重新登入為 `aaron.mcdonald@mailinator.com/password` 重新整理頁面後，您會看到張貼的留言不再以頭像顯示，而是顯示簡單的「xxx」。

![chlimage_1-43](assets/chlimage_1-43.png)
