---
title: 啟用表單入口網站元件
seo-title: Enabling forms portal components
description: 現成可用的Forms Portal元件已停用。 啟用Document Services和Document Services述詞群組，以啟用Forms Portal元件。
seo-description: Out of the box, Forms Portal components are disabled. Enable Document Services and Document Services Predicates groups to enable Forms Portal components.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Forms Portal
exl-id: 01c5eb6b-b097-4354-84b2-8bee7b7626f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 1%

---

# 啟用表單入口網站元件 {#enabling-forms-portal-components}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

現成可用的表單入口網站元件無法使用。 若要讓元件顯示在AEM sidekick的可用元件清單中，請執行下列步驟：

1. 登入您網站的製作例項，並開啟AEM Sites頁面。

1. 對於使用靜態模板的頁面，請執行以下步驟：

   1. 在頁首中，點選 ![畫布下拉式清單](assets/canvas-drop-down.png) > **設計** 以在「設計」模式中開啟頁面。
   1. 點選任何元件（含藍色邊框），然後點選 ![欄位層級](assets/field-level.png) 選擇包含當前元件的段落系統。
   1. 在段落系統中，點選 ![settings_icon](assets/settings_icon.png) 開啟段落系統的「編輯」(Edit)對話框。
   1. 從 **[!UICONTROL 允許的元件]**，啟用複選框 **[!UICONTROL 檔案服務]** 和 **[!UICONTROL 文檔服務謂詞]** 元件。 點選 **[!UICONTROL 確定]**.

1. 對於使用動態範本的頁面，請執行下列步驟：

   1. 在頁首中，點選 ![屬性](assets/properties.png) > **編輯範本** 以開啟頁面的範本。
   1. 點選 **版面容器** 點選 ![FeedManagement](assets/FeedManagement.png). 在 **允許的元件** 頁簽，啟用 **文檔服務和文檔服務謂詞** 選項，然後點選 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>您也可以選取元件，從這些類別中啟用特定元件。 如需元件及其使用方式的詳細資訊，請參閱 [建立表單入口網站頁面](/help/forms/using/creating-form-portal-page.md) 和 [在頁面中內嵌連結元件](/help/forms/using/embedding-link-component-page.md).

現在，元件瀏覽器中提供了文檔服務和文檔服務謂詞元件類別。 所有使用相同範本的頁面都會啟用元件。

## 相關文章

* [啟用表單入口網站元件](/help/forms/using/enabling-forms-portal-components.md)
* [建立表單入口網站頁面](/help/forms/using/creating-form-portal-page.md)
* [使用API列出網頁上的表單](/help/forms/using/listing-forms-webpage-using-apis.md)
* [使用草稿和提交元件](/help/forms/using/draft-submission-component.md)
* [自訂草稿和已提交表單的儲存](/help/forms/using/draft-submission-component.md)
* [將草稿和提交元件與資料庫整合的範例](/help/forms/using/integrate-draft-submission-database.md)
* [自訂表單入口網站元件的範本](/help/forms/using/customizing-templates-forms-portal-components.md)
* [在入口網站發佈表單簡介](/help/forms/using/introduction-publishing-forms.md)
