---
title: Dynamic Media影片設定檔
description: 'Dynamic Media隨附預先定義的最適化視訊編碼設定檔。 此現成可用設定檔中的設定已最佳化，可為客戶提供最佳的視訊檢視體驗。 '
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
exl-id: 3602e1b9-624d-408f-a7f6-1598b62dbd22
feature: 視訊設定檔，視訊
role: Admin,User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '3071'
ht-degree: 17%

---

# Dynamic Media影片設定檔 {#video-profiles}

Dynamic Media已隨附預先定義的最適化視訊編碼設定檔。 此現成可用設定檔中的設定已最佳化，可為客戶提供最佳的檢視體驗。 當您使用「最適化視訊編碼」設定檔為主視訊編碼時，在播放期間，視訊播放器會根據客戶的網際網路連線速度自動調整視訊資料流的品質。 這稱為最適化串流。

以下是決定視訊品質的其他因素：

* **上傳主視訊的解析度**

   如果MP4視頻以低解析度（如240p或360p）記錄，則不能以高清流式傳輸。

* **視訊播放器大小**

   依預設，適用性視訊編碼設定檔中的&#x200B;**[!UICONTROL Width]**&#x200B;會設為&#x200B;**[!UICONTROL Auto]**。 同樣地，在播放期間會根據播放器的大小使用最佳品質。

另請參閱[視訊編碼最佳作法](video.md#best-practices-for-encoding-videos)。

>[!NOTE]
>
>若要產生視訊的中繼資料和相關的視訊影像縮圖，視訊本身需要在動態媒體中執行編碼程式。在AEM中，如果您已啟用動態媒 **** 體並設定視訊雲端服務，「動態媒體編碼視訊」工作流程會對視訊進行編碼。此工作流程會擷取工作流程處理歷程記錄和失敗資訊。
>
>請參閱 [監控視訊編碼和YouTube發佈進度](video.md#monitoring-video-encoding-and-youtube-publishing-progress)。如果您已啟用Dynamic Media並設定視訊雲端服務，當您上傳視訊時，**[!UICONTROL Dynamic Media編碼視訊]**&#x200B;工作流程會自動生效。 (如果您未使用動態媒體， **[!UICONTROL DAM更新資產工作流程將生效]** 。)
>
>搜尋資產時，中繼資料很實用。 縮圖是編碼期間產生的靜態視訊影像。 AEM系統需要這些參數，並用於使用者介面，協助您在&#x200B;**[!UICONTROL 卡片檢視]**、**[!UICONTROL 搜尋結果]**&#x200B;檢視和&#x200B;**[!UICONTROL 資產清單]**&#x200B;檢視中以視覺方式識別視訊。 點選編碼視訊的&#x200B;**[!UICONTROL 轉譯]**&#x200B;圖示（畫家的浮動視窗）時，您可以看到產生的縮圖。

建立完視訊描述檔後，可將其套用至資料夾或多個資料夾。 請參閱[將視訊設定檔套用至資料夾。](#applying-a-video-profile-to-folders)

若要定義其他資產類型的進階處理參數，請參閱[設定資產處理](config-dms7.md#configuring-asset-processing)。

## 適用性視訊編碼預設集 {#adaptive-video-encoding-presets}

下表列出將設定檔編碼為行動裝置、平板電腦裝置和桌上型電腦的最適化視訊串流的最佳實務。 您可以將這些預設集用於任何外觀比例視訊。

<table> 
 <tbody> 
  <tr> 
   <td><strong>視訊格式轉碼器</strong></td> 
   <td><strong>視訊大小 — 寬度(px)</strong></td> 
   <td><strong>視訊大小 — 高度(px)</strong></td> 
   <td><strong>保持長寬比？</strong></td> 
   <td><strong>視訊位元速率(Kbps)</strong></td> 
   <td><strong>視訊影格速率(Fps)</strong></td> 
   <td><strong>音訊轉碼器</strong></td> 
   <td><strong>音頻位元速率(Kbps)</strong></td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264(mp4)</p> </td> 
   <td>auto</td> 
   <td>360</td> 
   <td>是</td> 
   <td>730</td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264(mp4)</p> </td> 
   <td>自動</td> 
   <td>540</td> 
   <td>是</td> 
   <td>2000<br /> </td> 
   <td>30</td> 
   <td>杜比HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264(mp4)</p> </td> 
   <td>自動</td> 
   <td>720<br /> </td> 
   <td>是</td> 
   <td>3000<br /> </td> 
   <td>30</td> 
   <td>杜比HE-AAC</td> 
   <td>128</td> 
  </tr> 
 </tbody> 
</table>

## 建立Dynamic Media視訊編碼設定檔以進行最適化串流 {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamic Media已隨附預先定義的適用性視訊編碼設定檔，此設定檔為一組適用於MP4 H.264的視訊上傳設定，並針對最佳的檢視體驗進行最佳化。 上傳影片時，您可以使用此設定檔。

不過，如果此預先定義的設定檔不符合您的需求，您可以選取建立自己的最適化視訊編碼設定檔。 當您使用設定&#x200B;**[!UICONTROL 編碼進行最適化串流]**-*最佳實務* — 您新增至設定檔的所有編碼預設集都會經過驗證，以確保所有視訊都有相同的外觀比例。 此外，編碼視訊被視為串流的多位元速率集。

當您建立視訊編碼設定檔時，您會發現大部分的編碼選項都已預先填入建議的預設設定，以協助您。 不過，如果您選取的值不是建議的預設值，請注意，這可能會在播放期間和其他效能問題導致視訊品質不佳。

因此，對於設定檔中的所有MP4 H.264視訊編碼預設集，會驗證下列值，以確保它們在設定檔中的各個編碼預設集之間相同，從而可進行最適化串流：

* 視頻格式編解碼器 — MP4 H.264(.mp4)
* 音訊轉碼器
* 音訊位元速率
* 保持長寬比
* 兩遍編碼
* 固定位元速率
* H264 設定檔
* 音訊取樣速率

如果值不同，您可以繼續依原樣建立設定檔。 不過請注意，不可能進行最適化串流。 而是讓使用者體驗單位元速率串流。 建議您編輯編碼設定，以便在設定檔中的各個編碼預設集之間使用相同的值。 （請注意，如果已啟用「最適化串流編碼&#x200B;]**」，視訊設定檔/預設集編輯器應強制同等使用最適化視訊編碼設定。）**[!UICONTROL 

另請參閱[建立漸進式串流的視訊編碼設定檔](#creating-a-video-encoding-profile-for-progressive-streaming)。

另請參閱[視訊編碼最佳作法](video.md#best-practices-for-encoding-videos)。

若要定義其他資產類型的進階處理參數，請參閱[設定資產處理](config-dms7.md#configuring-asset-processing)。

建立完視訊描述檔後，可將其套用至資料夾或多個資料夾。

**若要建立適用性串流的Dynamic Media視訊編碼設定檔**:

1. 點選或按一下AEM標誌，並導覽至「**[!UICONTROL 工具>資產>視訊描述檔]**」。
1. 點選&#x200B;**[!UICONTROL 建立]**&#x200B;以新增視訊描述檔。

1. 輸入設定檔的名稱和說明。
1. 確定已勾選適用性串流的&#x200B;**[!UICONTROL 編碼]**（預設）。
1. 點選&#x200B;**[!UICONTROL 新增視訊編碼預設集]**。
1. 在&#x200B;**[!UICONTROL Basic]**&#x200B;標籤上，設定視訊和音訊選項。

   請點選每個選項旁的資訊圖示，以取得其他說明或根據選取的視訊格式codec建議的設定。

1. 在「視訊大小」標題下，確定已勾選「**[!UICONTROL 保留外觀比例]**」 。
1. 設定視頻幀大小解析度（像素）。 使用&#x200B;**[!UICONTROL Auto]**&#x200B;值來自動縮放以匹配源長寬比（寬高比）。 例如「自動x 480」或「640」。

   執行下列任一操作：

   * 在&#x200B;**[!UICONTROL Width]**&#x200B;欄位中，輸入&#x200B;**[!UICONTROL auto]**。 在&#x200B;**[!UICONTROL Height]**&#x200B;欄位中，以像素輸入值。
   * 若要協助您視覺化視訊的大小，請點選&#x200B;**[!UICONTROL 資訊]**&#x200B;右側的&#x200B;**[!UICONTROL 高度]**&#x200B;圖示(i)，以開啟&#x200B;**[!UICONTROL 大小計算器]**&#x200B;頁面。 使用&#x200B;**[!UICONTROL 大小計算器]**&#x200B;設定您想要的視訊尺寸（由藍色方塊表示）。 完成後，點選右上角的&#x200B;**[!UICONTROL X]**。

1. （可選）點選&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤，並確定已選取&#x200B;**[!UICONTROL Use Default Values]**&#x200B;核取方塊（建議）。 或者，修改進階視訊和音訊設定。
1. 在頁面的右上角，點選&#x200B;**[!UICONTROL Save]**&#x200B;以儲存預設集。
1. 執行下列任一操作：

   * 重複步驟5-10以建立其他編碼預設集。 （最適化視訊串流需要多個視訊預設集。）
   * 在頁面的右上角，再次點選&#x200B;**[!UICONTROL Save]**&#x200B;以儲存描述檔。

## 監控編碼作業的進度 {#monitoring-the-progress-of-an-encoding-job}

顯示處理指標（或進度列），以便您能以視覺化方式監控視訊編碼工作的進度。

您也可以檢視`error.log`檔案，以監控編碼作業的進度、查看編碼是否已完成，或查看任何作業錯誤。 在安裝AEM例項的`logs`資料夾中找到`error.log`。

## 建立用於漸進式串流的Dynamic Media視訊編碼設定檔 {#creating-a-video-encoding-profile-for-progressive-streaming}

如果您選擇不使用「編碼」選項進行最適化串流 ****，請注意，您新增至描述檔的所有編碼預設集都會被視為個別視訊轉譯，以用於單位元速率串流或漸進式視訊傳送。此外，沒有驗證可確保所有視訊轉譯具有相同的外觀比例。

視您執行的模式而定，支援的視訊格式轉碼器如下：

* Dynamic Media-Scene7模式：H.264(.mp4)
* Dynamic Media — 混合模式：H.264(.mp4), WebM

另請參閱[建立最適化串流的視訊編碼設定檔](#creating-a-video-encoding-profile-for-adaptive-streaming)。

另請參閱[視訊編碼最佳作法](video.md#best-practices-for-encoding-videos)。

若要定義其他資產類型的進階處理參數，請參閱[設定資產處理](config-dms7.md#configuring-asset-processing)。

建立完視訊描述檔後，可將其套用至資料夾或多個資料夾。

**若要建立用於漸進式串流的Dynamic Media視訊編碼設定檔：**

1. 點選AEM標誌並導覽至「工 **[!UICONTROL 具 > 資產 >視 訊設定檔]**」。
1. 點選&#x200B;**[!UICONTROL 建立]**&#x200B;以新增視訊描述檔。
1. 輸入設定檔的名稱和說明。
1. 清除「最適化串流編碼&#x200B;]**」核取方塊。**[!UICONTROL 
1. 點選&#x200B;**[!UICONTROL 新增視訊編碼預設集]**。
1. 在&#x200B;**[!UICONTROL Basic]**&#x200B;標籤上，設定視訊和音訊選項。

   請點選每個選項旁的&#x200B;**[!UICONTROL 資訊]**&#x200B;圖示，以取得其他說明或根據選取的視訊格式codec建議的設定。

1. （可選）在&#x200B;**視訊大小**&#x200B;標題下，取消選中&#x200B;**[!UICONTROL 保留外觀比例]**。
1. 在&#x200B;**[!UICONTROL Width]**&#x200B;欄位中，輸入&#x200B;**[!UICONTROL auto]**;在&#x200B;**[!UICONTROL Height]**&#x200B;欄位的右側，點選&#x200B;**[!UICONTROL Information]**&#x200B;圖示。 使用&#x200B;**[!UICONTROL 大小計算器]**&#x200B;頁面進一步設定您想要的視訊維度（藍方塊）。 完成後，點選&#x200B;**[!UICONTROL X]**。
1. （選用）執行下列其中一項作業：

   * 點選&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤，並確認已選取&#x200B;**[!UICONTROL Use Default Values]**&#x200B;核取方塊（建議）。
   * 清除&#x200B;**[!UICONTROL 使用預設值]**&#x200B;核取方塊，並指定您想要的視訊設定和音訊設定。

      請點選每個選項旁的&#x200B;**[!UICONTROL 資訊]**&#x200B;圖示，以取得其他說明或根據選取的視訊格式codec建議的設定。

1. 在頁面的右上角，點選&#x200B;**[!UICONTROL Save]**&#x200B;以儲存預設集。
1. 執行下列任一操作：

   * 重複步驟5-10以建立其他編碼預設集。
   * 在頁面的右上角，點選「儲存 **** 」以儲存描述檔。

## 使用自訂新增的視訊編碼參數 {#using-custom-added-video-encoding-parameters}

您可以編輯現有的視訊編碼設定檔，以利用進階視訊編碼參數；當您在AEM中建立或編輯視訊設定檔時，無法在使用者介面中找到這些參數。 您可以自訂將一或多個進階參數（例如&#x200B;**[!UICONTROL minBitrate]**&#x200B;和&#x200B;**[!UICONTROL maxBitrate]**）新增至您現有的設定檔。

**若要使用自訂新增的視訊編碼參數**:

1. 點選AEM標誌，然後導覽至「工 **[!UICONTROL 具 >一 般 > CRXDE Lite]**」。
1. 從&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;頁面，在左側的&#x200B;**[!UICONTROL 瀏覽器]**&#x200B;面板中，導覽至下列內容：

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. 在頁面右下側的面板中，從&#x200B;**[!UICONTROL Properties]**&#x200B;標籤中，指定您要使用之參數的&#x200B;**[!UICONTROL Name]**、**[!UICONTROL Type]**&#x200B;和&#x200B;**[!UICONTROL Value]**。

   下列進階參數可供使用：

   <table> 
    <tbody> 
    <tr> 
    <td><strong>名稱</strong></td> 
    <td><strong>說明</strong><br /> </td> 
    <td><strong>類型</strong><br /> </td> 
    <td><strong>值</strong></td> 
    </tr> 
    <tr> 
    <td><code>h264Level</code></td> 
    <td>要用於編碼的H.264級。 這通常會根據您使用的編碼設定自動決定。</td> 
    <td><code>String</code></td> 
    <td><p>10 * h264</p> <p>例如3.0 = 30,1.3 = 13)</p> <p>無預設值。</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>關鍵幀之間的幀的目標數量。 計算此值以每2-10秒生成一個關鍵幀。 例如，在每秒30幀時，關鍵幀間隔應為60-300。<br /> <br /> 較低的關鍵幀間隔可改善最適化視頻編碼的流搜索和流切換行為，還可能改善具有大量運動的視頻的質量。但是，由於關鍵幀會增加檔案的大小，因此較低的關鍵幀間隔通常會導致以指定位元速率顯示的整體視頻質量較低。</td> 
    <td><code>String</code></td> 
    <td><p>正數。</p> <p>預設為300。</p> <p>HLS（HTTP即時串流）的建議值為60-90。</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>允許可變位元速率編碼的最小位元速率，單位為每秒千位元組數。</p> <p>只有當您建立或編輯視訊編碼設定檔時，在「進階」標籤中取消選取「使用常數位元速率」<strong>時，此參數才適用。</strong></p> <p>另請參閱<a href="/help/assets/video.md#bitrate">位元速率</a>。</p> </td> 
    <td><code>String</code></td> 
    <td><p>正數，以每秒位數為單位。</p> <p>無預設值。</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>允許可變位元速率編碼的最大位元速率（以每秒位元組數為單位）。</p> <p>只有當您建立或編輯視訊編碼設定檔時，在「進階」標籤中取消選取「使用常數位元速率」<strong>時，此參數才適用。</strong></p> <p>另請參閱<a href="/help/assets/video.md#bitrate">位元速率</a>。</p> </td> 
    <td><code>String</code></td> 
    <td><p>正數，以每秒位數為單位。</p> <p>無預設值。 不過，建議的值最多是編碼位元速率的兩倍。</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>將值設為<code>true</code>以強制音訊資料流的常數位元速率（如果音訊codec支援）。</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>預設值為<code>false</code>。</p> <p>HLS（HTTP即時串流）的建議值為<code>false</code>。</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. 在頁面的右下角附近，點選&#x200B;**[!UICONTROL Add]**。
1. 執行下列任一操作：

   * 重複步驟3和4，將其他參數新增至您的視訊編碼設定檔。
   * 在頁面的左上角附近，點選「**[!UICONTROL Save All]**」。

1. 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;頁面的左上角，點選&#x200B;**[!UICONTROL Back Home]**&#x200B;圖示以返回AEM。

### 編輯Dynamic Media視訊編碼設定檔 {#editing-a-video-encoding-profile}

您可以編輯已建立的任何視訊編碼設定檔，以新增、編輯或刪除該設定檔中的視訊預設集。

依預設，您無法編輯Dynamic Media隨附的預先定義且現成可用的&#x200B;**[!UICONTROL 適用性視訊編碼]**&#x200B;設定檔。 相反地，您可以輕鬆複製設定檔並以新名稱儲存。 然後，您可以在複製的設定檔中編輯所需的預設集。

另請參閱[視訊編碼最佳作法](video.md#best-practices-for-encoding-videos)。

若要定義其他資產類型的進階處理參數，請參閱[設定資產處理](config-dms7.md#configuring-asset-processing)。

**若要編輯Dynamic Media視訊編碼設定檔**:

1. 點選AEM標誌並導覽至「工 **[!UICONTROL 具 > 資產 >視 訊設定檔]**」。
1. 在&#x200B;**[!UICONTROL 視訊描述檔]**&#x200B;頁面上，檢查一個視訊描述檔名稱。
1. 在工具列上，點選&#x200B;**[!UICONTROL Edit]**。
1. 在&#x200B;**[!UICONTROL 視訊編碼設定檔]**&#x200B;頁面上，視需要編輯名稱和說明。
1. 最佳實務是，請確定已選取「 **[!UICONTROL 最適化串流編碼]** 」核取方塊。

   點選資訊圖示以取得最適化串流的說明。（如果您正在編輯漸進式視訊設定檔，請勿選取此核取方塊。）

1. 在&#x200B;**[!UICONTROL 視訊編碼預設集]**&#x200B;標題下，新增、編輯或刪除組成設定檔的視訊編碼預設集。

   點選&#x200B;**[!UICONTROL Basic]**&#x200B;和&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤上每個選項旁的&#x200B;**[!UICONTROL 資訊]**&#x200B;圖示，以取得其他說明或根據選取的視訊格式編解碼器建議的設定。

1. 在頁面的右上角，點選&#x200B;**[!UICONTROL Save]**。

### 複製Dynamic Media視訊編碼設定檔 {#copying-a-video-encoding-profile}

1. 點選AEM標誌並導覽至「工 **[!UICONTROL 具 > 資產 >視 訊設定檔]**」。
1. 在&#x200B;**[!UICONTROL 視訊描述檔]**&#x200B;頁面上，檢查一個視訊描述檔名稱。
1. 在工具列上，點選&#x200B;**[!UICONTROL Copy]**。
1. 在&#x200B;**[!UICONTROL 視訊編碼描述檔]**&#x200B;頁面上，輸入描述檔的新名稱。
1. 最佳實務是，請確定已選取「 **[!UICONTROL 最適化串流編碼]** 」核取方塊。點選資訊圖示以取得最適化串流的說明。 (如果您要複製漸進式視訊設定檔，請勿選取核取方塊。) 

   在Dynamic Media — 混合模式中，如果WebM視訊預設集是視訊設定檔的一部分，則無法進行最適化串流的&#x200B;**[!UICONTROL 編碼]**，因為所有預設集必須為MP4。
1. 在&#x200B;**[!UICONTROL 視訊編碼預設集]**&#x200B;標題下，新增、編輯或刪除組成設定檔的視訊編碼預設集。

   點選&#x200B;**[!UICONTROL Basic]**&#x200B;和&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤上每個選項旁的&#x200B;**[!UICONTROL 資訊]**&#x200B;圖示，以取得建議的設定和說明。

1. 在頁面的右上角，點選&#x200B;**[!UICONTROL Save]**。

### 刪除Dynamic Media視訊編碼設定檔 {#deleting-a-video-encoding-profile}

1. 點選AEM標誌並導覽至「工 **[!UICONTROL 具 > 資產 >視 訊設定檔]**」。
1. 在&#x200B;**[!UICONTROL 視訊描述檔]**&#x200B;頁面上，檢查一或多個視訊描述檔名稱。
1. 在工具列上，點選&#x200B;**[!UICONTROL Delete]**。
1. 點選&#x200B;**[!UICONTROL 確定]**。

## 將Dynamic Media視訊設定檔套用至資料夾 {#applying-a-video-profile-to-folders}

將視訊描述檔指派給資料夾時，任何子資料夾都會自動從其父資料夾繼承描述檔。 這表示您只能將一個視訊描述檔指派給資料夾。 因此，請仔細考慮上傳、儲存、使用和封存資產的資料夾結構。

如果您將不同的視訊描述檔指派給資料夾，新的描述檔會覆寫先前的描述檔。 先前的資料夾資產維持不變。 新設定檔會套用至稍後新增至資料夾的資產。

在用戶介面中，會以卡片名稱中顯示的設定檔名稱來表示已為其指派設定檔的資料夾。

![chlimage_1-517](assets/chlimage_1-517.png)

您可以將視訊設定檔套用至特定資料夾，或全域套用至所有資產。

### 將視訊設定檔套用至特定資料夾 {#applying-video-profiles-to-specific-folders}

您可以從「工具」菜單或在資料夾中從「屬性」將視頻配置檔案應 **[!UICONTROL 用到資料夾]******。本節說明如何以兩種方式將視訊描述檔套用至資料夾。

已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。

#### 從設定檔使用者介面將Dynamic Media視訊設定檔套用至資料夾 {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. 點選AEM標誌並導覽至「工 **[!UICONTROL 具 > 資產 >視 訊設定檔]**」。
1. 選取您要套用至資料夾或多個資料夾的視訊設定檔。
1. 點選 **[!UICONTROL 「將描述檔套用至檔案夾」]** ，然後選取您要用來接收新上傳資產的檔案夾或多個檔案夾，並點選「套 **[!UICONTROL 用」]**。已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。

#### 從屬性將Dynamic Media視訊設定檔套用至資料夾 {#applying-video-profiles-to-folders-from-properties}

1. 點選AEM標誌並導覽至&#x200B;**[!UICONTROL Assets]**，然後導覽至您要套用視訊描述檔的資料夾。
1. 在資料夾中，點選核取標籤以選取，然後點選&#x200B;**[!UICONTROL 屬性]**。
1. 選取&#x200B;**[!UICONTROL 視訊描述檔]**&#x200B;標籤，然後從下拉式選單中選取描述檔，然後點選&#x200B;**[!UICONTROL 儲存並關閉]**。 已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。

   ![chlimage_1-518](assets/chlimage_1-518.png)

### 全域套用Dynamic Media影片設定檔 {#applying-a-video-profile-globally}

除了將設定檔套用至資料夾之外，您也可以全域套用一個設定檔，讓任何資料夾中上傳至AEM資產的任何內容都會套用選取的設定檔。

**若要全域套用Dynamic Media影片設定檔**:

1. 導覽至CRXDE Lite至下列節點：`/content/dam/jcr:content`。
1. 新增屬性&#x200B;**[!UICONTROL videoProfile]**:`/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. 點選「**[!UICONTROL 儲存全部]**」。

![chlimage_1-519](assets/chlimage_1-519.png)

## 從資料夾移除Dynamic Media視訊設定檔 {#removing-a-video-profile-from-folders}

從資料夾移除視訊描述檔時，任何子資料夾都會自動從其父資料夾移除描述檔。 不過，資料夾內發生的檔案處理仍維持不變。

您可以從「工具」功能表內的資料夾或在資料夾內的「資料夾設定」中移除視訊描述檔 ********。本節說明如何以兩種方式從資料夾移除視訊描述檔。

### 透過設定檔使用者介面從資料夾移除Dynamic Media視訊設定檔 {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. 點選AEM標誌並導覽至「工 **[!UICONTROL 具 > 資產 >視 訊設定檔]**」。
1. 選取您要從資料夾或多個資料夾中移除的視訊設定檔。
1. 點選「**[!UICONTROL 從資料夾移除描述檔」]** ，然後選取您要用來從中移除描述檔的資料夾或多個資料夾，並點選「**[!UICONTROL 移除]**」。

   您可以確認視訊描述檔不再套用至資料夾，因為資料夾名稱下方不再顯示該名稱。

### 透過屬性從資料夾移除Dynamic Media視訊設定檔 {#removing-video-profiles-from-folders-via-properties}

1. 點選AEM標誌並導覽至&#x200B;**[!UICONTROL Assets]**，然後導覽至您要移除視訊描述檔的資料夾。
1. 在資料夾中，點選核取標籤以選取，然後點選&#x200B;**[!UICONTROL 屬性]**。
1. 選取「**[!UICONTROL 視訊描述檔]**」標籤，然後從下拉式選單中選取「**[!UICONTROL 無]**」，然後點選「**[!UICONTROL 儲存並關閉]**」。 已為其分配配置檔案的資料夾將通過資料夾名稱正下方的配置檔案名稱顯示來指示。
