---
title: We.金融汽車保險續訂參考網站逐步說明
seo-title: We.金融汽車保險續訂參考網站逐步說明
description: 閱讀We.Finance汽車保險使用案例的詳細參考網站逐步說明，展示AEM表單及其與Microsoft Dynamics的整合如何協助客戶個人化金融服務公司的客戶體驗。
seo-description: 閱讀We.Finance汽車保險使用案例的詳細參考網站逐步說明，展示AEM表單及其與Microsoft Dynamics的整合如何協助客戶個人化金融服務公司的客戶體驗。
uuid: 18676ab4-9f8d-4014-b751-2a722fd152da
contentOwner: dekalra
topic-tags: introduction
discoiquuid: a960d489-f5a3-436a-b028-54292648c7be
exl-id: db416cbc-27a7-4a2c-b4b3-43e8963faf22
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# We.Finance汽車保險續訂參考網站逐步說明{#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## 先決條件{#pre-requisites}

按照[Setup中的說明設定參考站點，並配置AEM 6.4 Forms參考站點](/help/forms/using/setup-reference-sites.md)。

## We.Finance參考站點方案{#we-finance-reference-site-scenario}

We.Finance網站是金融服務網站，旨在幫助您了解AEM Forms的互動式通訊功能。

閱讀We.Finance汽車保險使用案例的詳細逐步說明，該案例將展示AEM表單及其與Microsoft Dynamics的整合如何幫助客戶個人化金融服務公司的客戶體驗。 互動式逐步說明旨在簡化金融公司複雜數位交易和客戶通訊的實作。

**歷程從使用案例開始：**

莎拉·羅絲是We.Finance的現有客戶，已購買了汽車保險單。 現在是她的保險單續期的時候。 We.Finance保險代理Gloria Rios向Sarah發送了關於她保單續期的提醒。 Sarah遵循電子郵件中提供的指示，並成功完成此程式。

## 自動保險申請逐步{#auto-insurance-application-walkthrough}

We.Finance自動保險應用程式案例是用戶的視覺旁白，並基於以下兩個角色：

* We.Finance客戶莎拉·羅斯
* Gloria Rios,We.Finance保險代理

### Gloria發送了We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}的保險單續訂通信

Gloria登錄AEM實例，按一下&#x200B;**自動保險續訂，**，然後按一下&#x200B;**開啟代理UI。**&#x200B;按一下「 」，保險單上就會預填Sarah Rose的保單細節。Gloria點擊&#x200B;**提交**，螢幕上將顯示一條消息「Submission Initiated」，然後在幾秒內顯示「Submitted Successfully」。

Sarah收到一封電子郵件，主題是「您的汽車保險續訂」。

![agent_ui_email](assets/agent_ui_email.png)

#### 你自己看{#see-it-yourself}

前往&#x200B;**Adobe Experience Manager** > **Forms** > **Forms與檔案** > **We.Finance** > **自動保險**。 選擇&#x200B;**自動保險續訂**&#x200B;互動式通信，然後按一下&#x200B;**開啟代理UI**。 互動式通訊會在代理程式UI中開啟。 輸入有效的電子郵件地址以接收附加策略文檔的電子郵件，然後按一下「提交」。

您可以直接從`https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`訪問並查看「汽車保險續訂」交互通信

### Sarah收到We.Finance發來的保險單續訂通訊，並決定續訂{#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah收到一封來自We.Finance的附件電子郵件，提醒她汽車保險政策即將到期。 附件是她的汽車保險信的打印版本。

Sarah按一下&#x200B;**立即續訂**&#x200B;並被導向至她的汽車保險信函的Web版本。 在此信的上方，Sarah會找到政策到期的剩餘天數。 該頁為Sarah提供了保險單詳細資訊的基本概覽，如保單編號、到期金額，以及折扣優惠和忠誠獎勵等其他資訊。 Sarah再次按一下策略底部的&#x200B;**立即續訂**。

![ref1](assets/ref1.png)

#### 其運作方式{#how-it-works}

您的汽車保險信的Web和打印輸出是使用Interactive Communications的多通道功能建立的。

電子郵件中的「立即續約」按鈕會連結至「汽車保險續約」應用程式，此應用程式是發佈執行個體上的互動式通訊。

#### 你自己看{#see-it-yourself-1}

您必須已收到附加PDF的電子郵件。 PDF是您的汽車保險信的打印版本。 按一下&#x200B;**立即續訂**&#x200B;以訪問策略的Web版本。 檢查您的個人資訊和策略詳細資訊，然後按一下&#x200B;**立即續訂**，將您轉到另一個互動式通信。

電子郵件中的&#x200B;**立即續訂**&#x200B;按鈕會將Sarah引導到策略的Web版本。 您可以造訪下列URL:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

您可以檢查自動保險續訂的詳細摘要，然後按一下頁面底部的&#x200B;**立即續訂**。

### Sarah到達付款頁{#sarah-reaches-the-payment-page}

We.Finance將Sarah帶到「付款」頁。 Sarah會重新檢查其「政策編號」和「到期日」，並附上記錄。 在頁面的右側，她檢查續訂的「付款摘要」，其總金額有10%的溢價折扣。

#### 其運作方式{#how-it-works-1}

「立即續訂」按鈕將Sarah引導到付款頁。 付款頁面是最適化表單。

#### 你自己看{#see-it-yourself-2}

按一下&#x200B;**立即續約**&#x200B;以進入「付款」頁面。 填寫您的信用卡資訊，然後按一下「付款」。****

您可以前往製作執行個體中的付款頁面，網址為

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah進行付款並完成{#sarah-makes-the-payment-and-completes-the-process}流程

Sarah填寫信用卡詳細資訊，然後按一下&#x200B;**支付**。

#### 其運作方式{#how-it-works-2}

當Sarah填寫信用卡詳細資訊並按一下「提交」時，將處理她的信用卡付款，螢幕上將顯示以最適化表單配置的感謝消息。

#### 你自己看{#see-it-yourself-3}

按一下「付款」後，您可以檢視確認訊息(位於

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
