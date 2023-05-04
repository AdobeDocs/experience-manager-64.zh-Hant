---
title: We.Gov參考網站逐步說明
seo-title: We.Gov reference site walkthrough
description: 請參閱We.Gov參考網站逐步說明，了解AEM Forms如何協助政府管理個別資訊。
seo-description: See the We.Gov reference site walkthrough to understand how AEM Forms helps governments manage individual information.
uuid: 348f9067-28b5-47ed-8e83-0dbadeff0854
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 25a6d702-9995-4c63-99d8-3e5d710bb0c4
exl-id: c8ebd18b-fa24-4264-bd17-f553a2a784d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2753'
ht-degree: 0%

---

# We.Gov參考網站逐步說明 {#we-gov-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 先決條件 {#pre-requisite}

依照 [設定AEM Forms參考網站](/help/forms/using/setup-reference-sites.md).

## 參考網站案例 {#reference-site-scenario}

We.Gov是一個國營組織，允許養父母在收養孩子時報名接受子女撫養。 網站會管理下列項目：

* 申請人、收養父母的資格
* 申請人的個人和專業詳細資訊（如果申請人有資格獲得子女支援）
* 被收養兒童的個人細節

   申請人可以提供多個子女的詳細資訊
* 申請人可領取子女撫養費的銀行賬戶詳細資訊
* 收回應用程式費
* 應用程式評估
* 批准申請
* 自動與申請人溝通

提交申請並支付費用後，申請人收到組織發來的電子郵件，確認提交的申請。

We.Gov組織會收到應用程式。 組織會評估申請，並核准正版的申請。

申請獲得批准後，申請人會從We.Gov站點收到一封電子郵件。 此 **查看文檔** 電子郵件中的選項，該選項指向具有申請人註冊詳細資訊的文檔。

下列資訊圖表顯示We.Gov參考網站案例的逐步工作流程。

![workflow_aem_gov_2](assets/workflow_aem_gov_2.png)

此情境包含下列角色：

* 薩拉·羅斯，要求撫養孩子的養父母
* 喬，被收養的孩子
* We.Gov核准部主管Gloria Rios
* 負責申請評估的現場代理Conard Simms

## Sarah啟動了資格檢查 {#sarah-initiates-her-eligibility-check}

申請人可以檢查申請子女支援福利的資格。 網站可讓使用者回答問題，讓他們判斷其應用程式是否符合福利資格。 養父母莎拉是這個項目的潛在申請人。 資格表是We.Gov站點的「子項支援申請」服務的一部分。 為了檢查她的資格，Sarah點擊了 **[!UICONTROL 子支援]** 在We.Gov網站上。 在「子支援」頁面中，Sarah按一下 **[!UICONTROL 檢查您的資格]**.

除了上述方法，Sarah還可以按一下 **[!UICONTROL 開始使用]** 在首頁上。 系統會導覽至「所有應用程式」頁面，您可以按一下下方的「套用」 **[!UICONTROL 子支援服務應用程式]**. 然後，莎拉被帶到資格檢查。

在「檢查子支援資格」頁中，Sarah會被詢問一組問題，以確定她是否有資格享受子支援福利。 通過這些問題，她被問到：

* 如果她是孩子的監護人
* 如果她和孩子生活在GX狀態
* 兒童年齡組和兒童教育。

莎拉回答了這些問題，而且她的資格得到了驗證。 她的回答決定了她是否有資格獲得兒童撫養權。

Sarah被告知她有資格獲得兒童撫養費，申請費為25美元。

### 運作方式 {#how-it-works}

Sarah的資格是透過使用規則編輯器建立的資格障礙來驗證。 規則編輯器可讓您指定在申請人可填寫申請表之前符合的條件。 當申請人Sarah符合所有資格條件時，她就開始申請表了。

資格檢查是子級支援應用程式適用性表單的一部分。 規則會在下列情況下驗證資格：

* 申請人是監護人
* 申請人和兒童留在GX狀態
* 申請人對孩子進行日常照料
* 獲得支助服務的兒童的年齡不足16歲。

### 你自己看 {#see-it-yourself}

在瀏覽器中，開啟 `https://<hostname>:<PublishPort>/content/we-gov/en.html`. 在We.Gov站點中，按一下「子支援」。 在「子支援」頁面中，按一下「檢查您的資格」。

若要查看規則：

1. 在製作執行個體上以編輯模式開啟表單。 URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`.
1. 選取元件並按一下 ![編輯規則](assets/edit-rules.png).

   規則編輯器隨即開啟，列出表單中套用的所有規則。

1. 在左側面板中，按一下規則 `passMsg` 和 `failMsg` 了解資格檢查的運作方式。

## Sarah開始申請兒童撫養 {#sarah-starts-her-application-for-child-support}

Sarah點擊 **[!UICONTROL 啟動應用程式]** 在她被告知有資格獲得子女撫養費後。\
在「子項支援服務應用程式」頁中，Sarah提供了以下各節的詳細資訊：

* **[!UICONTROL 關於申請人]**:讓Sarah在本小節中提供詳細資訊。

* **[!UICONTROL 子資訊]**:讓Sarah提供兒童的資訊，這些資訊由支援服務提供。

* **[!UICONTROL 付款]**:讓Sarah提供她的銀行詳細資訊，We.Gov可以在這些資訊中存放每月支援補償。

* **[!UICONTROL 費用支付]**:讓Sarah提供她的信用卡詳細資訊，以支付申請費。

依預設，Sarah會被帶至 **[!UICONTROL 關於申請人]** 區段。

![案頭上的子支援應用程式](assets/desktop.png)

Sarah隨時可以點擊 **[!UICONTROL 稍後回來]** 繼續申請。 當她點擊 **[!UICONTROL 稍後回來]**，她的進度會儲存為草稿，而她可以選擇將草稿透過電子郵件傳送。

當她點擊 **[!UICONTROL 傳送電子郵件]**，她會收到一封電子郵件，內含其表單草稿的連結。

We.Gov網站上的子支援表單使用最適化表單。 她可以使用電子郵件中的連結，並在行動裝置上填寫表單。

>[!NOTE]
>
>從電子郵件繼續工作流程僅適用於登入的使用者。 在參考網站案例中，請確定已新增使用者Sarah Rose。 Sarah的登錄憑據為 `srose/password`.

![mob1](assets/mob1.png)

Sarah可以在任何部分提供詳細資訊，但只有在她提供所有部分的必需資訊後，才接受申請費。 申請不完整，無需支付費用，並且需要用星號標籤的欄位。

### <strong>莎拉提供了她的資訊</strong> {#strong-sarah-provides-her-information-strong}

莎拉點了 **[!UICONTROL 啟動應用程式]**，她將被帶到「申請兒童支援服務」頁的「申請人資訊」部分。 在「申請人資訊」下，Sarah將瀏覽各個頁簽，並為申請提供個人資訊。 她按了 **[!UICONTROL 下一個]** 來導覽標籤。

在「申請人資訊」下，要求她在以下頁簽下提供詳細資訊：

* **[!UICONTROL 基本資訊]**

在「基本資訊」下，Sarah提供身份證明和個人資訊。 Sarah的個人資訊包括她的姓名、電子郵件ID和社會安全號碼。

* **[!UICONTROL 關係]**

   在「關係」下，莎拉輸入了她婚姻狀況的資訊。

* **[!UICONTROL 其他資訊]**

   在「其他資訊」下，Sarah輸入ID號、出生日期、當前地址和電話號碼。

### Sarah提供兒童資訊 {#sarah-provides-child-information}

在Sarah提供個人資訊和點擊後 **[!UICONTROL 下一個]**，則會前往「子項資訊」區段。

在「子項資訊」部分，她提供了以下詳細資訊：

* 申請兒童支助服務的兒童人數
* 兒童姓名、社會保障號碼、出生日期和出生地

如果莎拉選了多個孩子，她會收到額外的表格，並附上相同的詳細資訊。\
莎拉選擇了她的獨生女喬，並輸入了他的名字。

### Sarah提供付款資訊 {#sarah-provides-payment-information}

在Sarah提供收養兒童（或兒童）的資訊和點擊後 **[!UICONTROL 下一個]**，她會被帶到 **[!UICONTROL 付款資訊]** 區段。

在「付款資訊」部分，她提供了銀行帳戶詳細資訊，可以在其中獲得子女支援福利。\
她輸入了10位的銀行帳號。

## 莎拉付了申請費，簽了名 {#sarah-pays-the-application-fee-and-signs-the-form}

在莎拉同意申請的條款和條件後，她支付了25美元的申請費。 處理申請需要支付申請費。\
Sarah輸入了信用卡詳細資訊和點擊次數 **[!UICONTROL 立即支付]**. 付費後，應用程式的PDF版本會顯示簽名欄位。

![sarah-sign-1](assets/sarah-sign-1.png)

Sarah可以選擇輸入、使用Draw來手寫、插入簽名影像，或者使用手機的觸摸屏來繪製簽名。 Sarah鍵入她的名字，然後按一下「按一下以簽名」。

她的申請被提交到We.Gov網站。

### <strong>Sarah收到確認電子郵件</strong> {#strong-sarah-receives-an-acknowledgement-email-strong}

Sarah支付申請費後，她會收到We.Gov網站發來的確認電子郵件。\
We.Gov會處理該申請，Sarah會被告知，她的申請獲得批准後，將獲得每月補償。

![sarah-ack-email](assets/sarah-ack-email.png)

### 運作方式 {#how-it-works-1}

子支援應用程式使用頂端標籤、精靈和折疊式功能表等面板配置的組合來建立體驗。 它使用名為We.Gov子模板的表單模板。

申請人可以跨部分移動，以填寫表單的不同部分。 當申請人填寫表格、提交表格、同意條款和條件並支付費用時，將啟動自定義工作流。 自訂工作流程會傳送自動電子郵件給確認申請提交的申請人。 申請書轉送本組織有關部門核准。

表單的佈局在政府子支援服務主題中指定。 樣式包括元件樣式、頁面背景、元件的錯誤狀態格式和字型樣式。

適用性檢查使用表單中指定的規則。 它使用以下指定的有效性檢查：

`SHOW passMsgWHEN (Does the child live in the state of GX? is equal to Yes) AND (Do you live in the state of GX? is equal to Yes) AND ( (Who has the main day-to-day care of the child? is equal to You) AND (Are you: is equal to The custodial parent) ) AND (Is the child you are applying for: is equal to Under 16 years) ELSE Hide`

`HIDE failMsg WHEN (Does the child lives in the state of GX? is equal to Yes) AND ( (Do you live in the state of GX? is equal to Yes) AND (Who has the main day-to-day care of the child? is equal to You) ) AND (Is the child you are applying for: is equal to Under 16 years) AND (Are you: is equal to The custodial parent) ELSE Show`

### 你自己看 {#see-it-yourself-1}

在瀏覽器中，開啟 `https://<hostname>:<PublishPort>/content/forms/af/we-gov/child-support/css.html` 並填寫所需資訊。 在填寫所需資訊、支付費用並簽署文檔後提交申請時，您會收到確認電子郵件。

請在此處參閱We.Gov子範本： `https://<hostname>:<AuthorPort>/editor.html/conf/we-gov/settings/wcm/templates/we-gov-child-template/structure.html`

請在此處查看主題： `https://<hostname>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-gov/we-gov-theme-A/jcr:content`

若要查看所有規則，請執行下列步驟：

1. 在製作模式中開啟表單。

   URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`

1. 選取元件，然後點選 ![編輯規則](assets/edit-rules.png). 所有規則都列在規則編輯器中，包括上述規則。

## Gloria收到申請 {#gloria-receives-the-application}

We.Gov核准主管Gloria可以檢視、核准或拒絕提交的申請。 AEM收件匣可讓她在單一位置查看所有已提交的應用程式。

### 運作方式 {#how-it-works-2}

當Sarah填寫並提交子支援應用程式時，將建立該應用程式的PDF或記錄文檔，並將其發送到Gloria Rios的收件箱。 Gloria可以查看提交的申請，並接受或拒絕。

### 你自己看 {#see-it-yourself-2}

開啟頁面 `https://<hostname***>:<PublishPort>/content/we-gov/en.html`. 在頁面上，點選 **[!UICONTROL 登入]**，請選取 **[!UICONTROL 以代表身分登入]** 核取方塊，使用grios/password作為Gloria Rios的使用者名稱/密碼登入AEM收件匣。 出現子支援應用程式。 如需有關將AEM收件匣用於表單導向工作流程工作的資訊，請參閱 [在AEM收件匣中管理Forms應用程式和任務](/help/forms/using/manage-applications-inbox.md).

![We.Gov的收件箱](assets/gloria-inbox.png)

Gloria可以從應用程式儀表板查看、批准或拒絕應用程式。

### 運作方式 {#how-it-works-3}

We.Gov核准主管Gloria開啟了她的AEM收件匣。 她在任務清單中看到了一個審核任務。 她開啟並檢視了審核工作。

她看到表格的PDF上，充滿了莎拉輸入的詳細資訊以及莎拉上傳的檔案。\
Gloria可以批准或拒絕該申請。 不過，格洛麗亞點擊了 **[!UICONTROL 需要評估]** 來評估申請。

![gloria-sends-assessment](assets/gloria-sends-assessment.png)

Sarah的應用程式是AEM工作流程的起始點。 它會在提交子支援申請表時啟動AEM工作流。 AEM工作流程會為Gloria建立工作，該工作流程會顯示在其AEM收件匣中。 當Gloria請求現場評估時，將為現場代理建立新任務。

### 你自己看 {#see-it-yourself-3}

如果設定完成，AEM工作流程會在表單提交後立即開始。 使用Gloria的憑據登錄到收件箱。

訪問收件箱： https://&lt;***主機名***>:&lt;***PublishPort***>/content/we-gov/en.html。 在頁面上，點選 **[!UICONTROL 登入]**，請選取 **[!UICONTROL 以代表身分登入]** 複選框使用Gloria的預設憑據：

* 用戶名：格里奧
* 密碼：密碼

在她的AEM收件匣中，Sarah的應用程式會新增為審核任務。 選擇任務，然後按一下 **需要評估** 以繼續下一步。

### Conard獲取評估任務 {#conard-assessment-task}

格洛麗亞點擊 **[!UICONTROL 需要評估]**,Conard會在其AEM收件匣中取得檢閱工作。 任務是工作流程模型中定義之AEM工作流程的下一步。 他看到審核任務並開啟它。

Conard將獲取申請人評估任務，如下所示。

![conrad-inbox](assets/conrad-inbox.png)

子支援評估是與任務關聯的表單。 他得到了莎拉的詳細資訊，以及支援檔案（附於任務詳細資訊中）。 Conard在設備上填寫現場評估表，並提交以進行重新評估。

科納德覈實了莎拉提供的所有細節，莎拉簽了評估書。 AEM Forms可取用位置和時間戳記，並將其新增至簽名。

![提交以進行重新評估](assets/submit-for-re-evaluation.png)

控制點點按 **[!UICONTROL 提交以進行重新評估]**,AEM工作流程會將評估提交給We.Gov組織。

### 運作方式 {#how-it-works-4}

當Gloria請求評估時，將啟動AEM工作流中的下一步，並將評估任務添加到Conard的收件箱中。 康納德是現場工作人員角色。

康納德拜訪了莎拉的住處，覈實了莎拉提供的資訊是真的，並填寫了評估表。 Conard可以存取Sarah填入的完整表單的PDF。

### 你自己看 {#see-it-yourself-4}

在平板電腦上開啟AEM收件匣，然後使用Conard的憑證登入。

Conard的預設憑證為：

* 用戶名：cms
* 密碼：密碼

您可以在收件箱中看到新的「評估請求」任務。 提交已完成的評估，然後繼續下一步。

### Gloria審核評估並批准申請 {#gloria-reviews-the-assessment-and-approves-the-application}

在Conard提交評估後，Gloria在收件箱中看到一個審核任務。 她選擇並開啟 **[!UICONTROL 檢閱]**.

![gloriinbox-1](assets/gloriainbox-1.png)

在「任務詳細資訊」下，Gloria將最後採取的操作視為「提交以進行重新評估」（由Conard提供）。 格洛麗亞認為科納德·西姆斯評估了申請。

![grolifert](assets/gloriaapproves.png)

### 運作方式 {#how-it-works-5}

在Conard提交評估後，Gloria在收件箱中看到一個審核任務。 她選擇並開啟「審閱」。 在「任務詳細資訊」下，Gloria查看Conard的評估評論，即「按順序找到的所有內容」。

格洛麗亞批准了申請。

### 你自己看 {#see-it-yourself-5}

開啟收件匣，並使用Gloria的憑證登入。 名為「查看」的新任務將出現在收件箱中。

開啟任務以查看上次執行的操作的狀態。 根據評估，批准應用程式。

## Sarah收到核准電子郵件 {#sarah-receives-an-approval-email}

Gloria核准申請後，Sarah會收到We.Gov發來的一封電子郵件，信中說她的申請已獲得批准。

此 **[!UICONTROL 查看文檔]** 按鈕（在電子郵件連結中）。 Sarah點擊 **[!UICONTROL 查看文檔。]**

![approval-reguration-kit-email](assets/approval-enrolment-kit-email.png)

登記單據列出了詳細資訊，如參考標識、子代覆蓋、啟動日期、銀行帳號、付款頻率和付款金額。

![sarah-enrollment-details](assets/sarah-enrollment-details.png)

Sarah可以查看她在同一頁上載的文檔。

![已上載文檔](assets/uploaded-documents.png)

### 運作方式 {#how-it-works-6}

當Gloria批准該應用程式時，Sarah會收到一封自動電子郵件，其中包含註冊文檔的連結。

註冊文檔是互動式通信，可以在任何設備上查看。 它包含了兒童支援服務的詳細資訊，以及Sarah提供的資訊。

### 你自己看 {#see-it-yourself-6}

檢查您為自動電子郵件配置的電子郵件客戶端，該電子郵件帶有註冊文檔的連結。

或者，要在瀏覽器中查看文檔，請開啟： `https://<hostname>:<PublishPort>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-gov/child-support/enrollment-document&referenceId=[reference-id]&channel=web`

## We.Gov分析應用程式的效能 {#we-gov-analyzes-the-performance-of-the-application}

We.Gov會不時檢查其子項支援服務應用程式的效能，以檢查客戶可能面臨的任何問題。 他們利用此分析來做出關於子支援服務應用程式中所需更改的明智決策，以增強用戶體驗，降低表單放棄率，從而改善轉換。 他們善用AEM Forms與Adobe Analytics的整合來進行分析。 下列影像可描繪其分析控制面板。

![child-support-analytics-dashboard](assets/child-support-analytics-dashboard.png)

### 運作方式 {#how-it-works-7}

子支援服務應用程式表單的效能度量使用Adobe Analytics進行跟蹤。 如需設定Adobe Analytics和檢視報表的詳細資訊，請參閱 [為表單和檔案設定分析](/help/forms/using/configure-analytics-forms-documents.md).

### 你自己看 {#see-it-yourself-7}

為了讓您檢視和探索分析報表，我們提供了參考網站中子支援服務應用程式的種子資料。 使用種子資料之前，請參閱 [設定Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). 在製作例項中執行下列步驟，檢視含有種子資料的報表：

1. 前往 **[!UICONTROL Forms與檔案]** UI網址： https://&lt;*主機名*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. 按一下以開啟 **We.Gov** 資料夾。
1. 選擇 **[!UICONTROL 子支援服務應用程式]** 適用性表單，然後按一下 **[!UICONTROL 啟用Analytics]** 的下一頁。

1. 再次選取表單，然後按一下 **[!UICONTROL Analytics報表]** ，以產生報表。 您一開始會看到空白報表。

若要產生含種子資料的分析報表：

1. 在CRXDE lite的地址瀏覽器中，鍵入： **/apps/we-gov/demo-farts/analyticsTestData/Child支援服務Analytics測試資料**
1. 在左側目錄結構中選擇種子資料。
1. 按兩下所選檔案以在右側面板中開啟其內容。
1. 複製測試資料檔案中的所有內容。
1. 在CRXDE中，導覽至： **/content/dam/formsanddocuments/we-gov/child-support/css/jcr:content/analyticsdatanode/lastsevendays**
1. 在「屬性」下的「分析資料」欄位中，貼上測試資料檔案的複製內容。
1. 現在，重新產生分析報表 **[!UICONTROL 子支援服務應用程式]**. 您可以在產生的報表中看到種子資料。
