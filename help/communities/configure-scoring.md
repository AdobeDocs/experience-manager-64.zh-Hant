---
title: 計分和徽章要點
seo-title: Scoring and Badges Essentials
description: 計分與徽章功能概觀
seo-description: Scoring and Badges feature overview
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
exl-id: 84aa46d5-4ca4-4f6e-b0b9-fc9907be00a5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 1%

---

# 計分和徽章要點 {#scoring-and-badges-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Communities計分和徽章功能提供識別和獎勵社群成員的能力。

如需設定功能的詳細資訊，請參閱

* [社群計分和徽章](implementing-scoring.md)

本頁包含其他技術詳細資訊：

* 如何 [顯示徽章](#displaying-badges) 為影像或文字
* 如何開啟廣泛 [偵錯記錄](#debug-log-for-scoring-and-badging)
* 如何 [訪問UGC](#ugc-for-scoring-and-badging) 與打分和徽章有關

>[!CAUTION]
>
>CRXDE Lite中可見的實作結構可能會有所變更。

## 顯示徽章 {#displaying-badges}

徽章是否顯示為文字或影像，在HBS範本的用戶端進行控制。

例如，搜尋 `this.isAssigned` in `/libs/social/forum/components/hbs/topic/list-item.hbs`,:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

如果為true, isAssigned表示已為角色分配徽章，且徽章應顯示為文本。

如果為false，則為「已分配」表示已為已獲得分數授予徽章，且徽章應顯示為影像。

對此行為所做的任何變更都應在自訂指令碼中進行（覆寫或覆蓋）。 請參閱 [用戶端自訂](client-customize.md).

## 計分和簽名的調試日誌 {#debug-log-for-scoring-and-badging}

若要協助除錯計分和標籤，可設定自訂記錄檔。 如果此功能出現問題，則此日誌檔案的內容將提供給客戶支援。

如需詳細指示，請造訪 [建立自訂記錄檔](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

若要快速設定slinglog檔案：

1. 存取 **[!UICONTROL Adobe Experience Manager Web主控台記錄支援]**，例如

   * http://localhost:4502/system/console/slinglog

1. 選擇 **[!UICONTROL 添加新記錄器]**

   1. 選擇 `DEBUG` for **[!UICONTROL 記錄層級]**
   1. 輸入 **[!UICONTROL 記錄檔]**，例如

      * logs/scoring-debug.log
   1. 輸入2 **[!UICONTROL 記錄器]** （類）條目(使用 `+` 圖示)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. 選擇 **[!UICONTROL 儲存]**



![chlimage_1-248](assets/chlimage_1-248.png)

要查看日誌條目，請執行以下操作：

* 從Web控制台

   * 在 **[!UICONTROL 狀態]** 功能表
   * 選擇 **[!UICONTROL 記錄檔]**
   * 搜尋您的記錄檔檔案名稱，例如 `scoring-debug`

* 在伺服器的本地磁碟上

   * 日誌檔案為&lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log
   * 例如 `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC用於計分和簽名 {#ugc-for-scoring-and-badging}

當選擇的SRP是JSRP或MSRP，但不是ASRP時，可以查看與計分和徽章相關的UGC。 (如果不熟悉這些術語，請參閱 [社群內容儲存](working-with-srp.md) 和 [儲存資源提供程式概述](srp.md).)

存取計分和加註資料的說明使用JSRP，因為UGC可透過 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

**JSRP關於作者**:在製作環境中實驗會導致UGC，而此UGC僅可從製作環境中看到。

**發佈JSRP**:同樣地，如果在發佈環境上進行測試，則需要以發佈例項的管理權限存取CRXDE Lite。 如果發佈執行個體在 [生產模式](../../help/sites-administering/production-ready.md) (nosamplecontent runmode)，則必須 [啟用CRXDE Lite](../../help/sites-administering/enabling-crxde-lite.md).

UGC在JSRP上的基地位置為 `/content/usergenerated/asi/jcr/`.

### 計分與加號API {#scoring-and-badging-apis}

下列API可供使用：

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

已安裝的最新Javadoc [發行](deploy-communities.md#LatestReleases) 供開發人員從Adobe存放庫使用。 請參閱 [將Maven用於社群：Javadocs](maven.md#javadocs).

**UGC在存放庫中的位置和格式可能會變更，恕不另行警告**.

### 範例設定 {#example-setup}

存放庫資料的螢幕擷取畫面來自為兩個不同AEM網站上的論壇設定計分和標籤：

1. 具有唯一ID的AEM網站（使用精靈建立的社群網站）:

   * 使用在 [快速入門教學課程](getting-started.md)
   * 找到論壇頁面節點

      * `/content/sites/engage/en/forum/jcr:content`
   * 添加計分和標籤屬性

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * 找到論壇元件節點

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * 新增屬性以顯示徽章

      * `allowBadges = true`
   * 使用者登入、建立論壇主題，並獲得銅牌





1. AEM網站 *無* 唯一id:

   * 使用 [社群元件指南](components-guide.md)
   * 找到論壇頁面節點

      * `/content/community-components/en/forum/jcr:content`
   * 添加計分和標籤屬性

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * 找到論壇元件節點

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * 新增屬性以顯示徽章

      * `allowBadges = true`
   * 使用者登入、建立論壇主題，並獲得銅牌




1. 系統會使用cURL為使用者指派協調者徽章：

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

由於使用者已獲得兩個銅牌，並且已獲得版主徽章，因此以下是使用者在論壇項目中的顯示方式：

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>此範例不遵循下列最佳實務：
>
>* 計分規則名稱應全域唯一；它們的結尾不應該是同一個名稱。\
   >  以下範例 *not* 要執行：\
   >  /etc/community/scoring/rules/site1/forums計分\
   >  /etc/community/scoring/rules/site2/forums計分
>
>* 建立不同AEM網站的不重複徽章影像
>


### 訪問計分UGC {#access-scoring-ugc}

使用 [API](#scoring-and-badging-apis) 為偏好設定。

為了調查目的，以JSRP為例，包含分數的基本資料夾為

* `/content/usergenerated/asi/jcr/scoring`

的子節點 `scoring`是計分規則名稱。 因此，最佳實務是，伺服器上的計分規則名稱是全域唯一的。

對於Geometrixx參與網站，使用者及其分數位於包含計分規則名稱、社群網站網站ID( `engage-ba81p`)、唯一id和使用者id:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

對於社群元件指南網站，使用者及其分數位於以計分規則名稱（預設ID）建構的路徑中( `default-site`)、唯一id和使用者id:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

分數會儲存在屬性中 `scoreValue_tl` 其中可能直接包含值或間接引用atomicCounter。

![chlimage_1-251](assets/chlimage_1-251.png)

### 訪問標籤UGC {#access-badging-ugc}

使用 [API](#scoring-and-badging-apis) 為偏好設定。

為了調查目的，以JSRP為例，包含已指派或已授予徽章之資訊的基本資料夾為

* /content/usergenerated/asi/jcr

後接使用者設定檔的路徑，結尾為徽章資料夾，例如

* /home/users/community/w271Oup2Z4DjnOQrviv/profile/badgs

#### 獎章 {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### 指派徽章 {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## 其他資訊 {#additional-information}

要根據點顯示按排序的成員清單，請執行以下操作：

* [排行榜功能](functions.md#leaderboard-function) 以包含在社群網站或群組範本中。
* [排行榜元件](enabling-leaderboard.md)，此元件為排行榜功能的精選元件，用於頁面編寫。
