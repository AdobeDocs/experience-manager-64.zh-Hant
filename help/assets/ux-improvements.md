---
title: Assets中的使用者體驗增強功能
description: 本文說明AEM 6.4 Assets中的使用者體驗改善。
contentOwner: AG
feature: 發行資訊
role: Leader,Business Practitioner
exl-id: 65029113-987e-46eb-86eb-8028233031f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 1%

---

# 資產{#user-experience-enhancements-in-assets}中的使用者體驗增強功能

AEM 6.4 Assets包含數種可用性改善，可提供順暢的使用者體驗並提高生產力。 您可以建立/管理上市內容的速度增加，可提高業務的內容速度。

介面回應速度更快，可協助您有效管理大量資產。 您可以快速搜尋、顯示、排序，以及順利捲動一長串項目。

您可以個人化各種檢視 — 卡片、清單和欄檢視。 例如，您可以設定要在「卡片」檢視中顯示的縮圖大小。 對於「清單」檢視，您可以設定要針對清單中的資產顯示的詳細資訊層級。 AEM 6.4 Assets包含新的樹狀檢視，可讓您輕鬆導覽Assets存放庫並尋找資產。

## 延遲載入{#lazy-loading}

當您在AEM 6.4 Assets中瀏覽/搜尋資產時，一次最多會顯示200個資產。 您可以更快捲動結果，這在瀏覽長清單的結果時特別有用。 由於一次載入了大量資產，因此瀏覽體驗會很流暢。

如果您點選/按一下資產以檢閱其詳細資訊頁面，您只需點選/按一下工具列中的「上一步」按鈕，即可返回結果頁面。

## 卡片檢視改善{#card-view-improvements}

您可以根據您使用的裝置和所需的詳細程度，在「卡片」檢視中調整資產縮圖的大小。 這樣，您就可以個人化您的檢視，並控制顯示的縮圖數目。

要在「卡片」視圖中調整縮圖的大小，請執行以下步驟：

1. 點選/按一下工具列中的「版面」圖示，然後選擇「**[!UICONTROL 檢視設定]**」選項。

   ![view_settings](assets/view_settings.png)

1. 從&#x200B;**[!UICONTROL 檢視設定]**&#x200B;對話方塊中，選取所需的縮圖大小，然後點選/按一下&#x200B;**[!UICONTROL 更新]**。

   ![view_settings_dialog](assets/view_settings_dialog.png)

1. 查看以所選大小顯示的縮略圖。

   ![thumbnails_changed](assets/thumbnails_changed.png)

「卡片」檢視中的方塊現在會顯示其他資訊，例如發佈狀態。

![publish_status](assets/publish_status.png)

## 清單檢視改善{#list-view-improvements}

在「清單」檢視中，第一欄現在預設會顯示資產的檔案名稱。 也會顯示其他資訊，例如發佈和處理狀態及地區設定。

![list_view](assets/list_view.png)

您可以選擇設定要顯示的詳細資訊量。 點選/按一下「版面」圖示，選擇&#x200B;**[!UICONTROL 「檢視設定」]**&#x200B;選項，並指定您要顯示在&#x200B;**[!UICONTROL 「檢視設定」]**&#x200B;對話方塊中的欄。

![view_settings_dialoglistview](assets/view_settings_dialoglistview.png)

## 欄檢視改善{#column-view-improvements}

除了「卡片」和「清單」檢視，您現在還可以從「欄」檢視導覽至資產的詳細資訊頁面。 從「欄」檢視中選取資產，然後點選/按一下資產快照下的「更多詳細資料&#x200B;]**」。**[!UICONTROL 

![更多詳情](assets/more_details.png)

## 樹視圖{#tree-view}

AEM 6.4資產包含樹狀檢視，可讓您輕鬆瀏覽資產階層，並導覽至所需的資產或資料夾。

若要開啟「樹」視圖，請點選/按一下`Assets UI`中的「GlobalNav」表徵圖，然後從菜單中選擇「**[!UICONTROL 內容樹]**」。

![content_tree](assets/content_tree.png)

從內容階層導覽至所需的資產。

![navigate_contentree](assets/navigate_contenttree.png)

## 導覽資產詳細資料{#navigating-asset-details}

資產詳細資訊頁面現在包含工具列中的「上一頁」和「下一頁」按鈕，讓您可以連續檢視資料夾中的所有影像。

您也可以滑動或使用鍵盤上的方向鍵，在影像之間來回移動（視您的裝置而定）。

您可以依據所選的配置，透過下列方式開啟資產的詳細資訊頁面：

| **檢視** | **如何開啟資產詳細資訊頁面** |
|---|---|
| [!UICONTROL 卡片檢視] | 點選/按一下資產圖磚。 |
| [!UICONTROL 清單檢視] | 點選/按一下清單中資產的列項目。 |
| [!UICONTROL 欄檢視] | 點選/按一下資產快照中的&#x200B;**[!UICONTROL 更多詳細資訊]**&#x200B;按鈕。 |

使用「上一頁/下一頁」按鈕，在資產之間來回移動。

![prev_next_buttons](assets/prev_next_buttons.png)
