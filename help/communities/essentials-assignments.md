---
title: 工作總攬
seo-title: 工作總攬
description: 啟用社群的工作總攬功能概觀
seo-description: 啟用社群的工作總攬功能概觀
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---

# 工作總攬{#assignments-essentials}

本頁提供了使用[啟用社區](overview.md#enablement-community)站點的分配功能的基本資訊。

指派功能是將啟用資源和學習路徑指派給啟用社群的成員。

## 客戶端{#essentials-for-client-side}的要點

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
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
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
   <td>請參閱<a href="assignments.md">工作總攬功能</a></td> 
  </tr>
 </tbody>
</table>

### 完成和成功狀態{#completion-and-success-status}

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

## 伺服器端{#essentials-for-server-side}的要點

### 指定任務功能 {#assignments-function}

包含[分配函式](functions.md#assignments-function)的社區站點結構包括配置的` [assignments](assignments.md)`元件。

### 參考API {#reference-apis}

* [啟用API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [報表API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [報表分析API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
