---
title: 透過DTM啟用Assets Insights
description: 了解如何使用AdobeDynamic Tag Management(DTM)來啟用Assets Insights。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 1%

---

# 透過DTM啟用Assets Insights {#enabling-asset-insights-through-dtm}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe動態Tag Management是啟用數位行銷工具的工具。 此服務免費提供給Adobe Analytics客戶。 您可以自訂追蹤代碼，讓協力廠商CMS解決方案能使用Assets Insights，或使用DTM插入Assets Insights標籤。 僅支援並提供影像見解。

>[!CAUTION]
>
>AdobeDTM已淘汰，以支援 [!DNL Adobe Experience Platform] 很快就會到 [終止服務](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). Adobe建議您 [use [!DNL Adobe Experience Platform] assets insights](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html).

執行下列步驟以透過DTM啟用Assets Insights:

1. 點選/按一下 [!DNL Experience Manager] 標誌，然後 **[!UICONTROL 工具]** > **[!UICONTROL 資產]** > **[!UICONTROL 前瞻分析設定]**.
1. [設定 [!DNL Experience Manager] 具DTMCloud Service的例項](../sites-administering/dtm.md)

   登入後，API代號應該可供使用 [https://dtm.adobe.com](https://dtm.adobe.com/) 和瀏覽 **[!UICONTROL 帳戶設定]** 中。 從資產分析的角度來看，不需要執行此步驟，因為整合 [!DNL Experience Manager Sites] 資產前瞻分析功能仍在運作中。

1. 登入 [https://dtm.adobe.com](https://dtm.adobe.com/)，並視情況選取公司。
1. 建立/開啟現有Web屬性

   * 選取 **[!UICONTROL Web屬性]** 標籤，然後點選/按一下 **[!UICONTROL 新增屬性]**.
   * 視需要更新欄位，然後點選/按一下 **[!UICONTROL 建立屬性]** (請參閱 [檔案](https://helpx.adobe.com/experience-manager/using/dtm.html))。

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. 在 **[!UICONTROL 規則]** 索引標籤，選取 **[!UICONTROL 頁面載入規則]** 從導覽窗格中，點選/按一下 **[!UICONTROL 建立新規則]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. 展開 **[!UICONTROL Javascript/第三方標籤]**. 然後點選/按一下 **[!UICONTROL 新增指令碼]** 在 **[!UICONTROL 循序HTML]** 頁簽以開啟「指令碼」對話框。

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. 點選/按一下 [!DNL Experience Manager] 標誌，然後 **[!UICONTROL 工具>資產]**.
1. 點選/按一下 **[!UICONTROL 前瞻分析頁面追蹤器]**，複製追蹤器程式碼，然後貼到您在步驟6中開啟的「指令碼」對話方塊中。 儲存變更。

   >[!NOTE]
   >
   >* `AppMeasurement.js` 已移除。 預期可透過DTM的Adobe Analytics工具取得。
   >* 呼叫 `assetAnalytics.dispatcher.init()` 已移除。 當DTM的Adobe Analytics工具完成載入時，即應呼叫函式。
   >* 視Assets Insights頁面追蹤器的托管位置(例如AEM、CDN等)而定，指令碼來源的來源可能需要變更。
   >* 對於AEM托管的頁面追蹤器，來源應使用Dispatcher例項的主機名稱指向發佈例項。


1. 開啟 [https://dtm.adobe.com](https://dtm.adobe.com). 按一下Web屬性中的「概觀」 ，然後按一下「新增工具」或開啟現有的Adobe Analytics工具。 建立工具時，可將「配置方法」設定為「自動」。

   ![chlimage_1-196](assets/chlimage_1-196.png)

   視情況選取測試/生產報表套裝。

1. 展開 **[!UICONTROL 程式庫管理]**，並確保 **[!UICONTROL 在載入程式庫]** 設為 **[!UICONTROL 頁面頂端]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. 展開 **[!UICONTROL 自訂頁面程式碼]**，然後按一下或點選 **[!UICONTROL 開啟編輯器]**.

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. 將下列程式碼貼入視窗中：

   ```java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, please include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * DTM中的頁面載入規則只包含pagetracker.js程式碼。 任何 `assetAnalytics` 欄位會視為預設值的覆寫。 預設不是必要項目。
   * 程式碼呼叫 `assetAnalytics.dispatcher.init()` 在確認 `_satellite.getToolsByType('sc')[0].getS()` 已初始化， `assetAnalytics,dispatcher.init` 的URL區段。 因此，您可以略過在步驟11中新增。
   * 如前瞻分析頁面追蹤器程式碼(**[!UICONTROL 工具>資產>前瞻分析頁面追蹤器]**)，頁面追蹤器未建立 `AppMeasurement` 物件，前三個引數（RSID、追蹤伺服器和訪客命名空間）則無關。 會傳遞空字串，以反白標示此項目。

      其餘引數則對應至「前瞻分析設定」頁面(**[!UICONTROL 工具>資產>深入分析設定]**)。

   * AppMeasurement物件是透過查詢擷取 `satelliteLib` SiteCatalyst引擎。 如果已配置多個標籤，請適當更改陣列選擇器的索引。 陣列中的項目會依DTM介面中可用的SiteCatalyst工具排序。

1. 儲存並關閉「代碼編輯器」視窗，然後在「工具」設定中儲存變更。
1. 在 **[!UICONTROL 核准]** 標籤中，批准兩個待審批。 DTM標籤已準備好插入網頁。 如需如何在網頁中插入DTM標籤的詳細資訊，請參閱封存頁面關於 [將DTM整合至自訂頁面範本](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template).
