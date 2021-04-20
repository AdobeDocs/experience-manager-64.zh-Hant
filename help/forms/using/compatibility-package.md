---
title: 相容性包
seo-title: 相容性包
description: '在AEM Forms6.4上安裝相容性軟體包可讓您使用AEM Forms6.3的通信管理資產和不建議使用的自適應表單模板和頁面 '
seo-description: 在AEM Forms6.4上安裝相容性軟體包可讓您使用AEM Forms6.3的通信管理資產和不建議使用的自適應表單模板和頁面
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 9%

---


# 安裝相容性軟體包{#compatibility-package}

在AEM Forms6.4上安裝相容性軟體包可讓您使用AEM Forms6.3的通信管理資產和不建議使用的自適應表單模板和頁面

## 概覽 {#overview}

在AEM Forms6.4中，互動式通訊是建立客戶通訊的預設和建議方式。要繼續使用來自AEM6.3Forms和AEM6.2Forms的字母，需要安裝[AEMFD相容性軟體包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

AEMFD相容性軟體包允許您使用AEM Forms6.4上AEM Forms6.3和6.2的以下資產：

* 在AEM Forms6.3和6.2中建立的檔案片段
* 字母
* 資料字典
* 不再支援的最適化表單範本和頁面

如需詳細資訊，請參閱[透過安裝Compatibility套件使資產與AEM Forms6.4相容。](/help/forms/using/compatibility-package.md#assetsmadecompatible)

## 在AEM Forms6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}中增加對AEM Forms6.3和6.2資產的支援

執行升級後，請執行下列動作以安裝AEMFD相容性套件，並讓您的資產與6.4相容：

確保已預裝[AEM Compatibility package](/help/sites-deploying/backward-compatibility.md)。

1. 安裝[Compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

   有關上載和安裝軟體包的詳細資訊，請參閱[如何使用軟體包](/help/sites-administering/package-manager.md)。

1. 穩定日誌後，重新啟動伺服器。
1. 使用移轉公用程式，讓資產與6.4相容。

   有關詳細資訊，請參見[遷移實用程式](/help/forms/using/migration-utility.md)。

## 通過安裝Compatibility軟體包{#assetsmadecompatible}使與AEM Forms6.4相容的資產

通過安裝Compatibility軟體包，您可以使以下資產和模板與AEM Forms6.4相容：

* 6.3版及更舊版本AEM的Commentering Management資產

   * [字母](/help/forms/using/create-letter.md)
   * [資料字典](/help/forms/using/data-dictionary.md)
   * 文件片段

* 不建議使用的最適化表單範本

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* 最適化表單已過時的頁面：

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment

