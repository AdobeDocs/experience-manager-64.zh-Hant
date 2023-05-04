---
title: 產生XDP表單的HTML5預覽
seo-title: Generate HTML5 preview of an XDP form
description: 「LiveCycle設計工具」中的「預覽HTML」索引標籤可用來預覽表單在瀏覽器中的顯示效果。
seo-description: Preview HTML tab in LiveCycle Designer can be used to preview forms as they appear in a browser.
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
feature: Mobile Forms
exl-id: f855d3f9-cf3c-4883-b82b-d607250c3dae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 1%

---

# 產生XDP表單的HTML5預覽 {#generate-html-preview-of-an-xdp-form}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

在AEM Forms Designer中設計表單時，除了預覽表單的PDF轉譯外，您也可以預覽表單的HTML5轉譯。 您可以使用 **預覽HTML** 標籤來預覽表單在瀏覽器中的顯示效果。

## 在Designer中啟用XDP表單的HTML預覽 {#html-preview-of-forms-in-forms-designer}

若要讓Designer產生XDP表單的HTML預覽，請執行下列設定：

* 設定Apache Sling Authentication Service
* 禁用保護模式
* 提供AEM Forms伺服器的詳細資訊

### 設定Apache Sling Authentication Service {#configure-apache-sling-authentication-service}

1. 前往 `https://[server]:[port]/system/console/configMgr` 在AEM Forms上運行OSGi或

   `https://[server]:[port]/lc/system/console/configMgr` 在JEE上執行的AEM Forms。

1. 找到並按一下 **Apache Sling Authentication Service** 設定，以在編輯模式中開啟它。

1. 視您是在OSGi或JEE上執行AEM Forms，請在 **驗證需求** 欄位：

   * AEM Forms on JEE

      * -/content/xfaforms
      * -/etc/clientlibs
   * AEM Forms on OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >請勿在「驗證需求」欄位中複製並貼上指定的值，因為它可能會損毀值中的特殊字元。 請改為在欄位中輸入指定值。

1. 在 **[!UICONTROL 匿名用戶名]** 和 **[!UICONTROL 匿名用戶密碼]** 欄位。 指定的憑據用於處理匿名身份驗證並允許匿名用戶訪問。
1. 按一下 **儲存** 以儲存設定。

### 禁用保護模式 {#disable-protected-mode}

此 [受保護模式](/help/forms/using/get-xdp-pdf-documents-aem.md) 預設為開啟。 讓環境保持啟用狀態。 您可以停用該功能，以便在開發環境中預覽HTML5 Forms。 執行下列步驟以停用：

1. 以管理員身分登入AEM Web Console。

   * OSGi上的AEM Forms URL `https://[server]:[port]/system/console/configMgr`
   * JEE上的AEM Forms的URL為 `https://[server]:[port]/lc/system/console/configMgr`

1. 開啟 **[!UICONTROL 行動Forms設定]** 編輯。
1. 取消選取 **[!UICONTROL 保護模式]** 選項，然後按一下 **[!UICONTROL 儲存]**.

### 提供AEM Forms伺服器的詳細資訊 {#provide-details-of-aem-forms-server}

1. 在設計工具中，前往 **工具** >  **選項**.
1. 在「選項」窗口中，選擇 **伺服器選項** 頁面，提供下列詳細資訊，然後按一下 **確定**.

   * **伺服器URL**:AEM Forms伺服器URL。
   * **HTTP埠號**:AEM伺服器埠。 預設值為 4502。
   * **HTML預覽內容：** 轉譯XFA表單之設定檔的路徑。 以下預設配置檔案用於在設計器中預覽表單。 不過，您也可以指定自訂設定檔的路徑。

      * `/content/xfaforms/profiles/default.html` (AEM Forms on OSGi)
      * `/lc/content/xfaforms/profiles/default.html` (JEE版AEM Forms)
   * **Forms管理器內容：** 部署Forms Manager UI的內容路徑。 預設值為：

      * `/aem/forms` (AEM Forms on OSGi)
      * `/lc/forms` (JEE版AEM Forms)

   **注意：** *確認AEM Forms伺服器已啟動並執行。 HTML預覽會連線至CRX伺服器，以*&#x200B;產生&#x200B;*預覽。*

   ![AEM Forms設計工具選項 ](assets/server_options.png)

   AEM Forms設計工具選項

1. 若要預覽HTML中的表單，請按一下 **預覽HTML** 標籤。

   >[!NOTE]
   >
   >如果HTML預覽頁簽已關閉，請按F4以開啟預覽HTML頁簽。 您也可以從「檢視」功能表選取「預覽HTML」，以開啟「預覽HTML」標籤。

   >[!NOTE]
   >
   >HTML預覽不支援PDF檔案，HTML預覽僅適用於XDP檔案。

## 使用範例資料預覽表單 {#to-preview-a-form-using-sample-data}

Designer可讓您使用範例XML資料來預覽和測試表單。 建議您經常使用範例資料測試表單，以確保表單可正確轉譯。

如果您沒有範例資料，可由設計人員建立，或由您自行建立。 (請參閱 [自動產生範例資料以預覽表單](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) 和 [建立範例資料以預覽表單的方式](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

使用範例資料來源來測試您的表單，可確保資料和欄位已對應，且重複的子表單會如預期般重複。 您可以建立平衡的表單版面，為每個物件提供適當空間以顯示合併的資料。

1. 選擇 **檔案>表單屬性**.

1. 按一下 **預覽** 頁簽，然後在「資料檔案」方塊中，輸入測試資料檔案的完整路徑。 您也可以使用「瀏覽」按鈕來導覽至檔案。

1. 按一下&#x200B;**「確定」**。下次在 **預覽HTML** 頁簽中，示例XML檔案中的資料值將顯示在相應的對象中。

## 在儲存庫中預覽表單 {#html-preview-of-forms-in-forms-manager}

在AEM Forms中，您可以在存放庫中預覽表單和檔案。 預覽有助於確切了解使用者使用表單的外觀和行為。

[**聯絡支援**](https://www.adobe.com/tw/account/sign-in.supportportal.html)
