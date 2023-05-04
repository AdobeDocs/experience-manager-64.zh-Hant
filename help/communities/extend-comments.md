---
title: 擴展注釋元件
seo-title: Extend Comments Component
description: 擴展「注釋」元件，以更改其外觀或行為以供特定用途使用
seo-description: Extend the Comments component to alter its appearance or behavior for specific uses
uuid: 6f439097-b1d0-4e7d-afcf-01d8f43aa866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a07a4690-0e47-4a76-84cb-96abdc70b835
exl-id: f6722953-ff71-4fba-b76e-1d566f71f6d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 2%

---

# 擴展注釋元件 {#extend-comments-component}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

其意圖 [延伸](client-customize.md#extensions) 預設元件是根據特定用途改變元件的外觀或行為。

元件的路徑是唯一的，並將預設元件作為超級資源類型引用。 與元件覆蓋的全球範圍相比，風險較小，因為範圍有限。

>[!NOTE]
>
>延伸 [覆蓋](client-customize.md#overlays) 不支援元件。

## 範例 {#example}

假設註解元件的標題在AEM例項的一個網站上必須以替代外觀顯示，而在另一個網站上以預設顯示。 更好的解決方案是，確保有多個注釋元件可供不同網站使用，而不是覆蓋預設注釋（這會變更所有例項的注釋元件）。

若要實作此解決方案，請建立可擴充（覆寫）現有元件並修改Handlebars指令碼的新元件。 使用新注釋的網站區域可以使用擴展注釋，而使用預設外觀的網站則不受影響。

註解元件實際上是構成註解系統的兩個元件之一。 因此，有兩個元件可延伸： *評論* 和 *註解*. 要編輯的指令碼位於*注釋*元件的 `header.hbs` 檔案，而父項 *評論* 元件（註解系統）是作者實際新增至頁面的元件。

若要延伸意見，您需要：

1. [建立元件](extend-create-components.md)
1. [將注釋添加到示例頁](extend-sample-page.md)
1. [更改外觀](extend-alter-appearance.md)
