---
title: 基本配置概念
seo-title: 基本配置概念
description: 了解如何設定AEM。
seo-description: 了解如何設定AEM。
uuid: edcdd4bd-5917-417e-8913-40d488383ea9
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 2673ea92-1651-4b1b-9aac-f4ba8b36782e
feature: 設定
exl-id: 758ef6d2-2eba-44ef-8e65-18258c4e9123
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2153'
ht-degree: 1%

---

# 基本配置概念{#basic-configuration-concepts}

Adobe Experience Manager(AEM)已安裝，且所有參數皆具有預設設定，可讓其「立即」執行。 不過，您可以根據自己的特定需求設定AEM。

AEM有許多方面可以設定：

* 有些項目通常為每個項目安裝](#primary-configuration-considerations)配置，必須進行審核以確認它們是否適用於您的項目。[
* [進一步](#further-configuration-considerations) 配置可能是常見的，但並非必要；與功能或系統效能和穩定性有關。
* 其他則僅為AEM的某些選用功能所需（這些功能會與適當功能一起記錄）。

您可以使用下列任一項，根據特定設定進行這些變更：

* **Adobe CQ Web Console**

   這是配置OSGi套件和服務的標準位置。

   如需詳細資訊和建議的實務，請參閱[設定OSGi](/help/sites-deploying/configuring-osgi.md) 。

* **存放庫**

   存放庫中提供OSGi設定的子集。 這可確保複製或複製存放庫內容會重新建立相同的設定。 您也可以根據執行模式，將自己的設定新增至存放庫。

   有關詳細資訊，請參閱儲存庫](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository)中的[OSGi配置，特別是[向儲存庫](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)添加新配置。

* **檔案系統**

   檔案系統中包含一些配置檔案。

* **AEM WCM**

   AEM WCM本身可以配置各種方面，許多方面都使用[Tools](/help/sites-administering/tools-consoles.md)控制台；例如，複製代理。

>[!NOTE]
>
>使用Adobe Experience Manager時，有數種方法可管理OSGi服務（主控台或存放庫節點）的組態設定。
>
>如需完整詳細資訊，請參閱[設定OSGi](/help/sites-deploying/configuring-osgi.md) 。

>[!NOTE]
>
>設定AEM很簡單，但您必須注意：
>
>某些變更可能會對應用程式造成重大影響。 因此，在開始設定AEM之前，請確定您擁有必要的經驗和知識，並只進行您知道需要的變更。 通過OSGi控制台所做的任何更改都應用於運行的系統（無需重新啟動）。****

## 主要配置注意事項{#primary-configuration-considerations}

此清單詳細說明了通常為每個新專案設定的主要區域。 並非所有項目都需要，但必須閱讀並審核清單，才能查看適用於您專案的項目。

此清單提供每個設定方面的簡短概述，以及提供完整詳細資料之頁面的連結。

### 安全檢查清單{#security-checklist}

[安全性檢查清單](/help/sites-administering/security-checklist.md)中列出了幾個關鍵配置問題。 請務必閱讀此檔案，並採取安裝所需的任何動作。

### 設定預設UI — 觸控最佳化或傳統{#configuring-the-default-ui-touch-optimized-or-classic}

AEM中有兩個可用的UI:

* 觸控最佳化UI
* 傳統UI

您可以使用[根對應](/help/sites-deploying/osgi-configuration-settings.md)來設定所需的UI。

>[!NOTE]
>
>有關選擇UI的詳細資訊，請參閱[選擇UI](/help/sites-authoring/select-ui.md)。

### IPv4和IPv6 {#ipv-and-ipv}

AEM的所有元素（例如存放庫、Dispatcher等）都可以安裝在IPv4和IPv6網路中。

操作是無縫的，因為不需要特殊配置，如果需要，您只需使用適合您網路類型的格式指定IP地址即可。

這表示當需要指定IP位址時，您可以（視需要）從下列項目中選取：

* IPv6地址

   例如`https://[ab12::34c5:6d7:8e90:1234]:4502`

* IPv4地址

   例如`https://123.1.1.4:4502`

* 伺服器名稱

   例如， `https://www.yourserver.com:4502`

* 對於IPv4和IPv6網路安裝，將解釋`localhost`的預設案例

   例如， `http://localhost:4502`

### 版本清除{#version-purging}

在標準安裝中，每當您啟動頁面（更新內容後）時，AEM都會建立新的頁面或節點版本。您也可以使用sidekick的&#x200B;**Versioning**&#x200B;標籤，根據請求建立其他版本。 所有這些版本都儲存在儲存庫中，並可視需要還原。

這些版本永遠不會清除，因此儲存庫大小會隨著時間而增長，因此需要管理。

如需完整詳細資訊，請參閱[版本清除](/help/sites-deploying/version-purging.md)，尤其是[Version Manager](/help/sites-deploying/version-purging.md#version-manager)，以了解建立新版本時如何設定AEM以清除舊版本的詳細資訊。

### 記錄 {#logging}

AEM可讓您設定：

* 中央記錄服務的全局參數
* 要求資料記錄；要求資訊的專用記錄設定
* 個別服務的特定設定；例如，日誌消息的單個日誌檔案和格式

如需完整詳細資訊，請參閱[記錄](/help/sites-deploying/configure-logging.md)。

### 執行模式 {#run-modes}

執行模式可讓您針對特定用途調整AEM執行個體；例如，製作或發佈、測試、開發或內部網路等。

為此，請定義每個執行模式的設定參數集合。 所有執行模式都會套用一組基本的設定參數，然後您就可以根據特定環境的用途調整其他設定。 接著會視需要套用。

所有配置設定都儲存在一個儲存庫中，並通過設定&#x200B;**運行模式**&#x200B;來激活。

如需完整詳細資訊，請參閱[執行模式](/help/sites-deploying/configure-runmodes.md) 。

### 單一登入{#single-sign-on}

單一登入(SSO)允許用戶在提供一次身份驗證憑據（如用戶名和密碼）後訪問多個系統。 單獨的系統（稱為可信驗證器）執行該驗證，並提供具有用戶憑據的Experience Manager。 Experience Manager會檢查並強制使用者的存取權限（即決定允許使用者存取的資源）。

如需詳細資訊，請參閱[單一登入](/help/sites-deploying/single-sign-on.md) 。

### 資源映射{#resource-mapping}

資源對應可用來定義AEM的重新導向、虛名URL和虛擬主機。

例如，您可以將這些對應用於：

* 為所有要求加上前置詞`/content`，以便對網站的訪客隱藏內部結構。
* 定義重新導向，以便將所有要求重新導向至您網站的`/content/en/gateway`頁面。`https://gbiv.com/`

有關詳細資訊，請參閱[資源映射](/help/sites-deploying/resource-mapping.md)。

### 複製、反向複製和複製代理{#replication-reverse-replication-and-replication-agents}

復寫代理是AEM的中心，作為用於：

* [從作者發佈（啟動）](/help/sites-authoring/publishing-pages.md) 內容至發佈環境。
* 明確排清Dispatcher快取中的內容。
* 將使用者輸入（例如，表單輸入）從發佈環境傳回製作環境（在製作環境控制之下）。

有關詳細資訊，請參見[Replication](/help/sites-deploying/replication.md)。

### OSGi配置設定{#osgi-configuration-settings}

[](https://www.osgi.org/) OSG是AEM技術堆疊中的基本元素。它可用來控制AEM的複合套件組合及其設定。

如需與專案實作相關的各種套件組合清單（依套件組合列出），請參閱[OSGi組態設定](/help/sites-deploying/osgi-configuration-settings.md)。 並非所有列出的設定都需要調整，有些設定可協助您了解AEM的運作方式。

使用AEM時，有數種方法可管理這類服務的組態設定；如需詳細資訊和建議實務，請參閱[設定OSGi](/help/sites-deploying/configuring-osgi.md) 。

### 配置LDAP {#configuring-ldap}

要驗證儲存在（中央）LDAP目錄（如Active Directory）中的用戶，需要LDAP驗證。 這有助於減少管理使用者帳戶所需的工作量。

LDAP驗證發生在儲存庫級別，因此由儲存庫直接處理。 有關詳細資訊，請參閱[使用AEM](/help/sites-administering/ldap-config.md)配置LDAP。

有關AEM內的用戶管理（包括訪問權限的分配），請參閱[用戶管理和安全性](/help/sites-administering/security.md)。

### 設定Dispatcher {#configuring-the-dispatcher}

Dispatcher是Adobe的快取和/或負載平衡工具。 使用Dispatcher也有助於保護您的AEM伺服器免受攻擊。 因此，您可以搭配使用 Dispatcher 與企業級 Web 伺服器，以提高 AEM 例項的安全性。

如需完整詳細資訊，請參閱[Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)，尤其是[設定Dispatcher](https://helpx.adobe.com/tw/experience-manager/dispatcher/using/dispatcher-configuration.html)以取得進一步的設定詳細資料。

### 配置AEMLiveCycle連接器{#configuring-aem-livecycle-connector}

隨著AEM Doc Services和AEM Doc Security的發行，我們現在能夠叫用LiveCycle檔案服務來轉譯XFA表單、將檔案轉換為PDF，以及保護檔案的原則。 如需詳細資訊，請閱讀[AEMLiveCycle連接器](https://helpx.adobe.com/livecycle/help/aem/aem-livecycle-connector.html)。

### 作業卸載和拓撲管理{#job-offloading-and-topology-administration}

[](/help/sites-deploying/offloading.md) 卸載分配處理任務量在拓撲中分配Experience Manager實例。透過卸載，您可以使用特定Experience Manager例項來執行特定類型的處理。 專門處理可讓您最大限度地利用可用的伺服器資源。

拓撲是鬆散耦合的Experience Manager群集，它們參與卸載。 群集由一個或多個Experience Manager伺服器實例（單個實例被視為群集）組成。

有關如何查看或修改拓撲成員資格的詳細資訊，請參閱[管理拓撲](/help/sites-deploying/offloading.md#administering-topologies)部分。

### 配置歡迎控制台{#configuring-the-welcome-console}

傳統UI的歡迎控制台提供AEM中各種主控台和功能的連結清單。

您可以設定可見的連結，如需詳細資訊，請參閱[設定歡迎控制台](/help/sites-developing/customizing-the-welcome-console.md) 。

### 為效能配置{#configuring-for-performance}

[](/help/sites-deploying/configuring-performance.md) 效能是專案的關鍵。AEM的某些方面（和/或基礎存放庫）可進行設定，以最佳化效能。

有關詳細資訊，請參閱[效能配置](/help/sites-deploying/configuring-performance.md#configuring-for-performance)。

<!--delete ### Scaling {#scaling}

Scaling a CQ installation correctly depends greatly on the details of your particular use case. A detailed discussion of solution patterns for various situations can be found in [Scaling CQ](/help/sites-deploying/scaling.md).-->

### 共用資料儲存{#shared-data-store}

存放庫資料存放區用於將大型二進位檔的儲存空間從存放庫的適當位置卸載至個別區域，讓存放庫樹狀結構中相同二進位檔的多個執行個體（例如影像）只能儲存一次。

此「一次儲存、多次引用」功能可擴展為不僅提供單個儲存庫樹，而且提供完全獨立的儲存庫，方法是將每個儲存庫的資料儲存配置為引用相同的共用檔案系統位置。

這樣的資料儲存可以在同一群集中的不同節點之間共用，在同一安裝中可以共用不同的發佈和/或製作實例，或在不同安裝中甚至完全不同的實例。

如需詳細資訊，請參閱[設定資料儲存區和節點儲存區](/help/sites-deploying/data-store-config.md)。

## 進一步配置注意事項{#further-configuration-considerations}

### 啟用HTTP over SSL {#enabling-http-over-ssl}

您可以啟用HTTP over SSL，以運用更安全的連線至您的伺服器。

如需詳細資訊，請參閱[透過SSL啟用HTTP](/help/sites-administering/ssl-by-default.md) 。

### AEM門戶和門戶{#aem-portals-and-portlets}

門戶是Web應用程式，它提供個性化、單一登錄、來自不同來源的內容整合，並承載資訊系統的展示層。 Portlet元件還允許您在頁上嵌入Portlet。 若要存取CQ5 WCM提供的內容，可以使用CQ5 Portal Director Portlet來安裝入口伺服器。 您可以通過安裝、配置Portlet並將Portlet添加到門戶頁面來執行此操作。

有關詳細資訊，請參見[門戶和Portlet](/help/sites-administering/aem-as-portal.md)。

### 靜態對象{#expiration-of-static-objects}的過期

靜態物件（例如圖示）不會變更。 因此，應將系統配置為使它們不會過期（在合理的時間段內），從而減少不必要的流量。

有關詳細資訊，請參閱[靜態對象的過期](/help/sites-deploying/expiration-static-objects.md)。

### 在Java進程{#open-files-in-the-java-process}中開啟FIle

每個java進程都可能訪問檔案 — 這需要系統資源。 因此，會定義上限，指允許每個進程同時訪問的檔案數。 如果超出此值，則可能發生例外錯誤。

如果AEM進程超過此上限，則在`error.log`中將顯示消息「 `too many open files`」。

若要避免這類例外，您必須：

1. 檢查您的AEM程式使用的開啟檔案數。

   執行此檢查的方式取決於執行個體執行的平台。 可以使用lsof(Unix)或Process Explorer(Windows)等實用程式。

   開發和測試期間應監控此值，以：

   * 確認檔案已視需要關閉
   * 以確定所需的最大值（在各種情況下）

1. 設定允許的最大值。

   新價值應滿足當前需求和未來任何峰值，因此最好將當前需求增加一倍。

   預設情況下， `serverctl`將`CQ_MAX_OPEN_FILES`配置為`8192`;這應該足以在大多數情況下使用。

### 配置RTF編輯器{#configuring-the-rich-text-editor}

**RTF編輯器**(**RTE**)為作者提供範圍廣泛的[功能](/help/sites-authoring/rich-text-editor.md)，以編輯其文字內容；為他們提供表徵圖、選擇框和WYSIWYG體驗的菜單。

如需詳細資訊，請參閱[設定RTF編輯器](/help/sites-administering/rich-text-editor.md) 。

### 為頁面編輯設定還原{#configuring-undo-for-page-editing}

有幾個屬性可控制編輯頁面時的還原和重做命令行為。 您可以設定這些項目，如需詳細資訊，請參閱[為頁面編輯設定還原](/help/sites-administering/config-undo.md) 。

### 配置視頻元件{#configuring-the-video-component}

[視訊元件](/help/sites-authoring/default-components-foundation.md#video)可讓您在頁面上放置預先定義且現成可用的視訊元素。

若要正確進行轉碼，您的管理員必須分別[安裝FFmpeg](/help/sites-administering/config-video.md#install-ffmpeg)。 它們也可以[設定您的視訊描述檔](/help/sites-administering/config-video.md#configure-video-profiles)以搭配html5元素使用。

### 設定和自訂報表{#configuring-and-customizing-reports}

為協助您監視和分析執行個體的狀態，CQ提供一系列預設報表，您可依個別需求加以設定：

如需詳細資訊，請參閱[報表自訂基本概念](/help/sites-administering/reporting.md#the-basics-of-report-customization) 。

### 配置電子郵件通知{#configuring-email-notification}

CQ會傳送電子郵件通知給下列使用者：

* 已訂閱頁面事件，例如修改或復寫。
* 已訂閱論壇活動。
* 必須在工作流程中執行步驟。

如需詳細資訊，請參閱[設定電子郵件通知](/help/sites-administering/notification.md) 。

### 啟用頁面曝光數{#enabling-page-impressions}

頁面曝光數會顯示在傳統UI網站管理控制台的&#x200B;**曝光數**&#x200B;欄中。 若要啟用頁面曝光次數的擷取，您必須進行設定：

* 在發佈例項上：

   * [Day CQ WCM頁面統計資料](/help/sites-deploying/osgi-configuration-settings.md)

* 在Author例項上：

   * [Adobe頁面曝光次數追蹤](/help/sites-deploying/osgi-configuration-settings.md)

>[!CAUTION]
>
>在製作環境中設定Adobe頁面曝光次數追蹤器將允許匿名要求追蹤服務。
