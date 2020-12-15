---
title: 安裝和設定AEM 3D
seo-title: 安裝和設定AEM 3D
description: 瞭解如何安裝和設定AEM 3D
seo-description: 瞭解如何安裝和設定AEM 3D
uuid: a60732ff-fd66-4f29-b901-42a3cfd58b65
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5898d084-4b45-41bc-ad2e-2fcc65b0392c
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 0%

---


# 安裝和設定AEM 3D {#installing-and-configuring-aem-d}

>[!IMPORTANT]
>
>不再支援AEM 6.4中的AEM 3D。 Adobe建議您將[AEM中的3D資產功能當做雲端服務](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html)或[AEM 6.5.3或更新版本使用。](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

AEM 3D（3.0版）的安裝與設定涉及下列事項：

1. 安裝Autodesk® FBX® SDK程式庫。
1. 下載並安裝原生3D程式碼套件。
1. 設定3D資產擷取工作流程並重新啟動AEM。
1. 驗證AEM 3D的設定。

另請參閱[使用3D資產](assets-3d.md)。

如需先決條件、支援的瀏覽器和其他重要的發行資訊，請參閱[AEM 3D Assets發行說明](/help/release-notes/aem3d-release-notes.md)。

另請參閱[使用3D Sites元件](using-the-3d-sites-component.md)。

>[!NOTE]
>
>在下載並安裝3D套件之前，請確定您已成功安裝所有必備的AEM套件。 請參閱[AEM 3D發行說明。](install-config-3d.md)

## 安裝Autodesk FBX SDK庫{#installing-the-autodesk-fbx-sdk-library}

原生AEM 3D程式碼需要Autodesk FBX程式庫才能支援FBX檔案格式。 （Adobe目前無法轉散發此資料庫。）

另請參閱[高級配置設定](advanced-config-3d.md)。

1. 登入安裝AEM的主機。

   * 如果這是Windows Server部署，請以管理員身份登錄到伺服器。
   * 如果這是MAC或Windows案頭，請確定您擁有管理員權限。

1. 使用適合您作業系統的連結下載&#x200B;**FBX SDK 2016.1.2**&#x200B;版本

   * **Windows**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe)

   * **OS X**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz)

   * **Linux**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz)

1. 安裝FBX SDK:

   * Windows. 安裝至AEM所在的相同磁碟機。
   * 麥克。 安裝至AEM所在的相同分區。
   * Linux. 解壓下載的軟體包，然後按照`<yourFBXSDKpath>/Install_FbxFileSdk.txt`中的說明操作。 將SDK安裝至`/usr`。

## 下載並安裝原生3D程式碼套件{#downloading-and-installing-the-native-d-code-package}

>[!NOTE]
>
>在您繼續安裝和設定AEM 3D之前，Adobe建議您部署任何適用的Service Pack和其他相關功能套件。 請參閱[AEM 3D發行說明](/help/release-notes/aem3d-release-notes.md)。

另請參閱[高級配置設定](advanced-config-3d.md)。

**若要安裝原生3D程式碼套件**:

1. 執行下列任一項作業：

   * 如果這是Windows Server部署，請以管理員身份登錄到伺服器。
   * 如果這是Mac或Windows案頭，請確定您具有管理員權限。

1. 請確定您有可存取AEM的支援瀏覽器。

   請參閱[系統需求](/help/release-notes/aem3d-release-notes.md#system-requirements)。

1. 訪問[軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)。 找到`AEM-6.4-DynamicMedia-3D`功能套件的3.0.1版並下載。

1. 在AEM中，按一下「工具>管理>部署>封裝管理員&#x200B;**[!UICONTROL 」。]**

1. 將下載的功能套件上傳至AEM。 找到它，然後按一下&#x200B;**[!UICONTROL Install]**。

1. 在&#x200B;**[!UICONTROL 安裝軟體包]**&#x200B;對話框中，展開&#x200B;**高級設定**，然後將&#x200B;**[!UICONTROL 訪問控制處理]**&#x200B;設定為&#x200B;**合併**。
1. 按一下&#x200B;**[!UICONTROL Install]**&#x200B;開始安裝軟體包。

   檔案`sample-3D-content.zip`放在&#x200B;**[!UICONTROL Assets]**&#x200B;根資料夾中。 如需詳細資訊，請參閱[驗證AEM 3D](#validating-the-setup-of-aem-d)的設定。

## 設定3D資產擷取工作流程並重新啟動AEM {#configuring-the-d-asset-ingestion-workflow-and-restarting-aem}

**若要設定3D資產擷取工作流程**:

1. 在AEM中，按一下AEM標誌以存取全域導覽主控台，然後按一下「工具&#x200B;****」圖示並導覽至「工作流程>模型&#x200B;]**」。**[!UICONTROL 
1. 在「**[!UICONTROL 工作流模型]**」頁面上，將滑鼠指標暫留在「DAM更新資產&#x200B;]**」工作流程上，當出現複選標籤時，選取它。**[!UICONTROL 

1. 在工具欄上，按一下&#x200B;**[!UICONTROL 編輯]**。
1. 在&#x200B;**[!UICONTROL DAM Update Asset]**&#x200B;畫面的AEM浮動面板中，按一下「工作流程」右側的&#x200B;**[!UICONTROL Plus]**&#x200B;圖示以展開清單。 在清單中選擇&#x200B;**[!UICONTROL 處理步驟]**。
1. 將&#x200B;**[!UICONTROL 處理步驟]**&#x200B;拖放到工作流結束前&#x200B;**[!UICONTROL DAM更新資產工作流完成]**&#x200B;元件的工作流中。

   ![3d_process_step_underaem6-4](assets/3d_process_step_underaem6-4.png)

1. 按兩下新添加的進程步驟。
1. 在&#x200B;**[!UICONTROL 步驟屬性]**&#x200B;對話框的&#x200B;**[!UICONTROL Common]**&#x200B;頁籤的&#x200B;**[!UICONTROL Title]**&#x200B;欄位中，為進程輸入適當的說明，如`Process 3D content`。
1. 按一下&#x200B;**[!UICONTROL Process]**&#x200B;頁籤。

1. 從&#x200B;**[!UICONTROL Process]**&#x200B;下拉菜單中，選擇&#x200B;**[!UICONTROL Geometric 3D Object Service]** ，然後選擇&#x200B;**[!UICONTROL Handler Advance]**&#x200B;複選框。

   ![3d_install-process-steppropertiesdlg](assets/3d_install-process-steppropertiesdlg.png)

1. 在對話框的右上角附近，按一下複選標籤表徵圖以返回「DAM更新資產」頁。
1. 在&#x200B;**[!UICONTROL DAM更新資產]**&#x200B;頁面的右上角，按一下&#x200B;**[!UICONTROL 同步]**&#x200B;以儲存編輯的工作流程模型。
1. 重新啟動AEM。

   重新啟動後，您就可以上傳3D內容，並讓AEM處理它。

   繼續[驗證AEM 3D](#validating-the-setup-of-aem-d)的設定。

## 驗證AEM 3D {#validating-the-setup-of-aem-d}的設定

1. 在AEM中，按一下「工具>資產」，然後下載`sample-3D-content.zip`並展開下載的檔案。 ****（您現在可以在AEM中刪除`sample-3D-content.zip`。）

   請確定您位於&#x200B;**[!UICONTROL 卡片檢視]**&#x200B;中，以檢視其餘步驟的上傳和處理意見回應。

1. 建立名為`test3d`的資料夾以接收測試內容。
1. 將所有檔案從`sample-3D-content/images`上傳至`test3d`資料夾。
1. 等待上傳和處理完成。 您可能需要重新整理瀏覽器。

   將3個`.fbx`檔案從`sample-3D-content/`上傳至`test3d`資料夾。

   尚未上傳。ma模型檔案。

1. 在「資訊卡檢視」中，觀察3D資產資訊卡上顯示的訊息橫幅。

   每個資產會透過數個處理步驟進行。 當&#x200B;**[!UICONTROL 建立預覽……]**&#x200B;處理步驟完成，卡片會以縮圖影像更新。 完成最終處理後，橫幅會以&#x200B;**[!UICONTROL NEW]**&#x200B;指示器取代。

   >[!NOTE]
   >
   >在3D處理進行中時，預期CPU的使用率會非常高。 視可用的CPU容量而定，完成所有處理可能需要相當長的時間。

   ![screenshop_2017-01-2518-29-32](assets/screenshot_2017-01-2518-29-32.png)

1. 您現在將學習如何解決檔案相依性。

   在`stage-helipad.fbx`卡的&#x200B;**[!UICONTROL 未解決的依賴項]**&#x200B;標題上，按一下&#x200B;**[!UICONTROL 驚嘆號]**&#x200B;表徵圖以導航到資產的屬性並開啟&#x200B;**依賴項**&#x200B;頁籤。

   ![chlimage_1-372](assets/chlimage_1-372.png)

1. 按一下檔案名稱右側的&#x200B;**[!UICONTROL 資料夾／放大鏡]**&#x200B;圖示，以開啟資產瀏覽器並解析相依性，如下所示：

   ![chlimage_1-373](assets/chlimage_1-373.png)

1. 按一下「儲存」和「關閉」，分別完成資產處理並返回「卡片檢視」。**[!UICONTROL ****]**]****[!UICONTROL 
1. 處理完成時，您會在&#x200B;**[!UICONTROL 卡片檢視]**&#x200B;中看到下列內容：

   ![chlimage_1-374](assets/chlimage_1-374.png)

1. 在test3d頁面上，按一下`logo-sphere.fbx`卡片，以在&#x200B;**[!UICONTROL 詳細資料檢視]**&#x200B;中開啟模型。

   在logo-sphere.fbx頁面的右上角，按一下「舞台精選」圖示以展開下拉式功能表，然後選取`stage-spotlights.fbx`。

   ![chlimage_1-375](assets/chlimage_1-375.png)

1. 從&#x200B;**[!UICONTROL 舞台精選]**&#x200B;下拉式清單中，選取`stage-helipad.fbx`。

   使用滑鼠左鍵調整視圖。 背景和模型光源會改變以反映新舞台選取。

   ![chlimage_1-376](assets/chlimage_1-376.png)

## 設定對Adobe Dimension資產{#configuring-support-for-adobe-dimension-assets}的支援

>[!NOTE]
>
>此配置任務是可選的。

您可以選擇在AEM 3D中設定Adobe Dimension資產的支援。

您必須設定外部轉換服務，以允許在AEM中擷取、預覽和發佈Adobe Dimension 3D資產。 服務會從專屬的Adobe Dimension(`.dn`)格式轉換為glTF（格式化為`.glb`檔案）的變體，並與Dn資產一起儲存為轉譯。 `.glb`轉譯可用於在AEM Assets、Sites和Screens中以網路為基礎檢視3D資產，也可供下載，以便與協力廠商應用程式搭配使用。

>[!NOTE]
>
>轉換服務由Adobe在Amazon AWS中代管。 在正確設定服務後，上傳至AEM的`.dn`檔案會透過Amazon S3中的暫儲存存，安全地複製至轉換服務。 轉換結果會透過暫存S3儲存傳回至AEM。 所有傳輸和儲存都受到保護。 此外，內容在S3中持續存在，轉換服務只會短暫（通常不超過幾分鐘）。

**若要設定Adobe Dimension資產的支援**:

1. 請洽詢您的Adobe AEM客戶經理、布建專家或支援代表，以要求&#x200B;**AEM3D服務**&#x200B;的認證。

   >[!NOTE]
   >
   >每個組織只需要一組認證，不論其上安裝認證的AEM例項數為何。

1. 確認您收到下列資訊：

   * accountId
   * customerId
   * 密碼
   * identityPoolId
   * userPoolId
   * clientId

1. 以管理員身分，登入您要安裝認證的AEM作者例項，然後開啟&#x200B;**[!UICONTROL CRXDE Lite]**。
1. 在CRXDE Lite中執行下列動作，以設定新認證資訊：

   1. 導覽至`/libs/settings/dam/v3D/services/dncr`並將`clientId`屬性設為新值。
   1. 導覽至`/libs/settings/dam/v3D/services/aws`，並將`accountId`、`customerId`、`identityPoolId`和`userPoolId`屬性設定為新值。
   1. 將新口令值載入到`encryptedPassword`屬性中。 當您點選&#x200B;**[!UICONTROL 全部儲存]**&#x200B;時，此值會自動加密。
   1. 點選&#x200B;**[!UICONTROL 全部儲存]**，重新載入頁面，然後確認`encryptedPassword`屬性顯示的字串是大括弧所包含。 此外觀表示密碼已正確加密且安全。

1. 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中執行下列動作，指定`.glb`轉換轉譯的格式：

   1. 導覽至&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中的`/libs/settings/dam/v3D/services/dncr`。
   1. 將`outputFormat`屬性設為`Dn`或`generic`。

      設為`Dn`時，`.glb`轉換會包含Adobe專用的擴充功能，例如IBL光源，以便在AEM中檢視Dn資產時提供最佳品質。 不過，轉換的。glb轉譯可能無法在協力廠商應用程式中正常顯示。

      當設為`generic`時，`.glb`轉譯是一般的，不含Adobe專用的副檔名。 此設定可讓它用於協力廠商應用程式，而使用AEM 3D檢視器進行檢視的視覺效果將會不佳。

1. 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中執行以下操作，以啟用Dn檔案格式：

   1. 導航到 `/libs/settings/dam/v3D/assetTypes/Dn`.
   1. 將`Enabled`屬性設為true。

1. 通過執行以下操作來驗證配置：

   1. 開啟AEM資產。
   1. 將`logo_sphere.dn`上載到`test3d`資料夾。 檔案位於`sample-3D-content/models`中。

      請注意，`sample-3D-content.zip`之前是為了驗證基本3D功能而下載的。
   1. 返回&#x200B;**[!UICONTROL 卡片檢視]**，並觀察已上傳資產上顯示的訊息橫幅。 **[!UICONTROL 轉換格式……]**&#x200B;橫幅會在轉換程式進行時顯示。
   1. 完成所有處理後，請在&#x200B;**[!UICONTROL 詳細資料檢視]**&#x200B;中開啟資產，以確認已轉換的資產已正確顯示且檢視器的導覽控制項可用。

   ![image2018-11-2_15-51-19](assets/image2018-11-2_15-51-19.png)

   如果在10-15分鐘後，**[!UICONTROL 卡片檢視]**&#x200B;的Dn資產上顯示「處理錯誤」，轉換失敗。

   如果出現這種情況，您可以執行下列動作來疑難排解轉換問題：

   * 刪除資產，然後再次上傳它。
   * 請確定您已正確設定&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中的所有設定參數。
   * 驗證沒有防火牆阻止對轉換服務和AWS端點的訪問。
