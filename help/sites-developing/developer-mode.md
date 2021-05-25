---
title: 開發人員模式
seo-title: 開發人員模式
description: 開發人員模式會開啟側面板，其中包含數個標籤，為開發人員提供目前頁面的相關資訊
seo-description: 開發人員模式會開啟側面板，其中包含數個標籤，為開發人員提供目前頁面的相關資訊
uuid: 2ff0d85e-fe49-4506-b6d6-74cc060d7ea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: efbe46a3-c37f-4b67-8b3a-188cfc75118b
exl-id: 733eddf1-48f9-45c2-a1b4-138cf32b4b59
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# 開發者模式{#developer-mode}

在AEM中編輯頁面時，有數個[模式](/help/sites-authoring/author-environment-tools.md#page-modes)可供使用，包括開發人員模式。 這會開啟一個側面板，其中包含數個標籤，為開發人員提供目前頁面的相關資訊。 這三個標籤是：

* **[](#components)** 元件，用於查看結構和效能資訊。
* **[](#tests)** 測試執行測試和分析結果。
* **[](#errors)** 錯誤，無法查看發生的任何問題。

這些功能可協助開發人員：

* Discover:頁面的組成。
* 調試：何時何地發生，進而有助於解決問題。
* 測試：應用程式是否如預期般運作。

>[!CAUTION]
>
>開發人員模式：
>
>* 僅適用於觸控式UI（編輯頁面時）。
>* 在行動裝置上或案頭上的小視窗上皆無法使用（因空間限制）。
   >   * 當寬度小於1024px時即會發生此情況。
>* 僅對`administrators`組成員的用戶可用。


>[!CAUTION]
>
>開發人員模式僅適用於未使用nosamplecontent執行模式的標準製作例項。
>
>如有需要，可將其設定為使用：
>
>* 在使用nosamplecontent執行模式的製作例項上
>* 發佈例項

>
>
使用後應再次停用。

>[!NOTE]
>
>請參閱：
>
>* 知識庫文章[疑難排解AEM TouchUI問題](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)，以取得進一步提示和工具。
>* AEM Gems工作階段關於[AEM 6.0開發人員模式](https://docs.adobe.com/content/ddc/en/gems/aem-6-0-developer-mode.html)。


## 開啟開發人員模式{#opening-developer-mode}

開發人員模式是作為側面板實作到頁面編輯器。 若要開啟面板，請從頁面編輯器工具列的模式選取器中選取&#x200B;**開發人員**:

![chlimage_1-229](assets/chlimage_1-229.png)

面板分為兩個標籤：

* **[元件](/help/sites-developing/developer-mode.md#components)**  — 這會顯示與作者內容樹狀結構 [類](/help/sites-authoring/author-environment-tools.md#content-tree) 似的元件樹

* **[錯誤](/help/sites-developing/developer-mode.md#errors)**  — 發生問題時，會顯示每個元件的詳細資訊。

### 元件 {#components}

![chlimage_1-230](assets/chlimage_1-230.png)

這會顯示元件樹，其中包含：

* 概述在頁面上呈現的元件和範本鏈（SLY、JSP等）。 樹可以展開，以顯示階層內的內容。
* 顯示轉譯元件所需的伺服器端計算時間。
* 允許您展開樹並在樹中選擇特定元件。 「選擇」提供對元件詳細資訊的訪問；例如：

   * 儲存庫路徑
   * 指令碼連結(以CRXDE Lite存取)

* 選取的元件（在內容流程中，以藍色邊框表示）會在內容樹狀結構中反白顯示（反之亦然）。

這有助於：

* 決定並比較每個元件的轉譯時間。
* 請參閱並了解階層。
* 了解並改善頁面載入時間，方法是尋找緩慢的元件。

每個元件項目都可顯示（例如）:

![chlimage_1-231](assets/chlimage_1-231.png)

* **查看詳細資訊**:一個清單連結，其中顯示：

   * 用於呈現元件的所有元件指令碼。
   * 此特定元件的儲存庫內容路徑。

   ![chlimage_1-232](assets/chlimage_1-232.png)

* **編輯指令碼**:連結：

   * 以CRXDE Lite開啟元件指令碼。

* 展開元件輸入項（箭頭頭）也可以顯示：

   * 所選元件內的階層。
   * 單獨呈現所選元件、內嵌的任何個別元件以及合併總計的呈現時間。

   ![chlimage_1-233](assets/chlimage_1-233.png)

>[!CAUTION]
>
>有些連結指向`/libs`下的指令碼。 但是，這些僅供參考，您&#x200B;**不得**&#x200B;編輯`/libs`下的任何內容，因為您所做的任何更改都可能丟失。 這是因為當您升級或套用Hotfix/Feature Pack時，此分支很可能會發生變更。 您需要的任何變更都應在`/apps`下進行，請參閱[覆蓋和覆寫](/help/sites-developing/overlays.md)。

### 錯誤 {#errors}

![chlimage_1-234](assets/chlimage_1-234.png)

希望&#x200B;**Errors**&#x200B;標籤將始終為空（如上所示），但當出現問題時，將顯示每個元件的以下詳細資訊：

* 如果元件將項目寫入錯誤記錄，以及錯誤的詳細資訊，並將連結導向CRXDE Lite內的適當程式碼，則會發出警告。
* 元件開啟管理工作階段時出現警告。

例如，在呼叫未定義方法的情況下，產生的錯誤會顯示在&#x200B;**Errors**&#x200B;標籤中：

![chlimage_1-235](assets/chlimage_1-235.png)

「元件」頁簽的樹中的元件條目在發生錯誤時也將用指示器標籤。

### 測試 {#tests}

>[!CAUTION]
>
>在AEM 6.2中，開發人員模式的測試功能已重新實作為獨立工具應用程式。
>
>如需完整詳細資訊，請參閱[測試您的UI](/help/sites-developing/hobbes.md)。
