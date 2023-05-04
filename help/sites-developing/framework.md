---
title: AEM 標記框架
seo-title: AEM Tagging Framework
description: 標籤內容並運用AEM標籤基礎結構
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: 55ba5977-217b-4b0f-a794-ddb9216ee62b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 4b680d17-383b-4173-a444-0b7bdb24e6c8
feature: Tagging
exl-id: bae592db-dc36-409f-b841-0582c464c3f6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1800'
ht-degree: 1%

---

# AEM 標記框架{#aem-tagging-framework}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

若要標籤內容並運用AEM標籤基礎結構：

* 標籤必須存在為類型的節點 [`cq:Tag`](#tags-cq-tag-node-type) 在 [分類根節點。](#taxonomy-root-node)
* 標籤的內容節點 `NodeType` 必須包括 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 米辛。
* 此 [TagID](#tagid) 會新增至內容節點的 [`cq:tags`](#tagged-content-cq-tags-property) 屬性，並解析到類型的節點 [`cq:Tag`.](#tags-cq-tag-node-type)

## 標籤：cq：標籤節點類型  {#tags-cq-tag-node-type}

標籤的聲明被捕獲到儲存庫中類型的節點中 `cq:Tag.`

標籤可以是簡單的字詞(例如 `fruit`)或代表階層分類法(例如 `fruit/apple`，即一般水果和更具體的蘋果)。

標籤由唯一的TagID識別。

標籤包含選用的中繼資訊，例如標題、本地化標題和說明。 標題應顯示在使用者介面中，而非 `TagID`，若存在。

標籤架構也能限製作者和網站訪客僅使用特定、預先定義的標籤。

### 標籤特性 {#tag-characteristics}

* 節點類型為 `cq:Tag`.
* 節點名稱是 [`TagID`.](#tagid)
* 此 [`TagID`](#tagid) 一律包含 [命名空間。](#tag-namespace)
* 可選 `jcr:title` 屬性（UI中顯示的標題）
* 可選 `jcr:description` 屬性
* 包含子節點時，稱為 [容器標籤。](#container-tags)
* 它會儲存在存放庫中，位於稱為 [分類根節點。](#taxonomy-root-node)

### 標記 ID {#tagid}

A `TagID` 標識解析到儲存庫中標籤節點的路徑。

通常， `TagID` 是以命名空間開頭的速記，或是絕對開頭的 [分類根節點](#taxonomy-root-node).

當內容經過標籤時，如果內容尚未存在，則 [`cq:tags`](#tagged-content-cq-tags-property) 屬性會新增至內容節點，而 `TagID` 已新增至屬性的字串陣列值。

此 `TagID` 包含a [命名空間](#tag-namespace) 接著是當地 `TagID`. [容器標籤](#container-tags) 具有子標籤，該子標籤表示分類中的分層順序。 子標籤可用來參照與任何本機標籤相同的標籤 `TagID`. 例如，將內容標籤為 `fruit` 即使是具有子標籤的容器標籤，例如 `fruit/apple` 和 `fruit/banana`.

### 分類根節點 {#taxonomy-root-node}

分類根節點是儲存庫中所有標籤的基本路徑。 分類根節點不能是類型的節點 `cq:Tag`.

在AEM中，基本路徑為 `/content/cq:tags` 根節點是 `cq:Folder`.

### 標籤命名空間 {#tag-namespace}

命名空間允許群組項目。 最典型的使用案例是每個網站（例如公用、內部和入口網站）或每個大型應用程式(例如Sites、Assets、Forms)都有命名空間，但命名空間可用於各種其他需求。 使用者介面中使用命名空間，以僅顯示適用於目前內容的標籤子集（即特定命名空間的標籤）。

標籤的命名空間是分類子樹狀結構中的第一層，也就是緊接在 [分類根節點](#taxonomy-root-node). 命名空間是一種節點 `cq:Tag` 其父母 `cq:Tag` 節點類型。

所有標籤都有命名空間。 若未指定命名空間，則會將標籤指派給預設命名空間，也就是 `TagID` `default` (標題為 `Standard Tags`) `/content/cq:tags/default`.

### 容器標籤 {#container-tags}

容器標籤是類型的節點 `cq:Tag` 包含任何數目和類型的子節點，因此可以使用自訂中繼資料增強標籤模型。

此外，分類法中的容器標籤（或超標籤）是所有子標籤的子總和。 例如，標示為的內容 `fruit/apple` 被視為已加上 `fruit` 還有。 這表示搜尋只有標籤的內容 `fruit` 也會找到標籤了的內容 `fruit/apple`.

### 解析TagID {#resolving-tagids}

如果標籤ID包含冒號 `:`，冒號會將命名空間與標籤或子分類法分開，然後以一般斜線分隔 `/`. 如果標籤ID沒有冒號，表示預設命名空間。

標籤的標準且唯一位置如下所示 `/content/cq:tags`.

標籤會參考未指向 `cq:Tag` 節點被視為無效，且會被忽略。

下表顯示一些範例 `TagIDs`、其元素，以及 `TagID` 解析至儲存庫中的絕對路徑。

| `TagID` | 命名空間 | 本機ID | 容器標籤 | 葉標籤 | 絕對儲存庫路徑 |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`、`apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | 無 | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | 無 | 無 | 無 | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### 標籤標題的本地化 {#localization-of-tag-title}

當標籤包含選用的標題字串時(`jcr:title`)可新增屬性，將顯示的標題當地化 `jcr:title.<locale>`.

如需更多詳細資訊，請參閱：

* [不同語言的標籤，](/help/sites-developing/building.md#tags-in-different-languages) 說明API的使用方式。
* [管理不同語言的標籤，](/help/sites-administering/tags.md#managing-tags-in-different-languages) 說明「標籤」控制台的使用。

### 存取控制 {#access-control}

標籤存在於存放庫的 [分類根節點。](#taxonomy-root-node) 您可以在存放庫中設定適當的ACL，借此允許或拒絕作者和網站訪客在指定命名空間中建立標籤。

此外，拒絕某些標籤或命名空間的讀取權限，將可控制將標籤套用至特定內容的能力。

典型配置包括：

* 允許 `tag-administrators` 組/角色寫入訪問所有命名空間(在 `/content/cq:tags`)。
   * 此群組隨附AEM現成可用。
* 允許使用者/作者讀取應讀取之所有命名空間的存取權（大多為）。
* 允許使用者/作者撰寫存取使用者/作者應可自由定義標籤的命名空間(`add_node` 在 `/content/cq:tags/some_namespace`)

## 可標籤內容：cq：可標籤的Mixin {#taggable-content-cq-taggable-mixin}

為了讓應用程式開發人員將標籤附加到內容類型，節點的註冊([CND](https://jackrabbit.apache.org/node-type-notation.html))必須包含 `cq:Taggable` mixin或 `cq:OwnerTaggable` 米辛。

此 `cq:OwnerTaggable` mixin，它繼承自 `cq:Taggable`，旨在指出內容可由擁有者/作者分類。 在AEM中，它只是 `cq:PageContent` 節點。 此 `cq:OwnerTaggable` 標籤架構不需要mixin。

>[!NOTE]
>
>建議只在匯總內容項目的頂層節點（或其上）上啟用標籤 `jcr:content` 節點)。 範例包括：
>
>* 頁面( `cq:Page`)，其中 `jcr:content`節點的類型 `cq:PageContent` 包括 `cq:Taggable` 米辛。
>* 資產( `cq:Asset`)，其中 `jcr:content/metadata` 節點總是有 `cq:Taggable` 米辛。


### 節點類型標籤法(CND) {#node-type-notation-cnd}

儲存庫中的節點類型定義以CND檔案的形式存在。 CND標籤法是JCR檔案中的定義 [此處](https://jackrabbit.apache.org/node-type-notation.html).

AEM中包含之節點類型的基本定義如下：

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

## 標籤的內容：cq:tags屬性 {#tagged-content-cq-tags-property}

此 `cq:tags` 屬性是用來儲存一或多個字串陣列 `TagID`是否由作者或網站訪客套用至內容時。 只有在新增至以 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 米辛。

>[!NOTE]
>
>若要運用AEM標籤功能，自訂開發的應用程式不應定義標籤屬性， `cq:tags`.

## 移動及合併標籤 {#moving-and-merging-tags}

以下說明使用移動或合併標籤時，儲存庫中的效果 [標籤主控台](/help/sites-administering/tags.md):

* 標籤A移動或合併至標籤B時位於 `/content/cq:tags`:

   * 標籤A未刪除，且會取得 `cq:movedTo` 屬性。
   * 標籤B會建立（若有移動）並取得 `cq:backlinks` 屬性。

* `cq:movedTo` 指向標籤B。

   * 此屬性表示標籤A已移動或合併至標籤B。
   * 移動標籤B會據此更新此屬性。 因此，標籤A會隱藏，並僅保留在存放庫中，以解析指向標籤A的內容節點中的標籤ID。
   * 標籤垃圾收集器會再次移除標籤A之類的標籤，不再將內容節點指向它們。
   * 的特殊值 `cq:movedTo` 屬性為 `nirvana`:標籤刪除時會套用，但無法從存放庫中移除，因為存在具有的子標籤 `cq:movedTo` 必須保留。

      >[!NOTE]
      >
      >此 `cq:movedTo` 只有在符合下列任一條件時，才會將屬性新增至移動或合併的標籤：
      >
      >1. 標籤用於內容（亦即有參考）。
      >1. 標籤包含已移動的子項。


* `cq:backlinks` 保留反向的參照，即保留已移至標籤B或與標籤B合併的所有標籤的清單。

   * 這主要是為了保留 `cq:movedTo`屬性，直到標籤B移動/合併/刪除或標籤B啟動時為止，在此情況下，其所有反向連結標籤也必須啟動。

>[!NOTE]
>
>此 `cq:backlinks` 只有在符合下列任一條件時，才會將屬性新增至移動或合併的標籤：
>
>1. 標籤用於內容（亦即有參考）。
>1. 標籤包含已移動的子項。


* 閱讀 `cq:tags` 內容節點的屬性包含下列解析：

   1. 如果下沒有匹配項 `/content/cq:tags`，則不會傳回任何標籤。
   1. 如果標籤具有 `cq:movedTo` 屬性集，則會遵循參考的標籤ID。

      * 只要後面的標籤具有 `cq:movedTo` 屬性。
   1. 如果後面的標籤沒有 `cq:movedTo` 屬性，則會讀取標籤。


* 若要在移動或合併標籤時發佈變更， `cq:Tag` 節點及其所有反向連結都必須複製。
   * 在標籤管理主控台中啟動標籤時，就會自動完成這項作業。

* 稍後更新頁面的 `cq:tags` 屬性會自動清除「舊」參考。
   * 觸發此動作是因為透過API解析移動的標籤會傳回目的地標籤，因而提供目的地標籤ID。

## 標籤移轉 {#tags-migration}

在Adobe Experience Manager 6.4以上，標籤會儲存在 `/content/cq:tags`. 不過，在Adobe Experience Manager已從舊版升級的案例中，標籤仍會顯示在舊位置下 `/etc/tags`. 在升級的系統中，需要將標籤移轉至 `/content/cq:tags`.

>[!NOTE]
>
>在標籤頁面的「頁面屬性」中，建議使用標籤ID(例如 `geometrixx-outdoors:activity/biking`)，而非硬式編碼標籤基本路徑(例如 `/etc/tags/geometrixx-outdoors/activity/biking`)。
>
>要列出標籤， `com.day.cq.tagging.servlets.TagListServlet` 可供使用。

>[!NOTE]
>
>建議使用標籤管理程式API作為資源。

### 如果升級的AEM例項支援TagManager API**

1. 元件開始時，TagManager API會偵測它是否為升級版AEM例項。 在升級的系統中，標籤儲存在 `/etc/tags`.

1. TagManager API接著會以回溯相容模式執行，這表示API會使用 `/etc/tags` 作為基本路徑。 否則會使用新位置 `/content/cq:tags`.

1. 更新標籤位置。

1. 將標籤移轉至新位置後，請執行下列指令碼。

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

指令碼會擷取所有具有 `/etc/tags` 的值 `cq:movedTo/cq:backLinks` 屬性。 然後，它會反覆擷取的結果集，並解析 `cq:movedTo` 和 `cq:backlinks` 屬性值為 `/content/cq:tags` 路徑(在 `/etc/tags` 值中偵測到)。

### 如果升級的AEM執行個體在傳統UI上執行**

>[!NOTE]
>
>傳統UI不符合零停機時間標準，也不支援新的標籤基路徑。 如果您想使用傳統UI，但 `/etc/tags` 需要建立後面 `cq-tagging` 元件重新啟動。

如果升級的AEM例項受TagManager API支援，並在傳統UI中執行：

1. 參考舊標籤基路徑後 `/etc/tags` 替換為使用tagId或新標籤位置 `/content/cq:tags`，您可以將標籤移轉至新位置 `/content/cq:tags` 在CRX DE中，接著重新啟動元件。

1. 將標籤移轉至新位置後，請執行上述指令碼。
