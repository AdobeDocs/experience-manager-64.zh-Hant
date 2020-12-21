---
title: 相容性包
seo-title: 相容性包
description: '在AEM Forms 6.4上安裝Compatibility套件可讓您使用AEM Forms 6.3的Correponsement Management資產，以及不建議使用的最適化表單範本和頁面 '
seo-description: 在AEM Forms 6.4上安裝Compatibility套件可讓您使用AEM Forms 6.3的Correponsement Management資產，以及不建議使用的最適化表單範本和頁面
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 1%

---


# 安裝相容性軟體包{#compatibility-package}

在AEM Forms 6.4上安裝Compatibility套件可讓您使用AEM Forms 6.3的Correponsement Management資產，以及不建議使用的最適化表單範本和頁面

## 概覽 {#overview}

在AEM Forms 6.4中建立客戶通訊的預設和建議方式是互動式通訊。若要繼續使用AEM 6.3 Forms和AEM 6.2 Forms的字母，您必須安裝[AEMFD Compatibility套件](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

AEMFD相容性套件可讓您在AEM Forms 6.4上使用AEM Forms 6.3和6.2的下列資產：

* 在AEM Forms 6.3和6.2中建立的檔案片段
* 字母
* 資料字典
* 不再支援的最適化表單範本和頁面

如需詳細資訊，請參閱「透過安裝Compatibility套件使資產與AEM Forms 6.4相容」。[](/help/forms/using/compatibility-package.md#assetsmadecompatible)

## 在AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}中新增對AEM Forms 6.3和6.2資產的支援

執行升級後，請執行下列動作以安裝AEMFD相容性套件，並讓您的資產與6.4相容：

請確定您已預先安裝[AEM Compatibility package](/help/sites-deploying/backward-compatibility.md)。

1. 安裝[Compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

   有關上載和安裝軟體包的詳細資訊，請參閱[如何使用軟體包](/help/sites-administering/package-manager.md)。

1. 穩定日誌後，重新啟動伺服器。
1. 使用移轉公用程式，讓資產與6.4相容。

   有關詳細資訊，請參見[遷移實用程式](/help/forms/using/migration-utility.md)。

## 透過安裝Compatibility套件{#assetsmadecompatible}，讓資產與AEM Forms 6.4相容

透過安裝「相容性」套件，您可讓下列資產和範本與AEM Forms 6.4相容：

* 來自AEM 6.3及舊版的Correponsement Management Assets

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

