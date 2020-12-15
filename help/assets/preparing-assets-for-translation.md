---
title: 準備翻譯資產
description: 建立語言根資料夾，以準備翻譯多語言資產。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 77c62a8f2ca50f8aaff556a6848fabaee71017ce
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 2%

---


# 準備翻譯資產{#preparing-assets-for-translation}

多語言資產是指包含多種語言的二進位檔、中繼資料和標籤的資產。 一般而言，資產的二進位檔、中繼資料和標籤都以一種語言存在，然後會翻譯成其他語言，以用於多語言專案。

在Adobe Experience Manager(AEM)Assets中，多語言資產會包含在檔案夾中，其中每個檔案夾都包含不同語言的資產。

每個語言資料夾都稱為語言副本。 語言副本的根資料夾（稱為語言根目錄）標識語言副本中內容的語言。 例如，*/content/dam/it*&#x200B;是義大利文語言副本的義大利文根目錄。 語言副本必須使用[正確配置的語言root](preparing-assets-for-translation.md#creating-a-language-root)，以便在執行源資產翻譯時定位正確的語言。

您原本新增資產的語言副本是主要語言。 語言主要是翻譯成其他語言的源。

範例資料夾階層包含數種語言根目錄：

```java
/content
    /- dam
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

執行下列步驟以準備要翻譯的資產：

1. 建立您的語言主要語言的語言根目錄。 例如，範例檔案夾階層中英文版副本的語言根目錄為`/content/dam/en`。 確保根據[建立語言根目錄](preparing-assets-for-translation.md#creating-a-language-root)中的資訊正確配置語言根目錄。

1. 將資產新增至您的語言主要版本。
1. 建立您需要語言副本的每種目標語言的語言根目錄。

## 建立語言根{#creating-a-language-root}

要建立語言根目錄，請建立資料夾並使用ISO語言代碼作為「名稱」屬性的值。 建立語言根目錄後，可以在語言根目錄的任何級別建立語言副本。

例如，範例階層的義大利文語言副本的根頁面具有`it`作為Name屬性。 Name屬性用作儲存庫中資產節點的名稱，因此確定資產的路徑。(`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. 在「資產」主控台中，按一下/點選「 **[!UICONTROL 建立]** 」，然後從 **[!UICONTROL 選單選擇「資料夾]** 」。

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. 在「名稱」欄位中，以`<language-code>`格式輸入國家代碼。

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. 按一下或點選「**[!UICONTROL 建立]**」。 語言根目錄是在「資產」主控台中建立。

## 查看語言根{#viewing-language-roots}

觸控最佳化的UI提供「參考」面板，顯示已在AEM Assets中建立的語言根目錄清單。

1. 在「資產」主控台中，選取您要建立語言副本的語言主要版本。
1. 按一下或點選GlobalNav表徵圖，然後選擇&#x200B;**[!UICONTROL References]**&#x200B;以開啟「Reference（參考）」窗格。

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. 在「參考」窗格中，按一下或點選「語言副本」。 ****「語言副本」面板會顯示資產的語言副本。

   ![chlimage_1-123](assets/chlimage_1-123.png)

