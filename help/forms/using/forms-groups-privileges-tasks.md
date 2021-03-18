---
title: AEM Forms論OSGi集團與特權
seo-title: AEM Forms論OSGi集團與特權
description: 指派使用者至群組，以在OSGi上管理AEM Forms
seo-description: 指派使用者至群組，以在OSGi上管理AEM Forms
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: 管理員
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 2%

---


# AEM Forms關於OSGi組和權限{#aem-forms-on-osgi-groups-and-privileges}

指派使用者至群組，以在OSGi上管理AEM Forms

您可以[建立組](/help/sites-administering/user-group-ac-admin.md#group-administration)，並將策略和[用戶](/help/sites-administering/user-group-ac-admin.md#user-administration)分配給中的組AEM。 這些原則可控制屬於群組的使用者的權限。

在安裝[AEM Forms附加套件](/help/forms/using/installing-configuring-aem-forms-osgi.md)後，本文中提及的群組（例如forms-user和forms-power-user）會自動可供指派。 下表列出了用戶可以根據組分配在OSGi上為AEM Forms執行的任務：

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
     <li>建立、預覽、發佈及提交最適化表單</li> 
     <li>建立、預覽和發佈互動式通訊和檔案片段</li> 
     <li>上傳資產至例AEM項</li> 
     <li>建立主題</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>建立、預覽、發佈及提交最適化表單</li> 
     <li>建立、預覽和發佈互動式通訊和檔案片段</li> 
     <li>使用程式碼編輯器建立最適化表單的指令碼</li> 
     <li>上傳包含指令碼的資產</li> 
     <li>建立主題</li> 
     <li>包含XDP的導入包</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>審查提交內容</li> 
     <li>批准或拒絕提交</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
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
     <li>使用Agent UI訪問通信管理信函或交互通信</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>工作流程編輯器</p> </td> 
   <td>
    <ul> 
     <li>建立收件箱應用程式</li> 
     <li>建立工作流程模型</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>使用收件AEM匣應用程式</li> 
     <li>管理工作流程例項</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>配置 PDF 產生器</li> 
     <li>設定Watched資料夾</li> 
     <li>管理工作流程應用程式</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. 具有表單使用者群組權限的使用者無法編寫最適化表單的指令碼。
1. 具有模板作者組權限的用戶無法編寫模板指令碼。

