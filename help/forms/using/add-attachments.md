---
title: 添加附件
seo-title: Adding attachments
description: 在AEM Forms應用程式中，將像片和手寫筆記新增為工作的註解
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
exl-id: ad1cc63a-cf99-456b-8b83-0605fb3ac6ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# 添加附件 {#adding-attachments}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 在與AEM Forms工作流程伺服器(JEE上的AEM Forms)同步的表單中新增附件 {#adding-annotations}

AEM Forms應用程式可讓您將影像、草稿附註及文字附註附加至與AEM Forms JEE伺服器同步的表單。 如果您的表單是從AEM Forms工作流程伺服器載入，您的附件會新增至表單。 您可以點選附件按鈕 ![附件 — 應用程式](assets/attachments-app.png) 一起查看表單中的所有附件。 紅色通知指定表單中的附件數。 如果表單中沒有附件，則看不到紅色通知按鈕。 如果表單中沒有附件，當您點選「附件」按鈕時 ![atch](assets/attch.png)，您可以選擇附加照片或手寫。

您的選項為：

* **[!UICONTROL 圖庫]**:可讓您從儲存在裝置上的圖片新增圖片。

* **[!UICONTROL 相機]**:讓您拍照並將其新增至表單。

* **[!UICONTROL 附註]**:可讓您新增手寫或文字附註。 使用 ![手寫](assets/scribble.png) 添加手繪， ![鍵盤](assets/keyboard.png) 添加文本注釋。

>[!NOTE]
>
>其他AEM Forms應用程式使用者可看到由一個使用者新增的附件。 其他用戶無法刪除用戶添加的附件。

### 「附件」螢幕 {#the-attachments-screen}

要查看某個位置中的所有附件，請點選 ![附件 — 應用程式](assets/attachments-app.png). 您可以在此處添加、更名和刪除附件。

![一個位置中的所有附件](assets/attachments-screen.png)

您可以使用 **+** 按鈕，以附加另一圖片、手寫或文本。

### 添加照片 {#adding-a-photograph}

您可以使用行動裝置的相機或裝置中儲存的圖片，附加表單中的圖片。

1. 點選附件按鈕 ![atch](assets/attch.png) 在窗底。
1. 點選 **[!UICONTROL 圖庫]** 或 **[!UICONTROL 相機]** 顯示的快顯視窗中。
1. 根據您選取的選項，執行下列動作：

   1. 如果您選取 **[!UICONTROL 相機]**.

      拍照。 然後點選 **[!UICONTROL 使用]** ![use-pic](assets/use-pic.png) 按鈕。

      或點選 **[!UICONTROL 重奪]** ![重複](assets/retake.png) 按鈕重拍照片。

   1. 如果您選取 **[!UICONTROL 圖庫]**.

      裝置的影像瀏覽器彈出。 在裝置的圖片瀏覽器中，點選您要附加的圖片。

### 新增附註 {#adding-a-note}

此 **附註** 選項可讓您在表單中新增手繪手寫體和文字附件。

1. 點選附件按鈕 ![atch](assets/attch.png) 在窗底。
1. 點選 **[!UICONTROL 附註]** 顯示的快顯視窗中。
1. 在啟動的「附註」使用者介面中，擷取手繪文字。

   ![手寫介面](assets/scribble-ui.png)
   **圖：** *手寫*

   您可以在手寫介面中使用下列選項：

   * **[!UICONTROL 清除]**:清除螢幕。
   * **[!UICONTROL 完成]**:加上當前的手寫筆。
   * **[!UICONTROL 取消]**:放棄當前手寫體並退出手寫體用戶介面。
   * ![鍵盤](assets/keyboard.png):清除手寫字元，並讓您新增文字附註。

   ![AEM Forms應用程式鍵盤手寫](assets/keyboard-inapp.png)

## 不使用AEM Forms工作流程(OSGi上的AEM Forms)與AEM Forms伺服器同步的表單附件 {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

與AEM Forms OSGi伺服器同步的行動表單附件的運作方式與AEM Forms JEE伺服器類似。

從AEM Forms OSGi伺服器載入應用程式中的適用性表單不支援表單層級附件。 若要附加影像或文字附註，請在您編寫表單時啟用欄位層級附件。 從欄位上的元件瀏覽器拖放檔案附件元件。

在最適化表單中，您可以在記錄檔案(DoR)中檢視附加的檔案。 看， [為非XFA適用性表單產生記錄檔案](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
