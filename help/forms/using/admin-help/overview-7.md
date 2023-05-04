---
title: 表單設定基本知識
seo-title: Basics of configuring forms
description: 了解有助於您建立互動式資料擷取應用程式的各種表單服務。
seo-description: Learn about the various forms services that help you create interactive data capture applications.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 616cd550-c3bd-4daf-887d-0470f1b08389
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 2%

---

# 表單設定基本知識 {#basics-of-configuring-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Forms服務可讓您建立互動式資料擷取用戶端應用程式，以驗證、處理、轉換及傳遞通常在Designer中建立的表單。 表單作者開發單一表單設計，Forms服務會以各種格式轉譯：

* 在Adobe Reader中或在瀏覽器中做為PDF
* HTML，包括相容的XHTML 1.0轉譯
* 作為表單指南，適用於支援AdobeFlash Player的各種瀏覽器環境。

如需Forms服務的其他資訊，請參閱 [服務參考](https://www.adobe.com/go/learn_aemforms_services_63).

使用管理控制台中的Forms頁面，您可以設定Forms服務的行為。 這些設定適用於服務的所有調用。 任何透過AEM Forms SDK傳送的參數都會覆寫管理控制台中設定的設定；但是，它們只影響該特定調用。

在管理控制台中變更Forms設定後，按一下「儲存」 。 您不需要重新啟動伺服器，變更才會生效。 不過，在配置快取模式設定時，您可能需要停止並重新啟動Forms服務。 (請參閱 [啟動和停止服務](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
