---
title: 建立並指派啟用資源
seo-title: 建立並指派啟用資源
description: 新增啟用資源
seo-description: 新增啟用資源
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 2%

---


# 建立並分配啟用資源{#create-and-assign-enablement-resources}

## 添加啟用資源{#add-an-enablement-resource}

要向新社區站點添加啟用資源，請執行以下操作：

* 關於作者實例
   * 例如，[http://localhost:4502/](http://localhost:4503/)
* 以系統管理員身分登入
* 在全局導航中，選擇&#x200B;**社區> [資源](resources.md)**

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* 選取要新增啟用資源的社群網站
   * 選取 `Enablement Tutorial`
* 從菜單中，選擇` Create`
* 選擇&#x200B;**[!UICONTROL 資源]**

![chlimage_1-201](assets/chlimage_1-201.png)

### 基本資訊 {#basic-info}

填寫資源的基本資訊：

* **[!UICONTROL 網站名稱]**:設定為所選社區站點的名稱：啟用教學課程
* **[!UICONTROL 資源名稱(&amp;A)]**:滑雪課程1
* **[!UICONTROL 標籤]**:教學課程：運動／滑雪
* **[!UICONTROL 在目錄中顯示]**:開啟
* **[!UICONTROL 說明]**:為初學者在雪上滑動
* **[!UICONTROL 新增影像]**:在其「分配」視圖中為成員添加表示資源的映像
   ![chlimage_1-202](assets/chlimage_1-202.png)
* 選擇&#x200B;**[!UICONTROL Next]**

### 新增內容 {#add-content}

雖然它看起來好像可以選擇多個資源，但只允許一個。

選擇右上角的`'+' icon` ，以通過標識源開始選擇資源的過程。

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

上傳資源。 如果視訊資源，請上傳自訂影像以在視訊開始播放前顯示，或允許從視訊產生縮圖（可能需要幾分鐘——不需要等待）。

![chlimage_1-205](assets/chlimage_1-205.png)

* 選擇&#x200B;**[!UICONTROL Next]**

### 設定 {#settings}

* **[!UICONTROL 社交設]**
定讓學員在體驗註解和啟用資源評分時，保留預設設定。
* **[!UICONTROL 到期日期]**

   *（可選）* 可以選擇完成分配的日期。
* **[!UICONTROL 資原作者]**

   *（可選）* 留空。
* **[!UICONTROL 資源聯絡與發佈；]**

   *（必要）使* 用下拉菜單選擇成員 `Quinn Harper`。
* **[!UICONTROL 資源專家]**

   *（可選）* 留空。
   **注意**:如果不顯示用戶或組，請檢查是否已將其添加到組中， `Community Enable Members` 並 ** 保存發佈實例。
   ![chlimage_1-206](assets/chlimage_1-206.png)
* 選擇&#x200B;**[!UICONTROL Next]**

### 指定任務 {#assignments}

* **[!UICONTROL 新增]**
受指派者保留未設定，因為此啟用資源將新增至學習路徑。如果將學員指派給個別的啟用資源以及包含啟用資源的學習路徑，則會將學員指派給啟用資源兩次。

![chlimage_1-207](assets/chlimage_1-207.png)

* 選擇&#x200B;**[!UICONTROL 建立]**

![chlimage_1-208](assets/chlimage_1-208.png)

成功建立資源將返回資源控制台，並選擇新建的資源。 在此主控台中，您可以發佈、新增學員並變更其他設定。

若要上傳新版啟用資源，建議您建立新資源，然後從舊版中取消註冊成員，並將他們註冊到新版本。

### 發佈資源{#publish-the-resource}

註冊者必須先發佈它，才能查看已指派的資源：

* 選擇全球`Publish`圖示

啟動已確認並顯示成功訊息：

![chlimage_1-209](assets/chlimage_1-209.png)

## 添加第二個啟用資源{#add-a-second-enablement-resource}

重複上述步驟，建立並發佈第二個相關的啟用資源，從中建立學習路徑。

![chlimage_1-210](assets/chlimage_1-210.png)

**發** 布第二個資源。

返回其資源的啟用教學課程清單。

*提示：如果兩個資源都不可見，請刷新頁面。*

![chlimage_1-211](assets/chlimage_1-211.png)

## 添加學習路徑{#add-a-learning-path}

學習路徑是構成課程的啟用資源的邏輯分組。

* 從資源控制台中，選擇`+ Create`
* 選擇&#x200B;**[!UICONTROL 學習路徑]**

![chlimage_1-212](assets/chlimage_1-212.png)

添加&#x200B;**[!UICONTROL 基本資訊]**:

* **[!UICONTROL 學習路徑名稱]**:滑雪課
* **[!UICONTROL 標籤]**:教學課程：滑雪
* **[!UICONTROL 在目錄中顯示]**:未選中
* **[!UICONTROL 上傳影]** 像以代表資源主控台中的學習路徑

![chlimage_1-213](assets/chlimage_1-213.png)

* 選擇&#x200B;**[!UICONTROL Next]**

略過下一個面板，因為沒有要新增的先決學習路徑。

* 選擇&#x200B;**[!UICONTROL Next]**

在「新增資源」面板上

* 選擇`+ Add Resources`以選擇要添加到學習路徑的2個滑雪課程資源

   注意：將只能選擇&#x200B;**published**&#x200B;資源。

>[!NOTE]
>
>您只能選擇與學習路徑位於同一級別的可用資源。 例如，對於在群組中建立的學習路徑，只有群組層級資源可供使用；對於在社群網站中建立的學習路徑，該網站中的資源可供新增至學習路徑。

* 選擇&#x200B;**[!UICONTROL 提交]**。

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* 選擇&#x200B;**[!UICONTROL Next]**

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL 新增受]**
指派者使用下拉式功能表來選取 
`Community Ski Class` 群組，其中應包含成 `Riley Taylor` 員  `Sidney Croft.`

* **[!UICONTROL 學習路徑連絡與快速；]**

   *（必要）使* 用下拉菜單選擇成員 `Quinn Harper`。

* 選擇&#x200B;**[!UICONTROL 建立]**

![chlimage_1-217](assets/chlimage_1-217.png)

成功建立學習路徑將返回「資源」(Resources)控制台，並選擇新建的學習路徑。 在此主控台中，您可以發佈、新增學員並變更其他設定。

**發** 布學習路徑。

