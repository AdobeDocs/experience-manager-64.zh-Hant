---
title: AEM Assets發行說明
seo-title: AEM Assets
description: Adobe Experience Manager 6.4 Assets專屬發行說明。
seo-description: Release notes specific to Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 1%

---

# AEM Assets發行說明 {#aem-assets-release-notes}

本發行說明涵蓋AEM 6.4 Assets中完成的主要功能、重點和增強功能。 如需詳細資訊，請遵循提供的連結。

## Adobe資產連結 {#adobe-asset-link}

AdobeCreative Cloud中的企業資產連結可簡化創意人員與行銷人員在內容建立程式中的協作。 這是企業Creative Cloud中的新原生功能，可直接從Adobe Photoshop、Adobe Illustrator或Adobe InDesign連線至AEM Assets，而不需離開這些工具。

若要進一步了解功能、必要條件及存取方式，請參閱 [Adobe資產連結](https://helpx.adobe.com/tw/enterprise/using/adobe-asset-link.html) 頁面。

## 增強智慧標籤(由Adobe Sensei提供技術支援) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4除了於AEM 6.3中啟動的智慧標籤外，也導入了以人工智慧為基礎的增強智慧標籤功能。

* 智慧內容服務學習客戶的業務分類法，並使用該分類法來自動標籤數位資產，除了通用標籤外，還有與客戶相關的標籤。 它可大幅改善資產發現能力，並縮短上市時間。
* Adobe Sensei提供智慧內容服務，可讓您根據業務分類訓練影像識別演算法。 然後，系統會使用此內容智慧，對類似資產套用相關標籤。

若要使用AEM Assets增強智慧標籤，請安裝 [最新的AEM 6.4 Service Pack](https://helpx.adobe.com/tw/experience-manager/aem-releases-updates.html).

## 智慧翻譯搜尋(由Adobe Sensei提供技術支援) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4引入了智慧翻譯搜尋功能，以支援多語言搜尋案例。 現在，擁有跨多個地區設定的全球分散團隊的客戶可以存取不同語言的搜尋功能，而無須執行成本高昂且耗時的翻譯工作流程。

* 無需手動干預即可翻譯搜尋查詢。
* 智慧標籤會以英文產生，並會機器翻譯成其他語言。
* 多語言搜尋是使用開放原始碼程式庫Apache Joshua所建置，可支援超過50種語言。

## 使用者體驗 {#user-experience}

AEM 6.4可大幅改善瀏覽、搜尋、多頁資產和管理工具等領域的使用者體驗。 詳情如下：

瀏覽改善

* 新增內容樹狀結構邊欄，以快速導覽資產階層。 這會與清單檢視結合，還原傳統UI互動模型以瀏覽資產階層。
* 新的鍵盤快速鍵（例如：m）可移動資產、p可開啟屬性頁面、Ctrl + C可複製操作等。
* 改善捲動功能、在卡片和清單檢視中延遲載入體驗，以瀏覽大量資產。
* 改善「卡片檢視」，並支援根據檢視設定而調整不同大小的卡片。
* 改善資產詳細資訊體驗，提供檢視、導覽至「上一個」或「下一個」資產，以及資產數量、流動資產的功能。

搜尋改善

* 新的「返回搜索」按鈕，可導覽至搜尋項目，並返回搜尋結果中的相同位置，而不需再次執行搜尋查詢。
* 新的搜尋結果計數可顯示搜尋結果的數量。
* 改善「檔案類型搜尋篩選」，與先前的影像、檔案、多媒體選項相比，可根據微調mime類型(例如JPG、PNG和PSD)篩選搜尋結果。
* 改善具有精確時間戳記的搜尋篩選器，而非先前的時間滑桿功能。

多頁資產改良

* 改善多頁資產瀏覽體驗，並減少點按次數。
* 改善的註解和註解支援，所有註解和註解都可在資產層級（而非頁面層級）整理。

管理工具改良

* 改善「中繼資料」、「搜尋」和「含有預先類型的報表」管理工具中的屬性選擇器，並簡化管理體驗。

目錄

* 改善使用者體驗，與範本使用者介面保持一致。 如需詳細資訊，請參閱 [目錄製作者](../sites-administering/catalog-producer.md).

## 中繼資料 {#metadata}

AEM 6.4提供多種進階中繼資料管理功能，可大規模管理中繼資料，並透過規則和驗證強制執行中繼資料完整性。 以下是主要功能：

* 新的「大量中繼資料匯出」功能，可將大量資產的中繼資料匯出（全部、選擇性）為CSV格式，以供編輯、共用和協力廠商整合。
* 新增「大量中繼資料匯入」功能，可匯入CSV檔案以新增中繼資料，一次更新多個資產的現有中繼資料。 此操作為非同步操作，不會影響系統效能。 完成後，系統會透過AEM通知系統通知使用者。
* 使用中繼資料結構工具新增階層式和內容中繼資料。 現在可以定義相依性鏈，以及欄位之間的值對應。 您也可以定義顯示/隱藏中繼資料表單欄位的內容。 這樣，您隨時都只能根據其他欄位的值顯示相關欄位。

## 報表 {#reports}

AEM 6.4提供重大資產報告增強功能：

* 全新企業級、可擴充（適用於大型存放庫）的報表架構，套用Sling作業，以非同步處理報表請求。 您可以排程特定日期和時間的報表。 您也可以新增自訂欄至報表。
* 新的OOTB報表最常由客戶詢問，例如磁碟使用、檔案、連結共用、發佈至Brand Portal和智慧標籤訓練。
* 新的報表建立和管理UI包含微調選項、存取已封存報表的功能，請參閱報表執行狀態（成功、失敗、佇列等）。

## Brand Portal {#brand-portal}

* **6.3平台升級**:Brand Portal從AEM 6.0升級至AEM 6.3，具備新功能並改善效能。
* **平行發佈**:在AEM Assets和Brand Portal（以前是1個）之間可執行最多複製，這可大幅改善發佈效能
* **結構與搜尋面向發佈**:可將中繼資料結構和自訂搜尋刻面發佈至Brand Portal，如此可避免工作重複。
* **大量標籤發佈**:可將分類法（連同階層）發佈至Brand Portal，消除工作重複。
* **自行註冊或請求存取**:非註冊使用者的工作流程至Brand Portal。
* **應用程式內（螢幕上）維護通知**:通知會提前顯示，以避免業務中斷。
* **報表改善**:提供三份OOTB報表：下載、發佈和連結分享。
* **基於DRM的限制**:授權資產過期後，就無法從Brand Portal下載。

## AEM 桌面應用程式 {#aem-desktop-app}

AEM案頭應用程式已更新至1.8版，與AEM 6.4相容。AEM案頭應用程式的完整變更清單提供於專用的 [AEM案頭應用程式發行說明](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html) 檔案。\
以下是自AEM 6.3發行以來的AEM案頭應用程式重點清單：

* 可在背景上傳階層式資料夾。
* UI可監視背景中的資產上傳。
* 改善快取功能，包括管理快取參數的UI。
* 更廣泛支援AEM驗證設定(SAML/SSO)和網路代理。
* 支援性：從使用者介面輕鬆存取記錄檔。
* 改善客戶問題的穩定性和修正。

為了更輕鬆存取檔案和最佳實務，您可以取得下列檔案：

* [使用手冊](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)，針對使用應用程式的使用者。
* [安裝指南](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/install-upgrade.html)，旨在讓管理員設定AEM和AEM案頭應用程式以共同運作

## 分層儲存 {#tiered-storage}

AEM 6.4包含一組支援各種分層儲存首選項和實施生命週期規則的功能。 儲存選項也支援（但不限於）公共雲 — AWS或Azure。

* 用戶可以隨意選擇儲存類並稍後更改儲存類，並定義將資產從一個類儲存到另一個類的規則，或管理其資產的生命週期。
* 使用者透過選擇不同的AWS或Azure來降低儲存成本。

如需支援平台的概觀，請參閱 [技術需求檔案](../sites-deploying/technical-requirements.md).

## 已關閉的使用者群組 {#closed-user-group}

* 在AEM 6.4中，「封閉使用者群組」或CUG提供在發佈執行個體上限制資料夾存取的方式，這是觸控式UI選項，可透過資料夾層級的資料夾屬性頁面新增主體，並套用至內部的所有資料夾和子資料夾/資產。
* 在發佈模式中，如果已設定CUG並在資料夾上啟用授權，則當使用者嘗試存取資料夾時，會將使用者重新導向至登入頁面。 因此，授權使用者只有在成功登入後，才能存取資料夾及其資產。 因此，CUG限制除了所選承擔者之外，所有人對內容存放庫中指定樹的讀取存取。

## Dynamic Media附加元件 {#dynamic-media-add-on}

Dynamic Media 6.4版支援新模式：透過AEM Assets網頁UI上傳和管理主資產，而Dynamic Media雲端傳送服務會在背景處理動態轉譯和其他動態媒體功能。

在此模式中(先於 [AEM 6.3 Feature Pack 14410和18912](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html))，使用者便能透過現代AEM Assets網頁UI獲得端對端資產管理和動態媒體功能，同時仍可運用回溯相容於Dynamic Media Classic(Scene7)的傳送服務，包括未變更的傳送URL。

此外，AEM 6.4也推出了Adobe Sensei提供的新功能、VR和3D等新興媒體的增強功能、Dynamic Media檢視器，以及互動式影像和轉盤橫幅中的體驗片段支援。

### 智慧型裁切(由Adobe Sensei提供技術支援) {#smart-crop-powered-by-adobe-sensei}

* 智慧型裁切功能會自動提供影像的非破壞性裁切，以保留回應式設計的興趣點。 您可以預覽已裁切的建議，並視需要手動調整。
* 此功能還支援為產品影像自動生成色票。 自動色票產生有助於自動將顏色色票、圖樣色票或兩者新增至產品影像。

請參閱 [影像設定檔](../assets/image-profiles.md) 檔案以深入了解。

另請參閱 [將Dynamic Media Assets新增至頁面](../assets/adding-dynamic-media-assets-to-pages.md) 說明檔案，進一步了解如何搭配Dynamic Media元件使用智慧型裁切。

### 智慧型影像 {#smart-imaging}

* 智慧型影像處理利用每個用戶的獨特觀看特性，自動提供針對其體驗而優化的影像，從而獲得更好的效能和參與度。
* 影像會根據瀏覽器功能自動轉換為不同格式。
* 影像品質設定是分別在瀏覽器中決定並套用。 這種智慧使有限的頻寬和較低的連接速度都能接受映像載入效能。

請參閱 [智慧型影像](../assets/imaging-faq.md) 檔案以深入了解。

### 新興媒體和檢視器增強功能 {#emerging-media-amp-viewer-enhancements}

* 支援新的檢視器，為使用者提供更好、沈浸式的體驗。
* 全景查看器有助於吸引用戶，並提供更好的體驗室場景、屬性、位置和景觀的功能。 請參閱 [全景影像](../assets/panoramic-images.md) 要學習的檔案。

* VR檢視器可為屬性、位置和景觀提供身臨其境的體驗。
* 針對產品影像最佳化的垂直影像檢視器。
* 改善鍵盤協助工具。
