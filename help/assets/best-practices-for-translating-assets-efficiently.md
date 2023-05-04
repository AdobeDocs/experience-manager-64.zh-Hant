---
title: 有效轉譯資產的最佳實務
description: 高效管理資產的最佳做法，以同步各種翻譯版本並簡化翻譯工作流程。
contentOwner: AG
feature: Translation
role: User,Admin
exl-id: 15162b80-ddef-4ec0-9db6-36695c93ebb1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 1%

---

# 有效轉譯資產的最佳實務 {#best-practices-for-translating-assets-efficiently}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets支援多語言工作流程，將數位資產的二進位檔、中繼資料和標籤轉譯為多個地區設定，以及管理翻譯的資產。 如需詳細資訊，請參閱 [多語言資產](multilingual-assets.md).

為有效管理資產以確保不同翻譯版本保持同步，請建立 [語言副本](preparing-assets-for-translation.md) 執行翻譯工作流程之前取得Assets的說明。

資產或一組資產的語言副本是具有類似內容階層的語言同層級項目（或相同語言中的資產版本）。

每個語言副本都是獨立的資產。 因此，將資產轉譯為多個地區設定可大幅增加CRX存放庫的大小。 例如，將總大小為10 GB的資產轉換為兩種語言，可將存放庫大小增加約20 GB（每種語言10 GB）。

與中繼資料和標籤相比，資產二進位檔佔用的儲存空間要大得多。 因此，如果轉譯中繼資料和標籤只符合您的目的，請忽略轉譯二進位檔。 您可以保留存放庫中二進位檔的原始副本，以便與轉譯為不同地區設定的中繼資料和標籤產生關聯。 維護單一二進位檔副本（而非多個轉譯版本），可將對存放庫大小的影響降至最低。

檔案資料儲存和Amazon S3資料儲存提供了最適合這些情況的儲存基礎結構。 這些儲存存放庫會儲存資產二進位檔的單一副本（包括轉譯），這些二進位檔可由多個地區設定中的中繼資料和標籤共用。 因此，建立資產語言復本以及轉譯中繼資料和標籤不會影響存放庫大小。

您也可以對一些工作流程和翻譯整合框架進行一些配置更改，以進一步簡化流程。

1. 執行下列任一項作業：

   * [設定檔案資料儲存](/help/sites-deploying/data-store-config.md)
   * [設定Amazon S3資料存放區](/help/sites-deploying/data-store-config.md)

1. 停用 [DAM中繼資料回寫](/help/sites-administering/workflow-offloader.md#disable-offloading) 工作流程

   正如名字所暗示的， *DAM中繼資料回寫* 工作流程會將中繼資料重新寫入二進位檔案。 因為中繼資料在翻譯後會變更，因此將其寫回二進位檔案會為語言副本產生不同的二進位。

   >[!NOTE]
   >
   >停用 *DAM中繼資料回寫* 工作流程會關閉XMP中繼資料對資產二進位檔的回寫。 因此，未來的中繼資料變更將不再儲存在資產中。 在禁用此工作流之前評估後果。

1. 啟用 *設定上次修改日期* 工作流程。

   此 *DAM中繼資料回寫* 工作流程會設定資產的上次修改日期。 因為您在步驟2中停用此工作流程， [!DNL Experience Manager Assets] 無法再將資產的最後修改日期保持為最新。 因此，請啟用 *設定上次修改日期* 工作流程，確保資產的上次修改日期為最新。 具有過時的上次修改日期的資產可能會導致錯誤。

1. [配置翻譯整合框架](/help/sites-administering/tc-tic.md) 停止轉譯資產二進位檔。 取消選取「資產」標籤下的「轉譯資產」選項，以停止轉譯Asset二進位檔。
1. 使用 [多語言資產工作流程](multilingual-assets.md).
