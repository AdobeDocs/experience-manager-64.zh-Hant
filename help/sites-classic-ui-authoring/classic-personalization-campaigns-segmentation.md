---
title: 了解分段
seo-title: Understanding Segmentation
description: 區段是建立促銷活動時的主要考量。 在大多數情況下，您在開始行銷活動之前必須先定義區段。
seo-description: Segmentation is a key consideration when creating a campaign. In most cases, you will need to have segments already defined before starting your campaign.
uuid: 609d83b3-df0e-44ad-8e27-90b676d2666b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: bb75f4ab-d983-45f6-98a3-da8bd9b63751
exl-id: 441cf983-e1dc-4343-9c2c-e5ed5891e84b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 2%

---

# 了解分段{#understanding-segmentation}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

區段是建立促銷活動時的主要考量。 在大多數情況下，您在開始行銷活動之前必須先定義區段。

網站訪客來到網站時，其興趣和目標不同。 了解這些目標並滿足期望是線上行銷的重要成功因素。

分段功能可透過分析訪客的以下項目並加以特性，來達到此目的：

* 網站上的活動
* 側面像
* 其他網站上的活動

接著，內容便可根據訪客的需求和興趣來明確鎖定目標，具體取決於其相符的區段。

## 使用區段 {#using-segmentation}

區段定義於 [設定區段](/help/sites-administering/campaign-segmentation.md). 它們可用來指引特定目標對象所看到的實際內容。

## 區段術語 {#segmentation-terminology}

討論區段時，會使用下列術語：

**訪客** 訪客是指瀏覽網站的人。 該人員的造訪通常從反向連結頁面開始，然後移至您自己網站上的一或多個頁面檢視。 行為設定檔可從該人員造訪的詳細資訊建立。

**使用者** 使用者是在網站註冊以接收帳戶設定檔的訪客。 為了產生其設定檔，他們提供額外的身分識別，例如電子郵件地址和性別等。 您也可以收集其他資訊，包括社群活動和購買模式等。 根據設定檔中提供的資訊，可以建立人口統計設定檔。

**特徵** 特徵是訪客的特性或屬性，可用來判斷特定區段的成員資格。

**區段** 區段是共用特定特徵的訪客集合。 區段應具有獨特性，且與其他區段之間應有最低重疊。

**行為特徵** 行為特徵是指與訪客在網站上的行為相關的特徵。 這些類別包括：

* 您網站的興趣；包括瀏覽的頁面和購買的產品。
* 引用網站的興趣；包括搜索詞，或點擊廣告。
* 對其他網站的興趣；使用Spyjax等工具確定。
* 訪客忠誠度；瀏覽的持續時間、瀏覽的頻率。

**人口統計特徵** 這些是選定的母體特徵，包括：

* 年齡
* 收入
* 家族大小
* 婚姻狀況
* 性別
* 位置

**衍生特徵**

有些人口特徵在沒有註冊的情況下很難判斷，但可以結合行為和人口特徵來衍生。

例如，將反向連結URL（作為行為特徵）與人口統計資料(從工具(例如 [Google Ad Planner](https://www.google.com/adplanner/))可讓網站擁有者衍生其訪客的人口統計特徵。

**子區段** 一區段可細分為數個子區段。 這需透過定義其他特徵來完成。

**預告頁面** 預告頁面會導向特定對象。 它包含可用於宣傳預告段落的可重複使用內容。

**行銷活動** 促銷活動是宣傳頁面和電子郵件行銷頁面（例如電子報或邀請）的集合。 通常，促銷活動會執行一段有限的時間，並由另一個促銷活動取代。

**預告段落** 這是根據選取策略從其他頁面提取內容的段落。 此選擇策略可將區段和行銷活動納入考量。

**清單** 會從註冊使用者的區段中擷取清單。 例如，用於指導預告段落內容的位置。

>[!NOTE]
>
>請參閱 [區段](/help/sites-administering/campaign-segmentation.md) 以取得AEM中區段的詳細資訊。
