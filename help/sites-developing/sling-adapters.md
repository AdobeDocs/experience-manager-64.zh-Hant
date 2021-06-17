---
title: 使用 Sling 介面卡
seo-title: 使用 Sling 介面卡
description: Sling提供適配器模式，可方便轉換實作可適應介面的物件
seo-description: Sling提供適配器模式，可方便轉換實作可適應介面的物件
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 7780d04d-418e-494c-85c3-76bef5f35690
source-git-commit: dd996d0bb856b9140d420d03dec446a382d10acd
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 1%

---

# 使用 Sling 介面卡{#using-sling-adapters}

[](https://sling.apache.org) Slingoffers an Adapter  [patterforts](https://sling.apache.org/site/adapters.html) 可方便地轉換實現Adaptable介面的 [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 對象。此介面提供通用[adapTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)方法，該方法將對象轉換為作為參數傳遞的類類型。

例如，要將資源對象轉換為相應的Node對象，您只需執行以下操作：

```java
Node node = resource.adaptTo(Node.class);
```

## 使用案例{#use-cases}

有下列使用案例：

* 取得實作專屬物件。

   例如，通用[`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html)介面的基於JCR的實現提供對基礎JCR [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html)的訪問。

* 需要傳遞內部上下文對象的對象的快捷方式建立。

   例如，以JCR為基礎的[`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html)保存對請求的[`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html)的引用，而許多將根據該請求會話工作的對象（如[`PageManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html)或[`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html)）都需要該引用。

* 服務的捷徑。

   少見的案例 — `sling.getService()`也簡單。

### Null返回值{#null-return-value}

`adaptTo()` 可返回null。

原因多種多樣，包括：

* 實作不支援目標類型
* 處理此情況的適配器工廠不活動(例如 因為缺少服務引用)
* 內部條件失敗
* 服務不可用

請務必優雅地處理空大小寫。 對於jsp呈現，如果jsp失敗會導致內容為空，則可能是可接受的。

### 快取 {#caching}

為了改善效能，實施可免費快取從`obj.adaptTo()`呼叫傳回的物件。 如果`obj`相同，則返回的對象相同。

會針對所有`AdapterFactory`案例執行此快取。

但是，沒有一般規則 — 物件可以是新例項或現有例項。 這表示您無法依賴任何一種行為。 因此，尤其在`AdapterFactory`內，對象在此情境中可重複使用非常重要。

### 其運作方式{#how-it-works}

`Adaptable.adaptTo()`有多種實施方式：

* 物體本身；實作方法本身並對應至特定物件。
* 由[`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)映射任意對象。

   對象仍必須實現`Adaptable`介面，並且必須擴展[`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html)（它將`adaptTo`調用傳遞給中央適配器管理器）。

   這允許將掛接到現有類的`adaptTo`機制，如`Resource`。

* 兩者結合。

對於第一種情況，Javadoc可以說明`adaptTo-targets`的可能性。 但是，對於特定子類（例如基於JCR的資源），這通常是不可能的。 在後一種情況下，`AdapterFactory`的實施通常是套件組合的專用類的一部分，因此不會在客戶端API中公開，也不會列在javadoc中。 理論上，從[OSGi](/help/sites-deploying/configuring-osgi.md)服務運行時訪問所有`AdapterFactory`實施並查看其「adaptables」（源和目標）配置，但不能將它們相互映射。 最後，這取決於內部邏輯，必須加以記錄。 因此，這個參考。

## 引用 {#reference}

### Sling {#sling}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) 資源適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>如果這是基於JCR的資源或引用節點的JCR屬性。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">屬性</a></td> 
   <td>如果這是JCR型屬性型資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">項目</a></td> 
   <td>如果這是以JCR為基礎的資源（節點或屬性）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">地圖</a></td> 
   <td>如果這是基於JCR節點的資源（或其他資源支援值映射），則返回屬性的映射。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>如果屬性是基於JCR節點的資源（或其他資源支援值映射），則返回屬性的方便使用映射。 也可以使用<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code>（處理空大小寫等）來達到（更簡單）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>的擴展，允許在查找屬性時考慮資源的層次結構。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>如果這是JCR節點型資源，且使用者擁有修改該節點上屬性的權限。<br /> 注意：多個可持續映射不共用其值。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>傳回「檔案」的二進位內容<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) ResourceResolver適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">工作階段</a></td> 
   <td>如果這是以JCR為基礎的資源解析器（預設），則要求的JCR工作階段。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">元件管理器</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">設計工具</a></td> 
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
   <td>用於外部化絕對URL，即使沒有要求物件。<br /> </td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) SlingHttpServletRequest適應於：

尚無目標，但實施了可適應性，可作為自定義AdapterFactory中的源。

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) SlingHttpServletResponse適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>如果這是Sling重寫程式回應。</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) 頁面適應：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">資源</a><br /> </td> 
   <td>頁面的資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>標示為資源(==此)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>頁面的節點。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>頁面資源可調整的所有項目。</td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) 元件適應於：

| [資源](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 元件的資源。 |
|---|---|
| [LakedResource](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | 標示為資源(==此)。 |
| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 元件的節點。 |
| ... | 元件資源可適用於的所有項目。 |

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) 範本適應於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">資源</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>範本的資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>標示為資源(==此)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>此模板的節點。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>範本資源可調整的所有項目。</td> 
  </tr> 
 </tbody> 
</table>

#### 安全性 {#security}

[**可授權**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html)、使 [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) 用者 [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) 和群組適應：

| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 返回用戶/組首節點。 |
|---|---|
| [複製狀態](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | 返回用戶/組主節點的複製狀態。 |

#### DAM {#dam}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) 資產適應於：

| [資源](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 資產的資源。 |
|---|---|
| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 資產的節點。 |
| ... | 資產資源可適應的所有項目。 |

#### 標記 {#tagging}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) 標籤適應：

| [資源](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 標籤的資源。 |
|---|---|
| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 標籤的節點。 |
| ... | 標籤資源可調整的所有項目。 |

#### 其他 {#other}

此外，Sling / JCR / OCM也為自訂OCM（[物件內容對應](https://jackrabbit.apache.org/object-content-mapping.html)）物件提供` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)`。
