---
title: 靜態對象的過期
seo-title: 靜態對象的過期
description: 了解如何設定AEM，讓靜態物件不會過期（在合理的時段內）。
seo-description: 了解如何設定AEM，讓靜態物件不會過期（在合理的時段內）。
uuid: ee019a3d-4133-4d40-98ec-e0914b751fb3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 73f37b3c-5dbe-4132-bb60-daa8de871884
feature: 設定
exl-id: 3551d25c-c852-4f59-84fe-5e62f57ae63f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# 靜態對象的過期{#expiration-of-static-objects}

靜態物件（例如圖示）不會變更。 因此，應將系統配置為使它們不會過期（在合理的時間段內），從而減少不必要的流量。

其影響如下：

* 卸載來自伺服器基礎架構的請求。
* 隨著瀏覽器在瀏覽器快取中快取物件，提高頁面載入的效能。

HTTP標準會針對檔案的「過期」指定過期時間（例如，請參閱[RFC 2616](https://www.ietf.org/rfc/rfc2616.txt) &quot;超文字傳輸通訊協定 — HTTP 1.1&quot;的第14.21章）。 此標準使用標頭，允許客戶端快取對象，直到它們被視為過時；這樣的對象被快取指定的時間量，而不對源伺服器進行任何狀態檢查。

>[!NOTE]
>
>此設定與Dispatcher完全分開（且不適用）。
>
>Dispatcher的用途是快取AEM前面的資料。

可以且應快取所有非動態且不會隨時間變更的檔案。 Apache HTTPD伺服器的配置可能如下所示（取決於環境）:

>[!CAUTION]
>
>在定義將對象視為最新的時段時，必須小心。 由於在指定的時段已過&#x200B;*之前沒有檢查，因此客戶端最終可以從快取中呈現舊內容。*

1. **對於Author例項：**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /libs>
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType text/javascript "access plus 1 month"
     ExpiresByType image/png "access plus 1 month"
     ExpiresByType image/gif "access plus 1 month"
   </Location>
   ```

   這可讓中繼快取（例如瀏覽器快取）最多儲存一個月的CSS、Javascript、PNG和GIF檔案，直到它們過期為止。 這表示不需要向AEM或Web伺服器要求這些檔案，但可保留在瀏覽器快取中。

   網站的其他區段不應在製作例項上快取，因為這些區段隨時可能變更。

1. **對於發佈例項：**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /content>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   <Location /etc/designs>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   ```

   這可讓中間快取（例如瀏覽器快取）在用戶端快取中儲存最多一天的CSS、Javascript、PNG和GIF檔案。 雖然此範例說明`/content`和`/etc/designs`下所有項目的全域設定，但您應讓其更精細。

   您也可以考慮快取HTML頁面，視網站的更新頻率而定。 合理的時段為1小時：

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

配置靜態對象後，在選擇保存此類對象的頁時掃描`request.log`，以確認沒有對靜態對象提出（不必要的）請求。
