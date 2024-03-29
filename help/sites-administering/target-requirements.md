---
title: 與Adobe Target整合的必要條件
seo-title: Prerequisites for Integrating with Adobe Target
description: 了解與Adobe Target整合的必要條件。
seo-description: Find out about the prerequisites for integrating with Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
exl-id: f47e5c6a-ed52-4493-83bd-73e5e693d117
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 1%

---

# 與Adobe Target整合的必要條件{#prerequisites-for-integrating-with-adobe-target}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

作為 [整合AEM與Adobe Target](/help/sites-administering/target.md)，您需要向Adobe Target註冊、設定復寫代理，以及在發佈節點上保護活動設定。

## 向Adobe Target註冊 {#registering-with-adobe-target}

若要將AEM與Adobe Target整合，您必須具備有效的Adobe Target帳戶。 此帳戶至少必須具**核准**層級權限。 向Adobe Target註冊時，您會收到用戶端代碼。 您需要用戶端代碼和Adobe Target登入名稱及密碼，才能將AEM連線至Adobe Target。

用戶端代碼會在呼叫Adobe Target伺服器時識別Adobe Target客戶帳戶。

>[!NOTE]
>
>您的帳戶也必須由Target團隊啟用，才能使用整合。
>
>
>如果不是，請聯繫 [Adobe Target客戶服務](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html).

## 啟用目標複製代理 {#enabling-the-target-replication-agent}

測試和目標 [復寫代理](/help/sites-deploying/replication.md) 必須在製作例項上啟用。 請注意，如果您使用 [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) 執行模式以安裝AEM。 如需保護生產環境的詳細資訊，請參閱 [安全性檢查清單](/help/sites-administering/security-checklist.md).

1. 在AEM首頁上，按一下或點選 **工具** > **部署** > **復寫**.
1. 按一下或點選 **作者代理**.
1. 按一下或點選 **測試和目標（測試和目標）** 復寫代理，然後按一下或點選 **編輯**.
1. 選取「啟用」選項，然後按一下或點選 **確定**.

   >[!NOTE]
   >
   >當您設定測試和目標復寫代理時， **運輸** 頁簽，URI預設為 **tnt:///**. 請勿將此URI替換為 **https://admin.testandtarget.omniture.com**.
   >
   >請注意，如果您嘗試使用 **tnt:///**，則會擲回錯誤。 這是預期的行為，因為此URI僅供內部使用，不應與 **測試連線**.

## 保護活動設定節點 {#securing-the-activity-settings-node}

您必須保護活動設定節點的安全 **cq:ActivitySettings** 發佈例項，使一般使用者無法存取。 處理活動同步至Adobe Target的服務只應能存取活動設定節點。

此 **cq:ActivitySettings** 節點在CRXDE lite中的 `/content/campaigns/*nameofbrand*`* *在「jcr:content」節點下；* *例如 `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. 此節點僅在您定位元件後建立。

此 **cq:ActivitySettings** 活動jcr:content下的節點受以下ACL保護：

* 拒絕所有人
* 允許「target-activity-authors」的jcr:read,rep:write（作者是此群組的現成成員）
* 允許&quot;targetservice&quot;的jcr:read,rep:write

這些設定可確保一般使用者沒有節點屬性的存取權。 在製作和發佈時使用相同的ACL。 請參閱 [使用者管理與安全性](/help/sites-administering/security.md) 以取得更多資訊。

## 設定AEM外部化程式 {#configuring-the-aem-externalizer}

在Adobe Target中編輯活動時，URL會指向 **localhost** 除非您變更AEM製作節點上的URL。

要配置AEM外置程式：

1. 導覽至OSGi Web主控台，網址為 **https://&lt;server>:&lt;port>/system/console/configMgr。**
1. 查找 **Day CQ Link Externalizer** 並輸入作者節點的網域。

   ![chlimage_1-120](assets/chlimage_1-120.png)
