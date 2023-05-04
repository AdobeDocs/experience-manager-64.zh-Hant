---
title: 體驗已發佈的網站
seo-title: Experience the Published Site
description: 瀏覽到已發佈的站點
seo-description: Browse to a published site
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
exl-id: 8f716a59-1116-4855-baeb-3997de71b55f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 2%

---

# 體驗已發佈的網站 {#experience-the-published-site}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 在發佈時瀏覽到新站點 {#browse-to-new-site-on-publish}

現在新建立的社群網站已發佈完畢，請瀏覽至建立網站時顯示的URL，但位於發佈伺服器上，例如

* 作者URL = http://localhost:4502/content/sites/engage/en.html
* 發佈URL = http://localhost:4503/content/sites/engage/en.html

為了盡可能避免使用者對哪個成員在製作和發佈上登入的混淆，建議對每個例項使用不同的瀏覽器。

首次到達已發佈的網站時，網站訪客通常尚未登入，且為匿名。

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## 匿名網站訪客 {#anonymous-site-visitor}

匿名網站訪客在UI中看到下列內容：

* 網站標題。 哪些是快速入門教學課程
* 無個人資料連結
* 無消息連結
* 無通知連結
* 沙奇場
* 登入連結
* 品牌橫幅
* 「參考站點模板」中包含的元件的菜單連結

如果您選取各種連結，您會發現這些連結處於唯讀模式。

## 在JCR上防止匿名訪問 {#prevent-anonymous-access-on-jcr}

已知限制會透過jcr內容和json向匿名訪客公開社群網站內容，不過 **允許匿名訪問** 已針對網站內容停用。 不過，您可以使用Sling限制來控制此行為，作為因應措施。

若要保護您的社群網站內容，不讓匿名使用者透過jcr內容和json存取，請遵循下列步驟：

1. 在AEM Author例項上，前往https://&lt;host>:&lt;port>/editor.html/content/site/&lt;sitename>.html。

   >[!NOTE]
   >
   >請勿前往本地化網站。

1. 前往 **[!UICONTROL 頁面屬性]**.

   ![站點驗證](assets/site-authentication.png)

1. 前往 **[!UICONTROL 進階]** 標籤。

   ![page-properties](assets/page-properties.png)

1. 啟用 **[!UICONTROL 驗證需求]**.
1. 新增登入頁面的路徑。 例如， `/content/......./GetStarted`.
1. 發佈頁面。

## 受信任的社區成員 {#trusted-community-member}

此體驗假設 [阿隆·麥當諾](tutorials.md#demo-users) 已指派 [社群管理員和版主](create-site.md#roles). 否則，返回製作環境以 [修改站點設定](sites-console.md#modifying-site-properties) 選擇阿隆·麥當諾擔任社區經理和主持人。

在右上角選取 `Log in`，並使用使用者名稱「aaron.mcdonald@mailinator.com」和密碼「password」登入。 請注意使用Twitter或Facebook憑證登入的功能。

![chlimage_1-312](assets/chlimage_1-312.png)

登入後，請注意有新的功能表項目， `Administration`，因為會員被授予版主的角色。 現在，選取各種連結會更有趣。

![chlimage_1-313](assets/chlimage_1-313.png)

請注意，「日曆」頁面是首頁，因為選擇的「參考網站範本」會先包含「日曆」函式，接著是「活動資料流」函式、「論壇」函式等。 此結構可從 [網站範本](sites.md#edit-site-template) 主控台或修改製作環境中的網站屬性時：

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>如需Communities元件和功能的詳細資訊，請造訪
>
>* [Communities元件](author-communities.md) （適用於作者）
>* [元件、功能和功能要點](essentials.md) （適用於開發人員）
>


## 論壇連結 {#forum-link}

通過選擇「論壇」連結查看基本論壇功能。

成員可以發佈新主題或關注主題。

網站訪客可檢視貼文，並以各種方式加以排序。

![chlimage_1-315](assets/chlimage_1-315.png)

## 群組連結 {#groups-link}

由於Aaron是組管理員，因此選擇「組」連結將允許Aaron通過選擇組模板、影像、組是開啟還是秘密以及邀請成員來建立新的社區組。

這是在發佈環境中建立群組的範例。

群組也可在製作環境中建立，並在製作環境的社群網站內管理( [社群群組主控台](groups.md))。 體驗 [建立作者群組](nested-groups.md) 是本教學課程的下一個。

![chlimage_1-316](assets/chlimage_1-316.png)

建立參考群組：

1. 選擇 **[!UICONTROL 新組]**
1. **[!UICONTROL 設定標籤]**
   * 群組名稱: `Sports`
   * 說明: `A parent group for various sporting groups`
   * 群組 URL 名稱: `sports`
   * 選取 `Open Group` （允許任何社區成員加入）
1. **[!UICONTROL 範本索引標籤]**
   * 選擇 `Reference Group` （在其結構中包含組函式以允許嵌套組）
1. 選擇 **[!UICONTROL 建立群組]**

![chlimage_1-317](assets/chlimage_1-317.png)

建立新群組後， **選擇新的「運動」組** 以在其中建立兩個群組（巢狀）。 由於網站結構不能以群組功能開頭，因此在開啟「運動」群組後，必須選取「群組」連結：

![chlimage_1-318](assets/chlimage_1-318.png)

第二組連結，開頭為 `Blog`，屬於目前選取的群組， `Sports`群組。 選取「運動」 `Groups` 連結，則可在「運動」群組內巢狀內嵌兩個群組。

例如，新增兩個n `ew groups.`

* 已確認 `Baseball`
   * 將其設為 `Open Group` （必要會籍）
   * 在「模板」頁簽上，選擇 `Conversational Group`
* 已確認 `Gymnastics`
   * 將其設定變更為 `Member Only Group` （限製成員資格）
   * 在「模板」頁簽上，選擇 `Conversational Group`

**注意**:

* 在顯示兩個群組之前，可能需要重新整理頁面
* 此範本*不*包含群組函式，因此無法進一步巢狀群組
* 在作者上， [群組主控台](groups.md) 提供第三種選擇 — a `Public Group` （可選成員資格）

建立兩個群組後，請選取「棒球」群組、一個開啟的群組，並注意其連結： `Discussions` `What's New` `Members`
群組的連結會顯示在主要網站的連結下方，並產生下列顯示結果：

![chlimage_1-319](assets/chlimage_1-319.png)

在作者上 — 具有管理權限，導覽至 [Communities群組主控台](members.md) 然後把韋斯頓·麥考爾 `Community Engage Gymnastics <uid> Members` 群組。

繼續發佈，登出Aaron McDonald，並以匿名網站訪客的身分檢視運動群組：

* 從首頁
* 選擇 `Groups`連結
* 選擇 `Sports`連結
* 選取「運動」 `Groups`連結

只有棒球群組會顯示。

以Weston McCall(weston.mccall@dodgit.com /密碼)登入，並導覽至相同位置。 注意韋斯頓能 `Join` 開啟 `Baseball` 群組與 `enter or Leave` 私人 `Gymnastics`群組。

![chlimage_1-320](assets/chlimage_1-320.png)

## 網頁連結 {#web-page-link}

通過選擇「網頁」連結查看網站中包含的基本網頁。 標準AEM製作工具可用來在製作環境中將內容新增至此頁面。

例如，前往 **作者** 例項，開啟 `engage` 檔案夾 [Communities Sites主控台](sites-console.md)，請選取 **開啟網站** 圖示以進入作者編輯模式。 然後選取預覽模式以選取 `Web Page`連結，然後選取「編輯」模式以新增「標題」和「文字」元件。 最後，只重新發佈頁面或整個網站。

![chlimage_1-321](assets/chlimage_1-321.png)

## 管理連結 {#administration-link}

當社群成員擁有協調權限時，將會顯示「管理」連結，並選取該連結後，將顯示已張貼的社群內容，並允許其顯示 [已審核](moderate-ugc.md) 與 [協調控制台](moderation.md) 在製作環境中。

使用瀏覽器的返回按鈕返回已發佈的網站。 發佈環境中無法從全域導覽存取大部分的主控台。

![chlimage_1-322](assets/chlimage_1-322.png)

## 自註冊 {#self-registration}

登出後，可以建立新的使用者註冊。

* 選取 `Log In`
* 選取 `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

依預設，電子郵件地址為登入ID。 如果取消勾選，訪客可以輸入自己的登入id（使用者名稱）。 使用者名稱在發佈環境中必須是唯一的。

指定用戶名、電子郵件和密碼後，選擇 `Sign Up`會建立使用者並讓他們簽署。

登入後，顯示的第一頁為 `Profile`頁面，供他們個人化。

![chlimage_1-325](assets/chlimage_1-325.png)

如果成員忘記了其登錄ID，則可以使用其電子郵件地址進行恢復。

![chlimage_1-326](assets/chlimage_1-326.png)
