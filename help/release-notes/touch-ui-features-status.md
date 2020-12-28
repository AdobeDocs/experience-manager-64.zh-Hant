---
title: Touch UI功能狀態
seo-title: Touch UI功能狀態
description: Adobe Experience Manager 6.3 Touch UI的發行說明。
seo-description: Adobe Experience Manager 6.3 Touch UI的發行說明。
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
translation-type: tm+mt
source-git-commit: db26dd05f6c0997eeda462f27971cbcfa6737527
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 13%

---


# 觸控式UI功能狀態{#touch-ui-feature-status}

>[!CAUTION]
>
>在AEM的6.4版中，[Classic UI已過時](/help/release-notes/deprecated-removed-features.md)。 Adobe不打算對Classic UI做進一步的增強，而且建議使用者運用觸控式UI下提供的強大新功能。

從6.0版開始，AEM推出新的使用者介面，稱為「觸控式UI」（也稱為「觸控式UI」），與Adobe Marketing Cloud及整體Adobe使用者介面准則一致。 幾乎已達到功能部分，這已成為AEM中的標準UI，其舊版案頭導向介面稱為「傳統UI」。

雖然大部份的功能都存在於觸控式使用者介面中，但有些功能尚未完整，將會在未來版本中新增。

下列清單顯示AEM 6.4中實作之功能的目前狀態。

如需升級至AEM 6.4的客戶建議，請參閱[客戶使用者介面建議](/help/sites-deploying/ui-recommendations.md)以取得詳細資訊。

>[!NOTE]
>
>請注意，本頁僅涵蓋與傳統UI的功能奇偶校驗。
>
>未列出傳統UI中未顯示的觸控式UI新增和獨特的功能。

>[!NOTE]
>
>這份清單力求完整，但不應視為詳盡無遺。

## 圖例 {#legend}

* **完整**:此功能可在觸控式UI中完全使用
* **主要**:此功能大部分可在觸控式UI中使用。
* **遺漏**:此功能不在觸控式使用者介面中，必須使用傳統使用者介面才能執行此動作。
* **已取代**:此功能已取代為運作不同的新實作。
* **已移除**:此功能不再存在於觸控式UI中，也不會被取代。

## 功能狀態：網站管理員{#feature-status-sites-admin}

這是傳統UI網站管理員(`/siteadmin`)擁有的功能清單，以及觸控式UI(`/sites.html`)的狀態。

<table> 
 <tbody>
  <tr>
   <td><strong>功能<br /> </strong></td> 
   <td><strong>狀態<br /> </strong></td> 
   <td><strong>評論</strong></td> 
  </tr>
  <tr>
   <td>導覽網站階層</td> 
   <td>完成<br /> </td> 
   <td>AEM 6.4推出<a href="/help/sites-authoring/basic-handling.md#content-tree">內容樹狀檢視</a>。</td> 
  </tr>
  <tr>
   <td>啟動工作流程</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>建立新頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>建立新網站</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>建立新的啟動</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>建立新的livecopy <br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>建立資料夾</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>顯示出版物狀態</td> 
   <td>大部分</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>搜尋</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>複製／貼上頁面（複製）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>移動頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>發佈頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>無複製權限的發佈頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>稍後發佈</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>發佈樹狀結構</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消發佈頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消發佈頁面，但無複製權限</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>稍後取消發佈</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>刪除</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>鎖定／解鎖</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>檢視／編輯屬性</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>設定頁面上的權限</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>版本記錄</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>還原版本</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>恢復樹狀結構和恢復已刪除的頁</td> 
   <td>遺失</td> 
   <td>使用Classic UI。</td> 
  </tr>
  <tr>
   <td>顯示舊版和當前版本的差異<br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>即時複製動作（推出）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>查看語言副本</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>尋找和取代</td> 
   <td>缺少<br /> </td> 
   <td>使用Classic UI。</td> 
  </tr>
  <tr>
   <td>通知收件匣（JCR事件）</td> 
   <td>遺失</td> 
   <td>使用Classic UI。 將會以不同的實作取代。</td> 
  </tr>
  <tr>
   <td>引用</td> 
   <td>大部分</td> 
   <td>AEM 2019版本將新增傳入頁面連結的顯示。</td> 
  </tr>
 </tbody>
</table>

## 功能狀態：頁面編輯器{#feature-status-page-editor}

這是傳統UI頁面編輯器(`/cf#`)擁有的功能清單，以及觸控式編輯器(`/editor.html`)的狀態。

<table> 
 <tbody>
  <tr>
   <td><strong>功能</strong></td> 
   <td><strong>狀態</strong></td> 
   <td><strong>評論</strong></td> 
  </tr>
  <tr>
   <td>編輯網頁</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯行動網頁<br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯透過Design Importer匯入的內容<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯電子郵件</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯行動應用程式</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯表單</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯選件</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯工作流模型<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>代碼：編輯與預覽</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>自適應預覽<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：編輯設計</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：腳手架</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：即時副本狀態<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>新增註解</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯屬性<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>展開頁面</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>開始和顯示工作流程</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>工作流包處理</td> 
   <td>大部分</td> 
   <td>可在觸控式UI中完全存取。 傳統UI中仍顯示多個工作流程裝載。<br /> </td> 
  </tr>
  <tr>
   <td>鎖定／解鎖頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>發佈頁面 <br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消發佈頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>複製頁面</td> 
   <td>已移除<br /> </td> 
   <td>使用網站管理員來複製頁面<a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page"></a>。<br /> </td> 
  </tr>
  <tr>
   <td>移動頁面</td> 
   <td>已移除</td> 
   <td>使用網站管理員移動頁面<a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">。<br /></a> </td> 
  </tr>
  <tr>
   <td>刪除頁面</td> 
   <td>已移除</td> 
   <td>使用網站管理員<a href="/help/sites-authoring/managing-pages.md#deleting-a-page">刪除頁面</a>。<br /> </td> 
  </tr>
  <tr>
   <td>顯示偏好設定</td> 
   <td>已移除</td> 
   <td>使用網站管理員<a href="/help/sites-authoring/author-environment-tools.md#references">查看詳細的參考清單</a>。<br /> </td> 
  </tr>
  <tr>
   <td>稽核記錄</td> 
   <td>已移除</td> 
   <td>使用網站管理員和<a href="/help/sites-authoring/author-environment-tools.md#events-timeline">開啟活動邊欄</a>。<br /> </td> 
  </tr>
  <tr>
   <td>建立版本</td> 
   <td>已移除</td> 
   <td>使用網站管理員建立新版本<a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">。<br /></a> </td> 
  </tr>
  <tr>
   <td>還原版本</td> 
   <td>已移除</td> 
   <td>使用站點管理器恢復版本<a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">。</a></td> 
  </tr>
  <tr>
   <td>交換機啟動</td> 
   <td>已移除</td> 
   <td>使用網站管理員在啟動</a>之間切換<a href="/help/sites-authoring/launches-promoting.md">。<br /> </a></td> 
  </tr>
  <tr>
   <td>翻譯頁面</td> 
   <td>已移除</td> 
   <td>使用站點管理員將頁面添加到翻譯項目</a>。<br /><a href="/help/sites-administering/tc-manage.md"> </a></td> 
  </tr>
  <tr>
   <td>時間彎曲（選擇日期／時間，然後瀏覽網站的外觀）<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>設定權限</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>用戶端內容UI<br /> </td> 
   <td>已取代</td> 
   <td>使用<a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> UI，繼續使用。</td> 
  </tr>
  <tr>
   <td>各種媒體類型的內容搜尋器<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>元件清單</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>複製並貼上元件<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>剪貼簿中的元件清單</td> 
   <td>遺失</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>還原／重做</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>將內容拖放至元件預留位置</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>使用元件自動建立功能將內容直接拖放至parsys預留位置<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 功能狀態：文字、表格和影像編輯器{#feature-status-text-table-and-image-editors}

這是傳統UI文字、表格和影像編輯器的功能清單，以及觸控式UI的狀態。

<table> 
 <tbody>
  <tr>
   <td><strong>功能</strong></td> 
   <td><strong>狀態 </strong></td> 
   <td><strong>評論<br /> </strong></td> 
  </tr>
  <tr>
   <td>RTF 編輯器</td> 
   <td>完成</td> 
   <td>可用於就地、對話和全螢幕。</td> 
  </tr>
  <tr>
   <td>啟用／禁用RTE插件</td> 
   <td>完成<br /> </td> 
   <td>可以使用<a href="/help/sites-authoring/templates.md">模板編輯器</a>完成。</td> 
  </tr>
  <tr>
   <td>對純文字檔案使用RTE</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：連結與錨點</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：字元地圖</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：複製／貼上</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：從Microsoft Word<br />貼上 </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：尋找和取代</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：文字格式（粗體， ...）</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：子標題和上標</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：對齊</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：清單（項目符號／數字）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：段落格式</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：文字樣式</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：原始碼編輯器（編輯HTML）<br /> </td> 
   <td>完成<br /> </td> 
   <td>僅在對話框和全屏中可用。<br /> </td> 
  </tr>
  <tr>
   <td>RTE插件：拼字檢查器</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：表（嵌入式表編輯器）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：還原／重做<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：允許串聯影像</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>表格編輯器</td> 
   <td>完成</td> 
   <td>可用於就地、對話和全螢幕。<br /> </td> 
  </tr>
  <tr>
   <td>將影像拖放至表格儲存格<br /> </td> 
   <td>完成</td> 
   <td>可用串聯</td> 
  </tr>
  <tr>
   <td>影像編輯器<br /> </td> 
   <td>完成</td> 
   <td>可用於就地、對話和全螢幕。<br /> </td> 
  </tr>
  <tr>
   <td>啟用／停用IPE增效模組</td> 
   <td>完成</td> 
   <td><a href="/help/sites-authoring/templates.md">範本編輯器</a>中現在有UI。</td> 
  </tr>
  <tr>
   <td>IPE外掛程式：裁切</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE外掛程式：翻轉</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE外掛程式：還原／重做</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE外掛程式：影像地圖</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE外掛程式：旋轉</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE外掛程式：縮放</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 功能狀態：工具{#feature-status-tools}

這是傳統UI擁有的各種工具清單，以及觸控式UI中的狀態。

<table> 
 <tbody>
  <tr>
   <td><strong>功能<br /> </strong></td> 
   <td><strong>狀態<br /> </strong></td> 
   <td><strong>評論</strong></td> 
  </tr>
  <tr>
   <td>任務管理</td> 
   <td>已取代</td> 
   <td>6.0推出<a href="/help/sites-authoring/projects.md">專案與工作</a>。<br /> </td> 
  </tr>
  <tr>
   <td>工作流收件箱<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>頁面範本設定工作流程(<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>缺少<br /> </td> 
   <td>使用Classic UI。</td> 
  </tr>
  <tr>
   <td>標籤管理員UI<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>MSM/Blueprint Control Center</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Blueprint Manager UI</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>推出設定UI</td> 
   <td>遺失</td> 
   <td>使用Classic UI。</td> 
  </tr>
  <tr>
   <td>使用者、群組與權限UI<br /> </td> 
   <td>主要完成<br /> </td> 
   <td>若要進行進階權限編輯，請使用Classic UI。<br /> </td> 
  </tr>
  <tr>
   <td>清除版本(<code>/etc/versioning/purge.html</code>)</td> 
   <td>遺失</td> 
   <td>使用Classic UI。</td> 
  </tr>
  <tr>
   <td>外部連結檢查程式 (<code>/etc/linkchecker.html</code>)</td> 
   <td>遺失</td> 
   <td>使用Classic UI。<br /> </td> 
  </tr>
  <tr>
   <td>批量編輯器(<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>缺少<br /> </td> 
   <td>使用Classic UI。</td> 
  </tr>
 </tbody>
</table>

