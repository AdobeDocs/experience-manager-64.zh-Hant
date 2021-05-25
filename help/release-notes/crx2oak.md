---
title: CRX2OAK移轉工具
seo-title: CRX2OAK移轉工具
description: Adobe Experience Manager 6.4 CRX2OAK移轉工具的發行說明。
seo-description: Adobe Experience Manager 6.4 CRX2OAK移轉工具的發行說明。
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
exl-id: 441c8ba0-f8b2-4c2c-b7be-cfdad9e1e498
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# CRX2OAK遷移工具{#crx-oak-migration-tool}

## 變更和修正清單{#list-of-changes-and-fixes}

### 1.8.6（2018年6月） {#june}

* OAK-7339修正因引入LoopbackBlobStore而在MissingBlobStore上因UnsupportedOperationException而失效
* 使用Oak 1.8.4

### 1.8.4（2018年4月） {#april}

* 使用Oak 1.8.2版
* GRANITE-18104 Repo從6.3移轉至6.4的錯誤應該更有意義
* GRANITE-16571取代SHA-1的使用

   * 使用 — version選項時，工具檢查加總現在為SHA-512

* GRANITE-17601在CRX2Oak中使用oak-blob-cloud中內嵌oak-upgrade
* GRANITE-18553 crx2oak會在節點上保留版本屬性，即使版本未移轉亦然

### 版本1.6.8（2017年3月）{#version-march}

* 將Oak版本更新至1.6.1
* CQ-61847將crx2oak-quickstart-extension與crx2oak合併（新增移轉設定檔）
* CQ-97488提升和刪除AEM執行模式（透過重新寫入sling.options.file）
* GRANITE-12798/OAK-4260將等級從Oak Segment側分至Oak Segment Tar

### 版本1.4.2（2016年3月）{#version-march-1}

* 將Oak版本升級至1.4.1
* OAK-3846 / GRANITE-10748如果SNS節點違反nodetype限制，請重新命名
* OAK-3910 / GRANITE-10730移轉節點繼承自`mix:versionable`，不含版本記錄
* OAK-4128 / GRANITE-11757 `RepositorySidegrade`未複製根節點屬性

### 版本1.3.4（2016年1月）{#version-january}

* 將Oak版本升級至1.3.16
* OAK-3844 / GRANITE-10730針對沒有版本記錄的可轉換節點提供更佳支援
* OAK-3846如果SNS節點違反nodetype約束，則更名SNS節點

### 版本1.3.2（2015年12月）{#version-december}

* 將Oak版本升級至1.3.12
* 移轉後不應移動資料存放區目錄(GRANITE-10447)
* 將crx2oak-quickstart-extension與crx2oak合併(CQ-61847)
* crx2oak在存放庫中重複值時失敗(CQ-61906)
* 從CQ 5.x移轉後開始的AEM長時間(GRANITE-10309)
* 在crx2oak中支援多個LDAP伺服器(GRANITE-9917)
* 強制檢查最大節點名稱長度(OAK-3111)
* 支援以S3DataSource作為移轉來源(OAK-3685)
