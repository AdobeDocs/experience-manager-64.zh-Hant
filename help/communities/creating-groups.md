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

當[groups函式](functions.md#groups-function)存在於[社區站點](sites-console.md)結構中時，即存在此能力。

[社群群組範本](tools-groups.md)提供動態建立社群群組時的社群群組頁面設計。

將該功能添加到社區站點的結構或社區站點模板時，為組功能選擇一個或多個組模板。 此群組範本清單會顯示給從社群網站動態建立新群組的成員或作者。

## 建立新組{#creating-a-new-group}

建立新社群群群組的能力取決於包含群組功能的社群網站，例如從` [Reference Site Template](sites.md)`建立的社群網站。

下面的範例使用從`Reference Site Template`建立的社群網站，如&lt;a1/> AEM Communities[教學課程中所述。](getting-started.md)

這是在選取&#x200B;**[!UICONTROL Groups]**&#x200B;功能表項目時載入發佈的頁面：

![chlimage_1-236](assets/chlimage_1-236.png)

選擇&#x200B;**[!UICONTROL 新建組]**&#x200B;表徵圖後，將開啟編輯對話框。

在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下，您提供群組的基本功能：

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 群組]**
名稱要在社群網站上顯示的群組標題。

* **[!UICONTROL 說]**
明要顯示在社群網站上的群組說明。

* **[!UICONTROL 邀]**
請要邀請加入群組的成員清單。提前輸入搜尋將提供社群成員的邀請建議。

* **[!UICONTROL 群組URL]**
名稱成為URL一部分之群組頁面的名稱。

* **[!UICONTROL 開啟群]**
組 
`Open Group` 指出任何匿名網站訪客皆可檢視該內容，並將取消選取 `Member Only Group`。

* **[!UICONTROL 僅成員組選]**
擇 
`Member Only Group` 表示只有群組成員可以檢視內容，且會取消選取 `Open Group`。

在&#x200B;**[!UICONTROL Template]**&#x200B;標籤下，可以從社區組模板清單中進行選擇，這些模板是在社區站點結構或社區站點模板中包含組功能時指定的。

![chlimage_1-238](assets/chlimage_1-238.png)

在&#x200B;**[!UICONTROL Image]**&#x200B;標籤下，可上傳影像，以便在社群網站的「群組」頁面上顯示群組。 預設樣式表會將影像大小設為170 x 90像素。

![chlimage_1-239](assets/chlimage_1-239.png)

選擇&#x200B;**[!UICONTROL 建立群組]**&#x200B;按鈕後，會根據所選範本建立群組的頁面，並為會員資格建立使用者群組，而「群組」頁面將會更新以顯示新的子社群。

例如，具有名為「焦點群組」的新子社群的「群組」頁面（已上傳影像縮圖）會顯示如下（仍以社群群組管理員身分登入）:

![chlimage_1-240](assets/chlimage_1-240.png)

選擇`Focus Group`連結會在瀏覽器中開啟「焦點群組」頁面，此頁面會根據所選範本具有初始外觀，並在主社群網站功能表下方包含子功能表：

![chlimage_1-241](assets/chlimage_1-241.png)

## 社區組成員清單元件{#community-group-member-list-component}

`Community Group Member List`元件是供群組範本開發人員使用。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[Community Group Essentials](essentials-groups.md)頁面。

有關社區組的其他資訊，請訪問[管理用戶和組](users.md)。
