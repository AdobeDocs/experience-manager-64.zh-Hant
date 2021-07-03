---
title: 準備翻譯資產
description: 建立語言根資料夾，以準備轉譯多語言資產。
contentOwner: AG
feature: 項目，翻譯
role: User,Admin
exl-id: cc6c4f9e-8e22-4622-8b24-230ae258351c
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 2%

---

# 準備翻譯資產 {#preparing-assets-for-translation}

多語言資產是指具有多種語言的二進位檔、中繼資料和標籤的資產。 資產的二進位檔、中繼資料和標籤通常以一種語言存在，然後轉譯為其他語言，以用於多語言專案。

在Adobe Experience Manager(AEM)資產中，多語言資產會包含在資料夾中，每個資料夾都包含不同語言的資產。

每個語言資料夾都稱為語言副本。 語言副本的根資料夾（稱為語言根）標識語言副本中內容的語言。 例如， */content/dam/it*&#x200B;是義大利文語言副本的義大利文根。 語言副本必須使用[正確配置的語言根](preparing-assets-for-translation.md#creating-a-language-root)，以便在執行源資產翻譯時定位正確的語言。

您最初新增資產的語言副本是語言主要。 語言主要是翻譯成其他語言的源。

範例資料夾階層包含數種語言根：

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

執行下列步驟準備翻譯資產：

1. 建立語言主要的語言根。 例如，範例資料夾階層中英文副本的語言根目錄為`/content/dam/en`。 確保根據[建立語言根](preparing-assets-for-translation.md#creating-a-language-root)中的資訊正確配置語言根。

1. 將資產新增至您的語言主要版本。
1. 建立您需要語言副本的每種目標語言的語言根。

## 建立語言根 {#creating-a-language-root}

要建立語言根，請建立資料夾並使用ISO語言代碼作為Name屬性的值。 建立語言根後，您就可以在語言根的任何層級建立語言副本。

例如，範例階層的義大利語言副本的根頁面會以`it`作為Name屬性。 Name屬性會作為存放庫中資產節點的名稱，因此會決定資產的路徑。(`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. 在「資產」主控台中，按一下/點選「 **[!UICONTROL 建立]** 」，然後從 **[!UICONTROL 選單選擇「資料夾]** 」。

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. 在「名稱」欄位中，以`<language-code>`格式輸入國家/地區代碼。

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. 按一下或點選&#x200B;**[!UICONTROL 建立]**。 語言根目錄會在Assets主控台中建立。

## 查看語言根 {#viewing-language-roots}

觸控最佳化UI提供「參考」面板，顯示已在AEM Assets中建立的語言根清單。

1. 在Assets控制台中，選取您要建立語言副本的主要語言。
1. 按一下或點選GlobalNav表徵圖，然後選擇&#x200B;**[!UICONTROL References]**&#x200B;以開啟「Reference」窗格。

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. 在「參考」窗格中，按一下或點選「語言副本」****。 「語言復本」面板會顯示資產的語言復本。

   ![chlimage_1-123](assets/chlimage_1-123.png)
