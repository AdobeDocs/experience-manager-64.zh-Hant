---
title: Livefyre Feature Pack 2.0.6發行說明
seo-title: Livefyre Feature Pack 2.0.6發行說明
description: Livefyre Feature Pack 2.0.6發行說明
seo-description: Livefyre Feature Pack 2.0.6發行說明
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# Livefyre Feature Pack 2.0.6發行說明{#livefyre-feature-pack-release-notes}

## 發行資訊 {#release-information}

| 產品 | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| 版本 | 2.0.6 |
| 類型 | 功能發行 |
| 日期 | 2018年8月31日 |
| 下載URL | 聯絡您的管理員 |
| 相容性(*) | AEM 6.4 SP1、6.4、6.3 GA和6.2 SP1 |
| 說明 | 此套件可讓您將Livefyre領先業界的組織功能與AEM實例整合，讓您在幾分鐘內將重要的使用者產生內容(UGC)從社交網路發佈至您的網站。 |

## Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}包含哪些功能

此套件將Livefyre領先業界的組織功能與您的AEM實例整合，讓您在幾分鐘內將重要的使用者產生內容(UGC)從社交網路發佈至您的網站。 此軟體包有三個不同的元件：

**將UGC內容匯入AEM資產**

* 使用UGC匯入工具，將Twitter和Instagram使用者產生的內容(UGC)從Livefyre Studio匯入AEM Assets。
* 存取您的Livefyre資料庫。
* 使用Livefyre Social搜尋在Twitter和Instagram上即時搜尋。
* 管理UGC的權限。

**將Livefyre元件新增至AEM網站或社群**

* 使用一套社交元件（包括地圖、收藏館和媒體塗鴉牆），即時建立和自訂動態且引人入勝的體驗。
* 在AEM網站或社群中發佈UGC。

**使用AEM Commerce將產品目錄匯入Livefyre**

* 將您現有的產品目錄完美整合至Livefyre，以推動使用者在網站上的互動與轉化，並提供可購買的UGC體驗。
* 編輯或刪除AEM Commerce產品目錄中的項目，並自動更新Livefyre中的變更。

如需安裝的協助，請參閱[與Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)整合。

### 其他發行資訊{#additional-release-information}

由於更新會影響Instagram非商業使用者帳戶內容的匯總，因此我們無法再代表您張貼意見或自動檢查作者的回覆。 [按一下這裡以進一步瞭解](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/)。

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6不支援AEM Classic UI。

#### 新功能或改進{#new-feature-or-improvement}

* 新增在Livefyre中設定權限要求社交帳戶之前，先搜尋UGC的功能。 您必須設定社交帳戶以請求權限，或者如果您擁有內容，則覆寫權限請求。
* Instagram和Twitter [UGC權限要求工作流程](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)已更新，以符合最新的API。
* 權限狀態和適當動作現在會顯示在權限請求畫面上。

#### 錯誤修正 {#bug-fixes}

* 修正在Livefyre Studio中刪除用於權限要求的社交帳戶時，在AEM中載入UGC程式庫時發生錯誤的問題。
* 修正Livefyre Studio中的資產計數不符合AEM UGC程式庫中的資產計數的問題。
* 修正UGC程式庫中，在重設篩選選項後顯示篩選結果的問題。
* 修正AEM Commerce中，呼叫動作按鈕將使用者重新導向至錯誤URL的問題。
* 修正AEM Sites中拖放多個元件至parsys預留位置的問題，此問題會導致其消失。
* 修正在傳送權限要求時，停用的社交帳戶可供選擇的問題。
* 修正從「資產」拖放UGC至「網站」時產生錯誤的問題。
* 修正將聊天和Liveblog元件拖放至Sites時，未建立應用程式的問題。
* 修正當使用者嘗試留言時，「留言應用程式」產生錯誤的問題。
* 修正將Livefyre媒體塗鴉牆應用程式新增至網站時，在Java內容儲存庫中建立額外節點的問題。
* 修正造成Instagram UGC搜尋中分頁和控制台錯誤的問題。
* 修正Instagram使用者圖示在「資產」中產生API錯誤的問題。
* 已修正將「評論」應用程式新增至無預先定義格式之網站的問題。
* 修正Touch UI功能和內嵌編輯的問題。
* 修正匯入特定Instagram影像資產時造成錯誤的問題。
* 修正AEM中的Livefyre HTTP用戶端不支援Proxy設定的問題。
