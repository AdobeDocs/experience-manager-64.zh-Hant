---
title: AEM 6.4中的存放庫重新調整架構
seo-title: Repository Restructuring in AEM 6.4
description: 了解AEM 6.4中存放庫重新調整架構的基本概念和推理
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 2%

---

# AEM 6.4中的存放庫重新調整架構{#repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

在AEM 6.4之前，客戶代碼部署在JCR的不可預測區域，在升級時可能會有所變更。 因此，正式的AEM發行通常會覆寫自訂程式碼、設定或內容。 此外，客戶變更有時會覆寫AEM產品代碼或內容，導致產品功能中斷。

透過清楚定義AEM產品代碼和客戶代碼的階層，可以避免這些衝突。

為此，從AEM 6.4開始，為了在未來版本中繼續，內容將從/etc重組為存放庫中的其他資料夾，並附上內容所在位置的准則，請遵循下列高階規則：

* AEM產品程式碼一律會放置在/libs中，且不得由自訂程式碼覆寫
* 自訂程式碼應放置在/apps、/content和/conf中

## 對6.4升級的影響 {#impact-on-upgrades}

升級至AEM 6.4時，/etc底下的大部分內容會複製到存放庫中的其他資料夾中。 這些新位置是參考內容的偏好位置。 不過，我們已嘗試讓AEM 6.4升級回溯相容/etc資料夾中的先前位置，因此在大多數情況下，AEM程式碼會繼續參考舊位置，直到在客戶應用程式中主動（且在許多情況下手動）進行變更為止。 從時間軸的觀點來看，有兩類變更：

* 透過6.4升級 — 少數的/etc重組變更無法回溯相容，因此在AEM 6.4升級中，應規劃並實作修改。
* 在6.5升級之前 — 在將來的升級後的某個時間，絕大多數的/etc重組更改都可以延遲。 如先前所述，AEM 6.4程式碼將繼續參考舊位置，直到修改在客戶版本中實作為止。 雖然沒有應進行變更的強制時間表，但建議在6.5升級前進行，因為未來功能可能需仰賴參考的新位置。 此外，根據慣例，特定功能的檔案會參考新位置，因此，如果仍使用舊位置，則可能會造成混淆。

### 重組指導 {#restructuring-guidance}

規劃升級至AEM 6.4時，應參考下列各解決方案頁面，以評估工作成果：

* [所有AEM解決方案共同的存放庫重組](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [AEM Sites存放庫重組](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [AEM Assets存放庫重組](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html)
* [AEM Assets Dynamic Media存放庫重組](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [AEM Forms存放庫重組](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [AEM Communities存放庫重組](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [AEM商務存放庫重組](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

每個頁面包含與必要變更的緊急程度對應的兩個區段。 在「具有6.4升級」一節下的任何項目，都應作為AEM 6.4升級專案的一部分處理。 「6.5版升級前」下的任何項目可選擇延後至升級後。

頁面上的每個條目都包含一個「重新調整指南」欄位，該欄位詳細說明了建議的技術策略，以便與新的6.4儲存庫模型保持一致，以便參照先前位於/etc資料夾下的內容的新位置。 其他「附註」欄位可提供任何其他實用內容。
