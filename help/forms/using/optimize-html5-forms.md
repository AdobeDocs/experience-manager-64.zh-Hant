---
title: 最佳化HTML5表單
seo-title: Optimizing HTML5 forms
description: 您可以最佳化HTML5表單的輸出大小。
seo-description: You can optimize the output size of the HTML5 forms.
uuid: 959f0b6a-9e4d-478a-afa8-4c39011fdf7a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: bdb9edc2-6a37-4d3f-97d5-0fc5664316be
feature: Mobile Forms
exl-id: 8d2b5294-9763-4348-b927-706ebac90b95
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# 最佳化HTML5表單 {#optimizing-html-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

HTML5表單會以HTML5格式轉譯表單。 結果的輸出可能會很大，具體取決於表單大小和表單中的影像等因素。 若要最佳化資料傳輸，建議的方法是使用要求提供來源的Web伺服器來壓縮HTML回應。 此方法可減少回應大小、網路流量，以及在伺服器與用戶端電腦之間串流資料所需的時間。

本文說明使用JBoss為Apache Web Server 2.0 32位元啟用壓縮所需的步驟。

*注意：下列說明不適用於Apache Web Server 2.0 32位以外的伺服器。*

獲取適用於您的作業系統的Apache Web伺服器軟體：

* 對於Windows，請從Apache HTTP Server Project站點下載Apache Web伺服器。
* 對於Solaris 64位，請從Sunfreeware for Solaris網站下載Apache Web伺服器。
* 對於Linux,Apache Web伺服器預安裝在Linux系統上。

Apache可以使用HTTP或AJP通訊協定與JBoss通訊。

1. 取消註解下列模組設定： *APACHE_HOME/conf/httpd.conf* 檔案。

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >對於Linux，預設的APACHE_HOME目錄為/etc/httpd/。

1. 在JBoss的埠8080上配置代理。

   將下列設定新增至 *APACHE_HOME/conf/httpd.conf* 設定檔。

   ```java
   ProxyPass / https://<server_Name>:8080/
   ProxyPassReverse / https://<server_Name>:8080/
   ```

   >[!NOTE]
   >
   >使用Proxy時，需要進行下列設定變更：
   > 
   >* 訪問： *https://&lt;server>:&lt;port>/system/console/configMgr*
   * 編輯Apache Sling反向連結篩選器的設定
   * 在「允許主機」中，添加代理伺服器的條目


1. 啟用壓縮。

   將下列設定新增至 *APACHE_HOME/conf/httpd.conf* 設定檔。

   ```java
   <Location /content/xfaforms>
     <IfModule mod_deflate.c>
        SetOutputFilter DEFLATE
        # Don’t compress
        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
        SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
       #Dealing with proxy servers
   
        <IfModule mod_headers.c>
           Header append Vary User-Agent
        </IfModule>
     </IfModule>
   </Location>
   ```

1. 若要存取AEM伺服器，請使用https://[Apache_server]:80。
