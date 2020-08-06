---
title: 社群群組
seo-title: 社群群組
description: 建立社群群組
seo-description: 建立社群群組
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---


# 社群群組 {#community-groups}

社群群組功能是讓來自發佈和作者環境的授權使用者（社群成員和作者）在社群網站中動態建立子社群的能力。

當群組功能出現在社 [群網站結構](functions.md#groups-function) 中時，就會 [出現此功能](sites-console.md) 。

社 [群群組範本](tools-groups.md) ，可在動態建立社群群組時，提供社群群組頁面的設計。

將該功能添加到社區站點的結構或社區站點模板時，為組功能選擇一個或多個組模板。 此群組範本清單會顯示給從社群網站動態建立新群組的成員或作者。

## 建立新群組 {#creating-a-new-group}

建立新社群群群組的能力，取決於社群網站的存在，其中包含群組功能，例如從建立的社群網站 ` [Reference Site Template](sites.md)`。

下列範例使用從中建立的社群網站，如「AEM社群快速入門」教 `Reference Site Template` 學課程中 [所述](getting-started.md) 。

這是在選取「群組」功能表項目時， **[!UICONTROL 在發佈時載入]** 的頁面：

![chlimage_1-236](assets/chlimage_1-236.png)

選擇「新建組」 **[!UICONTROL 表徵圖後]** ，將開啟編輯對話框。

在「設 **[!UICONTROL 定]** 」標籤下，您提供群組的基本功能：

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 群組名]**&#x200B;稱要顯示在社群網站上的群組標題。

* **[!UICONTROL 說]**&#x200B;明要在社群網站上顯示的群組說明。

* **[!UICONTROL 邀請]**&#x200B;要邀請加入群組的成員清單。 提前輸入搜尋將提供社群成員邀請的建議。

* **[!UICONTROL 群組URL名]**&#x200B;稱成為URL一部分之群組頁面的名稱。

* **[!UICONTROL 開啟群組]**&#x200B;選取 
`Open Group` 指出任何匿名網站訪客皆可檢視該內容，並將取消選取 `Member Only Group`。

* **[!UICONTROL 僅成員組選]**&#x200B;擇 
`Member Only Group` 表示只有群組成員可以檢視內容，且會取消選取 `Open Group`。

在「模 **[!UICONTROL 板]** 」(Template)頁籤下，可以從社區組模板清單中進行選擇，這些模板是在社區站點結構或社區站點模板中包含組功能時指定的。

![chlimage_1-238](assets/chlimage_1-238.png)

在「影 **[!UICONTROL 像]** 」標籤下方，可上傳影像，以便在社群網站的「群組」頁面上顯示群組。 預設樣式表會將影像大小設為170 x 90像素。

![chlimage_1-239](assets/chlimage_1-239.png)

選取「建 **[!UICONTROL 立群組]** 」按鈕後，會根據選擇的範本建立群組的頁面，並為會籍建立使用者群組，而「群組」頁面將會更新以顯示新的子社群。

例如，具有名為「焦點群組」的新子社群的「群組」頁面（已上傳影像縮圖）會顯示如下（仍以社群群組管理員身分登入）:

![chlimage_1-240](assets/chlimage_1-240.png)

選取連 `Focus Group` 結會在瀏覽器中開啟「焦點群組」頁面，此頁面會根據所選範本具有初始外觀，並在主社群網站功能表下方包含子功能表：

![chlimage_1-241](assets/chlimage_1-241.png)

## Community Group Member List Component {#community-group-member-list-component}

此元 `Community Group Member List` 件僅供群組範本開發人員使用。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發 [人員的Community Group Essentials](essentials-groups.md) （社群群組基本工具）頁面。

如需社群群組的其他相關資訊，請造 [訪管理使用者和使用者群組](users.md)。
