---
title: 有效率地轉譯資產的最佳實務
description: 有效管理資產的最佳做法，可同步各種翻譯版本並簡化翻譯工作流程。
contentOwner: AG
feature: Translation
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---


# 有效轉譯資產的最佳實務{#best-practices-for-translating-assets-efficiently}

Adobe Experience Manager(AEM)Assets支援多語言工作流程，將數位資產的二進位檔、中繼資料和標籤轉譯為多個地區，並管理翻譯的資產。 如需詳細資訊，請參閱[多語言資產](multilingual-assets.md)。

為有效管理資產以確保不同翻譯版本保持同步，請在執行翻譯工作流程之前先建立資產的[語言副本](preparing-assets-for-translation.md)。

資產或資產群組的語言副本是具有類似內容階層的語言同級（或資產的同級版本，以同一語言）。

每個語言版本都是獨立資產。 因此，將資產轉換為多個地區設定可大幅增加CRX儲存庫的大小。 例如，將總大小為10 GB的資產轉換為兩種語言可以將儲存庫大小增加約20 GB（每種語言為10 GB）。

資產二進位檔比中繼資料和標籤佔用的儲存空間要大得多。 因此，如果轉換中繼資料和標籤只符合您的目的，請省略轉換二進位檔。 您可以保留儲存庫中二進位檔案的原始副本，以便與翻譯為不同地區設定的元資料和標籤關聯。 維護一個二進位檔案副本（而不是多個翻譯版本），將對儲存庫大小的影響降至最低。

檔案資料儲存和AmazonS3資料儲存提供了最適合這些情況的儲存基礎架構。 這些儲存儲存庫儲存資產二進位檔案（包括轉譯）的單一副本，這些二進位檔案可由元資料和標籤在多個地區設定中共用。 因此，建立資產語言副本和翻譯元資料和標籤不會影響儲存庫大小。

您還可以對一些工作流和翻譯整合框架進行一些配置更改，以進一步簡化流程。

1. 執行下列任一項作業：

   * [設定檔案資料儲存區](/help/sites-deploying/data-store-config.md)
   * [設定AmazonS3資料儲存](/help/sites-deploying/data-store-config.md)

1. 停用[DAM MetaData回寫](/help/sites-administering/workflow-offloader.md#disable-offloading)工作流程

   如名稱所示，*DAM中繼資料回寫*&#x200B;工作流程會將中繼資料重新寫入二進位檔案。 由於中繼資料在轉譯後會變更，因此將它寫回二進位檔案會為語言副本產生不同的二進位檔。

   >[!NOTE]
   >
   >停用&#x200B;*DAM MetaData Writeback*&#x200B;工作流程會關閉資產二進位檔XMP案的中繼資料回寫。 因此，未來的中繼資料變更將不再儲存在資產中。 在禁用此工作流之前評估後果。

1. 啟用&#x200B;*設定上次修改日期*&#x200B;工作流程。

   *DAM MetaData Writeback*&#x200B;工作流程會設定資產的上次修改日期。 由於您在步驟2中停用此工作流程，AEM Assets無法再將資產的上次修改日期保持為最新。 因此，請啟用「設定上次修改日期&#x200B;*」工作流程，以確保資產的上次修改日期是最新的。*&#x200B;具有過時上次修改日期的資產可能會導致錯誤。

1. [配置翻譯整合框架以](/help/sites-administering/tc-tic.md) 停止翻譯資產二進位檔案。取消選取「資產」標籤下的「轉譯資產」選項，以停止轉譯資產二進位檔案。
1. 使用[多語言資產工作流程](multilingual-assets.md)翻譯資產中繼資料／標籤。

