---
title: 使用記錄檔
seo-title: 使用記錄檔
description: 了解如何使用記錄檔來疑難排解AEM。
seo-description: 了解如何使用記錄檔來疑難排解AEM。
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 3%

---

# 使用日誌{#working-with-logs}

本節包含可協助您進行疑難排解之記錄的詳細資訊。

CRX記錄詳細記錄。 開啟快速入門程式後，您可以在以下位置找到日誌：

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## 啟用DEBUG日誌級別{#activating-the-debug-log-level}

預設日誌級別為INFO，即未記錄DEBUG消息。

若要啟用DEBUG記錄層級，請使用CRX總管來設定

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

要除錯的屬性。 請勿將記錄檔保留在DEBUG記錄層級，因為它會產生許多記錄檔。

除錯檔案中的一行通常以DEBUG開頭，然後提供記錄層級、安裝程式動作和記錄訊息。 例如：

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

記錄層級如下：

| 0 | 錯誤 | 操作失敗，安裝程式無法繼續。 |
|---|---|---|
| 1 | 錯誤 | 操作失敗。 安裝繼續，但CRX的一部分未正確安裝，因此無法正常工作。 |
| 2 | 警告 | 操作已成功，但遇到問題。 CRX可能或無法正常運作。 |
| 3 | 資訊 | 操作成功。 |

## 用於{#verbose-option-used-for-troubleshooting}故障排除的詳細選項

啟動CRX時，可以將 — v(verbose)選項添加到命令行，如下所示：&quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

使用詳細選項進行故障排除，因為此選項在控制台上顯示一些快速啟動日誌輸出。
