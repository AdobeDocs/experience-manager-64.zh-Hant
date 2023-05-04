---
title: 社群網站要點
seo-title: Community Site Essentials
description: 導出和刪除社區站點以及建立自定義站點模板
seo-description: Exporting and deleting community sites and creating custom site templates
uuid: f0ec0e71-64e9-415a-b14a-939a9b1611c1
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: dc7a085e-d6de-4bc8-bd7e-6b43f8d172d2
exl-id: 2b26d937-4ebf-4a67-9715-a21c8fc45e1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 2%

---

# 社群網站要點 {#community-site-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 自訂網站範本 {#custom-site-template}

可以為社區站點的每個語言副本分別指定自定義站點模板。

為此，

* 建立自訂範本
* 覆蓋預設網站範本路徑
* 將自訂範本新增至覆蓋路徑
* 新增 `page-template` 屬性 `configuration` 節點

**預設範本**:

/**libs**/social/console/components/hbs/sitepage/**網站頁面**.hbs

**覆蓋路徑中的自訂範本**:

/**app**/social/console/components/hbs/sitepage/**&lt;*template-name*>**.hbs

**屬性**:頁面範本\
**類型**:字串\
**值**:&lt;*template-name*>（無擴充功能）

**配置節點**:

/content/&lt;*社群網站路徑*>/&lt;*朗*>/configuration

例如：/content/sites/engage/en/configuration

>[!NOTE]
>
>重疊路徑中的所有節點只需屬於類型 `Folder`.

>[!CAUTION]
>
>如果為自訂範本指定名稱 *sitepage.hbs,* 然後，將自定義所有社區站點。

### 自訂網站範本範例 {#custom-site-template-example}

例如， `vertical-sitepage.hbs` 是網站範本，可導致將功能表連結垂直放在頁面左側，而非水準放在橫幅下方。

[取得檔案](assets/vertical-sitepage.hbs)
將自訂網站範本放置在覆蓋資料夾中：

/**app**/social/console/components/hbs/sitepage/**垂直網站頁面**.hbs

借由新增 `page-template` 屬性到配置節點：

/content/sites/sample/en/configuration

![chlimage_1-80](assets/chlimage_1-80.png)

一定要 **全部儲存** 和將自訂程式碼複製到所有AEM例項（從主控台發佈社群網站內容時不包含自訂程式碼）。

複製自訂程式碼的建議作法為 [建立套件](../../help/sites-administering/package-manager.md#creating-a-new-package) 並部署在所有執行個體上。

## 導出社區站點 {#exporting-a-community-site}

建立社群網站後，即可將網站匯出為儲存在套件管理器中且可供下載和上傳的AEM套件。

這可從 [Communities Sites主控台](sites-console.md#exporting-the-site).

請注意，社群網站套件中未包含UGC和自訂程式碼。

要導出UGC，請使用 [AEM Communities UGC移轉工具](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)，此為GitHub上提供的開放原始碼移轉工具。

## 刪除社群網站 {#deleting-a-community-site}

自AEM Communities 6.3 Service Pack 1起，從Communities > Sites主控台將游標暫留在社群網站上時，會顯示「刪除網站」圖示。 在開發期間，如果需要刪除社群網站並重新開始，您可以使用此功能。 刪除社群網站時，會移除與該網站相關聯的下列項目：

* [UGC](#user-generated-content)
* [使用者群組](#community-user-groups)
* [Assets](#enablement-assets)
* [資料庫記錄](#database-records)

### 社群不重複網站ID {#community-unique-site-id}

若要識別與社群網站相關聯的唯一網站ID，請使用CRXDE:

* 導覽至網站的語言根目錄，例如 `/content/sites/*<site name>*/en/rep:policy`

* 尋找 `allow<#>` 節點 `rep:principalName` 在 `rep:principalName = *community-enable-nrh9h-members*`

* 網站ID是 `rep:principalName`
例如，若 
`rep:principalName = community-enable-nrh9h-members`

   * **網站名稱** = *啟用*
   * **網站ID** = *nrh9h*
   * **唯一網站識別碼** = *enable-nrh9h*

### 使用者產生的內容 {#user-generated-content}

從Github取得communities-srp-tools專案：

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

這包含一個Servlet，可從任何SRP中刪除所有UGC。

所有UGC都可移除，或針對特定網站移除，例如：

* path=/content/usergenerated/asi/mongo/content/sites/engage

這只會移除使用者產生的內容（在發佈時輸入），以及非製作內容（在作者時輸入）。 因此， [陰影節點](srp.md#shadownodes) 不受影響。

### 社群使用者群組 {#community-user-groups}

在所有製作和發佈例項上，從 [安全控制台](../../help/sites-administering/security.md)，找到並移除 [使用者群組](users.md) 即：

* 前置詞為 `community`
* 後跟 [唯一網站id](#community-unique-site-id)

例如， `community-engage-x0e11-members`.

### 啟用資產 {#enablement-assets}

從主控台：

* 選擇 **[!UICONTROL 資產]**
* 輸入 **[!UICONTROL 選擇]** 模式
* 選取名為的資料夾，其 [唯一網站識別碼](#community-unique-site-id)
* 選擇 **[!UICONTROL 刪除]** (可能需要從 **[!UICONTROL 更多……]**)

### 資料庫記錄 {#database-records}

沒有工具可選擇性地刪除一個特定啟用社區站點的資料庫條目。

刪除所有社群網站時，請使用MySQL Workbench刪除enablementdb和scormengedb。
