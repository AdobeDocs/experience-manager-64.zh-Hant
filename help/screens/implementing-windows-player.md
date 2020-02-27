---
title: 實作Windows 10 Player
seo-title: 實作Windows 10 Player
description: '請依照本頁來瞭解如何設定AEM Screens Windows 10播放器。 '
seo-description: '請依照本頁來瞭解如何設定AEM Screens Windows 10播放器。 '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# 實作Windows 10 Player{#implementing-windows-player}

本節說明如何設定AEM Screens Windows 10播放器。 它提供設定檔、可用選項和建議的資訊，說明要用於開發和測試的設定。

## 安裝Windows Player {#installing-windows-player}

若要實作適用於AEM畫面的Windows Player，請安裝適用於AEM畫面的Windows Player。

請造訪 [**AEM 6.4播放器下載頁面&#x200B;**](https://download.macromedia.com/screens/)。

### 臨機方法 {#ad-hoc-method}

安裝最新Windows Player(*.exe*)的臨機方法，請造 [**訪AEM 6.4 Player下載頁面&#x200B;**](https://download.macromedia.com/screens/)。

下載應用程式後，請依照播放器上的步驟完成臨機安裝：

1. 長按左上角以開啟管理面板。
1. 從左 **側動作功能表導覽至** 「設定」，然後輸入您要連線至的AEM例項的位置（位址），然後按一下「 **儲存」**。

1. 按一下左 **側動作功能表** 中的「註冊」連結，以完成裝置註冊程式。

### 使用一個配置註冊多個Windows 10播放器 {#registering-multiple-windows-players-with-one-configuration}

在安裝Windows播放器後，您可以使用一個配置註冊多個播放器。

>[!NOTE]
>
>**Windows Player大量註冊**
>
>實作Windows播放器時，您不需要手動設定每個播放器。 您可以在設定JSON檔案經過測試並準備好進行部署後，再加以更新。
>
>配置將確保所有播放器ping配置檔案中提供的同一伺服器。 您仍必須手動註冊每個播放器。

請依照下列步驟來設定Windows 10 Player:

1. 安裝Windows Player。
1. 在 ***%appdata%\com.adobe.aem.screens.player\config.json下尋找設定檔案***。
1. 使用下列資訊更新設定JSON，然後將相同資料夾複製到播放器所在的所有系統。

### 策略屬性 {#policy-attributes}

下表匯總了策略屬性，其中包含範例策略JSON以供參考：

| **原則名稱** | **目的** |
|---|---|
| 伺服器 | Adobe Experience Manager(AEM)伺服器的URL。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI以在網站上設定裝置。 在完全設定並投入生產時，設為false。 |
| enableOSD | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定後，請考慮在生產中設定為false。 |
| enableActivityUI | 啟用以顯示活動的進度，例如下載和同步。 啟用疑難排解功能，並在完全設定後在生產中停用。 |

#### 範例原則JSON檔案 {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

