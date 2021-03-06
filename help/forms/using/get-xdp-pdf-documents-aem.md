---
title: 在AEM Forms中取得XDP和PDF檔案
seo-title: 在AEM Forms中取得XDP和PDF檔案
description: AEM Forms可讓您上傳表單和支援的資產，以搭配最適化表單使用。 您也可以以ZIP形式大量上傳表單和相關資源。
seo-description: AEM Forms可讓您上傳表單和支援的資產，以搭配最適化表單使用。 您也可以以ZIP形式大量上傳表單和相關資源。
uuid: c2a86d89-0c56-4d29-932a-dd09277fa7cb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 99da0d37-726e-42b9-b98a-5dd6c2165af6
role: Admin
exl-id: 50bf178d-7a3c-41df-9d13-99c74d944700
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# 在AEM Forms中取得XDP和PDF檔案 {#getting-xdp-and-pdf-documents-in-aem-forms}

## 概覽 {#overview}

您可以上傳至AEM Forms，將表單從本機檔案系統匯入CRX存放庫。 下列資產類型支援上傳操作：

* 表單範本（XFA表單）
* PDF forms
* 文檔（一般PDF文檔）

您可以個別上傳支援的資產類型，或以ZIP封存的形式上傳。 您只能上傳`Resource`類型的資產，並附上ZIP封存中的XFA表單。

>[!NOTE]
>
>請確定您是`form-power-users`群組的成員，才能上傳XDP檔案。 請連絡您的管理員以成為群組的成員。

## 上傳表單 {#uploading-forms}

1. 存取`https://[server]:[port]/aem/forms.html`以登入AEM Forms使用者介面。
1. 導覽至您要上傳表單的資料夾，或導覽至包含表單的資料夾。
1. 在動作工具列中，點選&#x200B;**建立>檔案上傳**。

   ![「建立」下的「從本地儲存」選項](assets/step.png)

1. 「上傳表單」或「封裝」對話方塊可讓您瀏覽並選擇要上傳的檔案。 檔案瀏覽器只會顯示支援的檔案格式（ZIP、XDP和PDF）。

   >[!NOTE]
   >
   >檔案名只能包含英數字元、連字型大小或底線。

1. 選取檔案後按一下「上傳」可上傳檔案，或按一下「取消」可取消上傳。 快顯視窗會列出新增的資產，以及目前位置更新的資產。

   >[!NOTE]
   >
   >若為ZIP檔案，則會顯示所有受支援資產的相對路徑。 系統會忽略ZIP中不支援的資產，且不會列出。 不過，如果ZIP封存檔僅包含不支援的資產，則會顯示錯誤訊息，而非快顯對話方塊。

   ![上傳XFA表單時的上傳對話方塊](assets/upload-scr.png)

1. 如果一或多個資產的檔案名稱無效，則會顯示錯誤。 更正以紅色突出顯示的檔案名並重新上載。

   ![上傳XFA表單時出現錯誤訊息](assets/upload-scr-err.png)

上傳完成後，背景工作流程會根據資產的預覽，為每個資產產生縮圖。 較新版本的資產（如果上傳）會覆寫現有資產。

### 保護模式 {#protected-mode}

AEM Forms伺服器可讓您執行JavaScript程式碼。 惡意JavaScript程式碼可能會損害AEM Forms環境。 受保護模式會限制AEM Forms僅從信任的資產和位置執行XDP檔案。 AEM Forms UI中可用的所有XDP都視為信任的資產。

預設情況下，受保護模式處於開啟狀態。 如有必要，您可以禁用保護模式：

1. 以管理員身分登入AEM Web Console。 URL為`https://[server]:[port]/system/console/configMgr`
1. 開啟行動Forms設定以進行編輯。
1. 取消選擇「保護模式」選項，然後按一下「**保存**」。 已禁用受保護模式。

## 更新參考的XFA表單 {#updating-referenced-xfa-forms}

在AEM Forms中，最適化表單或其他XFA表單範本都可參照XFA表單範本。 此外，範本可以參照資源或其他XFA範本。

參考XFA的適用性表單的欄位已與XFA中可用的欄位系結。 更新表單範本時，相關聯的最適化表單會嘗試與XFA同步。 如需詳細資訊，請參閱將適用性表單與相關聯的XFA](/help/forms/using/synchronizing-adaptive-forms-xfa.md)同步。[

移除表單範本會損毀相依的最適化表單或表單範本。 這種最適化表單有時非正式地稱為骯臟表單。 在AEM Forms使用者介面中，您可透過下列兩種方式找到臟表單。

* 資產清單中的適用性表單縮圖上會顯示警告圖示，當您將指標暫留在警告圖示上時，會顯示下列訊息。

   `Schema/Form Template for this adaptive form has been updated so please go to Authoring mode and rebase it with new version.`

![更新相關XFA後不同步適用性表單的警告](assets/dirtyaf.png)

會維持旗標，以指出適用性表單是否臟。 此資訊可在表單屬性頁面上，與表單中繼資料一併取得。 只有臟適用性表單，中繼資料屬性`Model Refresh`才會顯示`Recommended`值。

![指出自適性表單與XFA模型不同步](assets/model-refresh.png)
