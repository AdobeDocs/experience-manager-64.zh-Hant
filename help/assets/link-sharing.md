---
title: 使用連結共用資產
description: 以URL共用資產、資料夾和集合。
contentOwner: AG
feature: Link Sharing,Asset Management
role: User
exl-id: bf4b0acf-4103-4da1-8666-c6d9fe80c41f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 6%

---

# 透過連結共用資產 {#asset-link-sharing}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] 可讓您與組織成員和外部實體（包括合作夥伴和廠商）以URL的形式共用資產、資料夾和集合。 透過連結共用資產是讓外部使用者無須先登入即可取得資源的便利方式 [!DNL Assets].

>[!PREREQUISITES]
>
>* 您需要資料夾或要以連結形式共用的資產的編輯ACL權限。
>* 若要傳送電子郵件給使用者，請在 [Day CQ Mail Service](#configmailservice).


## 共用資產 {#share-assets}

若要產生您要與使用者共用之資產的URL，請使用「連結共用」對話方塊。 具有管理員權限或具有讀取權限的用戶位於 `/var/dam/share` 位置可檢視與其共用的連結。

1. 在 [!DNL Assets] 使用者介面，選取要以連結形式共用的資產。
1. 在工具列中，按一下 **[!UICONTROL 共用連結]** ![共用資產圖示](assets/assets_share.png). 點擊 **[!UICONTROL 共用]** 會預先顯示在 [!UICONTROL 共用連結] 欄位。 在您按一下 **[!UICONTROL 提交]**.

   ![與連結共用對話方塊](assets/chlimage_1-542.png)

   *圖：以連結形式共用資產的對話方塊。*

1. 在「連結共用」對話方 **[!UICONTROL 塊的電子郵件地址方塊中]** ，輸入您要共用連結之使用者的電子郵件ID。您可以新增一或多個使用者。

   ![直接從「連結共用」對話方塊共用資產的連結](assets/chlimage_1-543.png)

   *圖：直接從共用資產連結 [!UICONTROL 連結共用] 對話框。*

   >[!NOTE]
   >
   >如果您輸入非貴組織成員之使用者的電子郵件ID，則 [!UICONTROL 外部用戶] 前置詞為使用者的電子郵件ID。

1. 在 **[!UICONTROL 主旨]** 框中，輸入要共用的資產的主題。
1. 在 **[!UICONTROL 訊息]** 框中，輸入可選消息。

1. 在 **[!UICONTROL 過期]** 欄位，指定連結停止運作的到期日和時間。 連結的預設過期時間為一天。

   ![設定共用連結的到期日](assets/chlimage_1-544.png)

1. 若要讓使用者下載原始資產以及轉譯，請選取 **[!UICONTROL 允許下載原始檔案]**. 依預設，使用者只能下載您以連結形式共用之資產的轉譯。

1. 按一下 **[!UICONTROL 共用]**. 訊息會確認連結已透過電子郵件與使用者共用。

1. 若要檢視共用資產，請按一下傳送給使用者之電子郵件中的連結。 若要產生資產的預覽，請按一下共用資產。 若要關閉預覽，請按一下 **[!UICONTROL 返回]**. 如果您已共用資料夾，請按一下 **[!UICONTROL 父資料夾]** 返回父資料夾。

   ![chlimage_1-546](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >[!DNL Experience Manager] 支援僅產生支援之檔案類型的資產預覽。 如果共用其他MIME類型，則您只能下載資產且無法預覽。

1. 若要下載共用資產，請按一下 **[!UICONTROL 選擇]** 在工具列中，按一下資產，然後按一下 **[!UICONTROL 下載]** 的上界。

   ![下載共用資產的工具列選項](assets/chlimage_1-547.png)

1. 若要檢視您已作為連結共用的資產，請前往 [!DNL Assets] 使用者介面，然後按一下 [!DNL Experience Manager] 標誌。 選擇 **[!UICONTROL 導覽]**. 在導航窗格中，選擇 **[!UICONTROL 共用連結]** 顯示共用資產清單。

1. 若要取消共用資產，請選取資產，然後按一下 **[!UICONTROL 取消共用]** 的上界。 之後會顯示確認訊息。 資產的項目會從清單中移除。

## 設定Day CQ郵件服務 {#configure-day-cq-mail-service}

1. 在 [!DNL Experience Manager] 首頁，導航 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web主控台]**.
1. 從服務清單中，找到 **[!UICONTROL Day CQ Mail Service]**.
1. 按一下 **[!UICONTROL 編輯]** ，並為 **[!UICONTROL Day CQ Mail Service]** 詳細資訊按其名稱提及：

   * SMTP伺服器主機名：電子郵件伺服器主機名稱
   * SMTP伺服器埠：電子郵件伺服器埠
   * SMTP用戶：電子郵件伺服器使用者名稱
   * SMTP密碼：電子郵件伺服器密碼

   ![chlimage_1-548](assets/chlimage_1-548.png)

1. 按一下「**[!UICONTROL 儲存]**」。

## 配置最大資料大小 {#configure-maximum-data-size}

當您從使用連結共用功能共用的連結下載資產時， [!DNL Experience Manager] 從存放庫壓縮資產階層，然後以ZIP檔案傳回資產。 但是，在ZIP檔案中可壓縮的資料量沒有限制的情況下，會對大量資料進行壓縮，這會導致JVM記憶體不足錯誤。 要保護系統免受由於此情況而可能發生的拒絕服務攻擊，請使用 **[!UICONTROL 最大內容大小（未壓縮）]** 參數 **[!UICONTROL 日CQ DAM臨機資產共用代理Servlet]** 在Configuration Manager中。 如果資產的未壓縮大小超過設定的值，資產下載請求就會遭到拒絕。 預設值為100 MB。

1. 按一下 [!DNL Experience Manager] 標誌，然後 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web主控台]**.
1. 在Web主控台中，找出 **[!UICONTROL 日CQ DAM臨機資產共用代理Servlet]** 設定。
1. 在編輯模 **[!UICONTROL 式中開啟「日CQ DAM臨機資產共用代理Servlet]** 」設定，並修改「最大內容大小 (未壓縮) 」 **[!UICONTROL 參數的值]** 。

   ![chlimage_1-549](assets/chlimage_1-549.png)

1. 儲存變更。

## 最佳實務和疑難排解 {#best-practices-and-troubleshooting}

* 資產資料夾或名稱中包含空白字元的集合可能無法共用。
* 如果使用者無法下載共用資產，請洽詢您的 [!DNL Experience Manager] 管理員 [下載限制](#configure-maximum-data-size) 。
* 如果您無法傳送包含共用資產連結的電子郵件，或如果其他使用者無法收到您的電子郵件，請洽詢您的 [!DNL Experience Manager] 管理員 [電子郵件服務](#configure-day-cq-mail-service) 是否已配置。
* 如果您無法使用連結共用功能來共用資產，請確定您擁有適當的權限。 請參閱 [共用資產](#share-assets).
* 如果共用資產移至不同位置，其連結會停止運作。 重新建立連結並重新與使用者共用。

* 如果您想要共用來自 [!DNL Experience Manager] 製作部署至外部實體，請確定您只公開下列用於連結共用的URL，例如 `GET` 僅要求。 基於安全原因封鎖其他URL。

   * `http://[aem_server]:[port]/linkshare.html`
   * `http://[aem_server]:[port]/linksharepreview.html`
   * `http://[aem_server]:[port]/linkexpired.html`
   在 [!DNL Experience Manager] 介面，存取 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web主控台]**. 開啟 **[!UICONTROL Day CQ Link Externalizer]** 設定，並修改 **[!UICONTROL 網域]** 欄位，其值針對 `local`, `author`，和 `publish`. 若 `local` 和 `author` 屬性，請分別提供本機和製作例項的URL。 如果您執行單一 [!DNL Experience Manager] 製作例項，請對 `local` 和 `author` 屬性。 若為發佈例項，請提供 [!DNL Experience Manager] 發佈例項。
