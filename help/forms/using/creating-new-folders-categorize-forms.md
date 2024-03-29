---
title: 建立新資料夾以對表單進行分類
seo-title: Create new folders to categorize forms
description: 使用資料夾來組織表單範本、PDF、資源和最適化表單。
seo-description: Use folders to organize your form templates, PDFs, resources, and adaptive forms.
uuid: 63fcb807-c9cf-49ae-ad69-6b1187543470
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 2a8f4380-8d0f-4354-b2da-4e0c02a545e3
role: Admin
exl-id: 6c989701-10c7-466e-b3e5-008a6d377574
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# 建立新資料夾以對表單進行分類 {#create-new-folders-to-categorize-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以使用資料夾來更妥善地組織資產。 由於AEM Forms支援多種類型的資產(表單範本、PDF、檔案、資源和最適化表單，以及各種中繼資料)，因此您可以使用資料夾來根據所需的條件對表單進行分類。

AEM Forms可讓您變更資料夾的標題。 標題與儲存庫中儲存資料夾的節點名稱不同。 標題會保留為資料夾的中繼資料。 如果您變更資料夾的標題，資料夾內任何資產的路徑都不受影響。

## 建立資料夾 {#create-a-folder}

您可以透過下列其中一種方式，在AEM Forms中建立資料夾：

* 上傳包含所需資料夾結構中資產的ZIP檔案(請參閱 [在AEM Forms中取得XDP和PDF檔案](/help/forms/using/get-xdp-pdf-documents-aem.md))

* 建立新的空資料夾

1. 登入AEM Forms使用者介面： `https://<server>:<port>/aem/forms.html`.
1. 導覽至您要建立資料夾的位置。
1. 按一下 ![aem6forms_add](assets/aem6forms_add.png) 圖示，然後選取 **[!UICONTROL 建立資料夾]**.

1. 輸入以下詳細資訊：

   * **標題：** 資料夾的顯示名稱
   * **名稱：** *（強制）* 要在儲存庫中儲存資料夾的節點名稱

   >[!NOTE]
   >
   >依預設，名稱欄位的值會自動從標題填入。 名稱只能包含英數字元，或連字型大小(-)和底線(_)特殊字元。 標題中輸入的任何其他特殊字元都會自動以連字型大小取代，系統會提示您確認新名稱。 您可以選擇繼續使用建議的名稱或進一步編輯它。

1. 按一下 **[!UICONTROL 提交].**

   資產清單中的目前位置會顯示帶有您所定義標題的新資料夾。

   如果資料夾存在並指定名稱，則提交會失敗，並出現錯誤。 您可以將游標移至錯誤上以檢視錯誤訊息 ![aem6forms_error_alert](assets/aem6forms_error_alert.png) 表徵圖，顯示在名稱欄位旁邊。

### 編輯資料夾標題 {#edit-the-folder-title-br}

1. 選擇要編輯其標題的資料夾。
1. 按一下編輯 ![aem6forms_edit](assets/aem6forms_edit.png) 圖示。
1. 輸入新標題。 文字欄位已預先填入資料夾標題的目前值。 您可以將其變更為新值。
1. 按一下 **[!UICONTROL 提交].**
