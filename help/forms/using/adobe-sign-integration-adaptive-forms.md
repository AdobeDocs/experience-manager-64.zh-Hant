---
title: 整合Acrobat Sign與AEM Forms
seo-title: Integrate Acrobat Sign with AEM Forms
description: 了解如何設定Acrobat Sign for AEM Forms
seo-description: Learn how to configure Acrobat Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Acrobat Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 13%

---

# 整合Acrobat Sign與AEM Forms {#integrate-adobe-sign-with-aem-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Acrobat Sign可啟用最適化表單的電子簽名工作流程。 電子簽名有助於改善處理法律、銷售、薪資、人力資源管理及許多領域文件的工作流程。

在典型的Acrobat Sign和最適化表單案例中，使用者會填入最適化表單以 **申請服務**. 例如，信用卡申請表和市民福利表單。用戶申請、提交和簽署申請表單時，此表單會被傳送給服務提供者，以進一步動作。服務提供商審核應用程式，並使用Acrobat Sign來標籤已批准的應用程式。 若要啟用類似的電子簽名工作流程，您可以整合Acrobat Sign與AEM Forms。

若要搭配AEM Forms使用Acrobat Sign，請在AEM雲端服務中設定Acrobat Sign:

## 必備條件 {#prerequisites}

若要整合Acrobat Sign與AEM Forms，您需要下列項目：

* 活動 [Acrobat Sign開發人員帳戶。](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* 安 [啟用SSL](/help/sites-administering/ssl-by-default.md) AEM Forms伺服器。
* 安 [Acrobat Sign API應用程式](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Acrobat Sign API應用程式的憑證（用戶端ID和用戶端密碼）。
* 重新設定時，請從製作和發佈執行個體移除現有的Acrobat Sign設定。
* 使用製作和發佈執行個體的[同一密碼編譯金鑰](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed)。

## 使用AEM Forms設定Acrobat Sign {#configure-adobe-sign-with-aem-forms}

準備好必要條件後，請執行下列步驟，在製作執行個體上使用AEM Forms設定Acrobat Sign:

1. 在AEM Forms作者例項上，導覽至 **工具** ![錘](assets/hammer.png) > **一般** > **配置瀏覽器**.
   * 請參閱 [設定瀏覽器檔案](/help/sites-administering/configurations.md) 以取得更多資訊。
1. 在 **[!UICONTROL 配置瀏覽器]** 頁面，點選 **[!UICONTROL 建立]**.
1. 在 **[!UICONTROL 建立配置]** 對話框，指定 **[!UICONTROL 標題]** 若為設定，請啟用 **[!UICONTROL 雲端設定]**，然後點選 **[!UICONTROL 建立]**. 它會為雲端服務建立設定容器。
1. 導覽至 **工具** ![錘](assets/hammer.png) > **Cloud Services** > **Acrobat Sign** ，然後選取您在上述步驟中建立的設定容器。

   >[!NOTE]
   >
   >您可以執行步驟1至4來建立新的設定容器，以及在容器中建立Acrobat Sign設定，或使用現有 `global` 資料夾 **工具** ![錘](assets/hammer.png) > **Cloud Services** > **Acrobat Sign**. 如果您在新設定容器中建立設定，請務必在 **[!UICONTROL 組態容器]** 欄位。

   >[!NOTE]
   確認雲端服務設定頁面的URL開頭為 **HTTPS**. 如果沒有， [啟用SSL](/help/sites-administering/ssl-by-default.md) AEM Forms伺服器。

1. 在設定頁面上，點選 **[!UICONTROL 建立]** 在AEM Forms中建立Acrobat Sign設定。
1. 在 **[!UICONTROL 一般]** 的 **[!UICONTROL 建立Acrobat Sign設定]** 頁面，指定 **名稱** 針對設定並點選 **下一個**. 您可以選擇指定標題並瀏覽以選取設定的縮圖。

1. 將您目前瀏覽器視窗中的 URL 複製到筆記本。必須使用AEM Forms來設定Acrobat Sign應用程式。

1. 為Acrobat Sign應用程式配置OAuth設定：

   1. 開啟瀏覽器視窗並登入Acrobat Sign開發人員帳戶。
   1. 選取為AEM Forms設定的應用程式，然後點選「設定OAuth以使用應用程式」。
   1. 在 **重新導向URL** 框中，添加在上一步中複製的HTTPS URL，然後按一下 **儲存**.
   1. 為Acrobat Sign應用程式啟用下列OAuth設定，然後按一下 **儲存**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   如需設定Acrobat Sign應用程式的OAuth設定及取得金鑰的逐步資訊，請參閱 [配置應用程式的oAuth設定](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) 開發人員檔案。

   ![OAuth Config](assets/oauthconfig_new.png)

1. 返回 **建立Acrobat Sign設定** 頁面。 在 **[!UICONTROL 設定]** 標籤 **[!UICONTROL OAuth URL]** 欄位提及下列預設URL:

   `https://secure.na1.echosign.com/public/oauth`

   其中：

   **na1** 是指預設的資料庫分片。

   您可以修改資料庫分片的值。重新啟動伺服器，以便能夠將新值用於資料庫共用。

1. 指定 **用戶端ID** （亦稱為應用程式ID）和 **用戶端密碼**. 選取 **也啟用Acrobat Sign以取得附件** 選項，將附加至適用性表單的檔案附加至傳送以供簽署的對應Acrobat Sign檔案。

   點選 **[!UICONTROL 連線至Acrobat Sign]**. 提示輸入憑證時，請提供建立Acrobat Sign應用程式時所使用之帳戶的使用者名稱和密碼。

   點選 **[!UICONTROL 建立]** 來建立Acrobat Sign設定。

1. 開啟AEM Web Console。 URL為 `https://'[server]:[port]'/system/console/configMgr`
1. 開啟 **Forms通用配置服務。**
1. 在 **允許** 欄位， **選取** 所有用戶 — 所有用戶（匿名或已登錄）都可以預覽附件、驗證和簽名表單，然後按一下 **儲存。** 製作例項已設定為使用Acrobat Sign。
1. 使用 [複製](/help/sites-deploying/replication.md) 在對應的發佈執行個體上建立相同設定。

現在，Acrobat Sign已與AEM Forms整合，且可在最適化表單中使用。 結束日期 [在最適化表單中使用Acrobat Sign服務](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)，請在適用性表單屬性中指定上述建立的設定容器。

## 設定Acrobat Sign排程器以同步簽署狀態 {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

只有在所有簽署者完成簽署程式後，才會提交已啟用Acrobat Sign的最適化表單。 依預設，Acrobat Sign排程器服務會排程在每24小時後檢查（輪詢）簽署者回應。 您可以為您的環境變更預設間隔。執行下列步驟以變更預設間隔：

1. 使用管理員憑證登入AEM Forms伺服器並導覽至 **工具** > **操作** > **Web主控台**.

   您也可以在瀏覽器視窗中開啟下列URL:
   `https://[localhost]:'port'/system/console/configMgr`

1. 找出並開啟 **Acrobat Sign設定服務** 選項。 指定 [cron表達](https://en.wikipedia.org/wiki/Cron#CRON_expression) 在 **狀態更新調度程式表達式** 欄位，按一下 **儲存**. 例如，要在每天00:00 am運行配置服務，請指定 `0 0 0 1/1 * ? *` 在 **狀態更新調度程式表達式** 欄位。

Acrobat Sign的同步狀態預設間隔現已變更。

## 相關文章 {#related-articles}

* [在最適化表單中使用Acrobat Sign](../../forms/using/working-with-adobe-sign.md)
* [搭配使用Acrobat Sign與AEM Forms（影片）](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [整合Acrobat Sign與AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
