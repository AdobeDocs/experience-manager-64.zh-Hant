---
title: Livefyre Feature Pack 2.0.6發行說明
seo-title: Livefyre Feature Pack 2.0.6 Release Notes
description: Livefyre Feature Pack 2.0.6發行說明
seo-description: Livefyre Feature Pack 2.0.6 Release Notes
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 2%

---

# Livefyre Feature Pack 2.0.6發行說明 {#livefyre-feature-pack-release-notes}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 發行資訊 {#release-information}

| 產品 | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| 版本 | 2.0.6 |
| 類型 | 功能發行 |
| 日期 | 2018 年 8 月 31 日 |
| 下載 URL | 請聯絡您的管理員 |
| 相容性 (*) | AEM 6.4 SP1、6.4、6.3 GA和6.2 SP1 |
| 說明 | 此套件可讓您整合Livefyre領先業界的組織功能與您的AEM執行個體，讓您在數分鐘內將寶貴的使用者產生內容(UGC)從社交網路發佈至您的網站。 |

## Livefyre Feature Pack 2.0.6包含的內容 {#what-is-included-in-livefyre-feature-pack}

此套件整合了Livefyre領先業界的組織功能與您的AEM例項，讓您能在數分鐘內將寶貴的使用者產生內容(UGC)從社交網路發佈至您的網站。 此套件有三種不同的元件：

**將UGC內容匯入AEM Assets**

* 使用UGC匯入工具，將Twitter和Instagram使用者產生的內容(UGC)從Livefyre Studio匯入AEM Assets。
* 存取您的Livefyre資料庫。
* 使用Livefyre Social搜尋即時在Twitter和Instagram上搜尋。
* 在UGC上管理權限。

**將Livefyre元件新增至AEM Sites或Communities**

* 使用一套社交元件（包括地圖、圖庫和媒體塗鴉牆），即時建立和自訂動態且吸引人的體驗。
* 在AEM Sites或社群中發佈UGC。

**透過AEM Commerce將產品目錄匯入Livefyre**

* 將您現有的產品目錄流暢整合至Livefyre，以促進使用者在您網站中的參與和轉換，並提供可購買的UGC體驗。
* 編輯或刪除AEM Commerce Product Catalog中的項目，並自動更新Livefyre中的變更。

如需安裝的說明，請參閱 [與Livefyre整合](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html).

### 其他發行資訊 {#additional-release-information}

由於更新會影響Instagram非業務使用者帳戶的內容匯總，因此我們無法代表您張貼意見或自動檢查作者的回覆。 [按一下這裡以了解更多資訊](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6不支援AEM Classic UI。

#### 新功能或改善 {#new-feature-or-improvement}

* 新增在Livefyre中設定權限要求社交帳戶前，可搜尋UGC的功能。 您必須設定社交帳戶以要求權限，或如果您擁有內容，則必須覆寫權限要求。
* Instagram和Twitter [UGC權限要求工作流程](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html) 已更新，以符合最新的API。
* 權限狀態和適當的動作現在會顯示在權限請求畫面上。

#### 錯誤修正 {#bug-fixes}

* 修正刪除Livefyre Studio中用於權限要求的社交帳戶時，在AEM中載入UGC程式庫時發生錯誤的問題。
* 修正Livefyre Studio中的資產計數與AEM UGC程式庫中的資產計數不符的問題。
* 修正UGC程式庫中，重設篩選選項後顯示篩選結果的問題。
* 修正AEM Commerce中，動作呼叫按鈕將使用者重新導向至錯誤URL的問題。
* 修正AEM Sites中將多個元件拖放至parsys預留位置導致其消失的問題。
* 修正在傳送權限請求時，可供選取停用之社交帳戶的問題。
* 修正從「資產」拖放UGC至「網站」時發生錯誤的問題。
* 修正將聊天和Liveblog元件拖放至Sites時，未建立應用程式的問題。
* 修正使用者嘗試留言時，「留言應用程式」產生錯誤的問題。
* 修正將Livefyre Media Wall App新增至網站時，會在Java內容存放庫中建立額外節點的問題。
* 修正造成Instagram UGC搜尋中發生分頁和控制台錯誤的問題。
* 修正Instagram使用者圖示在Assets中產生API錯誤的問題。
* 修正「審核」應用程式新增至無預先定義格式之網站的問題。
* 修正觸控式UI功能和內嵌編輯的問題。
* 修正匯入某些Instagram影像資產時發生錯誤的問題。
* 修正AEM中的Livefyre HTTP Client不支援Proxy設定的問題。
