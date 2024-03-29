---
title: 網站管理
seo-title: Website Administration
description: 了解如何在AEM中管理多語言網站。
seo-description: Learn how to manage multilingual websites in AEM.
uuid: a32d458b-a5ad-46ef-a68c-4717c63b4bdd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: fabaa3e8-1657-4ed4-abb2-990117bec39c
exl-id: e8f83d21-b55e-4415-a581-8df1b71a84b1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 5%

---

# 網站管理{#website-administration}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

以下管理工具可用於管理網站和頁面：

* Multi Site Manager(MSM)可讓您在多個位置中使用相同的網站內容，同時允許變數：

   * [重複使用內容：多網站管理員和 Live Copy](/help/sites-administering/msm.md)

* 翻譯可讓您自動翻譯頁面內容、資產和使用者產生的內容，以建立和維護多語言網站：

   * [翻譯多語言網站的內容](/help/sites-administering/translation.md)

* 這兩項功能可結合，以迎合同時兼顧的網站需求 [多國語和多語言](#multinational-and-multilingual-sites).

## 跨國和多語言網站 {#multinational-and-multilingual-sites}

您可以結合使用「多網站管理員」和翻譯工作流程，以有效建立跨國和多語言網站的內容。 為特定國家/地區以一種語言建立主網站，然後使用該內容作為其他網站的基礎，在需要時使用翻譯：

* [翻譯](/help/sites-administering/translation.md) 將主版網站改成不同語言。

* 使用 [多網站管理員](/help/sites-administering/msm.md) 至：

   * 重新使用主版網站和翻譯的內容，為其他國家和文化建立網站。
   * 請務必將多站點管理器的使用限制為一種語言的內容，例如，國家/地區站點中的英語主語 — >英語分支、法語主語 — >國家/地區站點中的法語分支。
   * 如果需要，請分離即時副本的元素以添加本地化詳細資訊。

下圖說明主要概念如何交叉（但不顯示涉及的所有級別/元素）:

![chlimage_1-71](assets/chlimage_1-71.png)

>[!NOTE]
>
>在此及可比較的情況下，MSM不會管理這樣的不同語言版本。
>
>* [MSM](/help/sites-administering/msm.md) 在語言的邊界內管理從Blueprint（例如全局主版）到Live Copy（例如本地站點）的翻譯內容的部署。
>* 此 [翻譯](/help/sites-administering/translation.md) AEM的整合功能與第三方翻譯管理服務相結合，可管理語言並將內容翻譯成這些不同語言。
>
>如需更進階的使用案例，MSM也可跨語言主版使用。

>[!NOTE]
>
>針對所有使用案例，建議閱讀下列最佳實務：
>
>* [MSM最佳實務](/help/sites-administering/msm-best-practices.md);特別是：
   >
   >   * [建立網站](/help/sites-administering/msm-best-practices.md#create-site)
   >   * [MSM與多語言網站](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [翻譯最佳實務](/help/sites-administering/tc-bp.md)

