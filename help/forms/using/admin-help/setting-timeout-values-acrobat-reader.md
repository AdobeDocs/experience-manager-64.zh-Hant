---
title: 設定與Acrobat Reader DC擴充功能搭配使用的逾時值
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: 了解如何設定逾時值以搭配Acrobat Reader DC擴充功能使用。
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 2%

---

# 設定與Acrobat Reader DC擴充功能搭配使用的逾時值  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

在Acrobat Reader DC擴充功能中處理許多PDF檔案時，請確定下列逾時值已適當設定，以防止工作逾時和失敗：

**文檔處理超時**

此值可在管理控制台中設定。 按一下「設定」>「核心繫統設定」>「配置」，並指定「預設文檔處理超時」的值。

**User Manager AEM Forms逾時：** 此值可透過編輯config.xml檔案來設定。 在管理控制台中，按一下「設定>使用者管理>設定>匯入和匯出設定檔」，然後按一下「匯出」。 開啟導出的config.xml檔案並編輯以下行：

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

儲存，然後將config.xml檔案匯入回管理控制台。

**應用程式伺服器會話超時：** 此值可在應用程式伺服器上設定。 如需詳細資訊，請參閱應用程式伺服器隨附的檔案。
