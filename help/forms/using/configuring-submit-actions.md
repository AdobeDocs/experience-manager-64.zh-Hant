---
title: 設定提交動作
seo-title: Configuring the Submit action
description: AEM Forms可讓您設定提交動作，以定義提交後處理最適化表單的方式。 您可以使用內建的提交動作，或從草稿開始撰寫自己的動作。
seo-description: AEM Forms allows you to configure a submit action to define how an adaptive form is processed after submission. You can use built-in submit actions or write your own from scratch.
uuid: aa261e65-a1ec-402b-80de-0ba8a294e315
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: fea76f90-22d5-4836-9901-a35229401eb0
feature: Adaptive Forms
exl-id: 2a842bdc-6dcf-42cc-9a45-57ac15b79eb7
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 0%

---

# 設定提交動作 {#configuring-the-submit-action}

## 提交動作簡介 {#introduction-to-submit-actions}

當使用者按一下最適化表單上的「提交」按鈕時，會觸發提交動作。 您可以在最適化表單上設定提交動作。 最適化表單提供一些立即可用的提交動作。 您可以複製和擴展預設提交操作，以建立自己的提交操作。 不過，您可以根據需求撰寫並註冊自己的提交動作，以便以提交的表單處理資料。

預填或提交表單時，已提交的資料會透過AEM路由，以便以中間格式進行資料篡改。 除非適用性表單使用Acrobat Sign、驗證、表單入口網站草稿或提交，或AEM工作流程，否則資料不會儲存在AEM例項上

您可以在 **[!UICONTROL 提交]** 區段（位於側邊欄中）。

![配置提交操作](assets/thank-you-setting.png)
**圖：** *配置提交操作*

適用性表單可用的預設提交動作為：

* 提交到REST端點
* 傳送電子郵件
* 透過電子郵件傳送PDF
* 叫用Forms Workflow
* 使用表單資料模型提交
* Forms Portal提交動作
* 叫用AEM工作流程

>[!NOTE]
>
>透過電子郵件提交動作傳送PDF僅適用於以XFA範本作為表單模型的最適化表單。

>[!NOTE]
>
>確保 [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder exists。 臨時儲存附件時需要該目錄。 如果目錄不存在，請建立它。

>[!CAUTION]
>
>若您 [預填](/help/forms/using/prepopulate-adaptive-form-fields.md) 表單範本、表單資料模型或結構式適用性表單（含XML或JSON資料）會向結構（XML結構描述、JSON結構描述、表單範本或表單資料模型）投訴，而結構（即資料不包含） &lt;afdata>, &lt;afbounddata>，和 &lt;/afunbounddata> 標籤，則無界欄位的資料(無界欄位是沒有 [賓德雷夫](/help/forms/using/prepopulate-adaptive-form-fields.md) 屬性)的欄位。

您可以撰寫最適化表單的自訂提交動作，以符合您的使用案例。 如需詳細資訊，請參閱 [撰寫最適化表單的自訂提交動作](/help/forms/using/custom-submit-action-form.md).

## 提交到REST端點 {#submit-to-rest-endpoint}

此 **[!UICONTROL 提交到REST端點]** 提交選項會將表單中填入的資料傳遞至已設定的確認頁面，作為HTTPGET請求的一部分。 您可以新增要請求的欄位名稱。 請求的格式為：

`{fieldName}={request parameter name}`

如下圖所示， `param1` 和 `param2` 會以參數的形式傳遞，且值會從 **[!UICONTROL textbox]** 和 **[!UICONTROL 數字框]** 欄位供下一個動作使用。

您也可以 **[!UICONTROL 啟用POST請求]** 和提供要求張貼的URL。 若要將資料提交至托管表單的AEM伺服器，請使用與AEM伺服器的根路徑相對應的相對路徑。 例如， /content/forms/af/SampleForm.html。 要向任何其他伺服器提交資料，請使用絕對路徑。

![配置Rest端點提交操作](assets/action-config.png)

配置Rest端點提交操作

>[!NOTE]
若要在REST URL中以參數形式傳遞欄位，所有欄位都必須有不同的元素名稱，即使欄位放在不同面板上亦然。

### 將提交的資料發佈至資源或外部休息端點  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

使用 **[!UICONTROL 提交到REST端點]** 動作，將提交的資料張貼至其餘URL。 URL可以是內部（轉譯表單的伺服器）或外部伺服器。

若要將資料發佈至內部伺服器，請提供資源的路徑。 資料會發佈在資源的路徑上。 例如/content/restEndPoint。 對於這些帖子請求，使用提交請求的驗證資訊。

若要將資料發佈至外部伺服器，請提供URL。 URL的格式為https:// host:port/path_to_rest_end_point。 請確定您已設定以匿名方式處理POST要求的路徑。

![以感謝頁面參數傳遞之欄位值的對應](assets/post-enabled-actionconfig.png)

在上述範例中，使用者在 `textbox` 使用參數擷取 `param1`. 用於發佈使用 `param1` 為：

`String data=request.getParameter("param1");`

同樣，用於發佈XML資料和附件的參數也是 `dataXml` 和 `attachments`.

例如，在指令碼中使用這兩個參數可將資料剖析至余下的端點。 您使用下列語法來儲存和剖析資料：

`String data=request.getParameter("dataXml");`\
`String att=request.getParameter("attachments");`

在此範例中， `data` 儲存XML資料，並 `att` 儲存附件資料。

## 傳送電子郵件 {#send-email}

此 **[!UICONTROL 傳送電子郵件]** 提交動作會在表單成功提交時，傳送電子郵件給一或多個收件者。 產生的電子郵件可包含預先定義格式的表單資料。

>[!NOTE]
所有表單欄位都必須有不同的元素名稱，即使它們放置在不同的面板上亦然)，以便將表單資料包含在電子郵件中。

## 透過電子郵件傳送PDF {#send-pdf-via-email}

此 **[!UICONTROL 透過電子郵件傳送PDF]** 提交動作會在成功提交表單時，傳送包含表單資料之PDF的電子郵件給一或多個收件者。

**注意：** *此提交動作適用於具有記錄檔案範本的XFA型適用性表單和XSD型適配表單。*

## 叫用表單工作流程 {#invoke-a-forms-workflow}

此 **[!UICONTROL 提交至Forms工作流程]** 提交選項會將資料xml和檔案附件（如果有的話）傳送至現有的AdobeLiveCycle或JEE程式上的AEM Forms。

有關如何配置「提交至表單」工作流提交操作的資訊，請參閱 [使用表單工作流程提交和處理表單資料](/help/forms/using/submit-form-data-livecycle-process.md).

## 使用表單資料模型提交 {#submit-using-form-data-model}

此 **[!UICONTROL 使用表單資料模型提交]** 提交動作會將表單資料模型中指定資料模型物件的已提交適用性表單資料寫入其資料來源。 在配置提交操作時，您可以選擇要將其提交資料寫回其資料源的資料模型對象。

此外，您可以使用表單資料模型和記錄檔案(DoR)將表單附件提交到資料源。

如需表單資料模型的相關資訊，請參閱 [AEM Forms資料整合](/help/forms/using/data-integration.md).

## Forms Portal提交動作 {#forms-portal-submit-action}

此 **[!UICONTROL Forms Portal提交動作]** 選項可透過AEM Forms入口網站取得表單資料。

如需Forms Portal和提交動作的詳細資訊，請參閱 [草稿和提交元件](/help/forms/using/draft-submission-component.md).

## 叫用AEM工作流程 {#invoke-an-aem-workflow}

此 **[!UICONTROL 叫用AEM工作流程]** 提交動作會將適用性表單與AEM工作流程建立關聯。 提交表單時，相關聯的工作流程會自動在處理節點上啟動。 此外，它會將資料檔案、附件和記錄檔案（如果適用）放置在工作流的裝載位置。

使用 **[!UICONTROL 叫用AEM工作流程]** 提交動作， [配置AEM DS設定](/help/forms/using/configuring-the-processing-server-url-.md). 如需建立AEM工作流程的詳細資訊，請參閱 [OSGi上的表單導向工作流程](/help/forms/using/aem-forms-workflow.md).

## 適用性表單中的伺服器端重新驗證 {#server-side-revalidation-in-adaptive-form}

通常，在任何線上資料擷取系統中，開發人員會在用戶端放置一些JavaScript驗證，以強制執行一些業務規則。 但在現代瀏覽器中，一般使用者可以略過這些驗證，並使用各種技術（例如網頁瀏覽器DevTools主控台）手動執行提交作業。 此類技術也適用於最適化表單。 表單開發人員可以建立各種驗證邏輯，但技術上，一般使用者可以略過這些驗證邏輯，並將無效資料提交至伺服器。 無效資料會破壞表單作者已強制執行的業務規則。

伺服器端重新驗證功能也可執行最適化表單作者在伺服器上設計最適化表單時所提供的驗證。 它可防止表單驗證中呈現的資料提交和業務規則違反行為受到任何可能的影響。

### 要在伺服器上驗證什麼？ {#what-to-validate-on-server-br}

適用於最適化表單的所有現成(OOTB)欄位驗證會在伺服器上重新執行：

* 必要
* 驗證子句
* 驗證運算式

### 啟用伺服器端驗證 {#enabling-server-side-validation-br}

使用 **在伺服器上重新驗證** 在側邊欄的適用性表單容器下，啟用或停用目前表單的伺服器端驗證。

![啟用伺服器端驗證](assets/revalidate-on-server.png)
**圖：** *啟用伺服器端驗證*

如果最終用戶繞過這些驗證並提交表單，伺服器將再次執行驗證。 如果驗證在伺服器端失敗，則提交交易會停止。 最終用戶將再次顯示原始表單。 擷取的資料和提交的資料會以錯誤形式呈現給使用者。

### 支援驗證運算式中的自訂函式 {#supporting-custom-functions-in-validation-expressions-br}

有時，在 **複雜驗證規則**，完全驗證指令碼位於自訂函式中，而作者會從欄位驗證運算式呼叫這些自訂函式。 若要讓此自訂函式程式庫在執行伺服器端驗證時已知且可供使用，表單作者可在 **[!UICONTROL 基本]** 標籤，如下所示。

![支援驗證運算式中的自訂函式](assets/clientlib-cat.png)
**圖：** *支援驗證運算式中的自訂函式*

作者可以根據最適化表單設定自訂javascript程式庫。 在程式庫中，僅保留可重複使用的函式，此函式依存於jquery和underscore.js協力廠商程式庫。

## 提交動作的錯誤處理 {#error-handling-on-submit-action}

作為AEM安全性和強化准則的一部分，請配置自定義錯誤頁，如404.jsp和500.jsp。 提交表單時，會呼叫這些處理常式404或500錯誤。 在發佈節點上觸發這些錯誤代碼時，也會呼叫處理常式。

如需詳細資訊，請參閱 [自訂由錯誤處理常式顯示的頁面](/help/sites-developing/customizing-errorhandler-pages.md).
