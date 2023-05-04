---
title: AEM 6.4中的RDBMS支援
seo-title: RDBMS Support in AEM 6.4
description: 了解AEM 6.4中的關係資料庫持續性支援，以及可用的設定選項。
seo-description: Learn about the relational database persistence support in AEM 6.4 and the available configuration options.
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
feature: Configuring
exl-id: 89523bb4-e4c4-469c-802b-6fe27c816a2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 1%

---

# AEM 6.4中的RDBMS支援{#rdbms-support-in-aem}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

使用文檔微內覈實現了對AEM中關係資料庫持久性的支援。 文檔微內核是實現MongoDB持久性的基礎。

它包含以Mongo Java API為基礎的Java API。 也提供BlobStore API的實作。 預設情況下，Blob儲存在資料庫中。

如需實作詳細資訊，請參閱 [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) 和 [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) 檔案。

>[!NOTE]
>
>支援 **PostgreSQL 9.4** 也提供，但僅供示範之用。 它將無法用於生產環境。

## 支援的資料庫 {#supported-databases}

有關AEM中關係資料庫支援級別的詳細資訊，請參見 [技術需求頁面](/help/sites-deploying/technical-requirements.md).

## 配置步驟 {#configuration-steps}

存放庫是透過設定 `DocumentNodeStoreService` OSGi服務。 除了MongoDB外，它還擴展了它以支援關係資料庫持久性。

資料來源必須使用AEM進行設定，才能運作。 這是透過 `org.apache.sling.datasource.DataSourceFactory.config` 檔案。 相應資料庫的JDBC驅動程式需要作為本地配置內的OSGi包單獨提供。

有關為JDBC驅動程式建立OSGi套件組合的步驟，請參見 [檔案](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle) 在Apache Sling網站上。

>[!NOTE]
>
>某些SQL驅動程式已打包為OSGi包。
>
>如果是這種情況，請將jar檔案複製到install-path/crx-quickstart/install/9。

套件組合就緒後，請依照下列步驟以使用RDB持續性設定AEM:

1. 確保資料庫守護程式已啟動，並且您有可與AEM一起使用的活動資料庫。
1. 將AEM 6.3 jar複製到安裝目錄。
1. 建立名為 `crx-quickstart\install` （在安裝目錄中）。
1. 通過在 `crx-quickstart\install` 目錄：

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. 通過在 `crx-quickstart\install` 資料夾：

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >有關每個受支援資料庫的資料源配置的詳細資訊，請參見 [資料源配置選項](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. 接下來，準備要與AEM一起使用的JDBC OSGi套件組合：

   1. 請前往https://dev.mysql.com/downloads/connector/j/下載ZIP封存檔
      * 版本必須>= 5.1.38
   1. 擷取 `mysql-connector-java-version-bin.jar` （捆綁）
   1. 使用Web主控台來安裝和啟動套件組合：
      * 前往 *http://serveraddress:serverport/system/console/bundles*
      * 選擇 **安裝/更新**
      * 瀏覽至從下載的ZIP封存檔中擷取的套件組合
      * 檢查 **Oracle公司的MySQLcom.mysql.jdbc JDBC驅動程式** 活動，然後啟動。

1. 最後，從AEM開始 `crx3` 和 `crx3rdb` 執行模式：

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## 資料源配置選項 {#data-source-configuration-options}

此 `org.apache.sling.datasource.DataSourceFactory-oak.config` OSGi配置用於配置AEM和資料庫持久層之間通信所需的參數。

可使用下列設定選項：

* `datasource.name:` 資料來源名稱。 預設為 `oak`。

* `url:` 需要與JDBC一起使用的資料庫的URL字串。 每個資料庫類型都有其自己的URL字串格式。 如需詳細資訊，請參閱 [URL字串格式](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) 下方。

* `driverClassName:` JDBC驅動程式類名。 這會因您要使用的資料庫以及隨後連接到該資料庫所需的驅動程式而異。 以下是AEM支援的所有資料庫的類名：

   * `org.postgresql.Driver` (適用於PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` DB2;
   * `oracle.jdbc.OracleDriver` oracle;
   * `com.mysql.jdbc.Driver` （MySQL和MariaDB）;
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` Microsoft SQL Server（實驗性）。

* `username:` 資料庫運行的用戶名。

* `password:` 資料庫密碼。

### URL字串格式 {#url-string-formats}

根據需要使用的資料庫類型，在資料源配置中使用不同的URL字串格式。 以下是AEM目前支援的資料庫格式清單：

* `jdbc:postgresql:databasename` (適用於PostgreSQL;

* `jdbc:db2://localhost:port/databasename` DB2;
* `jdbc:oracle:thin:localhost:port:SID` oracle;
* `jdbc:mysql://localhost:3306/databasename` （MySQL和MariaDB）;

* `jdbc:sqlserver://localhost:1453;databaseName=name` Microsoft SQL Server（實驗性）。

## 已知限制 {#known-limitations}

雖然RDBMS持續性支援同時使用具有單一資料庫的多個AEM例項，但不支援同時安裝。

要解決此問題，請確保先使用單個成員運行安裝，然後在完成安裝後添加其他成員。
