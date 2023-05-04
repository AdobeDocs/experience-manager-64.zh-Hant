---
title: AEM Forms JEE修補程式安裝程式
description: AEM Forms JEE修補程式安裝程式
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
exl-id: ce5300ce-03f4-4e7b-bc5b-01a9968ebe06
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 23%

---

# AEM Forms JEE修補程式安裝程式 {#aem-forms-jee-patch-installer}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>[聯絡支援](https://www.adobe.com/tw/account/sign-in.supportportal.html) 以獲取更多資訊或獲取修補程式。

## 關於修補程式安裝程式 {#about-the-patch-installer}

AEM 6.4 Forms JEE修補程式安裝程式包含在此修補程式發行前，AEM 6.4 Forms JEE所有元件的所有已修正問題。 查看最新  [Cumulative Fix Pack發行說明](cfp-release-notes.md) 以取得已修正問題的完整清單。

## 安裝修補程式的必要條件 {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## 安裝和配置修補程式 {#installing-and-configuring-the-patch}

1. 備份&lt;*AEM_forms_root*>/部署資料夾。 如果決定解除安裝快速修正，則此為必要操作。
1. 停止應用程式伺服器。
1. 將修補程式安裝程式封存檔案解壓縮至硬碟。
1. 在根據您使用的作業系統命名的目錄中：

   * **Windows**
在複製安裝程式的硬碟上，導覽至安裝媒體或資料夾上的適當目錄，然後按兩下 
`aemforms64_cfp_install.exe` 檔案。

      * （Windows 32位元） `Windows\Disk1\InstData\VM`
      * （Windows 64位元） `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux、Solaris、AIX**
導覽至適當的目錄，然後在命令提示字元中輸入 
`./aem64_cfp_install.bin`。

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   這會啟動安裝精靈，引導您完成安裝。

1. 在 Introduction 面板上，按一下 **[!UICONTROL Next]**。
1. 在「選擇安裝資料夾」螢幕上，驗證針對現有安裝顯示的預設位置是否正確，或按一下 **[!UICONTROL 瀏覽]** 要選擇安裝AEM表單的替代資料夾，請按一下 **[!UICONTROL 下一個]**.

1. 閱讀 Quick Fix Patch Summary 資訊，然後按一下 **[!UICONTROL Next]**。
1. 閱讀 Pre-Installation Summary 資訊，然後按一下 **[!UICONTROL Install]**。
1. 安裝完成後，按一下**[!UICONTROL 下一個]**：將快速修復更新應用於已安裝的檔案。
1. [僅限Windows] 執行下列步驟之一：

   * 在按一下「完成」之前，取消選擇「啟動配置管理器」選項。 稍後使用 `ConfigurationManager.bat` 位於 `[aem-forms root]\configurationManager\bin`. 使用 `ConfigurationManager.bat` 有助於避免手動更新.lax檔案中的axis.jar名稱
   * 在按一下「完成」之前，取消選擇「啟動配置管理器」選項。 在運行配置管理器之前，使用 **ConfigurationManager.exe** 或 **ConfigurationManager_IPv6.exe**，導覽至 *&lt;aemforms_install_dir>\configurationManager\bin* 目錄和更新 **axis.jar** to **axis-1.4.1.1.jar** 在下列檔案中：

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. （僅基於Unix）預設選中「啟動配置管理器」複選框。 按一下 **[!UICONTROL Done]**，執行 Configuration Manager。

   若要稍後執行 Configuration Manager，請取消選取 Start Configuration Manager 選項，再按一下 Done。您稍後可以使用 `[AEM_forms_root]/configurationManager/bin` 目錄。

1. 根據您的應用程式伺服器，選擇以下文檔之一，然後按照 *設定和部署AEM表單* 區段。

   * [安裝和部署適用於JBoss的AEM表單](http://www.adobe.com/go/learn_aemforms_installJBoss_64_tw)
   * [安裝和部署AEM forms for WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64_tw)
   * [安裝和部署AEM forms for WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64_tw)

1. （僅限JBoss）安裝修補程式並配置伺服器後，刪除JBoss應用程式伺服器的tmp和工作目錄。

## 部署後配置 {#post-deployment-configurations}

### SAML設定 {#saml-configurations}

如果您已設定SAML驗證，且遇到大型IDP中繼資料的問題，安裝修補程式後請執行下列作業：

1. 在應用程式伺服器中設定以下系統屬性：\
   `um.saml.enable.large.xml=true`

1. 重新啟動伺服器。
1. 刪除現有的SAML驗證提供者，並如SAML設定所述，為現有網域再次新增這些提供者。

## 受影響的模組 {#impacted-modules}

* 文件服務
* 文件安全性
* Foundation JEE
* PDFG 服務

[聯絡支援](https://www.adobe.com/tw/account/sign-in.supportportal.html)
