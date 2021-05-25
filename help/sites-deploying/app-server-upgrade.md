---
title: 應用程式伺服器安裝的升級步驟
seo-title: 應用程式伺服器安裝的升級步驟
description: 了解如何升級透過應用程式伺服器部署的AEM例項。
seo-description: 了解如何升級透過應用程式伺服器部署的AEM例項。
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
feature: 升級
exl-id: 1c72093e-82c8-49ad-bd3c-d61904aaab28
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 應用程式伺服器安裝的升級步驟{#upgrade-steps-for-application-server-installations}

本節介紹為了更新AEM以安裝應用程式伺服器而需要遵循的過程。

此程式中的所有範例都使用JBoss做為應用程式伺服器，且表示您已部署AEM的有效版本。 此程式的用途是記錄從&#x200B;**AEM 5.6版到6.3**&#x200B;所執行的升級。

1. 首先，啟動JBoss。 在大多數情況下，您可以通過從終端運行以下命令來運行`standalone.sh`啟動指令碼：

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. 如果已部署AEM 5.6，請執行以下程式來檢查套件組合是否正常運作：

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. 接下來，取消部署AEM 5.6:

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. 停止JBoss。

1. 現在，使用crx2oak移轉工具移轉存放庫：

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >在此範例中，oak-repository是新轉換的存放庫所在的臨時目錄。 執行此步驟之前，請確定您有最新的crx2oak.jar版本。

1. 請執行下列動作，刪除sling.properties檔案中的必要屬性：

   1. 開啟位於`crx-quickstart/launchpad/sling.properties`的檔案
   1. 步驟文字移除下列屬性並儲存檔案：

      1. `sling.installer.dir`
      1. `felix.cm.dir`
      1. `granite.product.version`
      1. `org.osgi.framework.system.packages`
      1. `osgi-core-packages`
      1. `osgi-compendium-services`
      1. `jre-*`
      1. `sling.run.mode.install.options`

1. 移除不再需要的檔案和資料夾。 您需要明確移除的項目包括：

   * **launchpad/startup資料夾**。 您可以在終端機中執行下列命令以刪除它：`rm -rf crx-quickstart/launchpad/startup`
   * **base.jar檔案**:`find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * **BootstrapCommandFile_timestamp.txt檔案**:`rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. 將新移轉的區段存放區複製到其適當位置：

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. 也複製資料存放區：

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. 接下來，您需要建立包含將與新升級執行個體搭配使用之OSGi設定的資料夾。 更具體地說，需要在&#x200B;**crx-quickstart**&#x200B;下建立名為install的資料夾。

1. 現在，建立要與AEM 6.3搭配使用的節點儲存區和資料儲存區。您可以在&#x200B;**crx-quickstart\install**&#x200B;下建立兩個檔案，其名稱如下：

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   這兩個檔案會將AEM設定為使用TarMK節點存放區和檔案資料存放區。

1. 編輯組態檔，使其可供使用。 更具體而言：

   * 將下列行新增至&#x200B;**org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * 然後將下列行加入&#x200B;**org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. 執行以移除crx2執行模式：

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. 您現在需要變更AEM 6.3 war檔案中的執行模式。 為此，首先建立一個臨時資料夾，用於容納AEM 6.3戰爭。 此示例中資料夾的名稱為&#x200B;**temp**。 複製戰爭檔案後，從臨時資料夾內執行以擷取其內容：

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. 提取內容後，轉到&#x200B;**WEB-INF**&#x200B;資料夾並編輯`web.xml`檔案以更改運行模式。 要查找XML中設定它們的位置，請查找`sling.run.modes`字串。 找到此檔案後，請變更下一行程式碼中的執行模式，預設會將其設為製作：

   ```shell
   <param-value >author</param-value>
   ```

1. 將上述製作值變更，並將執行模式設為：author,crx3,crx3tar程式碼的最終區塊應如下所示：

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. 使用已修改的內容重新建立jar:

   ```shell
   jar cvf aem62.war
   ```

1. 最後，部署新的戰爭檔案：

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```
