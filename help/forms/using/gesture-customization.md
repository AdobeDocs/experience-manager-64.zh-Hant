---
title: 手勢自訂
seo-title: 手勢自訂
description: 自訂您AEM Forms應用程式上的手勢
seo-description: 自訂您AEM Forms應用程式上的手勢
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
exl-id: 238410e0-1623-49dc-b2fc-b5b2d5fb362b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 手勢自訂{#gesture-customization}

您可以自訂AEM Forms應用程式的手勢，提供與應用程式互動的不同方法。 例如，您可以添加新手勢以開啟或關閉任務或起始點。

## 若要自訂AEM Forms應用程式中的手勢{#to-customize-gestures-in-aem-forms-app}

在AEM Forms應用程式中，向左滑動會開啟新工作或起始點，而向右滑動則不會執行任何動作。 下列範例提供在AEM Forms應用程式中執行滑鼠右鍵手勢時，開啟新工作或起始點的步驟。

1. 開啟您的專案。

   * 若為iOS，請在Xcode中開啟`Capture.xcodeproj`
   * 若為Android，請在Eclipse中開啟Android專案。
   * 對於Windows，在Visual Studio中開啟`MWSWindows.sln`。

1. 導覽至檢視資料夾，並開啟`task.js`檔案以進行編輯。

   * 在Xcode中，導覽至「**擷取> www > wsmobile > js >執行階段>檢視**」資料夾。
   * 在Eclipse中，導覽至&#x200B;**assets > www > wsmobile > js > runtime > views**&#x200B;資料夾。
   * 在Visual Studio中，導航至&#x200B;**MWSindows > www > wsmobile > js > runtime > views**&#x200B;資料夾。

   >[!NOTE]
   >
   >task.js檔案包含與任務或起始點清單中列出的每個任務或起始點相關聯的骨幹視圖。

1. 在`task.js`檔案中，搜尋檢視的events屬性。

   events屬性是一個映射，每個條目的格式為：

   `"EventName Selector": "Function"`

   當您在`Selector`指定的HTML元素上觸發名為`EventName`的Javascript事件時，會呼叫`Function`。

1. 尋找

   * &quot;點選.taskContentArea&quot; :&quot;onTaskClick&quot;,

      &quot;點選.taskOpenArea&quot; :&quot;onTaskClick&quot;,

      &quot;tap .task-content&quot; :&quot;onTaskClick&quot;,

      &quot;tap .last_empty_div&quot; :&quot;onTaskClick&quot;,
   替換為

   * &quot;swipe .taskContentArea&quot; :&quot;onTaskClick&quot;,

      &quot;swipe .taskOpenArea&quot; :&quot;onTaskClick&quot;,

      &quot;滑動.task-content&quot; :&quot;onTaskClick&quot;,

      &quot;swipe .last_empty_div&quot; :&quot;onTaskClick&quot;,


1. 保存並關閉`task.js`檔案。
1. 建立並執行AEM Forms應用程式。 現在，您可以使用左側滑動和右側滑動來開啟。

同樣地，您也可以針對各種手勢、HTML元素和函式的組合，在其他檢視中進行變更。
