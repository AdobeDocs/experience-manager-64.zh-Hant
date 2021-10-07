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
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# 安裝Feature Pack 18912以大量移轉資產 {#installing-feature-pack}

Feature Pack 18912的安裝為&#x200B;_optional_。

Feature Pack 18912可讓您透過FTP將資產大量直接內嵌至AEM上的Dynamic Media - Scene 7模式，或將資產從Dynamic Media Classic移轉至AEM上的Dynamic Media - Scene7模式。 此功能包可從[Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)取得。

>[!NOTE]
>
>雖然您可以使用Feature Pack，自行將資產從Dynamic Media Classic大量移轉至Dynamic Media — 以AEM的Scene 7模式，或是使用Dynamic Media Classic的FTP功能大量移轉資產，但由於相關複雜性，Adobe不建議使用&#x200B;*not*&#x200B;此方法。
>
>因此，透過[Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)的移轉專案僅支援&#x200B;**&#x200B;等移轉功能套件。

安裝此Feature Pack之前，您必須先建立Service使用者，並提供該資訊給Adobe。

另請參閱[設定Dynamic Media - Scene7模式](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)。

**若要安裝Feature Pack 18912以大量移轉資產**,

1. 在您的AEM例項中，導覽至「**[!UICONTROL 工具>安全性>使用者>建立使用者]**」。 此服務用戶必須具有`/content/dam`的讀/寫權限。
1. 在&#x200B;**[!UICONTROL ID]**&#x200B;和&#x200B;**[!UICONTROL 密碼]**&#x200B;欄位中，輸入用戶名和密碼；例如`FTP User`。 此名稱會以建立資產的使用者身分顯示在時間軸中。 從FTP上傳資產時，會將資產上傳至FTP伺服器並推送至AEM時，視為已建立資產。
1. 如需Experience Manager](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html)，請聯絡[Adobe客戶支援，以要求存取Feature Pack 18912以供下載。 聯絡支援人員時，您可能需要下列資訊：

   * 您Author例項的伺服器IP位址，包括連接埠號（依預設，連接埠號為4502）。
   * AEM服務使用者使用者名稱和密碼。

1. AdobeAEM客戶支援提供FTP憑證，以及Feature Pack 18912的存取權。

1. 收到Feature Pack 18912時，請安裝它。

   請參閱[如何使用套件](/help/sites-administering/package-manager.md) ，以取得在AEM中使用軟體發佈和套件的詳細資訊。
