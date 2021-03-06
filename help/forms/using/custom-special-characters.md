---
title: 通信管理中的自訂特殊字元
seo-title: 通信管理中的自訂特殊字元
description: 了解如何在通信管理中新增自訂特殊字元。
seo-description: 了解如何在通信管理中新增自訂特殊字元。
uuid: ac4f1353-f1ef-43b7-8e80-aba56a155e3f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 1b5e6746-3618-46fe-ba2d-ec76bb79de1d
feature: 通信管理
exl-id: a6206ae1-b71b-4066-b7a0-ce39a60d6dd0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---

# 通信管理{#custom-special-characters-in-correspondence-management}中的自訂特殊字元

## 概覽 {#overview}

通信管理內建210個特殊字元的預設支援，您可輕鬆將其插入字母中。

例如，您可以插入下列特殊字元：

* 貨幣符號，如€、¥和£
* 數學符號，如∑、√、∂和^
* 標點符號為&quot;和&quot;

可以在字母中插入特殊字元：

* 在[文字編輯器](/help/forms/using/document-fragments.md#createtext)中
* 在[可編輯的通信中的內嵌模組](/help/forms/using/create-correspondence.md#managecontent)

![specialcharactersinlinemodule](assets/specialcharactersinlinemodule.png)

管理員可以透過自訂來新增對更多/自訂特殊字元的支援。 本文提供如何新增對其他自訂特殊字元支援的指示。

## 新增或修改通信管理中自訂特殊字元的支援 {#creatingfolderstructure}

使用下列步驟來新增對自訂特殊字元的支援：

1. 前往`https://[server]:[port]/[ContextPath]/crx/de`並以管理員身分登入。
1. 在應用程式資料夾中，建立名為&#x200B;**[!UICONTROL specialcharacters]**&#x200B;的資料夾，其路徑/結構類似於specialcharacters資料夾（位於libs下的textEditorConfig資料夾中）:

   1. 按一下右鍵以下路徑上的&#x200B;**指定字元**&#x200B;資料夾，然後選擇&#x200B;**覆蓋節點**:

      `/libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters`

   1. 確定「覆蓋節點」對話方塊有下列值：

      **路徑：** /libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters

      **覆蓋位置：** /apps/

      **匹配節點類型：已** 勾選

      >[!NOTE]
      >
      >請勿在/libs分支中進行變更。 您所做的任何變更都可能會遺失，因為只要您符合以下條件，此分支就會發生變更：
      >
      >* 在您的執行個體上升級
      >* 套用Hotfix
      >* 安裝功能套件


   1. 按一下&#x200B;**OK**，然後按一下&#x200B;**Save All**。 指定路徑中建立了指定字元資料夾。

      建立覆蓋後，驗證節點結構標籤。 使用覆蓋在/apps中建立的每個節點，應具有與該節點在/libs中定義的相同類別和屬性。 如果/apps位置下的節點結構中缺少任何屬性或標籤，請將其標籤與/libs中的對應節點同步。

1. 確保&#x200B;**[!UICONTROL textEditorConfig]**&#x200B;節點具有以下屬性和值：

   | 名稱 | 類型 | 值 |
   |---|---|---|
   | cmConfigurationType | 字串 | cmTextEditorConfiguration |
   | cssPath | 字串 | /libs/fd/cm/ma/gui/components/admin/createasset/textcontrol/clientlibs/textcontrol |

1. 按一下右鍵以下路徑上的&#x200B;**[!UICONTROL 指定字元]**&#x200B;資料夾，然後選擇&#x200B;**建立>子節點**，然後按一下&#x200B;**保存全部**:

   /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters/&lt;YourChildNode>

1. 刷新文本編輯器\建立通信UI頁。 您新增的節點是UI中特殊字元清單中的最後一個節點。
1. 按一下「**全部保存**」。
1. 視需要變更特殊字元：

<table> 
 <tbody> 
  <tr> 
   <td><strong>至...</strong></td> 
   <td><strong>完成下列步驟</strong></td> 
  </tr> 
  <tr> 
   <td>新增自訂特殊字元</td> 
   <td> 
    <ol> 
     <li>在「/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters」下添加子節點，並包含必需屬性。</li> 
     <li>按一下「全部儲存」</li> 
     <li>刷新文本編輯器\建立通信UI以查看更改。</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>更新現有特殊字元的屬性</td> 
   <td> 
    <ol> 
     <li>覆蓋要如上所述更新的節點，並驗證標籤和類別。</li> 
     <li>更改任何值，如caption、value、endValue和multipleCaption。 </li> 
     <li>按一下「全部儲存」 。 </li> 
     <li>刷新文本編輯器\建立通信UI以查看更改。</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>隱藏特殊字元</td> 
   <td> 
    <ol> 
     <li>覆蓋要隱藏在「/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters」下的節點</li> 
     <li>將sling:hideResource(Boolean)屬性新增至要隱藏的節點（在應用程式底下）。 </li> 
     <li>按一下「全部儲存」 。 </li> 
     <li>刷新文本編輯器\建立通信UI以查看更改。<br /> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>隱藏多個特殊字元</td> 
   <td> 
    <ol> 
     <li>將屬性"sling:hideChildren（String或String[]）"新增至"/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"。 </li> 
     <li>將節點名稱（要隱藏的特殊字元）新增為「sling:hideChildren」屬性的值。 </li> 
     <li>按一下「全部儲存」 。 </li> 
     <li>刷新文本編輯器\建立通信UI以查看更改。<br /> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>排序特殊字元</td> 
   <td> 
    <ol> 
     <li>在「/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters」下添加子節點，並包含必需屬性。 </li> 
     <li>將"sling:orderBefore(String)"屬性新增至新建立的子節點。 </li> 
     <li>將節點名稱新增為值，以顯示新新增的特殊字元。 </li> 
     <li>按一下「全部儲存」 。 </li> 
     <li>刷新文本編輯器\建立通信UI以查看更改。<br /> </li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>
