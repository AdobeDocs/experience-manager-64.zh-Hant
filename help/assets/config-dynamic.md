---
title: 配置Dynamic Media — 混合模式
seo-title: Configuring Dynamic Media - Hybrid mode
description: 了解如何設定Dynamic Media — 混合模式。
seo-description: Learn how to configure Dynamic Media - Hybrid mode.
uuid: de88f68f-4697-4ff0-8008-3ae6a4684a84
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 821eb27e-67c9-4589-9196-30dacb84fa59
exl-id: 1e122f97-ac37-44f5-a1cd-bf53ffda6f5b
feature: Configuration,Hybrid Mode
role: Admin,User,Developer
source-git-commit: a750c5425e33c2a115aab581b71862c1d30cf166
workflow-type: tm+mt
source-wordcount: '7780'
ht-degree: 1%

---

# 配置Dynamic Media — 混合模式 {#configuring-dynamic-media-hybrid-mode}

Dynamic Media — 需要啟用並設定混合功能，才能使用。 根據您的使用案例，Dynamic Media有數個[支援的設定](#supported-dynamic-media-configurations)。

>[!NOTE]
>
>如果您要在Scene7執行模式中設定及執行Dynamic Media，請參閱[設定Dynamic Media - Scene7模式](config-dms7.md)。
>
>如果您要以混合執行模式設定及執行Dynamic Media，請依照本頁的指示操作。

進一步了解如何在Dynamic Media中使用[video](video.md)。

如果您使用針對不同環境（例如開發、測試和即時生產）設定的Adobe Experience Manager，則需要為其中每個環境設定Dynamic MediaCloud Services。

如果您的Dynamic Media設定有問題，請務必查看Dynamic Media專用的記錄檔。 當您啟用動態媒體時，會自動安裝下列項目：

* `s7access.log`
* `ImageServing.log`

這些檔案記錄在[監控和維護您的AEM例項](/help/sites-deploying/monitoring-and-maintaining.md)中。

混合發佈與傳送是Dynamic Media新增Adobe Experience Manager的核心功能。 混合發佈可讓您從雲端而非AEM發佈節點傳送Dynamic Media資產，例如影像、集和視訊。

AEM發佈節點會繼續提供其他內容，例如Dynamic Media檢視器、網站頁面和靜態內容。

如果您是Dynamic Media的客戶，則必須使用混合式傳送作為所有Dynamic Media內容的傳送機制。

## 影片的混合發佈架構 {#hybrid-publishing-architecture-for-videos}

![chlimage_1-506](assets/chlimage_1-506.png)

## 影像混合發佈架構 {#hybrid-publishing-architecture-for-images}

![chlimage_1-507](assets/chlimage_1-507.png)

## 支援的Dynamic Media設定 {#supported-dynamic-media-configurations}

後面的設定任務參考下列術語：

| **詞彙** | **Dynamic Media已啟用** | **說明** |
|---|---|---|
| AEM製作節點 | 綠色圓圈中的白勾號 | 您部署至On-Premise或透過Managed Services的製作節點。 |
| AEM發佈節點 | 紅方的白色X。 | 您部署至內部部署或透過Managed Services的發佈節點。 |
| 影像服務發佈節點 | 綠色圓形中的白勾號。 | 您在由Adobe管理的資料中心上執行的發佈節點。 指影像服務URL。 |

您可以選擇僅針對影像、僅限視訊，或同時針對影像和視訊實作Dynamic Media。 若要判別針對特定案例設定Dynamic Media的步驟，請參閱下表。

<table> 
 <tbody> 
  <tr> 
   <td><strong>藍本</strong></td> 
   <td><strong>運作方式</strong></td> 
   <td><strong>配置步驟</strong></td> 
  </tr> 
  <tr> 
   <td>在生產環境中僅提供映像</td> 
   <td>影像會透過Adobe全球資料中心的伺服器傳送，然後由CDN快取，以提供可擴充的效能和全球觸及率。</td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>節點上，<a href="#enabling-dynamic-media">啟用動態媒體</a>。</li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services</a>中配置影像。</li> 
     <li><a href="#configuring-image-replication">配置映像複製</a>。</li> 
     <li><a href="#replicating-catalog-settings">複製目錄設定</a>。</li> 
     <li><a href="#replicating-viewer-presets">復寫檢視器預設集</a>。</li> 
     <li><a href="#using-default-asset-filters-for-replication">對復寫使用預設資產篩選器</a>。</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">配置Dynamic Media Image Server設定</a>。</li> 
     <li><a href="#delivering-assets">傳送資產</a>。</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>在預製作（開發、QE、預備等）中僅提供影像。</td> 
   <td>影像會透過AEM發佈節點傳送。 在此情境中，由於流量極少，因此不需要將影像傳送至Adobe的資料中心。 另外一項好處是，這可讓生產啟動前安全地預覽內容</td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>節點上，<a href="#enabling-dynamic-media">啟用動態媒體</a>。</li> 
     <li>在AEM <strong>publish</strong>節點上，<a href="#enabling-dynamic-media">啟用動態媒體</a>。</li> 
     <li><a href="#replicating-viewer-presets">復寫檢視器預設集</a>。</li> 
     <li>為非生產影像設定<a href="#setting-up-asset-filters-for-imaging-in-non-production-deployments">資產篩選器</a>。</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">配置Dynamic Media Image Server設定。</a></li> 
     <li><a href="#delivering-assets">傳送資產。</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>在任何環境（生產、開發、QE、預備等）中只傳送視訊</td> 
   <td>CDN會傳送並快取視訊，以提升效能並觸及全域。 視訊海報影像（播放起始前顯示的視訊縮圖）將由AEM發佈例項傳送。</td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>節點上，<a href="#enabling-dynamic-media">啟用動態媒體</a>。</li> 
     <li>在AEM <strong>publish</strong>節點上，<a href="#enabling-dynamic-media">啟用動態媒體</a>（發佈例項提供視訊海報影像，並提供視訊播放的中繼資料）。</li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services中設定視訊。</a></li> 
     <li><a href="#replicating-viewer-presets">復寫檢視器預設集</a>。</li> 
     <li>設定僅限視訊</a>的資產篩選器。<a href="#setting-up-asset-filters-for-video-only-deployments"></a></li> 
     <li><a href="#delivering-assets">傳送資產。</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>在生產中提供影像和視訊</td> 
   <td><p>CDN會傳送並快取視訊，以提升效能並觸及全域。 影像和視訊海報影像會透過Adobe全球資料中心的伺服器傳送，然後由CDN快取，以提供可擴充的效能和全球觸及率。</p> <p>請參閱前幾節，以在預製作業中設定影像或影片。 </p> </td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>節點上，<a href="#enabling-dynamic-media">啟用動態媒體</a>。</li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services中設定視訊。</a></li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services中配置影像。</a></li> 
     <li><a href="#configuring-image-replication">配置映像複製</a>。</li> 
     <li><a href="#replicating-catalog-settings">複製目錄設定</a>。</li> 
     <li><a href="#replicating-viewer-presets">復寫檢視器預設集</a>。</li> 
     <li><a href="#using-default-asset-filters-for-replication">對復寫使用預設資產篩選器。</a></li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">配置Dynamic Media Image Server設定。</a></li> 
     <li><a href="#delivering-assets">傳送資產。</a></li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>

## 啟用Dynamic Media {#enabling-dynamic-media}

[動態](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 媒體預設為停用。若要運用Dynamic Media功能，您必須使用&#x200B;**[!UICONTROL dynamicmedia]**&#x200B;執行模式來啟用動態媒體，如&#x200B;**[!UICONTROL publish]**&#x200B;執行模式。 啟用前，請務必檢閱[技術要求](/help/sites-deploying/technical-requirements.md#requirements-for-aem-dynamic-media-add-on)。

>[!NOTE]
>
>透過執行模式啟用動態媒體，會將&#x200B;**[!UICONTROL dynamicMediaEnabled]**&#x200B;標幟設為&#x200B;**[!UICONTROL true]**，取代AEM 6.1和AEM 6.0中您啟用動態媒體的功能。 此標幟在AEM 6.2和更新版本中沒有功能。 此外，您不需要重新啟動快速入門即可啟用動態媒體。

透過啟用Dynamic Media,UI中將提供動態媒體功能，而每個上傳的影像資產都會收到`cqdam.pyramid.tiff`轉譯，以用於快速傳送動態影像轉譯。 這些PTIFF具有顯著優點，包括(1)僅能管理單一主影像並即時產生無限轉譯，而無需任何額外儲存；以及(2)能使用互動式視覺效果，例如縮放、平移、回轉等。

如果您想在AEM中使用Dynamic Media Classic，除非您使用[特定藍本](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media)，否則不應啟用Dynamic Media。 除非您透過執行模式啟用Dynamic Media，否則Dynamic Media會停用。

要啟用動態媒體，必須從命令行或快速啟動檔案名啟用動態媒體運行模式。

**若要啟用動態媒體**:

1. 在命令行上，啟動快速啟動時，請執行以下操作：

   * 在啟動jar檔案時，將&#x200B;**[!UICONTROL -r dynamicmedia]**&#x200B;新增至命令列結尾。

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -r dynamicmedia
   ```

   如果您要發佈至s7delivery，則還需要包含下列trustStore引數：

   ```shell
   -Djavax.net.ssl.trustStore=<absoluteFilePath>/customerTrustStoreFileName>
   
    -Djavax.net.ssl.trustStorePassword=<passwordForTrustStoreFile>
   ```

1. 請求`http://localhost:4502/is/image` ，並確認影像伺服器現在正在運行。

   >[!NOTE]
   >
   >若要疑難排解Dynamic Media的問題，請參閱&#x200B;**[!UICONTROL crx-quickstart/logs/]**&#x200B;目錄中的下列記錄：
   >
   >* ImageServer-&lt;PortId>-&lt;yyyy>&lt;mm>&lt;dd>.log - ImageServer日誌提供用於分析內部ImageServer進程行為的統計資訊和分析資訊。

      映像伺服器日誌檔案名的示例：`ImageServer-57346-2019-07-25.log`
   * s7access-&lt;yyyy>&lt;mm>&lt;dd>.log - s7access日誌會記錄透過`/is/image`和`/is/content`對Dynamic Media提出的每個請求。
   這些記錄檔僅在啟用Dynamic Media時使用。 從&#x200B;**[!UICONTROL system/console/status-Bundlelist]**&#x200B;頁面產生的&#x200B;**下載完整**&#x200B;套件中未包含這些檔案；如果您有Dynamic Media問題，在呼叫客戶支援時，請將這兩個記錄附加至問題。

### 如果您將AEM安裝至不同的連接埠或內容路徑…… {#if-you-installed-aem-to-a-different-port-or-context-path}

如果要將[AEM部署到應用程式伺服器](/help/sites-deploying/application-server-install.md)並啟用Dynamic Media，則需要在外部化程式中配置&#x200B;**self**&#x200B;域。 否則，動態媒體資產的資產縮圖產生將無法正常運作。

此外，如果在不同的埠或上下文路徑上運行快速啟動，則還必須更改&#x200B;**self**&#x200B;域。

啟用Dynamic Media時，會使用Dynamic Media產生影像資產的靜態縮圖轉譯。 為了讓動態媒體能正常產生縮圖，AEM必須對其本身執行URL要求，且必須知道連接埠號和內容路徑。

在AEM中：

* [externalizer](/help/sites-developing/externalizer.md)中的&#x200B;**self**&#x200B;域用於檢索埠號和上下文路徑。
* 如果未配置&#x200B;**self**&#x200B;域，則從Jetty HTTP服務中檢索埠號和上下文路徑。

在AEM QuickStart WAR部署中，埠號和上下文路徑無法派生，因此必須配置&#x200B;**self**&#x200B;域。 有關如何配置&#x200B;**self**&#x200B;域的[外部化程式文檔](/help/sites-developing/externalizer.md)。

>[!NOTE]
在[AEM Quickstart獨立部署](/help/sites-deploying/deploy.md)中，通常不需要配置&#x200B;**self**&#x200B;域，因為埠號和上下文路徑可以自動配置。 但是，如果所有網路介面都關閉，則需要配置&#x200B;**self**&#x200B;域。

## 停用Dynamic Media  {#disabling-dynamic-media}

預設不會啟用動態媒體。 不過，如果您先前已啟用動態媒體，您稍後可能會想要將其關閉。

若要在啟用動態媒體後加以停用，請移除&#x200B;**[!UICONTROL -r dynamicmedia]**&#x200B;執行模式標幟。

**若要在啟用Dynamic Media後停用該功能**:

1. 在命令行中，啟動快速啟動時，可以執行以下任一操作：

   * 啟動JAR檔案時，請勿將`-r dynamicmedia`添加到命令行中。

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar
   ```

1. 請求`http://localhost:4502/is/image`。 您會收到Dynamic Media已停用的訊息。

   >[!NOTE]
   停用Dynamic Media執行模式後，會自動略過產生`qdam.pyramid.tiff`轉譯的工作流程步驟。 這也會停用動態轉譯支援和其他Dynamic Media功能。
   另請注意，設定AEM伺服器後，當Dynamic Media執行模式停用時，在該執行模式下上傳的所有資產現在都無效。

## （選用）將Dynamic Media預設集和設定從6.3移轉至6.4零停機時間 {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

如果您要將AEM Dynamic Media從6.3升級至6.4(現在包含零停機時間（也稱為「選擇加入」）部署)，則需要執行下列curl命令，將CRXDE Lite中的所有預設集和設定從`/etc`移轉至`/conf`。

**注意**:如果您以相容模式（即安裝相容性封裝）運行AEM實例，則無需運行這些命令。

若要將自訂預設集和設定從`/etc`移轉至`/conf`，請執行下列Linux curl命令：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

對於所有升級，無論是否使用相容性包，都可以通過運行以下命令複製現成可用的查看器預設集：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## 配置映像複製 {#configuring-image-replication}

Dynamic Media影像傳送的運作方式是從AEM Author發佈影像資產（包括視訊縮圖），並將其複製至Adobe的隨選復寫服務（復寫服務URL）。 然後會透過隨需影像傳送服務（影像服務URL）來傳送資產。

您必須執行下列動作：

1. [設定驗證](#setting-up-authentication)。
1. [設定復寫代理](#configuring-the-replication-agent)。

復寫代理會發佈Dynamic Media資產，例如影像、視訊中繼資料，並將集合發佈至Adobe托管的影像服務。 預設不啟用復寫代理。

配置複製代理後，需要[驗證並測試它是否已成功設定](#validating-the-replication-agent-for-dynamic-media)。 本節將介紹這些過程。

>[!NOTE]
建立PTIFF的預設記憶體限制為3 GB，涵蓋所有工作流程。 例如，您可以在其他工作流程暫停時處理一個需要3 GB記憶體的映像，或者並行處理10個每個需要300 MB記憶體的映像。
記憶體限制是可配置的，應符合系統資源可用性和正在處理的影像內容類型。 如果您有許多超大型資產，且系統記憶體足夠，您可以提高此限制，以確保並行處理影像。
超過最大記憶體限制的映像將被拒絕。
要更改PTIFF建立的記憶體限制，請導航至&#x200B;**[!UICONTROL 工具>操作> Web Console > Adobe CQ Scene7 PTiffManager]**&#x200B;並更改`maxMemory`值。

### 設定驗證 {#setting-up-authentication}

您需要在作者上設定復寫驗證，才能將影像復寫至Dynamic Media影像傳送服務。 要執行此操作，請取得KeyStore，然後將其儲存在&#x200B;**[!UICONTROL dynamic-media-replication]**&#x200B;使用者下，並加以設定。 您的公司管理員應在配置過程中收到包含KeyStore檔案和必要憑據的歡迎電子郵件。 如果您未收到此訊息，請聯絡客戶支援。

**若要設定驗證**:

1. 如果您尚未擁有KeyStore檔案和密碼，請聯絡客戶支援。 這是布建的一部分，它會將金鑰關聯至您的帳戶。
1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具>安全性>使用者]**。
1. 在「使用者管理」頁面上，導覽至&#x200B;**[!UICONTROL dynamic-media-replication]**&#x200B;使用者，然後點選以開啟。

   ![dm-replication](assets/dm-replication.png)

1. 在「編輯動態媒體復寫的使用者設定」頁面中，點選&#x200B;**[!UICONTROL 金鑰存放區]**&#x200B;標籤，然後點選&#x200B;**[!UICONTROL 建立金鑰存放區]**。

   ![dm-replication-keystore](assets/dm-replication-keystore.png)

1. 在&#x200B;**[!UICONTROL 設定密鑰儲存訪問密碼]**&#x200B;對話框中輸入密碼並確認密碼。

   >[!NOTE]
   記住您輸入的密碼。 以後配置&#x200B;**[!UICONTROL 複製代理]**&#x200B;時需要再次輸入。

   ![chlimage_1-508](assets/chlimage_1-508.png)

1. 在&#x200B;**[!UICONTROL 編輯動態媒體復寫的使用者設定]**&#x200B;頁面上，展開&#x200B;**[!UICONTROL 從KeyStore檔案]**&#x200B;新增私密金鑰區域，並新增下列項目（請參閱下列影像）:

   * 在&#x200B;**[!UICONTROL 新別名]**&#x200B;欄位中，輸入您稍後將在複製配置中使用的別名的名稱；例如， **replication**。
   * 點選&#x200B;**[!UICONTROL KeyStore File]**。 導覽至Adobe提供給您的KeyStore檔案，選取該檔案，然後點選&#x200B;**[!UICONTROL Open]**。
   * 在&#x200B;**[!UICONTROL KeyStore File Password]**&#x200B;欄位中，輸入KeyStore File密碼。 這是您在步驟5中建立的KeyStore密碼，但是是在設定期間發送給您的歡迎電子郵件中提供的KeyStore檔案密碼Adobe。 __&#x200B;如果您未收到KeyStore檔案密碼，請聯絡Adobe客戶支援。
   * 在&#x200B;**[!UICONTROL 私密金鑰密碼]**&#x200B;欄位中，輸入私密金鑰密碼（可能與前一步驟中提供的私密金鑰密碼相同）。 Adobe會在布建期間，在傳送給您的歡迎電子郵件中提供私密金鑰密碼。 如果您未收到私密金鑰密碼，請聯絡Adobe客戶支援。
   * 在&#x200B;**[!UICONTROL 私鑰別名]**&#x200B;欄位中，輸入私鑰別名。 例如， `companyname-alias`。 Adobe會在布建期間，於您收到的歡迎電子郵件中提供私密金鑰別名。 如果您未收到私密金鑰別名，請聯絡Adobe客戶支援。

   ![edit_settings_fordynamic-media-replication2](assets/edit_settings_fordynamic-media-replication2.png)

1. 點選「**[!UICONTROL 儲存並關閉]**」 ，將變更儲存至此使用者。

   接下來，您需要[配置複製代理。](#configuring-the-replication-agent)

### 設定複寫代理 {#configuring-the-replication-agent}

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具>部署>復寫>製作上的代理]**。
1. 在製作頁面上的代理，點選&#x200B;**[!UICONTROL Dynamic Media混合影像復寫(s7delivery)]**。
1. 點選「**[!UICONTROL Edit]**」。
1. 點選「**[!UICONTROL Settings]**」標籤，然後輸入以下內容：

   * **[!UICONTROL 已啟用]**  — 選中此複選框以啟用複製代理。
   * **[!UICONTROL 地區]**  — 設為適當的地區：北美、歐洲或亞洲
   * **[!UICONTROL 租用戶ID]**  — 此值是發佈至復寫服務的公司/租用戶名稱。此值是Adobe在布建期間傳送給您的歡迎電子郵件中提供的租用戶ID。 如果您未收到此訊息，請聯絡Adobe客戶支援。
   * **[!UICONTROL 密鑰儲存別名]**  — 此值與在設定驗證中生成密鑰時設定的**新別名**值 [相同](#setting-up-authentication);例如 `replication`。（請參閱[設定驗證](#setting-up-authentication)中的步驟7。）
   * **[!UICONTROL 金鑰存放密碼]**  — 這是您點選「建立金鑰存放區」時建立的金 **[!UICONTROL 鑰存放密碼]**。Adobe未提供此密碼。 請參閱[設定驗證](#setting-up-authentication)的步驟5。

   下圖顯示了包含示例資料的複製代理：

   ![chlimage_1-509](assets/chlimage_1-509.png)

1. 點選&#x200B;**[!UICONTROL 確定]**。

### 驗證Dynamic Media的復寫代理 {#validating-the-replication-agent-for-dynamic-media}

要驗證動態媒體的複製代理，請執行以下操作：

點選「**[!UICONTROL 測試連線]**」。 輸出示例如下：

```shell
11.03.2016 10:57:55 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
11.03.2016 10:57:55 - * Auth User: replication-receiver
11.03.2016 10:57:55 - * HTTP Version: 1.1
11.03.2016 10:57:55 - * Using OAuth 2.0 Authorization Grants
11.03.2016 10:57:55 - * OAuth 2.0 User: dynamic-media-replication
11.03.2016 10:57:55 - * OAuth 2.0 Token: '*****' initialized
11.03.2016 10:57:55 - Publishing: POST[https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=xfpuu-6613]
11.03.2016 10:57:55 - Publish response: OK[]
11.03.2016 10:57:55 - Transfer succeeded in 141 ms for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
-------------------------------------------------------------------------------------------------------------------------------
Replication test succeeded
```

>[!NOTE]
您也可以執行下列其中一項操作來檢查：
* 檢查復寫記錄，確認資產已復寫。
* 發佈影像。 點選影像，然後在下拉式選單中選取「**[!UICONTROL 檢視器]**」。 選取檢視器預設集，然後點選&#x200B;**[!UICONTROL URL]**，然後複製URL並貼到瀏覽器中，以確認您可以看到影像。


### 排解驗證疑難問題 {#troubleshooting-authentication}

在設定驗證時，以下是您在其解決方案中可能遇到的問題。 在檢查這些選項之前，請確保已設定複製。

#### 問題：HTTP狀態代碼401，帶消息 — 需要授權 {#problem-http-status-code-with-message-authorization-required}

此問題可能是由於未能為`dynamic-media-replication`用戶設定KeyStore所致。

```shell
Replication test to s7delivery:https://s7bern.macromedia.com:8580/is-publish/
17.06.2016 18:54:43 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}
17.06.2016 18:54:43 - * Auth User: replication-receiver
17.06.2016 18:54:43 - * HTTP Version: 1.1
17.06.2016 18:54:43 - * Using OAuth 2.0 Authorization Grants
17.06.2016 18:54:43 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 18:54:43 - No OAuth token available. OAuth not initialized
17.06.2016 18:54:43 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 18:54:43 - Publishing: POST[https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough]
17.06.2016 18:54:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
17.06.2016 18:54:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309,
 userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
```

**解決方案**:檢查是否已 `KeyStore` 儲存至 **[!UICONTROL dynamic-media-]** replicationuser，並且提供正確的密碼。

#### 問題：無法解密密鑰 — 無法解密資料 {#problem-could-not-decrypt-key-could-not-decrypt-data}

```xml
Replication test to s7delivery:https://<localhost>:8580/is-publish/
17.06.2016 19:00:16 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}
17.06.2016 19:00:16 - * Auth User: replication-receiver
17.06.2016 19:00:16 - * HTTP Version: 1.1
17.06.2016 19:00:16 - * Using OAuth 2.0 Authorization Grants
17.06.2016 19:00:16 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 19:00:16 - No OAuth token available. OAuth not initialized
17.06.2016 19:00:16 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 19:00:16 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}. java.lang.SecurityException: java.security.UnrecoverableKeyException: Could not decrypt key: Could not decrypt data.
```

**解決方案**:檢查密碼。複製代理中保存的密碼與用於建立密鑰庫的密碼不同。

#### 問題：InvalidAlgorithmParameterException {#problem-invalidalgorithmparameterexception}

此問題是由AEM Author例項中的設定錯誤所造成。 作者上的java程式未取得正確的`javax.net.ssl.trustStore`。 在復寫記錄中，您會看到此錯誤：

```shell
14.04.2016 09:37:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
14.04.2016 09:37:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

或錯誤日誌：

```shell
07.25.2019 12:00:59.893 *ERROR* [sling-threadpool-db2763bb-bc50-4bb5-bb64-10a09f432712-(apache-sling-job-thread-pool)-90-com_day_cq_replication_job_s7delivery(com/day/cq/replication/job/s7delivery)] com.day.cq.replication.Agent.s7delivery.queue Error during processing of replication.
 
java.io.IOException: Failed to execute request 'https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
        at com.scene7.is.catalog.service.publish.atomic.PublishingServiceHttp.executePost(PublishingServiceHttp.scala:195)
```

**解決方案**:請確定AEM Author上的java程式將系統屬性 **-Djavax.net.ssl.trustStore=** 設為有效的信任存放區。

#### 問題：KeyStore未設定或未初始化 {#problem-keystore-is-either-not-set-up-or-it-is-not-initialized}

此問題可能是由Hotfix或覆寫&#x200B;**[!UICONTROL dynamic-media-user]**&#x200B;或&#x200B;**[!UICONTROL keystore]**&#x200B;節點的功能套件所造成。

複製日誌示例：

```shell
Replication test to s7delivery:https://replicate-na.assetsadobe.com/is-publish
02.08.2016 14:37:44 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}
02.08.2016 14:37:44 - * Auth User: replication-receiver
02.08.2016 14:37:44 - * HTTP Version: 1.1
02.08.2016 14:37:44 - * Using OAuth 2.0 Authorization Grants
02.08.2016 14:37:44 - * OAuth 2.0 User: dynamic-media-replication
02.08.2016 14:37:44 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}. com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised key store for user dynamic-media-replication
```

**解決方案**:

1. 導覽至&#x200B;**[!UICONTROL 使用者管理]**&#x200B;頁面：

   `localhost:4502/libs/granite/security/content/useradmin.html`
1. 在&#x200B;**[!UICONTROL 使用者管理]**&#x200B;頁面上，導覽至&#x200B;**[!UICONTROL dynamic-media-replication]**&#x200B;使用者，然後點選以開啟。
1. 點選&#x200B;**[!UICONTROL KeyStore]**&#x200B;標籤。 如果出現&#x200B;**[!UICONTROL Create KeyStore]**&#x200B;按鈕，則您需要先重做[Setting up Authentication](#setting-up-authentication)下的步驟。
1. 如果您必須重做&#x200B;**[!UICONTROL KeyStore]**&#x200B;設定，則可能需要再次執行[配置複製代理](config-dynamic.md#configuring-the-replication-agent)。

   重新設定s7delivery復寫代理程式。

   `localhost:4502/etc/replication/agents.author/s7delivery.html`

1. 點選&#x200B;**[!UICONTROL 測試連線]**&#x200B;以驗證設定有效。

#### 問題：發佈代理程式使用SSL而非OAuth {#problem-publish-agent-is-using-ssl-instead-of-oauth}

此問題可能是由Hotfix或未正確安裝或覆寫設定的Feature Pack所造成。

複製日誌示例：

```shell
01.08.2016 18:42:59 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}
01.08.2016 18:42:59 - * Auth User: replication-receiver
01.08.2016 18:42:59 - * HTTP Version: 1.1
01.08.2016 18:42:59 - * Using Client Auth SSL alias - replication-receiver *
01.08.2016 18:42:59 - Publishing: POST[https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=altayerstaging]
01.08.2016 18:42:59 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
01.08.2016 18:42:59 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
```

**解決方案：**

1. 在 AEM 中，點選&#x200B;**[!UICONTROL 「工具」>「一般」>「CRXDE Lite」]**。

   `localhost:4502/crx/de/index.jsp`

1. 導覽至&#x200B;**[!UICONTROL s7delivery復寫代理]**&#x200B;節點。

   `localhost:4502/crx/de/index.jsp#/etc/replication/agents.author/s7delivery/jcr:content`

1. 將此設定添加到複製代理（值設定為&#x200B;**[!UICONTROL True]**&#x200B;的布爾值）:

   `enableOauth=true`

1. 在頁面的左上角附近，點選「**[!UICONTROL Save All]**」。

### 測試您的設定 {#testing-your-configuration}

Adobe建議您對配置執行端對端測試。

開始此測試之前，請確定您已完成下列操作：

* 新增影像預設集。
* 在&#x200B;**[!UICONTROL Cloud Services]**&#x200B;下配置&#x200B;**Dynamic Media配置（6.3之前）**。 此測試需要影像服務URL

若要測試您的設定：

1. 上傳影像資產。 （在「資產」中，點選「**[!UICONTROL 建立>檔案」]**&#x200B;並選取檔案。）
1. 等待工作流程完成。
1. 發佈影像資產。 （選取資產，然後點選&#x200B;**[!UICONTROL 快速發佈]**。）
1. 開啟影像並點選「**[!UICONTROL 轉譯]**」，導覽至該影像的轉譯。

   ![chlimage_1-510](assets/chlimage_1-510.png)

1. 選取任何動態轉譯。
1. 點選&#x200B;**[!UICONTROL URL]**&#x200B;以取得此資產的URL。
1. 導覽至選取的URL並檢查影像是否如預期般運作。

另一種測試已傳送資產的方法，是將req=exists附加至URL。

## 設定Dynamic MediaCloud Services {#configuring-dynamic-media-cloud-services}

Dynamic Media雲端服務提供雲端服務的支援，例如混合發佈及傳送影像和視訊、視訊分析、視訊編碼等。

在設定中，您需要輸入註冊ID、視訊服務URL、影像服務URL、復寫服務URL，並設定驗證。 您應已在帳戶布建過程中收到所有這些資訊。 若您未收到此資訊，請連絡您的Adobe Experience Manager管理員或Adobe技術支援以取得此資訊。

>[!NOTE]
設定Dynamic MediaCloud Services之前，請務必先設定您的發佈執行個體。 您也必須先設定復寫，才能設定Dynamic MediaCloud Services。

**若要設定dynamic media雲端服務**:

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具>Cloud Services>Dynamic Media設定(Pre-6.3)]**。
1. 在&#x200B;**[!UICONTROL Dynamic Media Configuration Browser]**&#x200B;頁面的左窗格中，選取&#x200B;**[!UICONTROL global]**，然後點選&#x200B;**[!UICONTROL Create]**。
1. 在&#x200B;**[!UICONTROL 建立Dynamic Media設定]**&#x200B;對話方塊的&#x200B;**[!UICONTROL Title]**&#x200B;欄位中，輸入標題。
1. 如果您要為視訊設定Dynamic Media,

   * 在&#x200B;**[!UICONTROL 註冊ID]**&#x200B;欄位中，鍵入您的註冊ID。
   * 在&#x200B;**[!UICONTROL 視訊服務URL]**&#x200B;欄位中，輸入Dynamic Media閘道的視訊服務URL。

1. 如果您要配置Dynamic Media以進行影像處理，請在&#x200B;**[!UICONTROL 影像服務URL]**&#x200B;欄位中，輸入Dynamic Media閘道的影像服務URL。
1. 點選&#x200B;**[!UICONTROL 儲存]**&#x200B;以返回Dynamic Media設定瀏覽器頁面。
1. 點選AEM標誌以存取全域導覽主控台。

## 設定視訊報表 {#configuring-video-reporting}

您可以使用Dynamic Media — 混合模式，在AEM的多個安裝間設定視訊報表。

**使用時機：** 設定Dynamic Media設定( **[!UICONTROL 6.3之前)]**&#x200B;時，已開始使用許多功能，包括視訊報表。此設定會在地區Analytics公司中建立報表套裝。 如果您設定多個製作節點，則會為每個節點分別建立報表套裝。 因此，安裝之間的報告資料不一致。 此外，如果每個製作節點參照相同的混合發佈伺服器，則上次安裝製作時會變更所有視訊報表的目標報表套裝。 此問題會使用過多的報表套裝來過度載入Analytics系統。

**快速入門：** 完成下列三個工作以設定視訊報表。

1. 在第一個製作節點上設定&#x200B;**[!UICONTROL Dynamic Media設定（6.3之前）]**&#x200B;後，建立[!DNL Video Analytics]預設套件。 此初始任務很重要，因為它允許新配置繼續使用相同的報表套裝。
1. 將[!DNL Video Analytics]預設套件安裝至您設定Dynamic Media設定（6.3之前）之前的任何&#x200B;***新***&#x200B;製作節點&#x200B;***。***

1. 驗證和調試包安裝。

### 在設定第一個製作節點後建立[!DNL Video Analytics]預設套件 {#creating-a-video-analytics-preset-package-after-configuring-the-first-author-node}

完成此任務後，您將擁有包含[!DNL Video Analytics]預設集的包檔案。 這些預設集包含報表套裝、追蹤伺服器、追蹤命名空間，以及Marketing Cloud組織ID（若有）。

1. 如果您尚未這麼做，請設定&#x200B;**[!UICONTROL Dynamic Media設定（6.3之前）]**。
1. （選用）檢視並複製&#x200B;**[!UICONTROL 報表套裝ID]**（您必須擁有JCR的存取權）。 雖然不需要&#x200B;**[!UICONTROL 報表套裝ID]**，但可讓驗證更輕鬆。
1. 使用&#x200B;**[!UICONTROL 包管理器]**&#x200B;建立包。
1. 編輯套件以包含篩選器。

   在AEM中：`/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

1. 建立套件。
1. 下載或共用[!DNL Video Analytics]預設套件，以便與後續的新製作節點共用。

### 先安裝[!DNL Video Analytics]預設套件，再設定其他製作節點 {#installing-the-video-analytics-preset-package-before-you-configure-additional-author-nodes}

請務必在&#x200B;_之前完成&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**的此任務。_&#x200B;若未這麼做，將會建立另一個未使用的報表套裝。 此外，即使視訊報表仍可正常運作，資料收集仍未最佳化。

請確定第一個製作節點的[!DNL Video Analytics]預設套件可在新的製作節點上存取。

1. 將您之前建立的[!DNL Video Analytics]預設套件上傳至&#x200B;**[!UICONTROL 套件管理器]**。
1. 安裝[!DNL Video Analytics]預設包。
1. 配置&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**。

### 驗證和調試包安裝 {#verifying-and-debugging-the-package-installation}

1. 執行下列任一操作以驗證軟體包，並在必要時調試軟體包安裝：

   * **透過 [!DNL Video Analytics] JCRT檢查預設集**
，或透 [!DNL Video Analytics] 過JCR檢查預設集，您必須擁有CRXDE Lite **[!UICONTROL 的存取權]**。

      AEM — 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中，導覽至`/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata  `

      即`http://localhost:4502/crx/de/index.jsp#/conf/global/settings/dam/dm/presets/analytics/jcr%3Acontent/userdata`

      如果您在「製作」節點上沒有&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;的存取權，可以透過「發佈」伺服器檢查預設集。

   * **透過影 [!DNL Video Analytics] 像伺服器檢查預設集**

      您可以發出影像伺服器`req=userdata`請求，直接驗證[!DNL Video Analytics]預設集。

      例如，若要查看「作者」節點上的[!DNL Video Analytics]預設集，您可以提出下列要求：

      `http://localhost:4502/is/image/conf/global/settings/dam/dm/presets/analytics?req=userdata`

      若要驗證發佈伺服器上的預設集，您可以向發佈伺服器發出類似的直接請求。 「製作」和「發佈」節點上的回應相同。 回應看起來類似下列：

      ```
      marketingCloudOrgId=0FC4E86B573F99CC7F000101
       reportSuite=aemaem6397618-2018-05-23
       trackingNamespace=aemvideodal
       trackingServer=aemvideodal.d2.sc.omtrdc.net
      ```

   * **透過AEM [!DNL Video Analytics] 中的「視訊報表」工具檢查預設集**

      點選&#x200B;**[!UICONTROL 工具>資產>視訊報表]** `http://localhost:4502/mnt/overlay/dam/gui/content/s7dam/videoreports/videoreport.html`

      如果您看見下列錯誤訊息，表示報表套裝可供使用，但未填入。 在系統收集任何資料之前，新安裝中的此錯誤是正確的，也是必要的。

      ![screen_shot_2018-05-23at52254pm](assets/screen_shot_2018-05-23at52254pm.png)
   若要產生報表資料，請上傳並發佈一個視訊。 使用&#x200B;**[!UICONTROL 複製URL]**&#x200B;並至少執行一次視訊。

   請注意，從視訊檢視器使用狀況填入報表資料可能需要12小時。

   如果發生錯誤，且報表套裝未正確設定，則會顯示下列警報。

   ![screen_shot_2018-05-23at52612pm](assets/screen_shot_2018-05-23at52612pm.png)

   如果在您設定&#x200B;**[!UICONTROL Dynamic Media設定（6.3之前）]**&#x200B;服務之前執行視訊報表，也會顯示此錯誤。

### 疑難排解視訊報表設定 {#troubleshooting-the-video-reporting-configuration}

* 安裝期間，有時連線至Analytics API伺服器會逾時。 安裝會重試連線20次，但仍會失敗。 發生此情況時，記錄檔會記錄多個錯誤。 搜尋 `SiteCatalystReportService`.
* 若先未安裝[!DNL Video Analytics]預設集套件，可能會建立新的報表套裝。
* 從AEM 6.3升級至AEM 6.4或AEM 6.4.1，然後設定&#x200B;**[!UICONTROL Dynamic Media設定（6.3之前）]**&#x200B;仍會建立報表套裝。 此問題已知且已在AEM 6.4.2中修正。

### 關於[!DNL Video Analytics]預設集 {#about-the-video-analytics-preset}

[!DNL Video Analytics]預設集（有時簡稱為分析預設集）會儲存在Dynamic Media中的檢視器預設集旁。 基本上與檢視器預設集相同，但包含用來設定AppMeasurement和視訊心率報表的資訊。

預設集的屬性如下：

* **[!UICONTROL reportSuite]**
* **[!UICONTROL trackingServer]**
* **[!UICONTROL trackingNamespace]**
* **[!UICONTROL marketingCloudOrgId]** (舊版AEM中不存在)

AEM 6.4及更新版本會在`/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`儲存此預設集

## 複製目錄設定 {#replicating-catalog-settings}

您必須透過JCR，在設定程式中發佈自己的預設目錄設定。 要複製目錄設定：

1. 在「終端機」視窗中，執行下列動作：

   `curl -u admin:admin localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

1. 在AEM中，導覽至&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中的下列位置（需要管理員權限）:

   `https://<server>:<port>/crx/de/index.jsp#/conf/global/settings/dam/dm/imageserver/`

1. 點選「**[!UICONTROL 復寫]**」標籤。
1. 點選&#x200B;**[!UICONTROL 復寫]**。

## 複製查看器預設集 {#replicating-viewer-presets}

若要使用檢視器預設集傳送資產，您必須復寫/發佈檢視器預設集。 （必須啟動&#x200B;_和_&#x200B;所有檢視器預設集，才能取得資產的URL或內嵌程式碼。） 如需詳細資訊，請參閱[發佈檢視器預設集](managing-viewer-presets.md#publishing-viewer-presets) 。

>[!NOTE]
依預設，當您選取&#x200B;**[!UICONTROL 轉譯]**&#x200B;時，系統會顯示各種轉譯，當您在資產的詳細資料檢視中選取&#x200B;**[!UICONTROL 檢視器]**&#x200B;時，系統會顯示各種檢視器預設集。 您可以增加或減少顯示的數量。 請參閱[增加顯示](/help/assets/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display)或[的影像預設集數目增加顯示](/help/assets/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display)的檢視器預設集數目。

## 篩選復寫資產 {#filtering-assets-for-replication}

在非Dynamic Media部署中，您會從AEM製作環境復寫&#x200B;_所有_&#x200B;資產（包括影像和視訊）至AEM發佈節點。 此工作流程是必要的，因為AEM發佈伺服器也會傳送資產。

不過，在Dynamic Media部署中，由於資產是透過雲端傳送，因此不需要將這些相同的資產複製到AEM發佈節點。 這樣的「混合發佈」工作流程可避免額外的儲存成本和更長的複製資產處理時間。 AEM發佈節點會繼續提供其他內容，例如Dynamic Media檢視器、網站頁面和靜態內容。

除複製資產外，還會複製下列非資產：

* Dynamic Media傳送設定：`/conf/global/settings/dam/dm/imageserver/configuration/jcr:content/settings`
* 影像預設集: `/conf/global/settings/dam/dm/presets/macros`
* 檢視器預設集: `/conf/global/settings/dam/dm/presets/viewer`

這些篩選器可讓您透過&#x200B;_排除_&#x200B;資產，避免複製到AEM發佈節點。

### 針對復寫使用預設資產篩選器 {#using-default-asset-filters-for-replication}

如果您是在生產&#x200B;_或_ 2)中使用Dynamic Media for 1)影像和視訊，則可以使用我們依現狀提供的預設篩選器。 下列篩選器預設為作用中：

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>篩選</strong></td> 
   <td><strong>Mime 類型</strong></td> 
   <td><strong>轉譯</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media影像傳送</td> 
   <td><p>濾鏡影像</p> <p>篩選集</p> <p> </p> </td> 
   <td><p>開頭為<strong>image/</strong></p> <p>包含<strong>application/</strong>，並以<strong>set</strong>結尾。</p> </td> 
   <td>現成可用的「篩選影像」（套用至單一影像資產，包括互動式影像）和「篩選集」（套用至回轉集、影像集、混合媒體集和轉盤集）將： 
    <ul> 
     <li>包含PTIFF影像和復寫中繼資料（任何以<strong>cqdam</strong>開頭的轉譯）。</li> 
     <li>從復寫中排除原始影像和靜態影像轉譯。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media影片傳送</td> 
   <td>filter-video</td> 
   <td>開頭為<strong>video/</strong></td> 
   <td>現成可用的「filter-video」將： 
    <ul> 
     <li>包含復寫的代理視訊轉譯、視訊縮圖/海報影像、中繼資料（在父視訊和視訊轉譯處）（任何以<strong>cqdam</strong>開頭的轉譯）。</li> 
     <li>排除原始視訊和靜態縮圖轉譯。<br /> <br /> <strong>注意：</strong> 代理視訊轉譯不包含二進位檔，而只是節點屬性。因此，對發佈者存放庫大小沒有影響。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media Classic整合</td> 
   <td><p>濾鏡影像</p> <p>篩選集</p> <p>filter-video</p> </td> 
   <td><p>開頭為<strong>image/</strong></p> <p>包含<strong>application/</strong>，並以<strong>set</strong>結尾。</p> <p>開頭為<strong>video/</strong></p> </td> 
   <td><p>您可以配置傳輸URI以指向您的AEM發佈伺服器，而不是AdobeDynamic Media雲複製服務URL。 設定此篩選器可讓Dynamic Media Classic傳送資產，而非AEM發佈例項。</p> <p>現成可用的「filter-images」、「filter-sets」和「filter-video」將：</p> 
    <ul> 
     <li>包含PTIFF影像、代理視訊轉譯和復寫的中繼資料。 但是，由於JCR中不存在這些JCR(針對執行AEM - Dynamic Media Classic整合的使用者)，因此IT無法有效運作。</li> 
     <li>排除原始影像、靜態影像轉譯、原始視訊和靜態縮圖轉譯之外。 相反，Dynamic Media Classic將會傳送影像和視訊資產。</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
篩選器會套用至mime類型，且不能是路徑特定。

### 為僅限視訊的部署設定資產篩選器 {#setting-up-asset-filters-for-video-only-deployments}

如果您只將Dynamic Media用於視訊，請依照下列步驟設定復寫的資產篩選器：

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具>部署>復寫>製作上的代理]**。
1. 在製作頁面上，點選&#x200B;**[!UICONTROL 預設代理（發佈）]**。
1. 點選「**[!UICONTROL Edit]**」。
1. 在&#x200B;**[!UICONTROL 代理設定]**&#x200B;對話框的[!UICONTROL 設定]頁簽中，選中&#x200B;**[!UICONTROL 啟用]**&#x200B;以開啟代理。
1. 點選&#x200B;**[!UICONTROL 確定]**。
1. 在 AEM 中，點選&#x200B;**[!UICONTROL 「工具」>「一般」>「CRXDE Lite」]**。
1. 在左資料夾樹中，導航到`/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`
1. 找到[!UICONTROL filter-video]，按一下右鍵並選擇&#x200B;**[!UICONTROL Copy]**。
1. 在左資料夾樹中，導航到`/etc/replication/agents.author/publish`
1. 找到[!UICONTROL jcr:content]，按一下右鍵並選擇&#x200B;**[!UICONTROL 貼上]**。

這會設定AEM發佈例項以傳送視訊海報影像以及播放所需的視訊中繼資料，而視訊本身是由Dynamic Media雲端服務傳送。 篩選器也會從復寫中排除發佈執行個體不需要的原始視訊和靜態縮圖轉譯。

### 在非生產部署中設定影像處理的資產篩選器 {#setting-up-asset-filters-for-imaging-in-non-production-deployments}

如果您在非生產部署中使用Dynamic Media進行影像處理，請依照下列步驟設定復寫的資產篩選器：

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具>部署>復寫>製作上的代理]**。
1. 在製作頁面上，點選&#x200B;**[!UICONTROL 預設代理（發佈）]**。
1. 點選「**[!UICONTROL Edit]**」。
1. 在&#x200B;**[!UICONTROL 代理設定]**&#x200B;對話框的&#x200B;**[!UICONTROL 設定]**&#x200B;頁簽中，選中&#x200B;**[!UICONTROL 啟用]**&#x200B;以開啟代理。
1. 點選&#x200B;**[!UICONTROL 確定]**。
1. 在 AEM 中，點選&#x200B;**[!UICONTROL 「工具」>「一般」>「CRXDE Lite」]**。
1. 在左資料夾樹中，導航到`/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`

   ![image-2018-01-16-10-22-40-410](assets/image-2018-01-16-10-22-40-410.png)

1. 找到&#x200B;**[!UICONTROL filter-images]**，按一下右鍵並選擇&#x200B;**[!UICONTROL Copy]**。
1. 在左資料夾樹中，導航到`/etc/replication/agents.author/publish`
1. 找到&#x200B;**[!UICONTROL jcr:content]**，按一下右鍵並選擇&#x200B;**[!UICONTROL 建立>建立節點]**。 輸入`nt:unstructured`類型的名稱`damRenditionFilters`。
1. 找到[!UICONTROL `damRenditionFilters`]，按一下右鍵並選擇&#x200B;**[!UICONTROL 貼上]**。

這會設定AEM發佈例項，將影像傳送至您的非生產環境。 篩選器也會從復寫中排除原始影像和靜態轉譯，這在發佈執行個體上不需要。

>[!NOTE]
如果作者中有許多不同的篩選器，則每個代理都需要指派不同的使用者。 Granite程式碼會強制使用每個使用者一個篩選器模型。 每個篩選器設定的使用者一律不同。
如果您在伺服器上使用多個篩選器（例如，一個要發佈的復寫篩選器，另一個要傳送的篩選器），則您需要確保這兩個篩選器在&#x200B;**[!UICONTROL jcr:content]**&#x200B;節點中為其指派不同的&#x200B;**userId**。 請參閱下圖：

![image-2018-01-16-10-26-28-465](assets/image-2018-01-16-10-26-28-465.png)

### 自訂復寫的資產篩選器 {#customizing-asset-filters-for-replication}

（可選）要自訂復寫的資產篩選器：

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具>一般>CRXDE Lite]**。
1. 在左側資料夾樹中，導覽至`/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`以檢閱篩選器。

   ![chlimage_1-511](assets/chlimage_1-511.png)

1. 若要定義篩選器的Mime類型，可以按如下方式找到Mime類型：

   在左側邊欄中，展開&#x200B;**[!UICONTROL content > dam > &lt;`locate_your_asset`> > jcr:content > metadata]**，然後在表格中找出`dc:format`。

   下圖是資產`dc:format`路徑的範例。

   ![chlimage_1-512](assets/chlimage_1-512.png)

   請注意，資產`Fiji Red.jpg`的`dc:format`為`image/jpeg`。

   若要讓此篩選器套用至所有影像，而不論其格式為何，請將值設為`image/*`，其中`*`是套用至任何格式之所有影像的規則運算式。

   要讓篩選器僅應用於類型JPEG的影像，請輸入`image/jpeg`值。

1. 定義您要包含或排除在復寫中的轉譯。

   可用於篩選複製的字元包括：

<table> 
 <tbody> 
  <tr> 
   <td><strong>要使用的字元</strong></td> 
   <td><strong>如何篩選資產以進行復寫</strong></td> 
  </tr> 
  <tr> 
   <td>*</td> 
   <td>通配符<br /> </td> 
  </tr> 
  <tr> 
   <td>+</td> 
   <td>包含復寫資產。</td> 
  </tr> 
  <tr> 
   <td>-</td> 
   <td>排除復寫中的資產。</td> 
  </tr> 
 </tbody> 
</table>

導航到 `content/dam/<locate_your_asset>/jcr:content/renditions`.

下圖是資產轉譯的範例。

![chlimage_1-513](assets/chlimage_1-513.png)

使用上述範例，如果您只想複製PTIFF(金字塔TIFF)，則可輸入`+cqdam,*`，其中包含以`cqdam`開頭的所有轉譯。 在範例中，該轉譯為`cqdam.pyramid.tiff`。

如果只想複製原始檔案，則輸入`+original`。

## 配置Dynamic Media Image Server設定 {#configuring-dynamic-media-image-server-settings}

設定Dynamic Media Image Server包括編輯Adobe CQ Scene7 ImageServer套件組合和Adobe CQ Scene7 PlatformServer套件組合。

>[!NOTE]
Dynamic Media在啟用](#enabling-dynamic-media)後即可運作[。 不過，您可以選擇配置Dynamic Media Image Server以符合特定規格或需求，以微調安裝。

**先決條件**: __ 配置Dynamic Media Image Server之前，請確保Windows的VM包括Microsoft Visual C++庫的安裝。必須有這些程式庫才能執行Dynamic Media Image Server。 您可以在[此處](https://www.microsoft.com/en-us/download/details.aspx?id=26999)下載Microsoft Visual C++ 2010可再發行套件(x64)。

**若要設定Dynamic Media影像伺服器設定**:

1. 在AEM的左上角，點選&#x200B;**[!UICONTROL Adobe Experience Manager]**&#x200B;以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具>作業> Web Console]**。
1. 在「**[!UICONTROL Adobe Experience Manager Web Console設定]**」頁面上，點選「**[!UICONTROL OSGi >設定]** 」，列出AEM中目前執行的所有套件組合。

   Dynamic Media傳送伺服器位於清單中的下列名稱中：

   * **[!UICONTROL Adobe CQ Scene7 ImageServer]**
   * **[!UICONTROL Adobe CQ Scene7 PlatformServer]**

1. 在套件組合清單中，在&#x200B;**[!UICONTROL Adobe CQ Scene7 ImageServer]**&#x200B;右側，點選&#x200B;**[!UICONTROL Edit]**&#x200B;圖示。
1. 在&#x200B;**[!UICONTROL Adobe CQ Scene7 ImageServer]**&#x200B;對話方塊中，設定下列設定值：

   >[!NOTE]
   在大多數情況下，不需要變更預設值。 但是，如果您確實更改了預設值，則必須重新啟動包，更改才會生效。

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性</strong></td> 
   <td><strong>預設值</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>TcpPort.name</td> 
   <td><code><em>empty</em></code></td> 
   <td>用於與ImageServer進程通信的埠號。 預設情況下，自動檢測空閒埠。</td> 
  </tr> 
  <tr> 
   <td>AllowRemoteAccess.name</td> 
   <td><code><em>empty</em></code></td> 
   <td><p>允許或不允許遠程訪問ImageServer進程。 如果為false，則映像伺服器僅偵聽本地主機。</p> <p>指向本地主機的預設外置程式設定需要指定特定VM實例的實際域或IP地址。 原因是本地主機可能指向VM的父系統。</p> <p>VM的域或IP地址可能需要一個主機檔案條目，以便它能夠自行解析。</p> </td> 
  </tr> 
  <tr> 
   <td>MaxRenderRgnPixels</td> 
   <td>16兆帕</td> 
   <td>所呈現的最大大小（百萬像素）。</td> 
  </tr> 
  <tr> 
   <td>MaxMessageSize</td> 
   <td>16 MB</td> 
   <td>已傳送的最大消息大小(MB)。</td> 
  </tr> 
  <tr> 
   <td>RandomAccessUrlTimeout</td> 
   <td>20</td> 
   <td>逾時值，表示ImageServer將等待JCR響應範圍內的磁貼請求的時間（秒）。</td> 
  </tr> 
  <tr> 
   <td>工作線程</td> 
   <td>10</td> 
   <td>工作線程數。</td> 
  </tr> 
 </tbody> 
</table>

1. 點選&#x200B;**[!UICONTROL 儲存]**。
1. 在套件組合清單中，在&#x200B;**[!UICONTROL Adobe CQ Scene7 PlatformServer]**&#x200B;右側，點選&#x200B;**[!UICONTROL Edit]**&#x200B;圖示。
1. 在&#x200B;**[!UICONTROL Adobe CQ Scene7 PlatformServer]**&#x200B;對話方塊中，設定下列預設值選項：

   >[!NOTE]
   Dynamic Media Image Server使用其自己的磁碟快取來快取響應。 AEM HTTP快取和Dispacher無法用來快取來自Dynamic Media Image Server的回應。

   | **屬性** | **預設值** | **說明** |
   |---|---|---|
   | **[!UICONTROL 已啟用快取]** | 已核取 | 是否啟用響應快取。 |
   | **[!UICONTROL 快取根]** | 快取 | 回應快取資料夾的一或多個路徑。 相對路徑會針對內部s7影像處理套件資料夾進行解析。 |
   | **[!UICONTROL 快取最大大小]** | 200000000 | 響應快取的最大大小（以位元組為單位）。 |
   | **[!UICONTROL 快取最大條目數]** | 100000 | 快取中允許的最大條目數。 |

### 預設資訊清單設定 {#default-manifest-settings}

預設資訊清單可讓您設定用於產生Dynamic Media傳送回應的預設值。 您可以微調質量(JPEG質量、解析度、重採樣模式)、快取（過期），並防止渲染太大的影像(defaultpix、defaultthumbpix、maxpix)。

預設資訊清單配置的位置取自&#x200B;**[!UICONTROL Adobe CQ Scene7 PlatformServer]**&#x200B;套件組合的&#x200B;**[!UICONTROL 目錄根]**&#x200B;預設值。 預設情況下，此值位於&#x200B;**[!UICONTROL Tools > General > CRXDE Lite]**&#x200B;中的以下路徑：

`/conf/global/settings/dam/dm/imageserver/`

![configimageservercrxdelite](assets/configimageservercrxdelite.png)

您可以輸入新值，以變更屬性的值，如下表所述。

完成對預設資訊清單的更改後，在頁面的左上角，點選&#x200B;**[!UICONTROL Save All]**。

請務必點選&#x200B;**[!UICONTROL 存取控制]**&#x200B;標籤（位於&#x200B;**[!UICONTROL 屬性]**&#x200B;標籤的右側），然後為每個人和動態媒體復寫使用者將存取控制權限設為`jcr:read`。

![configimageserverxdeliteaccesscontroltab](assets/configimageservercrxdeliteaccesscontroltab.png)

資訊清單設定表及其預設值：

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性</strong></td> 
   <td><strong>預設值</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>bkgcolor</td> 
   <td>FFFFFF</td> 
   <td><p>預設背景顏色。 RGB值，用於填入不含實際影像資料的回覆影像的任何區域。</p> <p>另請參閱影像伺服API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html">BkgColor</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>defaultpix</td> 
   <td>三十萬零三百</td> 
   <td><p>預設視圖大小。 如果請求未使用wid=、hei=或scl=明確指定檢視大小，則伺服器會限制回覆影像不大於此寬度和高度。</p> <p>指定為兩個整數，0或更大，以逗號分隔。 寬度和高度（像素）。 可將任一或兩個值設為0，以保持它們不受約束。 不適用於巢狀/內嵌的請求。</p> <p>另請參閱影像伺服API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html">DefaultPix</a>。</p> <p>不過，您通常是使用檢視器預設集或影像預設集來傳送資產。 Defaultpix僅適用於未使用檢視器預設集或影像預設集的資產。</p> </td> 
  </tr> 
  <tr> 
   <td>defaulthumbpix</td> 
   <td>十萬零一百</td> 
   <td><p>預設縮圖大小。 用於縮圖請求(req=tmb)，而非屬性：:DefaultPix。</p> <p>如果縮圖請求(req=tmb)未顯式指定大小，則伺服器將答復影像限制為不大於此寬度和高度，而未顯式指定使用wid=、hei=或scl=的視圖大小。</p> <p>指定為兩個整數，0或更大，以逗號分隔。 寬度和高度（像素）。 可將任一或兩個值設為0，以保持它們不受約束。 </p> <p>不適用於巢狀/內嵌的請求。</p> <p>另請參閱影像伺服API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html">DefaultThumbPix</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td>過期</td> 
   <td>36000000</td> 
   <td><p>預設的客戶端快取存留時間。 提供預設過期時間間隔，以備特定目錄記錄不包含有效的目錄：：過期值時使用。</p> <p>實數，0或更高。 自回覆資料產生以來直到過期的毫秒數。 設為0一律會立即讓回覆影像過期，這會有效停用用戶端快取。 依預設，此值會設為10小時，這表示如果發佈新影像，舊影像需要10小時才會離開使用者的快取。 如果您需要快取，請盡快清除，請聯絡客戶支援。</p> <p>另請參閱影像伺服API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html">過期</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>jpegquality</td> 
   <td>80</td> 
   <td><p>預設JPEG編碼屬性。 指定JPEG回覆影像的預設屬性。</p> <p>整數和標幟，以逗號分隔。 第一個值在1..100範圍內，並定義品質。 對於正常行為，第二個值可以是0，或者禁用通常由JPEG編碼器使用的RGB色度下採樣。</p> <p>另請參閱影像提供API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html">JpegQuality</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>maxpix</td> 
   <td>20萬0千2百</td> 
   <td><p>回覆影像大小限制。 傳回給用戶端的最大回覆影像寬度和高度。</p> <p>如果請求導致寬度或高度大於屬性：:MaxPix的回覆影像，則伺服器會傳回錯誤。</p> <p>另請參閱影像伺服API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html">MaxPix</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>resmode</td> 
   <td>SHARP2</td> 
   <td><p>預設重新取樣模式。 指定用於縮放影像資料的預設重採樣和插值屬性。</p> <p>若要求中未指定resMode=，則使用。</p> <p>允許的值包括BILIN、BICUB或SHARP2。</p> <p>列舉。 對於bilin，設為2，對於bicub，設為3，對於sharp2插值模式，設為4。 使用sharp2可獲得最佳結果。</p> <p>另請參閱影像伺服API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html">ResMode</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>解析度</td> 
   <td>72</td> 
   <td><p>預設對象解析度。 提供預設對象解析，以防特定目錄記錄不包含有效的目錄：:Resolution值。</p> <p>實數，大於0。 通常以每英吋像素表示，但也可以以其他單位表示，例如每米像素。</p> <p>另請參閱影像伺服API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-resolution.html">解析度</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>thumbnaitime</td> 
   <td>1%,11%,21%,31%,41%,51%,61%,71%,81%,91%</td> 
   <td>這些值代表視訊播放時間的快照，並傳遞至<a href="https://encoding.com/">encoding.com</a>。 如需詳細資訊，請參閱<a href="/help/assets/video.md#about-video-thumbnails">關於視訊縮圖</a> 。</td> 
  </tr> 
 </tbody> 
</table>

## 設定Dynamic Media色彩管理 {#configuring-dynamic-media-color-management}

Dynamic Media色彩管理可讓您為預覽的資產進行色彩校正。

透過色彩校正，擷取的資產可保留其色彩空間(RGB、CMYK、灰色)，以及在產生的金字塔TIFF轉譯中內嵌的色彩描述檔。 當您請求動態轉譯時，影像顏色會校正到目標顏色空間中。 您可以在JCR的Dynamic Media發佈設定中設定輸出顏色設定檔。

Adobe色彩管理使用ICC設定檔，這是由國際色彩協會(ICC)定義的格式。

您可以使用CMYK、RGB或灰色輸出來配置動態媒體色彩管理和配置影像預設集。 請參閱[設定影像預設集](managing-image-presets.md)。

進階使用案例可使用手動配置&#x200B;**[!UICONTROL icc=]**&#x200B;修飾符來明確選擇輸出顏色配置檔案：

* **[!UICONTROL icc]**  — 輸 [出顏色配置檔案。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html)

* **[!UICONTROL iccEmbed]**  — 內 [嵌顏色設定檔。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html)

>[!NOTE]
只有在安裝了[Software Distribution的Feature Pack 12445](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-12445)時，才能使用標準的Adobe色彩設定檔集。 所有Feature Pack和Service Pack均可在[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)取得。 Feature Pack 12445提供Adobe色彩設定檔。

### 安裝Feature Pack 12445 {#installing-feature-pack}

您必須安裝Feature Pack 12445，才能使用動態媒體色彩管理功能。

**安裝Feature Pack 12445**:

1. 導覽至[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)並下載`cq-6.3.0-featurepack-12445`。

   有關在[!DNL Adobe Experience Manager]中使用包的詳細資訊，請參閱[如何使用包](/help/sites-administering/package-manager.md)。

1. 安裝功能套件。

### 設定預設顏色設定檔 {#configuring-the-default-color-profiles}

安裝Feature Pack後，需要配置適當的預設顏色配置檔案，以在請求RGB或CMYK影像資料時啟用顏色校正。

**要配置預設顏色配置檔案**:

1. 在&#x200B;**[!UICONTROL 工具>一般>CRXDE Lite]**&#x200B;中，導覽至包含預設Adobe Color設定檔的`/conf/global/settings/dam/dm/imageserver/configuration/settings`。

   ![chlimage_1-514](assets/chlimage_1-514.png)

1. 通過滾動到&#x200B;**[!UICONTROL Properties]**&#x200B;頁簽底部並手動輸入屬性名稱、類型和值來添加顏色校正屬性，如下表所述。 輸入值後，點選&#x200B;**[!UICONTROL Add]**，然後點選&#x200B;**[!UICONTROL Save All]**&#x200B;以儲存您的值。

   **[!UICONTROL 色彩校正屬性]**&#x200B;表中描述了色彩校正屬性。 可以分配給顏色校正屬性的值在&#x200B;**[!UICONTROL 顏色配置檔案]**&#x200B;表中。

   例如，在&#x200B;**[!UICONTROL Name]**&#x200B;中，添加`iccprofilecmyk`，選擇&#x200B;**[!UICONTROL Type]** `String`，並將`WebCoated`添加為&#x200B;**[!UICONTROL Value]**。 點選「**[!UICONTROL 新增]**」，然後點選「**[!UICONTROL 儲存全部]**」以儲存您的值。

   ![chlimage_1-515](assets/chlimage_1-515.png)

   **色彩校正屬性表**

   <table> 
    <tbody> 
      <tr> 
      <td><strong>屬性</strong></td> 
      <td><strong>類型</strong></td> 
      <td><strong>預設</strong></td> 
      <td><strong>說明</strong></td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html">iccprofilergb</a></td> 
      <td>字串</td> 
      <td>&lt;empty&gt;</td> 
      <td>預設RGB顏色配置檔案的名稱。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html">icprofilecmyk</a></td> 
      <td>字串</td> 
      <td>&lt;empty&gt;</td> 
      <td>預設CMYK顏色配置檔案的名稱。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html">iccprofilegrey</a></td> 
      <td>字串</td> 
      <td>&lt;empty&gt;</td> 
      <td>預設灰色配置檔案的名稱。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcrgb.html">iccprofilescrgb</a></td> 
      <td>字串</td> 
      <td>&lt;empty&gt;</td> 
      <td>用於沒有嵌入顏色配置檔案的RGB影像的預設RGB顏色配置檔案的名稱</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrccmyk.html">icprofilersccmank</a></td> 
      <td>字串</td> 
      <td>&lt;empty&gt;</td> 
      <td>用於沒有嵌入顏色配置檔案的CMYK影像的預設CMYK顏色配置檔案的名稱。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcgray.html">iccprofilercgrey</a></td> 
      <td>字串</td> 
      <td>&lt;empty&gt;</td> 
      <td>用於沒有嵌入顏色配置檔案的CMYK影像的預設灰度顏色配置檔案的名稱。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccblackpointcompensation.html">iccblackpointcompensation</a></td> 
      <td>布林值 (Boolean)</td> 
      <td>True</td> 
      <td>指定在顏色校正期間是否應執行黑點補償。 Adobe建議開啟此選項。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccdither.html">icdither</a></td> 
      <td>布林值 (Boolean)</td> 
      <td>False</td> 
      <td>指定在色彩校正期間是否應進行抖動。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html">icrenderintent</a></td> 
      <td>字串</td> 
      <td>相對值</td> 
      <td><p>指定渲染目的。 可接受的值為：<strong>知覺、相對、飽和、絕對。 </strong><i></i>Adobe建 <strong>議 </strong><i></i>相對值作為預設值。</p> </td> 
      </tr> 
    </tbody> 
    </table>

   >[!NOTE]
   屬性名稱區分大小寫，且必須全部為小寫。

   **色彩描述檔表格**

   已安裝下列顏色設定檔：

   <table> 
    <tbody> 
      <tr> 
      <th><p>名稱</p> </th> 
      <th><p>色彩空間</p> </th> 
      <th><p>說明</p> </th> 
      </tr> 
      <tr> 
      <td>AdobeRGB</td> 
      <td>RGB</td> 
      <td>Adobe RGB市（1998年）</td> 
      </tr> 
      <tr> 
      <td>AppleRGB</td> 
      <td>RGB</td> 
      <td>AppleRGB</td> 
      </tr> 
      <tr> 
      <td>CIERGB</td> 
      <td>RGB</td> 
      <td>CIERGB</td> 
      </tr> 
      <tr> 
      <td>CobatedFogra27</td> 
      <td>CMYK</td> 
      <td>塗層FOGRA27(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CobatedFogra39</td> 
      <td>CMYK</td> 
      <td>塗層FOGRA39(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CobatedGraCol</td> 
      <td>CMYK</td> 
      <td>塗層GRACoL 2006(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>ColorMatchRGB</td> 
      <td>RGB</td> 
      <td>ColorMatchRGB</td> 
      </tr> 
      <tr> 
      <td>歐洲ISOC已處理</td> 
      <td>CMYK</td> 
      <td>歐洲ISO塗層FOGRA27</td> 
      </tr> 
      <tr> 
      <td>EuroscaleCobated</td> 
      <td>CMYK</td> 
      <td>塗有V2的歐洲標準</td> 
      </tr> 
      <tr> 
      <td>EuroscaleUncobated</td> 
      <td>CMYK</td> 
      <td>歐洲標準無塗層v2</td> 
      </tr> 
      <tr> 
      <td>JapanColorCobated</td> 
      <td>CMYK</td> 
      <td>2001年日本塗料</td> 
      </tr> 
      <tr> 
      <td>JapanColorSpeable</td> 
      <td>CMYK</td> 
      <td>《2002年日本彩色報》</td> 
      </tr> 
      <tr> 
      <td>JapanColorUncobated</td> 
      <td>CMYK</td> 
      <td>2001年日本顏色無塗層</td> 
      </tr> 
      <tr> 
      <td>JapanColorWebCobated</td> 
      <td>CMYK</td> 
      <td>日本彩色2003網版</td> 
      </tr> 
      <tr> 
      <td>JapanWebCobated</td> 
      <td>CMYK</td> 
      <td>Japan Web Cobated（廣告）</td> 
      </tr> 
      <tr> 
      <td>新聞紙SNAP2007</td> 
      <td>CMYK</td> 
      <td>美國新聞紙(SNAP 2007)</td> 
      </tr> 
      <tr> 
      <td>NTSC</td> 
      <td>RGB</td> 
      <td>NTSC（1953年）</td> 
      </tr> 
      <tr> 
      <td>PAL</td> 
      <td>RGB</td> 
      <td>PAL/SECAM</td> 
      </tr> 
      <tr> 
      <td>ProPhoto</td> 
      <td>RGB</td> 
      <td>ProPhotoRGB</td> 
      </tr> 
      <tr> 
      <td>PS4Default</td> 
      <td>CMYK</td> 
      <td>Photoshop 4預設CMYK</td> 
      </tr> 
      <tr> 
      <td>PS5Default</td> 
      <td>CMYK</td> 
      <td>Photoshop 5預設CMYK</td> 
      </tr> 
      <tr> 
      <td>張紙塗層</td> 
      <td>CMYK</td> 
      <td>美國鈑金件塗層v2</td> 
      </tr> 
      <tr> 
      <td>鈑金件未塗覆</td> 
      <td>CMYK</td> 
      <td>美國鈑金未塗層v2</td> 
      </tr> 
      <tr> 
      <td>SMPTE</td> 
      <td>RGB</td> 
      <td>SMPTE-C</td> 
      </tr> 
      <tr> 
      <td>sRGB</td> 
      <td>RGB</td> 
      <td>sRGB IEC61966-2.1</td> 
      </tr> 
      <tr> 
      <td>無塗層Fogra29</td> 
      <td>CMYK</td> 
      <td>無塗層FOGRA29(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCobated</td> 
      <td>CMYK</td> 
      <td>美國塗層網板(SWOP)v2</td> 
      </tr> 
      <tr> 
      <td>WebCobatedFogra28</td> 
      <td>CMYK</td> 
      <td>Web Cobated FOGRA28(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCobatedGrade3</td> 
      <td>CMYK</td> 
      <td>SWOP 2006三級紙</td> 
      </tr> 
      <tr> 
      <td>WebCobatedGrade5</td> 
      <td>CMYK</td> 
      <td>SWOP 2006五級紙</td> 
      </tr> 
      <tr> 
      <td>WebUncobated</td> 
      <td>CMYK</td> 
      <td>美國網路未塗層v2</td> 
      </tr> 
      <tr> 
      <td>寬色域RGB</td> 
      <td>RGB</td> 
      <td>寬色域RGB</td> 
      </tr> 
    </tbody> 
    </table>

1. 點選「**[!UICONTROL 儲存全部]**」。

例如，您可以將&#x200B;**[!UICONTROL iccprofilergb]**&#x200B;設為`sRGB`，將&#x200B;**[!UICONTROL iccprofilemyk]**&#x200B;設為`WebCoated`。 這麼做會執行下列動作：

* 啟用RGB和CMYK影像的顏色校正。
* 沒有顏色輪廓的RGB影像假定位於`sRGB`顏色空間中。
* 假定沒有顏色輪廓的CMYK影像位於`WebCoated`顏色空間中。
* 傳回RGB輸出的動態轉譯，會以`sRGB`色域傳回。
* 傳回CMYK輸出的動態轉譯，會在`WebCoated`色域中傳回。

## 傳遞資產 {#delivering-assets}

完成上述所有工作後，即會從影像或視訊服務提供啟動的Dynamic Media資產。 在AEM中，此功能會顯示在&#x200B;**[!UICONTROL 複製影像URL]**、**[!UICONTROL 複製檢視器URL]**、**[!UICONTROL 內嵌檢視器代碼]**&#x200B;和WCM中。

請參閱[傳送Dynamic Media資產](delivering-dynamic-media-assets.md)。

<table> 
 <tbody> 
  <tr> 
   <td><strong>當你……</strong></td> 
   <td><strong>結果</strong></td> 
  </tr> 
  <tr> 
   <td>複製影像URL</td> 
   <td><p>「複製URL」對話方塊會顯示類似下列的URL（URL僅供示範之用）:</p> <p><code>https://IMAGESERVICEPUBLISHNODE/is/image/content/dam/path/to/Image.jpg?$preset$</code></p> <p>其中<code>IMAGESERVICEPUBLISHNODE</code>指的是影像服務URL。</p> <p>另請參閱<a href="/help/assets/delivering-dynamic-media-assets.md">傳送Dynamic Media資產</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>複製檢視器URL</td> 
   <td><p>「複製URL」對話方塊會顯示類似下列的URL（URL僅供示範之用）:</p> <p><code>https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/BasicZoomViewer.html?asset=/content/dam/path/to/Image.jpg&amp;config=/conf/global/settings/dam/dm/presets/viewer/Zoom_dark&amp;serverUrl=https://IMAGESERVICEPUBLISHNODE/is/image/&amp;contentRoot=%2F</code></p> <p>其中， <code>PUBLISHNODE</code>代表一般AEM發佈節點，而<code>IMAGESERVICEPUBLISHNODE</code>代表影像服務URL。</p> <p>另請參閱<a href="/help/assets/delivering-dynamic-media-assets.md">傳送Dynamic Media資產</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>複製檢視器的內嵌程式碼</td> 
   <td><p>「複製內嵌程式碼」對話方塊會顯示類似下列的程式碼片段（程式碼範例僅供示範之用）:</p> <p><code class="code">&lt;style type="text/css"&gt;
       #s7basiczoom_div.s7basiczoomviewer{
       width:100%;
       height:auto;
       }
       &lt;/style&gt;
       &lt;script
       type="text/javascript" src="https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/js/BasicZoomViewer.js"&gt;&lt;/script&gt;
       &lt;div id="s7basiczoom_div"&gt;&lt;/div&gt;
       &lt;script type="text/javascript"&gt;
       var s7basiczoomviewer = new s7viewers.BasicZoomViewer({
       "containerId" : "s7basiczoom_div",
       "params" : {
       "serverurl" : "https://IMAGESERVICEPUBLISHNODE/is/image/",
       "contenturl" : "https://PUBLISHNODE/",
       "config" : "/conf/global/settings/dam/dm/presets/viewer/Zoom_dark",
       "asset" : "/content/dam/path/to/Image.jpg" }
       }).init();
       &lt;/script&gt;</code></p> <p>其中， <code>PUBLISHNODE</code>代表一般AEM發佈節點，而<code>IMAGESERVICEPUBLISHNODE</code>代表影像服務URL。</p> <p>另請參閱<a href="/help/assets/delivering-dynamic-media-assets.md">傳送Dynamic Media資產</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

### WCM Dynamic Media和互動式媒體元件 {#wcm-dynamic-media-and-interactive-media-components}

參考Dynamic Media和互動式媒體元件的WCM頁面參考傳送服務。
