---
title: Assets Proxy Development
description: 代理是 [!DNL Experience Manager] 使用代理工作處理作業的實例。 了解如何設定 [!DNL Experience Manager] 代理、支援的操作、代理元件以及如何開發自定義代理工作器。
contentOwner: AG
feature: Asset Processing
role: Admin, Architect
exl-id: c7511326-697e-4749-ab46-513cdbaa00d8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---

# Assets Proxy Development {#assets-proxy-development}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets會使用代理來分發特定工作的處理作業。

代理是特定（有時也是獨立的） [!DNL Experience Manager] 使用代理工作者作為處理者，負責處理工作並建立結果的實例。 代理工作器可用於各種任務。 若 [!DNL Experience Manager] Assets Proxy此設定可用來載入資產以在內呈現 [!DNL Experience Manager] 資產。 例如， [IDS代理工作程式](indesign.md) 使用InDesign Server來處理要用於 [!DNL Experience Manager] 資產。

當代理為獨立 [!DNL Experience Manager] 例項有助於降低 [!DNL Experience Manager] 製作例項。 依預設， [!DNL Experience Manager] 資產會在相同JVM中執行資產處理任務（透過Proxy外部化），以減少 [!DNL Experience Manager] 製作例項。

## 代理（HTTP訪問） {#proxy-http-access}

當代理設定為接受處理作業時，可通過HTTP Servlet使用： `/libs/dam/cloud/proxy`. 此Servlet會從發佈的參數建立Sling作業。 然後，此代碼將添加到代理作業隊列，並連接到相應的代理工作器。

### 支援的操作 {#supported-operations}

* `job`

   **需求**:參數 `jobevent` 必須設定為序列化值映射。 這可用來建立 `Event` 處理者。

   **結果**:新增工作。 如果成功，則會傳回唯一的工作ID。

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **需求**:參數 `jobid` 必須設定。

   **結果**:返回由作業處理器建立的結果節點的JSON表示。

```shell
curl -u admin:admin -F":operation=result" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502   /libs/dam/cloud/proxy
```

* `resource`

   **需求**:必須設定參數jobid。

   **結果**:傳回與指定作業相關聯的資源。

```shell
curl -u admin:admin -F":operation=resource" -F"jobid=xxxxxxxxxxxx"
    -F"resourcePath=something.pdf" http://localhost:4502/libs/dam/cloud/proxy
```

* `remove`

   **需求**:必須設定參數jobid。

   **結果**:如果找到作業，則刪除該作業。

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### 代理工作人員 {#proxy-worker}

代理工作人員是負責處理作業和建立結果的處理器。 工作程式位於代理執行個體上，必須實作 [sling作業處理器](https://sling.apache.org/site/eventing-and-jobs.html) 被認定為代理工作者。

>[!NOTE]
>
>工作人員必須實施 [sling作業處理器](https://sling.apache.org/site/eventing-and-jobs.html) 被認定為代理工作者。

### 用戶端API {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html) 可作為OSGi服務使用，該服務提供建立作業、移除作業以及從這些作業中獲取結果的方法。 此服務的預設實作(`JobServiceImpl`)使用HTTP用戶端與遠端代理servlet通訊。

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
>Proxy API的參考檔案位於 [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/commons/proxy/package-summary.html).

Proxy和Proxy工作程式設定皆可透過雲端服務設定取得，可從 [!DNL Experience Manager] 資產 **工具** 主控台或 `/etc/cloudservices/proxy`. 每個代理工作程式應在 `/etc/cloudservices/proxy` 對於工作器特定配置詳細資訊(例如， `/etc/cloudservices/proxy/workername`)。

>[!NOTE]
>
>請參閱 [Indesign Server代理工作器配置](indesign.md#configuring-the-proxy-worker-for-indesign-server) 和 [Cloud Services設定](../sites-developing/extending-cloud-config.md) 以取得更多資訊。

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

### 開發自定義代理工作器 {#developing-a-customized-proxy-worker}

此 [IDS代理工作程式](indesign.md) 是 [!DNL Experience Manager] 已提供現成可用的資產代理工作人員，以委外處理Indesign資產。

您也可以開發和設定自己的 [!DNL Experience Manager] 資產代理員工，以建立專業員工來派送和外包您的 [!DNL Experience Manager] 資產處理工作。

設定您自己的自訂代理工作程式時，您必須：

* 設定和實作（使用Sling事件）:

   * 自訂工作主題
   * 自訂工作事件處理常式

* 然後使用JobService API來執行下列動作：

   * 將自訂作業派送給代理
   * 管理您的作業

* 如果您想從工作流程使用代理，必須使用WorkflowExternalProcess API和JobService API實作自訂外部步驟。

下列圖表和步驟詳細說明如何繼續：

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>在以下步驟中，將Indesign等效項指示為參考示例。

1. A [Sling作業](https://sling.apache.org/site/eventing-and-jobs.html) ，因此您需要為使用案例定義工作主題。

   例如，請參閱 `IDSJob.IDS_EXTENDSCRIPT_JOB` IDS代理工作程式。

1. 外部步驟用於觸發事件，然後等待完成；這是透過輪詢id來完成。 您必須自行開發步驟，才能實作新功能。

   實作 `WorkflowExternalProcess`，然後使用JobService API和您的工作主題準備工作事件，並將其發送到JobService（OSGi服務）。

   例如，請參閱 `INDDMediaExtractProcess`.java（用於IDS代理工作器）。

1. 實作主題的工作處理常式。 此處理常式需要開發，以便執行您的特定動作，且視為背景實作。

   例如，請參閱 `IDSJobProcessor.java` IDS代理工作程式。

1. 善用 `ProxyUtil.java` 在dam-commons中。 這可讓您使用dam代理將工作分派給員工。

>[!NOTE]
>
>什麼 [!DNL Experience Manager] 池機制是資產代理框架不提供現成可用的。
>
>InDesign整合允許訪問內部設計伺服器池(IDSPool)。 此集區是Indesign整合專屬，而非 [!DNL Experience Manager] 資產代理架構。

>[!NOTE]
>
>結果同步：
>
>若有n個例項使用相同的Proxy，處理結果會與Proxy一起。 這是客戶端的作業([!DNL Experience Manager] 作者)，使用與建立工作時提供給用戶端的相同唯一作業ID來請求結果。 代理只需完成該作業，並使結果準備好被請求。
