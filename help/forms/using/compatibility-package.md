---
title: 相容性套件
seo-title: Compatibility Package
description: '在AEM Forms 6.4上安裝相容性套件可讓您使用AEM Forms 6.3的通信管理資產以及過時的適用性表單範本和頁面 '
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# 安裝相容性套件 {#compatibility-package}

在AEM Forms 6.4上安裝相容性套件可讓您使用AEM Forms 6.3的通信管理資產以及過時的適用性表單範本和頁面

## 概覽 {#overview}

在AEM Forms 6.4中，互動式通訊是建立客戶通訊的預設和建議方法。若要繼續使用AEM 6.3 Forms和AEM 6.2 Forms的信函，您需要安裝[AEMFD相容性套件](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)。

AEMFD相容性套件可讓您使用AEM Forms 6.4上AEM Forms 6.3和6.2的下列資產：

* 在AEM Forms 6.3和6.2中建立的檔案片段
* 字母
* 資料字典
* 適用性表單已棄用的範本和頁面

如需詳細資訊，請參閱安裝相容性套件](/help/forms/using/compatibility-package.md#assetsmadecompatible)讓資產與AEM Forms 6.4相容。[

## 新增對AEM Forms 6.3和AEM Forms 6.4中6.2資產的支援 {#add-support-for-aem-forms-and-assets-in-aem-forms}

執行升級後，請執行下列動作以安裝AEMFD相容性套件，並讓您的資產與6.4相容：

請確定您已預先安裝[AEM相容性套件](/help/sites-deploying/backward-compatibility.md)。

1. 安裝[相容性包](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)。

   有關上載和安裝包的詳細資訊，請參閱[如何使用包](/help/sites-administering/package-manager.md)。

1. 穩定日誌後，重新啟動伺服器。
1. 使用移轉公用程式，讓資產與6.4相容。

   如需詳細資訊，請參閱[migration utility](/help/forms/using/migration-utility.md)。

## 安裝相容性套件，使資產與AEM Forms 6.4相容 {#assetsmadecompatible}

安裝相容性套件後，您就可以讓下列資產和範本與AEM Forms 6.4相容：

* 來自AEM 6.3及舊版的通信管理資產

   * [字母](/help/forms/using/create-letter.md)
   * [資料字典](/help/forms/using/data-dictionary.md)
   * 文件片段

* 過時的適用性表單範本

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* 已棄用的適用性表單頁面：

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advandenrollment
