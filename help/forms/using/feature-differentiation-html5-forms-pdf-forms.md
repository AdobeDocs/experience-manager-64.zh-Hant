---
title: HTML5表單和PDF forms之間的功能差異
seo-title: Feature differentiation between HTML5 forms and PDF forms
description: HTML5表單和PDF forms支援的功能
seo-description: Feature supported in HTML5 forms and PDF forms
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
feature: Mobile Forms
exl-id: 2b82e68c-ec11-417d-a8e2-769da9b35140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 3%

---

# HTML5表單和PDF forms之間的功能差異 {#feature-differentiation-between-html-forms-and-pdf-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

下表指定了為HTML5表單和PDF forms提供的功能支援：

<table> 
 <tbody>
  <tr>
   <th>功能</th> 
   <th>HTML5 Forms</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>條碼<br /> </td> 
   <td>在用戶介面級別不可用。 </td> 
   <td>支援</td> 
  </tr>
  <tr>
   <td>簽名欄位<br /> </td> 
   <td><strong>數位簽名</strong> 不支援，但是新 <strong>手寫簽名</strong> 會為紙張（如簽名）新增欄位。 你可以用 <strong>手寫簽名</strong> 欄位。 簽名將作為影像保存在窗體上。 您可以在 <strong>手寫簽名</strong> 欄位。</td> 
   <td>簽名欄位可用於 <strong>數位簽名</strong>.</td> 
  </tr>
  <tr>
   <td>資料合併</td> 
   <td>支援</td> 
   <td>支援</td> 
  </tr>
  <tr>
   <td>影像</td> 
   <td>資料URI配置用於顯示影像。 所有新版瀏覽器都支援此配置，但每個瀏覽器支援的影像格式範圍有所不同。<br /> </td> 
   <td>支援.gif、.png、.jpeg、.bmp和.tiff格式。</td> 
  </tr>
  <tr>
   <td>分頁<br /> </td> 
   <td><p>HTML5表單會分成面板和方塊，以提供與PDF forms類似的外觀。 頁面大小會動態計算。 如果HTML5表單中的頁面所有內容都被刪除或標籤為隱藏，則空白頁面會隱藏，空白頁面上方和下方的頁面之間不會顯示空白字元（空白字元）。</p> <p>如果資料合併或指令碼將內容新增至頁面，則頁面的長度會擴展以容納新新增的內容。 表單中不會新增任何頁面以容納新新增的內容。 </p> <p><strong>注意：</strong> 刪除或標籤HTML5表單中的所有頁面內容後，空白頁面（空白字元）在第1頁和第2頁之間仍可見，但在任何其他頁面之間則不可見。</p> </td> 
   <td>PDF中的分頁取決於合併的資料內容或使用者內容，而頁面計數會據此增加/減少。</td> 
  </tr>
  <tr>
   <td>頁首/頁尾 </td> 
   <td>支援. <br /> <br /> 由於HTML5行動表單不支援分頁，因此頁首和頁尾只會顯示一次。 不過，您可以在版面中設定它們，以在行動表單預覽的多個位置顯示。<br /> </td> 
   <td>支援。</td> 
  </tr>
  <tr>
   <td>自訂介面工具集</td> 
   <td>您可以自訂Widget，以增強行動裝置上的使用者體驗。<br /> </td> 
   <td>所有小部件都被鎖定，無法插入自定義小部件。<br /> </td> 
  </tr>
  <tr>
   <td>XFA指令碼API</td> 
   <td>支援最常使用的XFA指令碼結構。 有關支援的構造的詳細資訊，請參見 <a href="/help/forms/using/scripting-support.md">指令碼支援</a>.</td> 
   <td>支援所有XFA指令碼結構。</td> 
  </tr>
  <tr>
   <td>Acrobat指令碼API </td> 
   <td>HTML5表單支援最常使用的API。 如需詳細資訊，請參閱 <a href="/help/forms/using/scripting-support.md">指令碼支援</a>.</td> 
   <td>如果PDF檔案是在Acrobat或Reader內開啟，則也支援Acrobat提供的所有指令碼API。</td> 
  </tr>
  <tr>
   <td>支援由右至左語言 </td> 
   <td>支援</td> 
   <td>支援</td> 
  </tr>
 </tbody>
</table>

請遵循最佳實務，為HTML5轉譯啟用表單範本，並確保HTML5表單和XFA型PDF的行為與外觀一致。 如需最佳實務的詳細清單，請參閱 [設計HTML5表單的最佳實務。](/help/forms/using/best-practices-for-html5-forms.md)
