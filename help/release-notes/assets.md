---
title: AEM Assets發行說明
seo-title: AEM Assets
description: Adobe Experience Manager 6.4 Assets的發行說明。
seo-description: Adobe Experience Manager 6.4 Assets的發行說明。
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 1%

---


# AEM Assets發行說明{#aem-assets-release-notes}

這些版本注意事項涵蓋AEM 6.4 Assets中的主要功能、重點和增強功能。 如需詳細資訊，請依照提供的連結進行。

## Adobe Asset Link {#adobe-asset-link}

適用於企業的Creative Cloud中的Adobe Asset Link可簡化創意人員與行銷人員在內容建立程式中的協作。 它是適用於企業的Creative Cloud的新原生功能，可直接從Adobe Photoshop、Adobe Illustrator或Adobe InDesign連線至AEM資產。 而不需離開這些工具。

若要進一步瞭解功能、必要條件及如何存取，請參閱[Adobe Asset Link](https://helpx.adobe.com/tw/enterprise/using/adobe-asset-link.html)頁面。

## 增強的智慧型標籤（由Adobe Sensei提供支援）{#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4除了在AEM 6.3中啟動的智慧型標籤外，還推出以人工智慧為基礎的增強智慧型標籤功能。

* 智慧型內容服務會學習客戶的業務分類法，並使用該分類法，除了使用一般標籤外，還使用客戶相關標籤自動標籤數位資產。 它可大幅改善資產發現能力，並縮短上市時間。
* Adobe Sensei為智慧型內容服務提供支援，讓您針對業務分類法訓練影像識別演算法。 然後，此內容智慧會用來對類似資產套用相關標籤。

若要使用AEM Assets Enhanced Smart Tags，請安裝[最新的AEM 6.4](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)服務套件。

## 智慧型翻譯搜尋（由Adobe Sensei提供支援）{#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4推出智慧型翻譯搜尋功能，以支援多語言搜尋藍本。 擁有跨多個地區的全球團隊的客戶現在可以存取不同語言的搜尋功能，而不需要進行昂貴且耗時的翻譯工作流程。

* 無需手動干預，即可翻譯搜索查詢。
* 智慧型標籤會以英文產生，並以機器翻譯成其他語言。
* 多語言搜尋是使用支援50多種語言的開放原始碼程式庫Apache Joshua來建立。

## 使用者體驗{#user-experience}

AEM 6.4在瀏覽、搜尋、多頁資產和管理工具等方面提供大幅的使用者體驗改善。 詳細資訊如下：

瀏覽改良功能

* 新的內容樹狀結構可快速導覽資產階層。 這會與清單檢視結合，將Classic UI互動模型還原為瀏覽資產階層。
* 新的鍵盤快速鍵（例如m）可移動資產、p可開啟屬性頁面、Ctrl + C可復製作業等。
* 已改善捲動、在卡片和清單檢視中延遲載入的體驗，以瀏覽大量資產。
* 改善卡片檢視，並支援根據檢視設定而調整不同大小的卡片。
* 改善資產詳細資訊體驗，並能夠檢視、導覽至「上一個」或「下一個」資產，以及資產數目（即流動資產）。

搜尋改進

* 新的「返回搜尋」按鈕，可導覽至搜尋項目，並返回搜尋結果中的相同位置，而不需重新執行搜尋查詢。
* 新的搜尋結果計數，以顯示搜尋結果的數目。
* 改良的檔案類型搜尋篩選功能，可根據細粒度的JPG、PNG和PSD等MIME類型（與先前的影像、檔案、多媒體選項相比）來篩選搜尋結果。
* 改進搜尋篩選器，提供精確的時間戳記，而非先前的時間滑桿功能。

多頁資產改良功能

* 改善多頁資產瀏覽體驗，減少點按次數。
* 改善的註解和註解支援，所有註解都在資產層級而非頁面層級進行整理。

管理工具改進

* 改進「管理工具」中的「中繼資料」、「搜尋」和「報告」的「屬性」選取器，並提前輸入及瀏覽功能以簡化管理體驗。

目錄

* 改善使用者體驗，與範本使用者介面對齊。 如需詳細資訊，請參閱[Catalog Producer](../sites-administering/catalog-producer.md)。

## 中繼資料 {#metadata}

AEM 6.4包含多種進階中繼資料管理功能，可大規模管理中繼資料，並透過規則和驗證強制執行中繼資料完整性。 以下是主要功能：

* 全新大量中繼資料匯出功能，可匯出（全部、選擇性）大量資產的CSV格式中繼資料，以進行編輯、共用和協力廠商整合。
* 全新大量中繼資料匯入功能：匯入CSV檔案以新增中繼資料，一次更新多個資產的現有中繼資料。 此操作是非同步的，不會影響系統效能。 完成後，使用者會透過AEM的Notification系統收到通知。
* 使用中繼資料結構工具建立全新的階層式和內容相關中繼資料。 現在，您可以定義相依性的鏈，以及欄位之間的值映射。 您也可以定義顯示／隱藏中繼資料表單欄位的內容。 這樣，您隨時都只能根據其他欄位中的值顯示相關欄位。

## 報表 {#reports}

AEM 6.4提供大幅的資產報告增強功能：

* 全新的企業層級、可擴充（適用於大型儲存庫）報表架構，套用Sling工作以非同步處理報表請求。 您可以排程特定日期和時間的報表。 您也可以新增自訂欄至報表。
* 新的OOTB報告最常被客戶問及，例如磁碟使用、檔案、連結分享、發佈至品牌入口網站和智慧標籤訓練。
* 新的報表建立和管理UI，提供更精細的選項、存取封存報表的功能、查看報表執行狀態（成功、失敗、佇列等）。

## 品牌入口網站 {#brand-portal}

* **6.3平台升級**:品牌入口網站從AEM 6.0升級至AEM 6.3，並具備新功能和效能改進。
* **平行發佈**:在AEM Assets和品牌入口網站（之前為1個）之間最多可進行複製，這可大幅改善發佈效能
* **架構與搜尋Facet發佈**:能夠將中繼資料結構描述和自訂搜尋刻面發佈至品牌入口網站，以免重複工作。
* **大量標籤發佈**:能夠將分類法（連同階層）發佈至品牌入口網站，以消除工作重複。
* **自行註冊或請求存取**:品牌入口網站的非註冊使用者工作流程。
* **應用程式內（螢幕上）維護通知**:通知會提前顯示，以避免業務中斷。
* **報告改進**:有三份OOTB報告可供使用：下載、發佈和連結分享。
* **DRM限制**:授權資產過期後，就無法再從Brand Portal下載。

## AEM案頭應用程式{#aem-desktop-app}

AEM案頭應用程式已更新至1.8版，與AEM 6.4相容。AEM案頭應用程式的完整變更清單會提供在專屬的[AEM案頭應用程式版本注意事項](https://docs.adobe.com/content/help/zh-Hant/experience-manager-desktop-app/using/release-notes.html)檔案中。\
以下是自AEM 6.3發行以來AEM案頭應用程式摘要清單：

* 能夠在背景上傳階層式資料夾。
* UI可監控背景中的資產上傳。
* 快取改進功能，包括管理快取參數的UI。
* 更廣泛支援AEM驗證設定(SAML/SSO)和網路代理。
* 可支援性：從使用者介面輕鬆存取記錄檔。
* 已改善客戶問題的穩定性和修正。

為了更輕鬆地存取檔案和最佳實務，請提供下列檔案：

* [使用者指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)，針對使用應用程式的使用者。
* [安裝指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/install-upgrade.html)，旨在讓管理員設定AEM和AEM案頭應用程式以搭配運作

## 分層儲存{#tiered-storage}

AEM 6.4包含一組功能，可支援各種分層儲存偏好設定並實作生命週期規則。 儲存選項還支援（但不限於）公共雲- AWS或Azure。

* 用戶可以隨意選擇和以後更改儲存類，並定義將資產從一個類儲存到另一個類的規則，或管理其資產的生命週期。
* 用戶能夠通過選擇不同的AWS或Azure降低儲存成本。

有關受支援平台的概述，請參閱[技術要求文檔](../sites-deploying/technical-requirements.md)。

## 已關閉的使用者群組 {#closed-user-group}

* 在AEM 6.4中，「已關閉使用者群組」或CUG提供一種方式，可限制發佈例項上的資料夾存取權，這是觸控式UI選項，可透過資料夾層級的資料夾屬性頁面新增承擔者，並套用至內部的所有資料夾和子資料夾／資產。
* 在發佈模式中，如果已設定CUG並在資料夾上啟用授權，當使用者嘗試存取資料夾時，會將使用者重新導向至登入頁面。 因此，授權使用者只有在成功登入後，才能存取資料夾及其資產。 因此，CUG會限制內容儲存庫中除選定承擔者外的所有人對給定樹的讀取訪問。

## 動態媒體附加元件{#dynamic-media-add-on}

6.4版動態媒體支援新模式——其中主要資產會透過AEM Assets網頁UI上傳和管理，而動態轉譯和其他動態媒體功能則會由Dynamic Media雲端傳送服務在背景處理。

在此模式中（先隨[AEM 6.3功能套件14410和18912](https://helpx.adobe.com/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)發行推出），使用者可運用現代AEM Assets網頁UI的端對端資產管理和動態媒體功能，並仍可運用向後相容於Dynamic Media Classic(Dynamic Media Classic)的傳送服務(scene7)-包括未變更的傳送URL。

此外，AEM 6.4還推出Adobe Sensei支援的新功能、VR和3D等新興媒體的增強功能、動態媒體檢視器，以及互動式影像和轉盤橫幅中的體驗片段支援。

### 智慧型裁切（由Adobe Sensei提供支援）{#smart-crop-powered-by-adobe-sensei}

* 智慧型裁切會自動提供影像的非破壞性裁切，以保留互動式設計的興趣點。 您可以預覽裁切的建議，並視需要手動調整。
* 此功能也可讓產品影像產生自動色票。 自動產生色票有助於自動將色票、圖樣色票或兩者加入產品影像。

如需詳細資訊，請參閱[影像描述檔](../assets/image-profiles.md)檔案。

另請參閱[新增動態媒體資產至頁面](../assets/adding-dynamic-media-assets-to-pages.md)檔案，以進一步瞭解搭配動態媒體元件使用智慧型裁切。

### 智慧型影像 {#smart-imaging}

* 智慧型影像處理運用每位使用者獨特的檢視特性，自動提供最佳化的影像體驗，進而提供更佳的效能和參與度。
* 影像會根據瀏覽器功能自動轉換為不同的格式。
* 在瀏覽器中分別確定和套用影像品質設定。 此智慧功能可讓有限的頻寬和較慢的連線速度，讓影像載入效能可接受。

請參閱[智慧型影像](../assets/imaging-faq.md)說明檔案以瞭解更多資訊。

### 新興媒體和檢視器增強功能{#emerging-media-amp-viewer-enhancements}

* 支援新的檢視器，為使用者提供更好、如臨現場的體驗。
* 全景檢視器有助於吸引使用者，並提供更佳的房間場景、屬性、位置和風景體驗。 請參閱[全景影像](../assets/panoramic-images.md)檔案以瞭解。

* VR檢視器為屬性、位置和風景提供身歷其境的體驗。
* 針對產品影像最佳化的垂直影像檢視器。
* 鍵盤協助工具改良功能。

### 3D與Dimension CC {#d-and-integration-with-dimension-cc}整合

已引入與[Adobe Dimension CC](https://www.adobe.com/products/dimension.html)的整合，讓3D工作流程更順暢。 如需詳細資訊，請參閱[使用3D資產](../assets/assets-3d.md)檔案。
