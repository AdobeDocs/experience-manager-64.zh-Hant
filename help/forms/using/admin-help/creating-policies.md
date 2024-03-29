---
title: 建立和管理策略
seo-title: Creating and managing policies
description: 策略是一組機密設定，以及可以訪問應用策略的文檔的用戶。 您可以使用AEM表單建立和管理各種類型的原則。
seo-description: A policy is a set of confidentiality settings and users who can access a document to which the policy is applied. You can create and manage various types of policies using AEM forms.
uuid: 72be06f3-3e90-495e-8425-72380d95704a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fa054d30-c7dc-4b64-acf1-cbcbe8827df5
feature: Document Security
exl-id: a4e69794-ea83-4cb6-a3da-cef0ceb6892a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4754'
ht-degree: 0%

---

# 建立和管理策略 {#creating-and-managing-policies}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

A *原則* 定義一組機密設定，以及可以訪問應用策略的文檔的用戶。 A *策略集* 用於分組具有共同業務目的的一組策略。 然後，這些策略集將可供系統中的用戶子集使用。 如需原則的詳細資訊，請參閱 [策略和受策略保護的文檔](/help/forms/using/admin-help/document-security.md#policies-and-policy-protected-documents).

## 策略類型 {#types-of-policies}

檔案安全性提供下列類型的原則。

**個人政策**

用戶可以建立、編輯、複製、刪除自己的策略，並使用與特定情況相應的設定。 只有建立策略的人員和管理員才能訪問該個人策略。 個人策略會顯示在「策略」頁的「我的策略」頁簽上。

如果管理員啟用此功能，受邀用戶也可以建立、編輯、複製和刪除個人策略。

**共用原則**

管理員和策略集協調者根據貴組織針對不同類型的文檔和用戶識別的機密要求建立共用策略。 共用策略包含在策略集中，可供所有授權用戶（文檔發佈者、策略集協調者和文檔接收者）使用，用於特定策略集。 管理員和策略集協調員可以啟用和禁用共用策略。 共用策略顯示在「策略」頁的「策略集」頁簽上的策略集中。

首次安裝文檔安全時，它包含一個共用策略，名為 *限制為所有承擔者*. 將此策略應用於文檔時，任何可以登錄到文檔安全的用戶都可以訪問該文檔。 此策略位於名為的策略集中 *全局策略集*. 預設情況下，不啟用此策略。 如果符合組織的需求，您可以加以啟用。

**Microsoft Outlook自動生成的策略**

使用Acrobat，您可以在Microsoft Outlook中，將原則套用至您以電子郵件附件形式傳送的檔案。 在Outlook中，您可以使用現有策略或使用自動生成的策略來保護文檔，該策略由Acrobat生成，具有預設的機密設定，並應用於附加到電子郵件的文檔。 (見* [Acrobat說明](https://help.adobe.com/en_US/acrobat/pro/using/index.html)*.)

>[!NOTE]
>
>為了在Outlook中可用策略，必須在Acrobat中將策略設定為收藏夾。 所有其他策略（包括您是發佈者的策略）不會顯示在Outlook中。

## 誰可以建立和管理策略和策略集 {#who-can-create-and-manage-policies-and-policy-sets}

您與策略和策略集交互的方式取決於您在組織內的角色：

**用戶：** 用戶可以建立、編輯和刪除其個人策略。 如果管理員啟用此功能，受邀用戶也可以建立個人策略。

**策略集協調員：** 策略集協調者可以在策略集中建立和管理共用策略，在策略集中將它們指定為協調者。 策略集協調者通常是組織中的專家，他可以最好地編寫特定策略集中的策略。

**管理員：** 管理員可以編輯任何使用者的個人原則。 他們可以建立共用原則。 他們還可以建立、編輯和刪除策略集，並指定策略集協調員。

有關各種文檔安全形色的詳細資訊，請參見 [關於檔案安全性使用者](/help/forms/using/admin-help/document-security.md#about-document-security-users).

## 建立和編輯原則 {#creating-and-editing-policies}

用戶可以建立或編輯個人策略以供自己使用。 管理員和策略集協調員可以為組織建立或編輯共用策略。

### 編輯原則的考量事項 {#considerations-for-editing-policies}

編輯策略時，更改將影響策略當前保護的文檔以及策略之後保護的文檔。 例如，如果從當前應用於文檔的策略中刪除收件者，則收件者無法再開啟該文檔。

文檔的狀態決定了更改何時生效：

* 如果文檔處於聯機狀態，則會立即應用更改，除非用戶已開啟該文檔。 在這種情況下，用戶必須關閉文檔，更改才會生效。
* 如果收件者離線使用檔案（例如，在筆記型電腦上），變更將在下次收件者上線檔案時生效，並透過開啟任何受原則保護的檔案來與檔案安全性同步。

>[!NOTE]
>
>Acrobat自動為附加至Microsoft Outlook電子郵件訊息之檔案的收件者產生的原則，不會出現在原則清單中。 只有開啟關聯文檔的「文檔詳細資訊」頁，才能查看這些策略。

編輯策略時，將應用以下限制：

* 只有管理員啟用此功能時，受邀用戶才能編輯策略。 如果無法編輯策略，則「編輯」選項將不可用。
* 只有策略集協調者具有正確權限時，才能編輯策略集中的策略。 超級用戶或策略集管理員在文檔安全管理員介面中設定這些權限。
* 如果策略配置了自建立策略後管理員刪除的水印，則如果編輯並保存該策略，則此水印將不再應用於文檔。 只有在不編輯策略的情況下，刪除的水印才對現有策略有效。 如果編輯策略，則必須選擇另一個水印來替換已刪除的水印。
* 您無法通過編輯當前應用的策略來授予對文檔的匿名訪問權。 如果編輯策略，則用戶仍必須登錄才能訪問該文檔。 要對此文檔應用匿名訪問，請先刪除客戶端應用程式中的策略，然後應用允許匿名訪問的其他策略。
* Acrobat為附加至Microsoft Outlook中電子郵件訊息之檔案的收件者自動產生的原則，不會出現在原則清單中。 要訪問此策略，請在「文檔」頁上找到文檔，開啟「文檔詳細資訊」頁，然後按一下文檔詳細資訊清單中的策略名稱。

**建立或編輯策略**

1. 在文檔安全頁上，按一下「策略」，然後按一下以下任一頁簽：

   * 要建立或編輯個人策略，請按一下「我的策略」頁簽。
   * 要建立或編輯共用策略，如果您有權限，請按一下「策略集」頁簽，然後按一下相應的策略集名稱，然後按一下「策略」頁簽。

1. 按一下「新建」或從清單中選擇要編輯的策略。
1. 在「名稱」框中，鍵入唯一標識策略的名稱。 在「說明」方塊中，說明原則的作用及使用時機。 如果策略位於策略集內，則所有指定用戶的策略清單中將顯示該名稱和說明。 個人策略僅供用戶和管理員使用。

   名稱或說明中不能使用下列字元：

   * 小於號(&lt;)
   * 大於號(>)
   * &amp;符號
   * 單引號(&#39;)
   * 雙引號(&quot;&quot;)
   * 反斜線(\)
   * 正斜線(/)

   如果在名稱或說明中使用以下字元，則這些字元將轉換為空格：

   * 歸位（ASCII字元13）
   * 新行（ASCII字元10）。

   >[!NOTE]
   >
   >您可以建立包含擴展字元的策略名稱；但是，當在兩個字串之間進行比較時，重音字元和非重音字元（如&quot;e&quot;和&quot;é&quot;）被視為相同。 當某人建立策略時，將進行比較以檢查是否已存在同名策略。 除帶重音的字元外，比較無法區分相同的名稱。 假定已將策略添加到資料庫中，並且不添加新策略。

1. 將用戶和組添加到策略並設定相應的權限。 (請參閱 [使用者和群組](creating-policies.md#users-and-groups).)
1. 在「一般設定」下，選取適當的選項。 (請參閱 [一般設定](creating-policies.md#general-settings).)
1. （可選）如果適用，請選擇外部授權提供程式並指定其屬性。 如果您不想使用外部授權提供程式，請按一下刪除預設提供程式。

   外部授權提供程式用於設定策略內的屬性，當選中時，外部授權提供程式將使用此資訊來評估策略。 可用屬性由管理員和安裝軟體的人員配置。

1. 在「進階設定」下，選取適當的選項。 (請參閱 [進階設定](creating-policies.md#advanced-settings).)
1. 在「不可更改的高級設定」下，選擇適當的選項。 (請參閱 [不可更改的高級設定](creating-policies.md#unchangeable-advanced-settings).)
1. 按一下「儲存」。策略將顯示在策略清單中。 新策略旁會出現一個帶紅色圓圈的表徵圖，表示該策略仍處於禁用狀態。

   要使策略可供用戶使用，請啟用它。 (請參閱 [啟用或禁用共用策略](creating-policies.md#enable-or-disable-shared-policies).)

### 使用者和群組 {#users-and-groups}

在「用戶和組」區域中，指定有權訪問受策略保護的文檔的用戶。 對於您指定的每個用戶或組，您還可以設定文檔使用權限。

>[!NOTE]
>
>文檔發佈者是使用策略保護文檔的用戶。 預設情況下，策略上始終包含此用戶，具有完全訪問權限，包括吊銷和策略切換功能。 但是，管理員可以更改文檔發佈者對共用策略的訪問權限。 例如，管理員可以限制文檔發佈者撤消文檔訪問或切換策略。

**添加用戶或組：** 若要新增使用者或使用者群組，請按一下「新增使用者或群組」 ，然後按一下「進階搜尋」以尋找使用者或群組。 使用者包括您組織的內部使用者，以及已透過檔案安全性註冊的受邀使用者。 選擇此選項後，將顯示「添加用戶或組」頁：

* 在「尋找」方塊中，輸入使用者或群組名稱或電子郵件地址。
* 在使用清單中，選擇名稱或電子郵件。
* 在「類型」清單中，選擇「用戶」或「組」。
* 從「在」(In)清單中選擇要搜索的域，然後按一下「查找」(Find)。
* 返回結果時，選擇要添加的用戶或組，然後按一下「添加」。

>[!NOTE]
>
>如果您輸入了正確的受邀用戶名或電子郵件地址，並且未返回任何結果，則用戶可能尚未註冊，或者帳戶可能被刪除。 您可以嘗試將使用者新增為受邀的使用者類型，或聯絡您的管理員。

**邀請新用戶：** 若要新增受邀的使用者，請按一下「邀請新使用者」，在出現的方塊中輸入使用者的電子郵件地址，然後按一下「邀請」。 只有在管理員啟用此選項時，此選項才可用。 將新的受邀用戶添加到策略時，如果用戶尚未被邀請註冊，則文檔安全性會發送註冊邀請電子郵件。 使用者必須使用電子郵件中的連結來建立帳戶，然後才能啟用帳戶。

註冊後，受邀用戶可以使用他們具有授權的受策略保護的文檔。 根據管理員啟用的功能，外部用戶可能具有將策略應用到文檔、建立、編輯和刪除策略以及將其他外部用戶添加到策略的權限。

**添加匿名用戶：** 要允許匿名用戶訪問，請按一下添加匿名用戶。 只有在管理員為文檔安全啟用匿名用戶訪問時，此選項才可用。 （請參閱配置文檔安全伺服器。） 此選項授予每個人對受此策略保護的文檔的訪問權限，而不管他們是否具有文檔安全帳戶。 如果選擇此選項，則無法將其他類型的用戶添加到策略。

>[!NOTE]
>
>要允許匿名訪問當前沒有的受策略保護的文檔，請刪除現有策略，然後應用允許匿名訪問的策略。 如果切換或更改現有策略，則用戶仍必須登錄才能訪問該文檔。

#### 指定用戶和組的文檔權限 {#specify-the-document-permissions-for-users-and-groups}

您可以一次為一個用戶或組指定文檔權限，也可以從清單中選擇多個用戶和組，並使用列標題區域中的選項更改其權限。

預設情況下，所有受策略保護的文檔都具有允許用戶聯機時開啟它們的權限。

「權限和選項」頁簽顯示在文檔安全性中。

「權限」(Permissions)頁簽上提供了這些文檔權限。 您可以將這些權限應用於PDF、PTC Pro/E和Microsoft Office檔案。

**打印：** 允許用戶打印受此策略保護的文檔。 對於Office和Pro/E檔案，可以選擇「打印」複選框以允許打印，或者清除它以防止打印。 如果您選取「顯示自訂PDF權限」核取方塊，您可以選取下列選項：

**不允許：** 不允許用戶打印PDF。

**允許：** 允許用戶打印PDF。

**低解析度。 僅限：** 允許用戶以低解析度打印PDF。

**修改：** 允許用戶修改受此策略保護的文檔。 對於Office和Pro/E檔案，可以選中「修改」(Modify)複選框以允許修改，或者清除它以防止修改。 如果您選取「顯示自訂PDF權限」核取方塊，您可以選取下列選項：

**不允許：** 不允許用戶修改PDF。

**任何：** 使用者可以修改PDF。

**協作：** 允許使用者使用Adobe Acrobat中的「共同作業」選項與他人共同作業。 此權限允許用戶複製表單資料，即使未在策略中明確指定「複製」權限。

**更改頁面：** 允許使用者新增和移除頁面，以及編輯PDF中的內容。

**Fill &amp; Sign:** 使用者可填寫PDF上的表單欄位並加以簽署。

**複製：** 允許用戶從受此策略保護的文檔中複製文本。

**螢幕Reader:** 如果您選取「顯示PDF的自訂權限」核取方塊，則會顯示此權限。 選取此選項時，Adobe Acrobat有權將暫時標籤新增至PDF，以透過螢幕助讀程式改善其可讀性。

「選項」(Options)頁簽上提供了這些文檔權限。 可將這些權限應用於PDF、PTC Pro/E和Microsoft Office檔案：

**離線：** 允許用戶離線查看受此策略保護的文檔。

**權限有效性：** 選擇權限始終有效或設定文檔權限有效期。 如果您選取有效期間，請按一下日曆圖示以選取日期，並使用箭頭以24小時格式指定時間。

對於共用策略，管理員可以禁用文檔發佈者（將策略應用到文檔的用戶）的以下權限：

**撤銷：** 允許文檔發佈商撤消文檔訪問權限。

**交換機：** 允許文檔發佈者切換策略權限。

### 一般設定 {#general-settings}

「一般設定」區域包含下列設定：

**有效期：** 受策略保護的文檔可供授權收件人訪問的時間段。 您可以從以下有效期選項中選擇：

**在以下情況下，文檔將無效：** 從文檔安全起的指定天數內，可以訪問該文檔。

**此日期後文檔將無效：** 從將策略應用到文檔的日期到指定的結束日期，該文檔有效。

**有效自：** 文檔在您指定的日期期間有效。 您可以按一下日曆圖示，使用日曆來選取日期（如果適用）。

**文檔始終有效：** 文檔有效期不會過期。

>[!NOTE]
>
>有效日期是以檔案安全系統的時區為基礎，而非您本機電腦的時區。

**審計：** 啟用或禁用對與受策略保護的文檔關聯的事件的審核。 例如，文檔安全性可以記錄諸如嘗試開啟文檔之類的事件。 「事件」頁面的清單中顯示已審計事件。 如果未選擇此選項，則文檔安全性不會記錄與策略關聯的文檔的事件。

>[!NOTE]
>
>管理員還必須在「審核和隱私設定」配置頁上啟用伺服器審核，審核功能才能正常工作。

**延伸使用量追蹤：** 啟用或停用「延伸使用量追蹤」。 檔案安全性支援追蹤與在PDF檔案上執行的各種作業相關聯的使用者事件。 文檔安全對象可使用Java指令碼進行訪問。 按鈕點擊、正在播放的多媒體檔案或保存檔案是可以從受策略保護的PDF引發的一些事件示例。 使用文檔安全對象，您還可以檢索用戶資訊。 可以在全局級別或策略級別從文檔安全伺服器啟用事件跟蹤。

**自動離線租賃期：** 接收方離線使用受策略保護的文檔（沒有活動的Internet或網路連接）的最大天數。 當租賃期過期時，收件人必須再次同步文檔以繼續使用它。

### 外部授權服務提供者 {#external-authorization-providers}

如果您已配置任何身份驗證提供程式，請選擇外部身份驗證提供程式。 列出可用的提供程式。

### 驗證設定 {#authentication-settings}

您可以覆蓋在伺服器上配置的身份驗證設定，並指定與此策略相關的身份驗證選項。 選擇覆蓋全局身份驗證設定，然後選擇與此策略相關的身份驗證選項。 下列驗證選項可用：

**允許用戶名密碼驗證：** 選擇此選項可使客戶端應用程式在連接到伺服器時使用用戶名/密碼驗證。

**允許Kerberos身份驗證：** 選擇此選項可使客戶端應用程式在連接到伺服器時使用Kerberos身份驗證。

**允許客戶端證書驗證：** 選擇此選項可使客戶端應用程式在連接到伺服器時使用證書身份驗證。

**允許擴展身份驗證** 選擇以啟用擴展身份驗證。 選擇此選項可使客戶端應用程式使用擴展身份驗證。 擴展身份驗證提供定製的身份驗證進程和在Document Security伺服器上配置的不同身份驗證選項

如果要覆蓋全局身份驗證設定，則可以選擇與此策略相關的身份驗證選項。 例如，如果您已在伺服器上啟用了三個驗證選項（用戶名和密碼、客戶端證書和擴展驗證），則可以覆蓋該全局設定，並僅為此策略選擇擴展驗證。 您必須確保伺服器上已設定您在此處選取的驗證選項。 在此示例中，無法選擇Kerberos作為身份驗證選項，因為它未在伺服器上配置。

>[!NOTE]
>
>Apple Mac OS X支援Adobe Acrobat 11.0.6版及更新版本的延伸驗證。

### 進階設定 {#advanced-settings}

「進階設定」區域包含下列設定：

**動態水印：** 選擇要動態顯示在文檔頁面上的水印（例如，當收件者打印文檔時）。 動態水印會唯一識別檔案，因此有助於確保檔案的機密性並防止侵犯版權。 例如，管理員可以配置一個動態水印，該水印顯示當前日期、使用文檔的人員的用戶名或標識符，或用於保護文檔的策略的名稱。 水印還可以顯示自定義文本或圖形元素（如果配置）。 管理員配置水印選項，管理員和用戶可以將它們應用到策略。

(請參閱 [配置動態水印](/help/forms/using/admin-help/configuring-client-server-options.md#configure-dynamic-watermarks).)

如果您正在編輯策略，並且管理員刪除了您以前為此策略選擇的配置水印，則「編輯策略」頁上將顯示一個注釋。 在這種情況下，如果要保存已編輯的文檔，則如果要在文檔上顯示新水印，請選擇新水印。

>[!NOTE]
>
>對於提供匿名用戶訪問的策略，即使您選擇此類型的水印，匿名用戶的用戶名和標識符也不會顯示為水印。

**僅使用經認證的Acrobat外掛程式進行PDF:** 為策略選擇時，此選項指定在開啟使用策略保護的文檔時，必須以認證模式運行Acrobat 8.0和更高版本。 Acrobat以認證模式執行時，不會載入任何協力廠商外掛程式。

如果您擔心檔案收件者撰寫外掛程式，而能夠規避Acrobat 8.0及更新版本中任何檔案保護，請選取此選項。 如果您的檔案收件者需要在Acrobat中使用協力廠商外掛程式來與檔案互動，請勿選取此選項。

此選項僅啟用Acrobat 8.0或更新版本中的認證模式；管理員必須停用Acrobat 7.0的存取權。

(請參閱 [配置文檔安全伺服器](/help/forms/using/admin-help/configuring-client-server-options.md#configure-the-document-security-server).)

此選項不適用於Adobe Reader。

**拒絕訪問錯誤消息：** 未經許可而嘗試開啟受策略保護文檔的任何人都會看到的消息。 此訊息會顯示在Acrobat中。 無法顯示此消息的客戶端將顯示預設消息，以指示拒絕訪問。

### 不可更改的高級設定 {#unchangeable-advanced-settings}

「不可更改的高級設定」區域包含以下設定。 保存策略後，無法更改這些設定。

**加密算法和密鑰長度：** 用來保護您的檔案。 您可以從下列選項中選擇：

* AES 128位
* 256位。 只有Acrobat 9.0和更新版本支援此選項。 要對PDF檔案使用AES 256加密，請獲取並安裝Java加密擴展(JCE)無限強度管轄策略檔案。 這些檔案將替換 [JAVE_HOME]/lib/安全資料夾。 例如，如果您使用Sun JDK 1.6，請將下載的檔案複製到 [dep root]/Java/jdk1.6.0_26/lib/安全資料夾。 您可以從以下網址下載這些檔案： [Java SE下載](https://java.sun.com/javase/downloads/index.jsp).
* 不加密。 Acrobat 9.0和更新版本目前支援此選項。 如果選擇此選項，則禁用「文檔限制」選項。 如果您希望將文檔安全性用於文檔審核或版本控制，但不想加密文檔，則此選項可能很有用。

**文檔限制：** 選擇要加密的PDF文檔元件。 其他客戶端應用程式會加密整個文檔，但不會加密連結或嵌入的檔案。 您可以從下列選項中選擇：

* 整個文檔，包括其附件和元資料。 *中繼資料* 是有關文檔及其內容的資訊，可通過文檔屬性對話框或Acrobat高級菜單查看。 在Acrobat中，您可以將不同類型的檔案（例如文字、音訊和視訊檔案）附加至PDF檔案。
* 文檔及其附件，但不是元資料。
* 僅文檔附件。 您可以加密PDF檔案的附件，而不加密文檔內容。

## 啟用或禁用共用策略 {#enable-or-disable-shared-policies}

要使共用策略可用，管理員或策略集協調器必須啟用它。 您可以啟用新策略或先前禁用的策略。 您禁用的共用策略仍對受該策略保護的文檔強制執行。

禁用的策略旁會出現紅色X。

>[!NOTE]
>
>管理員無法禁用個人策略，用戶不能啟用和禁用自己的策略。

1. 在文檔安全頁上，按一下「策略」，然後按一下「策略集」頁簽。
1. 按一下相應的策略集名稱，然後按一下「策略」頁簽。
1. 選擇相應策略旁的複選框，按一下「啟用」或「禁用」，然後按一下「確定」。

## 查看有關策略的資訊 {#view-information-about-a-policy}

使用「我的策略」頁簽，可以搜索個人策略。

管理員建立的策略集會列在「策略」頁的「策略集」頁簽上，其中包含有關策略集的資訊，包括其名稱、建立和修改的日期以及說明。 按一下策略集名稱以查看其詳細資訊。 具有管理策略權限的策略集協調員可以在特定策略集中建立共用策略。

建立或編輯策略時，將顯示一個頁面，您可以在其中配置策略名稱、權限級別、機密設定以及要包含在策略中的收件人等詳細資訊。

管理員可以為策略配置以下機密設定：

* 一般文檔機密選項，如文檔有效期和離線租用期
* 已授權的用戶，以及每個用戶的文檔限制和權限
* 高級文檔機密選項，包括動態水印和文檔加密

用戶可以查看他們建立的策略以及他們有權訪問的任何共用策略。 管理員可以查看文檔安全中的所有共用策略和個人策略。

您可以查看清單中顯示的策略的詳細資訊，包括策略中包含的用戶或組以及為這些用戶指定的機密設定。

>[!NOTE]
>
>Acrobat自動為附加至Microsoft Outlook電子郵件訊息之檔案的收件者產生的原則，不會出現在原則清單中。 只有開啟關聯文檔的「文檔詳細資訊」頁，才能查看這些策略。

1. 在文檔安全頁上，按一下「策略」，然後按一下「我的策略」頁簽。
1. 填寫搜索資訊以搜索個人策略。
1. 從清單中選擇適當的策略。
1. 在「策略詳細資訊」頁上，您可以查看有關策略的詳細資訊、編輯策略或查看與策略相關的事件。

## 搜尋原則 {#search-for-policies}

管理員可以搜索共用策略以及其他用戶建立的個人策略。

1. 要搜索共用策略，請按一下「策略」，然後按一下「策略集」頁簽。 按一下清單中的策略集，然後按一下「策略」頁簽。

   要搜索個人策略，請在文檔安全頁上，按一下「策略」，然後按一下「我的策略」頁簽。

1. 在「查找」清單中，選擇以下選項之一：

   **策略ID:** 用戶建立策略時生成的策略標識號。 必須鍵入確切的策略ID。

   **策略名稱：** 策略的名稱。 您可以搜索策略名稱的一部分或全部。

1. 在文字方塊中，輸入對應的值。 例如，如果選擇了策略名稱，請輸入要搜索的策略名稱。
1. 在「顯示」清單中，選擇要顯示的結果數，然後按一下「查找」。 將顯示搜索結果。
1. （可選）要查看策略詳細資訊，請按一下策略。

## 複製策略 {#copy-a-policy}

您可以複製現有策略，並以新名稱和說明進行保存。 複製策略是使用現有設定建立新策略的一種有效方法。

只有管理員啟用此功能時，外部用戶才能複製策略。 如果無法建立策略，則「複製」選項將不可用。

1. 在文檔安全頁上，按一下「策略」，然後按一下「我的策略」頁簽。
1. 從清單中選擇適當的策略。
1. 在「策略詳細資訊」頁上，按一下「複製」。
1. 在「新策略名稱」框中，鍵入新策略名稱。 （可選）鍵入新的「說明」。

   名稱或說明中不能使用下列字元：

   * 小於號(&lt;)
   * 大於號(>)
   * &amp;符號
   * 單引號(&#39;)
   * 雙引號(&quot;&quot;)
   * 反斜線(\)
   * 正斜線(/)

   如果在名稱或說明中使用以下字元，則這些字元將轉換為空格：

   * 歸位（ASCII字元13）
   * 新行（ASCII字元10）。

   >[!NOTE]
   >
   >您可以建立包含擴展字元的策略名稱；但是，當在兩個字串之間進行比較時，重音字元和非重音字元（如&quot;e&quot;和&quot;é&quot;）被視為相同。 當某人建立策略時，將進行比較以檢查是否已存在同名策略。 除帶重音的字元外，比較無法區分相同的名稱。 假定已將策略添加到資料庫中，並且不添加新策略。

1. 按一下「確定」。

## 刪除策略 {#delete-a-policy}

您可以刪除已建立的原則。 管理員可以刪除任何用戶建立的策略。 策略集協調者可以刪除其策略集中的策略。 您刪除的策略仍對受該策略保護的文檔強制執行。 一次可以刪除多個策略。

只有管理員啟用此功能時，受邀用戶才能刪除策略。 如果無法刪除策略，則刪除選項將不可用。

1. 在文檔安全頁上，按一下「策略」。
1. 按一下「我的策略」頁簽。
1. 要刪除共用策略，請按一下「策略集」頁簽，然後按一下相應的策略集名稱。
1. 選擇相應策略旁的複選框，然後按一下「刪除」，然後按一下「確定」。

>[!NOTE]
>
>必須使用客戶端應用程式從文檔中刪除策略。 (請參閱Acrobat說明或適當的Acrobat Reader DC擴充功能說明)。

## 對策略清單進行排序 {#sort-the-policy-list}

您可以按列標題對策略清單進行排序，以便更輕鬆地查找策略。 欄標題旁的三角形圖示表示目前要排序的欄。 向上指向的三角形表示升序，而向下指向的三角形表示降序。

1. 在文檔安全頁上，按一下「策略」，然後按一下「策略集」頁簽。
1. 選擇策略集，然後按一下「策略」頁簽。
1. 按一下適當的欄標題。
1. 要更改排序順序，請再次按一下列。
