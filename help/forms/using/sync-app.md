---
title: 同步應用程式
seo-title: Synchronizing the app
description: 將行動裝置上的AEM Forms應用程式與AEM Forms伺服器同步。
seo-description: Synchronize the AEM Forms app on your mobile device with the AEM Forms server.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
exl-id: b5681fe5-69ba-4fc0-95e3-6ffdcdd95382
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# 同步應用程式 {#synchronizing-the-app}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 同步應用程式 {#synchronizing-the-app-1}

應用程式中的表單會從AEM Forms伺服器下載。 表單會下載至「工作」和「Forms」標籤下。 從表單建立的草稿會下載到「草稿」標籤中，而從任務建立的草稿則會下載到「任務」標籤中。 若是OSGi伺服器上的獨立表單，表單和草稿會分別在Forms和草稿標籤中下載。

當您完成表單並提交時，如果應用程式上線，表單會立即上傳回AEM Forms伺服器。 應用程式同步時，系統會從伺服器擷取表單。 不過，如果應用程式上線，草稿會立即同步至伺服器。

依預設，當您與AEM Forms伺服器上線時，您的應用程式會每15分鐘同步一次。 但是，您可以選擇更改同步頻率。 或者，您可以隨時手動同步應用程式。

**手動同步應用程式的方式**

點選「同步」按鈕 ![sync-app](assets/sync-app.png) 在主螢幕的右下角。

**更改同步頻率**

1. 若要前往「設定」畫面，請點選「主畫面」左上角的功能表按鈕，然後點選 **設定**.
1. 在「設定」畫面中，點選「一般」標籤。

   ![「常規設定」窗口中的同步頻率設定](assets/gen-settings-1.png)

1. 在「同步頻率」選項上，點選「同步頻率」右側的值。
1. 在下拉式清單中，選取新的同步頻率。

### 技術規格 {#technical-specifications}

* runtime/offline/util/offline.js中包含將離線應用程式資料提交至AEM Forms伺服器的主要邏輯。
* 在.js中，對processOfflineSubmittedSavedTasks(...)函式的調用將已保存/已提交的任務發送到伺服器。 它也可處理同步過程中的任何錯誤或衝突。 如果提交任務失敗，應用程式上的任務會標示為失敗。 此外，任務仍保留在您的發件箱中。
* syncSubmittedTask()和syncSavedTask()函式對單個任務執行操作。
* 當用戶選擇將離線狀態同步到伺服器或由後台線程自動同步後，任務清單元件將啟動對processOfflineSubmittedSavedTasks()函式的調用。
