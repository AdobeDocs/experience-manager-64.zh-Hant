---
title: 安裝Feature Pack 18912以進行大量資產移轉
seo-title: 安裝Feature Pack 18912以進行大量資產移轉
description: 功能套件18912可讓您透過FTP大量收錄資產，或將資產從Dynamic Media經典移轉至Dynamic MediaAEM。 此可選功能套件可從Adobe支援取得。
seo-description: 功能套件18912可讓您透過FTP大量收錄資產，或將資產從Dynamic Media經典移轉至Dynamic MediaAEM。 此可選功能套件可從Adobe支援取得。
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# 安裝功能套件18912以進行大量資產移轉{#installing-feature-pack}

功能包18912的安裝是&#x200B;_可選_。

功能套件18912可讓您透過FTP將大量資產直接內嵌至Dynamic Media- Scene 7模式，或AEM將資產從Dynamic Media經典移轉至Dynamic Media-Scene7模式AEM。 功能包可從[Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)取得。

>[!NOTE]
>
>雖然您可以使用功能套件自行將資產從Dynamic Media經典大量移轉至Dynamic Media-使用Dynamic Media經典的FTP功能在Scene 7模式中AEM，或大量移轉資產，但Adobe不建議使用&#x200B;*not*，因為涉及的複雜性。
>
>因此，遷移功能包（如此）僅&#x200B;*作為通過[Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)遷移項目的一部分支援*。

在安裝此功能套件之前，您必須先建立服務使用者並提供該資訊給Adobe。

另請參閱[配置Dynamic Media-Scene7模式](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)。

**若要安裝功能套件18912以進行大量資產移轉**,

1. 在您AEM的例項中，導覽至&#x200B;**[!UICONTROL 工具>安全性>使用者>建立使用者]**。 此服務用戶必須具有`/content/dam`的讀／寫權限。
1. 在&#x200B;**[!UICONTROL ID]**&#x200B;和&#x200B;**[!UICONTROL Password]**&#x200B;欄位中，輸入用戶名和密碼；例如，`FTP User`。 此名稱會以建立資產的使用者身分出現在時間軸中。 當資產從FTP上傳時，當資產上傳至FTP伺服器並推送至時，即視為已建立AEM資產。
1. 聯絡[Adobe企業支援以取得Experience Manager](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html)，要求存取功能套件18912以進行下載。 當您聯絡支援人員時，可能需要下列資訊：

   * 您「作者」實例的伺服器IP地址，包括埠號（預設情況下，埠號為4502）。
   * 服AEM務用戶用戶名和密碼。

1. Adobe企業支AEM援提供您FTP憑證和功能套件18912的存取權。

1. 收到功能套件18912時，請安裝它。

   有關在中使用軟體分發和軟體包的詳細資訊，請參閱[如何使用軟體包](/help/sites-administering/package-manager.md)AEM。
