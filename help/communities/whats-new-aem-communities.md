---
title: AEM 6.4社群的新功能
description: AEM Communities為企業提供框架，以便其合作夥伴、客戶和員工之間進行協作。
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 0%

---

# AEM 6.4社群的新功能 {#what-s-new-in-aem-communities}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Communities為企業提供框架，以便其合作夥伴、客戶和員工之間進行協作。 它將社交功能導入網站結構，並幫助企業參與並傳授知識給利益相關方，以提升其品牌價值。

AEM 6.4 Communities提供增強社群使用者體驗的功能，並簡化社群管理員、協調者和管理員的日常工作。

深入閱讀，快速了解新功能和增強功能。 另請參閱AEM 6.4 Communities [發行說明](../release-notes/communities-release-notes.md). 如需AEM 6.4 Communities檔案，請造訪 [AEM 6.4 Communities使用指南](home.md).

## 管理子社區或社區組 {#managing-sub-communities-or-community-groups}

AEM Communities可讓社群管理員在製作環境中，使用預先定義的範本，在社群網站內建立群組和子群組。 這些群組可作為子社群，而子社群可繼承許多設定，例如父網站的主題和樣式。 不過，這些群組可能與父網站不同，例如有一組不同的群組協調者，或者安全層級可能有所不同。 這些群體作為獨立、完整的小型社區發揮作用，這些社區通過以下改進進一步增強了能力。

### 在單一步驟中建立多地區設定群組 {#create-multi-locale-groups-in-single-step}

作為社群網站的一部分，多語言群組可在單一操作中建立。 **[!UICONTROL 其他可用的社群群組語言]** 欄位 **[!UICONTROL 社群群組範本]** 頁面，此頁面在建立 [新社群組](groups.md) 在社群網站中，便能實現此目標。

![多語言組–1](assets/multilingualgroup-1.png)

若要建立這類群組，使用者只需從Sites主控台導覽至所需社群網站的「群組集合」即可。 建立群組，並在 **[!UICONTROL 其他可用的社群群組語言]** 欄位 **[!UICONTROL 社群群組範本]** 頁面。

### 從群組控制台刪除社群群組 {#delete-community-groups-from-groups-console}

AEM 6.4社群在社群網站主控台的社群群組收集中，提供現有社群群組上的刪除群組圖示。 如此可啟用 [組刪除](groups.md#deleting-the-group) 按一下，並刪除與該組關聯的所有項（如內容和用戶成員）。

![deletegrp](assets/deletegrp.png)

### 在群組中建立並指派啟用資源 {#create-and-assign-enablement-resources-within-groups}

現在可以針對特定一組目標社群成員來建立、管理和發佈學習內容。 由於可用於社區組（不僅是整個社區站點）的目錄和分配功能，啟用管理人員可以 [指派啟用資源](resource.md) 學習通往一小群人的道路。

![assignmentcatalog](assets/assignmentcatalog.png)

## 協調使用者產生的內容 {#moderating-user-generated-content}

AEM 6.4 Communities對調節功能幾乎沒有改善，有助於緩解社群協調者的日常生活。

### 自動垃圾郵件檢測  {#automatic-spam-detection}

新的垃圾郵件檢測引擎有助於過濾掉用戶在社區站點或組上生成的不需要和未經請求的內容。 啟用後，此功能可以根據預定義的一組垃圾郵件單詞將用戶生成的內容標籤為「垃圾郵件」或「非垃圾郵件」。 協調者可進一步針對內容採取動作，以拒絕或允許內容出現在發佈執行個體上。 這些協調動作可內嵌執行，或透過大量協調主控台執行。

![spamdetection-1](assets/spamdetection-1.png)

[垃圾郵件檢測器](moderate-ugc.md#spam-detection) 以90%的準確度，尋找並標籤指定一段使用者產生的內容。 不過，預設不會啟用此功能。 要啟用此功能，社區管理員需要導航到系統/控制台上的configMgr ，並添加垃圾郵件進程。

![spamprocess-1](assets/spamprocess-1.png)

### QnA的新（已應答/未應答）篩選器 {#new-answered-unanswered-filters-for-qna}

AEM 6.4新增兩個 [新篩選器](moderation.md#filter-rail)，針對QnA問題已命名為已回答和未回答，以大量協調主控台。 這些篩選器可在「篩選器邊欄」的「狀態」下使用。

![狀態](assets/statuses.png)

選取「已回答」狀態時，內容區域中的版主將看到所有已回答的問題。 但是，如果僅選擇「未回答」狀態，則版主將看到除已回答問題之外的所有內容（適用於所有內容類型），因為在未回答的問題和其他內容（如論壇主題、部落格文章或評論）中，不存在負責「已答問題」的屬性。

### 書籤協調篩選器 {#bookmark-moderation-filters}

AEM Communities提供 [為預先定義的協調篩選建立書籤](moderation.md#filter-rail) 在協調控制台上。 稍後可重新檢視這些已儲存的書籤，並與其他使用者共用。

使用者只需在協調控制台的「篩選邊欄」中選取所需的篩選器，即可檢視篩選過的UGC，並將篩選器加入書籤即可。 這些篩選器會附加至URL字串的結尾，因此可以共用、重複使用，並在稍後重新檢視。

## 管理社群網站 {#managing-community-sites}

AEM 6.4 Communities提供網站管理增強功能，可確保網站管理員輕鬆建立、管理及刪除許多不同語言的社群網站。

### 在一個步驟中建立多地區設定社群網站 {#create-multi-locale-community-sites-in-one-step}

AEM Communities允許建立 [多語言社群網站](create-site.md) 單次操作。 這可能是因為有多種語言可供在中選取 **[!UICONTROL 社區站點基語言]** 欄位 **[!UICONTROL 網站範本]** 頁面，同時從sites console建立新的社群網站。

![多本地化](assets/multilocalesite.png)

用戶可以同時為這些站點選擇配置資料夾、品牌和許多其他配置。

### 從站點控制台刪除社區站點 {#delete-community-sites-from-sites-console}

AEM 6.4社群在社群網站控制台中，提供現有社群網站上的「刪除網站」圖示。 這可讓 [刪除站點](create-site.md) 和關聯項目。

![網站動作](assets/siteactions.png)

## 管理UGC和使用者設定檔 {#managing-ugc-and-user-profiles}

AEM Communities揭露將使用者資料保護置於社群體驗的核心 [API現成可用](user-ugc-management-service.md) 和 [範例servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). 這些API有助於大量管理（大量刪除和大量匯出）使用者產生的內容和刪除使用者設定檔，且有助於處理EU GDPR法規遵循要求。

## 變更 {#what-s-changed}

* AEM 6.4 Communities中不再提供現成可用的驗證碼驗證，以建立新的社群網站。 不過，Communities網站可自訂為包含 [Google元件reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) 以提高安全性。
* 上傳自訂CSS的選項已從社群網站和群組主題中移除。
* 已在大量協調UI的篩選欄中新增「僅限內容」和「搜尋」圖示。
* 已在大量協調UI的篩選欄中新增內容路徑篩選。
* 已從大量協調UI中移除切換至大量模式和退出大量模式。 要進入多選模式，請按一下選擇( ![選擇](assets/selecticon.png))圖示，此圖示會顯示在透過滑鼠（案頭）暫留在貼文上，或按住手指（行動）。
