---
title: 使用AEM Forms工作區
seo-title: 使用AEM Forms工作區
description: 透過此程式工作流程快速概觀，開始使用AEM Forms工作區。
seo-description: 透過此程式工作流程快速概觀，開始使用AEM Forms工作區。
uuid: fac103bd-142b-46cc-9db7-22d1880260f8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ebabecb9-91c4-4991-8f5b-d27f940d2ecb
exl-id: b5ca864c-0895-4c83-a8f6-1913452b1b01
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 0%

---

# 使用AEM Forms工作區{#working-with-aem-forms-workspace}

## 簡介 {#introduction}

AEM Forms工作區是AEM Forms的一部分。 Workspace除了方便PDF forms外，還可促進HTML Forms的轉譯。 現在，您可以從行動介面和Web應用程式參與業務流程。

此外，AEM Forms工作區也可使用標準HTML和JavaScript™開發方法進行高度自訂。 它是基於元件的軟體，可輕鬆與其他Web應用程式整合。

如需詳細資訊，請參閱[AEM Forms工作區簡介](/help/forms/using/introduction-html-workspace.md)。

## 熟悉{#getting-familiar}

要熟悉建立表單應用程式以自動化業務流程的端到端流程，請遵循逐步說明。 完成逐步說明後，您可以使用Workbench、Designer和AEM Forms工作區來建立、管理和測試應用程式。 如需實作詳細資訊，請參閱[建立您的第一個AEM Forms應用程式](https://help.adobe.com/en_US/livecycle/11.0/CreateFirstApp/index.html)。

## 功能概述{#functional-overview}

您可以使用AEM Forms工作區來執行下列工作：

**開始業務流程：** AEM Forms工作區會依照您的組織所設計和設定的流程分類。您可以將常用的類別設為我的最愛，以快速存取類別。 啟動流程時，您通常會填寫表單，以啟動表單工作流程控制的業務流程。 有關詳細資訊，請參閱[啟動進程](/help/forms/using/starting-processes.md)。

**查看任務並對任務執行操作：** 查看待辦事項清單時，您會看到分配給您的業務流程中的任務，或分配給您所屬的任何組的任務，或是其他用戶的共用任務。您可以視需要開啟、處理及完成工作。 完成任務通常包括提供資訊、批准表單或拒絕表單。 如需詳細資訊，請參閱[使用待辦事項清單](/help/forms/using/todo-lists.md)。

**追蹤工作**:若要追蹤您的工作，請使用AEM Forms工作區的「追蹤」標籤。您可以搜尋您啟動或參與的作用中或已完成的程式。 您可以查看屬於流程一部分的任務、分配和表單。 您也可以使用先前啟動的流程的表單資料來啟動新流程。 如需詳細資訊，請參閱[追蹤程式](/help/forms/using/tracking-processes.md)。

## AEM Forms工作區新產品{#new-offering-of-aem-forms-workspace}

**支援批量任務**:

您可以核准相同類型的多個工作。 選擇一個任務進行審批後，將僅啟用具有相同進程、具有相同任務名稱和相同路由選項的任務。 如需實作詳細資訊，請參閱[使用待辦清單](/help/forms/using/todo-lists.md)。

## 從Flex工作區移轉至AEM Forms工作區{#migrating-from-flex-workspace-to-aem-forms-workspace}

**持續運作的功能**

AEM Forms on JEE也會依預設部署Flex Workspace。 它仍如往常般運作，而您所有現有的程式和自訂功能會持續運作。

**將現有程式移轉至AEM Forms工作區：**

在AEM Forms工作區中，與XDP表單相關聯的預設轉譯與提交服務（位於預設動作設定檔中）已變更，且已推出新服務。 有關詳細資訊，請參閱[新建呈現和提交服務](/help/forms/using/new-render-submit-service.md)。 若要移轉可與XDP表單搭配使用的現有程式，以利用這些服務，您可以遵循[這些步驟](/help/forms/using/new-render-submit-service.md)。

**將Flex工作區自訂對應至AEM Forms工作區：**

兩個工作區中各種自訂類型之間的對應如下。

<table> 
 <tbody>
  <tr>
   <td><strong>自訂類型 </strong></td> 
   <td><strong>涵蓋的自訂 </strong></td> 
   <td><strong>對應的AEM Forms工作區自訂案例</strong></td> 
  </tr>
  <tr>
   <td>本地化自訂</td> 
   <td>
    <ol> 
     <li>更改工作區的區域設定</li> 
    </ol> </td> 
   <td>
    <ol> 
     <li><a href="/help/forms/using/changing-locale-user-interface.md">變更AEM Forms工作區地區</a></li> 
    </ol> </td> 
  </tr>
  <tr>
   <td>主題自訂</td> 
   <td>
    <ol> 
     <li>替換影像</li> 
     <li>修改顏色</li> 
    </ol> </td> 
   <td>
    <ol> 
     <li><a href="/help/forms/using/changing-organization-logo-branding.md">更改組織徽標</a> </li> 
     <li><a href="/help/forms/using/changing-color-scheme-interface.md">變更色彩配置</a></li> 
    </ol> </td> 
  </tr>
  <tr>
   <td>配置自訂</td> 
   <td>
    <ol> 
     <li>簡化工作區用戶介面<br /> </li> 
     <li>建立新登入畫面</li> 
     <li>建立自訂核准容器</li> 
    </ol> </td> 
   <td>
    <ol> 
     <li><a href="/help/forms/using/description-reusable-components.md">使用可重複使用的元件</a></li> 
     <li><a href="/help/forms/using/creating-new-login-screen.md">建立新的登入畫面</a></li> 
     <li>已棄用核准容器。</li> 
    </ol> </td> 
  </tr>
 </tbody>
</table>

### AEM Forms工作區{#limitations-of-aem-forms-workspace}的限制

Flex工作區中未提供的部分功能包括：訊息和通知、歡迎頁面、核准容器及管理欄標題的選項。 如需完整清單，請參閱AEM Forms workspace中無法使用的Flex Workspace功能](/help/forms/using/features-flex-workspace-available-html.md) 。[

## 使用AEM Forms工作區開發{#developing-with-aem-forms-workspace}

### 架構 {#architecture}

AEM Forms工作區是以HTML和JavaScript™為基礎，由CRX™托管的網頁應用程式。 在瀏覽器中開啟工作區URL時，會存取CRX™資源，並在瀏覽器中將應用程式轉譯為HTML頁面。 JavaScript程式庫和自訂JavaScript程式碼會管理應用程式的內部和外部行為，例如使用者介面、使用者互動，以及與AEM Forms伺服器的通訊。 如需詳細資訊，請參閱AEM Forms工作區[architecture](/help/forms/using/html-workspace-architecture.md)。

### AEM Forms工作區自訂{#aem-forms-workspace-customization}

AEM Forms工作區支援多種自訂功能，以更新使用者介面的版面、外觀、功能等。 這些自訂項目包括更新下列其中一或多個項目：

* 用戶介面的外觀
* 使用語義自定義的功能
* 在其他Web應用程式中重複使用HTML元件

[customization](introduction-customizing-html-workspace.md)文章說明此類自訂的類型。

### 設定開發人員環境{#set-up-the-developer-environment}

AEM Forms工作區交付項目包括部署在CRX上的CRX套件、包含完整原始碼的SDK封存、協力廠商JavaScript程式庫，以及AEM Forms工作區的建置指令碼。 使用這些設定來設定開發人員環境，以執行上述的自訂。 如需詳細資訊，請參閱[建立AEM Forms工作區程式碼](introduction-customizing-html-workspace.md#building-html-workspace-code)。

您可以自訂介面和核心功能的主要部分，例如字型、色彩配置、標誌、登入畫面、錯誤對話方塊、與協力廠商應用程式的整合，以及在協力廠商應用程式中重複使用元件。 您還可以增強「任務摘要」頁上顯示的內容，顯示任務路由操作的影像，甚至修改建立AEM Forms工作區應用程式的低級骨幹模型和視圖。

### XDP Forms的HTML呈現{#html-rendering-of-xdp-forms}

根據預設，對於新流程，XDP表單會以PDF格式在桌上型電腦上呈現，以HTML格式在平板電腦上呈現。 您可以一律以HTML格式轉譯XDP表單。 有關詳細資訊，請參閱[新呈現和提交服務](/help/forms/using/new-render-submit-service.md)。

[Mobile ](https://helpx.adobe.com/livecycle/help/mobile-forms/introduction.html) Forms功能可搭配設定檔 [使用](https://helpx.adobe.com/livecycle/help/mobile-forms/creating-profile.html)，可啟用XDP表單的HTML轉譯。依預設，「呈現新HTML表單」會使用您可以變更的`default.html`設定檔。 您也可以新增在以HTML格式轉譯XDP表單前發生的自訂變更。

## AEM Forms workspace應用程式{#aem-forms-workspace-app}

若要在行動裝置上處理您的業務流程，您可以使用AEM Forms的AEM Forms工作區應用程式產品。 如需詳細資訊，請參閱[AEM Forms工作區應用程式概述](https://helpx.adobe.com/livecycle/help/mobile-workspace/mobile-workspace-overview.html)。
