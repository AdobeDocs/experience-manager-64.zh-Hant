---
title: 初始設定
seo-title: Initial Setup
description: 設定社群
seo-description: Setting up Communities
uuid: c53d280c-c5ae-47cf-8038-f0dea68e15ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 0d462ad1-5619-4bb6-9609-bc8987c40a0c
exl-id: 27e92acb-16bd-4519-a7fc-ea1655c56be8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 3%

---

# 初始設定 {#initial-setup}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 啟動製作和發佈例項 {#start-author-and-publish-instances}

為了開發和展示用途，必須執行一個製作和一個發佈例項。

若要這麼做，請遵循基本AEM [快速入門](../../help/sites-deploying/deploy.md#getting-started) 指令，將產生

* 製作環境 [localhost:4502](http://localhost:4502/)
* 發佈環境於 [localhost:4503](http://localhost:4503/)

對於AEM Communities,

* 製作環境適用於

   * 開發網站、範本和元件
   * 管理和配置任務

* 發佈環境適用於

   * 發佈和協調內容的社群體驗
   * 建立社區組、成員和成員組

>[!NOTE]
>
>如果不熟悉AEM，請在 [基本處理](../../help/sites-authoring/basic-handling.md) 和 [製作頁面的快速指南](../../help/sites-authoring/qg-page-authoring.md).

## 安裝最新的Communities版本 {#install-latest-communities-release}

本教學課程會建立 [參與社群網站](overview.md#engagement-community) 和是以AEM Communities 6.2 feature pack 1.10版為基礎。

若要確認已安裝最新的Feature Pack，請造訪：

* [最新發行](deploy-communities.md#latest-releases)

若為建立 [啟用社群網站](overview.md#enablement-community)，造訪 [AEM Communities啟用快速入門](getting-started-enablement.md).

## 設定 Analytics {#configure-analytics}

當 [Adobe Analytics已針對社群網站進行設定](analytics.md)，您可以取得社群活動的相關資訊，以增強社群成員的體驗，並為網站的管理員提供意見回饋。

與Adobe Analytics整合為選用。

## 設定通知的電子郵件 {#configure-email-for-notifications}

通知功能，預設適用於使用 `Communities Sites` console提供電子郵件通道以接收通知。

必須為網站正確設定電子郵件。

請參閱 [設定電子郵件](email.md).

## 啟用通道服務 {#enable-the-tunnel-service}

在製作環境中建立社群網站時，通道服務可將角色指派給在發佈環境中註冊的受信任社群成員。 通道服務也允許從 [成員和組控制台](members.md) 在製作環境中。

公約適用於在發佈環境中建立的成員和成員組 *not* 在製作環境中重新建立。 如需詳細資訊，請參閱 [管理使用者和使用者群組](users.md).

有關在 **作者** 例項，請參閱 [通道服務](deploy-communities.md#tunnel-service-on-author).

## 社區管理員角色 {#community-administrator-role}

社區管理員組的成員可以建立社區站點、管理站點、管理成員（他們可以禁止社區中的成員），以及審核內容。

### 建立使用者 {#create-user}

在 *作者*，此角色被分配給社區管理員：

* 在製作例項上

   * 例如， [http://localhost:4502/](http://localhost:4503/)

* 以管理員權限登入

   * 例如，使用者名稱&#39;admin&#39; /密碼&#39;admin&#39;

* 從主控台導覽至 **[!UICONTROL 「工具」>「操作」>「安全」>「用戶」]**
* 從 **[!UICONTROL 編輯]** 菜單，選擇 **[!UICONTROL 添加用戶]**

* 在 `Create New User` 對話框輸入

   * **[!UICONTROL ID&amp;Ast;]**:天狼星
   * **[!UICONTROL 電子郵件地址]**:sirius.nilson@mailinator.com
   * **[!UICONTROL 密碼(&amp;A);]**:密碼
   * **[!UICONTROL 確認密碼(&amp;A);]**:密碼
   * **[!UICONTROL 名字]**:西里烏
   * **[!UICONTROL 姓氏(&amp;A);]**:尼爾森

### 將Sirius分配給社區管理員組 {#assign-sirius-to-community-administrators-group}

向下捲動至 `Add User to Groups`:

* 輸入&#39;C&#39;以搜索

   * 選取 `Community Administrators`
   * 選取 `Community Enablement Managers`

* 選擇 **[!UICONTROL 儲存]**

![chlimage_1-301](assets/chlimage_1-301.png)

## 啟用社交登入 {#enable-social-login}

在使用Facebook和Twitter的社交登入示範版本之前，您必須

1. 安裝修正套件或 [最新功能套件](deploy-communities.md#latestfeaturepack) (2017年3月Facebook API變更)
1. [啟用OAuth提供者](social-login.md#adobe-granite-oauth-authentication-handler) 在發佈環境中

對於生產伺服器，必須建立提供社交登入所需的雲端服務。

請參閱 [使用Facebook和Twitter進行社交登入](social-login.md).

## 建立教學課程標籤 {#create-tutorial-tags}

使用的標籤命名空間，建立要用於參與和啟用教學課程的標籤 `Tutorial`.

使用 [標籤主控台](../../help/sites-administering/tags.md#tagging-console) 若要建立下列標籤：

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![chlimage_1-302](assets/chlimage_1-302.png)

然後依照

1. [設定標籤權限](../../help/sites-administering/tags.md#setting-tag-permissions)
1. [發佈標籤](../../help/sites-administering/tags.md#publishing-tags)

為AEM Communities快速入門Tutorials建立的標籤範例套件

[取得檔案](assets/tutorial_tags-v63.zip)

## 用於UGC公共儲存的MongoDB {#mongodb-for-ugc-common-store}

建議您設定，但可選 [MSRP](msrp.md) (MongoDB)作為 [公用商店](working-with-srp.md) 以體驗從發佈和/或作者環境調節所有UGC的彈性。

如需指示，請造訪 [如何設定示範的MongoDB](demo-mongo.md).

依預設，安裝製作和發佈AEM例項會導致將使用者產生的內容(UGC)儲存在 [JCR Tar儲存](../../help/sites-deploying/platform.md) 使用 [JSRP](jsrp.md). JSRP不是常見商店，這表示UGC只會顯示在輸入的執行個體上。 通常，UGC是在發佈例項上輸入，且不會顯示在製作環境中，導致所有協調工作都需要使用發佈例項。
