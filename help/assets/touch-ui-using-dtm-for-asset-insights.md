---
title: 透過DTM啟用Assets Insights
description: 了解如何使用AdobeDynamic Tag Management(DTM)來啟用Assets Insights。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: 2b3a6972d703314d56d3dc711fb6a514cb1942d5
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---

# 透過DTM啟用Assets Insights {#enabling-asset-insights-through-dtm}

Adobe動態標籤管理是啟用數位行銷工具的工具。 此服務免費提供給Adobe Analytics客戶。 您可以自訂追蹤代碼，讓協力廠商CMS解決方案能使用Assets Insights，或使用DTM插入Assets Insights標籤。 僅支援並提供影像見解。

>[!CAUTION]
>
>AdobeDTM已過時，改用[!DNL Adobe Experience Platform]，很快將到達[生命週期結束](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f)。 Adobe建議您[對於資產前瞻分析](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html)使用 [!DNL Adobe Experience Platform] 。

執行下列步驟以透過DTM啟用Assets Insights:

1. 點選/按一下AEM標誌，然後前往「**[!UICONTROL 工具]** > **[!UICONTROL 資產]** > **[!UICONTROL 前瞻分析設定]**」。
1. [使用DTM設定AEM例項Cloud Service](../sites-administering/dtm.md)

   一旦您登入[https://dtm.adobe.com](https://dtm.adobe.com/)並從「設定檔」圖示造訪&#x200B;**[!UICONTROL 帳戶設定]**,API代號就應可供使用。 從Assets Insights的觀點來看，不需要執行此步驟，因為AEM Sites與Assets Insights的整合仍在進行中。

1. 登入[https://dtm.adobe.com](https://dtm.adobe.com/)，並視情況選取公司。
1. 建立/開啟現有Web屬性

   * 選擇&#x200B;**[!UICONTROL Web屬性]**&#x200B;頁簽，然後點選/按一下&#x200B;**[!UICONTROL Add Property]**。
   * 視需要更新欄位，然後點選/按一下「建立屬性&#x200B;****」（請參閱[檔案](https://helpx.adobe.com/experience-manager/using/dtm.html)）。

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. 在&#x200B;**[!UICONTROL Rules]**&#x200B;標籤中，從導航窗格中選擇&#x200B;**[!UICONTROL Page Load Rules]**，然後點選/按一下&#x200B;**[!UICONTROL Create New Rule]**。

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. 展開&#x200B;**[!UICONTROL Javascript /第三方標籤]**。 然後點選/按一下&#x200B;**[!UICONTROL 連續HTML]**&#x200B;標籤中的「新增指令碼&#x200B;]**」以開啟「指令碼」對話方塊。**[!UICONTROL 

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. 點選/按一下AEM標誌，然後前往「**[!UICONTROL 工具>資產]**」。
1. 點選/按一下&#x200B;**[!UICONTROL 前瞻分析頁面追蹤器]**，複製追蹤器程式碼，然後貼到您在步驟6中開啟的「指令碼」對話方塊中。 儲存變更。

   >[!NOTE]
   >
   >* `AppMeasurement.js` 已移除。預期可透過DTM的Adobe Analytics工具取得。
   >* 已移除對`assetAnalytics.dispatcher.init()`的呼叫。 當DTM的Adobe Analytics工具完成載入時，即應呼叫函式。
   >* 視Assets Insights頁面追蹤器的托管位置(例如AEM、CDN等)而定，指令碼來源的來源可能需要變更。
   >* 對於AEM托管的頁面追蹤器，來源應使用Dispatcher例項的主機名稱指向發佈例項。


1. 開啟[https://dtm.adobe.com](https://dtm.adobe.com)。 按一下Web屬性中的「概觀」 ，然後按一下「新增工具」或開啟現有的Adobe Analytics工具。 建立工具時，可將「配置方法」設定為「自動」。

   ![chlimage_1-196](assets/chlimage_1-196.png)

   視情況選取測試/生產報表套裝。

1. 展開&#x200B;**[!UICONTROL 程式庫管理]**，並確定&#x200B;**[!UICONTROL 在]**&#x200B;載入程式庫已設為&#x200B;**[!UICONTROL 頁面頂端]**。

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. 展開&#x200B;**[!UICONTROL 自訂頁面程式碼]**，然後按一下或點選&#x200B;**[!UICONTROL 開啟編輯器]**。

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

   * DTM中的頁面載入規則只包含pagetracker.js程式碼。 任何`assetAnalytics`欄位都被視為預設值的覆寫。 預設不是必要項目。
   * 在確定`_satellite.getToolsByType('sc')[0].getS()`已初始化且`assetAnalytics,dispatcher.init`可用後，程式碼會呼叫`assetAnalytics.dispatcher.init()`。 因此，您可以略過在步驟11中新增。
   * 如前瞻分析頁面追蹤器程式碼（**[!UICONTROL 工具>資產>前瞻分析頁面追蹤器]**）內的註解所示，當頁面追蹤器未建立`AppMeasurement`物件時，前三個引數（RSID、追蹤伺服器和訪客命名空間）則無關。 會傳遞空字串，以反白標示此項目。

      其餘引數對應至前瞻分析設定頁面（**[!UICONTROL 工具>資產>前瞻分析設定]**）中設定的項目。

   * AppMeasurement物件是透過查詢所有可用SiteCatalyst引擎的`satelliteLib`來擷取。 如果已配置多個標籤，請適當更改陣列選擇器的索引。 陣列中的項目會依DTM介面中可用的SiteCatalyst工具排序。

1. 儲存並關閉「代碼編輯器」視窗，然後在「工具」設定中儲存變更。
1. 在&#x200B;**[!UICONTROL Approvals]**&#x200B;標籤中，批准兩個待審批。 DTM標籤已準備好插入網頁。 如需如何在網頁中插入DTM標籤的詳細資訊，請參閱關於[將DTM整合至自訂頁面範本](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template)的封存頁面。
