---
title: 資產代理開發
description: 'Proxy是使用Proxy工作者來處理工作的AEM例項。 瞭解如何設定AEM Proxy、支援的作業、Proxy元件，以及如何開發自訂Proxy工作器。 '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0560d47dcffbf9b74a36ea00e118f8a176adafcd
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---


# 資產代理開發{#assets-proxy-development}

Adobe Experience Manager(AEM)Assets會使用代理來分發特定工作的處理。

Proxy是特定（有時也是個別的）AEM例項，使用proxy工作者做為處理工作和建立結果的處理者。 代理工作器可用於各種任務。 如果是AEM Assets Proxy，則可用來載入資產，以便在AEM Assets中轉譯。 例如，[IDS代理工作者](indesign.md)使用InDesign Server來處理檔案，以便用於AEM Assets。

當proxy是個別的AEM例項時，這有助於降低AEM製作例項的負載。 依預設，AEM Assets會在相同JVM（透過Proxy外部化）中執行資產處理工作，以減少AEM製作例項的負載。

## 代理（HTTP訪問）{#proxy-http-access}

Proxy可透過HTTP Servlet取得，當它設定為接受下列位置的處理工作時：`/libs/dam/cloud/proxy`。 此servlet會從已張貼的參數建立sling工作。 然後，這會新增至代理工作佇列，並連線至適當的代理工作器。

### 支援的操作{#supported-operations}

* `job`

   **需求**:參數必 `jobevent` 須設為序列化值映射。這用於為作業處理器建立`Event`。

   **結果**:新增工作。如果成功，則會傳回唯一的工作ID。

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **需求**:必須 `jobid` 設定參數。

   **結果**:傳回由作業處理者建立之結果節點的JSON表示法。

```shell
curl -u admin:admin -F":operation=result" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502   /libs/dam/cloud/proxy
```

* `resource`

   **需求**:必須設定參數jobid。

   **結果**:返回與給定作業關聯的資源。

```shell
curl -u admin:admin -F":operation=resource" -F"jobid=xxxxxxxxxxxx"
    -F"resourcePath=something.pdf" http://localhost:4502/libs/dam/cloud/proxy
```

* `remove`

   **需求**:必須設定參數jobid。

   **結果**:如果找到作業，則刪除作業。

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### 代理工作器{#proxy-worker}

代理工作者是負責處理作業和建立結果的處理者。 工作者駐留在proxy例項上，且必須實作[sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html)才能辨識為proxy工作者。

>[!NOTE]
>
>工作者必須實作[sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html)才能被辨識為代理工作者。

### 用戶端API {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html) 可作為OSGi服務使用，該服務提供建立作業、刪除作業和從這些作業中獲取結果的方法。此服務的預設實現(`JobServiceImpl`)使用HTTP客戶端與遠程代理Servlet通信。

以下是API使用的範例：

```java
@Reference
 JobService proxyJobService;

 // to create a new job
 final Hashtable props = new Hashtable();
 props.put("someproperty", "some value");
 props.put(JobUtil.PROPERTY_JOB_TOPIC, "myworker/job"); // this is an identifier of the worker
 final String jobId = proxyJobService.addJob(props, new Asset[]{asset});

 // to check status (returns JobService.STATUS_FINISHED or JobService.STATUS_INPROGRESS)
 int status = proxyJobService.getStatus(jobId)

 // to get the result
 final String jsonString = proxyJobService.getResult(jobId);

 // to remove job and cleanup
 proxyJobService.removeJob(jobId);
```

### 雲端服務設定 {#cloud-service-configurations}

>[!NOTE]
>
>[`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/proxy/package-summary.html)下方提供代理API的參考檔案。

Proxy和Proxy工作器組態都可透過雲端服務組態取得，您可從AEM Assets **Tools**&#x200B;主控台或`/etc/cloudservices/proxy`下存取。 每個代理工作器都需要在`/etc/cloudservices/proxy`下添加一個節點，以瞭解特定於工作器的配置詳細資訊（例如`/etc/cloudservices/proxy/workername`）。

>[!NOTE]
>
>如需詳細資訊，請參閱[Indesign Server Proxy Worker設定](indesign.md#configuring-the-proxy-worker-for-indesign-server)和[雲端服務設定](../sites-developing/extending-cloud-config.md)。

以下是API使用的範例：

```java
@Reference(policy = ReferencePolicy.STATIC)
 ProxyConfig proxyConfig;
 
 // to get proxy config
 Configuration cloudConfig = proxyConfig.getConfiguration();
 final String value = cloudConfig.get("someProperty", "defaultValue");

 // to get worker config
 Configuration cloudConfig = proxyConfig.getConfiguration("workername");
 final String value = cloudConfig.get("someProperty", "defaultValue");
```

### 開發自定義的代理工作器{#developing-a-customized-proxy-worker}

[IDS代理工作者](indesign.md)是AEM Assets代理工作者的範例，此代理工作者已提供現成可用的功能，以外包Indesign資產的處理。

您也可以開發和設定您自己的AEM Assets代理工作者，以建立專業工作者，以派送和外包您的AEM Assets處理工作。

要設定您自己的自定義代理工作器，您必須：

* 設定和實作（使用Sling事件）:

   * 自訂工作主題
   * 自訂工作事件處理常式

* 然後，使用JobService API可：

   * 將您的自訂工作分派給代理
   * 管理您的工作

* 如果您想從工作流程使用Proxy，則必須使用WorkflowExternalProcess API和JobService API實作自訂外部步驟。

下圖和步驟詳細說明如何繼續：

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>在以下步驟中，Indesign等效項指示為參考示例。

1. 使用[Sling job](https://sling.apache.org/site/eventing-and-jobs.html)，因此您必須為使用案例定義工作主題。

   例如，請參見`IDSJob.IDS_EXTENDSCRIPT_JOB`以瞭解IDS代理工作器。

1. 外部步驟用來觸發事件，然後等待完成；這是透過輪詢id來完成的。 您必須自行制定實施新功能的步驟。

   實作`WorkflowExternalProcess`，然後使用JobService API和您的工作主題準備工作事件並將其分派到JobService（OSGi服務）。

   例如，請參見`INDDMediaExtractProcess`.java for the IDS proxy worker。

1. 實作主題的工作處理常式。 此處理常式需要開發，以便執行您的特定動作，並視為工作者實作。

   例如，請參見`IDSJobProcessor.java`以瞭解IDS代理工作器。

1. 在dam-commons中使用`ProxyUtil.java`。 這可讓您使用dam代理將工作分派給員工。

>[!NOTE]
>
>AEM Assets proxy架構不提供現成可用的池機制。
>
>InDesign整合可讓您存取InDesign Servers(IDSPool)池。 此集區是Indesign整合專用的，不屬於AEM Assets代理架構的一部分。

>[!NOTE]
>
>結果同步：
>
>使用相同proxy的n個例項時，處理結果會保留在proxy中。 是用戶端（AEM作者）的工作，會使用與建立工作時提供給用戶端的相同唯一工作ID來請求結果。 Proxy只會完成工作，並讓結果隨時可供要求。
