---
title: SRP and UGC Essentials
seo-title: SRP and UGC Essentials
description: Storage resource provider and user-generated content overview
seo-description: Storage resource provider and user-generated content overview
uuid: a4ee8725-f554-4fcf-ac1e-34878d6c02f8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0763f236-5648-49e9-8a24-dbc8f4c77ee3
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# SRP and UGC Essentials {#srp-and-ugc-essentials}

## 簡介 {#introduction}

如果不熟悉儲存資源提供商(SRP)及其與用戶生成內容(UGC)的關係，請訪問 [社區內容儲存](working-with-srp.md)[和儲存資源提供商概述](srp.md)。

This section of the documentation provides some essential information about SRP and UGC.

## StorageResourceProvider API {#storageresourceprovider-api}

SocialResourceProvider API(SRP API)是各種Sling Resource Provider API的擴充功能。 It includes support for pagination and atomic increment (useful for tally and scoring).

Queries are necessary for SCF components as there is the need to sort by date, helpfulness, number of votes, and so on. All SRP options have flexible query mechanisms which do not rely on bucketing.

The SRP storage location incorporates the component path. SRP API應一律用於存取UGC，因為根路徑取決於所選SRP選項，例如ASRP、MSRP或JSRP。

SRP API不是抽象類，它是介面。 A custom implementation should not be undertaken lightly, as the benefits of future improvements to internal implementations would be missed when upgrading to a new release.

The means for using the SRP API are through provided utilities, such as those found in the SocialResourceUtilities package.

When upgrading from AEM 6.0 or earlier, it will be necessary to migrate UGC for all SRPs, for which an Open Source tool is available. See [Upgrading to AEM Communities 6.3](upgrade.md).

>[!NOTE]
>
>Historically, utilities for accessing UGC were found in the SocialUtils package, which no longer exists.
>
>For replacement utilities, see [SocialUtils Refactoring](socialutils.md).

## Utility Method to Access UGC {#utility-method-to-access-ugc}

To access UGC, use a method from the SocialResourceUtilities package that returns a path suitable for accessing UGC from SRP and replaces the deprecated method found in the SocialUtils package.

Following is a minimal example of using the resourceToUGCStoragePath() method in a servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String ugcPath = socialResourceUtilities.resourceToUGCStoragePath(request.getResource());
  // rest of servlet
}
```

如需其他SocialUtils替代項目，請參 [閱SocialUtils重構](socialutils.md)。

如需編碼准則，請造 [訪使用SRP存取UGC](accessing-ugc-with-srp.md)。

>[!CAUTION]
>
>傳回的路徑resourceToUGCStoragePath()是*not *不適合 [ACL檢查](srp.md#for-access-control-acls)。

## 訪問ACL的實用方法 {#utility-method-to-access-acls}

某些SRP實施（如ASRP和MSRP）將社區內容儲存在不提供ACL驗證的資料庫中。 Shadow nodes provide a location in the local repository to which ACLs can be applied.

Using the SRP API, all SRP options perform the same check of the shadow location prior to all CRUD operations.

To check ACLs, use a method that returns a path suitable for checking the permissions applied to the resource&#39;s UGC.

Following is a simple example of using the resourceToACLPath() method in a servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String aclPath = socialResourceUtilities.resourceToACLPath(request.getResource());
  // rest of servlet
}
```

>[!CAUTION]
>
>The path returned by resourceToACLPath() is *not *suitable for [accessing the UGC](#utility-method-to-access-acls) itself.

## UGC-Related Storage Locations {#ugc-related-storage-locations}

The following descriptions of storage location may be of help when developing with JSRP or perhaps MSRP. There is currently no UI to access UGC stored in ASRP, as there is for JSRP ([CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)) and MSRP (MongoDB tools).

**component location**

When a member enters UGC in the publish environment, they are interacting with a component as part of an AEM site.

An example of such a component is the [comments component](http://localhost:4502/content/community-components/en/comments.html) that exists in the [Community Components Guide](components-guide.md) site. The path to the comment node in the local repository is:

* 元件路徑= */content/community-components/en/comments/jcr:content/content/include/comments*

**陰影節點位置**

建立UGC還會建立 [一個影子節點](srp.md#about-shadow-nodes-in-jcr) ，以便應用必要的ACL。 到本地儲存庫中相應卷影節點的路徑是在元件路徑中預先放置卷影節點根路徑的結果：

* 根路徑= /content/usergenerated
* 注釋陰影節點= /content/usergenerated/content/community-components/en/comments/jcr:content/content/include/comments

**UGC位置**

UGC不是在這兩個位置中建立的，且僅應使用叫用SRP API的 [公用程式方法](#utility-method-to-access-ugc) 來存取。

* 根路徑= /content/usergenerated/asi/srp-choice
* JSRP的UGC節點= /content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/includable/comments/srzd-let_it_be_

*請注意*，對於JSRP,UGC節點將只 *會出現* （作者或發佈）在輸入AEM例項上。 如果在發佈例項上輸入，則無法從作者的協調控制台進行協調。

## 相關資訊 {#related-information}

* [儲存資源提供方概述](srp.md) -簡介和儲存庫使用概述
* [使用SRP存取UGC](accessing-ugc-with-srp.md) —— 編碼准則
* [SocialUtils重構](socialutils.md) -將不建議使用的公用程式方法對應至目前的SRP公用程式方法

