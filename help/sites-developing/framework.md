---
title: 標AEM記框架
seo-title: AEM Tagging Framework
description: 標籤內容並利用標AEM記基礎架構
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: 55ba5977-217b-4b0f-a794-ddb9216ee62b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 4b680d17-383b-4173-a444-0b7bdb24e6c8
feature: Tagging
exl-id: bae592db-dc36-409f-b841-0582c464c3f6
source-git-commit: 381e760d1634dec6c6cdb933fd4da6b4652e6ff7
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 0%

---

# 標AEM記框架{#aem-tagging-framework}

要標籤內容並利用標籤基礎AEM架構：

* 標籤必須作為類型的節點存在 [`cq:Tag`](#tags-cq-tag-node-type) 下 [分類根節點。](#taxonomy-root-node)
* 標籤內容節點的 `NodeType` 必須包括 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 混音。
* 的 [標籤ID](#tagid) 添加到內容節點的 [`cq:tags`](#tagged-content-cq-tags-property) 屬性並解析為類型的節點 [`cq:Tag`。](#tags-cq-tag-node-type)

## 標籤：cq：標籤節點類型  {#tags-cq-tag-node-type}

標籤的聲明將捕獲在類型節點的儲存庫中 `cq:Tag.`

標籤可以是簡單單詞(例如， `fruit`)或表示分層分類(例如 `fruit/apple`意思是，既包括水果，也包括更具體的蘋果)。

標籤由唯一的TagID標識。

標籤具有可選的元資訊，如標題、本地化標題和說明。 標題應顯示在用戶介面中，而不是 `TagID`，當存在時。

標籤框架還允許限製作者和站點訪問者僅使用特定的預定義標籤。

### 標籤特性 {#tag-characteristics}

* 節點類型為 `cq:Tag`。
* 節點名稱是 [`TagID`。](#tagid)
* 的 [`TagID`](#tagid) 始終包括 [命名空間。](#tag-namespace)
* 可選 `jcr:title` 屬性（要在UI中顯示的標題）
* 可選 `jcr:description` 屬性
* 包含子節點時，稱為 [容器標籤。](#container-tags)
* 它儲存在儲存庫中名為 [分類根節點。](#taxonomy-root-node)

### 標記 ID {#tagid}

A `TagID` 標識解析為儲存庫中標籤節點的路徑。

通常， `TagID` 是以命名空間開頭的速記，或者它可以從 [分類根節點](#taxonomy-root-node)。

當內容被標籤時，如果內容尚不存在， [`cq:tags`](#tagged-content-cq-tags-property) 屬性將添加到內容節點， `TagID` 添加到屬性的字串陣列值。

的 `TagID` 由 [命名空間](#tag-namespace) 接著是當地人 `TagID`。 [容器標籤](#container-tags) 具有表示分類中分層順序的子標籤。 子標籤可用於引用與任何本地標籤相同的標籤 `TagID`。 例如，用 `fruit` 允許，即使它是帶有子標籤的容器標籤，如 `fruit/apple` 和 `fruit/banana`。

### 分類根節點 {#taxonomy-root-node}

分類根節點是儲存庫中所有標籤的基本路徑。 分類根節點不能是類型的節點 `cq:Tag`。

在AEM中，基本路徑為 `/content/cq:tags` 根節點的類型 `cq:Folder`。

### 標籤命名空間 {#tag-namespace}

命名空間允許組內容。 最典型的使用情形是每個站點（例如，公共、內部和門戶）或每個較大的應用程式(例如，站點、資產、Forms)都有一個命名空間，但命名空間可用於各種其他需要。 在用戶介面中使用命名空間只顯示適用於當前內容的標籤子集（即特定命名空間的標籤）。

標籤的命名空間是分類子樹中的第一級，即緊靠在 [分類根節點](#taxonomy-root-node)。 命名空間是類型的節點 `cq:Tag` 其父母不是 `cq:Tag` 節點類型。

所有標籤都具有命名空間。 如果未指定命名空間，則將標籤分配給預設命名空間， `TagID` `default` （標題） `Standard Tags`) `/content/cq:tags/default`。

### 容器標籤 {#container-tags}

容器標籤是類型的節點 `cq:Tag` 包含任意數量和類型的子節點，這使用自定義元資料增強標籤模型成為可能。

此外，分類中的容器標籤（或超標籤）用作所有子標籤的子總和。 例如，標籤為 `fruit/apple` 被視為帶有 `fruit` 也是。 這意味著搜索僅使用 `fruit` 還會找到標有 `fruit/apple`。

### 解析標籤ID {#resolving-tagids}

如果標籤ID包含冒號 `:`，冒號將命名空間與標籤或子分類分開，然後用正常斜槓分開 `/`。 如果標籤ID沒有冒號，則預設命名空間為默示命名空間。

標籤的標準和唯一位置低於 `/content/cq:tags`。

引用不指向的非現有路徑或路徑的標籤 `cq:Tag` 節點被視為無效且被忽略。

下表顯示了一些示例 `TagIDs`它們的元素，以及 `TagID` 解析為儲存庫中的絕對路徑。

| `TagID` | 命名空間 | 本地ID | 容器標籤 | 葉標籤 | 絕對儲存庫路徑 |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | 無 | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | 無 | 無 | 無 | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### 標籤標題的本地化 {#localization-of-tag-title}

當標籤包含可選標題字串(`jcr:title`)可以通過添加屬性來本地化顯示標題 `jcr:title.<locale>`。

有關詳細資訊，請參閱：

* [不同語言的標籤，](/help/sites-developing/building.md#tags-in-different-languages) 描述API的使用。
* [管理不同語言的標籤，](/help/sites-administering/tags.md#managing-tags-in-different-languages) 描述了「標籤」控制台的使用。

### 存取控制 {#access-control}

標籤作為節點存在於 [分類根節點。](#taxonomy-root-node) 允許或拒絕作者和站點訪問者在給定命名空間中建立標籤的能力可以通過在儲存庫中設定適當的ACL來實現。

此外，拒絕某些標籤或命名空間的讀取權限將控制將標籤應用於特定內容的能力。

典型配置包括：

* 允許 `tag-administrators` 組/角色寫入訪問所有命名空間（在下添加/修改） `/content/cq:tags`)。
   * 這組AEM帶有現成功能。
* 允許用戶/作者讀取對應可讀取的所有命名空間（大多為所有命名空間）的訪問權限。
* 允許用戶/作者對用戶/作者可自由定義標籤的命名空間進行寫入訪問(`add_node` 在 `/content/cq:tags/some_namespace`)

## 可聚集內容：cq：可聚集混合 {#taggable-content-cq-taggable-mixin}

為了讓應用程式開發人員將標籤附加到內容類型，節點的註冊([CND](https://jackrabbit.apache.org/node-type-notation.html))必須包括 `cq:Taggable` 混合或 `cq:OwnerTaggable` 混音。

的 `cq:OwnerTaggable` mixin，它繼承自 `cq:Taggable`，意在表示內容可以由所有者/作者分類。 在AEM中，它只是 `cq:PageContent` 的下界。 的 `cq:OwnerTaggable` 標籤框架不需要mixin。

>[!NOTE]
>
>建議僅在聚合內容項的頂級節點上（或其上）啟用標籤 `jcr:content` 節點)。 示例包括：
>
>* 頁面( `cq:Page`) `jcr:content`節點的類型 `cq:PageContent` 包括 `cq:Taggable` 混音。
>* 資產( `cq:Asset`) `jcr:content/metadata` 節點始終具有 `cq:Taggable` 混音。


### 節點類型表示法(CND) {#node-type-notation-cnd}

節點類型定義作為CND檔案存在於儲存庫中。 CND表示法定義為JCR文檔的一部分 [這裡](https://jackrabbit.apache.org/node-type-notation.html)。

包含在中的節點類型的基本AEM定義如下：

```text
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## 標籤內容：cq：標籤屬性 {#tagged-content-cq-tags-property}

的 `cq:tags` 屬性是用於儲存一個或多個字串的陣列 `TagID`當作者或站點訪問者將它們應用於內容時。 僅當添加到使用 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 混音。

>[!NOTE]
>
>要利用標AEM記功能，自定義開發的應用程式不應定義標籤屬性 `cq:tags`。

## 移動和合併標籤 {#moving-and-merging-tags}

以下是在使用 [標籤控制台](/help/sites-administering/tags.md):

* 當標籤A被移動或合併到標籤B中時 `/content/cq:tags`:

   * 未刪除標籤A並獲取 `cq:movedTo` 屬性。
   * 標籤B已建立（如果移動）並獲取 `cq:backlinks` 屬性。

* `cq:movedTo` 指向標籤B。

   * 此屬性表示標籤A已被移動或合併到標籤B中。
   * 移動標籤B將相應更新此屬性。 因此標籤A被隱藏，並且僅被保存在儲存庫中以解析指向標籤A的內容節點中的標籤ID。
   * 標籤垃圾收集器會刪除標籤A等標籤，不再再將內容節點指向它們。
   * 的特殊值 `cq:movedTo` 屬性 `nirvana`:在刪除標籤但無法從儲存庫中刪除時應用該標籤，因為存在帶有子標籤的 `cq:movedTo` 必須保留。

      >[!NOTE]
      >
      >的 `cq:movedTo` 僅當滿足以下任一條件時，才會將屬性添加到已移動或合併的標籤：
      >
      >1. 標籤用於內容（意味著它有引用）。
      >1. 標籤包含已移動的子項。


* `cq:backlinks` 將引用保持在另一個方向，即保留已移動到標籤B或與標籤B合併的所有標籤的清單。

   * 這大部分是為了 `cq:movedTo`屬性，當標籤B被移動/合併/刪除或標籤B被激活時，其所有後連結標籤也必須被激活。

>[!NOTE]
>
>的 `cq:backlinks` 僅當滿足以下任一條件時，才會將屬性添加到已移動或合併的標籤：
>
>1. 標籤用於內容（意味著它有引用）。
>1. 標籤包含已移動的子項。


* 讀取 `cq:tags` 內容節點的屬性涉及以下解析：

   1. 如果下面沒有匹配項 `/content/cq:tags`，不返回標籤。
   1. 如果標籤具有 `cq:movedTo` 屬性集，引用的標籤ID後跟。

      * 只要後續標籤具有 `cq:movedTo` 屬性。
   1. 如果跟隨的標籤沒有 `cq:movedTo` 屬性，標籤將被讀取。


* 要在移動或合併標籤時發佈更改， `cq:Tag` 必須複製節點及其所有回鏈。
   * 在標籤管理控制台中激活標籤時，將自動執行此操作。

* 以後對頁面的更新 `cq:tags` 屬性自動清除「舊」引用。
   * 觸發此觸發是因為通過API解析移動的標籤返回目標標籤，從而提供目標標籤ID。

## 標籤遷移 {#tags-migration}

在Adobe Experience Manager6.4以後，標籤在 `/content/cq:tags`。 但是，在Adobe Experience Manager已從以前版本升級的情況下，標籤仍在舊位置下 `/etc/tags`。 在升級的系統中，需要將標籤遷移到 `/content/cq:tags`。

>[!NOTE]
>
>在「標籤的頁屬性」頁中，建議使用標籤ID(例如 `geometrixx-outdoors:activity/biking`)而不是硬編碼標籤基路徑(例如， `/etc/tags/geometrixx-outdoors/activity/biking`)。
>
>要列出標籤， `com.day.cq.tagging.servlets.TagListServlet` 可使用。

>[!NOTE]
>
>建議使用標籤管理器API作為資源。

### 如果升AEM級的實例支援TagManager API**

1. 在元件啟動時，TagManager API將檢測它是否是升級的實AEM例。 在升級的系統中，標籤儲存在 `/etc/tags`。

1. 然後，TagManager API在向後相容模式下運行，這意味著API使用 `/etc/tags` 作為基本路徑。 否則，將使用新位置 `/content/cq:tags`。

1. 更新標籤位置。

1. 將標籤遷移到新位置後，運行以下指令碼。

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
        def tagPath = node.path;
        println "tag = ${tagPath}";

        if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags")){

                def movedTo = node.getProperty("cq:movedTo").getValue().toString();

                println "cq:movedTo = ${movedTo} \n";

                movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
                node.setProperty("cq:movedTo",movedTo);
        } else if(node.hasProperty("cq:backlinks")){

               String[] backLinks = node.getProperty("cq:backlinks").getValues();
               int count = 0;

               backLinks.each { value ->
                       if(value.startsWith("/etc/tags")){
                               println "cq:backlinks = ${value}\n";
                               backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
                       count++;
               }

               node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

指令碼將讀取所有具有 `/etc/tags` 值 `cq:movedTo/cq:backLinks` 屬性。 然後，它迭代讀取的結果集並解析 `cq:movedTo` 和 `cq:backlinks` 屬性值 `/content/cq:tags` 路徑(在 `/etc/tags` 在值中檢測到)。

### 如果升級AEM的實例在經典UI**上運行

>[!NOTE]
>
>標準UI不符合零停機時間，不支援新的標籤基本路徑。 如果要使用傳統UI `/etc/tags` 需要建立後跟 `cq-tagging` 元件重新啟動。

如果升級的實AEM例受TagManager API支援，並在Classic UI中運行：

1. 一次引用舊標籤基路徑 `/etc/tags` 替換為使用tagId或新標籤位置 `/content/cq:tags`，可以將標籤遷移到新位置 `/content/cq:tags` 在CRX DE中，然後重新啟動元件。

1. 將標籤遷移到新位置後，運行上述指令碼。
