---
title: 不發佈建立您的第一個最適化檔案
seo-title: DO NOT PUBLISH Create your first adaptive document
description: 不發佈
seo-description: DO NOT PUBLISH
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 1%

---


# 不發佈建立您的第一個最適化檔案 {#do-not-publish-create-your-first-adaptive-document}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 使用案例 {#use-case}

We Finance是金融服務領域的領先組織，提供全面且個人化的金融解決方案，以符合不同客戶設定檔的需求。

客戶的車險保單之一即將到期，他們將向她發送一個提醒，該提醒是互動式的，包括一個PDF，並帶有續訂報價。 該通信還包括其他資訊，例如忠誠獎勵和折扣優惠。

入口網站會在AdobeAEM上執行。 Web和打印歡迎通道輸出是使用自適應文檔的多通道功能建立的。

在本教學課程結束時，您會有類似下列的適用性檔案：
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)建立第一個最適化檔案教學課程分為幾個步驟。 每個步驟本身就是完整的文章。

<table> 
 <tbody>
  <tr>
   <th>你會學到</th> 
   <th>
    <ul> 
     <li>建立最適化檔案和表單資料模型。</li> 
     <li>建立最適化文檔的模板和主題。</li> 
     <li>使用規則編輯器建立業務規則。<br /> </li> 
     <li>發佈最適化檔案。 <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>必備條件</td> 
   <td>
    <ul> 
     <li>設定AEM製作例項。 </li> 
     <li>安裝 AEM Forms 附加元件. 如需詳細資訊，請參閱 <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">安裝及設定AEM Forms</a>.</li> 
     <li>從資料庫提供程式獲取JDBC資料庫驅動程式（JAR檔案）。 本教程中的示例基於MySQL資料庫，並使用Oracle的MySQL JDBC資料庫驅動程式。 </li> 
     <li>設定包含客戶資料的資料庫。 資料庫是建立最適化文檔的必要條件。 本教學課程使用資料庫來顯示表單資料模型和AEM Forms的持續性功能。 </li> 
     <li>建立/匯入並啟用 <a href="/help/forms/using/web-channel-print-channel.md">用於打印和Web通道的模板</a>.</li> 
     <li>確定您擁有 <a href="/help/forms/using/document-fragments.md">根據FDM記錄片段</a>.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## 步驟1:建立表單資料模型 {#step-create-form-data-model}

表單資料模型可將最適化檔案連結至不同的資料來源。 例如，AEM用戶配置檔案、RESTful Web服務、基於SOAP的Web服務、OData服務和關係資料庫。 表單資料模型是業務實體和服務在連接資料源中提供的統一資料表示模式。 您可以使用具有最適化檔案的表單資料模型，從連線的資料來源擷取資料。 如需表單資料模型的詳細資訊，請參閱 [AEM Forms資料整合](/help/forms/using/data-integration.md).

目標：

* 將資料庫例項(Microsoft Dynamics)設定為資料來源
* 使用Microsoft Dynamics作為資料來源建立表單資料模型
* 添加資料模型對象以形成資料模型
* 為表單資料模型配置讀寫服務
* 測試表單資料模型和已配置的服務（含測試資料）

## 步驟2:建立最適化檔案 {#step-create-an-adaptive-document}

「客戶通訊」可集中處理及管理安全、個人化及互動式通信的建立、集合及傳遞，例如商業信函、信函、檔案、對帳單、利益通知、財富管理說明書、行銷郵件、帳單及歡迎套件。

使用最適化檔案，您可以建立吸引人、回應式、動態且最適化的客戶通訊。 AEM Forms提供拖放式WYSIWYG編輯器，以建立最適化檔案。

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

目標：

* 根據表單資料模型建立最適化檔案的列印和網頁輸出。
* 最適化表單的版面欄位，以向客戶顯示資訊
* 建立規則，以從表單資料模型擷取和顯示資訊至最適化檔案。

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## 步驟3:將規則套用至最適化檔案欄位（僅限Web通道） {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

適用性檔案提供編輯器，可編寫適用性檔案物件的規則。 這些規則根據文檔上的預設條件和用戶操作定義要在文檔對象上觸發的操作。 這有助於確保準確性，並加快適用性檔案網頁版的使用者體驗。 如需適用性檔案規則和規則編輯器的詳細資訊，請參閱 [規則編輯器](/help/forms/using/rule-editor.md).

目標：

* 建立規則並套用至最適化檔案的Web通道欄位
* 使用規則觸發Web通道中的文檔資料模型服務

## 步驟4:設定最適化檔案的樣式（僅限Web通道） {#step-style-the-adaptive-document-web-channel-only}

最適化檔案提供編輯器，用於建立最適化檔案的主題和線上樣式。 主題包含元件和面板的樣式詳細資訊，您可以在不同檔案的網路頻道上重複使用主題。 樣式包括背景顏色、狀態顏色、透明度、對齊方式和大小等屬性。 將主題應用於文檔時，指定樣式會反映在文檔的相應元件上。 如需詳細資訊，請參閱 [主題](/help/forms/using/themes.md).

目標：

* 建立最適化檔案Web頻道的主題
* 將主題套用至最適化檔案Web頻道
* 驗證行動裝置和桌上型電腦上最適化檔案Web通道的外觀

## 步驟5:發佈最適化檔案 {#step-publish-the-adaptive-document}

建立完最適化檔案後，您需要將其發佈，以便可供發佈例項使用，讓代理可在此發佈例項中使用最適化檔案，以便根據該檔案建立通訊例項。

若要發佈最適化檔案，檔案作者必須擁有必要的權限。
