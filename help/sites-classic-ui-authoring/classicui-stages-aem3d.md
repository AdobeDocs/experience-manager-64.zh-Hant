---
title: 關於AEM 3D中階段的使用
seo-title: 關於AEM 3D中階段的使用
description: 階段是輕量級的3D場景檔案，可提供基本的檢視環境（光源、背景、地面或其他固定幾何）、選購的預先定義相機，以及協力廠商轉譯器的轉譯設定。
seo-description: 階段是輕量級的3D場景檔案，可提供基本的檢視環境（光源、背景、地面或其他固定幾何）、選購的預先定義相機，以及協力廠商轉譯器的轉譯設定。
uuid: 303ecbbd-131e-4c6f-812a-1e056b1e1d63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: cbcfbe88-e60c-446c-bbfe-2509831d6c22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# 關於AEM 3D中階段的使用{#about-the-use-of-stages-in-aem-d}

階段是輕量級的3D場景檔案，可提供基本的檢視環境（光源、背景、地面或其他固定幾何）、選購的預先定義相機，以及協力廠商轉譯器的轉譯設定。

>[!NOTE]
>
>OBJ 3D格式不支援光源。 因此，它無法用來提供AEM 3D的階段。

舞台的檔案格式會決定您可與該舞台搭配使用的轉譯器。 例如，如果Autodesk® Maya®用於高品質的演算，則舞台必須是或 `.ma` 格 `.mb` 式。 如果您只想使用預設的Rapid Refine™轉譯器，則任何支援的舞台檔案格式都可接受。

AEM 3D中的所有演算設定，除輸出影像類型和大小外，必須預先設定並儲存至舞台檔案，才能上傳至AEM。

