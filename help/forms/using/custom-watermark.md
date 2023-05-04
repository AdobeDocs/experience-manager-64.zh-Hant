---
title: 信函PDF預覽中的自訂浮水印
seo-title: Custom watermark in letter PDF preview
description: 了解如何在信函PDF預覽中建立自訂浮水印。
seo-description: Learn how to create custom watermark in letter PDF preview.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
feature: Correspondence Management
exl-id: 8aeabd95-948d-4a54-b593-1eda8ddd731b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# 信函PDF預覽中的自訂浮水印 {#custom-watermark-in-letter-pdf-preview}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

在「建立通信」UI中，代理用戶會以最終形式預覽通信，在該形式下，通信將被發送到後置處理，例如用於電子郵件或打印。

為了防止未授權使用此資料，組織可以在預覽PDF上加上浮水印。 預設水印為「PREVIEW」，會出現在整個PDF。

若要在預覽PDF中啟用浮水印，請選取 **[!UICONTROL 套用浮水印]** 預覽期間選項(在 **[!UICONTROL 通信管理配置]** at `https://[server]:[port]/system/console/configMgr`.

![預設水印](assets/default-watermark.png)

您可以使用下列步驟來自訂浮水印的文字和外觀：

## 在「建立通信UI」的PDF預覽中自訂浮水印 {#customizewatermark-}

1. 前往 `https://[server]:[port]/[ContextPath]/crx/de` 並以管理員身分登入。
1. 在應用程式資料夾中，建立名為 **[!UICONTROL 預覽水印]** 具有與libs資料夾中的previewwatermark資料夾類似的路徑/結構：

   1. 按一下右鍵以下路徑的**previewwatermark **資料夾，然後選擇 **覆蓋節點**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. 確定「覆蓋節點」對話方塊有下列值：

      **路徑：** /libs/fd/cm/configFiles/previewwatermark

      **覆蓋位置：** /apps/

      **匹配節點類型：** 已勾選

      >[!NOTE]
      >
      >請勿在/libs分支中進行變更。 您所做的任何變更都可能會遺失，因為只要您符合以下條件，此分支就會發生變更：
      >
      >* 在您的執行個體上升級
      >* 套用Hotfix
      >* 安裝功能套件


   1. 按一下 **確定** 然後按一下 **全部儲存**. 此 **[!UICONTROL 預覽水印]** 資料夾會建立在指定的路徑中。

1. 從「/libs/fd/cm/configFiles/previewwatermark」資料夾複製ddx檔案並貼到「/apps/fd/cm/configFiles/previewwatermark」資料夾，然後按一下 **[!UICONTROL 全部儲存]**.
1. 在/apps/fd/cm/configFiles/previewwatermark/底下的ddx檔案中進行所需的變更。

   ```
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   有關自定義水印外觀、文本和對齊方式的資訊，請參閱 [組合器服務和DDX參考](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) 檔案。

   >[!NOTE]
   >
   >在ddx檔案中，對結果和來源的參照應保持不變，為output.pdf和input.pdf。 也不應變更檔案ddx的名稱。

1. 按一下 **全部儲存**.
