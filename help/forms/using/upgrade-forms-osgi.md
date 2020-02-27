---
title: 升級至AEM 6.4 Forms
seo-title: 升級至AEM 6.4 Forms
description: '您可以從AEM 6.1 Forms、AEM 6.2 Forms和LiveCycle ES4 SP1直接升級至AEM 6.3 Forms。 '
seo-description: '您可以從AEM 6.1 Forms、AEM 6.2 Forms和LiveCycle ES4 SP1直接升級至AEM 6.3 Forms。 '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: d2657bc364b7a814fac9228afdec60f96faaf175

---


# 升級至OSGi上的AEM 6.4 Forms {#upgrade-to-aem-forms-osgi}

請根據您的環境，使用下列升級途徑之一。

## AEM 6.2 Forms或AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

您可以直接從AEM 6.2 Forms或AEM 6.3 Forms升級至AEM 6.4 Forms。 執行下列動作：

1. 將現有的AEM例項升級至AEM 6.4。步驟如下：

   1. 安裝AEM 6.2 Forms或AEM 6.3 Forms的最新Service Pack和修補程式。 如需詳細資訊，請參閱：

      * [AEM 6.2版本注意事項](https://helpx.adobe.com/experience-manager/6-2/release-notes.html)
      * [AEM 6.3版本注意事項](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
      * [AEM維護中樞](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)
   1. 準備升級的源實例。 如需詳細步驟，請 [參閱「升級至AEM 6.4」](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance)。
   1. 下載 [AEM 6.4 quickStart](/help/sites-deploying/deploy.md#getting%20the%20software)。
   1. **（僅限基於Unix/Linux的安裝）** ，如果您使用UNIX或Linux作為基礎作業系統，請開啟終端窗口，導航到包含crx-quickstart的資料夾，然後運行以下命令：

      `chmod -R 755 ../crx-quickstart`

   1. 將您的AEM實例升級至AEM 6.3。如需逐步指示，請參 [閱升級至AEM 6.4](/help/sites-deploying/upgrade.md)。

      在繼續後續步驟之前，請等待&lt;crx-repository>/error.log檔案中停止顯示ServiceEvent REGISTERED和ServiceEvent UNREGISTERED消息。

      >[!NOTE]
      >
      >伺服器啟動並執行後，一些AEM Forms組合會維持在安裝狀態。 每個安裝的捆綁包數量可能不同。 您可以安全地忽略這些束的狀態。 捆綁包列於 `https://[server]:[port]/system/console/`。


1. 安裝AEM Forms附加元件套件。 步驟如下：

   1. 以管理員身分登入AEM伺服器，並開啟套件共用。 套件共用的預設URL為 `https://[server]:[port]/crx/packageshare`。
   1. 在套件共用中，搜尋 **[!UICONTROL AEM 6.4 Forms附加元件套件]**，按一下適用於您作業系統的套件，然後按一下「下 **[!UICONTROL 載」]**。 閱讀並接受授權合約，然後按一下「 **[!UICONTROL 確定]**」。 下載開始。 下載後，「已下 **[!UICONTROL 載]** 」一詞會出現在套件旁。

      或者，您也可以使用 [AEM Forms版本中列出的超連結](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) ，手動下載套件。

   1. 下載完成後，按一下「已下 **[!UICONTROL 載」]**。 您被重定向到包管理器。 在包管理器中，搜索下載的包，然後按一下安 **[!UICONTROL 裝]**。

      如果您使用 [AEM Forms版本中所列的直接連結手動下載套件](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)，然後開啟AEM Package Manager，按一下「 **[!UICONTROL Upload Package]**」（上傳套件），選取已下載的套件，然後按一下「上傳」。 上載包後，按一下包名稱，然後按一下安 **[!UICONTROL 裝]**。

      >[!NOTE]
      >
      >安裝套件後，系統會提示您重新啟動AEM例項。 **不要立即停止伺服器。** 在停止AEM Forms伺服器之前，請等到ServiceEvent REGISTERED和ServiceEvent UNREGISTERED訊息停止出現在&lt;crx-repository>/error.log檔案中，且記錄檔是穩定的。 另請注意，一些軟體包可以保持安裝狀態。 您可以安全地忽略這些包的狀態。

   1. 停止AEM例項並刪除下列檔案：

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. 啟動AEM例項。


1. 執行安裝後活動。

   * **運行遷移實用程式**

      移轉公用程式可讓舊版的最適化表單和通訊管理資產與AEM 6.4表單相容。 您可以從AEM套件共用下載公用程式。 有關配置和使用遷移實用程式的逐步資訊，請參見遷移實 [用程式](/help/forms/using/migration-utility.md)。

      如果您使用 [Sample將草稿和提交元件與資料庫整合併從舊版升級](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) ，則在執行升級後運行以下SQL查詢：

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

   * **（如果僅從AEM 6.2 Forms或舊版升級）重新設定Adobe Sign**

      如果您在舊版AEM Forms中設定了Adobe Sign，請從AEM cloud服務重新設定Adobe Sign。 如需詳細資訊，請參 [閱「將Adobe Sign與AEM Forms整合」](/help/forms/using/adobe-sign-integration-adaptive-forms.md)。

   * **（如果僅從AEM 6.2 Forms或舊版升級）重新設定分析和報表**

      在AEM 6.4 Forms中，沒有來源的流量變數和曝光的成功事件。 因此，當您從AEM 6.2 Forms或舊版升級時，AEM Forms會停止傳送資料至Adobe Analytics伺服器，而且不提供最適化表單的分析報表。 此外，AEM 6.4 Forms針對表單分析和成功事件的版本，針對欄位逗留時間引入流量變數。 因此，請重新設定AEM Forms環境的分析和報表。 如需詳細步驟，請參 [閱設定分析和報表](/help/forms/using/configure-analytics-forms-documents.md)。

1. 驗證伺服器是否升級成功，所有資料也成功遷移，並且可以正常運行。

   * **** 驗證捆綁的狀態：確保所有捆綁包都處於活動狀態。
   * **** 驗證複製和反向複製：發佈、填寫及送出幾份移轉的表格。 也驗證已提交的資料。
   * **** 驗證管理員和開發人員使用者介面的存取權：從管理帳戶登入AEM例項，並確認您擁有下列URL的存取權：

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`
   >[!NOTE]
   在AEM 6.4 Forms中，crx-repository的結構已變更。 升級至AEM 6.4表單後，請使用您重新建立的自訂變更路徑。 如需變更路徑的完整清單，請參 [閱AEM 6.4中的Forms Repository Restructing](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)。

## AEM 6.0 Forms and AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

無法使用從 **AEM 6.0 Forms** 和 **** AEM 6.1 Forms直接升級至AEM 6.4 Forms的路徑。 執行 [AEM 6.2 Forms](/help/forms/using/upgrade.md) 或 [](/help/forms/using/upgrade.md) AEM 6.3 Forms的中級升級，然後從AEM 6.2 Forms或AEM 6.3 Forms升級至AEM 6.4 Forms。
