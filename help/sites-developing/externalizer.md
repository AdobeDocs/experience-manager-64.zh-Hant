---
title: 將URL外部化
seo-title: Externalizing URLs
description: Externalizer是OSGI服務，可讓您以程式設計方式將資源路徑轉換為外部和絕對URL
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# 將URL外部化{#externalizing-urls}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

在AEM中， **外置器** 是OSGI服務，可讓您以程式設計方式轉換資源路徑(例如 `/path/to/my/page`)放入外部和絕對URL(例如 `https://www.mycompany.com/path/to/my/page`)，方法是使用預先設定的DNS來預先修正路徑。

由於例項在Web層後面執行時無法知道其外部可見的URL，且由於有時必須在請求範圍之外建立連結，因此此服務提供一個集中位置來設定這些外部URL並建置它們。

本頁面說明如何設定 **外置器** 服務及使用方式。 如需更多詳細資訊，請參閱 [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## 配置Externalizer服務 {#configuring-the-externalizer-service}

此 **外置器** 服務可讓您集中定義多個網域，這些網域可用來以程式設計方式為資源路徑加上前置詞。 每個網域都以唯一名稱識別，該名稱用於以程式設計方式參考網域。

為定義域映射 **外置器** 服務：

1. 透過導覽至Configuration Manager **工具**，然後 **Web主控台**，或輸入 `https://<host>:<port>/system/console/configMgr.`
1. 按一下 **Day CQ Link Externalizer** 開啟「配置」對話框。

   >[!NOTE]
   >
   >至設定的直接連結為 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 定義網域對應：映射由唯一名稱組成，該名稱可在代碼中用於引用域、空格和域：

   `<unique-name> [scheme://]server[:port][/contextpath]`，其中：

   * **方案** 通常是http或https，但也可以是ftp等。;視需要使用https強制執行https連結；若要求將URL外部化時用戶端代碼未覆寫配置，則會使用此URL。
   * **伺服器** 是主機名（可以是域名或ip地址）。
   * **埠** （可選）是埠號。
   * **contextpath** （選用）只有在AEM安裝為位於不同內容路徑下的網頁應用程式時才會設定。

   例如：`production https://my.production.instance`

   下列對應名稱是預先定義的，且必須一律設定，因為AEM需仰賴這些名稱：

   * **本地**  — 本機執行個體
   * **作者**  — 編寫系統DNS
   * **發佈**  — 公開對應的網站DNS

   >[!NOTE]
   >
   >自訂設定可讓您新增類別，例如「生產」、「測試」，甚至外部非AEM系統，例如「my-internal-webservice」，此自訂設定有助於避免在專案的程式碼基底中不同位置以硬式編碼撰寫此類URL。

1. 按一下 **儲存** 來儲存變更。

>[!NOTE]
>
>Adobe建議您 [將配置添加到儲存庫](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## 使用Externalizer服務 {#using-the-externalizer-service}

本節提供幾個範例，說明 **外置器** 可使用服務。

**要在JSP中獲取Externalizer服務，請執行以下操作：**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**若要將具有&#39;publish&#39;網域的路徑外部化：**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

假設網域對應「 `publish https://www.website.com`&quot;,myExternaledUrl的結尾是值&quot; `https://www.website.com/contextpath/my/page.html`」。

**若要將具有「作者」網域的路徑外部化：**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

假設網域對應「 `author https://author.website.com`&quot;,myExternaledUrl的結尾是值&quot; `https://author.website.com/contextpath/my/page.html`」。

**要將具有&#39;local&#39;域的路徑外部化：**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

假設網域對應「 `local https://publish-3.internal`&quot;,myExternaledUrl的結尾是值&quot; `https://publish-3.internal/contextpath/my/page.html`」。

您可以在 [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
