---
title: '"Microsoft SQL Server資料庫：微調配置」'
seo-title: "Microsoft SQL Server database: Fine-tuning the configuration"
description: 了解如何微調Microsoft SQL Server資料庫的配置。
seo-description: Learn how you can fine tune the configuration of your Microsoft SQL Server database.
uuid: 2d618aab-3c67-4edb-a28f-a20904689e6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS, SG_AEMFORMS
discoiquuid: 70559a94-42ea-411a-a32f-5f38bc17ff96
exl-id: 5392027c-eb5a-49c4-bf9b-fe7d399ae0a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# Microsoft SQL Server資料庫：微調配置 {#microsoft-sql-server-database-fine-tuning-the-configuration}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

使用Microsoft SQL Server時，應更改預設配置設定。 按一下右鍵Enterprise Manager中的本地伺服器以訪問「屬性」對話框。

## 記憶體設定 {#memory-settings}

將最小記憶體分配更改為盡可能大的數字。 如果資料庫在單獨的電腦上運行，請使用所有記憶體。 預設設定不會積極分配記憶體，這會阻礙幾乎任何資料庫的效能。 在生產機器上分配記憶體時，您應該最積極。

## 處理器設定 {#processor-settings}

修改處理器設定，最重要的是，選中「在Windows上提升SQL Server優先順序」複選框，使伺服器使用盡可能多的週期。 「使用NT纖維」設定不那麼重要，但您也可以選擇它。

## 資料庫設定 {#database-settings}

更改資料庫設定。 最重要的設定是恢復間隔，它指定了崩潰後等待恢復的最長時間。 預設設定為1分鐘。 使用5到15分鐘的較大值可提高效能，因為它使伺服器有更多時間將更改從資料庫日誌寫入資料庫檔案。

>[!NOTE]
>
>此設定不會影響交易行為，因為它只會變更啟動時必須執行的記錄檔重播的長度。

將日誌和資料檔案的空間分配大小設定為比初始資料庫大得多。 考慮一年中資料庫的增長情況。 理想情況下，日誌和資料檔案在連續的範圍內分配，這樣資料就不會在整個磁碟上被碎片化。
