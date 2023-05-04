---
title: 頁面匯出工具
seo-title: The Page Exporter
description: 了解如何使用AEM Page Exporter。
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# 頁面匯出工具{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM可讓您將頁面匯出為完整的網頁，包含影像、.js和.css檔案。

匯出設定完成後，您只需取代 `html` with `export.zip` 會在URL中取得zip檔案下載，其中包含html格式的轉譯頁面和參考的資產。 頁面中的所有路徑（例如影像路徑）都會重寫，以指向zip檔案中包含的檔案或伺服器上的資源。

## 匯出頁面 {#exporting-a-page}

下列步驟說明如何匯出頁面，並假設您的網站有匯出設定範本。 組態範本定義頁面的匯出方式，且是您網站專屬的。 若要建立設定範本，請參閱 [為您的網站建立頁面匯出工具組態](#creating-a-page-exporter-configuration-for-your-site) 區段。

要導出頁面，請執行以下操作：

1. 在瀏覽器中，開啟頁面。 例如：
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. 開啟頁面屬性對話方塊，選取 **進階** 標籤，然後展開 **匯出** 欄位集。

1. 按一下放大鏡圖示並選取設定範本。 選取 **geometrixx** 範本，因為這是Geometrixx網站的預設範本。 按一下&#x200B;**「確定」**。

1. 按一下 **確定** 以關閉頁面屬性對話方塊。
1. 以取代 `html` with `export.zip` 中。

1. 下載 `<page-name>.export.zip` 檔案傳送至您的檔案系統。

1. 在您的檔案系統中，將檔案解壓縮：

   * 頁面html檔案( `<page-name>.html`)在下方可用 `<unzip-dir>/<page-path>`
   * 其他資源（.js檔案、.css檔案、影像、...）是根據匯出範本中的設定而找到。 在此範例中，有些資源如下 `<unzip-dir>/etc`，部分在下方 `<unzip-dir>/<page-path>`.

1. 開啟頁面html檔案( `<unzip-dir>/<page-path>.html`)以檢查呈現。

## 為您的網站建立頁面匯出工具組態 {#creating-a-page-exporter-configuration-for-your-site}

頁面匯出器以內容同步架構為基礎。 頁面屬性對話方塊中可用的設定為設定範本。 它們定義了頁面的所有必要相依性。 觸發頁面匯出時，會使用設定範本，並動態地將頁面路徑和設計路徑套用至設定。 然後會使用標準的「內容同步」功能來建立zip檔案。

AEM內嵌一些範本，包括：

* 預設值為 `/etc/contentsync/templates/default`. 此範本：

   * 在存放庫中找不到設定範本時，即為後援範本。
   * 可作為新配置模板的基礎。

* 專用於 **Geometrixx** 網站，在 `/etc/contentsync/templates/geometrixx`. 此範本可作為建立新範本的範例。

要建立頁面導出器配置模板，請執行以下操作：

1. 在 **CRXDE Lite**，請在下方建立節點 `/etc/contentsync/templates`:

   * 名稱：例如 `mysite`. 選擇頁面導出器模板時，該名稱將出現在頁面屬性對話框中。
   * 類型: `nt:unstructured`

1. 在範本節點下方，在此處呼叫 `mysite`，請使用下述設定節點建立節點結構。

### 頁面導出器配置節點 {#page-exporter-configuration-nodes}

配置模板由節點結構組成。 每個節點都有 `type` 定義zip檔案建立程式中特定動作的屬性。 有關類型屬性的詳細資訊，請參閱內容同步架構頁面中的配置類型概述部分。

以下節點可用於構建導出配置模板：

**頁面節點** 頁面節點可用來將頁面html複製到zip檔案。 其特點如下：

* 是強制節點。
* 位於下方 `/etc/contentsync/templates/<sitename>`.
* 其名稱為 `page`.
* 其節點類型為 `nt:unstructured`

此 `page` 節點具有以下屬性：

* A `type` 以值設定的屬性 `pages`.

* 沒有 `path` 屬性，因為目前頁面路徑會動態複製到設定。

* 其他屬性在內容同步架構的「設定類型概觀」一節中有說明。

**重寫節點** 重寫節點定義如何在匯出的頁面中重寫連結。 重寫的連結可以指向zip檔案中包含的檔案或指向伺服器上的資源。

請參閱內容同步頁面，以取得 `rewrite` 節點。

**設計節點** 設計節點用於複製用於導出頁面的設計。 其特點如下：

* 為選用。
* 位於下方 `/etc/contentsync/templates/<sitename>`.
* 其名稱為 `design`.
* 其節點類型為 `nt:unstructured`.

此 `design` 節點具有以下屬性：

* A `type` 屬性設為值 `copy`.

* 沒有 `path` 屬性，因為目前頁面路徑會動態複製到設定。

**一般節點** 一般節點可用來將clientlibs .js或.css檔案等資源複製到zip檔案。 其特點如下：

* 為選用。
* 位於下方 `/etc/contentsync/templates/<sitename>`.
* 沒有特定名稱。
* 其節點類型為 `nt:unstructured`.
* 有 `type` 屬性和任何 `type` 在內容同步框架的「配置類型概述」部分中定義的相關屬性。

例如，下列設定節點會將geometrixx clientlibs .js檔案複製到zip檔案：

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

此 **Geometrixx** 頁面匯出設定範本會顯示如何設定頁面匯出。 若要以json格式檢視瀏覽器中範本的節點結構，請要求下列URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**實作自訂設定**

如您在節點結構中所注意， **Geometrixx** 頁面匯出組態範本有 `logo` 節點 `type` 屬性設定為 `image`. 這是已建立的特殊組態類型，可將影像標誌複製至zip檔案。 為符合某些特定需求，您可能需要實作自訂 `type` 屬性：若要這麼做，請參閱「內容同步」頁面中的「實作自訂更新處理常式」區段。

## 以程式設計方式匯出頁面 {#programmatically-exporting-a-page}

若要以程式設計方式匯出頁面，您可以使用 [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI服務。 此服務可讓您：

* 匯出頁面並寫入HTTP servlet回應。
* 匯出頁面並在特定位置儲存zip檔案。

系結至 `export` 選取器和 `zip` 擴充功能使用PageExporter服務。

## 疑難排解 {#troubleshooting}

如果您在下載zip檔案時遇到問題，可以刪除 `/var/contentsync` 節點，並再次傳送匯出請求。
