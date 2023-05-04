---
title: CSRF保護框架
seo-title: The CSRF Protection Framework
description: 該框架利用令牌來保證客戶端請求的合法性
seo-description: The framework makes use of tokens to guarantee that the client request is legitimate
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: 533c348e-517f-4d70-a89c-bfc87f71a633
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 2%

---

# CSRF保護框架{#the-csrf-protection-framework}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

除了Apache Sling Referrer Filter外，Ache還提供新的CSRF保護架構，以防止這類攻擊。

該框架利用令牌來保證客戶端請求的合法性。 當表單傳送至用戶端時產生代號，並在表單傳回至伺服器時驗證。

>[!NOTE]
>
>匿名使用者的發佈例項上沒有代號。

## 要求 {#requirements}

### 相依性 {#dependencies}

仰賴 `granite.jquery` 依賴性將自動受益於CSRF保護框架。 如果任何元件的情況不是這樣，則必須聲明相依性 `granite.csrf.standalone` 之後才能使用框架。

### 複製加密密鑰 {#replicating-crypto-keys}

若要使用代號，您必須復寫 `/etc/keys/hmac` 二進位至部署中的所有執行個體。 將HMAC密鑰複製到所有實例的一個方便方法是建立包含密鑰的包，並通過包管理器在所有實例上安裝它。

>[!NOTE]
>
>請確定您也必須 [Dispatcher設定變更](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) 以便使用CSRF保護框架。

>[!NOTE]
>
>如果您將資訊清單快取與Web應用程式搭配使用，請務必新增「**&amp;ast;**」，以確定代號不會使CSRF代號產生呼叫離線。 如需詳細資訊，請參閱 [連結](https://www.w3.org/TR/offline-webapps/).
>
>如需CSRF攻擊的詳細資訊以及緩解這些攻擊的方法，請參閱 [「跨網站請求偽造OWASP」頁](https://owasp.org/www-community/attacks/csrf).
