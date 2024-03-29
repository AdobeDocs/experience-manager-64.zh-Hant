---
title: 品牌自訂
seo-title: Branding Customization
description: 自訂應用程式圖示、應用程式名稱、啟動影像和登入頁面，為AEM Forms應用程式提供獨特的組織專屬外觀和風格。
seo-description: Customize the application icon, application name, launch images, and login page to provide a distinct organization-specific look and feel to AEM Forms app.
uuid: fece0fa8-c417-45eb-93f1-a91b49835fa0
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: f6440a36-719a-4f89-b7db-1af918a3469a
exl-id: 5c5cdfe6-37f2-45c7-b679-23e3592842b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 2%

---

# 品牌自訂 {#branding-customization}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以自訂應用程式圖示、應用程式名稱、啟動影像和登入頁面，為AEM Forms應用程式提供組織專屬的不同外觀。 例如，您可以變更影像以使用貴組織的標誌。 AEM Forms應用程式支援下列自訂：

* 自訂應用程式圖示和啟動影像
* 自訂應用程式名稱
* 在登入頁面上自訂影像
* 自訂應用程式選單中的標誌

## 自訂圖示和啟動影像 {#customizing-icon-and-launch-images}

執行下列步驟來自訂AEM Forms應用程式的預設應用程式圖示和啟動影像：

>[!NOTE]
>
>對於所有表徵圖和影像，請使用非隔行掃描的PNG格式。

### 若要自訂圖示和啟動影像 {#to-customize-icon-and-launch-images}

#### 針對iOS {#for-ios}

1. 開啟 `Capture.xcodeproj` 專案。
1. (***自訂圖示***)在捕獲的導航器視圖中，導航到 **[!UICONTROL 「捕獲」>「捕獲」>「支援檔案」>「捕獲 — info.plist」]**. 按一下圖示檔案旁的下拉式清單。 指定圖示檔案的名稱(.png)，並在上傳檔案 **[!UICONTROL 捕獲>捕獲>資源>表徵圖]**. 目前支援的維度為：29x29、50x50、58x58、72x72、100x100和144x144。
1. (***自訂啟動影像***)確認影像的檔案名稱為：

   * 縱向： `Default-Portrait~ipad.png` 和 `Default-Portrait@2x~ipad.png`
   * 橫向： `Default-Landscape~ipad.png` 和 `Default-Landscape@2x~ipad.png`

   將它們上傳到捕獲項目以替換項目中的現有檔案。

   >[!NOTE]
   >
   >確定影像的名稱和解析度符合您在專案中取代的影像。

1. 在iOS裝置或iOS模擬器上建立及執行AEM Forms應用程式。

#### 適用於Android {#for-android}

1. 將應用程式表徵圖檔案命名為：

   `ic_launcher.png`

1. 將對應的表徵圖檔案放置在以下目錄中：

   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-hdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-mdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xhdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xxhdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xxxhdpi`

   >[!NOTE]
   >
   >確定影像的名稱和解析度符合您在專案中取代的影像。

1. 重建AEM Forms應用程式。

### Windows版 {#for-windows}

1. 取代路徑中的圖示：

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\icons\windows`

1. 替換路徑中的啟動器映像：

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\screens\windows`

   >[!NOTE]
   >
   >確定影像的名稱和解析度符合您在專案中取代的影像。

1. 重建AEM Forms應用程式。

## 自訂應用程式名稱 {#customize-the-app-name}

### 針對iOS {#for-ios-1}

1. 開啟 `Capture.xcodeproj` 專案。
1. 在捕獲的導航視圖中，導航到 **[!UICONTROL 「捕獲」>「捕獲」>「支援檔案」>「InfoPlist.strings」]**.

   更新 `CFBundleDisplayName` 屬性，以顯示您要為應用程式顯示的名稱。

1. 在iOS裝置或iOS模擬器上建立及執行AEM Forms應用程式。

   如需建立iOS應用程式的詳細資訊，請參閱 [設定Xcode專案並建置iOS應用程式](/help/forms/using/setup-xcode-project-build-installer.md).

### 適用於Android {#for-android-1}

1. 在任何文本或Xml編輯器中開啟以下Xml:

   `[User_Home]/Projects/[your-project]/src/android/res/values/strings.xml and android/res/values-en/strings.xml`

1. 更新索引鍵的值 `app_name`.
1. 重建AEM Forms應用程式。

   如需建立Android適用應用程式的詳細資訊，請參閱 [設定Eclipse專案並建置Android應用程式](/help/forms/using/setup-eclipse-project-build-installer.md).

### Windows版 {#for-windows-1}

1. 在任何文字編輯器中開啟下列Xml:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\config.xml`

1. 更新 `<name>...</name>` 標籤。
1. 重建AEM Forms應用程式。

   有關構建Windows應用程式的詳細資訊，請參閱 [設定Visual Studio項目並構建Windows應用程式](/help/forms/using/setup-visual-studio-project-build-installer.md).

## 在登入頁面上自訂影像 {#customizing-images-on-the-login-page}

AEM Forms應用程式的登入頁面有標誌和背景影像。 徽標位於登錄對話框的上方，而背景影像位於登錄對話框的下方。 執行下列步驟來自訂登入頁面上的預設影像：

**開始之前**

請確定您有下列影像：

<table> 
 <tbody> 
  <tr> 
   <th><p>說明</p> </th> 
   <th><p>大小</p> </th> 
   <th><p>檔案名稱</p> </th> 
  </tr> 
  <tr> 
   <td><p>標誌</p> </td> 
   <td><p>72 x 72像素</p> </td> 
   <td><p>LC-logo.png</p> </td> 
  </tr> 
  <tr> 
   <td><p>背景影像（縱向）</p> </td> 
   <td><p>1280 x 989像素</p> </td> 
   <td><p>Landing_bg.jpeg</p> </td> 
  </tr> 
 </tbody> 
</table>

**使用Xcode自訂登入頁面上的影像**

1. 開啟 `Capture.xcodeproj` 專案。

1. 導覽至 `www/wsmobile/images`檔案夾。
1. 要更改徽標，請替換預設 `LC-logo.png` 檔案(含自訂 `LC-logo.png` 檔案。
1. 若要變更背景，請取代預設值 `Landing_bg.jpeg` 檔案(含自訂 `Landing_bg.jpeg`檔案。
1. 在iOS裝置或iOS模擬器上建立及執行AEM Forms應用程式。

### 使用Eclipse自訂登入頁面上的影像 {#to-customize-images-on-the-login-pages-using-eclipse}

1. 在Eclipse中開啟Android專案。

1. 導覽至 `assets/www/wsmobile/images`檔案夾。
1. 要更改徽標，請替換預設 `LC-logo.png` 檔案(含自訂 `LC-logo.png` 檔案。
1. 若要變更背景，請取代預設值 `Landing_bg.jpeg` 檔案(含自訂 `Landing_bg.jpeg`檔案。
1. 在Android裝置上建立及執行AEM Forms應用程式。

### 使用Visual Studio自定義登錄頁上的影像 {#to-customize-images-on-the-login-pages-using-visual-studio}

1. 開啟 `MWSWindows.sln` 專案。

1. 導覽至 `MWSWindows\www\wsmobile\images`檔案夾。
1. 要更改徽標，請替換預設 `LC-logo.png` 檔案(含自訂 `LC-logo.png` 檔案。
1. 若要變更背景，請取代預設值 `Landing_bg.jpeg` 檔案(含自訂 `Landing_bg.jpeg`檔案。
1. 在Windows裝置上建立及執行AEM Forms應用程式。

## 自訂應用程式選單中的標誌 {#customizing_images_on_the_login_page-1}

登入AEM Forms應用程式並點選功能表按鈕後，您會在功能表上方看到標誌。 執行下列步驟來自訂預設標誌：

**開始之前**

確定您有下列影像：

<table> 
 <tbody> 
  <tr> 
   <th><p>說明</p> </th> 
   <th><p>大小</p> </th> 
   <th><p>檔案名稱</p> </th> 
  </tr> 
  <tr> 
   <td><p>標誌</p> </td> 
   <td><p>72 x 72像素</p> </td> 
   <td><p>aem_icon.png</p> </td> 
  </tr> 
 </tbody> 
</table>

**使用Xcode自訂登入頁面上的影像**

1. 開啟 `Capture.xcodeproj` 專案。

1. 導覽至 `www/wsmobile/images`檔案夾。
1. 若要變更標誌，請取代預設 `aem_icon.png` 檔案(含自訂 `aem_icon.png` 檔案。
1. 在iOS裝置或iOS模擬器上建立及執行AEM Forms應用程式。

### 使用Eclipse自訂登入頁面上的影像 {#to-customize-images-on-the-login-pages-using-eclipse-1}

1. 在Eclipse中開啟Android專案。

1. 導覽至 `assets/www/wsmobile/images`檔案夾。
1. 若要變更標誌，請取代預設 `aem_icon.png` 檔案(含自訂 `aem_icon.png` 檔案。
1. 在Android裝置上建立及執行AEM Forms應用程式。

### 使用Visual Studio自定義登錄頁上的影像 {#to-customize-images-on-the-login-pages-using-visual-studio-1}

1. 開啟 `MWSWindows.sln` 專案。

1. 導覽至 `MWSWindows\www\wsmobile\images`檔案夾。
1. 若要變更標誌，請取代預設 `aem_icon.png` 檔案(含自訂 `aem_icon.png` 檔案。
1. 在Windows裝置上建立及執行AEM Forms應用程式。
