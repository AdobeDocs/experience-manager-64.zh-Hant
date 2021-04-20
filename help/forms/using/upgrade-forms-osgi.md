---
title: 升級至 AEM 6.4 Forms
seo-title: 升級至 AEM 6.4 Forms
description: '您可以執行從6.1 AEMForms、AEM 6.2Forms和LiveCycleES4 SP1到AEM6.3Forms的直接升級。 '
seo-description: '您可以執行從6.1 AEMForms、AEM 6.2Forms和LiveCycleES4 SP1到AEM6.3Forms的直接升級。 '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 9%

---


# 升級至AEMOSGi {#upgrade-to-aem-forms-osgi}上的Forms6.4版

請根據您的環境，使用下列升級途徑之一。

## AEM  6.2FormsAEM或6.3FormsAEM > 6.4Forms{#upgrade-aem-forms-62-63-to-64}

您可以執行從6.2Forms或6.3AEMForms直AEM接升級到AEM6.4Forms。 請執行下列動作：

1. 將現有AEM實例升AEM級至6.4。步驟如下：

   1. 安裝適用於6.2Forms或AEM6.3Forms的最AEM新Service Pack和修補程式。 如需詳細資訊，請參閱：

      * [AEM 6.2 發行說明](https://helpx.adobe.com/tw/experience-manager/6-2/release-notes.html)
      * [AEM 6.3 發行說明](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html)
      * [AEM維護中樞](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)
   1. 準備升級的源實例。 如需詳細步驟，請參閱[升級至AEM6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance)。
   1. 下載[AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software)。
   1. **（僅限基於Unix/Linux的安裝）** 如果您使用UNIX或Linux作為底層作業系統，請開啟終端窗口，導航到包含crx-quickstart的資料夾，然後運行以下命令：

      `chmod -R 755 ../crx-quickstart`

   1. 將您的AEM實例升AEM級至6.3。如需逐步指示，請參閱[升級至AEM6.4](/help/sites-deploying/upgrade.md)。

      在繼續後續步驟之前，請等待&lt;crx-repository>/error.log檔案中停止顯示ServiceEvent REGISTERED和ServiceEvent UNREGISTERED消息。

      >[!NOTE]
      >
      >伺服器啟動並運行後，一些AEM Forms捆綁包仍處於安裝狀態。 每個安裝的捆綁包數量可能不同。 您可以安全地忽略這些束的狀態。 捆綁列在`https://[server]:[port]/system/console/`。


1. 安裝AEM Forms附加套件。 步驟如下：

   1. 開啟 [Software Distribution](https://experience.adobe.com/downloads)。您需要 Adobe ID 才能登入 Software Distribution。
   1. 點一下頁首功能表中的 **[!UICONTROL Adobe Experience Manager]**。
   1. 在&#x200B;**[!UICONTROL Filters]**&#x200B;區段中：
      1. 從&#x200B;**[!UICONTROL Solution]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL Forms]**。
      1. 選擇包的版本和類型。 您也可以使用&#x200B;**[!UICONTROL 搜尋下載]**&#x200B;選項來篩選結果。
   1. 點選適用於您作業系統的套件名稱，選取「**[!UICONTROL 接受EULA條款]**」，然後點選「**[!UICONTROL 下載]**」。
   1. 開啟[套件管理器](https://docs.adobe.com/content/help/zh-Hant/experience-manager-65/administering/contentmanagement/package-manager.html)，然後按一下&#x200B;**[!UICONTROL 「上傳套件」]**&#x200B;即可上傳套件。
   1. 選擇軟體包並按一下&#x200B;**[!UICONTROL Install]**。

      您也可以使用[AEM Forms版本](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)文章中所列的直接連結下載套件。

      >[!NOTE]
      >
      >安裝軟體包後，系統會提示您重新啟動AEM實例。 **不要立即停止伺服器。** 在停止AEM Forms伺服器之前，請等到ServiceEvent REGISTERED和ServiceEvent UNREGISTERED消息停止顯示在 &lt;crx-repository>/error.log檔案中，並且日誌是穩定的。另請注意，一些軟體包可以保持安裝狀態。 您可以安全地忽略這些包的狀態。

   1. 停止實AEM例並刪除以下檔案：

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. 啟動AEM實例。


1. 執行安裝後活動。

   * **運行遷移實用程式**

      遷移實用程式使舊版的自適應表單和通信管理資產與AEM6.4表單相容。 您可以從「軟體散發」下載AEM此公用程式。 有關配置和使用遷移實用程式的逐步資訊，請參見[遷移實用程式](/help/forms/using/migration-utility.md)。

      如果您使用[Sample將草稿和提交元件](integrate-draft-submission-database.md)與資料庫整合併從舊版升級，則在執行升級後運行以下SQL查詢：

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(如果僅從AEM6.2Forms或舊版升級)重新配置Adobe Sign**

      如果您在舊版AEM Forms中設定了Adobe Sign，請從AEM Cloud服務重新設定Adobe Sign。 如需詳細資訊，請參閱[將Adobe Sign與AEM Forms整合。](/help/forms/using/adobe-sign-integration-adaptive-forms.md)

   * **(如果僅從AEM6.2Forms或舊版升級)重新設定分析和報表**

      在AEMForms6.4中，不提供來源的流量變數和曝光的成功事件。 因此，從6.2Forms或舊AEM版升級時，AEM Forms停止傳送資料至Adobe Analytics伺服器，因此無法使用最適化表單的分析報表。 此外，AEM6.4Forms推出表單分析和成功事件版本的流量變數，用於欄位逗留時間。 因此，請為您的AEM Forms環境重新配置分析和報告。 如需詳細步驟，請參閱[設定分析和報表](/help/forms/using/configure-analytics-forms-documents.md)。

1. 驗證伺服器是否升級成功，所有資料也成功遷移，並且可以正常運行。

   * **驗證綁定的狀態：確** 保所有綁定都處於活動狀態。
   * **驗證複製和反向複製：** 發佈、填寫和提交一些遷移的表單。也驗證已提交的資料。
   * **驗證管理員和開發人員使用者介** 面的存取權：從AEM管理員帳戶登入例項，並確認您擁有下列URL的存取權：

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   在AEMForms6.4中，crx-repository的結構已經更改。 升級至AEM6.4表格後，請使用重新建立的變更路徑進行自訂。 有關更改路徑的完整清單，請參見[Forms6.4&lt;a1/AEM>中的資料庫重組。](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)

## AEM  6.0FormsAEM和6.1FormsAEM > 6.4Forms{#upgrade-aem-forms-60-61-to-64}

不提供從&#x200B;**AEM 6.0Forms**&#x200B;和&#x200B;**AEM 6.1Forms**&#x200B;到AEM6.4Forms的直接升級路徑。 執行中級[升級至AEM6.2Forms](/help/forms/using/upgrade.md)或[升級至AEM6.3Forms](/help/forms/using/upgrade.md)，然後從AEM6.2Forms或AEM6.3Forms升級至6.4AEMForms。
