---
title: 以程式設計方式與工作流程互動
description: 了解如何使用API和指令碼管理工作流程，並以程式設計方式與工作流程互動。
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
exl-id: da06850a-c4d5-44dd-b572-771e3b2a66c5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2015'
ht-degree: 0%

---

# 以程式設計方式與工作流程互動{#interacting-with-workflows-programmatically}

當[自定義和擴展工作流](/help/sites-developing/workflows-customizing-extending.md)時，您可以訪問工作流對象：

* [使用工作流程Java API](#using-the-workflow-java-api)
* [在ECMA指令碼中取得工作流程物件](#obtaining-workflow-objects-in-ecma-scripts)
* [使用工作流程REST API](#using-the-workflow-rest-api)

## 使用工作流Java API {#using-the-workflow-java-api}

工作流Java API包含[`com.adobe.granite.workflow`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/package-summary.html)套件和數個子套件。 API中最重要的成員是`com.adobe.granite.workflow.WorkflowSession`類。 `WorkflowSession`類提供對設計時間和運行時工作流對象的訪問：

* 工作流程模型
* 工作項目
* 工作流程例項
* 工作流程資料
* 收件匣項目

類還提供了幾種干預工作流生命週期的方法。

下表提供與工作流程以程式設計方式互動時要使用的多個關鍵Java對象的參考文檔的連結。 下面的示例演示如何獲取和使用代碼中的類對象。

| 功能 | 物件 |
|---|---|
| 存取工作流程 | [`WorkflowSession`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html) |
| 執行和查詢工作流實例 | [`Workflow`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/Workflow.html)</br>[`WorkItem`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkItem.html)</br>[`WorkflowData`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkflowData.html) |
| 管理工作流模型 | [`WorkflowModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowModel.html)</br>[`WorkflowNode`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowNode.html)</br>[`WorkflowTransition`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowTransition.html) |
| 工作流中（或不）的節點的資訊 | [`WorkflowStatus`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) |

## 在ECMA指令碼{#obtaining-workflow-objects-in-ecma-scripts}中獲取工作流對象

如[找到指令碼](/help/sites-developing/the-basics.md#locating-the-script)中所述，AEM（透過Apache Sling）提供執行伺服器端ECMA指令碼的ECMA指令碼引擎。 [`org.apache.sling.scripting.core.ScriptHelper`](https://sling.apache.org/apidocs/sling5/org/apache/sling/scripting/core/ScriptHelper.html)類別可作為`sling`變數立即供指令碼使用。

`ScriptHelper`類提供對`SlingHttpServletRequest`的訪問，您可以使用該最終獲取`WorkflowSession`對象；例如：

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

## 使用工作流REST API {#using-the-workflow-rest-api}

工作流程主控台大量使用REST API;因此，本頁面說明工作流程的REST API。

>[!NOTE]
>
>curl命令行工具允許您使用Workflow REST API訪問工作流對象並管理實例生命週期。 本頁的範例示範如何透過curl命令列工具使用REST API。

REST API支援下列動作：

* 啟動或停止工作流服務
* 建立、更新或刪除工作流模型
* [啟動、暫停、繼續或終止工作流實例](/help/sites-administering/workflows.md#workflow-status-and-actions)
* 完成或委派工作項目

>[!NOTE]
>
>使用Firebug（用於網頁開發的Firefox擴充功能），便可在控制台運作時遵循HTTP流量。 例如，您可以檢查具有`POST`請求而傳送至AEM伺服器的參數和值。

在此頁面中，假設AEM在本地主機上的埠`4502`上運行，且安裝上下文為&quot; `/`&quot;（根）。 如果不是安裝的情況，則需要相應地調整HTTP請求所應用的URI。

`GET`要求支援的呈現方式為JSON呈現。 `GET`的URL應具有`.json`副檔名，例如：

`http://localhost:4502/etc/workflow.json`

### 管理工作流實例{#managing-workflow-instances}

下列HTTP要求方法適用於：

`http://localhost:4502/etc/workflow/instances`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP要求方法</td> 
   <td>動作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>列出可用的工作流實例。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td><p>建立新的工作流實例。 參數為：<br /> - <code>model</code>:相應工作流模型<br /> - <code>payloadType</code>的ID(URI):包含裝載的類型（例如<code>JCR_PATH</code>或URL）。<br /> 裝載會以參數的形式傳 <code>payload</code>送。傳回<code>201</code>(<code>CREATED</code>)回應，並附上包含新工作流程執行個體資源URL的位置標題。</p> </td> 
  </tr> 
 </tbody> 
</table>

#### 按狀態{#managing-a-workflow-instance-by-its-state}管理工作流實例

下列HTTP要求方法適用於：

`http://localhost:4502/etc/workflow/instances.{state}`

| HTTP要求方法 | 動作 |
|---|---|
| `GET` | 列出可用的工作流實例及其狀態（`RUNNING`、`SUSPENDED`、`ABORTED`或`COMPLETED`） |

#### 使用工作流實例的ID {#managing-a-workflow-instance-by-its-id}管理工作流實例

下列HTTP要求方法適用於：

`http://localhost:4502/etc/workflow/instances/{id}`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP要求方法</td> 
   <td>動作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>取得例項資料（定義和中繼資料），包括個別工作流程模型的連結。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>變更例項的狀態。 新狀態會以參數<code>state</code>的形式傳送，且必須具有下列其中一個值：<code>RUNNING</code>、<code>SUSPENDED</code>或<code>ABORTED</code>。<br /> 如果無法存取新狀態（例如當暫停終止的執行個體時）, <code>409</code> 則會將(<code>CONFLICT</code>)回應傳回給用戶端。</td> 
  </tr> 
 </tbody> 
</table>

### 管理工作流模型{#managing-workflow-models}

下列HTTP要求方法適用於：

`http://localhost:4502/etc/workflow/models`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP要求方法</td> 
   <td>動作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>列出可用的工作流模型。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>建立新工作流程模型. 如果發送參數<code>title</code>，則會建立具有指定標題的新模型。 將JSON模型定義附加為參數<code>model</code>，會根據提供的定義建立新的工作流程模型。<br /> 回 <code>201</code> 應(<code>CREATED</code>)會與包含新工作流程模型資源URL的位置標題一併傳回。<br /> 當模型定義附加為名為的檔案參數時，也會發生相同的情 <code>modelfile</code>況。<br /> 在和參數的情 <code>model</code> 況 <code>modelfile</code> 下，定義序列化格式 <code>type</code> 都需要其他參數，稱為。可使用OSGI API整合新的序列化格式。 標準JSON序列化程式會與工作流程引擎一併提供。 其類型為JSON。 如需格式的範例，請參閱下方。</td> 
  </tr> 
 </tbody> 
</table>

範例：在瀏覽器中，`http://localhost:4502/etc/workflow/models.json`的要求會產生類似下列的json回應：

```
[
    {"uri":"/var/workflow/models/activationmodel"}
    ,{"uri":"/var/workflow/models/dam/adddamsize"}
    ,{"uri":"/var/workflow/models/cloudconfigs/dtm-reactor/library-download"}
    ,{"uri":"/var/workflow/models/ac-newsletter-workflow-simple"}
    ,{"uri":"/var/workflow/models/dam/dam-create-language-copy"}
    ,{"uri":"/var/workflow/models/dam/dam-create-and-translate-language-copy"}
    ,{"uri":"/var/workflow/models/dam-indesign-proxy"}
    ,{"uri":"/var/workflow/models/dam-xmp-writeback"}
    ,{"uri":"/var/workflow/models/dam-parse-word-documents"}
    ,{"uri":"/var/workflow/models/dam/process_subasset"}
    ,{"uri":"/var/workflow/models/dam/dam_set_last_modified"}
    ,{"uri":"/var/workflow/models/dam/dam-autotag-assets"}
    ,{"uri":"/var/workflow/models/dam/update_asset"}
    ,{"uri":"/var/workflow/models/dam/update_asset_offloading"}
    ,{"uri":"/var/workflow/models/dam/dam-update-language-copy"}
    ,{"uri":"/var/workflow/models/dam/update_from_lightbox"}
    ,{"uri":"/var/workflow/models/cloudservices/DTM_bundle_download"}
    ,{"uri":"/var/workflow/models/dam/dam_download_asset"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-encode-video"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-thumbnail-replacement"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail"}
    ,{"uri":"/var/workflow/models/newsletter_bounce_check"}
    ,{"uri":"/var/workflow/models/projects/photo_shoot_submission"}
    ,{"uri":"/var/workflow/models/projects/product_photo_shoot"}
    ,{"uri":"/var/workflow/models/projects/approval_workflow"}
    ,{"uri":"/var/workflow/models/prototype-01"}
    ,{"uri":"/var/workflow/models/publish_example"}
    ,{"uri":"/var/workflow/models/publish_to_campaign"}
    ,{"uri":"/var/workflow/models/screens/publish_to_author_bin"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_publish_to_youtube"}
    ,{"uri":"/var/workflow/models/projects/request_copy"}
    ,{"uri":"/var/workflow/models/projects/request_email"}
    ,{"uri":"/var/workflow/models/projects/request_landing_page"}
    ,{"uri":"/var/workflow/models/projects/request_launch"}
    ,{"uri":"/var/workflow/models/request_for_activation"}
    ,{"uri":"/var/workflow/models/request_for_deactivation"}
    ,{"uri":"/var/workflow/models/request_for_deletion"}
    ,{"uri":"/var/workflow/models/request_for_deletion_without_deactivation"}
    ,{"uri":"/var/workflow/models/request_to_complete_move_operation"}
    ,{"uri":"/var/workflow/models/reverse_replication"}
    ,{"uri":"/var/workflow/models/salesforce-com-export"}
    ,{"uri":"/var/workflow/models/scene7"}
    ,{"uri":"/var/workflow/models/scheduled_activation"}
    ,{"uri":"/var/workflow/models/scheduled_deactivation"}
    ,{"uri":"/var/workflow/models/screens/screens-update-asset"}
    ,{"uri":"/var/workflow/models/translation"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_remove_from_youtube"}
    ,{"uri":"/var/workflow/models/wcm-translation/create_language_copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/prepare_translation_project"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-i18n-dictionary"}
    ,{"uri":"/var/workflow/models/wcm-translation/sync_translation_job"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-language-copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/update_language_copy"}
]
```

#### 管理特定工作流模型{#managing-a-specific-workflow-model}

下列HTTP要求方法適用於：

`http://localhost:4502*{uri}*`

其中`*{uri}*`是儲存庫中模型節點的路徑。

<table> 
 <tbody> 
  <tr> 
   <td>HTTP要求方法</td> 
   <td>動作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>獲取模型的<code>HEAD</code>版本（定義和元資料）。</td> 
  </tr> 
  <tr> 
   <td><code>PUT</code></td> 
   <td>更新模型的<code>HEAD</code>版本（建立新版本）。<br /> 新版本的模型的完整模型定義必須添加為 <code>model</code>參數。此外，建立新模型時需要<code>type</code>參數，且必須有值<code>JSON</code>。<br /> </td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>與PUT相同。 需要，因為AEM Widget不支援<code>PUT</code>操作。</td> 
  </tr> 
  <tr> 
   <td><code>DELETE</code></td> 
   <td>刪除模型。 為了解決防火牆/代理問題，<code>POST</code>包含<code>X-HTTP-Method-Override</code>標題條目（值<code>DELETE</code>）也將作為<code>DELETE</code>請求接受。</td> 
  </tr> 
 </tbody> 
</table>

範例：在瀏覽器中，`http://localhost:4502/var/workflow/models/publish_example.json`請求會傳回與下列程式碼類似的`json`回應：

```shell
{
  "id":"/var/workflow/models/publish_example",
  "title":"Publish Example",
  "version":"1.0",
  "description":"This example shows a simple review and publish process.",
  "metaData": 
  {
    "multiResourceSupport":"true",
    "tags":"wcm,publish"
  },
  "nodes":
  [{
    "id":"node0",
    "type":"START",
    "title":"Start",
    "description":"The start node of the workflow.",
    "metaData":
    {
    }
  },
  {
    "id":"node1",
    "type":"PARTICIPANT",
    "title":"Validate Content",
    "description":"Validate the modified content.",
    "metaData":
    {
      "PARTICIPANT":"admin"
    }
  },
  {
    "id":"node2",
    "type":"PROCESS",
    "title":"Publish Content",
    "description":"Publish the modified content.",
    "metaData":
    {
      "PROCESS_AUTO_ADVANCE":"true",
      "PROCESS":"com.day.cq.wcm.workflow.process.ActivatePageProcess"
    }
  },
  {
    "id":"node3",
    "type":"END",
    "title":"End",
    "description":"The end node of the workflow.",
    "metaData":
    {
    }
  }],
  "transitions":
  [{
    "from":"node0",
    "to":"node1",
    "metaData":
    {
    }
  },
  {
    "from":"node1",
    "to":"node2",
    "metaData":
    {
    }
  },
  {
    "from":"node2",
    "to":"node3",
    "metaData":
    {
    }
  }
]}
```

#### 使用{#managing-a-workflow-model-by-its-version}版本管理工作流模型

下列HTTP要求方法適用於：

`http://localhost:4502/etc/workflow/models/{id}.{version}`

| HTTP要求方法 | 動作 |
|---|---|
| `GET` | 獲取給定版本中模型的資料（如果存在）。 |

### 管理（用戶）收件箱{#managing-user-inboxes}

下列HTTP要求方法適用於：

`http://localhost:4502/bin/workflow/inbox`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP要求方法</td> 
   <td>動作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>列出使用者收件匣中的工作項目，由HTTP驗證標題識別。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>完成將URI作為參數<code>item</code>發送的工作項，並將相應的工作流實例推進到下一個節點，該節點由參數<code>route</code>或<code>backroute</code>定義，以備後退。<br /> 如果發送 <code>delegatee</code> 了參數，則將由參數標識的工作項 <code>item</code> 委派給指定的參與者。</td> 
  </tr> 
 </tbody> 
</table>

#### 通過WorkItem ID {#managing-a-user-inbox-by-the-workitem-id}管理（用戶）收件箱

下列HTTP要求方法適用於：

`http://localhost:4502/bin/workflow/inbox/{id}`

| HTTP要求方法 | 動作 |
|---|---|
| `GET` | 獲取由其ID標識的收件箱`WorkItem`的資料（定義和元資料）。 |

## 範例 {#examples}

### 如何取得所有執行中工作流程的清單及其ID {#how-to-get-a-list-of-all-running-workflows-with-their-ids}

若要取得所有執行中工作流程的清單，請執行下列GET:

`http://localhost:4502/etc/workflow/instances.RUNNING.json`

#### 如何以其ID取得所有執行中工作流程的清單 — 使用curl {#how-to-get-a-list-of-all-running-workflows-with-their-ids-rest-using-curl}重設

使用curl的範例：

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/instances.RUNNING.json
```

結果中顯示的`uri`可作為其他命令中的實例`id`使用；例如：

```shell
[
    {"uri":"/etc/workflow/instances/server0/2017-03-08/request_for_activation_1"}
]
```

>[!NOTE]
>
>此`curl`命令可與任何[工作流狀態](/help/sites-administering/workflows.md#workflow-status-and-actions)一起使用，以取代`RUNNING`。

### 如何變更工作流程標題{#how-to-change-the-workflow-title}

要更改工作流控制台的&#x200B;**Instances**&#x200B;頁簽中顯示的&#x200B;**Workflow Title**，請發送`POST`命令：

* 至: `http://localhost:4502/etc/workflow/instances/{id}`

* 搭配下列參數：

   * `action`:其價值必須是：  `UPDATE`
   * `workflowTitle`:工作流程標題

#### 如何使用curl {#how-to-change-the-workflow-title-rest-using-curl}變更工作流程標題 — REST

使用curl的範例：

```shell
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/{id}

# for example
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
```

### 如何列出所有工作流模型{#how-to-list-all-workflow-models}

要獲取所有可用工作流模型的清單，請執行以下GET:

`http://localhost:4502/etc/workflow/models.json`

#### 如何列出所有工作流模型 — 使用curl {#how-to-list-all-workflow-models-rest-using-curl}進行REST

使用curl的範例：

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/models.json
```

>[!NOTE]
>
>另請參閱[管理工作流模型](#managing-workflow-models)。

### 獲取WorkflowSession對象{#obtaining-a-workflowsession-object}

`com.adobe.granite.workflow.WorkflowSession`類可從`javax.jcr.Session`對象或`org.apache.sling.api.resource.ResourceResolver`對象進行調整。

#### 獲取WorkflowSession對象 — Java {#obtaining-a-workflowsession-object-java}

在JSP指令碼（或Servlet類的Java代碼）中，使用HTTP請求對象獲取`SlingHttpServletRequest`對象，該對象提供對`ResourceResolver`對象的訪問。 將`ResourceResolver`物件調整為`WorkflowSession`。

```java
<%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" 
    import="com.adobe.granite.workflow.WorkflowSession,
  org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
%>
```

#### 獲取WorkflowSession對象 — ECMA指令碼{#obtaining-a-workflowsession-object-ecma-script}

使用`sling`變數來取得您用來取得`ResourceResolver`物件的`SlingHttpServletRequest`物件。 將`ResourceResolver`物件調整為`WorkflowSession`物件。

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

### 建立、讀取或刪除工作流模型{#creating-reading-or-deleting-workflow-models}

下列範例顯示如何存取工作流程模型：

* Java和ECMA指令碼的代碼使用`WorkflowSession.createNewModel`方法。
* curl命令直接使用其URL訪問模型。

所用範例：

1. 建立模型（ID為`/var/workflow/models/mymodel/jcr:content/model`）。
1. 刪除模型。

>[!NOTE]
>
>刪除模型會將模型的`metaData`子節點的`deleted`屬性設定為`true`。
>
>刪除不會刪除模型節點。

建立新模型時：

* 工作流模型編輯器要求模型使用`/var/workflow/models`下方的特定節點結構。 模型的父節點必須為`cq:Page`類型，其中`jcr:content`節點具有以下屬性值：

   * `sling:resourceType`: `cq/workflow/components/pages/model`
   * `cq:template`:  `/libs/cq/workflow/templates/model`

   建立模型時，必須先建立此`cq:Page`節點，並使用其`jcr:content`節點作為模型節點的父節點。

* 某些方法識別模型所需的`id`參數是儲存庫中模型節點的絕對路徑：

   `/var/workflow/models/<*model_name>*/jcr:content/model`

   >[!NOTE]
   >
   >請參閱[如何列出所有工作流模型](#how-to-list-all-workflow-models)。

#### 建立、讀取或刪除工作流模型 — Java {#creating-reading-or-deleting-workflow-models-java}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" import="com.adobe.granite.workflow.WorkflowSession,
                 com.adobe.granite.workflow.model.WorkflowModel,
             org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
/* Create the parent page */
String modelRepo = new String("/var/workflow/models");
String modelTemplate = new String ("/libs/cq/workflow/templates/model");
String modelName = new String("mymodel");
Page modelParent = pageManager.create(modelRepo, modelName, modelTemplate, "My workflow model");

/* create the model */
String modelId = new String(modelParent.getPath()+"/jcr:content/model")
WorkflowModel model = wfSession.createNewModel("Made using Java",modelId);

/* delete the model */
wfSession.deleteModel(modelId);
%>
```

#### 建立、讀取或刪除工作流模型 — ECMA指令碼{#creating-reading-or-deleting-workflow-models-ecma-script}

```
var resolver = sling.getRequest().getResource().getResourceResolver();
var wfSession = resolver.adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
var pageManager = resolver.adaptTo(Packages.com.day.cq.wcm.api.PageManager);

//create the parent page node
var workflowPage = pageManager.create("/var/workflow/models", "mymodel", "/libs/cq/workflow/templates/model", "Created via ECMA Script");
var modelId = workflowPage.getPath()+ "/jcr:content/model";
//create the model
var model = wfSession.createNewModel("My Model", modelId);
//delete the model
var model = wfSession.deleteModel(modelId);
```

#### 刪除工作流模型 — 使用curl {#deleting-a-workflow-model-rest-using-curl}進行REST

```shell
# deleting the model by its id
curl -u admin:admin -X DELETE http://localhost:4502/etc/workflow/models/{id}
```

>[!NOTE]
>
>由於需要詳細程度，對於建立和/或讀取模型，curl不被視為實用。

### 檢查工作流狀態{#filtering-out-system-workflows-when-checking-workflow-status}時過濾掉系統工作流

您可以使用[WorkflowStatus API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html)來檢索有關節點的工作流狀態的資訊。

各種方法都有參數：

`excludeSystemWorkflows`

此參數可設為`true`，以指出應將系統工作流程排除在相關結果之外。

您[可以更新OSGi配置](/help/sites-deploying/configuring-osgi.md) **AdobeGranite工作流PayloadMapCache**，該配置指定要作為系統工作流的工作流`Models`。 預設（執行階段）工作流模型為：

* `/var/workflow/models/scheduled_activation/jcr:content/model`
* `/var/workflow/models/scheduled_deactivation/jcr:content/model`

### 超時{#auto-advance-participant-step-after-a-timeout}後的自動提前參與者步驟

如果需要自動提前在預定時間內尚未完成的&#x200B;**參與者**&#x200B;步驟，您可以：

1. 實作OSGI事件接聽程式，以監聽任務建立和修改。
1. 指定逾時（截止時間），然後建立要在該時間觸發的排程Sling工作。
1. 撰寫逾時到期時收到通知的工作處理常式，並觸發工作。

   如果任務尚未完成，此處理程式將對任務執行所需操作

>[!NOTE]
>
>必須明確界定要採取的行動，才能採用這種辦法。

### 與工作流實例{#interacting-with-workflow-instances}交互

以下提供如何與工作流程例項互動（程式設計）的基本範例。

#### 與工作流實例交互 — Java {#interacting-with-workflow-instances-java}

```java
// starting a workflow
WorkflowModel model = wfSession.getModel(workflowId);
WorkflowData wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
Workflow[] workflows workflows = wfSession.getAllWorkflows();
Workflow workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### 與工作流實例交互 — ECMA指令碼{#interacting-with-workflow-instances-ecma-script}

```
// starting a workflow
var model = wfSession.getModel(workflowId);
var wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
var workflows = wfSession.getWorkflows(“RUNNING“);
var workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### 與工作流程例項互動 — 使用curl {#interacting-with-workflow-instances-rest-using-curl}進行REST

* **啟動工作流程**

   ```shell
   # starting a workflow
   curl -d "model={id}&payloadType={type}&payload={payload}" http://localhost:4502/etc/workflow/instances
   
   # for example:
   curl -u admin:admin -d "model=/var/workflow/models/request_for_activation&payloadType=JCR_PATH&payload=/content/we-retail/us/en/products" http://localhost:4502/etc/workflow/instances
   ```

* **列出執行個體**

   ```shell
   # listing the instances
   curl -u admin:admin http://localhost:4502/etc/workflow/instances.json
   ```

   這會列出所有例項；例如：

   ```shell
   [
       {"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_1"}
       ,{"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_2"}
   ]
   ```

   >[!NOTE]
   >
   >請參閱[如何取得所有執行中工作流程的清單](#how-to-get-a-list-of-all-running-workflows-with-their-ids)及其ID，以列出具有特定狀態的例項。

* **暫停工作流程**

   ```shell
   # suspending a workflow
   curl -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **繼續工作流程**

   ```shell
   # resuming a workflow
   curl -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **終止工作流實例**

   ```shell
   # terminating a workflow
   curl -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

### 與工作項{#interacting-with-work-items}交互

以下提供如何（程式化）與工作項目互動的基本範例。

#### 與工作項交互 — Java {#interacting-with-work-items-java}

```java
// querying work items
WorkItem[] workItems = wfSession.getActiveWorkItems();
WorkItem workItem = wfSession.getWorkItem(id);

// getting routes
List<Route> routes = wfSession.getRoutes(workItem);

// delegating
Iterator<Participant> delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### 與工作項交互 — ECMA指令碼{#interacting-with-work-items-ecma-script}

```
// querying work items
var workItems = wfSession.getActiveWorkItems();
var workItem = wfSession.getWorkItem(id);

// getting routes
var routes = wfSession.getRoutes(workItem);

// delegating
var delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### 與工作項目互動 — 使用curl {#interacting-with-work-items-rest-using-curl}進行REST

* **從收件箱中列出工作項**

   ```shell
   # listing the work items
   curl -u admin:admin http://localhost:4502/bin/workflow/inbox
   ```

   將列出當前收件箱中工作項的詳細資訊；例如：

   ```shell
   [{
       "uri_xss": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "uri": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "currentAssignee_xss": "workflow-administrators",
       "currentAssignee": "workflow-administrators",
       "startTime": 1519656289274,
       "payloadType_xss": "JCR_PATH",
       "payloadType": "JCR_PATH",
       "payload_xss": "/content/we-retail/es/es",
       "payload": "/content/we-retail/es/es",
       "comment_xss": "Process resource is null",
       "comment": "Process resource is null",
       "type_xss": "WorkItem",
       "type": "WorkItem"
     },{
       "uri_xss": "configuration/configure_analyticstargeting",
       "uri": "configuration/configure_analyticstargeting",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/securitychecklist",
       "uri": "configuration/securitychecklist",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/enable_collectionofanonymoususagedata",
       "uri": "configuration/enable_collectionofanonymoususagedata",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/configuressl",
       "uri": "configuration/configuressl",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     }
   ```

* **委派工作項**

   ```xml
   # delegating
   curl -d "item={item}&delegatee={delegatee}" http://localhost:4502/bin/workflow/inbox
   
   # for example: 
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_act_1&delegatee=administrators" http://localhost:4502/bin/workflow/inbox
   ```

   >[!NOTE]
   >
   >`delegatee`必須是工作流程步驟的有效選項。

* **完成或推進工作項目到下一步**

   ```xml
   # retrieve the list of routes; the results will be similar to {"results":1,"routes":[{"rid":"233123169","label":"End","label_xss":"End"}]}
   http://localhost:4502/etc/workflow/instances/<path-to-the-workitem>.routes.json
   
   # completing or advancing to the next step; use the appropriate route ID (rid value) from the above list
   curl -d "item={item}&route={route}" http://localhost:4502/bin/workflow/inbox
   
   # for example:
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_activation_1&route=233123169" http://localhost:4502/bin/workflow/inbox
   ```

### 監聽工作流事件{#listening-for-workflow-events}

使用OSGi事件框架監聽[ `com.adobe.granite.workflow.event.WorkflowEvent`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/event/WorkflowEvent.html)類定義的事件。 此類別也提供數種有用的方法，以取得關於事件主題的資訊。 例如， `getWorkItem`方法會針對事件中涉及的工作項目傳回`WorkItem`物件。

下列范常式式碼會定義服務，此服務會監聽工作流程事件並根據事件類型執行工作。

```java
package com.adobe.example.workflow.listeners;

import org.apache.sling.event.jobs.JobProcessor;
import org.apache.sling.event.jobs.JobUtil;

import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;

import com.adobe.granite.workflow.event.WorkflowEvent;
import com.adobe.granite.workflow.exec.WorkItem;

/**
 * The <code>WorkflowEventCatcher</code> class listens to workflow events. 
 */
@Component(metatype=false, immediate=true)
@Service(value=org.osgi.service.event.EventHandler.class)
public class WorkflowEventCatcher implements EventHandler, JobProcessor {

 @Property(value=com.adobe.granite.workflow.event.WorkflowEvent.EVENT_TOPIC)
 static final String EVENT_TOPICS = "event.topics";

 private static final Logger logger = LoggerFactory.getLogger(WorkflowEventCatcher.class);

 public void handleEvent(Event event) {
  JobUtil.processJob(event, this);
 }

 public boolean process(Event event) {
  logger.info("Received event of topic: " + event.getTopic());
  String topic = event.getTopic();

  try {
   if (topic.equals(WorkflowEvent.EVENT_TOPIC)) {
    WorkflowEvent wfevent = (WorkflowEvent)event;
    String eventType = wfevent.getEventType();
    String instanceId = wfevent.getWorkflowInstanceId();

    if (instanceId != null) {
     //workflow instance events
     if (eventType.equals(WorkflowEvent.WORKFLOW_STARTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_RESUMED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_SUSPENDED_EVENT)) {
      // your code comes here...
     } else if (
       eventType.equals(WorkflowEvent.WORKFLOW_ABORTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_COMPLETED_EVENT)) {
      // your code comes here...
     }
     // workflow node event
     if (eventType.equals(WorkflowEvent.NODE_TRANSITION_EVENT)) {
      WorkItem currentItem = (WorkItem) event.getProperty(WorkflowEvent.WORK_ITEM);
      // your code comes here...
     }
    }
   }
  } catch(Exception e){
   logger.debug(e.getMessage());
   e.printStackTrace();
  }
  return true;
 }
}
```
