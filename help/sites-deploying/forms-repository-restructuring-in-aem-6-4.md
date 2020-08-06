---
title: AEM 6.4中的Forms Repository Restructing
seo-title: AEM 6.4中的Forms Repository Restructing
description: 瞭解如何進行必要的變更，以移轉至AEM 6.4 for Forms中的新儲存庫結構。
seo-description: 瞭解如何進行必要的變更，以移轉至AEM 6.4 for Forms中的新儲存庫結構。
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 7%

---


# AEM 6.4中的Forms Repository Restructing{#forms-repository-restructuring-in-aem}

如AEM 6.4 [](/help/sites-deploying/repository-restructuring.md) （AEM 6.4中的父資料庫重組）頁面所述，升級至AEM 6.4的客戶應使用此頁面來評估與影響AEM Forms Solution的資料庫變更相關的工作量。 有些變更需要在AEM 6.4升級程式中努力工作，而有些則會延遲至6.5升級。

**使用6.4升級**

* [其他](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**6.5升級版之前**

* [Echosign Cloud服務設定](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Recaptcha雲端服務組態](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Typekit雲端服務設定](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [其他](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## 使用6.4升級 {#with-upgrade}

### 其他 {#misc}

| **上一個位置** | `/etc/clientlibs/fd/fp` |
|---|---|
| **新位置** | `/libs/fd/fp/components` |
| **重組指導** | 自訂程式碼中對「舊版」位置的任何明確參照都必須更新至「新增」位置。 |
| **附註** | 不應修改或擴展這些客戶端庫。 |

| **上一個位置** | `/etc/clientlibs/fd/rte` |
|---|---|
| **新位置** | `/libs/fd/rte` |
| **重組指導** | 對於客戶機庫中可以通過絕對路徑引用的資源，您需要在新資產中使用較新的路徑。 |
| **附註** | N/A |

| **上一個位置** | `/etc/clientlibs/fd/af` |
|---|---|
| **新位置** | `/libs/fd/af/authoring/clientlibs` |
| **重組指導** | 對於客戶機庫中可以通過絕對路徑引用的資源，您需要在新資產中使用較新的路徑。 |
| **附註** | N/A |

| **上一個位置** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **新位置** | `/libs/fd/xfaforms/clientlibs/` |
| **重組指導** | 對於客戶機庫中可以通過絕對路徑引用的資源，您需要在新資產中使用較新的路徑。 |
| **附註** | N/A |

| **上一個位置** | `/etc/clientlibs/fd/af` |
|---|---|
| **新位置** | `/libs/fd/af/runtime/clientlibs` |
| **重組指導** | 對於客戶機庫中可以通過絕對路徑引用的資源，您需要在新資產中使用較新的路徑。 |
| **附註** | N/A |

| **上一個位置** | `/etc/clientlibs/fd/af` |
|---|---|
| **新位置** | `/libs/fd/af/runtime/clientlibs` |
| **重組指導** | 對於客戶機庫中可以通過絕對路徑引用的資源，您需要在新資產中使用較新的路徑。 |
| **附註** | N/A |

| **上一個位置** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **新位置** | `/libs/fd/expeditor/clientlibs` |
| **重組指導** | 對於客戶機庫中可以通過絕對路徑引用的資源，您需要在新資產中使用較新的路徑。 |
| **附註** | N/A |

| **上一個位置** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **新位置** | `/libs/fd/fmaddon` |
| **重組指導** | 不建議或支援變更這些clientlibs。 如果已對這些clientlibs進行修改，則應回滾以使用AEM提供的程式碼。 |
| **附註** | N/A |

| **上一個位置** | `/etc/aep` |
|---|---|
| **新位置** | `/var/fd/content/annotations` |
| **重組指導** | 不建議或支援變更這些clientlibs。 如果已對這些clientlibs進行修改，則應回滾以使用AEM提供的程式碼。 |
| **附註** | N/A |

## 6.5升級版之前 {#prior-to-upgrade}

### Echosign Cloud服務設定 {#echosign-cloud-service-configuration}

| **上一個位置** | `/etc/cloudservices/echosign` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **重組指導** | 要從 [Forms Migration UI觸發的Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) （懶惰內容移轉）實用程式。 |
| **附註** | N/A |

### Recaptcha雲端服務組態 {#recaptcha-cloud-service-configurations}

| **上一個位置** | `/etc/cloudservices/recaptcha` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **重組指導** | 要從 [Forms Migration UI觸發的Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) （懶惰內容移轉）實用程式。 |
| **附註** | N/A |

### Typekit雲端服務設定 {#typekit-cloud-service-configurations}

| **上一個位置** | `/etc/cloudservices/typekit` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **重組指導** | 要從 [Forms Migration UI觸發的Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) （懶惰內容移轉）實用程式。 |
| **附註** | N/A |

### 其他 {#misc-1}

| **上一個位置** | `/etc/cloudservices/fdm` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **重組指導** | 要從 [Forms Migration UI觸發的Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) （懶惰內容移轉）實用程式。 |
| **附註** | N/A |

| **上一個位置** | `/etc/designs/fd/fp` |
|---|---|
| **新位置** | `/libs/fd/fp` |
| **重組指導** | 對/etc模板的任何引用最終應更新為指向其對應 `/libs` 項。 |
| **附註** | N/A |

