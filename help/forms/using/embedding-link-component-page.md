---
title: 在頁面中內嵌連結元件
seo-title: Embedding link component in a page
description: 您可以使用連結元件來從任何頁面連結最適化檔案或最適化表單。
seo-description: You can use the link component to link an adaptive document or an adaptive form from any page.
uuid: fde56b5f-634c-406f-a026-875f972f7c8f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: a4a36e73-3f7a-4173-8807-931f26daa35a
exl-id: eb816a35-0773-4eda-95b2-1d351c71be8b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# 在頁面中內嵌連結元件{#embedding-link-component-in-a-page}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 必備條件 {#prerequisites}

連結元件是「文檔服務」類別的成員。 確保「文檔服務」類別在AEM元件瀏覽器中可見。 如果未列出類別，請依照 [啟用表單入口網站元件](/help/forms/using/enabling-forms-portal-components.md).

## 連結元件 {#link-component}

連結元件可讓表單入口網站作者從頁面上的任何位置建立最適化表單的連結。 「連結」元件可在元件瀏覽器的「文檔服務」部分中使用。

執行下列步驟將連結元件新增至頁面：

1. 拖曳 **連結** 元件。 選取元件並點選 ![cppr](assets/cmppr.png). 「編輯連結元件」(Edit Link Component)對話框隨即開啟。

   ![edit-link-component](assets/edit-link-component.png)

1. 在 **顯示** 頁簽，指定以下內容：

   * **連結註解**:連結的文字或註解。
   * **連結工具提示**:連結的工具提示。
   * **版面範本**:連結元件版面的範本。

1. 開啟 **資產資訊** ，並指定資產的類型。 資產可以是 **表單**. 系統會根據選取的資產類型顯示下列選項：

   * **資產路徑**:儲存資產的存放庫路徑。
   * **呈現類型**:渲染格式 — PDF、HTML或自動。 「自動」呈現類型會偵測使用者環境，並因此將表單轉譯為HTML或PDF。 例如，如果從行動裝置存取表單，自動轉譯類型會以HTML呈現表單。
   * **提交URL:**  表單資料提交所在的servlet的URL。
   * **HTML設定檔**:將表單轉譯為HTML的設定檔。
   * **PDF設定檔**:將表單呈現為PDF文檔的配置檔案。

1. 開啟 **進階** 標籤。 您可以以索引鍵值配對格式指定其他參數。 按一下連結時，會連同表單一併傳遞這些額外參數。

   點選 **完成** 以儲存設定。

## 使用連結元件的最佳作法 {#best-practices-for-using-link-component-br}

* 如果在「表單路徑」中指定的路徑指向具有PDF作為允許的渲染格式的文檔，請確保選擇PDF作為渲染類型。
* 表單的提交URL可在數處指定，其優先順序如下：

   1. 表單中內嵌的提交URL（在提交按鈕中）具有最高優先順序。
   1. Forms Manager中提及的提交URL具有中等優先順序。
   1. 表單入口網站中提及的提交URL優先順序最低。
