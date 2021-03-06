---
title: 擴充ContextHub
seo-title: 擴充ContextHub
description: 當提供的儲存和模組不符合您的解決方案需求時，定義新類型的ContextHub儲存和模組
seo-description: 當提供的儲存和模組不符合您的解決方案需求時，定義新類型的ContextHub儲存和模組
uuid: 1d80c01d-ec5d-4e76-849d-bec0e1c3941a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 13a908ae-6965-4438-96d0-93516b500884
exl-id: 15b17bed-3422-43cf-b1af-91d9e0c5dfcb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---

# 擴展ContextHub{#extending-contexthub}

當提供的儲存和模組不符合您的解決方案需求時，定義新類型的ContextHub儲存和模組。

## 建立自定義儲存候選項{#creating-custom-store-candidates}

ContextHub存放區是根據註冊存放區候選項目建立。 若要建立自訂商店，您需要建立並註冊商店候選商店。

包含建立和註冊儲存候選項的代碼的javascript檔案必須包含在[客戶端庫資料夾](/help/sites-developing/clientlibs.md#creating-client-library-folders)中。 資料夾的類別必須符合下列模式：

```xml
contexthub.store.[storeType]
```

類別的`[storeType]`部分是註冊儲存候選項的`storeType`。 （請參閱[註冊ContextHub儲存候選項](/help/sites-developing/ch-extend.md#registering-a-contexthub-store-candidate)）。 例如，對於`contexthub.mystore`的storeType，客戶端庫資料夾的類別必須為`contexthub.store.contexthub.mystore`。

### 建立ContextHub儲存候選項{#creating-a-contexthub-store-candidate}

要建立儲存候選項，請使用[`ContextHub.Utils.inheritance.inherit`](/help/sites-developing/contexthub-api.md#inherit-child-parent)函式擴展一個基儲存：

* [&#39;ContextHub.Store.PerisentStore&#39;](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [&#39;ContextHub.Store.SessionStore&#39;](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [&#39;ContextHub.Store.JSONPStore&#39;](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore)
* [&#39;ContextHub.Store.PerisentJSONPStore&#39;](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)

請注意，每個基本儲存區都延伸[`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core)儲存區。

下面的示例建立`ContextHub.Store.PersistedStore`儲存候選項的最簡單擴展：

```
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

實際上，您的自訂存放區候選項目將定義其他函式或覆寫存放區的初始設定。 若干[樣本存放區候選項](/help/sites-developing/ch-samplestores.md)安裝在`/libs/granite/contexthub/components/stores`下方的存放庫中。 若要從這些範例中學習，請使用CRXDE Lite來開啟javascript檔案。

### 註冊ContextHub儲存候選項{#registering-a-contexthub-store-candidate}

註冊候選儲存庫以將其與ContextHub框架整合，並允許從中建立儲存庫。 要註冊儲存候選項，請使用`ContextHub.Utils.storeCandidates`類的[`registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies)函式。

註冊商店候選項時，您會提供商店類型的名稱。 從候選項建立商店時，您可以使用商店類型來識別其所根據的候選項。

註冊商店候選項時，您會指明其優先順序。 當使用與已註冊的儲存候選相同的儲存類型來註冊儲存候選時，使用優先順序較高的候選。 因此，您可以使用新實施來覆寫現有的商店候選項目。

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

在大多數情況下，只需要一個候選項，並且優先順序可以設定為`0`，但如果您有興趣，可以了解[更多高級註冊，](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies)允許根據javascript條件(`applies`)和候選優先順序選擇少數儲存實施之一。

## 建立ContextHub UI模組類型{#creating-contexthub-ui-module-types}

當隨ContextHub](/help/sites-developing/ch-samplemodules.md)安裝的[模組類型不符合您的需求時，建立自訂UI模組類型。 要建立UI模組類型，請通過擴展`ContextHub.UI.BaseModuleRenderer`類，然後向`ContextHub.UI`註冊它來建立新的UI模組轉譯器。

要建立UI模組呈現器，請建立`Class`對象，該對象包含呈現UI模組的邏輯。 至少，您的類必須執行以下操作：

* 擴展`ContextHub.UI.BaseModuleRenderer`類。 此類別是所有UI模組轉譯器的基本實作。 `Class`對象定義了名為`extend`的屬性，用於將此類命名為正在擴展的類。

* 提供預設設定。 建立`defaultConfig`屬性。 此屬性是一個對象，包含為[`contexthub.base`](/help/sites-developing/ch-samplemodules.md#contexthub-base-ui-module-type) UI模組定義的屬性，以及您需要的任何其他屬性。

`ContextHub.UI.BaseModuleRenderer`的源位於/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js。  要註冊渲染器，請使用`ContextHub.UI`類的[`registerRenderer`](/help/sites-developing/contexthub-api.md#registerrenderer-moduletype-renderer-dontrender)方法。 您必須提供模組類型的名稱。 管理員根據此轉譯器建立UI模組時，會指定此名稱。

在自行執行的匿名函式中建立並註冊渲染器類。 以下範例是以contexthub.browserinfo UI模組的原始碼為基礎。 此UI模組是`ContextHub.UI.BaseModuleRenderer`類的簡單擴展。

```xml
;(function() {

    var SurferinfoRenderer = new Class({
        extend: ContextHub.UI.BaseModuleRenderer,

        defaultConfig: {
            icon: 'coral-Icon--globe',
            title: 'Browser/OS Information',

            storeMapping: {
                surferinfo: 'surferinfo'
            },

            template:
                '<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p>' +
                '<p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>'
        }
    });

    ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());

}());
```

[用戶端程式庫資料夾](/help/sites-developing/clientlibs.md#creating-client-library-folders)中必須包含包含建立和註冊轉譯器的程式碼的javascript檔案。 資料夾的類別必須符合下列模式：

```xml
contexthub.module.[moduleType]
```

類別的`[moduleType]`部分是註冊模組呈現器的`moduleType`。 例如，對於`contexthub.browserinfo`的`moduleType`，客戶端庫資料夾的類別必須為`contexthub.module.contexthub.browserinfo`。
