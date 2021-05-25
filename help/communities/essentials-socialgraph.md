---
title: 社交圖表要點
seo-title: 社交圖表要點
description: 後續元件和下列元件概觀
seo-description: 後續元件和下列元件概觀
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
exl-id: 55aa015e-e0e4-411e-8e28-75006ae3090b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 2%

---

# 社交圖表要點{#social-graph-essentials}

社區成員能夠遵循[活動](essentials-activities.md)並遵循這些活動，具體表現在以下兩個部分：

`follow`元件必須與其他資源關聯，並且此關聯已為[社區站點](overview.md#communitiessites)中的現有社區成員和功能建立。

`following`元件列出當前成員後面或當前成員後面的成員。 此社交圖形中，成員之間關係包含在為社群網站建立的使用者設定檔中。

## 客戶端{#essentials-for-client-side}的要點

### 關注 {#following}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/socialgraph/components/hbs/relationships</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>包括</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.socialgraph</td> 
  </tr>
  <tr>
   <td> <strong>範本</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td> 
  </tr>
  <tr>
   <td> <strong>cs</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td> 
  </tr>
  <tr>
   <td><strong> 屬性</strong></td> 
   <td>請參閱<a href="socialgraph.md">使用社交圖表</a></td> 
  </tr>
  <tr>
   <td><strong> optional<br />屬性</strong></td> 
   <td>
    <ul> 
     <li>名稱: <strong><code>outgoing</code></strong></li> 
     <li>類型：布林值</li> 
     <li>值:<br /> 
      <ul> 
       <li><i>true - </i>元件將 <code>following</code> 列出目前登入成員的成員 <code>follows</code></li> 
       <li><i>false - </i>元件將 <code>following</code> 列出當前登 <code>follow </code>錄成員的成員</li> 
      </ul> </li> 
    </ul> <p>如果屬性遺失，則預設為<i>true</i>。 目前，無法在製作模式中使用編輯對話方塊來設定此屬性。 必須使用<a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>將屬性新增至<code>following </code>節點的例項。</p> </td> 
  </tr>
 </tbody>
</table>

### 關注 {#follow}

| **resourceType** | social/socialgraph/components/hbs/following |
|---|---|
| [**包括**](scf.md#add-or-include-a-communities-component) | 否 |
| **範本** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **cs** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [用戶端自訂](client-customize.md)

## 伺服器端{#essentials-for-server-side}的要點

* [社交圖表API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [社交圖表端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [伺服器端自訂](server-customize.md)
