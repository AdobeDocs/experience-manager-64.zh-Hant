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
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 8%

---

# 在OSGi上升級至AEM 6.4 Forms {#upgrade-to-aem-forms-osgi}

根據您的環境，使用下列其中一個升級路徑。

## AEM 6.2 Forms或AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

您可以從AEM 6.2 Forms或AEM 6.3 Forms直接升級至AEM 6.4 Forms。 請執行下列動作：

1. 將現有AEM執行個體升級至AEM 6.4。步驟如下：

   1. 安裝AEM 6.2 Forms或AEM 6.3 Forms的最新Service Pack和修補程式。 如需詳細資訊，請參閱：

      * [AEM 6.2 發行說明](https://helpx.adobe.com/tw/experience-manager/6-2/release-notes.html)
      * [AEM 6.3 發行說明](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html)
      * [AEM維護中心](https://helpx.adobe.com/tw/experience-manager/aem-releases-updates.html)
   1. 準備源實例以進行升級。 如需詳細步驟，請參閱 [升級至AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. 下載 [AEM 6.4快速入門](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **（僅基於Unix/Linux的安裝）** 如果您使用UNIX或Linux作為基礎作業系統，請開啟「終端機」窗口，導航至包含crx-quickstart的資料夾，然後運行以下命令：

      `chmod -R 755 ../crx-quickstart`

   1. 將AEM執行個體升級至AEM 6.3。如需逐步指示，請參閱 [升級至AEM 6.4](/help/sites-deploying/upgrade.md).

      在繼續後續步驟之前，請等待ServiceEvent REGISTERED和ServiceEvent UNEGRESTED消息停止顯示在 &lt;crx-repository>/error.log檔案。

      >[!NOTE]
      >
      >伺服器啟動並執行後，一些AEM Forms套件組合會維持安裝狀態。 每個安裝的套件組合數量可能有所不同。 您可以安全地忽略這些包的狀態。 套件組合列於 `https://[server]:[port]/system/console/`.


1. 安裝AEM Forms附加元件套件。 步驟如下：

   1. 開啟 [Software Distribution](https://experience.adobe.com/downloads)。您需要 Adobe ID 才能登入 Software Distribution。
   1. 點一下頁首功能表中的 **[!UICONTROL Adobe Experience Manager]**。
   1. 在 **[!UICONTROL 篩選器]** 小節：
      1. 選擇 **[!UICONTROL Forms]** 從 **[!UICONTROL 解決方案]** 下拉式清單。
      1. 選取套件的版本和類型。 您也可以使用 **[!UICONTROL 搜尋下載]** 選項來篩選結果。
   1. 點選適用於您作業系統的套件名稱，然後選取 **[!UICONTROL 接受EULA條款]**，然後點選 **[!UICONTROL 下載]**.
   1. 開啟[套件管理器](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)，然後按一下&#x200B;**[!UICONTROL 「上傳套件」]**&#x200B;即可上傳套件。
   1. 選取套件，然後按一下 **[!UICONTROL 安裝]**.

      您也可以使用下列直接連結下載套件： [AEM Forms版本](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 文章。

      >[!NOTE]
      >
      >安裝套件後，系統會提示您重新啟動AEM執行個體。 **不要立即停止伺服器。** 停止AEM Forms伺服器之前，請等到ServiceEvent REGISTERED和ServiceEvent UNECROVERD訊息停止出現在 &lt;crx-repository>/error.log檔案和日誌穩定。 另請注意，一些套件可能會保留為已安裝狀態。 您可以安全地忽略這些包的狀態。

   1. 停止AEM例項並刪除下列檔案：

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. 啟動 AEM 執行個體。


1. 執行安裝後活動。

   * **運行遷移實用程式**

      移轉公用程式讓舊版的最適化表單和通信管理資產與AEM 6.4表單相容。 您可以從AEM Software Distribution下載公用程式。 如需設定及使用移轉公用程式的逐步資訊，請參閱 [遷移實用程式](/help/forms/using/migration-utility.md).

      如果您使用 [整合草稿和提交元件的範例](integrate-draft-submission-database.md) 使用資料庫並從舊版升級，然後在執行升級後運行以下SQL查詢：

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

   * **(如果僅從AEM 6.2 Forms或舊版升級)重新設定Acrobat Sign**

      如果您在舊版AEM Forms中已設定Acrobat Sign，請從AEM雲端服務重新設定Acrobat Sign。 如需詳細資訊，請參閱 [整合Acrobat Sign與AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(如果僅從AEM 6.2 Forms或舊版升級)重新設定分析和報表**

      在AEM 6.4 Forms中，無法使用來源的流量變數和曝光的成功事件。 因此，當您從AEM 6.2 Forms或舊版升級時，AEM Forms會停止傳送資料至Adobe Analytics伺服器，且不提供適用性表單的分析報表。 此外，AEM 6.4 Forms也導入表單分析版本的流量變數，以及欄位逗留時間量的成功事件。 因此，請針對您的AEM Forms環境重新設定分析和報表。 如需詳細步驟，請參閱 [設定分析和報表](/help/forms/using/configure-analytics-forms-documents.md).

1. 驗證伺服器是否升級成功，所有資料是否也成功遷移，並且它可以正常運行。

   * **驗證包的狀態：** 請確定所有套件都處於作用中狀態。
   * **驗證複製和反向複製：** 發佈、填寫和提交一些移轉的表單。 也驗證提交的資料。
   * **驗證對管理員和開發人員用戶介面的訪問：** 從管理員帳戶登入AEM例項，並確認您擁有下列URL的存取權：

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   在AEM 6.4 Forms中，crx-repository的結構已變更。 升級至AEM 6.4表單後，請使用您重新建立的已變更路徑進行自訂。 如需已變更路徑的完整清單，請參閱 [Forms 6.4中的存放庫重新調整架構](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms和AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

直接升級路徑 **AEM 6.0 Forms** 和 **AEM 6.1 Forms** 無法使用AEM 6.4 Forms。 執行中間 [升級至AEM 6.2 Forms](/help/forms/using/upgrade.md) 或 [升級至AEM 6.3 Forms](/help/forms/using/upgrade.md) 然後從AEM 6.2 Forms或AEM 6.3 Forms升級至AEM 6.4 Forms。
