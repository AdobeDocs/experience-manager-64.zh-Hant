---
title: AEM Forms JEE修補程式安裝程式
description: 'null'
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 610e9a54adad3abdfecb8b2c4da67d677f75175e
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---


# AEM Forms JEE修補程式安裝程式 {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[如需詳細資訊](https://www.adobe.com/account/sign-in.supportportal.html) ，或聯絡支援以取得修補程式。

## 關於修補程式安裝程式 {#about-the-patch-installer}

AEM 6.4 Forms JEE修補程式安裝程式包含AEM 6.4 Forms JEE所有元件的所有已修正問題，直到本修補程式發行為止。 如需已修 [正問題的完整清單，請參閱最新的Cumulative Fix Pack發行說明](cfp-release-notes.md) 。

## 安裝修補程式的先決條件 {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## 安裝和配置修補程式 {#installing-and-configuring-the-patch}

1. 備份&lt;*AEM_forms_root*>/deploy資料夾。 如果您決定解除安裝快速修正，則此為必要項目。
1. 停止應用程式伺服器。
1. 將修補程式安裝程式封存檔案解壓縮至硬碟。
1. 在根據您使用的作業系統命名的目錄中：

   * **Windows**&#x200B;導覽至您硬碟上複製安裝程式之安裝媒體或資料夾的適當目錄，然後按兩下 
`aemforms64_cfp_install.exe` 檔案。

      * （Windows 32位元） `Windows\Disk1\InstData\VM`
      * （Windows 64位元） `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux、Solaris、AIX導**&#x200B;航到相應的目錄，然後從命令提示符鍵入 
`./aem64_cfp_install.bin`。

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   這會啟動安裝精靈，引導您完成安裝。

1. 在「簡介」面板上，按一下「 **[!UICONTROL 下一步]**」。
1. 在「選擇安裝檔案夾」畫面上，確認顯示的預設位置對您現有的安裝正確無誤，或按一下「 **[!UICONTROL Browse]** 」（瀏覽）以選取安裝AEM表單的替代檔案夾，然後按一下「 **[!UICONTROL Next」（下一步）]**。

1. 閱讀「快速修復補丁程式摘要」資訊，然後按一下「 **[!UICONTROL 下一步]**」。
1. 閱讀「安裝前摘要」資訊，然後按一下「 **[!UICONTROL 安裝]**」。
1. 安裝完成後，按一下「**[!UICONTROL 下一]**」，將快速修正更新套用至您安裝的檔案。
1. [僅Windows] 執行下列步驟之一：

   * 在按一下「完成」之前，請取消選擇「啟動配置管理器」選項。 稍後使用中的檔案運行 `ConfigurationManager.bat` 配置管理器 `[aem-forms root]\configurationManager\bin`。 使用 `ConfigurationManager.bat` 有助於避免手動更新。lax檔案中的axis.jar名稱
   * 在按一下「完成」之前，請取消選擇「啟動配置管理器」選項。 在使用 **ConfigurationManager.exe或** ConfigurationManager_IPv.exe運行配置管理器之前，請導航至 **&lt;AORMS_Install_>並更新**\configurationManager\binAxis. ********** Jar目錄至JarAxis.4.1.1.1.1Jar檔案，並在以下檔案中：

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. （僅基於Unix）預設選中「啟動配置管理器」(Start Configuration Manager)複選框。 按一下 **[!UICONTROL 完成]** ，運行配置管理器。

   若要稍後運行Configuration Manager，請在按一下「完成」之前取消選擇「啟動配置管理器」選項。 您稍後可以使用目錄中的相應指令碼啟動Configuration Manager `[AEM_forms_root]/configurationManager/bin` 。

1. 視您的應用程式伺服器而定，選擇下列其中一份檔案，並依照「設定和部署AEM表 *單」區段中的指示* 。

   * [安裝和部署JBoss的AEM表單](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [安裝和部署適用於WebSphere的AEM表單](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [安裝和部署適用於WebLogic的AEM表單](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. （僅限JBoss）安裝修補程式並配置伺服器後，刪除JBoss應用程式伺服器的tmp和工作目錄。

## 部署後配置 {#post-deployment-configurations}

### SAML設定 {#saml-configurations}

如果您已設定SAML驗證，並且遇到大型IDP中繼資料的問題，請在安裝修補程式後執行下列動作：

1. 在應用程式伺服器中設定以下系統屬性：\
   `um.saml.enable.large.xml=true`

1. 重新啟動伺服器。
1. 刪除現有的SAML驗證提供者，並依SAML設定中所述，重新新增現有網域的提供者。

## 受影響的模組 {#impacted-modules}

* 檔案服務
* Document Security
* Foundation JEE
* PDFG服務

[聯絡支援](https://www.adobe.com/account/sign-in.supportportal.html)
