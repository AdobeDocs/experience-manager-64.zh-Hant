---
title: 最大限度地減少資料庫增長的提示
seo-title: Tips for minimizing database growth
description: 持續時間較長的處理程式會將處理資料儲存在AEM表單資料庫中。 使用一些簡單的流程設計和產品配置策略，可將AEM表單資料庫的增長降至最低。
seo-description: Long-lived processes store process data in the AEM forms database. The growth of the AEM forms database can be minimized using a few easy process design and product configuration strategies.
uuid: 13f99d4f-848e-451e-90d9-55e202dc0bdb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 89441336-babc-4d1f-9053-d1566cd42d22
exl-id: 7b266170-c7e2-42e7-8ee0-153e1e73a901
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# 最大限度地減少資料庫增長的提示 {#tips-for-minimizing-database-growth}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

持續時間較長的處理程式會將處理資料儲存在AEM表單資料庫中。 使用一些簡單的流程設計和產品配置策略，可將AEM表單資料庫的增長降至最低。

## 流程設計提示 {#process-design-tips}

盡可能使用短期流程。 短期進程不會將進程資料儲存在資料庫中。 使用短期進程的缺點是，在管理控制台中不會跟蹤其狀態和狀態，並且沒有進程的歷史記錄。

某些服務操作(如「分配任務」操作（用戶服務）)要求它們用於長期流程。 在這種情況下，您可以將流程細分為多個子流程，並盡可能縮短這些子流程的使用時間。 如果使用此策略，短期子進程應處理大資料項，如文檔值。

請謹慎使用變數。 使用長期進程時，對於每個進程實例，在資料庫上為進程中的每個變數分配空間。 策略性使用變數可節省相當大的空間。 例如，當程式中不再需要舊值時，您可以覆寫變數值。 並刪除您已建立且未使用的任何變數。 您可以驗證程式以尋找未使用的變數。

使用簡單變數類型（例如字串或int），並盡可能避免使用複雜的變數類型。 即使變數不含值，也會為變數分配資料庫空間。 複雜變數通常需要比簡單變數更多的空間。

## 產品管理秘訣 {#product-administration-tips}

有效使用全局文檔儲存(GDS)。 表單伺服器上的GDS目錄可用於儲存傳遞至流程中屬於AEM表單一部分之服務的檔案。 為了提高效能，較小的文檔會儲存在記憶體中並保存在資料庫中。

管理控制台公開「預設文檔最大內聯大小」屬性，用於配置儲存在記憶體中並保存在資料庫中的文檔的最大大小。 (請參閱 [配置一般AEM表單設定](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).) 如果將此屬性設定為低值，則大多數文檔都保存在GDS目錄中，而不保存在資料庫中。 優點是，當檔案儲存在GDS目錄中時，不再需要時，您可以更輕鬆地刪除這些檔案。
