---
title: AEM Forms on OSGi Groups and Privileges
seo-title: AEM Forms on OSGi Groups and Privileges
description: 將使用者指派至群組，以在OSGi上管理AEM Forms
seo-description: Assign users to the groups to manage AEM Forms on OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: Admin
exl-id: a79e863e-c316-422e-a565-b0ffdeffcc00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 3%

---

# AEM Forms on OSGi Groups and Privileges {#aem-forms-on-osgi-groups-and-privileges}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

將使用者指派至群組，以在OSGi上管理AEM Forms

您可以 [建立群組](/help/sites-administering/user-group-ac-admin.md#group-administration) 並分配策略和 [使用者](/help/sites-administering/user-group-ac-admin.md#user-administration) 至AEM中的群組。 這些策略控制屬於組的用戶的權限。

安裝後 [AEM Forms附加元件套件](/help/forms/using/installing-configuring-aem-forms-osgi.md)，本文提及的群組（例如forms-user和forms-power-user）會自動可供指派。 下表列出使用者可根據群組指派在OSGi上為AEM Forms執行的任務：

<table> 
 <tbody>
  <tr>
   <td>群組</td> 
   <td>任務</td> 
  </tr>
  <tr>
   <td>forms-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>建立、預覽、發佈和提交最適化表單</li> 
     <li>建立、預覽和發佈互動式通訊和檔案片段</li> 
     <li>上傳資產至AEM例項</li> 
     <li>建立主題</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>建立、預覽、發佈和提交最適化表單</li> 
     <li>建立、預覽和發佈互動式通訊和檔案片段</li> 
     <li>使用程式碼編輯器建立最適化表單的指令碼</li> 
     <li>上傳資產，包括指令碼</li> 
     <li>建立主題</li> 
     <li>包含XDP的匯入套件</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>審核提交</li> 
     <li>批准或拒絕提交</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>範本作者 <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>建立並預覽最適化表單或互動式通訊範本</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>建立和修改表單資料模型</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-user-agent</td> 
   <td>
    <ul> 
     <li>使用代理UI訪問通信管理信函或互動式通信</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>工作流程編輯器</p> </td> 
   <td>
    <ul> 
     <li>建立收件箱應用程式</li> 
     <li>建立工作流模型</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>使用AEM收件匣應用程式</li> 
     <li>管理工作流程例項</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd管理員</td> 
   <td>
    <ul> 
     <li>配置 PDF 產生器</li> 
     <li>配置監看資料夾</li> 
     <li>管理工作流應用程式</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. 具有表單使用者群組權限的使用者無法編寫最適化表單的指令碼。
1. 具有模板作者組權限的用戶無法編寫模板的指令碼。
