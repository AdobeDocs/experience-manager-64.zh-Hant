---
title: 在AEM Forms應用程式中使用自動儲存
seo-title: Using autosave in AEM Forms app
description: 了解如何使用AEM Forms應用程式中的自動儲存功能，以避免資料遺失。
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# 在AEM Forms應用程式中使用自動儲存 {#using-autosave-in-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

使用者在Adobe Experience Manager Forms應用程式中輸入資料時，自動儲存功能會定期儲存資料。 AEM Forms應用程式中的自動儲存功能可協助您避免意外關閉應用程式時遺失資料。

您的應用程式可能會意外關閉：

* 如果設備因電池不足而關閉
* 如果使用者殺了應用程式
* 如果發生意外的當機

您可以指定應用程式儲存輸入資料的間隔。

>[!NOTE]
>
>審慎選取自動儲存頻率。 頻繁的自動保存操作可能會對設備的效能產生明顯的影響。

執行下列步驟以使用AEM Forms應用程式中的自動儲存功能：

1. 登入應用程式，並導覽至 **[!UICONTROL 設定>一般]**.
1. 在「一般」畫面中，使用 **[!UICONTROL 自動儲存頻率]** 選項，以選取您希望應用程式儲存輸入資料的間隔。
   [ ![設定自動儲存頻率](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. 當您重新啟動應用程式並以相同的使用者登入時，系統會提示您使用「復原未儲存的任務」對話方塊還原您的任務。 按一下 **[!UICONTROL 確定]** 在「恢復未保存的任務」對話框中，繼續使用已保存的任務。 您可以按一下 **[!UICONTROL 取消]** 刪除與上次觸發的自動儲存對應的已儲存資料，然後開始處理新任務。

   當您按一下 **[!UICONTROL 確定]**，則任務會以應用程式當機前所觸發之最新自動儲存對應的資料還原。 它包括表單資料和與任務關聯的所有附件。
   [ ![正在恢復任務&#x200B;](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**答：** 在制表 **B.** 應用被強制關閉 **C.** 「恢復未保存的任務」對話框重新啟動應用 **D.** 以原始資料還原的表單
