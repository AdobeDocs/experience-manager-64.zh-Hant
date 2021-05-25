---
title: 與Adobe Sign整合 |處理用戶資料
seo-title: 與Adobe Sign整合 |處理用戶資料
description: AEM Forms與Adobe Sign整合，以啟用最適化表單中的電子簽名工作流程，以處理法律、銷售、工資單、人力資源管理工作流程的表單或協定。 深入了解使用者資料、資料儲存，以及存取和刪除使用者資料。
seo-description: AEM Forms與Adobe Sign整合，以啟用最適化表單中的電子簽名工作流程，以處理法律、銷售、工資單、人力資源管理工作流程的表單或協定。 深入了解使用者資料、資料儲存，以及存取和刪除使用者資料。
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Adobe Sign
role: Administrator
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 與Adobe Sign整合 |處理用戶資料{#integration-with-adobe-sign-handling-user-data}

AEM Forms與Adobe Sign整合，以啟用最適化表單中的電子簽名工作流程，以處理法律、銷售、工資單、人力資源管理工作流程的表單或協定。 它允許單一和多用戶簽名、循序和同時的簽名工作流、以匿名或登錄用戶身份簽名表單，以及多種驗證用戶的方法。

當簽署者或多位簽署者簽署並提交最適化表單時，會產生Adobe Sign合約，其中包含簽署者的相關資訊。

如需AEM Forms與Adobe Sign整合的詳細資訊，請參閱[在最適化表單中使用Adobe Sign](/help/forms/using/working-with-adobe-sign.md)。

## 使用者資料和資料儲存 {#data}

Adobe Sign啟用的最適化表單包括與簽署者相關的資訊，且可能包含最適化表單所收集的其他使用者資料。 Adobe Sign服務會儲存具有合約內簽名的使用者資料。 合約會儲存在AEM Forms雲端服務中設定的Adobe Sign伺服器上。 此外，如果最適化表單設定為使用Forms Portal提交動作，則合約資料會與表單資料一起儲存在表單入口網站資料存放區中。

## 訪問和刪除用戶資料{#access-and-delete-user-data}

用戶資料在協定中收集，但不保存在任何服務表中。 Adobe Sign可讓管理員自行選擇如何管理其在服務中控制的資料。 Adobe Sign服務的隱私權管理員可以根據要求者的電子郵件地址列出或移除合約。

Adobe Sign提供網頁應用程式，可讓參與者搜尋協定，並視需要刪除協定。 如需詳細資訊，請參閱[Adobe Sign — 功能：刪除用戶資訊](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html)。

設定為使用Forms Portal提交動作的適用性表單的合約資料也會儲存在表單入口網站資料存放區中。 若要從表單入口網站資料存放區存取和刪除資料，請參閱[Forms入口網站 |處理使用者資料](/help/forms/using/forms-portal-handling-user-data.md)。
