---
title: 在AEM Forms中建立鎖定的體驗
seo-title: 在AEM Forms中建立鎖定的體驗
description: '使用AEM Forms中的Target為目標客戶建立自訂體驗。 '
seo-description: '使用AEM Forms中的Target為目標客戶建立自訂體驗。 '
uuid: 174b6054-8fe3-4ab2-8afd-435e5dff9044
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: 6cf54a08-d429-4a58-8429-a1cb784448d1
exl-id: 5a10ffea-2c69-4902-9754-399bd2e125f1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---

# 在AEM Forms {#create-targeted-experiences-in-aem-forms}中建立目標體驗

## 將Adobe Target與AEM Forms整合{#integrate-adobe-target-with-aem-forms}

與AEM整合的Adobe Target可讓您建立針對目標對象自訂的體驗。 透過Adobe Target，您可以建立A/B測試、測量使用者回應，以及為目標使用者產生自訂的Web內容。 您可以整合Adobe Target與AEM Forms，以鎖定最適化表單和互動式通訊的影像元件。

在AEM中設定Adobe Target以搭配最適化表單和互動式通訊使用，請參閱在AEM](/help/sites-administering/target.md)中建立Target設定和[新增架構](/help/sites-administering/target.md)。[

>[!NOTE]
>
>使用主機名稱或IP位址轉譯最適化表單或互動式通訊時，定位即可運作。 使用localhost呈現最適化表單或互動式通訊時失敗。

## 建立Target活動{#creating-a-target-activity}

1. 點選&#x200B;**Adobe Experience Manager >個人化>活動**。

   `https://<hostname>:<port>/libs/cq/personalization/touch-ui/content/v2/activities.html`

1. 在「活動」頁面中，點選&#x200B;**「建立>建立品牌」**。
1. 系統會要求您選擇範本並輸入屬性。

   選取範本，點選「 **Next」。** 在「屬性」區段中輸入品牌標題，然後點選「建 **立」。**
您的品牌現在會列在「活動」頁面中。

1. 在「活動」頁面中點選您的品牌。
1. 在品牌的主版區域中，點選&#x200B;**Create** > **Create Activity**。

   建立活動時，您需指定其詳細資料、目標及設定。

   「詳細資料」區段包含名稱、定位引擎和目標。 選取Adobe Target作為定位引擎時，您會啟用Target雲端設定選項。 選擇您的Target雲端設定，選擇「活動類型」，提供活動的目標，然後點選&#x200B;**Next**。 互動式通訊僅支援體驗鎖定目標活動類型。

   「目標」區段可讓您新增受眾體驗並命名。 按一下「**新增體驗**」以啟用「選取對象&#x200B;**」和「**&#x200B;命名體驗&#x200B;**」選項。**&#x200B;點選&#x200B;**選取對象**&#x200B;以查看對象及其來源的清單。 從「對象名稱」清單中選取對象。 點選&#x200B;**新增體驗**&#x200B;以命名體驗，然後點選&#x200B;**下一步**。

   「目標與設定」區段可讓您排程活動並排定活動的優先順序。 設定活動、目標量度、其他量度的開始日期、結束日期和優先順序，然後點選&#x200B;**Save**。

   活動現在會列在您的品牌頁面中。

   >[!NOTE]
   >
   >您可以忽略「您的活動已儲存，但未同步至Target」錯誤。 原因：如果在儲存活動時遇到下列體驗沒有選件」。

1. 若要啟用target，請編輯.jsp檔案以包含您的最適化表單範本所使用的用戶端程式庫。

   例如，在現成可用的實作中，按一下「**工具** > **CRXDE Lite**」。

   在CRXDE Lite地址欄中，鍵入/libs/fd/af/components/page/base/head.jsp以編輯head.jsp檔案。

   此實施使用simpleEnrollment模板。 在此實施中，修改head.jsp檔案以包括以下客戶端庫：

   `<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>`

   `<cq:include path="clientcontext_optimized" resourceType="/libs/cq/personalization/components/clientcontext_optimized"/>`

   `<cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>`

1. 若要啟用最適化表單的目標架構，請導覽至您的表單或互動式通訊，然後在編輯模式中開啟。

   若要在編輯模式下開啟表單或互動式通訊，請點選&#x200B;**選取**，然後點選&#x200B;**開啟**。

   或者，當您將指針移到表單或互動式通信表徵圖上時，不選擇該表單或互動式通信表徵圖時，將顯示四個按鈕。 您可以點選出現的&#x200B;**Edit**&#x200B;按鈕，以在編輯模式中開啟表單。

1. 在頁面工具列中，點選&#x200B;**頁面資訊** ![theme-options](assets/theme-options.png) > **開啟屬性**。
1. 在「一般資訊」頁簽中，選擇&#x200B;**Adobe Target**&#x200B;欄位的配置。 點選&#x200B;**儲存並關閉**。

## 將建立的活動套用至最適化表單影像或互動式通訊影像{#applying-created-activity-to-an-adaptive-form-image-or-an-interactive-communication-image}

1. 開啟最適化表單和互動式通訊以進行編輯。 如果您要開啟互動式通訊，請開啟Web頻道。

1. 在互動式通訊或最適化表單的製作模式中，新增要鎖定的影像。

   >[!NOTE]
   >
   >AEM Forms僅支援鎖定影像元件。 請確定托管影像元件的面板不包含任何其他元件，且面板的欄數設為1。

1. 從&#x200B;**Edit**&#x200B;切換至&#x200B;**Targeting**&#x200B;模式。 切換模式的選項靠近右上角。
1. 選取&#x200B;**BRAND**，選取&#x200B;**ACTIVITY**，然後點選&#x200B;**開始鎖定目標**。 「**對象**」功能表會顯示在編輯器的右側。

   ![定位功能表](assets/targeting-menu.png)

1. 從&#x200B;**「對象」**&#x200B;功能表選取對象，然後點選要鎖定的影像。 畫面隨即顯示。 在功能表中，點選&#x200B;**Target**。 點選影像，然後點選&#x200B;**設定**。 在「屬性」視窗中，選取要針對所選對象顯示的影像。 對所有對象重複此步驟。 互動式通訊或最適化表單中的影像已啟用體驗鎖定目標。

## 檢查已建立的活動是否與Target伺服器{#check-if-the-created-activity-syncs-with-the-target-server}同步

用於鎖定目標的活動會與Target伺服器同步。 若要檢查活動是否與目標伺服器同步，請在品牌頁面中檢查活動的狀態。

確認活動狀態為同步。

## 驗證Target行為{#validate-target-behavior}

驗證Target行為：

* 在製作模式中搭配`wcmmode preview`使用定位
* 在發佈模式中搭配`wcmmode preview`和`wcmmode disabled`使用定位

## 監視影像元件{#monitor-targeting-for-the-image-component}的目標定位

若要監視表單上影像元件的目標定位，請發佈影像、活動和最適化表單。

## 未結問題{#open-issues}

可見性運算式、針對最適化表單上的目標影像設定焦點失敗。
