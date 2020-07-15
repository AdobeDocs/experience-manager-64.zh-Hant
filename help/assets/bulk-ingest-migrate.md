---
title: 安裝Feature Pack 18912以進行大量資產移轉
seo-title: 安裝Feature Pack 18912以進行大量資產移轉
description: 功能套件18912可讓您透過FTP大量收錄資產，或在AEM中將資產從Dynamic Media Classic移轉至Dynamic Media。 Adobe支援提供此選用功能套件。
seo-description: 功能套件18912可讓您透過FTP大量收錄資產，或在AEM中將資產從Dynamic Media Classic移轉至Dynamic Media。 Adobe支援提供此選用功能套件。
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: b1603091bb05493c9cfffa6067f414f73774edb2
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# 安裝功能套件18912以進行大量資產移轉 {#installing-feature-pack}

安裝功能套件18912是可選 _的_。

功能套件18912可讓您透過FTP將大量資產直接收錄至AEM的Dynamic Media - Scene 7模式，或從Dynamic Media Classic將資產移轉至AEM的Dynamic Media - Scene7模式。 您可從 [Adobe專業服務取得功能套件](https://www.adobe.com/experience-cloud/consulting-services.html)。

>[!NOTE]
>
>雖然您可以使用功能套件將資產自行從Dynamic Media Classic大量移轉至Dynamic Media - AEM中的Scene 7模式，或使用Dynamic Media Classic的FTP功能大量移轉資產，但Adobe不建議使用此方 ** 法，因為涉及的複雜性。
>
>因此，移轉功能套件（例如此套件）僅 *支援* ，做為 [Adobe專業服務移轉專案的一部分](https://www.adobe.com/experience-cloud/consulting-services.html)。

在安裝此功能套件之前，您必須先建立服務使用者並將該資訊提供給Adobe。

另請參 [閱設定動態媒體- Scene7模式](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)。

**若要安裝功能套件18912以進行大量資產移轉**,

1. 在您的AEM例項中，導覽至「工 **[!UICONTROL 具>安全性>使用者>建立使用者」]**。 此服務用戶必須具有對的讀／寫權限 `/content/dam`。
1. 在「 **[!UICONTROL ID]** 」和「 **[!UICONTROL Password]** 」欄位中輸入用戶名和密碼； 例如， `FTP User`。 此名稱會以建立資產的使用者身分出現在時間軸中。 當資產從FTP上傳時，當資產上傳至FTP伺服器並推送至AEM時，即視為已建立資產。
1. 請聯 [絡Adobe Enterprise Support for Experience Manager](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html) ，要求存取功能套件18912以進行下載。 當您聯絡支援人員時，可能需要下列資訊：

   * 您「作者」實例的伺服器IP地址，包括埠號（預設情況下，埠號為4502）。
   * AEM服務使用者使用者使用者名稱和密碼。

1. Adobe Enterprise Support for AEM提供您FTP認證和功能套件18912的存取權。

1. 收到功能套件18912時，請安裝它。

   如需 [在AEM中使用「軟體散發」和「套件](/help/sites-administering/package-manager.md) 」的詳細資訊，請參閱如何使用套件。
