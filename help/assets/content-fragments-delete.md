---
title: 內容片段 - 刪除考量事項
seo-title: Content Fragments - Delete Considerations
description: 內容片段 - 刪除考量事項
seo-description: Content Fragments - Delete Considerations
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 11%

---

# 內容片段 - 刪除考量事項 {#content-fragments-delete-considerations}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>某些內容片段功能需要應用 [AEM 6.4 Service Pack 2(6.4.2.0)或更新版本](/help/release-notes/sp-release-notes.md).

## 權限 — 刪除或不刪除 {#permissions-delete-or-not-delete}

刪除內容的能力強大，但可能很敏感，許多行業需要限制和控制這些權限的分配方式。

若要刪除權限，內容片段必須在兩個層級加以考量：

1. **內容片段為單一實體。**

   * **使用案例**:需要編輯/更新內容片段的使用者 —  **並刪除整個片段**.
   * **權限**:此 [刪除](/help/sites-administering/security.md#actions) 權限可以 [透過「使用者和/或群組管理」指派](/help/sites-administering/security.md#managing-permissions).

1. **組成內容片段的多個子實體；例如，變異、子節點。**

   內容片段編輯器的基本操作要求可以刪除這種暫時的子元素。 例如，在操縱變異時；編輯中繼資料或管理相關內容時，也會一併啟用。

   * **使用案例**:需要編輯/更新內容片段的使用者 —  **而不允許刪除整個片段**.
   * **權限**:請參閱 [僅編輯器功能所需的權限](content-fragments-delete.md#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>當使用者沒有任何 [刪除](/help/sites-administering/security.md#actions) 權限，內容片段編輯器會在 *只讀* 模式。

>[!NOTE]
>
>另請參閱 [如何在AEM中稽核使用者管理作業](/help/sites-administering/audit-user-management-operations.md).

## 僅編輯器功能所需的權限 {#permissions-required-for-editor-functionality-only}

對於需要編輯/更新內容片段而不允許他們刪除整個片段的使用者 ****，必須指派特定權限，因為內容片段編輯器的基本操作要求可以刪除暫時的子元素。

例如，在操縱變異時；編輯中繼資料或管理相關內容時，也會一併啟用。

>[!NOTE]
>
>編輯/更新內容片段所需的刪除權限，會包含在「刪除」權限中 [透過「使用者和/或群組管理」指派](/help/sites-administering/security.md#managing-permissions).

編輯/更新片段所需的權限需要套用至包含內容片段的節點或適當的父節點（位於「 」下的任何層級） `/content/dam`)。 當指派給此父節點時，權限會套用至該分支內的所有節點。

例如，會保留所有內容片段的資料夾，例如：

* `/content/dam/contentfragments`

>[!CAUTION]
>
>在 `/content/dam` 也是可能的，因為所有內容片段都儲存在此處。
>
>但此動作會將相同的刪除權限套用至 *all* 其他資產類型。

允許特定使用者和/或群組編輯/更新內容片段的權限先決條件為：

>[!NOTE]
>
>此清單顯示所需的所有權限，而不只是刪除權限。

* 對於內容片段節點或資料夾：

   * `jcr:addChildNodes`、`jcr:modifyProperties`

* 若 `jcr:content` 所有內容片段的節點：

   * `jcr:addChildNodes`, `jcr:modifyProperties` 和 `jcr:removeChildNodes`

* 適用於以下所有節點 `jcr:content` 所有內容片段的：

   * `jcr:addChildNodes`, `jcr:modifyProperties` 和 `jcr:removeChildNodes`, `jcr:removeNode`

這些 `remove` 權限 [在CRXDE Lite內使用存取控制清單進行管理](/help/sites-administering/user-group-ac-admin.md#access-right-management).

此 `add` 和 `modify` 也可以使用CRXDE Lite管理權限，或使用「使用者管理」主控台管理權限。

例如， `remove` 組的權限 `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
