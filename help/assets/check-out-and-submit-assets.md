---
title: 簽入和簽出您的數字資產以進行編輯
description: 了解如何簽出要編輯的資產，以及在變更完成後重新簽入。
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0c79ed42-0acd-426e-8e14-412bb4117585
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 4%

---

# 資產中的簽入和簽出檔案 {#check-in-and-check-out-files-in-assets}

Adobe Experience Manager Assets可讓您簽出資產以進行編輯，並在您完成變更後重新簽入。 結帳資產後，您只能編輯、注釋、發佈、移動或刪除資產。 簽出資產會鎖定資產。 在您將資產簽回[!DNL Experience Manager]資產之前，其他使用者無法對資產執行任何這些操作。 不過，他們仍可以變更鎖定資產的中繼資料。

若要簽出或簽入資產，您需要這些資產的「寫入」存取權。

此功能可協助防止其他使用者覆寫作者所做的變更，讓多位使用者共同合作編輯團隊間的工作流程。

## 結帳資產 {#checking-out-assets}

1. 從資產UI中，選取您要結帳的資產。 您也可以選取多個要結帳的資產。

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. 在工具列中，按一下/點選&#x200B;**[!UICONTROL Checkout]**&#x200B;圖示。

   ![chlimage_1-469](assets/chlimage_1-469.png)

   請注意，**[!UICONTROL Checkout]**&#x200B;圖示會切換為開啟鎖的&#x200B;**[!UICONTROL Checkin]**&#x200B;圖示。

   ![chlimage_1-470](assets/chlimage_1-470.png)

   若要確認其他使用者是否可以編輯您簽出的資產，請以其他使用者身分登入。 簽出的資產縮圖上會顯示鎖定表徵圖。

   ![chlimage_1-471](assets/chlimage_1-471.png)

   選取資產。 請注意，工具列不會顯示任何選項，讓您編輯、注釋、發佈或刪除資產。

   ![chlimage_1-472](assets/chlimage_1-472.png)

   不過，您可以按一下/點選&#x200B;**[!UICONTROL 檢視屬性]**&#x200B;圖示，以編輯鎖定資產的中繼資料。

1. 按一下/點選「編輯」圖示，以在編輯模式中開啟資產。

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. 編輯資產並儲存變更。 例如，裁切影像並儲存。

   ![chlimage_1-474](assets/chlimage_1-474.png)

   您也可以選擇為資產加上注釋或發佈。

1. 從「資產」UI中選取已編輯的資產，然後按一下/點選工具列中的「 **[!UICONTROL 登入]** 」圖示。

   ![chlimage_1-475](assets/chlimage_1-475.png)

   已修改的資產已簽入[!DNL Assets]，可供其他使用者編輯。

## 強制簽入 {#forced-check-in}

管理員可以簽入其他用戶簽出的資產。

1. 以管理員身分登入[!DNL Assets]。
1. 從「資產」UI中，選取一或多個已由其他使用者簽出的資產。

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. 在工具列中，按一下/點選&#x200B;**[!UICONTROL 釋放鎖定]**&#x200B;圖示。 資產會重新簽入，供其他使用者編輯。

   ![chlimage_1-477](assets/chlimage_1-477.png)
