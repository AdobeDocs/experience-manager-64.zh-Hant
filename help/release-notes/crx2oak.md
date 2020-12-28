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
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# CRX2OAK移轉工具{#crx-oak-migration-tool}

## 變更和修正清單{#list-of-changes-and-fixes}

### 1.8.6（2018年6月）{#june}

* OAK-7339通過引入LoopbackBlobStore，所有修正在MissingBlobStore上與UnsupportedOperationException一起中斷
* 使用Oak 1.8.4

### 1.8.4（2018年4月）{#april}

* 使用Oak 1.8.2版
* GRANITE-18104 Repo從6.3到6.4的遷移錯誤應該更有意義
* GRANITE-16571取代SHA-1的使用

   * 使用—version選項時，工具校驗和現在為SHA-512

* GRANITE-17601在CRX2Oak with oak-blob-cloud中內嵌oak-upgrade
* GRANITE-18553 crx2oak會在節點上保留版本屬性，即使版本未移轉

### 1.6.8版（2017年3月）{#version-march}

* 將Oak版本更新為1.6.1
* CQ-61847將crx2oak-quickstart-extension與crx2oak合併（新增的移轉設定檔）
* CQ-97488升級和刪除AEM執行模式（透過重寫sling.options.file）
* GRANITE-12798/OAK-4260從Oak Segment到Oak Segment Tar的側等能力

### 1.4.2版（2016年3月）{#version-march-1}

* 將Oak版本升級至1.4.1
* OAK-3846 / GRANITE-10748如果SNS節點違反nodetype約束，請重新命名
* OAK-3910 / GRANITE-10730遷移節點繼承自`mix:versionable`，無版本歷史記錄
* OAK-4128 / GRANITE-11757 `RepositorySidegrade`不複製根節點屬性

### 1.3.4版（2016年1月）{#version-january}

* 將Oak版本升級至1.3.16
* OAK-3844 / GRANITE-10730更佳支援不含版本記錄的可轉換節點
* OAK-3846如果SNS節點違反nodetype約束，則重新命名這些節點

### 1.3.2版（2015年12月）{#version-december}

* 將Oak版升級至1.3.12
* 遷移後不應移動資料儲存目錄(GRANITE-10447)
* 將crx2oak-quickstart-extension與crx2oak合併(CQ-61847)
* crx2oak在資料庫中重複值時失敗(CQ-61906)
* 從CQ 5.x移轉後，長AEM開始(GRANITE-10309)
* 在crx2oak中支援多個LDAP伺服器(GRANITE-9917)
* 強制檢查最大節點名稱長度(OAK-3111)
* 支援S3DataSource做為移轉來源(OAK-3685)
