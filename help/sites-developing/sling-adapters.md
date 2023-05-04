---
title: 使用 Sling 介面卡
seo-title: Using Sling Adapters
description: Sling提供適配器模式，可方便轉換實作可適應介面的物件
seo-description: Sling offers an Adapter pattern to conveniently translate objects that implement the Adaptable interface
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 7780d04d-418e-494c-85c3-76bef5f35690
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1753'
ht-degree: 14%

---

# 使用 Sling 介面卡{#using-sling-adapters}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

[Sling](https://sling.apache.org) 選件 [適配器模式](https://sling.apache.org/site/adapters.html) 方便地轉換實現 [適應性](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 介面。 此介面提供一般 [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 將物件轉譯為要作為引數傳遞的類別類型的方法。

例如，要將資源對象轉換為相應的Node對象，您只需執行以下操作：

```java
Node node = resource.adaptTo(Node.class);
```

## 使用案例 {#use-cases}

有下列使用案例：

* 取得實作專屬物件。

   例如，以JCR為基礎的一般實作 [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) 介面提供對基礎JCR的訪問 [`Node`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* 需要傳遞內部上下文對象的對象的快捷方式建立。

   例如，以JCR為基礎 [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) 保有對請求的引用 [`JCR Session`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html)，而許多物件則需要此工作階段，例如 [`PageManager`](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) 或 [`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* 服務的捷徑。

   罕見的案例。 `sling.getService()` 也很簡單。

### Null返回值 {#null-return-value}

`adaptTo()` 可返回null。

原因多種多樣，包括：

* 實作不支援目標類型
* 處理此情況的適配器工廠不活動(例如 因為缺少服務引用)
* 內部條件失敗
* 服務不可用

請務必優雅地處理空大小寫。 對於jsp呈現，如果jsp失敗會導致內容為空，則可能是可接受的。

### 快取 {#caching}

為了改善效能，實施可免費快取從 `obj.adaptTo()` 呼叫。 若 `obj` 相同，則傳回的物件相同。

會針對所有使用者執行此快取 `AdapterFactory` 根據案例。

但是，沒有一般規則 — 物件可以是新例項或現有例項。 這表示您無法依賴任何一種行為。 因此，它很重要，尤其是內部 `AdapterFactory`，即物件可在此案例中重複使用。

### 運作方式 {#how-it-works}

有多種方式 `Adaptable.adaptTo()` 可實作：

* 物體本身；實作方法本身並對應至特定物件。
* 按 [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)，可映射任意對象。

   物件仍必須實作 `Adaptable` 介面和必須擴充 [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (通過 `adaptTo` 呼叫中央適配器管理器)。

   這可讓鈎點進入 `adaptTo` 現有類的機制，例如 `Resource`.

* 兩者結合。

在第一種情況中，Javadoc可以說明 `adaptTo-targets` 都是可能的。 但是，對於特定子類（例如基於JCR的資源），這通常是不可能的。 在後一種情況下， `AdapterFactory` 通常是套件組合的專用類別的一部分，因此在用戶端API中不會公開，也不會列在javadoc中。 從理論上講，可以訪問所有 `AdapterFactory` 實施 [OSGi](/help/sites-deploying/configuring-osgi.md) 服務運行時並查看其「適配器」（源和目標）配置，但不將它們相互映射。 最後，這取決於內部邏輯，必須加以記錄。 因此，這個參考。

## 參考 {#reference}

### Sling {#sling}

[**資源**](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) 適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>如果這是基於JCR的資源或引用節點的JCR屬性。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">屬性</a></td> 
   <td>如果這是JCR型屬性型資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">項目</a></td> 
   <td>如果這是以JCR為基礎的資源（節點或屬性）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">地圖</a></td> 
   <td>如果這是基於JCR節點的資源（或其他資源支援值映射），則返回屬性的映射。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>如果屬性是基於JCR節點的資源（或其他資源支援值映射），則返回屬性的方便使用映射。 也可使用<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> （處理空大小寫等）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td> 
   <td>的擴充功能 <a href="https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> 這可讓您在尋找屬性時考慮資源的階層。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>如果這是JCR節點型資源，且使用者擁有修改該節點上屬性的權限。<br /> 注意：多個可持續映射不共用其值。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>傳回「檔案」的二進位內容<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[**ResourceResolver**](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) 適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">工作階段</a></td> 
   <td>如果這是以JCR為基礎的資源解析器（預設），則要求的JCR工作階段。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">元件管理器</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>根據JCR工作階段，如果這是以JCR為基礎的資源解析器。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>根據JCR工作階段，如果這是以JCR為基礎的資源解析器。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>根據JCR工作階段，如果這是以JCR為基礎的資源解析器，以及使用者是否具有存取UserManager的權限。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">可授權項目</a> </td> 
   <td>目前的使用者。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">使用者</a><br /> </td> 
   <td>目前的使用者。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/privileges/PrivilegeManager.html">PrivilegeManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/Preferences.html">偏好設定</a></td> 
   <td>目前使用者的偏好設定（如果這是以JCR為基礎的資源解析器，則以JCR工作階段為基礎）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">首選項服務</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/auth/pin/PinManager.html">PinManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">外置器</a></td> 
   <td>用於外部化絕對URL，即使沒有要求物件亦然。<br /> </td> 
  </tr> 
 </tbody> 
</table>

[**SlingHttpServletRequest**](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) 適應於：

尚無目標，但實施了可適應性，可作為自定義AdapterFactory中的源。

[**SlingHttpServletResponse**](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) 適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>如果這是Sling重寫程式回應。</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[**頁面**](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) 適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td> 
   <td>頁面的資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>標示為資源(==此)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>頁面的節點。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>頁面資源可調整的所有項目。</td> 
  </tr> 
 </tbody> 
</table>

[**元件**](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) 適應於：

| [Resource](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 元件的資源。 |
|---|---|
| [LakedResource](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | 標示為資源(==此)。 |
| [節點](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 元件的節點。 |
| ... | 元件資源可適用於的所有項目。 |

[**範本**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) 適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>範本的資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>標示為資源(==此)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>此模板的節點。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>範本資源可調整的所有項目。</td> 
  </tr> 
 </tbody> 
</table>

#### 安全性 {#security}

[**可授權**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html), [**使用者**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) 和 [**群組**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) 適應：

| [節點](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 返回用戶/組首節點。 |
|---|---|
| [複製狀態](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | 返回用戶/組主節點的複製狀態。 |

#### DAM {#dam}

[**資產**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) 適應於：

| [Resource](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 資產的資源。 |
|---|---|
| [節點](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 資產的節點。 |
| ... | 資產資源可適應的所有項目。 |

#### 標記 {#tagging}

[**標籤**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) 適應於：

| [Resource](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 標籤的資源。 |
|---|---|
| [節點](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 標籤的節點。 |
| ... | 標籤資源可調整的所有項目。 |

#### 其他 {#other}

此外，Sling / JCR / OCM也提供 ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` 針對自訂OCM([物件內容對應](https://jackrabbit.apache.org/object-content-mapping.html))物件。
