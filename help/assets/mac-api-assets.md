---
title: Assets HTTP API
description: 瞭解Assets HTTP API的實作、資料模型和功能。 使用資產HTTP API執行資產相關的各種工作
contentOwner: AG
translation-type: tm+mt
source-git-commit: 57952323a3ae0990232506d551b91b724f830f20

---


# Assets HTTP API {#assets-http-api}

資產HTTP API可讓您對資產執行建立——讀取——更新——刪除(CRUD)作業，包括二進位、中繼資料、轉譯和註解，以及使用AEM內容片段的結構化內容。 它在公開， `/api/assets` 並實作為REST API。

若要存取API:

1. 在中開啟API服務文檔 `http://[hostname]:[port]/api.json`。
1. 請依循「資產」服務連結，前往 `http://[hostname]:[server]/api/assets.json`。

API回應是某些MIME類型的JSON，也是所有MIME類型的回應代碼。 JSON回應是選擇性的，可能無法使用，例如PDF檔案。 請依賴回應程式碼進行進一步分析或動作。

在「關 [!UICONTROL 閉時間]」後，資產及其轉譯無法透過「資產」網頁介面或HTTP API使用。 如果「開機時間」是未來，或「關機時間 [!UICONTROL 」是過去] ,API會傳回404錯誤訊息。

## Data model {#data-model}

Assets HTTP API會公開兩個主要元素、資料夾和資產。

### 資料夾 {#folders}

資料夾類似於傳統檔案系統中的目錄。 它們是其他資料夾或斷言的容器。 資料夾具有以下元件：

**實體**:資料夾的實體是其子元素，可以是資料夾和資產。

**屬性**:

```
name  -- Name of the folder. This is the same as the last segment in the URL path without the extension
title -- Optional title of the folder which can be displayed instead of its name
```

>[!NOTE]
>
>資料夾或資產的某些屬性會對應至不同的首碼。 JCR前置詞 `jcr:title`為、 `jcr:description`和 `jcr:language` ，將替換為 `dc` 前置詞。 因此，在傳回的JSON `dc:title` 中， `dc:description` 並分別 `jcr:title` 包含值和 `jcr:description`值。

**「連結** 」檔案夾會公開三個連結：

```xml
self      -- Link to itself
parent    -- Link to the parent folder
thumbnail -- (Optional) link to a folder thumbnail image
```

### 資產 {#assets}

資產是多部分元素，包括：

* 資產的屬性和中繼資料。
* 多個轉譯，例如原始轉譯（原始上傳的資產）、縮圖和各種其他轉譯。 其他轉譯可能是不同大小的影像、不同的視訊編碼，或從PDF或Adobe inDesign擷取的頁面。
* 選用的注釋。

在AEM中，檔案夾包含下列元件：

* 實體：「資產」的子系是其轉譯。
* 屬性
* 連結

資產HTTP API包含下列功能：

* 檢索資料夾清單
* 建立資料夾
* 建立資產
* 更新資產二進位檔
* 更新資產中繼資料
* 建立資產轉譯
* 更新資產轉譯
* 建立資產註解
* 複製資料夾或資產
* 移動資料夾或資產
* 刪除資料夾、資產或轉譯

>[!NOTE]
>
>為方便閱讀，下列範例會省略完整的cURL符號。 事實上，此符號確實與 [Resty](https://github.com/micha/resty) （cURL的指令碼包裝函式）相關。

**必備條件**

* 前往 `https://[AEM_server]:[port]/system/console/configMgr`.
* 導覽至 **[!UICONTROL Adobe Granite CSRF Filter]**。
* 請確定屬性篩選 **[!UICONTROL 方法]** : `POST`, `PUT`, `DELETE`。

## 檢索資料夾清單 {#retrieve-a-folder-listing}

檢索現有資料夾及其子實體（子資料夾或資產）的Siren表示法。

**要求**

```
GET /api/assets/myFolder.json
```

**回應碼**

```
200 - OK - success
404 - NOT FOUND - folder does not exist or is not accessible
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

**回應**

傳回的實體類別為assets/folder。

包含實體的屬性是每個實體的完整屬性集的子集。 為了取得實體的完整表示法，用戶端應擷取連結所指向之URL的內容，連結 `rel` 為 `self`:

## 建立資料夾 {#create-a-folder}

建立新 `sling`:在 `OrderedFolder` 給定路徑。 如果是&amp;ast;為，而不是節點名稱，則servlet將使用參數名稱作為節點名稱。 接受為請求資料是新資料夾的Siren表示法或一組名稱——值配對，編碼為 `application/www-form-urlencoded` 或 `multipart`/ `form``data`-，對直接從HTML表單建立資料夾非常有用。 此外，資料夾的屬性可指定為URL查詢參數。

如果給定路徑的父節 `500` 點不存在，操作將失敗，並帶有響應代碼。 如果資料夾已存在，則會傳 `409` 回回應代碼。

**參數**

```
name - Folder name
```

**要求**

```
POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'
```

或

```
POST /api/assets/* -F"name=myfolder" -F"title=My Folder"
```

**回應碼**

```
201 - CREATED - on successful creation
409 - CONFLICT - if folder already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 建立資產 {#create-an-asset}

在指定路徑上使用指定檔案建立DAM資產。 如果是&amp;ast;為，而不是節點名稱，則servlet將使用參數名稱或檔案名作為節點名稱。

**參數**

```
name - Asset name
file - File reference
```

**要求**

```
POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"
```

或

```
POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"
```

**回應碼**

```
201 - CREATED - if Asset has been created successfully
409 - CONFLICT - if Asset already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 更新資產二進位檔 {#update-asset-binary}

更新資產二進位（原始名稱的轉譯）。 如果已設定，則會觸發預設資產工作流程。

**要求**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png
```

**回應碼**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 更新資產中繼資料 {#update-asset-metadata}

更新資產中繼資料屬性。

**要求**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'
```

**回應碼**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 建立資產轉譯 {#create-an-asset-rendition}

建立資產的新資產轉譯。 如果未提供請求參數名稱，則使用檔案名稱做為轉譯名稱。

**參數**

```
name - Rendition name
file - File reference
```

**要求**

```
POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"
```

或

```
POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"
```

**回應碼**

```
201 - CREATED - if Rendition has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 更新資產轉譯 {#update-an-asset-rendition}

更新會分別以新的二進位資料取代資產轉譯。

**要求**

```
PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png
```

**回應碼**

```
200 - OK - if Rendition has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 建立資產注釋 {#create-an-asset-comment}

建立新資產註解。

**參數**

```
message - Message
annotationData - Annotation data (JSON)
```

**要求**

```
POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"
```

**回應碼**

```
201 - CREATED - if Comment has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 複製資料夾或資產 {#copy-a-folder-or-asset}

複製指定路徑上的資料夾或資產到新目標。

**請求標題**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - 'F' to prevent overwriting an existing destination
```

**要求**

```
COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"
```

**回應碼**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 移動資料夾或資產 {#move-a-folder-or-asset}

將指定路徑上的資料夾或資產移動到新目標。

**請求標題**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - either 'T' to force deletion of existing resources or 'F' to prevent overwriting an existing resource.
```

**要求**

```
MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"
```

**回應碼**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## 刪除資料夾、資產或轉譯 {#delete-a-folder-asset-or-rendition}

刪除給定路徑上的資源(-tree)。

**要求**

```
DELETE /api/assets/myFolder
```

或

```
DELETE /api/assets/myFolder/myAsset.png
```

或

```xml
DELETE /api/assets/myFolder/myAsset.png/renditions/original
```

**回應碼**

```
200 - OK - if folder has been deleted successfully
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

