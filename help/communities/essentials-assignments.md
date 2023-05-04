---
title: 工作總攬
seo-title: Assignments Essentials
description: 啟用社群的工作總攬功能概觀
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 12%

---

# 工作總攬 {#assignments-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此頁面提供使用的工作分配功能的基本資訊 [啟用社群](overview.md#enablement-community) 網站。

指派功能是將啟用資源和學習路徑指派給啟用社群的成員。

## 用戶端的要點 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>包括</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.beadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr>
  <tr>
   <td> <strong>範本</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>cs</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> 屬性</strong></td> 
   <td>請參閱 <a href="assignments.md">工作總攬功能</a></td> 
  </tr>
 </tbody>
</table>

### 完成和成功狀態 {#completion-and-success-status}

「完成」和「成功」狀態用於報表，以及「工作總攬」上的狀態橫幅。

完成狀態:

* 未指派
* 未開始（新）
* 進行中
* 完成

成功狀態:

* 未知
* 通過
* 失敗

完成和成功狀態的唯一可能組合是：

| **完成** | **成功** |
|---|---|
| 尚未開始 | 未知 |
| 進行中 | 未知 |
| 完成 | 通過 |
| 完成 | 失敗 |

## 伺服器端的Essentials {#essentials-for-server-side}

### 指定任務功能 {#assignments-function}

包含 [分配函式](functions.md#assignments-function)，包含已設定的 ` [assignments](assignments.md)` 元件。

### 參考API {#reference-apis}

* [啟用API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [報表API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [報表分析API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
