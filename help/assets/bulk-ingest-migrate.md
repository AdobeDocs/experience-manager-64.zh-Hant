---
title: 安裝Feature Pack 18912以移轉大量資產
seo-title: Installing Feature Pack 18912 for bulk asset migration
description: Feature Pack 18912可讓您透過FTP大量內嵌資產，或在AEM中將資產從Dynamic Media Classic移轉至Dynamic Media。 此選用功能套件提供Adobe支援。
seo-description: Feature pack 18912 lets you either bulk ingest assets by way of FTP, or migrate assets from Dynamic Media Classic to Dynamic Media in AEM. This optional feature pack is available from Adobe support.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 4%

---

# 安裝Feature Pack 18912以大量移轉資產 {#installing-feature-pack}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

安裝Feature Pack 18912為 _可選_.

Feature Pack 18912可讓您透過FTP將資產大量直接內嵌至AEM上的Dynamic Media - Scene 7模式，或將資產從Dynamic Media Classic移轉至AEM上的Dynamic Media - Scene7模式。 此功能包可從 [Adobe Professional Services](https://www.adobe.com/tw/experience-cloud/consulting-services.html).

>[!NOTE]
>
>雖然您可以使用Feature Pack，自行將資產從Dynamic Media Classic大量移轉至Dynamic Media — 以AEM的Scene 7模式，或使用Dynamic Media Classic的FTP功能大量移轉資產，但Adobe確實如此 *not* 請根據相關複雜性建議此方法。
>
>因此，移轉功能套件（如此） *僅限* 作為遷移項目的一部分，通過 [Adobe Professional Services](https://www.adobe.com/tw/experience-cloud/consulting-services.html).

安裝此Feature Pack之前，您必須先建立Service使用者，並提供該資訊給Adobe。

另請參閱 [設定Dynamic Media - Scene7模式](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**若要安裝Feature Pack 18912以大量移轉資產**,

1. 在您的AEM例項中，導覽至 **[!UICONTROL 「工具」>「安全性」>「用戶」>「建立用戶」]**. 此服務用戶必須具有 `/content/dam`.
1. 在 **[!UICONTROL ID]** 和 **[!UICONTROL 密碼]** 欄位，輸入用戶名和密碼；例如， `FTP User`. 此名稱會以建立資產的使用者身分顯示在時間軸中。 從FTP上傳資產時，會將資產上傳至FTP伺服器並推送至AEM時，視為已建立資產。
1. 連絡人 [AdobeExperience Manager支援](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html) 請求存取feature pack 18912以供下載。 聯絡支援人員時，您可能需要下列資訊：

   * 您Author例項的伺服器IP位址，包括連接埠號（依預設，連接埠號為4502）。
   * AEM服務使用者使用者名稱和密碼。

1. AdobeAEM客戶支援提供FTP憑證，以及Feature Pack 18912的存取權。

1. 收到Feature Pack 18912時，請安裝它。

   請參閱 [如何使用套件](/help/sites-administering/package-manager.md) 以取得在AEM中使用Software Distribution和套件的詳細資訊。
