---
title: 升級至 AEM 6.4 Forms
seo-title: Upgrade to AEM 6.4 Forms
description: 您可以從AEM 6.1 Forms、AEM 6.2 Forms和LiveCycleES4 SP1直接升級至AEM 6.3 Forms。
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# 在JEE升級至AEM 6.4 Forms {#upgrade-to-aem-forms-jee}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

根據您的環境，使用下列其中一個升級路徑。

## JEE版AEM 6.2 Forms或JEE版AEM 6.3 Forms > JEE版AEM 6.4 Forms {#aem-forms-jee-62-63-to-64}

請執行下列程式，將JEE上的現有AEM 6.2 Forms或JEE上的AEM 6.3 Forms升級至JEE上的AEM 6.4 Forms:

1. 從下載AEM 6.4 Forms on JEE安裝程式 [Adobe授權網站(LWS)](https://licensing.adobe.com/). 您需要有效的維護和支援合同才能下載安裝程式。
1. 請參閱 [升級檢查清單和規劃](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) 了解要執行的檢查，以確保成功升級。
1. 請參閱 [準備升級至AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) 學習並執行各項任務，以確保在最短的伺服器停機時間內正確運行升級。
1. 根據您現有的環境和應用程式伺服器，選擇以下文檔之一併按照說明操作。

   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms for JBoss](assets/upgrade-jboss.pdf)
   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms，以完成JBoss整套作業](assets/upgrade-turnkey.pdf)

## AEM 6.0 JEE上的Forms > JEE上的AEM 6.3 Forms {#aem-forms-jee-60-to-63}

無法從LiveCycleES2、LiveCycleES3、AEM 6.0 Forms、AEM 6.1 Forms直接升級至AEM 6.4 Forms。 您可以執行LiveCycle或AEM Forms的一或多個版本的中繼升級，然後從AEM 6.4 Forms升級。 如需中間版本清單及對應的升級指示，請參閱 [選擇升級路徑](upgrade.md).

## LiveCycleES4 SP1 > JEE上的AEM 6.4 Forms {#livecycle-es4sp1-forms-jee}

在JEE上將LiveCycleES4 SP1升級至AEM 6.4 Forms是不可用的升級，因為它涉及將資產和資料從舊版移轉至支援的應用程式伺服器、作業系統和資料庫的最新執行個體（新版本）。

以下概述將現有LiveCycleES4 SP1伺服器升級至AEM 6.4 Forms的程式。 有關詳細說明，請參閱流程結束時列出的文檔。

1. 升級前：

   1. 從下載AEM 6.4 Forms on JEE安裝程式 [Adobe授權網站(LWS)](https://licensing.adobe.com/). 您需要有效的維護和支援合同才能下載安裝程式。
   1. 決定要使用的內容存放庫（CRX存放庫）類型。 只有少數JEE功能上的AEM Forms會使用內容存放庫持續性來儲存內容和資產。 只有在您打算在JEE功能中使用此類AEM Forms時，才安裝及設定內容存放庫：

      * 在LiveCycleES4 SP1中，通信管理、Forms入口網站、HTML工作區和處理報告功能使用內容存放庫。 如果您未在LiveCycleES4中使用這些功能，且打算不在AEM Forms中使用這些功能，則不需要「內容存放庫」。
      * 在AEM Forms中，適用性Forms、通信管理、HTML5 Forms(在LiveCycleES4 SP1中稱為行動Forms)、Forms入口網站、HTML工作區、程式報表、OSGi上以Forms為中心的工作流程，功能使用內容存放庫。 如果您打算使用AEM Forms來執行這些功能，則需要「內容存放庫」。
      * 您不需要Content Repository（內容存放庫）才能使用AEM Forms檔案安全性。

      此外，LiveCycle的存放庫類型與AEM Forms不同。 如需可用的存放庫類型和相關資訊，請參閱 [為AEM Forms安裝選擇持續性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. 建立LiveCycleES4 SP1內容和資料的備份：

      建立LiveCycleES4 SP1資料庫、全局資料儲存(GDS)和crx-repository的備份（文檔安全性不需要）。 如果您要升級至MongoMK或RDBMK永續性，請將LiveCycleES4 SP1通信管理資產匯出至.cmp檔案中，並以AEM套件形式將資產表單。

   1. 確保JEE上的AEM 6.4 Forms支援您現有的平台(即應用程式伺服器、資料庫、作業系統、Adobe Acrobat、協力廠商應用程式和硬體)。 有關支援的硬體和軟體的資訊，請參閱 [支援的平台組合](/help/forms/using/aem-forms-jee-supported-platforms.md) 檔案。

      如果建立資料庫的新實例，請將步驟3中備份的資料導入資料庫。 有關如何將資料導入資料庫的資訊，請參閱相應資料庫供應商的文檔。

      >[!NOTE]
      >
      >如果您使用RDBMK持續性格式，請針對在JEE上的AEM Forms上執行的存放庫持續性和檔案服務使用單一資料庫。


1. 執行升級：

   1. 執行安裝程式，將AEM 6.4 Forms安裝在新伺服器上。 安裝程式會將所有必要檔案置於一個安裝目錄結構內的電腦上。
   1. 安裝完成後，請執行 **Configuration Manager** 設定各種AEM Forms模組並設定適當的設定。 除了配置設定，它還允許指定全局資料儲存(GDS)和crx-repository的路徑。

      >[!NOTE]
      >
      >在升級任務選擇螢幕上，選擇 **[!UICONTROL 從Adobe Experience Manager Forms 6.2.0升級]** 選項。 此 **[!UICONTROL 從Adobe Experience Manager Forms 6.2.0升級]** 選項可讓設定管理員從LiveCycleES4 SP1升級至AEM 6.4 Forms。

   1. (AEM Forms檔案安全性模組不需要)將內容匯入內容存放庫(CRX-Repository)至AEM 6.4 Forms伺服器。

      >[!NOTE]
      >
      >* 升級crx-repository並移轉內容後，請變更管理員帳戶的密碼。 如需詳細指示，請參閱 [更改現有用戶的密碼](/help/sites-administering/granite-user-group-admin.md).


1. 根據您的使用案例執行部署後任務以驗證登錄憑據、配置文檔服務、通信管理、文檔安全等。
1. 驗證伺服器是否升級成功：

   在升級的AEM Forms伺服器上執行一些常式操作，以確保伺服器升級成功。 您可以填寫並提交一些遷移的表單，或保護文檔以確保升級成功。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的結構已變更。 升級至AEM 6.4表單後，請使用您重新建立的已變更路徑進行自訂。 如需已變更路徑的完整清單，請參閱 [Forms 6.4中的存放庫重新調整架構](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**根據您現有的環境和應用程式伺服器，選擇以下文檔之一併按照詳細說明操作：**

* [從LiveCycleES4 SP1升級至AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle.pdf)
* [從LiveCycleES4 SP1升級至AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [從LiveCycleES4 SP1升級至AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [使用JBoss整套工具從LiveCycleES4 SP1升級至AEM 6.4 Forms](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycleES3 > JEE上的AEM 6.4 Forms {#livecycle-es3-forms-jee}

在JEE上將LiveCycleES3升級至AEM 6.4 Forms是不可用的升級，因為它涉及將資產和資料從舊版移轉至受支援應用程式伺服器、作業系統和資料庫的最新執行個體（新版本）。

以下概述將現有LiveCycleES3伺服器升級為AEM 6.4 Forms的程式。 有關詳細說明，請參閱流程結束時列出的文檔。

1. 升級前：

   1. 從下載AEM 6.4 Forms on JEE安裝程式 [Adobe授權網站(LWS)](https://licensing.adobe.com/). 您需要有效的維護和支援合同才能下載安裝程式。
   1. 決定要使用的內容存放庫（CRX存放庫）類型。 只有少數JEE功能上的AEM Forms會使用內容存放庫持續性來儲存內容和資產。 只有在您打算在JEE功能中使用此類AEM Forms時，才安裝及設定內容存放庫：

      * 在AEM Forms、適用性Forms、通信管理、HTML5 Forms、Forms入口網站、HTML工作區、程式報表，以及OSGi功能上以Forms為中心的工作流程中，使用內容存放庫。 如果您打算使用AEM Forms來執行這些功能，則需要「內容存放庫」。
      * 您不需要Content Repository（內容存放庫）才能使用AEM Forms檔案安全性。

      此外，LiveCycle的存放庫類型與AEM Forms不同。 如需可用的存放庫類型和相關資訊，請參閱 [為AEM Forms安裝選擇持續性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. 建立LiveCycleES3資料庫、全局資料儲存(GDS)和內容儲存庫的備份（文檔安全性不需要）。 如果您要升級至MongoMK或RDBMK持續性，請將LiveCycleES3通信管理資產匯出為封存。
   1. 確保JEE上的AEM 6.4 Forms支援您現有的平台(即應用程式伺服器、資料庫、作業系統、Adobe Acrobat、協力廠商應用程式和硬體)。 有關支援的硬體和軟體的資訊，請參閱 [支援的平台組合](/help/forms/using/aem-forms-jee-supported-platforms.md) 檔案。

      如果建立資料庫的新實例，請將步驟3中備份的資料導入資料庫。 有關如何將資料導入資料庫的資訊，請參閱相應資料庫供應商的文檔。

      >[!NOTE]
      >
      >如果您使用RDBMK持續性格式，請針對在JEE上的AEM Forms上執行的存放庫持續性和檔案服務使用單一資料庫。


1. 執行升級：

   1. 執行安裝程式，將AEM 6.4 Forms安裝在新伺服器上。 安裝程式會將所有必要檔案置於一個安裝目錄結構內的電腦上。
   1. 安裝完成後，請執行 **Configuration Manager** 設定各種AEM Forms模組並設定適當的設定。 除了配置設定，它還允許指定全局資料儲存(GDS)和crx-repository的路徑。

      >[!NOTE]
      >
      >在升級任務選擇螢幕上，選擇 **[!UICONTROL 從Adobe Experience Manager Forms 6.2.0升級]** 選項。 此 **[!UICONTROL 從Adobe Experience Manager Forms 6.2.0升級]** 選項可讓設定管理員從LiveCycleES3升級至AEM 6.4 Forms。

   1. (AEM Forms檔案安全性模組不需要)升級CRX存放庫並匯入AEM 6.4 Forms伺服器。

      >[!NOTE]
      >
      >升級crx-repository並移轉內容後，請變更管理員帳戶的密碼。 如需詳細指示，請參閱 [更改現有用戶的密碼](/help/sites-administering/granite-user-group-admin.md).
1. 根據您的使用案例執行部署後任務以驗證登錄憑據、配置文檔服務、通信管理、文檔安全等。
1. 驗證伺服器是否升級成功：

   在升級的AEM Forms伺服器上執行一些常式操作，以確保伺服器升級成功。 您可以填寫並提交一些遷移的表單，或保護文檔以確保升級成功。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的結構已變更。 升級至AEM 6.4表單後，請使用您重新建立的已變更路徑進行自訂。 如需已變更路徑的完整清單，請參閱 [Forms 6.4中的存放庫重新調整架構](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**根據您現有的環境和應用程式伺服器，選擇以下文檔之一併按照詳細說明操作：**

* [從LiveCycleES3升級至AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [從LiveCycleES3升級至AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [從LiveCycleES3升級至AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [使用JBoss Tunklying從LiveCycleES3升級至AEM 6.4 Forms](assets/upgrade-turnkey-livecycle-es3.pdf)
