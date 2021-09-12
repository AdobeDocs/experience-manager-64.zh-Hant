---
title: AEM與Creative Cloud整合最佳實務
description: 將AEM部署與Adobe Creative Cloud整合的最佳實務，以簡化資產傳輸工作流程並達到最高效率
contentOwner: AG
feature: Collaboration,Adobe Asset Link,Desktop App
role: User,Admin
exl-id: cb9bea05-3359-4fb4-b935-59e522a5f387
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '3566'
ht-degree: 16%

---

# AEM與Creative Cloud整合最佳實務 {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets是數位資產管理(DAM)解決方案，可與Adobe Creative Cloud整合，協助DAM使用者與創意團隊合作，簡化內容建立程式中的協作。

Adobe Creative Cloud為創意團隊提供解決方案和服務生態系統，協助他們建立數位資產。 它包括案頭和移動應用程式、雲端服務（如具有案頭同步功能或網頁體驗的儲存空間），以及Adobe Stock等市場。

請閱讀以了解根據您的使用案例在案頭和企業級DAM之間挑選哪些整合，以及連線工作流程的相關最佳實務。

>[!NOTE]
>
>AEM對Creative Cloud資料夾共用已淘汰，本指南不再涵蓋。 Adobe建議使用較新的功能，例如[Adobe資產連結](https://helpx.adobe.com/tw/enterprise/using/adobe-asset-link.html)或[AEM案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)，讓創意使用者能存取AEM中管理的資產。

## 創意人員、行銷人員和DAM使用者的共同作業需求 {#collaboration-needs-of-creatives-marketers-and-dam-users}

| 需求 | 使用案例 | 相關曲面 |
|---|---|---|
| 簡化案頭創意人員的體驗 | 為創意專業人員（更廣泛而言）簡化從DAM(AEM Assets)存取資產的程式，或是讓使用案頭的使用者在原生資產建立應用程式中工作。 他們需要簡單明瞭的方式來探索、使用（開啟）、編輯和儲存對AEM的變更，以及上傳新檔案。 | Win或Mac案頭；Creative Cloud應用程式 |
| 提供來自Adobe Stock的高品質、現成可用資產 | 行銷人員可協助進行資產來源搜尋和探索，協助加速內容建立流程。 創意專業人員可直接在其創意工具中使用已核准的資產。 | AEM Assets;Adobe Stock市集；中繼資料欄位 |
| 按組織分發和共用資產 | 內部部門/當地分支機構和外部合作夥伴、分銷商和代理使用母公司共用的已核准資產。 該組織希望安全無縫地共用已建立的資產，以便更廣泛地重複使用。 | Brand Portal, Asset Share Commons |

## Adobe產品以支援協作需求 {#adobe-offerings-to-support-the-collaboration-need}

| 相關角色的價值主張 | Adobe產品 | 相關曲面 |
|---|---|---|
| 創意使用者可從AEM探索資產、開啟及使用資產、編輯和上傳對AEM的變更，以及將新檔案上傳至AEM，而無須離開Creative Cloud應用程式。 | [Adobe資產連結](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop、Illustrator和InDesign |
| 業務使用者可簡化開啟和使用資產、編輯和上傳變更至AEM，以及從案頭環境將新檔案上傳至AEM。 他們會使用一般整合來開啟原生案頭應用程式中的任何資產類型，包括非Adobe的資產類型。 | [AEM 桌面應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | AEM案頭應用程式在Win和Mac案頭上 |
| 行銷人員和商務使用者可從AEM探索、預覽、授權及儲存及管理Adobe Stock資產。 授權和儲存的資產可提供選取的Adobe Stock中繼資料，以改善控管。 | [Experience Manager與Adobe Stock整合](aem-assets-adobe-stock.md) | AEM網頁介面 |

本文主要針對協作需求的前兩個方面。資產規模分配和採購作為一個使用案例被簡要提及。針對這些需求解決方案，請考慮Adobe品牌入口網站或資產共用公域。其他解決方案，例如[Brand Portal](https://helpx.adobe.com/tw/experience-manager/brand-portal/user-guide.html)，可以根據[Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)元件、[Link Share](/help/assets/link-sharing.md)，使用[Experience Manager資產](/help/assets/managing-assets-touch-ui.md)建立的解決方案，應根據特定需求審查。

![AEM的Creative Cloud連線：決定要使用的功能](assets/creative-connections-aem.png)

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

| 使用案例 | AEM 桌面應用程式 | 資料夾共用 | 其他解決方案 |
|---|---|---|---|
| 與Creative使用者共用較小數量(1)的DAM資產 | ✔✔ | ✔ |  |
| 與Creative使用者共用更多(2)個DAM資產 | ✔✔ | ✘ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [資產共用](assets-finder-editor.md) |
| 與可存取DAM的使用者共用DAM資產 | ✔✔ | ✔ | [連結共用](link-sharing.md) |
| 與無法存取DAM的使用者共用DAM資產 | ✘ | ✔✔ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [資產共用](assets-finder-editor.md) |
| 將較小的資產數量/數量儲存至DAM | ✔✔ | ✔ | [網頁UI上傳](managing-assets-touch-ui.md) |
| 將更多資產儲存至DAM(3) | ✔✔ | ✘ | [網頁UI上](managing-assets-touch-ui.md) <br> 傳自訂指令碼/工具 |
| 將大量資產移轉至DAM | ✘ | ✘ | [移轉指南](assets-migration-guide.md) |
| 在案頭上快速開啟資產 | ✔✔ | ✘ |  |
| 在案頭上快速開啟和變更資產 | ✔✔ | ✘ |  |

符號的圖例：

* ✔✔:首選解決方案
* ✔:可接受的解決方案
* ✘:不應用於使用案例

其他備注：

* （一）資產數量較少：例如，與專案或促銷活動相關的一小組資產
* （二）資產數量較多：例如，組織中所有已核准的資產
* (3)使用AEM案頭應用程式上傳資料夾功能

為支援資產散布使用案例，應考慮其他解決方案：

* [Brand ](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) Portal，適用於可設定、SaaS附加元件至AEM Assets，以發佈資產。
* 自訂解決方案是根據[資產共用公域](https://adobe-marketing-cloud.github.io/asset-share-commons/)程式碼基底所建立。
* AEM [連結共用](/help/assets/link-sharing.md)以使用連結來臨機共用資產。
* [AEM Assets ](/help/assets/managing-assets-touch-ui.md) web介面由AEM存取控制設定所保護的外部方的區域，以及必要的IT/網路配置調整，讓這些外部使用者能存取AEM。

## 重要概念和使用案例 {#key-concepts-and-use-cases}

### 常用術語表 {#glossary-of-common-terms}

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

* 請參閱[案頭應用程式最佳實務](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* 請參閱[Adobe Stock整合](aem-assets-adobe-stock.md)
* 請參閱[Adobe資產連結](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

以下是Experience Manager與Creative Cloud整合最佳實務的簡短摘要。 閱讀本檔案的其餘部分，以詳細了解這些內容。

* **對於在Photoshop、InDesign或Illustrator中工作的創意使用者：** Adobe Asset Link提供最佳的使用者體驗，包括對從AEM結帳的資產進行中工作的簡潔處理
* **** 為簡化從案頭存取任何一般檔案格式或應用程式的資產：使用AEM案頭應用程式
* **** 瞭解在DAM中儲存資產的原因及時機：更新將提供給組織中更廣大的團隊
* **** 請留意共用資產的數量：如果您的使用案例是資產分發，則治理和安全性可能是最重要的方面。請考慮使用大型工具 (例如品牌入口網站) 進行此作業。
* **** 瞭解資產生命週期：瞭解不同團隊在組織中如何處理資產
* **** 謹慎處理資產的頻繁儲存：Adobe Asset Link會透過PS、AI、ID為您處理。對於其他應用程式，請勿在映射/共用資料夾中執行進行中的工作，除非您需要DAM中的所有變更

### 從AEM Assets存取Adobe Stock資產 {#access-to-adobe-stock-assets-from-aem-assets}

[AEM與Adobe Stock](/help/assets/aem-assets-adobe-stock.md) 的整合可讓AEM使用者從Adobe Stock搜尋、預覽、授權及儲存資產至AEM。授權和儲存的Adobe Stock資產已選取Stock中繼資料，可用來搜尋含有額外篩選器的資產。

此整合的幾項重要要點：

* 從Adobe庫儲存存的資產儲存至AEM時，這些資產會變成一般AEM Assets，並以二進位檔儲存至AEM存放庫。 與Adobe Stock相關的某些中繼資料會儲存為AEM中的資產，否則擷取程式看起來與其他檔案相同。 例如，如果智慧標籤處於作用中狀態，則會在儲存時將標籤新增至這些資產。
* 儲存至AEM的資產是副本，而非回到Adobe Stock的連結。

**使用從Adobe Stock儲存至AEM的Creative Cloud**。此整合與Adobe資產連結無關，但Adobe資產連結會以這種方式辨識從Stock儲存的這些資產，並在Photoshop、Illustrator或InDesign的Adobe資產連結擴充功能UI中，在這些資產上顯示其他中繼資料和Stock圖示。 這些檔案可供瀏覽、開啟等使用，因為儲存至AEM時，這些檔案是一般的AEM資產。
在具有Adobe資產連結擴充功能的Creative Cloud應用程式中工作的創意使用者，除了可存取從Adobe Stock到AEM的已授權資產外，還可以使用Creative Cloud資料庫面板來搜尋、預覽和授權Adobe Stock資產。
授權並儲存至AEM的Adobe Stock資產可供存取AEM Assets部署的更多團隊使用，而透過「Creative Cloud資料庫」面板從Adobe Stock授權資產的創意工具，則預設只會在其Creative Cloud帳戶中供自己使用。

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## 關於在DAM中儲存資產 {#about-storing-assets-in-a-dam}

若要在創意與行銷/業務線(LOB)團隊之間設計有效的工作流程，並選擇最佳支援功能，請務必了解資產儲存於DAM的時間和原因。

### 資產為何儲存在DAM中 {#why-assets-are-stored-in-dam}

將資產儲存在DAM中，可讓資產輕鬆存取且可尋找。 它可確保組織或生態系統中的眾多使用者都能運用這些資產，包括合作夥伴、客戶等。

大多陣列織選擇僅儲存與下遊行銷/LOB流程相關的資產(透過AEM Sites發佈至Web管道或Adobe Experience Cloud、Advertising Cloud提供的其他管道，並由Analytics Cloud測量、提供給使用者/合作夥伴等)。 此外，組織會儲存DAM中可能經過審核/核准程式的資產。 這樣，DAM就能儲存大多數具有高利用機會的資產，並避免儲存閒置的資產。

儲存資產還需考慮技術和資源利用。 DAM提供儲存資產的其他相關服務，包括擷取中繼資料、版本設定、產生預覽/轉碼、管理參考以及新增存取控制資訊。 這些服務需要額外的時間和基礎架構資源。

通常，儲存所有資產和更新是不理想的。 例如，如果特定資產的更新品質不佳，且耗用過多資源，則資產可能不會儲存在DAM中。

### 資產儲存在DAM時 {#when-assets-are-stored-in-dam}

創意團隊（和組織）通常對在資產生命週期的每個階段儲存資產不感興趣。 例如，在下列情況下，他們會避免儲存資產：

* 尚未完成或有待試驗的資產
* 無法通過創意/內部團隊審核週期的資產
* 與相關資產相比，團隊有更好的候選人來代表其工作給外部團隊

通常，下列類別資產會儲存在DAM中：

* 已到期且被視為可供共用的資產
* 創意團隊預先選取的資產
* 根據特定合約或協定（例如，從RAW檔案轉換的JPG檔案、從PSD原始檔案轉換的TIFF/影像），市場營銷可使用或請求的特定資產格式

### 資產更新儲存於DAM時 {#when-updates-to-assets-are-stored-in-dam}

一般而言，DAM中只應儲存與較廣的DAM使用者集合相關的資產更新。 它可確保使用者（行銷和類似功能）只能在DAM資產時間軸中看到相關版本。

通常與資產生命週期中的主要里程碑相關的變更。 例如，創意團隊提供的初始創意就緒資產或根據請求/檢閱的官方更新應儲存在DAM中，並加以版本控制。

創意團隊在請求變更DAM中現有資產後進行更新，供行銷團隊檢閱，這是相關更新的範例。 應將其儲存並在DAM中加以版本控制，以供進一步參考或還原為舊版。

以下是通常不相關的更新範例：

* 在資產可供行銷審核之前先上傳的舊版資產
* 在創意團隊決定資產準備就緒前，會在進行中階段經常對資產進行創意變更

### DAM的使用者存取權 {#user-access-to-dam}

AEM Assets根據使用者對AEM Assets部署的存取權限，支援兩種使用者。 企業網路（防火牆）內的使用者通常可直接存取DAM。 企業網路以外的其他使用者無法直接存取。 使用者類型會從技術觀點決定可使用的整合。

#### 可直接存取DAM的創意使用者 {#creative-users-with-direct-access-to-dam}

內部創意團隊或已上線至內部網路的代理商/創意專業人員通常都能存取DAM例項，包括AEM登入。

在這種情況下，AEM案頭應用程式可協助您輕鬆存取最終/核准的資產，並將創意就緒的資產儲存至DAM。

#### 無法存取DAM的創意使用者 {#creative-users-without-access-to-dam}

無法直接存取DAM例項的外部機構和自由工作者可能需要存取已核准的資產，或想要將其新設計新增至DAM。

在這種情況下，您可以運用AEM/Creative Cloud整合來改善工作流程。 先決條件是創意使用者必須擁有Adobe ID，且擁有具有儲存服務的Creative Cloud帳戶。

使用下列策略來提供對最終/核准資產的存取權：

* 若要提供大量資產的存取權：使用[AEM Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html)，或客戶在AEM發佈基礎架構上實作[資產共用](assets-finder-editor.md)

* 若要提供對一些資產的存取：AEM與Adobe Creative Cloud的資料夾共用除了可以與AEM Assets Brand Portal或資產共用搭配使用。 請注意，此整合有某些限制，本文將詳細說明。

### 使用案例 {#use-cases}

下列使用案例說明DAM與設計人員案頭之間的各種工作流程類型。

#### 使用DAM中的資產建立新設計 {#creating-new-designs-using-assets-from-dam}

下圖說明數位資產的生命週期。 它說明創意使用者和DAM使用者（行銷人員、LOB使用者）如何運用現有資產，並使用這些資產來建立更多資產，並傳送給他們進行核准。

![chlimage_1-301](assets/chlimage_1-301.png)

資產生命週期包含下列階段：

1. 將核准的資產共用至創意案頭：DAM的最終資產可供創意使用者使用（案頭上）
1. 建立新設計（創意數位資產）:新檔案會儲存在進行中(WIP)區域中。
1. 在新設計中使用（放置）已核准資產：創意使用者使用Creative Cloud應用程式中現有的已核准資產來產生新資產
1. 經常保存WIP更新：創意使用者快速反覆並頻繁儲存檔案。 此時，創意使用者可能會與他人共同作業，但經常儲存的更新通常對DAM使用者不感興趣。
1. 資產達到創意就緒狀態，並儲存至「創意就緒」資料夾
1. 資產更新：DAM中的使用者可使用資產更新或新檔案
1. 資產投入生產：這是DAM程式，視組織而定，可能包括標籤、核准和變更存取控制。 此階段會將資產視為最終資產，而且可供更多團隊運用DAM來使用。 創意內容使用者也可以使用它來建立其他資產。

以下是一些關於如何透過此程式管理資產的一般建議：

* 對WIP檔案使用專用的儲存區域/系統，例如Adobe Creative Cloud Assets同步資料夾：與DAM使用者無關的經常更新，最好由專用系統處理，而非從AEM Assets內處理。 WIP資產可使用Adobe Creative Cloud案頭應用程式同步至本機磁碟、儲存於本機儲存空間等。
* 針對上傳至DAM的最終資產和資產使用個別資料夾/共用：為了更清楚明瞭，最終資產應該有自己的對應/共用資料夾（上方的「最終」範例），而要上傳回DAM的資產應該有自己的資產（「創意就緒」）

#### 變更DAM中管理的現有資產 {#changing-existing-assets-managed-in-dam}

在某些情況下，DAM中的資產可能需要變更。 範例包括：

* 請求從在AEM Assets中完成的審核和核准變更資產
* 對現有最終資產進行重大更新
* 快速編輯現有檔案（尤其是在最終核准之前）

在這種情況下，AEM案頭應用程式提供執行這些操作的最簡單方式。

![chlimage_1-302](assets/chlimage_1-302.png)

圖中描述的事件流如下：

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for AEM desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** 將資產從DAM共用至案頭，或直接在案頭上根據選擇的應用程式(例如Adobe Photoshop等)開啟。建議簽出以鎖定檔案。
* **2:** 微幅更新：編輯檔案並儲存變更。
* 步驟2的替代流量

   * **答：** 重大更新：如果檔案需要詳盡的變更集，則應間歇性儲存並複製至WIP資料夾/區域。
   * **B:** 在WIP資料夾中繼續處理檔案。儲存的變更不會同步至DAM中的版本
   * **C:** 更新完成後，檔案會複製回或儲存至對應的資料夾

* **3:** DAM會反映資產更新。簽入資產以解除鎖定。
* **4:** 資產投入生產。

以下是一些關於如何在此程式中管理資產的一般建議：

* 請避免直接儲存您從AEM案頭應用程式對應的網路共用中開啟的檔案，除非您對檔案所做的變更很小。
* 如果您想要進行其他變更、間歇性儲存或與創意團隊共同作業，請將檔案複製至個別的WIP資料夾。

#### 大量上傳至DAM {#bulk-upload-to-dam}

在某些情況下，您可能需要同時將大量檔案上傳至DAM，例如：

* 上傳像片或大型專案的結果
* 上傳由創意廣告公司提供的資產
* 如果選取是在DAM外部完成，則從較大的集合上傳選取的資產

請注意，本說明指的是以案頭使用者工作流程的一般部分，在運作上（例如每週或每次拍攝時等）上傳檔案。 此處未涵蓋大型資產遷移。

如果您想要大量上傳資產，可善用下列功能：

* 若要上傳大型/階層式資料夾，請使用AEM案頭應用程式，其提供[資料夾上傳](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload)功能。 您也可以上傳階層式資料夾結構。 資產會在背景上傳，因此不會系結至網頁瀏覽器工作階段
* 如果您要從單一資料夾上傳幾個檔案，請直接從案頭將檔案拖曳至Web UI，或使用AEM Assets Web UI中的「建立」選項。

>[!NOTE]
>
>您也可以使用自訂上傳程式，視您的業務需求而定。

#### 直接從案頭管理數位資產 {#managing-digital-assets-directly-from-desktop}

如果您使用網路檔案共用來管理數位資產，只要使用AEM案頭應用程式對應的網路共用，就會被視為方便的替代項目。 從網路檔案共用進行轉換時，請記住，AEM Web UI提供的數位資產管理功能集遠超網路共用（搜尋、集合、中繼資料、共同作業、預覽等）所能提供的功能，而AEM案頭應用程式則提供便利的連結，可將伺服器端的DAM存放庫與案頭上的工作連結。

避免使用AEM案頭應用程式直接在AEM Assets的網路共用中管理資產。 例如，請避免使用AEM案頭應用程式來移動/複製多個檔案。 請改為使用AEM Assets Web UI將資料夾從Finder/Explorer拖曳至網路共用，或使用AEM Assets資料夾上傳功能。

#### 資產移轉 {#asset-migration}

要規劃並執行從現有系統到新系統的資產遷移，或遷移儲存在伺服器上的大量資產，請參閱[遷移指南](/help/assets/assets-migration-guide.md)。 AEM案頭應用程式和AEM到Creative Cloud整合不支援這類移轉。 由於要內嵌的資產數量龐大，以及中繼資料對應、轉換和內嵌等其他需求，因此應使用不同的工具和方法來處理移轉。

>[!MORELIKETHIS]
>
>* [Adobe資產連結](https://helpx.adobe.com/in/enterprise/admin-guide.html/in/enterprise/using/adobe-asset-link.ug.html)
>* [AEM案頭應用程式最佳實務](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [AEM與Adobe Stock整合](aem-assets-adobe-stock.md)

