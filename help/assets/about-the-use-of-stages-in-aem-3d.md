---
title: 關於AEM 3D中階段的使用
seo-title: 關於AEM 3D中階段的使用
description: 舞台是輕量級的3D場景檔案，可提供基本的檢視環境。
seo-description: 舞台是輕量級的3D場景檔案，可提供基本的檢視環境。
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
translation-type: tm+mt
source-git-commit: 9cc06c16122b98146c51ac61d7fa27553a9d971e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# 關於在AEM 3D {#about-the-use-of-stages-in-aem-d}中使用階段

階段是輕量級的3D場景檔案，可提供基本的檢視環境（光源、背景、地面或其他固定幾何）、選購的預先定義相機，以及協力廠商轉譯器的轉譯設定。

>[!NOTE]
>
>**[!UICONTROL OBJ 3D]**&#x200B;格式不支援指示燈。 因此，它無法用來提供AEM 3D的階段。

舞台的檔案格式會決定您可與該舞台搭配使用的轉譯器。 例如，如果Autodesk® Maya®用於高品質的演算，則舞台必須是`.ma`或`.mb`格式。 如果您只想使用預設的Rapid Refine™轉譯器，則任何支援的舞台檔案格式都可接受。

在上傳至AEM之前，除輸出影像類型和大小外，AEM 3D中的所有演算設定都必須預先設定並儲存至舞台檔案中。