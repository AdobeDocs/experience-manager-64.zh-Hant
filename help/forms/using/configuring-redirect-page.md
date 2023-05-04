---
title: 設定重新導向頁面
seo-title: Configuring redirect page
description: 填寫最適化表單後，系統會將使用者重新導向至表單作者在建立表單時可設定的網頁。
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 1%

---

# 設定重新導向頁面 {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

表單作者可為每個表單設定一個頁面，在提交表單後，表單使用者會重新導向至該頁面。

1. 在編輯模式中，選取元件，然後按一下 ![欄位層級](assets/field-level.png) > **適用性表單容器**，然後按一下 ![cppr](assets/cmppr.png).

1. 在側欄中，按一下 **提交**.

1. 在提交區段的感謝頁面下方提供重新導向頁面的URL。
1. （可選）在「提交操作」下，對於「提交到REST」端點操作，您可以配置要傳遞到重定向頁的參數。

![重新導向頁面設定](assets/thank-you-setting-1.png)
**圖：** *重新導向頁面設定*

表單作者可使用傳遞至感謝頁面的下列參數。 對於所有可用的提交操作， `status` 和 `owner` 會傳遞參數。 除了這兩個參數外，還會為下列提交動作傳遞一些其他參數：

* **儲存內容動作** （已過時）: `contentPath` — 傳遞儲存已提交資料的儲存庫中節點的路徑。

* **儲存PDF動作** （已過時）: `contentPath` — 已提交的資料和儲儲存存庫中PDF檔案的節點路徑的路徑 — 將被傳遞。

* **提交至Forms工作流程**:會傳遞從表單工作流程傳回的輸出參數。

* **提交到REST端點**:系統會傳遞為欄位內與參數對應新增的參數。 `status` 和 `owner` 參數不會在此提交動作中傳遞。 如需詳細資訊，請參閱 [配置提交到REST端點提交操作](/help/forms/using/configuring-submit-actions.md).
