---
title: 外部化URL
seo-title: 外部化URL
description: Externalizer是OSGI服務，可讓您以程式設計方式將資源路徑轉換為外部和絕對URL
seo-description: Externalizer是OSGI服務，可讓您以程式設計方式將資源路徑轉換為外部和絕對URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# 外部化URL{#externalizing-urls}

在AEM中， **Externalizer** 是OSGI服務，可讓您以程式設計方式轉換資源路徑(例如 `/path/to/my/page`)，以預先設定的DNS來預先固定路徑， `https://www.mycompany.com/path/to/my/page`以將URL轉換為外部和絕對URL（例如）。

由於例項在Web圖層後面執行時無法知道其外部可見的URL，而且有時必須在請求範圍外建立連結，因此此服務提供一個集中位置來設定這些外部URL並建立它們。

本頁說明如何設定 **Externalizer** service，以及如何使用它。 如需詳細資訊，請參閱 [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html)。

## 配置Externalizer服務 {#configuring-the-externalizer-service}

Externalizer **** service可讓您集中定義多個網域，可用來以程式設計方式為資源路徑加上前置詞。 每個網域都由唯一名稱來識別，該名稱用於以程式設計方式參考網域。

要定義 **Externalizer服務的域映射** :

1. 通過工具依次導航到配 **置管理器**, **Web控制台**，或輸入 `https://<host>:<port>/system/console/configMgr.`
1. 按一 **下「日CQ連結外部化** 」以開啟設定對話方塊。

   >[!NOTE]
   >
   >配置的直接連結是 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 定義域映射： 映射由唯一名稱組成，可用於代碼中以引用域、空間和域：

   `<unique-name> [scheme://]server[:port][/contextpath]`，其中：

   * **scheme** 通常為http或https，但也可以是ftp等。; 視需要使用https來強制https連結； 當用戶端程式碼要求將URL外部化時，不會覆寫配置時，就會使用它。
   * **server** 是主機名（可以是域名或IP地址）。
   * **port** （可選）是埠號。
   * **contextpath** （選用）只有在AEM安裝為位於不同內容路徑下的網頁應用程式時才會設定。

   For example: `production https://my.production.instance`

   下列對應名稱是預先定義的，必須一律設定，因為AEM需仰賴這些名稱：

   * **local** —— 本地實例
   * **author** —— 編寫系統DNS
   * **publish** —— 公開對應的網站DNS

   >[!NOTE]
   >
   >自訂設定可讓您新增新類別，例如「生產」、「測試」或甚至外部非AEM系統（例如「my-internal-webservice」），對於避免在專案的程式碼基底中不同位置硬式編碼此類URL非常有用。

1. 按一 **下「儲存** 」以儲存變更。

>[!NOTE]
>
>Adobe建議您將 [設定新增至儲存庫](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)。

## 使用Externalizer服務 {#using-the-externalizer-service}

本節顯示如何使用 **Externalizer** 服務的一些示例。

**要在JSP中獲取Externalizer服務，請執行以下操作：**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**若要將路徑外部化為具有「發佈」網域：**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

假設網域對 `publish https://www.website.com`應&quot;&quot;,myExternalizedUrl最後會顯示值&quot; `https://www.website.com/contextpath/my/page.html`&quot;。

**要將具有「author」域的路徑外部化：**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

假設網域對 `author https://author.website.com`應&quot;&quot;,myExternalizedUrl最後會顯示值&quot; `https://author.website.com/contextpath/my/page.html`&quot;。

**要將具有「本地」域的路徑外部化：**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

假設網域對 `local https://publish-3.internal`應&quot;&quot;,myExternalizedUrl最後會顯示值&quot; `https://publish-3.internal/contextpath/my/page.html`&quot;。

您可以在 [Javadocs中找到更多範例](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html)。
