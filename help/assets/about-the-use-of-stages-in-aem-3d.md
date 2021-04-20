---
title: 關於在3D中使AEM用階段
seo-title: 關於在3D中使AEM用階段
description: 舞台是輕量級的3D場景檔案，可提供基本的檢視環境。
seo-description: 舞台是輕量級的3D場景檔案，可提供基本的檢視環境。
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
exl-id: 6d82fec0-608e-4eaa-aebd-b3ce2f7d8088
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# 關於在3D &lt;a0/AEM>中使用階段{#about-the-use-of-stages-in-aem-d}

階段是輕量級的3D場景檔案，可提供基本的檢視環境（光源、背景、地面或其他固定幾何）、選購的預先定義相機，以及協力廠商轉譯器的轉譯設定。

>[!NOTE]
>
>**[!UICONTROL OBJ 3D]**&#x200B;格式不支援指示燈。 因此，它無法用於提供3DAEM的階段。

舞台的檔案格式會決定您可與該舞台搭配使用的轉譯器。 例如，如果Autodesk® Maya®用於高品質的演算，則舞台必須是`.ma`或`.mb`格式。 如果您只想使用預設的Rapid Refine™轉譯器，則任何支援的舞台檔案格式都可接受。

除輸出影像類AEM型和大小外，所有3D演算設定都必須預先設定並儲存至舞台檔案，然後再上傳至AEM。
