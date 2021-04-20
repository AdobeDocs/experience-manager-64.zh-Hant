---
title: 整合AEM3D與Autodesk 3ds Max
seo-title: 將AEM3D與AutoDesk 3ds Max整合
description: 您可選擇將AEM3D與Autodesk 3ds Max軟體整合，以支援原生3ds Max檔案(.MAX)。 目前不支援以3ds Max進行演算。
seo-description: 您可選擇將AEM3D與Autodesk 3ds Max軟體整合，以支援原生3ds Max檔案(.MAX)。 目前不支援以3ds Max進行演算。
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
exl-id: 2edecd53-0a2d-44bb-968a-d988c780e142
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# 將AEM3D與Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}整合

>[!NOTE]
>
>此任務是可選的，僅與Windows相關。

您可選擇將AEM3D與Autodesk 3ds Max軟體整合，以支援原生3ds Max檔案(.MAX)。 目前不支援以3ds Max進行演算。

請參閱[進階組態設定](advanced-config-3d.md)。

另請參閱[將AEM3D與AutoDesk Maya](integrate-maya-with-3d.md)整合。

**若要將AEM3D與Autodesk 3ds Max整合**:

1. 在安裝AEM Author節點的相同伺服器上安裝Autodesk 3ds Max軟體。

   在安裝後，請確認您可以開啟和使用Maya，且沒有授權問題。

   >[!NOTE]
   >
   >為避免存取遭拒的問題，請使用與相同的管理員使用者帳戶安裝3ds MaxAEM。

1. 在3ds Max中，按一下&#x200B;**[!UICONTROL 自定義>插件管理器]**。

   找到`FBXMAX.DLU`並驗證其&#x200B;**[!UICONTROL Status]**&#x200B;是&#x200B;**[!UICONTROL loaded]**。

   關閉&#x200B;**[!UICONTROL 插件管理器]**&#x200B;對話框和3ds Max。

1. 更新轉換指令碼。

   使AEM用命令行指令碼調用3ds Max命令行實用程式`3dsmaxcmd.exe`。 如果安裝了3ds Max 2016以外的版本，或者將3ds Max安裝到非標準位置，或者安裝在不同的分區或驅動器上，則必須編AEM輯此指令碼。

   1. 開啟CRXDE Lite並導覽至`/libs/settings/dam/v3D/scripts/max`。
   1. 按兩下`export-fbx.bat`將其開啟。
   1. 視需要編輯指令碼的第一行，以反映`3dsmaxcmd.exe`實用程式的位置。 例如，如果使用3ds Max 2017，並將它安AEM裝在不同的磁碟驅動器上：

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. 在CRXDE Lite頁面的左上角附近，點選「Save All（全部保存）」。****

   在CRXDE Lite頁面的左上角附近，點選「Save All（全部保存）」。****

1. 移除工作資料夾（僅在先前嘗試擷取。MAX檔案時才必要）。

   1. 在CRXDE Lite中，導航到`/libs/settings/dam/v3D/Paths/maxWorkPath`。 預設情況下，此設定的值為`./MaxWork`，它相對於安裝根AEM資料夾。
   1. 登錄到伺服器本身，然後使用「檔案瀏覽器」導航到安AEM裝根資料夾。
   1. 刪除&#x200B;**[!UICONTROL MaxWork]**&#x200B;資料夾（包括其整個內容）（如果存在）。

      下次擷取。MAX檔案時，會自動重新建立資料夾。

1. 執行下列動作，以啟用3ds Max擷取：

   1. 在CRXDE Lite中，導航至`/libs/settings/dam/v3D/assetTypes/max`並將&#x200B;**[!UICONTROL Enabled]**&#x200B;屬性設定為true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. 在CRXDE Lite頁面的左上角附近，點選「Save All（全部保存）」。****

## 測試3D與AEMAutodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}的整合

1. 開啟AEM Assets，然後將位於`sample-3D-content/models`的`.max`檔案上傳至&#x200B;**[!UICONTROL test3d]**&#x200B;檔案夾。

   請注意，之前已下載sample-3D-content.zip，以驗證基本3D功能。

1. 返回&#x200B;**[!UICONTROL Card]**&#x200B;檢視並觀察已上傳資產上顯示的訊息橫幅。

   當3ds Max將原生3ds Max格式轉換為。FBX時，會顯示「轉換格式」橫幅。

1. 處理完成後，在&#x200B;**[!UICONTROL Detail]**&#x200B;視圖中開啟`logo-sphere.max`。

   「預覽」體驗與`logo_sphere.fbx`相同。
