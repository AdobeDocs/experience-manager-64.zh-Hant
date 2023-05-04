---
title: 大量中繼資料匯入和匯出
description: 本文說明如何大量匯入和匯出中繼資料。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 9%

---

# 大量中繼資料匯入和匯出 {#bulk-metadata-import-and-export}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager] Assets可讓您使用CSV檔案大量匯入資產中繼資料。 您可以匯入CSV檔案，針對最近上傳的資產或現有資產執行大量更新。 您也可以從協力廠商系統以CSV格式大量內嵌資產中繼資料。

## 匯入中繼資料 {#import-metadata}

中繼資料匯入為非同步，不會影響系統效能。 如果已勾選工作流程標幟，XMP回寫活動可能會導致資源密集型多個資產的中繼資料同步更新。 在精益伺服器使用期間規劃此類匯入，以防止對其他使用者的效能造成影響。

>[!NOTE]
>
>若要匯入自訂命名空間上的中繼資料，請先註冊命名空間。

若要大量匯入中繼資料，請執行下列步驟：

1. 導覽至「資產」使用者介面，然後點選/按一下 **[!UICONTROL 建立]** 的上界。
1. 從功能表選取 **[!UICONTROL 中繼資料]**.
1. 在 **[!UICONTROL 中繼資料匯入]** 頁面，點選/按一下 **[!UICONTROL 選擇檔案]**.  選取包含中繼資料的CSV檔案。
1. 確認CSV檔案包含下列參數：

   | 中繼資料匯入參數 | 說明 |
   |:---|:---|
   | [!UICONTROL 批次大小] | 要匯入中繼資料的批次中的資產數。 預設值為 50。最大值為100。 |
   | [!UICONTROL 欄位分隔符號] | 預設值為 `,`  — 逗號。 您可以指定任何其他字元。 |
   | [!UICONTROL 多值分隔符號] | 中繼資料值的分隔符號。 預設值為 `|`  — 管道。 |
   | [!UICONTROL 啟動工作流程] | 預設為False。 設為true時，和預設設定對 `DAM Metadata WriteBack Workflow` (會將中繼資料寫入二進位XMP資料)。 啟用工作流程會對系統造成效能影響。 |
   | [!UICONTROL 資產路徑欄名稱] | 定義含有資產的CSV檔案的欄名稱。 |

1. 點選/按一下 **[!UICONTROL 匯入]** 的上界。 匯入中繼資料後，通知會傳送至您的通知收件匣。 導覽至資產屬性頁面，並確認是否已為資產正確匯入中繼資料值。

若要在匯入中繼資料時新增日期和時間戳記，請使用 `YYYY-MM-DDThh:mm:ss.fff-00:00` 日期和時間的格式。 日期和時間以 `T`, `hh` 是24小時格式， `fff` 是納秒， `-00:00` 是時區偏移。 例如， `2020-03-26T11:26:00.000-07:00` 2020年3月26日為11:26:00.000 AM PST時間。

>[!CAUTION]
>
>如果日期格式不符 `YYYY-MM-DDThh:mm:ss.fff-00:00`，則不會設定日期值。 匯出的中繼資料CSV檔案的日期格式為 `YYYY-MM-DDThh:mm:ss-00:00`. 如果要導入它，請通過添加表示為的納秒值，將其轉換為可接受的格式 `fff`.

## 匯出存中繼資料 {#export-metadata}

大量匯出中繼資料的幾個使用案例為：

* 移轉資產時，在協力廠商系統中匯入中繼資料。
* 與更廣泛的專案團隊共用資產中繼資料。
* 測試或審核元資料以符合性。
* 將中繼資料外部化以進行個別本地化。

您可以將多個資產的中繼資料匯出為CSV格式。 中繼資料會以非同步方式匯出，不會影響系統的效能。 若要匯出中繼資料， [!DNL Experience Manager] 遍歷資產節點的屬性 `jcr:content/metadata` 及其子節點，並將中繼資料屬性匯出為CSV檔案。

若要大量匯出多個資產的中繼資料，請遵循下列步驟：

1. 選取包含您要匯出中繼資料之資產的資產資料夾。 從工具列中選取 **[!UICONTROL 匯出中繼資料]**.

1. 在 [!UICONTROL 中繼資料匯出] 對話框，指定CSV檔案的名稱。 若要匯出子資料夾中資產的中繼資料，請選取 **[!UICONTROL 在子資料夾中包含資產]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. 選取所需的選項。 提供檔案名稱，並視需要提供日期。
1. 在 **[!UICONTROL 要導出的屬性]**，指定您要匯出全部或特定屬性。 如果您選擇 **[!UICONTROL 選擇性]** 要匯出的屬性，新增所需的屬性。

1. 從工具列，點選/按一下 **[!UICONTROL 匯出]**. 訊息會確認中繼資料已匯出。 關閉訊息。

1. 開啟導出作業的收件箱通知。選擇作業，然後從工具 **[!UICONTROL 欄中]** ，按一下「開啟」。若要下載包含中繼資料的CSV檔案，請從工具列點選/按 **[!UICONTROL 一下「CSV下載]** 」。按一下&#x200B;**[!UICONTROL 關閉]**。

   ![csv_download](assets/csv_download.png)
