---
title: Digital Rights Management [!DNL Adobe Experience Manager Assets].
description: 了解如何在 [!DNL Experience Manager].
contentOwner: AG
feature: DRM,Asset Management
role: User,Admin
exl-id: 3eea4983-9dd5-4d69-ad93-3cd37a656d22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1466'
ht-degree: 8%

---

# 資產的 Digital Rights Management {#digital-rights-management-in-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

數位資產通常與指定使用條款和持續時間的授權相關聯。 因為 [!DNL Adobe Experience Manager Assets] 與 [!DNL Experience Manager] 平台，您就可以有效管理資產到期資訊和資產狀態。 您也可以將授權資訊與資產建立關聯。

## 資產過期 {#asset-expiration}

資產到期是強制執行資產授權要求的有效方式。 它可確保已發佈的資產在過期時未發佈，以免發生任何違反授權的情況。 沒有管理員權限的使用者無法編輯、複製、移動、發佈和下載過期的資產。

您可以在 [!DNL Assets] 「 」和「 」清單檢視中的主控台。

![expired_flag_card](assets/expired_flag_card.png)

*圖：在卡片檢視中，卡片上的標幟表示資產已過期。*

![expired_flag_list](assets/expired_flag_list.png)

*圖：在清單檢視中， [!UICONTROL 狀態] 欄顯示 [!UICONTROL 過期] 橫幅。*

您可以在 [!UICONTROL 時間表] 在左側邊欄。

![chlimage_1-144](assets/chlimage_1-144.png)

>[!NOTE]
>
>不同時區的使用者會以不同方式顯示資產的到期日。

您也可以在 **[!UICONTROL 參考]** 欄。 它可管理複合資產與參考的子資產、集合和專案之間的資產到期狀態和關係。

1. 導覽至您要檢視其參考網頁和複合資產的資產。
1. 選取資產，然後按一下 [!DNL Experience Manager] 標誌。

   ![chlimage_1-145](assets/chlimage_1-145.png)

1. 選擇 **[!UICONTROL 參考]** 的上界。

   ![chlimage_1-146](assets/chlimage_1-146.png)

   對於過期的資產，「參考」邊欄會顯示到期狀態 **[!UICONTROL 資產已過期]** 頂端。

   ![chlimage_1-147](assets/chlimage_1-147.png)

   如果資產已過期，「參考」邊欄會顯示狀態 **[!UICONTROL 資產已過期子資產]**.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### 搜尋過期的資產 {#search-expired-assets}

您可以在「搜尋」面板中搜尋過期的資產，包括過期的子資產。

1. 在 [!DNL Assets] 主控台，按一下 **[!UICONTROL 搜尋]** ，以顯示「Omnisearch」方塊。

   ![chlimage_1-149](assets/chlimage_1-149.png)

1. 在Omnisearch框中，按Enter鍵顯示搜索結果頁。

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. 按一下 [!DNL Experience Manager] 徽標以顯示搜索面板。

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. 按一下 **[!UICONTROL 到期狀態]** 選項加以展開。

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. 選擇 **[!UICONTROL 過期]**. 過期的資產會顯示在搜尋結果中。

   ![chlimage_1-153](assets/chlimage_1-153.png)

當您選擇 **[!UICONTROL 過期]** 選項 [!DNL Assets] 主控台只會顯示複合資產參照的過期資產和子資產。 參考過期子資產的複合資產，不會在子資產過期後立即顯示。 而是會顯示在 [!DNL Experience Manager] 會偵測排程器下次執行時，它們會參照過期的子資產。

如果您將已發佈資產的到期日修改為早於目前排程器週期的日期，排程仍會在下次執行時將此資產偵測為過期資產，並據以反映狀態。

此外，如果故障或錯誤使調度程式無法檢測當前週期中的過期資產，則調度程式將在下一個週期中重新檢查這些資產並檢測其過期狀態。

若要啟用 [!DNL Assets] 若要顯示參照的複合資產以及過期的子資產，請設定 **[!UICONTROL Adobe CQ DAM過期通知]** 工作流程 [!DNL Experience Manager] 配置管理器。

1. 開啟 [!DNL Experience Manager] 配置管理器。
1. 選擇 **[!UICONTROL Adobe CQ DAM過期通知]**. 依預設， **[!UICONTROL 基於時間的調度程式]** 已選取，系統會排程工作以在特定時間檢查資產是否已過期子資產。 作業完成後，過期的子資產和參考資產的資產會在搜尋結果中顯示為過期。

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. 要定期運行作業，請清除「基於時 **[!UICONTROL 間的調度程式規則]** 」欄位，並在「定期調度程式」欄位中以秒為單 **[!UICONTROL 位修改時間]** 。例如，示例表達式&#39;0 0 0 &amp;ast;&amp;ast;?&#39;會在00小時觸發工作。
1. 選擇 **[!UICONTROL 傳送電子郵件]** 在資產過期時收到電子郵件。

   >[!NOTE]
   >
   >僅限資產建立者（將特定資產上傳至的人員） [!DNL Assets])會在資產過期時收到電子郵件。 請參閱 [如何配置電子郵件通知](/help/sites-administering/notification.md) 如需有關在整體 [!DNL Experience Manager] 層級。

1. 在 **[!UICONTROL 以秒為單位的先前通知]** 欄位中，指定當您要接收到有關到期的通知時，資產到期前的時間（以秒為單位）。 如果您是管理員或資產建立者，您會在資產到期前收到訊息，通知您資產將在指定時間後到期。

   資產過期後，您會收到確認到期的其他通知。 此外，已過期的資產會停用。

1. 按一下「**[!UICONTROL 儲存]**」。

## 資產狀態 {#asset-states}

此 [!DNL Assets] 主控台可顯示資產的各種狀態。 根據特定資產的目前狀態，其卡片檢視會顯示描述其狀態的標籤，例如「已到期」、「已發佈」、「已核准」、「已拒絕」等。

1. 在 [!DNL Assets] 使用者介面，選取資產。

   ![chlimage_1-155](assets/chlimage_1-155.png)

1. 按一下 **[!UICONTROL 發佈]** 的上界。 如果你沒看到 **發佈** 在工具列上，按一下 **[!UICONTROL 更多]** 在工具列上，然後找出 **[!UICONTROL 發佈]** 選項。

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. 選擇 **[!UICONTROL 發佈]** ，然後關閉確認對話方塊。
1. 退出選擇模式。 資產的發佈狀態會顯示在卡片檢視中資產縮圖的底部。 在清單檢視中，「已發佈」欄會顯示資產發佈的時間。

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. 若要顯示其資產詳細資訊頁面，請在 [!DNL Assets] 介面，選取資產並按一下 **[!UICONTROL 屬性]**.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. 在進階標籤中，從 **[!UICONTROL 過期]** 欄位。

   ![在「過期」欄位中設定資產到期日期和時間](assets/chlimage_1-159.png)

   *圖： [!UICONTROL 進階] 標籤 [!UICONTROL 屬性] 頁面來設定資產過期時間。*

1. 按一下 **[!UICONTROL 儲存]** 然後按一下 **[!UICONTROL 關閉]** 顯示「資產」控制台。
1. 資產的發佈狀態會在卡片檢視中資產縮圖底部指出過期狀態。 在清單檢視中，資產的狀態會顯示為 **[!UICONTROL 過期]**.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. 在 [!DNL Assets] 控制台，選擇資料夾並在資料夾上建立審閱任務。
1. 複核和批准/拒絕複核任務中的資產，然後按一下 **[!UICONTROL 完成]**.
1. 導航至建立審閱任務的資料夾。 您核准/拒絕的資產狀態會顯示在卡片檢視的底部。 在清單檢視中，核准和到期狀態會顯示在適當的欄中。

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. 若要根據資產的狀態來搜尋資產，請按一下 **[!UICONTROL 搜尋]** 來顯示Omnisearch列。

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. 按回車鍵並按一下 [!DNL Experience Manager] 顯示「搜索」面板。
1. 在搜尋面板中，按一下 **[!UICONTROL 發佈狀態]** 選取 **[!UICONTROL 已發佈]** 若要在 [!DNL Assets].

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. 按一下 **[!UICONTROL 核准狀態]** 並按一下適當的選項，以搜尋已核准或已拒絕的資產。

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. 若要根據資產的到期狀態來搜尋資產，請在「搜尋」面 **[!UICONTROL 板中選取「到期狀態]** 」，然後選擇適當的選項。

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. 您也可以根據各種搜尋刻面下的狀態組合來搜尋資產。 例如，您可以在搜尋Facet中選取適當的選項，以搜尋已在審核任務中核准且尚未過期的已發佈資產。

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management [!DNL Assets] {#digital-rights-management-in-assets-1}

此功能可強制您接受授權合約，之後才能從下載授權資產 [!DNL Adobe Experience Manager Assets].

如果您選取受保護的資產，然後按一下 **[!UICONTROL 下載]**，系統會將您重新導向至授權頁面，以接受授權合約。 若您不接受授權合約， **[!UICONTROL 下載]** 選項無法使用。

如果選取項目包含多個受保護的資產，請一次選取一個資產、接受授權合約，然後繼續下載資產。

若符合以下任一條件，即視為資產受保護：

* 資產中繼資料屬性 `xmpRights:WebStatement` 指向包含資產授權合約的頁面路徑。
* 資產中繼資料屬性的值 `adobe_dam:restrictions` 是指定許可協定的原始HTML。

>[!NOTE]
>
>位置 `/etc/dam/drm/licenses` 用於在早期版本中儲存許可證 [!DNL Experience Manager] 已過時。
>
>如果您建立或修改許可證頁，或從上一頁將其埠連接 [!DNL Experience Manager] 發行版本，Adobe建議您將其儲存在 `/apps/settings/dam/drm/licenses` 或 `/conf/&ast;/settings/dam/drm/licenses`.

### 下載受DRM保護的資產 {#downloading-drm-assets}

1. 在卡片檢視中，選取您要下載的資產，然後按一下 **[!UICONTROL 下載]**.
1. 在「版 **[!UICONTROL 權管理]** 」頁面中，從清單中選取您要下載的資產。
1. 在 [!UICONTROL 授權] 窗格，選擇 **[!UICONTROL 同意]**. 資產旁會出現核取記號。 按一下 **[!UICONTROL 下載]** 選項。

   >[!NOTE]
   >
   >此 **[!UICONTROL 下載]** 只有在您選擇同意受保護資產的授權合約時，才會啟用「 」選項。 不過，如果您的選擇同時包含受保護和未受保護的資產，則只有受保護的資產會列在窗格和 **[!UICONTROL 下載]** 選項，即可下載未受保護的資產。 若要同時接受多個受保護資產的授權合約，請從清單中選取資產，然後選擇「同 **[!UICONTROL 意」]**。

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. 在對話方塊中，按一下 **[!UICONTROL 下載]** 下載資產或其轉譯。
