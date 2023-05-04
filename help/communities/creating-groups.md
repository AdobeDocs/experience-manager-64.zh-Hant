---
title: 社群群組
seo-title: Community Groups
description: 建立社群群組
seo-description: Creating community groups
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 3%

---

# 社群群組 {#community-groups}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

社群群組功能是讓來自發佈和作者環境的授權使用者（社群成員和作者）在社群網站中動態建立子社群的能力。

若 [組函式](functions.md#groups-function) 存在於 [社群網站](sites-console.md) 結構。

A [社群群組範本](tools-groups.md) 提供動態建立社群群組時的社群群組頁面設計。

當將該功能添加到社區站點的結構或社區站點模板時，為組功能選擇一個或多個組模板。 此群組範本清單會顯示給從社群網站動態建立新群組的成員或作者。

## 建立新群組 {#creating-a-new-group}

建立新社群群組的能力取決於社群網站的存在，該網站包含群組函式，例如從 ` [Reference Site Template](sites.md)`.

以下範例使用從 `Reference Site Template` 如 [開始使用AEM Communities](getting-started.md) 教學課程。

這是在 **[!UICONTROL 群組]** 已選取功能表項目：

![chlimage_1-236](assets/chlimage_1-236.png)

選取 **[!UICONTROL 新組]** 表徵圖，將開啟編輯對話框。

在 **[!UICONTROL 設定]** 頁簽，您可以提供組的基本功能：

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 群組名稱]**
要在社群網站上顯示的群組標題。

* **[!UICONTROL 說明]**
要在社群網站上顯示的群組說明。

* **[!UICONTROL 邀請]**
要邀請加入組的成員清單。 預先輸入搜尋可提供社群成員邀請的建議。

* **[!UICONTROL 群組URL名稱]**
成為URL一部分的群組頁面名稱。

* **[!UICONTROL 開啟群組]**
選取 
`Open Group` 表示任何匿名網站訪客都可能檢視內容，並將取消選取 `Member Only Group`.

* **[!UICONTROL 僅成員組]**
選取 
`Member Only Group` 僅指示組的成員可以查看內容，並將取消選擇 `Open Group`.

在 **[!UICONTROL 範本]** 索引標籤是從社區站點結構或社區站點模板中包含組函式時指定的社區組模板清單中進行選擇的功能。

![chlimage_1-238](assets/chlimage_1-238.png)

在 **[!UICONTROL 影像]** 索引標籤是上傳影像的功能，可在社群網站的「群組」頁面上顯示群組的影像。 預設樣式表會將影像大小為170 x 90像素。

![chlimage_1-239](assets/chlimage_1-239.png)

選取 **[!UICONTROL 建立群組]** 按鈕，則會根據所選的模板建立組的頁面，並為成員資格建立用戶組，並且「組」頁將被更新以顯示新的子社區。

例如，具有名為「焦點組」的新子社區的「組」頁將顯示如下（仍以社區組管理員身份登錄）:

![chlimage_1-240](assets/chlimage_1-240.png)

選取 `Focus Group` 連結將在瀏覽器中開啟「焦點組」頁面，該頁面具有基於所選模板的初始外觀，並在主社區網站菜單下包含子菜單：

![chlimage_1-241](assets/chlimage_1-241.png)

## 社區組成員清單元件 {#community-group-member-list-component}

此 `Community Group Member List` 元件供群組範本的開發人員使用。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [社群群組要點](essentials-groups.md) 頁面。

如需社群群組的其他相關資訊，請造訪 [管理使用者和使用者群組](users.md).
