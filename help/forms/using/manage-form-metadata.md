---
title: 管理表單中繼資料
seo-title: 管理表單中繼資料
description: 中繼資料可讓資產更輕鬆地分類和組織，並協助尋找特定資產的使用者。
seo-description: 中繼資料可讓資產更輕鬆地分類和組織，並協助尋找特定資產的使用者。
uuid: cdb5cb52-5b93-4d99-bd97-fba017406316
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 28549db2-e2f2-4a25-b0b1-785237d9d941
role: Admin
exl-id: d10bc3e9-66a6-4cb2-b484-da338259f1c8
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1995'
ht-degree: 1%

---

# 管理表單中繼資料 {#manage-form-metadata}

## 概覽  {#overview-nbsp}

中繼資料可讓資產更輕鬆地分類和組織，並協助尋找特定資產的使用者。

AEM Forms依預設會提供每個資產類型的一組已定義中繼資料。 除了預設中繼資料，您還可以新增自訂中繼資料至每個資產類型。 AEM Forms也為您提供合適的方式，讓您為表單有效地建立、管理和交換所有中繼資料。

如果您是開發人員或網站擁有者，可以自訂Forms Portal(AEM Forms的一般使用者介面)，以反映您在組織中使用的中繼資料。 如需Forms Portal的詳細資訊，請參閱[在入口網站上發佈表單的簡介](/help/forms/using/introduction-publishing-forms.md)。

## AEM Forms中的中繼資料  {#metadata-in-aem-forms-nbsp}

在AEM Forms中，與資產相關聯的中繼資料屬性清單取決於其類型。 此外，如果您新增任何自訂中繼資料屬性，則會將其新增至新增自訂中繼資料之類型的所有資產。

### 資產類型  {#asset-types-nbsp}

AEM Forms支援下列資產類型：

* 表單範本（XFA表單）
* PDF forms
* 文檔（一般PDF）
* 適用性表單
* 資源
* XFS

### 中繼資料的完整清單 {#extensive-list-of-metadata-nbsp}

以下是AEM Forms支援的中繼資料屬性詳細清單：

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性名稱</strong></td> 
   <td><strong>資產類型</strong></td> 
   <td><strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>標題</td> 
   <td>除了資源</td> 
   <td>窗體的顯示名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td>說明</td> 
   <td>除了資源</td> 
   <td>表單說明。 用戶可以指定此值。<br /> </td> 
  </tr> 
  <tr> 
   <td>類型</td> 
   <td>全部</td> 
   <td><p>指定資產類型的唯讀值。 它可以有下列其中一個值：</p> 
    <ul> 
     <li>表單範本</li> 
     <li>PDF表單、PDF表單(Acroform)或PDF表單（簽名）</li> 
     <li>文檔，文檔（已簽名）</li> 
     <li>調適性表單</li> 
     <li>資源</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>建立日期</td> 
   <td>全部</td> 
   <td>指定資產建立時間的唯讀值。</td> 
  </tr> 
  <tr> 
   <td>上次修改日期</td> 
   <td>全部</td> 
   <td>指定上次修改資產時間的唯讀值。</td> 
  </tr> 
  <tr> 
   <td>作者</td> 
   <td>除了資源</td> 
   <td><p>根據表單類型自動計算的唯讀值。</p> 
    <ul> 
     <li>PDF/表單範本/檔案 — 從上傳的二進位檔案擷取。</li> 
     <li>適用性表單 — 在表單建立時登入的使用者。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>狀態</td> 
   <td>除了資源</td> 
   <td><p> 一個唯讀值，它定義表單的以下狀態之一：</p> 
    <ul> 
     <li>無值：如果表單從未發佈。</li> 
     <li>已發佈：表單發佈時。</li> 
     <li>已修改：表單發佈後修改一次的時間。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>上次發佈日期</td> 
   <td>除了資源</td> 
   <td>一個唯讀值，指定表單上次發佈時間。</td> 
  </tr> 
  <tr> 
   <td>發佈開/關時間</td> 
   <td>除了資源</td> 
   <td><p>排程自動發佈/取消發佈表單的時間。 使用者在編輯中繼資料時設定此值。</p> 
    <ul> 
     <li>「發佈開啟」和「關閉」時間都應超過目前日期。 </li> 
     <li>「發佈關閉」時間應超過「發佈開啟」時間。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>提交URL</td> 
   <td><p>表單範本</p> <p>PDF表單</p> </td> 
   <td><p>配置用戶指定的URL以將表單資料提交到Servlet。</p> <p>提交URL可使用下列任何方法來設定，依優先順序列出：</p> 
    <ul> 
     <li>在AEM Forms Designer中建立XFA表單時，使用HTTP提交按鈕，直接在表單範本中指定提交URL。</li> 
     <li>在AEM Forms UI中，選取表單並指定編輯中繼資料屬性時的提交URL。</li> 
     <li>在Forms Portal中，編輯Search &amp; Lister元件，並在「表單連結」標籤下指定提交URL。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>HTML呈現設定檔</td> 
   <td>表單範本</td> 
   <td>以HTML格式呈現表單範本時使用的HTML呈現設定檔。</td> 
  </tr> 
  <tr> 
   <td>呈現格式</td> 
   <td><p>表單範本</p> <p>調適性表單</p> </td> 
   <td><p>此選項可讓使用者在發佈表單時指定表單的呈現格式：</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>兩者</li> 
    </ul> <p>此選項僅用於限制一般使用者可看見表單的表單入口網站上的轉譯格式。</p> </td> 
  </tr> 
  <tr> 
   <td>標記</td> 
   <td>除了資源</td> 
   <td>與表單相關聯的標籤可方便快速輕鬆搜尋。</td> 
  </tr> 
  <tr> 
   <td>引用</td> 
   <td><p>調適性表單</p> <p>表單範本</p> <p>資源</p> </td> 
   <td><p>此表單相關的資產清單（其他表單或資源）。 這些資產可分為下列兩個類別：</p> 
    <ul> 
     <li>指：目前表單所指的資產。</li> 
     <li>引用者：指流動資產的資產。</li> 
    </ul> <p>這些資產會顯示為連結，按一下它們即可直接存取其中繼資料。<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>表單模型(XDP/XSD)選項</td> 
   <td>調適性表單</td> 
   <td><p>指定編寫最適化表單時使用的表單模型。 此屬性可以有下列值：</p> 
    <ul> 
     <li>表單範本：從存放庫中現有的表單模板中選擇一個表單模板。 此值可以更新。</li> 
     <li>XML架構：已上載XSD檔案。 此值可以更新。</li> 
     <li>無</li> 
    </ul> 
    <div>
      選取後，表單模型即可更新，但無法移除。 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## 檢視表單中繼資料 {#view-form-metadata-nbsp}

資產有現有的屬性值，可以以唯讀模式檢視。 此中繼資料源於表單上傳或表單建立時。

1. 導覽至您要檢視中繼資料的資產位置。

1. 使用下列其中一種方式開啟屬性頁面：

   1. 按一下「快速操作」中的「查看屬性」 ![e_reviewmode_properties_n](assets/e_reviewmode_properties_n.png)表徵圖。

      >[!NOTE]
      >
      >「快速動作」是滑鼠暫留時在縮圖上顯示的動作項目。

   1. 選擇該表單，然後按一下工具欄中顯示的「查看屬性」 ![e_reviewmode_properties_n](assets/e_reviewmode_properties_n.png)表徵圖。
   1. 不在選取模式時，按一下表單縮圖以導覽至表單詳細資訊頁面。 現在，按一下右上方的![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png)眼睛圖示，然後按一下其下方清單中的「屬性」 。

1. 開啟的屬性頁面會顯示僅包含那些包含某些值的中繼資料屬性的結構。

   屬性頁面有一個工具列，其中包含兩個動作圖示：

   * 編輯：![aem6forms_edit](assets/aem6forms_edit.png)編輯中繼資料屬性值
   * 查看：![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png)導覽至「表單詳細資訊」頁面，該頁面會在預覽模式中開啟表單。

   內容部分分為兩部分：

   * 左側面板包含表單的縮圖
   * 右側面板包含以唯讀模式（分佈在各種標籤間）顯示的中繼資料屬性。


## 新增/更新表單中繼資料值 {#add-update-form-metadata-values-nbsp}

您可以編輯現有中繼資料屬性的值，或將新值新增至現有中繼資料屬性欄位（例如，中繼資料欄位空白時）。

### 更新元資料屬性值 {#update-metadata-property-values}

1. 請依照上一節中提及的步驟，開啟屬性頁面，供檢視所選表單的現有中繼資料。

1. 在工具列中，按一下編輯圖示![aem6forms_edit](assets/aem6forms_edit.png) ，將頁面模式從唯讀變更為讀/寫。

1. 開啟的屬性頁面包含混合了可編輯輸入欄位和靜態文本的架構。

1. 靜態文字中顯示的屬性是無法編輯的屬性。

1. 您可以導覽至其他標籤，以尋找放置在其下之中繼資料屬性的輸入欄位。

   此頁面有一個工具列，其中包含兩個與檢視模式中不同的動作圖示：

   * 取消：![aem6forms_close](assets/aem6forms_close.svg_w24.png)取消迄今對中繼資料屬性值所做的任何變更
   * 完成：![aem6forms_check](assets/aem6forms_check.png)儲存目前對中繼資料屬性值所做的所有變更

   這兩個動作都會將使用者引導回包含已更新值的屬性頁面的唯讀模式。

### 更新表單縮圖  {#update-the-form-thumbnail-nbsp}

屬性頁面中的左側面板會顯示表單的縮圖。 依預設，顯示的縮圖是建立表單（最適化表單）時或表單上傳時產生的縮圖。

對於所有表單類型，您可以選擇按一下「**[!UICONTROL 上傳影像]**」並從本機目錄瀏覽影像檔案，以上傳影像。 選取的影像會作為縮圖，而非預設影像。

針對適用性表單，提供額外功能，可讓使用者產生縮圖，作為目前適用性表單預覽的快照。 由於AEM Forms也支援製作最適化表單，每次您變更最適化表單時，最適化表單的預覽可能會改變。 產生縮圖的功能可協助您根據目前的預覽狀態，取得最適化表單的全新縮圖。 按一下「**[!UICONTROL 產生預覽]**」以執行此動作。

>[!NOTE]
>
>* 對縮圖使用正方形影像。 使用非正方形影像並在清單視圖中查看縮略圖時，縮略圖將出現剪貼。
>* 上傳或產生新影像後，縮圖會由此影像取代，且無法重設為上一個影像。

>



## 新增自訂中繼資料  {#add-custom-metadata-nbsp}

除了現成可用的中繼資料，AEM Forms也支援新的自訂中繼資料。

提供工具（中繼資料結構編輯器）來定義中繼資料配置的結構；也就是說，表單的&#x200B;**[!UICONTROL 屬性]**&#x200B;頁面中顯示內容的佈局。 中繼資料結構編輯器可讓您新增或修改資產的自訂結構。

AEM Forms會在此工具中公開支援表單類型的中繼資料結構。 如此一來，您便可存取這些結構，並使用中繼資料結構編輯器中提供的功能來新增自訂屬性。

### 導覽中繼資料結構編輯器  {#navigate-the-metadata-schema-editor-nbsp}

1. 導覽至「**[!UICONTROL 工具>資產>中繼資料結構]**」。

1. 從列出的架構表單中按一下&#x200B;**[!UICONTROL forms]**。

1. 從開啟的清單中，按一下您要新增自訂中繼資料的資產類型。

   >[!NOTE]
   >
   >這些結構包含出廠提供的元資料屬性，且不得更改/編輯（選中複選框，然後從工具欄按一下編輯），以避免出現功能問題。

1. 所點按的任何資產類型都會開啟包含`extendedmetadata`選項的清單。 編輯此架構。

1. 選取`extendedmetadata`旁的核取方塊，然後按一下工具列中顯示的編輯![aem6forms_edit](assets/aem6forms_edit.png)圖示。

1. AEM Forms會開啟所選資產類型的中繼資料結構編輯器/表單產生器（在此例中為最適化表單）。

   ![適用性表單類型的中繼資料結構編輯器](assets/metadata-schema-editor-for-adaptive-form-type.png)

[按一下放大](assets/metadata-schema-editor-for-adaptive-form-type.png)

   1. 左側面板包含標籤式區段，其中會放置欄位，右側面板會顯示所有可用的UI元件，以及從左側面板選取之欄位的屬性。

   1. 鎖定的區段無法編輯，且包含現成提供之所有中繼資料屬性的欄位。

   1. 您可以按一下+符號來新增其他標籤。

   1. 您可以將欄位元件從&#x200B;**[!UICONTROL Build Form]**&#x200B;區段拖曳至架構頁面，以新增所需類型的自訂欄位。
   1. 按一下欄位後，可在&#x200B;**[!UICONTROL Settings]**&#x200B;區段下提供此欄位的規格。

### 在結構編輯器中新增自訂中繼資料屬性  {#add-custom-metadata-property-in-schema-editor-nbsp}

1. 導覽至您要新增自訂屬性的索引標籤（現有或新）。

1. 從&#x200B;**[!UICONTROL Build Form]**&#x200B;區段拖曳所需類型的元件至左側面板，放置在方便的位置。

   >[!NOTE]
   >
   >您無法移動鎖定的區段，但您可以將元件放置在任何空格中。

1. 按一下您剛拖曳的元件。 在右側面板中開啟的「設定」標籤中，填寫下列欄位的資訊：

   1. 指定欄位標籤，在架構中放置的欄位上方作為顯示名稱(例如：部門)
   1. 在「對應至屬性」欄位下，您會看到預填值&#x200B;**&#39;。/jcr:content/metadata/default&#39;**。 將「**default**」變更為所需的屬性名稱，該名稱用於將屬性儲存在crx儲存庫中(例如：&#39;。/jcr:content/metadata/department&#39;)

      >[!NOTE]
      >
      >請勿更改前置詞&#39;。/jcr:content/metadata/&#39;，它定義了儲存屬性的路徑。
      >
      >
      >此外，屬性名稱必須是唯一的，以避免為存放庫中相同位置的兩個或兩個以上屬性寫入值。 因此，建議您變更「default」值。

   1. 根據需求填入其他設定。 例如：如果要將欄位設為必填欄位，請選取「必填」選項。

   1. 若要刪除您新增的欄位，請選取欄位，然後按一下刪除![delete-1](assets/delete-1.png)圖示。

1. 如有必要，請依照步驟1至3新增其他屬性。
1. 進行所有變更後，按一下「**完成**」。

   您已成功新增自訂中繼資料屬性。

AEM Forms中的所有適用性表單現在都包含此額外的中繼資料屬性。 您可以從屬性頁面進行編輯。
