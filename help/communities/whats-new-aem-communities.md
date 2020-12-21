---
title: AEM 6.4 Communities的新增功能
seo-title: AEM 6.4 Communities的新增功能
description: 'null'
seo-description: 'null'
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
translation-type: tm+mt
source-git-commit: 4a1be7a5a233557dff0e7cd3796380532f23d5eb
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 0%

---


# AEM 6.4 Communities的新增功能{#what-s-new-in-aem-communities}

AEM Communities為企業提供一個架構，讓其合作夥伴、客戶和員工之間進行協作。 它將社交功能引入網站結構，並協助企業與利益相關者互動並傳授知識，以提升其品牌價值。

AEM 6.4 Communities提供功能，以增強社群使用者的體驗，並簡化社群管理員、協調者和經理的日常工作。

進一步瞭解新功能和增強功能的快速簡介。 另請參閱AEM 6.4 Communities [發行說明](../release-notes/communities-release-notes.md)。 如需AEM 6.4 Communities檔案，請造訪[AEM 6.4 Communities使用指南](home.md)。

## 管理子社區或社區組{#managing-sub-communities-or-community-groups}

AEM Communities可讓社群管理員使用作者環境中預先定義的範本，在社群網站中建立群組和子群組。 這些群組是子社群，可繼承許多組態，例如父網站的主題和樣式。 但是，這些群組可能與父網站不同，例如具有不同群組協調者集合，或在安全性層級有所不同。 這些群體是獨立、羽翼豐滿的迷你社區，通過以下改進進一步增強了其能力。

### 在單一步驟{#create-multi-locale-groups-in-single-step}中建立多地區設定群組

在社群網站中，多語言群組可以透過單一操作來建立。 **[!UICONTROL 「社群群組範本」頁面中的「其他可]** 用社群群群組語言」欄位(在社群網站中建 **[!UICONTROL 立新社]**  [](groups.md) 群群組時提供)，讓您可以這麼做。

![多語言組-1](assets/multilingualgroup-1.png)

若要建立此類群組，使用者只需從「網站」主控台導覽至所需社群網站的「群組集合」即可。 建立群組，並在&#x200B;**[!UICONTROL 社群群組範本]**&#x200B;頁面的&#x200B;**[!UICONTROL 其他可用社群群組語言]**&#x200B;欄位中指定所需的語言。

### 從群組主控台{#delete-community-groups-from-groups-console}刪除社群群組

AEM 6.4 Communities在社群網站主控台的社群群組收集中，在現有的社群群組上提供「刪除群組」圖示。 如此一來，您只需按一下即可刪除[群組](groups.md#deleting-the-group)，並刪除與該群組相關的所有項目（例如內容和使用者成員資格）。

![deletegrp](assets/deletegrp.png)

### 在{#create-and-assign-enablement-resources-within-groups}群組中建立並指派啟用資源

現在，您可以針對一組特定目標社群成員建立、管理和發佈學習內容。 由於社群群組（不僅是整個社群網站）的目錄和指派功能可供使用，啟用管理員也可以[指派啟用資源](resource.md)和學習路徑給一小群人。

![指派目錄](assets/assignmentcatalog.png)

## 協調使用者產生的內容{#moderating-user-generated-content}

AEM 6.4 Communities對協調功能的改善很少，這有助於簡化社群協調者的日常生活。

### 自動垃圾郵件檢測{#automatic-spam-detection}

新的垃圾訊息偵測引擎有助於篩選社群網站或群組上不想要和未經請求的使用者產生的內容。 啟用後，此功能可以根據預先定義的垃圾訊息字詞集，將使用者產生的內容標示為垃圾訊息或非垃圾訊息。 協調者可進一步對內容採取行動以拒絕或允許內容出現在發佈例項中。 這些協調動作可以內嵌執行或透過大量協調主控台執行。

![spamdetection-1](assets/spamdetection-1.png)

[垃圾](moderate-ugc.md#spam-detection) 訊息偵測器可尋找並標籤特定使用者產生的內容，其正確性為90%。但是，此功能預設未啟用。 要啟用它，社區管理員需要導航到系統／控制台上的configMgr ，並添加垃圾郵件進程。

![spamprocess-1](assets/spamprocess-1.png)

### QnA {#new-answered-unanswered-filters-for-qna}的新（已應答／未應答）篩選器

AEM 6.4將兩個[新的篩選器](moderation.md#filter-rail)新增至大量協調主控台，名為QnA問題的已回答和未回答。 這些篩選器可在「篩選邊欄的狀態」下使用。

![狀態](assets/statuses.png)

在選取「已回答」狀態時，所有已回答的問題都會顯示在內容區域中的協調者。 但是，如果只選取「未回答」狀態，協調者將會看到除已回答問題外的所有內容（適用於所有內容類型），因為如果未回答問題，則負責「已答問題」的屬性不存在，而其他內容（如論壇主題、部落格文章或評論）則不存在。

### 書籤協調篩選{#bookmark-moderation-filters}

AEM Communities提供在協調主控台上將預先定義的協調篩選器[設為書籤的功能。 ](moderation.md#filter-rail)這些儲存的書籤稍後可重新檢視，並與其他使用者共用。

使用者只需從協調控制台的「篩選邊欄」中選取所需的篩選器，即可檢視篩選的UGC並在其瀏覽器上建立篩選器書籤。 這些篩選器會附加至URL字串的結尾，因此可以共用、重複使用並稍後重新檢視。

## 管理社區站點{#managing-community-sites}

AEM 6.4 Communities提供網站管理增強功能，可確保網站管理員輕鬆建立、管理和刪除許多不同語言的社群網站。

### 在單一步驟中建立多地區設定社群網站{#create-multi-locale-community-sites-in-one-step}

AEM Communities允許在單一作業中建立[多語言社群網站](create-site.md)。 這可能是因為在從站點控制台建立新社區站點時，**[!UICONTROL 站點模板]**&#x200B;頁面的&#x200B;**[!UICONTROL 社區站點基本語言]**&#x200B;欄位中提供了多種語言可供選擇。

![多本地化](assets/multilocalesite.png)

用戶可以同時為所有這些站點選擇配置資料夾、品牌和許多其他配置。

### 從站點控制台{#delete-community-sites-from-sites-console}刪除社區站點

AEM 6.4 Communities在社群網站主控台中，提供現有社群網站上的「刪除網站」圖示。 如此一來，[便能在按一下時刪除網站](create-site.md)和相關項目。

![siteactions](assets/siteactions.png)

## 管理UGC和用戶配置檔案{#managing-ugc-and-user-profiles}

AEM Communities將使用者資料保護放在社群體驗的核心，會公開[現成可用的API](user-ugc-management-service.md)和[範例servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet)。 這些API可協助大量管理（大量刪除和大量匯出）使用者產生的內容並刪除使用者個人檔案，並有助於處理EU GDPR合規性要求。

## {#what-s-changed}的變更

* AEM 6.4 Communities在建立新社群網站時，不再提供現成可用的驗證功能。 不過，Communities網站可自訂為包含[Google元件reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html)，以提高安全性。
* 上傳自訂CSS的選項已從社群網站和群組主題中移除。
* 「大量協調」UI中的「篩選邊欄」中已新增「僅限內容」和「搜尋」圖示。
* 「大量協調」UI的「篩選邊欄」中已新增「內容路徑」篩選。
* 已從「大量協調」UI移除切換至大量模式和「退出大量模式」。 要進入多選模式，請按一下貼文上的「選擇」(![selecticon](assets/selecticon.png))表徵圖，該表徵圖在將滑鼠（案頭）懸停在貼文上或在貼文上按住手指（移動）時顯示。
