---
title: 透過DTM啟用資產見解
description: 瞭解如何使用Adobe動態標籤管理(DTM)來啟用資產分析。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 0%

---


# 透過DTM {#enabling-asset-insights-through-dtm}啟用資產分析

Adobe動態標籤管理是可啟動數位行銷工具的工具。 酒店免費提供給Adobe Analytics客戶。 您可以自訂追蹤代碼，讓協力廠商CMS解決方案使用「資產前瞻分析」，或使用DTM插入「資產前瞻分析」標籤。 只有影像才支援並提供見解。

>[!CAUTION]
>
>AdobeDTM已過時，已改用Adobe Experience Platform Launch，很快即將到達[壽命結束](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f)。 Adobe建議您[使用Launch獲取資產見解](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html)。

執行下列步驟，透過DTM啟用資產分析：

1. 點選／按一AEM下標誌，並前往&#x200B;**[!UICONTROL 工具>資產>前瞻分析設定]**。
1. [使用AEMDTMCloud Service配置實例](../sites-administering/dtm.md)

   當您登入[https://dtm.adobe.com](https://dtm.adobe.com/)並從「設定檔」圖示造訪&#x200B;**[!UICONTROL 帳戶設定]**&#x200B;時，API Token應該可供使用。 從資產洞察的角度來看，此步驟不是必要步驟，因為AEM Sites與資產洞察的整合仍在進行中。

1. 登入[https://dtm.adobe.com](https://dtm.adobe.com/)，並視情況選擇公司。
1. 建立／開啟現有Web屬性

   * 選擇&#x200B;**[!UICONTROL Web屬性]**&#x200B;標籤，然後點選／按一下&#x200B;**[!UICONTROL 添加屬性]**。
   * 視需要更新欄位，點選／按一下「建立屬性&#x200B;**[!UICONTROL 」（請參閱[documentation](https://helpx.adobe.com/experience-manager/using/dtm.html)）。]**

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. 在&#x200B;**[!UICONTROL Rules]**&#x200B;標籤中，從導覽窗格中選擇&#x200B;**[!UICONTROL Page Load Rules]**，然後點選／按一下「建立新規則&#x200B;]**」。**[!UICONTROL 

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. 展開&#x200B;**[!UICONTROL Javascript /第三方標籤]**。 然後點選／按一下「循序HTML」標籤中的「新增指令碼」(**[!UICONTROL Add New Script]**)，以開啟「指令碼」對話方塊。****

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. 點選／按一AEM下標誌，並前往&#x200B;**[!UICONTROL 工具>資產]**。
1. 點選／按一下&#x200B;**[!UICONTROL 前瞻分析頁面追蹤器]**，複製追蹤器程式碼，然後貼到您在步驟6中開啟的指令碼對話方塊中。 儲存變更。

   >[!NOTE]
   >
   >* `AppMeasurement.js` 已移除。預計可透過DTM的Adobe Analytics工具取得。
   >* 將刪除對`assetAnalytics.dispatcher.init()`的調用。 當DTM的Adobe Analytics工具完成載入時，預期會呼叫此函式。
   >* 視資產前瞻分析頁面追蹤器的裝載位置(例如AEMCDN等)而定，指令碼來源的來源可能需要變更。
   >* 對於AEM托管的頁面追蹤器，來源應使用調度程式實例的主機名指向發佈實例。


1. 開啟[https://dtm.adobe.com](https://dtm.adobe.com)。 按一下Web屬性中的「概述」，然後按一下「新增工具」或開啟現有的Adobe Analytics工具。 建立工具時，可將「配置方法」(Configuration Method)設定為「自動」(Automatic)。

   ![chlimage_1-196](assets/chlimage_1-196.png)

   視需要選取「測試／生產」報表套裝。

1. 展開「庫管理」**[!UICONTROL ，並確保****的「載入庫」設定為「頁首」]**。]****[!UICONTROL 

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. 展開&#x200B;**[!UICONTROL 自訂頁面程式碼]**，然後按一下或點選&#x200B;**[!UICONTROL 開啟編輯器]**。

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. 在視窗中貼上下列程式碼：

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

   * DTM中的頁面載入規則僅包含pagetracker.js代碼。 任何`assetAnalytics`欄位皆視為預設值的覆寫。 預設不需要這些字元。
   * 在確定`_satellite.getToolsByType('sc')[0].getS()`已初始化且`assetAnalytics,dispatcher.init`可用後，代碼會呼叫`assetAnalytics.dispatcher.init()`。 因此，您可以略過在步驟11中加入。
   * 如前瞻分析頁面追蹤器程式碼（**[!UICONTROL 工具>資產>前瞻分析頁面追蹤器]**）中的注釋所示，當頁面追蹤器未建立`AppMeasurement`物件時，前三個引數（RSID、追蹤伺服器和訪客命名空間）並不相關。 會改為傳遞空字串以反白標示此值。

      其餘引數對應於「前瞻分析設定」頁面（**[!UICONTROL 工具>資產>前瞻分析設定]**）中設定的值。

   * AppMeasurement物件是透過查詢`satelliteLib`所有可用的SiteCatalyst引擎來擷取。 如果已設定多個標籤，請適當變更陣列選擇器的索引。 陣列中的條目按DTM介面中可用的SiteCatalyst工具排序。

1. 儲存並關閉「程式碼編輯器」視窗，然後儲存「工具」設定中的變更。
1. 在&#x200B;**[!UICONTROL Approvals]**&#x200B;標籤中，批准兩個待審批。 DTM標籤已準備好可插入網頁。 如需如何在網頁中插入DTM標籤的詳細資訊，請參閱[將DTM整合在自訂頁面範本中](https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template/)。
