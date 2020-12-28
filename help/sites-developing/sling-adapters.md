---
title: 使用 Sling 介面卡
seo-title: 使用 Sling 介面卡
description: Sling提供Adapter模式，可方便轉譯實作Appative介面的物件
seo-description: Sling提供Adapter模式，可方便轉譯實作Appative介面的物件
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
translation-type: tm+mt
source-git-commit: 269facfb6351b0b7c73e963ac7c5dc0b57c78a3e
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 1%

---


# 使用 Sling 介面卡{#using-sling-adapters}

[Slingoffers an ](https://sling.apache.org) Adapter  [patterno to fully translate objects that implement the ](https://sling.apache.org/site/adapters.html)  [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) Adaptableinterface.此介面提供通用[adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)方法，將對象轉換為作為參數傳遞的類類型。

例如，要將資源對象轉換為相應的節點對象，您只需執行以下操作：

```java
Node node = resource.adaptTo(Node.class);
```

## 使用案例{#use-cases}

以下是使用案例：

* 取得實作專屬物件。

   例如，通用[`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html)介面的基於JCR的實現提供對基礎JCR [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html)的訪問。

* 建立需要傳遞內部上下文對象的對象的快捷方式。

   例如，以JCR為基礎的[`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html)包含請求的[`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html)參考，而許多將根據該請求作業運作的物件則需要該參考，例如[`PageManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html)或[`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html)。

* 服務的捷徑。

   罕見的案例- `sling.getService()`也很簡單。

### 空返回值{#null-return-value}

`adaptTo()` 可以返回null。

原因有多種，包括：

* 實作不支援目標類型
* 處理此情況的適配器工廠不活動(如 由於缺少服務引用)
* 內部條件失敗
* 服務不可用

請務必妥善處理空值大小寫。 對於jsp渲染，如果jsp失敗，則可能會導致內容為空，這是可接受的。

### 快取{#caching}

為了改善效能，實作可自由快取從`obj.adaptTo()`呼叫傳回的物件。 如果`obj`相同，則返回的對象相同。

此快取會針對所有`AdapterFactory`基本案例執行。

但是，沒有一般規則——物件可以是新例項或現有例項。 這表示您無法依賴這兩種行為。 因此，在`AdapterFactory`內部，對象在此場景中可重複使用非常重要。

### 其運作方式{#how-it-works}

`Adaptable.adaptTo()`有多種實作方式：

* 物體本身；實現方法本身並映射到特定對象。
* 通過[`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)`，可映射任意對象。

   這些對象仍必須實施`Adaptable`介面，並且必須擴展[`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html)（它將`adaptTo`調用傳遞給中央適配器管理器）。

   這允許對現有類（如`Resource`）的`adaptTo`機制進行掛接。

* 兩者的結合。

對於第一種情況，javadocs可以說明`adaptTo-targets`的可能性。 但是，對於特定子類（如基於JCR的資源），通常不可能。 在後一種情況下，`AdapterFactory`的實施通常屬於綁定的私有類，因此不會在客戶端API中公開，也不會列在javadoc中。 從理論上講，從[OSGi](/help/sites-deploying/configuring-osgi.md)服務運行時訪問所有`AdapterFactory`實現並查看其「適配器」（源和目標）配置，但不能將它們相互映射。 最後，這取決於內部邏輯，而內部邏輯必須加以記錄。 因此，這一參考。

## 引用 {#reference}

### Sling {#sling}

[**資**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) 源適應：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>如果這是基於JCR節點的資源或引用節點的JCR屬性。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">屬性</a></td> 
   <td>如果這是基於JCR屬性的資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">項目</a></td> 
   <td>如果這是基於JCR的資源（節點或屬性）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">地圖</a></td> 
   <td>如果這是基於JCR節點的資源（或其他資源支援值映射），則返回屬性的映射。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>如果屬性是基於JCR節點的資源（或其他資源支援值映射），則返回該屬性的方便使用映射。 也可以使用<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code>（處理空大小寫等）來實現（更簡單）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>的擴展，允許在查找屬性時考慮資源的層次。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>如果這是基於JCR節點的資源，並且用戶有權修改該節點上的屬性。<br /> 注意：多個可持續地圖不共用其值。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>傳回「檔案」的二進位內容<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[**資源**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) 解析器適用於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">會話</a></td> 
   <td>請求的JCR會話(如果這是基於JCR的資源解析器（預設）)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">設計人員</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>根據JCR會話，如果這是基於JCR的資源解析器。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>根據JCR會話，如果這是基於JCR的資源解析器。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>根據JCR會話，如果這是基於JCR的資源解析器，以及用戶是否具有訪問UserManager的權限。</td> 
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
   <td>當前用戶的首選項（如果這是基於JCR的資源解析器，則基於JCR會話）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">PreferencesService</a></td> 
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
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">外置式</a></td> 
   <td>用於外部化絕對URL，即使沒有請求物件。<br /> </td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) SlingHttpServletRequestateed適用於：

目標尚未定位，但實施了可適應性，可作為自定義AdapterFactory中的源。

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) SlingHttpServletResponse適用於：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>如果這是吊索重寫回應。</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[**頁**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) 面適應：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">資源</a><br /> </td> 
   <td>頁面資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>標籤資源（==此）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>頁面的節點。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>頁面資源可調整的一切。</td> 
  </tr> 
 </tbody> 
</table>

[**元**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) 件適應：

| [資源](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 元件的資源。 |
|---|---|
| [LakedResource](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | 標籤資源（==此）。 |
| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 元件的節點。 |
| ... | 元件資源可適應的所有內容。 |

[**范**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) 本適應：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">資源</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>範本的資源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>標籤資源（==此）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">節點</a></td> 
   <td>此模板的節點。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>範本資源可以調整的一切。</td> 
  </tr> 
 </tbody> 
</table>

#### 安全性 {#security}

[**可授權**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html)、使 [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) 用者 [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) 和群組適應：

| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 返回用戶／組主節點。 |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | 返回用戶／組主節點的複製狀態。 |

#### DAM {#dam}

[**適**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) 用於：

| [資源](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 資產的資源。 |
|---|---|
| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 資產的節點。 |
| ... | 資產資源可以適應的所有項目。 |

#### 標記 {#tagging}

[**適**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) 用於：

| [資源](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 標籤的資源。 |
|---|---|
| [節點](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 標籤的節點。 |
| ... | 標籤資源可以適應的一切。 |

#### 其他 {#other}

此外，Sling / JCR / OCM也提供自訂OCM（[物件內容對應](https://jackrabbit.apache.org/object-content-mapping.html)）物件的` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)`。
