---
title: DSRP的MySQL配置
seo-title: DSRP的MySQL配置
description: 如何連接到MySQL伺服器並建立UGC資料庫
seo-description: 如何連接到MySQL伺服器並建立UGC資料庫
uuid: c058cc88-7ca2-4aed-9a36-b080e603f886
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: edc3043c-7ec4-4e4a-b008-95f1784f012e
role: Admin
exl-id: 1de1ffc6-63f8-4316-a2fa-5095d407c265
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# DSRP的MySQL配置 {#mysql-configuration-for-dsrp}

MySQL是關係資料庫，可用於儲存用戶生成的內容(UGC)。

這些說明說明如何連接到MySQL Server並建立UGC資料庫。

## 需求 {#requirements}

* [最新Communities功能套件](deploy-communities.md#latestfeaturepack)
* [MySQL的JDBC驅動程式](deploy-communities.md#jdbc-driver-for-mysql)
* 關係資料庫：

   * [MySQL ](https://dev.mysql.com/downloads/mysql/) ServerCommunity Server 5.6版或更新版本

      * 可在與AEM相同的主機上運行或遠程運行
   * [MySQL Workbench](https://dev.mysql.com/downloads/tools/workbench/)


## 安裝MySQL {#installing-mysql}

[](https://dev.mysql.com/downloads/mysql/) MySQL應按照目標OS的說明下載和安裝。

### 小寫表名 {#lower-case-table-names}

由於SQL不區分大小寫，因此對於區分大小寫的作業系統，必須包含一個設定來將所有表名都小寫。

例如，要指定Linux OS上所有小寫表名：

* 編輯檔案`/etc/my.cnf`
* 在`[mysqld]`區段中，新增下列行：

   `lower_case_table_names = 1`

### UTF8字元集 {#utf-character-set}

若要提供更好的多語言支援，必須使用UTF8字元集。

將MySQL更改為以UTF8作為其字元集：

* mysql>設定名稱&#39;utf8&#39;;

將MySQL資料庫更改為預設UTF8:

* 編輯檔案`/etc/my.cnf`
* 在`[client]`區段中，新增下列行：

   `default-character-set=utf8`

* 在`[mysqld]`區段中，新增下列行：

   `character-set-server=utf8`

## 安裝MySQL Workbench {#installing-mysql-workbench}

MySQL Workbench提供了用於執行SQL指令碼的UI，這些指令碼安裝架構和初始資料。

MySQL Workbench應按照目標作業系統的說明下載並安裝。

## Communities Connection {#communities-connection}

MySQL Workbench首次啟動時（除非已用於其他用途），它將不會顯示任何連線：

![chlimage_1-104](assets/chlimage_1-104.png)

### 新連接設定 {#new-connection-settings}

1. 選擇`MySQL Connections`右側的`+`表徵圖。
1. 在對話方塊`Setup New Connection`中，輸入適合您平台的值

   為了示範，將製作AEM例項和MySQL放在相同的伺服器上：

   * 連接名：`Communities`
   * 連接方法：`Standard (TCP/IP)`
   * 主機名：`127.0.0.1`
   * 使用者名稱: `root`
   * 密碼: `no password by default`
   * 預設架構：`leave blank`

1. 選擇`Test Connection`以驗證與正在運行的MySQL服務的連接

**附註**:

* 預設埠為`3306`
* 在[JDBC OSGi配置](#configurejdbcconnections)中，選擇的連接名作為資料源名輸入

#### 新建Communities連接 {#new-communities-connection}

![chlimage_1-105](assets/chlimage_1-105.png)

## 資料庫設定 {#database-setup}

開啟Communities連接以安裝資料庫。

![chlimage_1-106](assets/chlimage_1-106.png)

### 獲取SQL指令碼 {#obtain-the-sql-script}

從AEM儲存庫獲取SQL指令碼：

1. 瀏覽至CRXDE Lite

   * 例如， [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. 選取/libs/social/config/datastore/dsrp/schema資料夾
1. 下載 `init-schema.sql`

![chlimage_1-107](assets/chlimage_1-107.png)

下載架構的方法之一是

* 為sql檔案選擇`jcr:content`節點
* 請注意，`jcr:data`屬性的值是檢視連結

* 選取檢視連結，將資料儲存至本機檔案

### 建立DSRP資料庫 {#create-the-dsrp-database}

請依照下列步驟安裝資料庫。 資料庫的預設名稱為`communities`。

如果在指令碼中更改了資料庫名稱，請確保在[JDBC配置](#configurejdbcconnections)中也更改了該名稱。

#### 步驟1:開啟SQL檔案 {#step-open-sql-file}

在MySQL Workbench中

* 從「檔案」(File)下拉菜單中
* 選擇下載的`init_schema.sql`

![chlimage_1-108](assets/chlimage_1-108.png)

#### 步驟2:執行SQL指令碼 {#step-execute-sql-script}

在Workbench視窗中，針對在步驟1中開啟的檔案選取`lightening (flash) icon`以執行指令碼。

在下圖中，`init_schema.sql`檔案已準備好執行：

![chlimage_1-109](assets/chlimage_1-109.png)

#### 重新整理 {#refresh}

執行指令碼後，必須刷新`Navigator`的`SCHEMAS`部分，才能查看新資料庫。 使用「結構」右側的刷新表徵圖：

![chlimage_1-110](assets/chlimage_1-110.png)

## 配置JDBC連接 {#configure-jdbc-connection}

**Day Commons JDBC連接池**&#x200B;的OSGi配置配置MySQL JDBC驅動程式。

所有發佈和製作AEM例項都應指向相同的MySQL伺服器。

當MySQL在與AEM不同的伺服器上運行時，必須指定伺服器主機名來取代JDBC連接器中的「localhost」。

* 在每個製作和發佈AEM例項上
* 以管理員權限登錄
* 訪問[Web控制台](../../help/sites-deploying/configuring-osgi.md)

   * 例如， [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* 找到`Day Commons JDBC Connections Pool`
* 選擇`+`表徵圖以建立新的連接配置

![chlimage_1-111](assets/chlimage_1-111.png)

* 輸入下列值：

   * **[!UICONTROL JDBC驅動程式類]**:  `com.mysql.jdbc.Driver`
   * **[!UICONTROL JDBC連接URI]**:  `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

      如果MySQL伺服器與&#39;this&#39; AEM伺服器不同，請指定伺服器來取代localhost

      ** 通訊預設資料庫（架構）名稱

   * **[!UICONTROL 使用者名稱]**:  `root`

      或者，輸入MySQL Server的配置用戶名（如果不是「root」）

   * **[!UICONTROL 密碼]**:

      如果未為MySQL設定密碼，請清除此欄位，

      否則，請為MySQL用戶名輸入配置的密碼
   * **[!UICONTROL 資料源名稱]**:為MySQL連 [接輸入的名稱](#new-connection-settings)，例如「communities」

* 選擇&#x200B;**[!UICONTROL 保存]**
