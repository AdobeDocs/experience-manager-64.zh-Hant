---
title: 連結檢查程式
description: 「連結檢查程式」可協助驗證內部和外部連結，並允許連結重新寫入。
exl-id: 30718d02-3370-48aa-a5ba-242d5efaa14c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# 連結檢查程式 {#the-link-checker}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

內容作者不必擔心要驗證其內容頁面中包含的每個連結。

「連結檢查程式」會自動協助內容作者處理其連結，包括：

* 在連結新增至內容時驗證連結
* 顯示內容中所有外部連結的清單
* 執行連結轉換

「連結檢查程式」有 [配置選項](#configuring) 例如，定義驗證內部，允許從驗證中忽略某些連結或連結路徑，以及重寫連結重寫規則。

連結檢查程式會驗證兩者 [內部連結](#internal) 和 [外部連結。](#external)

>[!NOTE]
>
>由於「連結檢查器」會檢查每個內容頁面的連結，因此「連結檢查器」可能會影響大型存放庫的效能。 在這種情況下，您可能需要 [設定連結檢查程式的執行頻率](#configuring) 或 [將其停用。](#disabling)

## 內部連結檢查 {#internal}

內部連結是AEM存放庫中其他內容的連結。 可使用RTE的路徑選擇器或自訂元件來新增內部連結。 例如：

* 您的頁面 `/content/wknd/us/en/adventures/ski-touring.html`
* 包含連結至 `/content/wknd/us/en/adventures/extreme-ironing.html` 在 [文字元件。](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

內容作者新增內部連結至頁面時，就會立即驗證內部連結。 如果連結變成無效：

* 它會從發行者中移除。 連結的文字仍會保留，但連結本身會遭到移除。
* 在製作介面中會顯示為中斷的連結。

![編寫頁面時內部連結損毀](assets/link-checker-invalid-link-internal.png)

## 外部連結檢查 {#external}

外部連結是指向AEM存放庫外部內容的連結。 可使用RTE或自訂元件來新增外部連結。 例如：

* 您的頁面 `/content/wknd/us/en/adventures/ski-touring.html`
* 包含連結至 `https://bunwarmerthermalunderwear.com` 在 [文字元件。](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

外部連結會透過語法和檢查其可用性來驗證。 此檢查會在可設定的內部非同步執行。 如果連結檢查器發現外部連結無效：

* 它會從發行者中移除。 連結的文字仍會保留，但連結本身會遭到移除。
* 在製作介面中會顯示為中斷的連結。

![編寫頁面時內部連結損毀](assets/link-checker-invalid-link-external.png)

此外， [外部連結檢查程式](#external-link-checker) 介面提供內容頁面上所有外部連結的概觀。

### 使用外部連結檢查程式 {#external-link-checker}

要使用外部連結檢查器：

1. 使用 **導覽**，選取 **工具**，然後 **網站**.
1. 選擇 **外部連結檢查程式** 並顯示所有外部連結的清單。

![「外部連結檢查器」窗口](assets/external-link-checker.png)

會顯示下列資訊：

* **狀態**  — 連結的驗證狀態，可能為下列其中一項：
   * **有效**  — 連結檢查器可訪問外部連結
   * **待定**  — 外部連結已新增至網站內容，但尚未通過連結檢查程式驗證
   * **無效**  — 連結檢查程式無法存取外部連結
* **URL**  — 外部連結
* **反向連結**  — 包含外部連結的內容頁面
   * 這只會填入 [若已設定。](#configuring)
* **上次檢查**  — 上次連結檢查器驗證外部連結時
   * 檢查連結的頻率 [可設定。](#configuring)
* **上次狀態**  — 上次勾選連結時傳回的上次HTML狀態代碼
* **上次可用**  — 自上次連結可供「連結檢查器」使用後所經過的時間
* **上次存取**  — 自上次在編寫介面中存取含有外部連結的頁面以來的時間

您可以使用連結清單頂端的兩個按鈕來操控視窗的內容：

* **重新整理**  — 要刷新清單的內容
* **檢查**  — 檢查清單中選取的個別外部連結

### 外部連結檢查程式的運作方式 {#how-it-works}

外部連結檢查程式雖然簡單易用，但需仰賴許多服務並了解其運作方式，協助您了解如何 [配置連結檢查器](#configuring) 以滿足您的需求。

1. 每當內容作者儲存頁面的任何連結時，就會觸發事件處理常式。
1. 事件處理常式會周遊 `/content` 並檢查新連結或更新的連結，並將其新增至「連結檢查程式」的快取。
1. 此 **日CQ連結檢查程式服務** 然後按常規計畫執行，以檢查快取中的條目是否有效。
1. 經過語法驗證的連結隨後出現在 [外部連結檢查程式](#external-link-checker) 窗口。 不過，它們會在 **待定** 狀態。
1. 此 **日CQ連結檢查程式任務** 然後定期執行，以透過進行GET呼叫來驗證連結。
1. 此 **日CQ連結檢查程式任務** 接著，會使用GET呼叫的結果更新「外部連結檢查器」視窗中的項目。

## 配置連結檢查器 {#configuring}

AEM中的「連結檢查程式」會自動立即可用。 不過，有許多OSGi設定可修改以變更其行為：

* **日CQ連結檢查程式資訊儲存服務**  — 此服務定義儲存庫中的連結檢查器快取的大小。
* **日CQ連結檢查程式服務**  — 此服務會執行外部連結語法的非同步檢查。 您可以定義檢查期間，以及檢查程式在其他選項中跳過哪些類型的連結。
* **日CQ連結檢查程式任務**  — 此服務會執行外部連結的GET驗證。 它允許區間的不同定義，以檢查其他選項中的錯誤和良好連結。
* **Day CQ鏈路檢查器變壓器**  — 允許根據用戶定義的規則集轉換連結。

請參閱檔案 [OSGi組態設定](/help/sites-deploying/osgi-configuration-settings.md) 以取得如何變更OSGi設定的詳細資訊。

## 禁用連結檢查器 {#disabling}

您可以選擇完全停用連結檢查程式。 若要這麼做：

1. 開啟OSGi主控台。
1. 編輯 **Day CQ鏈路檢查器變壓器**
1. 勾選您要停用的選項：
   * **禁用檢查**  — 禁用連結驗證
   * **禁用重寫**  — 禁用連結轉換

>[!NOTE]
>
>如果您在開始建立內容後停用連結檢查，您仍可能在 [外部連結檢查程式視窗](#external-link-checker)，但不會再更新。
