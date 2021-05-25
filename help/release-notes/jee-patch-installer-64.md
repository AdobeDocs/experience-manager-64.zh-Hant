---
title: AEM Forms JEE修補程式安裝程式
description: AEM Forms JEE修補程式安裝程式
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
exl-id: ce5300ce-03f4-4e7b-bc5b-01a9968ebe06
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 24%

---

# AEM Forms JEE修補程式安裝程式{#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[如需](https://www.adobe.com/tw/account/sign-in.supportportal.html) 詳細資訊或取得修補程式，請聯絡支援。

## 關於修補程式安裝程式{#about-the-patch-installer}

AEM 6.4 Forms JEE修補程式安裝程式包含在此修補程式發行前，AEM 6.4 Forms JEE所有元件的所有已修正問題。 如需修正問題的完整清單，請參閱最新的[Cumulative Fix Pack發行說明](cfp-release-notes.md)。

## 安裝修補程式{#prerequisites-to-installing-the-patch}的先決條件

* AEM 6.4 Forms

## 安裝和配置修補程式{#installing-and-configuring-the-patch}

1. 備份&lt;*AEM_forms_root*>/deploy資料夾。 如果決定解除安裝快速修正，則此為必要操作。
1. 停止應用程式伺服器。
1. 將修補程式安裝程式封存檔案解壓縮至硬碟。
1. 在根據您使用的作業系統命名的目錄中：

   * **Windows**
在複製安裝程式的硬碟上，導覽至安裝媒體或資料夾上的適當目錄，然後按兩下 
`aemforms64_cfp_install.exe` 檔案。

      * （Windows 32位）`Windows\Disk1\InstData\VM`
      * （Windows 64位元）`Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux、Solaris、**
AIXNavigate到相應目錄，並在命令提示符下鍵入 
`./aem64_cfp_install.bin`。

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris)`Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   這會啟動安裝精靈，引導您完成安裝。

1. 在 Introduction 面板上，按一下 **[!UICONTROL Next]**。
1. 在「選擇安裝資料夾」螢幕上，驗證針對現有安裝顯示的預設位置是否正確，或按一下&#x200B;**[!UICONTROL Browse]**&#x200B;以選擇安裝AEM表單的替代資料夾，然後按一下&#x200B;**[!UICONTROL Next]**。

1. 閱讀 Quick Fix Patch Summary 資訊，然後按一下 **[!UICONTROL Next]**。
1. 閱讀 Pre-Installation Summary 資訊，然後按一下 **[!UICONTROL Install]**。
1. 安裝完成後，按一下**[!UICONTROL Next]**，將快速修正更新套用至已安裝的檔案。
1. [僅] 限Windows執行以下步驟之一：

   * 在按一下「完成」之前，取消選擇「啟動配置管理器」選項。 稍後使用`[aem-forms root]\configurationManager\bin`中的`ConfigurationManager.bat`檔案運行Configuration Manager。 使用`ConfigurationManager.bat`可幫助您避免手動更新.lax檔案中axis.jar名稱的名稱
   * 在按一下「完成」之前，取消選擇「啟動配置管理器」選項。 在使用&#x200B;**ConfigurationManager.exe**&#x200B;或&#x200B;**ConfigurationManager_IPv6.exe**&#x200B;運行Configuration Manager之前，請導航至&#x200B;*&lt;AEMForms_Install_Dir>\configurationManager\bin*&#x200B;目錄，並在以下檔案中將&#x200B;**axis.jar**&#x200B;更新為&#x200B;**axis-1.1.jar**:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. （僅基於Unix）預設選中「啟動配置管理器」複選框。 按一下 **[!UICONTROL Done]**，執行 Configuration Manager。

   若要稍後執行 Configuration Manager，請取消選取 Start Configuration Manager 選項，再按一下 Done。您稍後可以使用`[AEM_forms_root]/configurationManager/bin`目錄中的適當指令碼啟動Configuration Manager。

1. 根據您的應用程式伺服器，選擇以下文檔之一，然後按照&#x200B;*配置和部署AEM表單*&#x200B;部分中的說明操作。

   * [安裝和部署適用於JBoss的AEM表單](http://www.adobe.com/go/learn_aemforms_installJBoss_64_tw)
   * [安裝和部署AEM forms for WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64_tw)
   * [安裝和部署AEM forms for WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64_tw)

1. （僅限JBoss）安裝修補程式並配置伺服器後，刪除JBoss應用程式伺服器的tmp和工作目錄。

## 部署後配置{#post-deployment-configurations}

### SAML配置{#saml-configurations}

如果您已設定SAML驗證，且遇到大型IDP中繼資料的問題，請安裝修補程式後執行下列作業：

1. 在應用程式伺服器中設定以下系統屬性：\
   `um.saml.enable.large.xml=true`

1. 重新啟動伺服器。
1. 刪除現有的SAML驗證提供者，並如SAML設定所述，為現有網域再次新增這些提供者。

## 受影響的模組{#impacted-modules}

* 文件服務
* 文件安全性
* Foundation JEE
* PDFG 服務

[聯絡支援](https://www.adobe.com/account/sign-in.supportportal.html)
