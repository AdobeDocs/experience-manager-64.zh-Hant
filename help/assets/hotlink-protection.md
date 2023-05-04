---
title: 在 Dynamic Media 中啟用超連結保護
seo-title: Activating hotlink protection in Dynamic Media
description: 有關如何在Dynamic Media中啟用熱連結保護的資訊。
seo-description: Information on how to activate hotlink protection in Dynamic Media.
uuid: 5f93bc27-5edd-4143-8701-87896c52f0af
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: a70aa448-0f58-4ed2-9381-afcc76fa827f
exl-id: 9e27d45e-1d72-4663-a2c5-2ec48f2b23c4
feature: Asset Management
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 11%

---

# 在 Dynamic Media 中啟用超連結保護 {#activating-hotlink-protection-in-dynamic-media}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

快速連結是指第三方網站使用HTML程式碼來顯示您網站的影像時。 每次請求圖片時，他們都會使用您的頻寬，因為訪客的瀏覽器會直接從您的伺服器存取圖片。 快速連結 *保護* 是防止其他網站直接連結至您網頁上的圖片、CSS或JavaScript的方法。 這種防護有助於減少您Dynamic Media帳戶下不必要的頻寬使用。

[Adobe客戶支援](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) 可在CDN層級設定反向連結篩選器，讓Dynamic Media內容只提供給網域允許之網站清單上的網站。

若要提供連結保護，您必須使用Adobe的隨附CDN。 若要啟用快捷連結保護，管理員必須建立支援票證，以要求對您的Dynamic Media帳戶進行配置變更。 激活直接連結保護無需額外費用。
