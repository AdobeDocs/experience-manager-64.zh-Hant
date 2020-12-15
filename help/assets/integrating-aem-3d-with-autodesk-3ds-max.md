---
title: 整合AEM 3D與Autodesk 3ds Max
seo-title: 整合AEM 3D與AutoDesk 3ds Max
description: 您可選擇將AEM 3D與Autodesk 3ds Max軟體整合，以支援原生3ds Max檔案(.MAX)。 目前不支援以3ds Max進行演算。
seo-description: 您可選擇將AEM 3D與Autodesk 3ds Max軟體整合，以支援原生3ds Max檔案(.MAX)。 目前不支援以3ds Max進行演算。
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# 將AEM 3D與Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}整合

>[!NOTE]
>
>此任務是可選的，僅與Windows相關。

您可選擇將AEM 3D與Autodesk 3ds Max軟體整合，以支援原生3ds Max檔案(.MAX)。 目前不支援以3ds Max進行演算。

請參閱[進階組態設定](advanced-config-3d.md)。

另請參閱[將AEM 3D與AutoDesk Maya](integrate-maya-with-3d.md)整合。

**若要將AEM 3D與Autodesk 3ds Max整合**:

1. 在安裝AEM Author節點的相同伺服器上安裝Autodesk 3ds Max軟體。

   在安裝後，請確認您可以開啟和使用Maya，且沒有授權問題。

   >[!NOTE]
   >
   >若要避免存取遭拒的問題，請使用與AEM相同的管理員使用者帳戶安裝3ds Max。

1. 在3ds Max中，按一下&#x200B;**[!UICONTROL 自定義>插件管理器]**。

   找到`FBXMAX.DLU`並驗證其&#x200B;**[!UICONTROL Status]**&#x200B;是&#x200B;**[!UICONTROL loaded]**。

   關閉&#x200B;**[!UICONTROL 插件管理器]**&#x200B;對話框和3ds Max。

1. 更新轉換指令碼。

   AEM使用命令列指令碼來叫用3ds Max命令列公用程式`3dsmaxcmd.exe`。 如果您安裝的版本不是3ds Max 2016，或是將3ds Max安裝至非標準位置，或是將AEM安裝在不同的分區或磁碟機，您必須編輯此指令碼。

   1. 開啟CRXDE Lite並導覽至`/libs/settings/dam/v3D/scripts/max`。
   1. 按兩下`export-fbx.bat`將其開啟。
   1. 視需要編輯指令碼的第一行，以反映`3dsmaxcmd.exe`實用程式的位置。 例如，如果使用3ds Max 2017，而AEM則安裝在不同的磁碟機上：

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. 在「CRXDE Lite」頁面的左上角附近，點選「Save All（全部保存）」。****

   在「CRXDE Lite」頁面的左上角附近，點選「Save All（全部保存）」。****

1. 移除工作資料夾（僅在先前嘗試擷取。MAX檔案時才必要）。

   1. 在CRXDE Lite中，導覽至`/libs/settings/dam/v3D/Paths/maxWorkPath`。 依預設，此設定的值為`./MaxWork`，與AEM安裝根資料夾相關。
   1. 登入伺服器本身，並使用檔案總管導覽至AEM安裝根資料夾。
   1. 刪除&#x200B;**[!UICONTROL MaxWork]**&#x200B;資料夾（包括其整個內容）（如果存在）。

      下次擷取。MAX檔案時，會自動重新建立資料夾。

1. 執行下列動作，以啟用3ds Max擷取：

   1. 在CRXDE Lite中，導覽至`/libs/settings/dam/v3D/assetTypes/max`，並將&#x200B;**[!UICONTROL Enabled]**&#x200B;屬性設為true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. 在「CRXDE Lite」頁面的左上角附近，點選「Save All（全部保存）」。****

## 測試AEM 3D與Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}的整合

1. 開啟「AEM資產」，然後將位於`sample-3D-content/models`的`.max`檔案上傳至&#x200B;**[!UICONTROL test3d]**&#x200B;檔案夾。

   請注意，之前已下載sample-3D-content.zip，以驗證基本3D功能。

1. 返回&#x200B;**[!UICONTROL Card]**&#x200B;檢視並觀察已上傳資產上顯示的訊息橫幅。

   當3ds Max將原生3ds Max格式轉換為。FBX時，會顯示「轉換格式」橫幅。

1. 處理完成後，在&#x200B;**[!UICONTROL Detail]**&#x200B;視圖中開啟`logo-sphere.max`。

   「預覽」體驗與`logo_sphere.fbx`相同。

