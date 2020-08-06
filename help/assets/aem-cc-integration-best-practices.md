---
title: AEM與Creative Cloud整合最佳實務
description: 將AEM部署與Adobe Creative Cloud整合的最佳實務，以簡化資產轉讓工作流程並達到最高效率
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1f44950e3e0653df61289e1bd435d13829051365
workflow-type: tm+mt
source-wordcount: '3578'
ht-degree: 16%

---


# AEM與Creative Cloud整合最佳實務 {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets是數位資產管理(DAM)解決方案，可與Adobe Creative Cloud整合，以協助DAM使用者與創意團隊合作，簡化內容建立程式中的協作。

Adobe Creative Cloud為創意團隊提供解決方案與服務生態系統，以協助他們建立數位資產。 它包括案頭和行動應用程式、雲端服務（例如具備案頭同步功能或網頁體驗的儲存空間），以及Adobe Stock等市集。

閱讀內容，瞭解根據您的使用案例，在案頭和企業級DAM之間選擇哪些整合，以及連接工作流程的相關最佳實務。

>[!NOTE]
>
>AEM到Creative Cloud資料夾共用已過時，本指南不再涵蓋。 Adobe建議使用較新的功能(例如 [Adobe Asset Link](https://helpx.adobe.com/tw/enterprise/using/adobe-asset-link.html) 或 [](https://docs.adobe.com/content/help/zh-Hant/experience-manager-desktop-app/using/introduction.html) AEM案頭應用程式)，讓創意使用者可存取AEM中管理的資產。

## 創意人員、行銷人員和DAM使用者的協作需求 {#collaboration-needs-of-creatives-marketers-and-dam-users}

| 需求 | 使用案例 | 涉及的曲面 |
|---|---|---|
| 簡化案頭創意人員的體驗 | 簡化從DAM(AEM Assets)為創意專業人員（或更廣泛的是，在原生資產建立應用程式中工作的案頭使用者）存取資產的程式。 他們需要簡單明瞭的方式來探索、使用（開啟）、編輯和儲存AEM的變更，以及上傳新檔案。 | Win或Mac案頭； Creative Cloud應用程式 |
| 從Adobe Stock提供高品質、現成可用的資產 | 行銷人員協助資產採購和發現，協助加快內容建立流程。 創意專業人員可直接從其創意工具中使用核准的資產。 | AEM Assets; Adobe Stock市集； 中繼資料欄位 |
| 依組織分發及共用資產 | 內部部門／當地分支機構和外部合作夥伴、分銷商和代理商會使用母公司組織共用的已核准資產。 該組織希望安全無縫地共用已建立的資產，以便更廣泛地重複使用。 | 品牌入口網站、資產分享共用 |

## Adobe提供的產品可支援協作需求 {#adobe-offerings-to-support-the-collaboration-need}

| 相關人員的價值主張 | Adobe產品 | 涉及的曲面 |
|---|---|---|
| 創意使用者可從AEM發現資產、開啟並使用資產、編輯和上傳對AEM的變更，以及將新檔案上傳至AEM，而不需離開Creative Cloud應用程式。 | [Adobe Asset Link](https://helpx.adobe.com/tw/enterprise/using/adobe-asset-link.html) | Photoshop、Illustrator和InDesign |
| 商業使用者可簡化開啟和使用資產、編輯和上傳對AEM的變更，以及從案頭環境將新檔案上傳至AEM。 他們會使用一般整合來開啟原生案頭應用程式中的任何資產類型，包括非Adobe的資產類型。 | [AEM案頭應用程式](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) | Win和Mac案頭版的AEM案頭應用程式 |
| 行銷人員和商業使用者可從AEM中發現、預覽、授權及儲存及管理Adobe Stock資產。 授權和儲存的資產提供精選的Adobe Stock中繼資料，以提升治理。 | [Experience Manager與Adobe Stock整合](aem-assets-adobe-stock.md) | AEM網頁介面 |

本文主要針對協作需求的前兩個方面。資產規模分配和採購作為一個使用案例被簡要提及。針對這些需求解決方案，請考慮Adobe品牌入口網站或資產共用公域。Alternate solutions such as [Brand Portal](https://helpx.adobe.com/tw/experience-manager/brand-portal/user-guide.html), solutions that can be built based on [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) components, [Link Share](/help/assets/link-sharing.md), using [Experience Manager Assets](/help/assets/managing-assets-touch-ui.md) should be reviewed based on specific requirement.

![適用於AEM的Creative Cloud連線： 決定要使用哪些功能](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with AEM Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### 使用案例的對應

| 使用案例 | AEM案頭應用程式 | 資料夾共用 | 其他解決方案 |
|---|---|---|---|
| 與Creative使用者共用較少數量(1)的DAM資產 | ✔✔ | ✔ |  |
| 與Creative使用者共用更多(2)個DAM資產 | ✔✔ | ✘ | [品牌入口網站](https://docs.adobe.com/content/help/zh-Hant/experience-manager-brand-portal/using/home.html) <br> [資產共用](assets-finder-editor.md) |
| 與可存取DAM的使用者共用DAM資產 | ✔✔ | ✔ | [連結共用](link-sharing.md) |
| 與無法存取DAM的使用者共用DAM資產 | ✘ | ✔✔ | [品牌入口網站](https://docs.adobe.com/content/help/zh-Hant/experience-manager-brand-portal/using/home.html) <br> [資產共用](assets-finder-editor.md) |
| 將資產數量／數量減少至DAM | ✔✔ | ✔ | [網頁UI上傳](managing-assets-touch-ui.md) |
| 將更多資產儲存至DAM(3) | ✔✔ | ✘ | [網頁UI上傳](managing-assets-touch-ui.md)<br> 自訂指令碼／工具 |
| 將大量資產移轉至DAM | ✘ | ✘ | [遷移指南](assets-migration-guide.md) |
| 在案頭上快速開啟資產 | ✔✔ | ✘ |  |
| 在案頭上快速開啟和變更資產 | ✔✔ | ✘ |  |

符號的圖例：

* ✔✔: 首選解決方案
* ✔: 可接受的解決方案
* ✘: 不應用於使用案例

其他注釋：

* （一）資產數量減少： 例如，與專案或促銷活動相關的一小組資產
* （二）資產數量較多： 例如，組織中所有已核准的資產
* (3)使用AEM案頭應用程式上傳檔案夾功能

為支援資產散發使用案例，應考慮其他解決方案：

* [品牌入口網站](https://helpx.adobe.com/tw/experience-manager/brand-portal/user-guide.html) ，提供可設定、SaaS附加元件至AEM資產，以發佈資產。
* 自訂解決方案是根據「資產共 [用共用共用](https://adobe-marketing-cloud.github.io/asset-share-commons/) 」程式碼庫建立。
* AEM連 [結共用](/help/assets/link-sharing.md) ，使用連結臨機共用資產。
* [AEM Assets網頁介面](/help/assets/managing-assets-touch-ui.md) ，提供由AEM存取控制設定所保護的外部使用者區域，以及必要的IT/網路組態調整，讓這些外部使用者存取AEM。

## 主要概念和使用案例 {#key-concepts-and-use-cases}

### 常見術語辭彙表 {#glossary-of-common-terms}

* **在製品或創意在製品 (WIP)：**&#x200B;在資產生命週期中，資產會經歷多次變更，且通常尚未準備好更廣泛地與其他團隊共用的階段。
* **創意成熟資產：**&#x200B;已準備好更廣泛地與其他團隊共用，或已獲創意團隊選取/核准，要與行銷或 LOB 團隊共用的資產。
* **資產核准：**&#x200B;針對已上傳至 DAM 的資產執行的核准程序，通常包括品牌核准、法律核准等。
* **最終資產：**&#x200B;已完成所有核准/中繼資料標記，且已準備好更廣泛地供團隊使用的資產。此類資產會儲存在 DAM 中，並提供給所有 (或所有相關的) 使用者使用。這類資產可用於行銷管道，或供創意團隊創作設計。
* **小幅度資產更新/變更：**&#x200B;數位資產的快速微幅變更。此類更新/變更通常是為了因應潤飾或微幅編輯請求、資產檢閱或核准 (例如重新定位、變更文字大小、調整飽和度/亮度、顏色等) 而進行的。
* **重大資產更新/變更：**&#x200B;需要大量工作，且有時需要較長時間才能完成的數位資產變更。其中通常包含多項變更。資產在更新時必須儲存多次。重大資產更新通常會導致資產進入 WIP 階段。
* **DAM：**&#x200B;數位資產管理。在此文件中，其意義與 AEM Experience Manager Assets 相同，除非另有特別說明。
* **創意使用者：**&#x200B;使用 Creative Cloud 應用程式和服務建立數位資產的創意專業人員。在某些情況下，創意使用者可能是可使用 Creative Cloud、但不會建立數位資產的創意團隊成員 (例如創意總監或創意團隊經理)。
* **DAM 使用者：** DAM 系統的一般使用者。視組織而異，DAM 使用者可能是行銷或非行銷使用者，例如企業營運 (LOB) 使用者、圖書管理員、銷售人員等。

### 使用AEM和Creative Cloud整合時的考量事項 {#considerations-when-using-aem-and-creative-cloud-integration}

* 檢視桌 [面應用程式最佳實務](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* 檢視 [Adobe Stock整合](aem-assets-adobe-stock.md)
* 請參 [閱Adobe Asset Link](https://helpx.adobe.com/tw/enterprise/using/adobe-asset-link.html)

這是Experience Manager與Creative Cloud整合的最佳實務簡要摘要。 閱讀本檔案的其餘部分，以詳細瞭解這些內容。

* **對於在Photoshop、InDesign或Illustrator中工作的創意使用者：** Adobe Asset Link提供最佳的使用者體驗，包括對從AEM結帳的資產進行中工作的簡潔處理
* **** 為簡化從案頭存取任何一般檔案格式或應用程式的資產：使用AEM案頭應用程式
* **** 瞭解在DAM中儲存資產的原因及時機：更新將提供給組織中更廣大的團隊
* **** 請留意共用資產的數量：如果您的使用案例是資產分發，則治理和安全性可能是最重要的方面。請考慮使用大型工具 (例如品牌入口網站) 進行此作業。
* **** 瞭解資產生命週期：瞭解不同團隊在組織中如何處理資產
* **** 謹慎處理資產的頻繁儲存：Adobe Asset Link會透過PS、AI、ID為您處理。對於其他應用程式，請勿在映射/共用資料夾中執行進行中的工作，除非您需要DAM中的所有變更

### 從AEM Assets存取Adobe Stock資產 {#access-to-adobe-stock-assets-from-aem-assets}

[AEM與Adobe Stock整合](/help/assets/aem-assets-adobe-stock.md) ，讓AEM使用者能夠搜尋、預覽、授權和儲存Adobe Stock中的資產。 授權和儲存的Adobe Stock資產已選取Stock中繼資料，可用來使用額外的篩選條件來搜尋。

有關此整合的幾點重要：

* 當Adobe Stock中的資產儲存至AEM時，這些資產會變成一般的AEM資產，並將二進位檔儲存至AEM儲存庫。 有些與Adobe Stock相關的中繼資料會儲存在AEM中用於資產，否則擷取程式看起來與任何其他檔案相同。 例如，如果「智慧型標籤」是作用中，則在儲存時會將標籤新增至這些資產。
* 儲存至AEM的資產是復本，而非回到Adobe Stock的連結。

**在Creative Cloud中使用從Adobe Stock儲存至AEM的資產**。 此整合與Adobe Asset Link無關，但Adobe Asset Link會以這種方式辨識從Stock儲存的這些資產，並在Photoshop、Illustrator或InDesign的Adobe Asset Link擴充功能UI中，在這些資產上顯示額外的中繼資料和Stock圖示。 這些檔案可供瀏覽、開啟等使用——因為它們是儲存至AEM時的一般AEM資產。
使用Adobe Asset Link擴充功能之Creative Cloud應用程式的創意使用者除了可從Adobe Stock存取已授權的資產到AEM外，還可以使用Creative Cloud Libraries面板來搜尋、預覽及授權Adobe Stock資產。
Adobe Stock中授權並儲存至AEM的資產可供存取AEM Assets部署的更廣大團隊使用，而透過Creative Cloud Libraries面板授權Adobe Stock資產的創意人員則會在其Creative Cloud帳戶中預設為自己提供。

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## 關於在DAM中儲存資產 {#about-storing-assets-in-a-dam}

為了在創意和行銷／業務線(LOB)團隊之間設計有效率的工作流程並選擇最佳支援功能，請務必瞭解資產儲存在DAM的時機和原因。

### 資產為何儲存在DAM中 {#why-assets-are-stored-in-dam}

將資產儲存在DAM中，讓資產更容易存取，而且可尋找。 它可確保整個組織或生態系統中的眾多使用者（包括合作夥伴、客戶等）都能運用這些資產。

大部分組織都選擇只儲存與下遊行銷/LOB程式相關的資產（透過AEM Sites發佈至網路通道或Adobe Experience Cloud - Marketing Cloud、Advertising Cloud所提供的其他通道，並由Analytics Cloud測量，提供給使用者／合作夥伴等）。 此外，組織會儲存在DAM中可能須經過審查／核准程式的資產。 如此，DAM會儲存大部分有高可能被利用的資產，並避免儲存閒置資產。

儲存資產也須受技術與資源使用考量。 DAM針對儲存的資產提供其他服務，包括擷取中繼資料、版本修訂、產生預覽／轉碼、管理參照以及新增存取控制資訊。 這些服務需要額外的時間和基礎架構資源。

通常，儲存所有資產和更新是不可取的。 例如，如果特定資產的更新品質不佳，且會耗用過多的資源，則資產可能無法儲存在DAM中。

### 資產儲存在DAM中時 {#when-assets-are-stored-in-dam}

創意團隊（和組織）通常對在資產生命週期的每個階段儲存資產不感興趣。 例如，在下列情況下，他們會避免儲存資產：

* 尚未完成或有待試驗的資產
* 無法通過創意／內部團隊審核週期的資產
* 與相關資產相比，團隊有更好的人選，可向外部團隊代表其工作

通常，下列類別資產會儲存在DAM中：

* 已到期且被視為可供分享的資產
* 創意團隊預先選取的資產
* 根據特定合約或合約（例如從RAW檔案轉換的JPG檔案、從PSD原稿轉換的TIFF/影像），行銷部門可使用或要求的特定資產格式

### 資產更新儲存在DAM中時 {#when-updates-to-assets-are-stored-in-dam}

通常，只應將與更廣泛的DAM使用者集合相關的資產更新儲存在DAM中。 它可確保使用者（行銷和類似功能）在DAM資產時間軸中只看到相關版本。

通常與資產生命週期中的重要里程碑相關的變更。 例如，創意團隊根據要求／審查提供的初始創意就緒資產或正式更新應儲存在DAM中，並加以版本控制。

在DAM中要求變更現有資產後，行銷團隊會更新以供其審核，這是相關更新的範例。 它應儲存並更新至DAM的版本，以供進一步參考或還原為舊版。

以下是通常不相關的更新範例：

* 資產上傳的早期版本，在準備好進行行銷審核之前
* 在創作團隊決定資產準備就緒之前，在進行中的階段中經常對資產進行創意變更

### 使用者存取DAM {#user-access-to-dam}

AEM Assets根據使用者對AEM Assets部署的存取權，支援兩種類型的使用者。 通常，企業網路（防火牆）內的使用者可直接存取DAM。 企業網路以外的其他使用者將無法直接存取。 使用者類型會決定從技術角度可使用哪些整合。

#### 直接存取DAM的創意使用者 {#creative-users-with-direct-access-to-dam}

通常，內部創意團隊或已登入內部網路的廣告公司／創意專業人員都可存取DAM例項，包括AEM登入。

在這種情況下，AEM案頭應用程式可協助您輕鬆存取最終／核准的資產，並讓您將創意就緒的資產儲存至DAM。

#### 無法存取DAM的創意使用者 {#creative-users-without-access-to-dam}

無法直接存取DAM例項的外部機構和自由工作者可能需要存取已核准的資產，或想要將其新設計新增至DAM。

在這種情況下，您可以運用AEM/Creative Cloud整合來改善工作流程。 先決條件是創意使用者必須擁有Adobe ID，並擁有含儲存服務的Creative Cloud帳戶。

使用下列策略來存取最終／核准的資產：

* 若要提供大量資產的存取權： 使 [用AEM Assets Brand Portal](https://helpx.adobe.com/tw/experience-manager/brand-portal/user-guide.html)，或客戶在AEM發佈基礎架構上實作 [「資產共用](assets-finder-editor.md) 」

* 若要存取一些資產： 除了AEM Assets品牌入口網站或資產共用外，還可以使用與Adobe Creative Cloud共用的AEM檔案夾。 請注意，本整合有某些限制，本文將詳細說明。

### 使用案例 {#use-cases}

下列使用案例說明DAM與設計人員案頭之間的各種工作流程類型。

#### 使用DAM的資產建立新設計 {#creating-new-designs-using-assets-from-dam}

下圖說明數位資產生命週期。 它說明創意使用者和DAM使用者（行銷人員、LOB使用者）如何運用現有資產，並使用這些資產來建立更多資產，並傳送給他們進行核准。

![chlimage_1-301](assets/chlimage_1-301.png)

資產生命週期包含下列階段：

1. 將核准的資產共用至創意案頭： DAM的最終資產已提供給創意使用者（在桌上型）
1. 建立新設計（創意數位資產）: 新檔案儲存在進行中(WIP)區域中。
1. 在新設計中使用（放置）已核准的資產： 創意使用者使用Creative Cloud應用程式中現有的已核准資產來產生新資產
1. 頻繁保存WIP更新： 創意使用者可快速重複，並經常儲存檔案。 目前階段，創意使用者可能會與他人共同作業，但經常儲存的更新通常對DAM使用者不感興趣。
1. 資產達到創意就緒狀態，並儲存至「創意就緒」檔案夾
1. 資產更新： DAM中的使用者可使用資產更新或新檔案
1. 資產投入生產： 這是DAM流程，視組織而定，可能包括標籤、核准和變更存取控制。 目前，該資產已視為最終資產，而且可以由更多團隊利用DAM來使用。 創意使用者也可以用它來建立其他資產。

以下是關於如何透過此程式管理資產的一些一般建議：

* 請針對WIP檔案使用專用的儲存區／系統，例如Adobe Creative Cloud Assets同步資料夾： 與DAM使用者無關的頻繁更新，最好由專用系統處理，而不是從AEM Assets中處理。 WIP資產可以使用Adobe Creative Cloud案頭應用程式同步至本機磁碟、儲存在本機儲存空間等。
* 針對上傳至DAM的最終資產和資產使用個別的資料夾／共用： 為避免疑義，最終資產應有自己的對應／共用資料夾（上方的「最終」範例），而要上傳回DAM的資產應有自己的資產（「創意就緒」）

#### 變更DAM中管理的現有資產 {#changing-existing-assets-managed-in-dam}

在某些情況下，DAM中的資產可能需要變更。 範例包括：

* 在AEM Assets中完成審核和核准後，要求變更資產
* 現有最終資產的主要更新
* 快速編輯現有檔案（尤其是在最終核准之前）

在這種情況下，AEM案頭應用程式提供最簡單的方式來執行這些作業。

![chlimage_1-302](assets/chlimage_1-302.png)

以下是圖中所示事件的流程：

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for AEM desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** 將資產從DAM共用至案頭，或直接在所選應用程式（例如Adobe Photoshop等）的案頭上開啟。 建議簽出以鎖定檔案。
* **2:** 次要更新： 編輯檔案並儲存變更。
* 步驟2的替代流程

   * **答：** 主要更新： 如果檔案需要詳細的更改集，則應間歇性地保存並複製到WIP資料夾／區域。
   * **B:** 在WIP資料夾中繼續處理檔案。 儲存的變更不會同步至DAM中的版本
   * **C:** 更新完成後，檔案會複製回或儲存至對應的資料夾

* **3:** 資產更新會反映在DAM中。 簽入資產以解除鎖定。
* **4:** 資產會投入生產。

以下是有關如何在整個流程中管理資產的一些一般建議：

* 請避免直接儲存您從AEM案頭應用程式映射的網路共用中開啟的檔案，除非您對檔案所做的變更很小。
* 如果您想要對檔案進行額外變更、間歇性儲存或與Creative團隊協作，請將檔案複製至個別的WIP檔案夾。

#### 大量上傳至DAM {#bulk-upload-to-dam}

在某些情況下，您可能需要同時將大量檔案上傳至DAM，例如：

* 上傳像片或大型專案的結果
* 上傳創意廣告公司提供的資產
* 如果選取是在DAM以外完成，請從較大的集合上傳選取的資產

請注意，本說明是指在案頭使用者工作流程中，以正常的方式（例如每週或每張像片等）上傳檔案。 此處未涵蓋大型資產遷移。

如果您想要大量上傳資產，可以運用下列功能：

* 若要上傳大型／階層式資料夾，請使用AEM案頭應用程式，此應用程式提供「資 [料夾上傳](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) 」功能。 您也可以上傳階層式資料夾結構。 資產會在背景上傳，因此不會系結至網頁瀏覽器作業
* 如果您想要從單一檔案夾上傳幾個檔案，請直接從案頭拖曳檔案至網頁UI，或使用AEM Assets網頁UI中的「建立」選項。

>[!NOTE]
>
>您也可以根據您的業務需求使用自訂的上載程式。

#### 直接從案頭管理數位資產 {#managing-digital-assets-directly-from-desktop}

如果您使用「網路檔案分享」來管理數位資產，只要使用AEM案頭應用程式所映射的網路分享，就會被視為方便的替代項目。 從網路檔案分享轉換時，請記住，AEM Web UI提供豐富的數位資產管理功能集，遠超網路分享（搜尋、系列、中繼資料、協作、預覽等）的可能，而AEM案頭應用程式則提供方便的連結，將伺服器端的DAM存放庫與桌上型電腦的工作連結。

請避免使用AEM案頭應用程式直接在AEM Assets的網路共用中管理資產。 例如，請避免使用AEM案頭應用程式來移動／複製多個檔案。 請改用AEM Assets網頁UI，將檔案夾從Finder/Explorer拖曳至網路共用，或使用AEM Assets檔案夾上傳功能。

#### 資產移轉 {#asset-migration}

要規劃並執行資產從現有系統遷移到新系統或遷移儲存在伺服器上的大量資產，請參閱遷移 [指南](/help/assets/assets-migration-guide.md)。 AEM案頭應用程式和AEM到Creative Cloud的整合不支援此類移轉。 由於需要吸收的資產數量龐大，以及對元資料映射、轉換和提取的額外要求，因此應使用不同的工具和方法來處理遷移。

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/in/enterprise/using/adobe-asset-link.html)
>* [AEM案頭應用程式最佳範例](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [AEM與Adobe Stock整合](aem-assets-adobe-stock.md)

