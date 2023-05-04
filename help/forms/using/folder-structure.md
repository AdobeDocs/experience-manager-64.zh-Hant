---
title: 了解資料夾結構
seo-title: Understanding the folder structure
description: 如何了解要自訂的AEM Forms工作區原始碼的資料夾結構。
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 2%

---

# 了解資料夾結構 {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Forms工作區元件是使用骨幹架構以MVC架構設計。 每個元件都有一個檔案，用於：

* 模型，包含商業邏輯。
* 範本，即包含介面控制項的HTML檔案。
* 視圖，它作為模板的控制器類。

所有元件的資產會置於下述的資料夾結構中。 若要存取資產，請登入CRXDE Lite並瀏覽 `/libs/ws/js/runtime/`.

**模型** 包含骨幹模型。

**檢視** 包含骨幹視圖。

**範本** 僅包含元件的HTML範本。

**路由** 包含通用路由。 路由內的範本資料夾包含HTML代碼和元件的參考。

**服務** 包含在REST端點上呼叫Adobe Experience Manager伺服器API的服務介面。

**util** 包含可由多個元件使用的通用實用程式。
