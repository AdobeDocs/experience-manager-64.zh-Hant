---
title: 使用中繼資料設定檔，將預設中繼資料套用至資料夾中的所有資產
description: 了解資產的中繼資料設定檔。 了解如何建立中繼資料設定檔，並將其套用至資料夾資產。
contentOwner: AG
feature: 中繼資料
role: User,Admin
exl-id: a7b0f1d6-7deb-4565-8c7f-27cad7cd6bf8
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 15%

---

# 中繼資料設定檔 {#metadata-profiles}

中繼資料設定檔可讓您將預設中繼資料套用至資料夾內的資產。 建立中繼資料描述檔並將其套用至資料夾。 您隨後上傳至資料夾的任何資產都會繼承您在中繼資料設定檔中設定的預設中繼資料。

## 新增中繼資料設定檔 {#adding-a-metadata-profile}

1. 點選或按一下AEM標誌，並導覽至「**[!UICONTROL 工具>資產>中繼資料描述檔]**」，然後點選「**[!UICONTROL 建立]**」。
1. 輸入元資料配置檔案的標題，例如「示例元資料」，然後按一下&#x200B;**[!UICONTROL Submit]**。 將顯示元資料配置檔案的&#x200B;**[!UICONTROL 編輯表單]**。

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. 按一下元件，然後在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤中配置其屬性。 例如，按一下&#x200B;**[!UICONTROL Description]**&#x200B;元件並編輯其屬性。

   ![chlimage_1-401](assets/chlimage_1-481.png)

   編輯&#x200B;**[!UICONTROL Description]**&#x200B;元件的以下屬性：

   * **[!UICONTROL 欄位標籤]**:中繼資料屬性的顯示名稱。僅供使用者參考。
   * **[!UICONTROL 對應至屬性]**:此屬性的值提供儲存在儲存庫中的資產節點的相對路徑/名稱。值應一律以`./`開頭，因為它表示路徑位於資產節點下。

   ![chlimage_1-482](assets/chlimage_1-482.png)

   您為&#x200B;**[!UICONTROL Map to property]**&#x200B;指定的值會儲存為資產中繼資料節點下的屬性。 例如，如果您指定。`/jcr:content/metadata/dc:desc` AEM Assets會將值 **[!UICONTROL 對應至屬性]**，並將值儲 `dc:desc` 存在資產的中繼資料節點。

   * **[!UICONTROL 預設值]**:使用此屬性為元資料元件添加預設值。例如，如果您指定「My description」，則此值會指派給資產中繼資料節點的屬性`dc:desc`。

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >新增預設值至新中繼資料屬性（在中尚未存在）。 `/jcr:content/metadata` 節點)預設不會在資產的「屬性」頁面上顯示屬 **** 性及其值。若要在資產的[!UICONTROL 屬性]頁面上檢視新屬性，請修改對應的架構表單。

1. （可選）從&#x200B;**[!UICONTROL Build Form]**&#x200B;標籤向&#x200B;**[!UICONTROL Edit Form]**&#x200B;添加更多元件，並在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤中配置其屬性。 「生成表單」頁籤提供 **[!UICONTROL 以下屬性]** :

| 元件 | 屬性 |
|---|---|
| [!UICONTROL 區段標題] | 欄位標籤，<br>說明 |
| [!UICONTROL 單行文字] | 欄位標籤， <br>映射至屬性， <br>預設值 |
| [!UICONTROL 多值文字] | 欄位標籤， <br>映射至屬性， <br>預設值 |
| [!UICONTROL 數量] | 欄位標籤， <br>映射至屬性， <br>預設值 |
| [!UICONTROL 日期] | 欄位標籤， <br>映射至屬性， <br>預設值 |
| [!UICONTROL 標準標記] | 欄位標籤， <br>映射至屬性， <br>預設值， <br>說明 |

![chlimage_1-484](assets/chlimage_1-484.png)

1. 按一下&#x200B;**[!UICONTROL Done]**。 中繼資料設定檔會新增至&#x200B;**[!UICONTROL 中繼資料設定檔]**&#x200B;頁面中的設定檔清單。

   ![chlimage_1-485](assets/chlimage_1-485.png)

## 複製中繼資料設定檔 {#copying-a-metadata-profile}

1. 從&#x200B;**[!UICONTROL 中繼資料描述檔]**&#x200B;頁面中，選取描述檔以製作其復本。

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. 按一下工具列中的&#x200B;**[!UICONTROL 複製]**。
1. 在&#x200B;**[!UICONTROL 複製元資料配置檔案]**&#x200B;對話框中，輸入配置檔案新副本的標題。
1. 按一下&#x200B;**[!UICONTROL Copy]**。 配置檔案的副本顯示在&#x200B;**[!UICONTROL 元資料配置檔案]**&#x200B;頁中的配置檔案清單中。

   ![chlimage_1-487](assets/chlimage_1-487.png)

## 刪除中繼資料設定檔 {#deleting-a-metadata-profile}

1. 從&#x200B;**[!UICONTROL 中繼資料描述檔]**&#x200B;頁面中，選取要刪除的描述檔。

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. 按一下工具列中的&#x200B;**[!UICONTROL 刪除中繼資料描述檔]** 。
1. 在對話框中，按一下&#x200B;**[!UICONTROL Delete]**&#x200B;以確認刪除操作。 元資料設定檔會從清單中刪除。

## 將中繼資料設定檔套用至資料夾 {#applying-a-metadata-profile-to-folders}

將元資料配置檔案分配給資料夾時，任何子資料夾都會自動從其父資料夾繼承配置檔案。 這表示您只能將一個中繼資料描述檔指派給資料夾。 因此，請仔細考慮上傳、儲存、使用和封存資產的資料夾結構。

如果您指派不同的中繼資料描述檔給資料夾，新的描述檔會覆寫先前的描述檔。 先前的資料夾資產維持不變。 新設定檔會套用至稍後新增至資料夾的資產。

在用戶介面中，會以卡片名稱中顯示的設定檔名稱來表示已為其指派設定檔的資料夾。

![chlimage_1-489](assets/chlimage_1-489.png)

您可以將中繼資料設定檔套用至特定資料夾，或全域套用至所有資產。

### 將中繼資料設定檔套用至特定資料夾 {#applying-metadata-profiles-to-specific-folders}

您可以從「工具」菜單或者在資料夾內的「屬性」中，將元資料配置檔案應 **[!UICONTROL 用到資料夾]******。本節說明如何以兩種方式將中繼資料描述檔套用至資料夾。

已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。

#### 從設定檔使用者介面將中繼資料設定檔套用至資料夾 {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. 點選AEM標誌並導覽至「**[!UICONTROL 工具>資產>中繼資料描述檔]**」。
1. 選取您要套用至資料夾或多個資料夾的中繼資料設定檔。

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. 點選「**[!UICONTROL 將中繼資料描述檔套用至資料夾」]**，然後選取您要用來接收新上傳資產的資料夾或多個資料夾，並點選「**[!UICONTROL Done]**」。 已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。

#### 從屬性將元資料配置檔案應用到資料夾 {#applying-metadata-profiles-to-folders-from-properties}

1. 在左側導軌中，點選&#x200B;**[!UICONTROL Assets]**，然後導覽至您要套用中繼資料描述檔的資料夾。
1. 在資料夾中，點選核取標籤以選取，然後點選&#x200B;**[!UICONTROL 屬性]**。

1. 選擇&#x200B;**[!UICONTROL 元資料配置檔案]**&#x200B;頁簽，然後從下拉菜單中選擇配置檔案，然後按一下&#x200B;**[!UICONTROL 保存]**。

   ![chlimage_1-491](assets/chlimage_1-491.png)

   已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。

### 全域套用中繼資料設定檔 {#applying-a-metadata-profile-globally}

除了將設定檔套用至資料夾之外，您也可以全域套用一個設定檔，讓任何資料夾中上傳至AEM資產的任何內容都會套用選取的設定檔。 若要全域套用中繼資料設定檔，請遵循下列步驟：

1. 執行下列任一操作：

   * 導覽至`https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam`並套用適當的設定檔，然後點選或按一下「**[!UICONTROL 儲存]**」。

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * 導覽至CRXDE Lite至下列節點：`/content/dam/jcr:content`。 新增屬性`metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>`，然後點選&#x200B;**[!UICONTROL 「儲存全部」]**。

      ![chlimage_1-493](assets/chlimage_1-493.png)

## 從資料夾中移除中繼資料描述檔 {#removing-a-metadata-profile-from-folders}

從資料夾移除中繼資料描述檔時，任何子資料夾都會自動從其父資料夾移除描述檔。 不過，資料夾內發生的檔案處理仍維持不變。

您可以從「工具」功能表內的資料夾或在資料夾內的「屬性」中移除中繼資料描述檔，或從「屬性」中移除中繼資料描述檔，或從「屬性」中移除中繼資料描述檔，或從「工具 **[!UICONTROL 」功能表]** 移除中繼資料描述檔 ****。本節將說明如何以兩種方式從資料夾中移除中繼資料描述檔。

### 透過設定檔使用者介面，從資料夾移除中繼資料設定檔 {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

若要透過設定檔使用者介面從資料夾移除中繼資料設定檔，請執行下列步驟：

1. 點選AEM標誌並導覽至「**[!UICONTROL 工具>資產>中繼資料描述檔]**」。
1. 選取要從資料夾或多個資料夾中移除的中繼資料設定檔。
1. 點選&#x200B;**[!UICONTROL 從資料夾移除中繼資料描述檔]**&#x200B;並選取您要用來從中移除描述檔的資料夾或多個資料夾，然後點選&#x200B;**[!UICONTROL Done]**。

   您可以確認中繼資料描述檔不再套用至資料夾，因為資料夾名稱下方不再顯示該名稱。

### 透過「屬性」從資料夾移除中繼資料描述檔 {#removing-metadata-profiles-from-folders-via-properties}

1. 點選AEM標誌並導覽&#x200B;**[!UICONTROL Assets]**，然後導覽至您要移除中繼資料描述檔的資料夾。
1. 在資料夾中，點選核取標籤以選取，然後點選&#x200B;**[!UICONTROL 屬性]**。
1. 選擇&#x200B;**[!UICONTROL 元資料配置檔案]**&#x200B;頁簽，然後從下拉菜單中選擇&#x200B;**[!UICONTROL 無]**。 點選&#x200B;**[!UICONTROL 儲存]**。

已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。
