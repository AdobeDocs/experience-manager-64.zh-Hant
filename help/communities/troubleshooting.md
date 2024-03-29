---
title: 疑難排解
seo-title: Troubleshooting
description: 疑難排解社群，包括已知問題
seo-description: Troubleshooting Community including Known Issues
uuid: 99225430-fa2a-4393-ae5a-18b19541c358
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cdb2d80a-2fbf-4ee6-b89b-b5d74e6d3bfc
exl-id: 1a1de20d-53f6-4787-92e3-e12f30d925d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 2%

---

# 疑難排解 {#troubleshooting}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本節包含常見問題和已知問題。

## 已知問題 {#known-issues}

### Dispatcher重新擷取失敗 {#dispatcher-refetch-fails}

將Dispatcher 4.1.5與較新版本的Jetty搭配使用時，重新擷取可能會在等候請求逾時後，導致「無法從遠端伺服器接收回應」。

使用Dispatcher 4.1.6或更新版本將可解決此問題。

### 從CQ 5.4升級後無法存取論壇貼文 {#cannot-access-forum-post-after-upgrading-from-cq}

如果論壇是在CQ 5.4上建立且張貼的主題，然後網站升級至AEM 5.6.1或更新版本，嘗試檢視現有貼文可能會導致頁面錯誤：

非法模式字元&#39;a&#39;\
無法在此伺服器上向/content/demoforums/forum-test.html提供請求

而記錄檔包含下列內容：

```xml
20.03.2014 22:49:35.805 ERROR [10.177.45.32 [1395380975744] GET /content/demoforums/forum-test.html HTTP/1.1] com.day.cq.wcm.tags.IncludeTag Error while executing script content.jsp
org.apache.sling.api.scripting.ScriptEvaluationException: 
at org.apache.sling.scripting.core.impl.DefaultSlingScript.call(DefaultSlingScript.java:388)
at org.apache.sling.scripting.core.impl.DefaultSlingScript.eval(DefaultSlingScript.java:171)
```

問題是com.day.cq.commons.date.RelativeTimeFormat的格式字串在5.4和5.5之間更改，以便不再接受&quot;ago&quot;的&quot;a&quot;。

因此，使用RelativeTimeFormat()API的任何程式碼都需要變更

* 從: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r a", resourceBundle);`
* 至: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r", resourceBundle);`

製作和發佈時失敗不同。 在製作時，會以靜默方式失敗，而只是不顯示論壇主題。 發佈時，會在頁面上擲回錯誤。

請參閱 [com.day.cq.commons.date.RelativeTimeFormat](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/date/RelativeTimeFormat.html) API以取得詳細資訊。

## 共同關注 {#common-concerns}

### 記錄中的警告：已棄用Handlebars {#warning-in-logs-handlebars-deprecated}

在啟動期間（不是第1次 — 但之後的每次），記錄中可能會顯示下列警告：

* 11.04.2014 08:38:07.223 **警告** [FelixStartLevel]com.github.jkank.handlebars.Handlebars Helper &#39;i18n&#39;已由&#39;com.adobe.cq.social.handlebars.I18nHelper@15bac645&#39;取代

此警告可以安全地忽略，如jkanck.handlebars.Handlebars，用於 [SCF](scf.md#handlebarsjavascripttemplatinglanguage)，隨附自己的i18n協助工具。 啟動時，會以AEM專用 [i18n幫手](handlebars-helpers.md#i-n). 此警告由第三方程式庫產生，以確認現有協助程式的覆寫。

### 記錄中的警告：OakResourceListener processOsgiEventQueue {#warning-in-logs-oakresourcelistener-processosgieventqueue}

張貼許多社交社群論壇主題，可能會產生來自OakResourceListenerprocessOsgiEventQueue的大量警告和資訊記錄。

這些警告可以安全地忽略。

```xml
23.04.2014 14:21:18.900 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.frq/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.908 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.prx/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
```

### 日誌中出錯：IndexElementFactory的NoClassDefFoundError {#error-in-logs-noclassdeffounderror-for-indexelementfactory}

將AEM 5.6.1 GA升級至最新cq-socialcommunities-pkg-1.4.x或AEM 6.0會在啟動期間導致記錄檔中發生錯誤，條件會自行解決，重新啟動時未看到錯誤即為證明。

```xml
14.11.2013 20:52:39.453 ERROR [Apache Sling JCR Resource Event Queue Processor for path '/'] com.adobe.cq.social.storage.index.impl.IndexService Error occurred while processing event java.util.ConcurrentModificationException
14.11.2013 20:52:40.716 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory) java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory
14.11.2013 20:52:40.717 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Failed creating the component instance; see log for reason
```
