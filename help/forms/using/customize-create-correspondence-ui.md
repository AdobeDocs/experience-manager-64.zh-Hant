---
title: 自訂建立通信UI
seo-title: 自訂建立通信UI
description: 了解如何自訂建立通信UI。
seo-description: 了解如何自訂建立通信UI。
uuid: 5b6eb8fd-0270-4638-bdf4-cb7015919d57
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 3efd8f5a-9f38-4d9b-88d6-d8fde6c9a644
feature: 通信管理
exl-id: 63cd01d2-a0d5-4f85-b9d2-ec3007ce3fa9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 0%

---

# 自定義建立通信UI {#customize-create-correspondence-ui}

## 概覽 {#overview}

通信管理可讓您重新品牌化其解決方案範本，以提升品牌價值，並符合貴組織的品牌標準。 品牌化使用者介面包括變更組織標誌，該標誌會顯示在「建立通信UI」的左上角。

您可以使用組織的標誌來變更「建立通信UI」中的標誌。

![建立通信UIFigure中的自](assets/0_1_introscreenshot.png)
**訂圖示：** *建立通信UI中的自訂圖示*

### 更改建立通信UI {#changing-the-logo-in-the-create-correspondence-ui}中的徽標

若要設定您所選擇的標誌影像，請執行下列操作：

1. 在CRX](#creatingfolderstructure)中建立適當的[資料夾結構。
1. [在您在CRX中](#uploadlogo) 建立的資料夾中上傳新的標誌檔案。

1. [在CRX上](#createcss) 設定CSS以參照新標誌。
1. 清除瀏覽器歷史記錄，然後[重新整理「建立通信UI」](#refreshccrui)。

## 建立所需的資料夾結構 {#creatingfolderstructure}

建立資料夾結構（如下所述），用於托管自定義徽標影像和樣式表。 根資料夾/apps的新資料夾結構與/libs資料夾的結構類似。

對於任何自訂，請在/apps分支中建立平行資料夾結構，如下所述。

/apps分支（資料夾結構）:

* 確保檔案安全，以防系統更新。 若是升級、功能套件或Hotfix，則會更新/libs分支，而如果您將變更托管於/libs分支，則會覆寫變更。
* 幫助您不打擾當前的系統/分支，如果使用預設位置來儲存自定義檔案，則可能會錯誤地解決該問題。
* 當AEM搜尋資源時，可協助您的資源獲得較高的優先順序。 AEM設定為先搜尋/apps分支，再搜尋/libs分支以尋找資源。 此機制表示系統會使用您的覆蓋（以及那裡定義的自訂）。

使用下列步驟在/apps分支中建立所需的資料夾結構：

1. 前往`https://[server]:[port]/[ContextPath]/crx/de`並以管理員身分登入。
1. 在應用程式資料夾中，建立名為`css`的資料夾，其路徑/結構類似於css資料夾（位於ccrui資料夾中）。

   建立CSS資料夾的步驟：

   1. 按一下右鍵以下路徑的&#x200B;**css**&#x200B;資料夾，然後選擇&#x200B;**覆蓋節點**:`/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css`

      ![覆蓋節點](assets/1_overlaynode_css.png)

   1. 確定「覆蓋節點」對話方塊有下列值：

      **路徑：** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css

      **覆蓋位置：** /apps/

      **匹配節點類型：已** 勾選

      ![覆蓋節點路徑](assets/0_1_5ioverlaynodedialog.png)

      >[!NOTE]
      >
      >請勿在/libs分支中進行變更。 您所做的任何變更都可能會遺失，因為只要您符合以下條件，此分支就會發生變更：
      >
      >* 在您的執行個體上升級
      >* 套用Hotfix
      >* 安裝功能套件


   1. 按一下&#x200B;**「確定」**。css資料夾會建立在指定的路徑中。

1. 在應用程式資料夾中，建立名為`imgs`的資料夾，其路徑/結構類似於imgs資料夾（位於ccrui資料夾中）。

   1. 按一下右鍵以下路徑的&#x200B;**imgs**&#x200B;資料夾，然後選擇&#x200B;**覆蓋節點**:`/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs`
   1. 確定「覆蓋節點」對話方塊有下列值：

      **路徑：** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs

      **覆蓋位置：** /apps/

      **匹配節點類型：已** 勾選

   1. 按一下&#x200B;**「確定」**。

      >[!NOTE]
      >
      >您也可以手動在/apps資料夾中建立資料夾結構。

1. 按一下「**全部保存」以在伺服器上保存更改。**

## 將新標誌上傳至CRX {#uploadlogo}

將自訂標誌檔案上傳至CRX。 標準HTML規則控管標誌的轉譯。 支援的影像檔案格式會根據您用來存取AEM Forms的瀏覽器而定。 所有瀏覽器都支援JPEG、GIF和PNG。 如需詳細資訊，請參閱支援影像格式的瀏覽器專屬檔案。

* 標誌影像的預設尺寸為48 px &amp;ast;48 px. 請確定您的影像類似此大小或大於48 px &amp;ast;48 px.
* 如果標誌影像的高度超過50像素，「建立通信」使用者介面會將影像縮小至最大50像素的高度，因為這是標題的高度。 縮小影像時，「建立通信」使用者介面會維護影像的外觀比例。
* 如果影像較小，「建立通信用戶介面」不會放大影像，因此請確定您使用的徽標影像的高度至少為48像素，寬度足夠清晰。

使用下列步驟將自訂標誌檔案上傳至CRX:

1. 前往 `https://[server]:[port]/[contextpath]/crx/de`. 如有必要，請以管理員身分登入。
1. 在CRXDE中，按一下右鍵以下路徑的&#x200B;**imgs**&#x200B;資料夾，然後選擇&#x200B;**建立>建立檔案**:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs/`

   ![在imgs資料夾中建立新節點](assets/2_contentexplorernewnode.png)

1. 在「建立檔案」對話框中，輸入檔案名為CustomLogo.png（或徽標檔案的名稱）。

   ![CustomLogo.png作為新節點](assets/3_contentexplorernewnode_customlogo.png)

1. 按一下「**全部保存**」。

   在您建立的新檔案（此處為CustomLogo.png）下，jcr:content屬性隨即顯示。

1. 在資料夾結構中按一下jcr:content。

   jcr:content的屬性隨即出現。

   ![jcrcontentpropertys](assets/jcrcontentproperties.png)

1. 連按兩下&#x200B;**jcr:data**&#x200B;屬性。

   將出現「編輯jcr:data」對話框。

   現在，按一下newlogo.png資料夾，按兩下jcr:content（dim選項）並設定nt:resource類型。 如果不存在，請建立名為jcr:content的屬性。

1. 在「編輯jcr:data」對話方塊中，按一下「**瀏覽**」 ，然後選取您要作為標誌的影像檔案（此處為CustomLogo.png）。

   支援的影像檔案格式會根據您用來存取AEM Forms的瀏覽器而定。 所有瀏覽器都支援JPEG、GIF和PNG。 如需詳細資訊，請參閱支援影像格式的瀏覽器專屬檔案。

   ![自訂標誌檔案範例](assets/geometrixx-outdoors.png)
   **圖：** *範例 — 要用作自訂標誌的CustomLogo.png*

1. 按一下「**全部保存**」。

## 建立CSS以整合標誌與UI {#createcss}

自訂標誌影像需要在內容內容中載入額外的樣式表。

使用下列步驟來設定樣式表以呈現標誌：

1. 前往 `https://[server]:[port]/[contextpath]/crx/de`. 如有必要，請以管理員身分登入。
1. 在以下位置建立名為customcss.css的檔案（不能使用其他檔案名）:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css/`

   建立customcss.css檔案的步驟：

   1. 按一下右鍵&#x200B;**css**&#x200B;資料夾，然後選擇&#x200B;**建立>建立檔案**。
   1. 在「新建檔案」對話框中，將CSS的名稱指定為`customcss.css`（不能使用其他檔案名），然後按一下「**確定**」。
   1. 將下列程式碼新增至新建立的css檔案。 在程式碼的content:url中，指定您已上傳至CRXDE中Imgs資料夾的影像名稱。

      ```css
      .logo, .logo:after {
      content:url("../imgs/CustomLogo.png");
      }
      ```

   1. 按一下「**全部保存**」。

## 重新整理「建立通信UI」以查看自訂標誌 {#refreshccrui}

清除瀏覽器快取，然後在瀏覽器中開啟「建立通信UI」例項。 您應該會看到自訂標誌。

![使用自訂標誌建立通信用](assets/0_1_introscreenshot-1.png)
**戶介面圖** *：「建立通信UI」中的自訂表徵圖*
