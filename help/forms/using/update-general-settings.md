---
title: 更新一般設定
seo-title: Updating general settings
description: 更新AEM Forms應用程式設定（例如首頁畫面），並擷取起始點和附件選項
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
exl-id: 5ca6212f-d3c7-4239-beba-9a0bdac4b1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 2%

---

# 更新一般設定 {#updating-general-settings}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Forms應用程式的一般設定可讓您指定設定，例如擷取附件、離線模式、登陸畫面、預設類別及自動儲存頻率。

## 更新應用程式中的一般設定 {#working-with-the-form}

當您將應用程式與AEM Forms伺服器同步時，所有表單和定義的工作都會下載至您的行動裝置。

現成可用的AEM Forms應用程式解決方案不會在您的應用程式同步時下載與每個表單相關聯的附件。

在「常規」頁簽中，更改下載附件、離線模式、登錄螢幕、自動保存和同步設定。 您可以變更 [主畫面](/help/forms/using/home-screen.md) 應用程式中。

**導覽至「設定」畫面上的「一般」標籤**

1. 若要前往「設定」畫面，請點選「主畫面」左上角的「功能表」按鈕，然後點選 **設定**.
1. 在「設定」畫面中，點選「一般」標籤。

   ![AEM Forms應用程式中的一般設定](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >選項在不同行動裝置上的顯示可能不同。

### 一般設定 {#general-settings}

您可以對應用程式的設定進行下列變更。

* **擷取任務附件**:指定在每個任務下載到您的應用程式時是否下載相關附件。

* **離線模式**:啟用或停用AEM Forms應用程式的離線服務。 請參閱 [在離線模式下工作](/help/forms/using/work-offline-mode.md) 以取得詳細資訊。

* **登陸畫面**:若要設定開始位置([主畫面](/help/forms/using/home-screen.md))。

   可用選項：

   * Forms
   * 任務
   * 我的最愛

* **預設類別**:可讓您選取要在主畫面中顯示的表單類別。 選取「全部」時，您可以在主畫面中看到所有表單。 系統會根據應用程式中載入的表單來填入類別。 Forms可根據AEM Forms伺服器中指定的表單設定，在應用程式中使用。

* **自動儲存頻率**:設定 [行動應用程式儲存表單資料](/help/forms/using/autosave-data-app.md) 本地。

* **同步頻率**:設定 [行動應用程式已同步](/help/forms/using/sync-app.md) 使AEM Forms伺服器處於聯機模式。

**清除本地資料**:清除資料庫，包括設備中所有用戶的設定和本地資料以及檔案儲存。

>[!NOTE]
>
>清除快取會立即將您登出應用程式。
>
>但系統會提示您確認清除快取操作。
