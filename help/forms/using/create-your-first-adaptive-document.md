---
title: 不要發佈：建立您的第一份最適化檔案
seo-title: 不要發佈：建立您的第一份最適化檔案
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# 不要發佈：建立您的第一份最適化檔案 {#do-not-publish-create-your-first-adaptive-document}

## 使用案例 {#use-case}

We Finance是金融服務領域的領先組織，提供全面且個人化的財務解決方案，以符合不同客戶個人檔案的需求。

其客戶的汽車保險單即將到期，他們會寄送提醒給她，此提醒是互動式的，內含續約報價的PDF。 此通訊內容也包含其他資訊，例如忠誠獎勵和折扣優惠。

入口網站會在Adobe AEM上執行。 網頁和列印歡迎頻道輸出是使用Adaptive Document的多頻道功能建立。

在本教學課程的結尾，您將會有類似下列的最適化檔案：
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf) [ ad-2建 ![立第](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)一個最適化檔案教學課程分為幾個步驟。 每個步驟本身都是完整的文章。

<table> 
 <tbody>
  <tr>
   <th>您將學習</th> 
   <th>
    <ul> 
     <li>建立最適化檔案和表單資料模型。</li> 
     <li>建立適應性檔案的範本和主題。</li> 
     <li>使用規則編輯器建立業務規則。<br /> </li> 
     <li>發佈最適化檔案。 <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>先決條件</td> 
   <td>
    <ul> 
     <li>設定AEM作者例項。 </li> 
     <li>安裝AEM Forms附加元件。 如需詳細資訊，請參 <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">閱「安裝及設定AEM表單」</a>。</li> 
     <li>從資料庫提供程式獲取JDBC資料庫驅動程式（JAR檔案）。 教程中的示例基於MySQL資料庫，並使用Oracle的MySQL JDBC資料庫驅動程式。 </li> 
     <li>設定包含客戶資料的資料庫。 資料庫是建立自適應文檔的必要條件。 本教學課程使用資料庫來顯示AEM Forms的表單資料模型和永續性功能。 </li> 
     <li>建立／匯入並啟 <a href="/help/forms/using/web-channel-print-channel.md">用列印和網頁頻道的範本</a>。</li> 
     <li>請確定您有 <a href="/help/forms/using/document-fragments.md">基於FDM的Document片段</a>。</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Step 1: Create Form Data Model {#step-create-form-data-model}

表單資料模型可讓自適應檔案連接至不同的資料來源。 例如，AEM使用者設定檔、REST風格的web services、SOAP架構的web services、OData服務和關係式資料庫。 表單資料模型是連接資料來源中可用之商業實體和服務的統一資料表示模式。 您可以將表單資料模型與最適化檔案搭配使用，以擷取連線資料來源的資料。 如需表單資料模型的詳細資訊，請參閱「 [AEM Forms資料整合」](/help/forms/using/data-integration.md)。

目標：

* 將資料庫實例(Microsoft Dynamics)配置為資料源
* 使用Microsoft Dynamics做為資料來源建立表單資料模型
* 新增資料模型物件以建立資料模型
* 為表單資料模型配置讀寫服務
* 測試表單資料模型及已設定的服務與測試資料

## 步驟2: 建立最適化檔案 {#step-create-an-adaptive-document}

客戶通訊部門集中管理安全、個人化和互動式通訊的建立、匯整和傳遞，例如商業通訊、信件、檔案、陳述、利益通知、財富管理招股說明書、行銷郵件、帳單和歡迎套件。

使用可調式檔案，您就可以建立吸引人、回應速度快、動態且具適應性的客戶溝通內容。 AEM Forms提供拖放式WYSIWYG編輯器，以建立最適化檔案。

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

目標：

* 根據表單資料模型建立最適化檔案的列印和網頁輸出。
* 最適化表單的版面欄位，以向客戶顯示資訊
* 建立規則，以擷取並顯示從表單資料模型到最適化檔案的資訊。

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## 步驟3: 將規則套用至最適化檔案欄位（僅限Web頻道） {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

最適化檔案提供編輯器，可編寫最適化檔案物件的規則。 這些規則會根據預設條件和使用者在檔案上的動作來定義要觸發檔案物件的動作。 它可協助確保在網頁版的最適化檔案中，提供精確性並加速使用者體驗。 有關自適應文檔規則和規則編輯器的詳細資訊，請參 [閱規則編輯器](/help/forms/using/rule-editor.md)。

目標：

* 建立規則並套用至最適化檔案的Web頻道欄位
* 使用規則在Web頻道中觸發檔案資料模型服務

## 步驟4: 設定最適化檔案的樣式（僅限網頁頻道） {#step-style-the-adaptive-document-web-channel-only}

最適化檔案提供編輯器，以建立最適化檔案的主題和行內樣式。 主題包含元件和面板的樣式詳細資訊，您可以在不同檔案的網頁頻道上重複使用主題。 樣式包括背景顏色、狀態顏色、透明度、對齊方式和大小等屬性。 當您將主題套用至檔案時，指定的樣式會反映在檔案的對應元件上。 如需詳細資訊，請參 [閱主題](/help/forms/using/themes.md)。

目標：

* 建立最適化檔案網頁頻道的主題
* 將主題套用至最適化檔案Web頻道
* 驗證在行動裝置和桌上型電腦上的最適化檔案網路頻道外觀

## 步驟5: 發佈最適化檔案 {#step-publish-the-adaptive-document}

建立完最適化文檔後，您需要將其發佈，以便在發佈實例上可用，在發佈實例中，代理可以使用最適化文檔建立基於該文檔的通信實例。

若要發佈最適化檔案，檔案作者必須擁有必要的權限。
