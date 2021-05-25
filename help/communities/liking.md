---
title: 使用贊
seo-title: 使用贊
description: 新增及設定按贊元件
seo-description: 新增及設定按贊元件
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# 按贊{#using-liking}

`Liking`元件是一種有用的工具，可讓使用者對特定內容（例如論壇內的評論）發表意見。 使用`Liking`元件，成員選擇心臟表徵圖以指示正面意見。

## 為頁面按贊{#adding-liking-to-a-page}

若要在製作模式中將`Liking`元件新增至頁面，請使用元件瀏覽器來找出

* `Communities / Liking`

並將其拖曳至頁面上的位置，例如與功能相對的位置，供使用者按贊。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

包含[必要的用戶端程式庫](essentials-liking.md#essentials-for-client-side)時，會以此方式顯示`Liking`元件。

![chlimage_1-93](assets/chlimage_1-93.png)

## 配置按贊{#configuring-liking}

選取要存取的放置`Liking`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![chlimage_1-94](assets/chlimage_1-94.png)

在&#x200B;**[!UICONTROL 文字與標籤]**&#x200B;標籤下，指定用於記錄按贊的屬性。

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL 正面回應標籤]**
(
*必要*)正面回應的屬性名稱。

* **[!UICONTROL 負面回應標籤]**
(
*必要*)負回應的屬性名稱。

* **[!UICONTROL 記帳名稱]**
(
*必要*)此投票元件執行個體的內部、可識別屬性名稱。

## 網站訪客體驗{#site-visitor-experience}

### 成員 {#members}

會員可隨時變更其喜好。

### 匿名 {#anonymous}

不支援匿名贊。 網站訪客必須註冊（成為會員）並登入以參與按贊。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[按贊要點](essentials-liking.md)頁面。
