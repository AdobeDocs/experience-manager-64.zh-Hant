---
title: 觸控式 UI 功能狀態
seo-title: Touch UI Feature Status
description: Adobe Experience Manager 6.3 Touch UI專屬的發行說明。
seo-description: Release notes specific to Adobe Experience Manager 6.3 Touch UI.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 15%

---

# 觸控式 UI 功能狀態 {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>若使用6.4版的AEM, [已棄用傳統UI](/help/release-notes/deprecated-removed-features.md). Adobe不打算對傳統UI進行進一步的增強，建議使用者運用觸控式UI提供的強大新功能。

從6.0版開始，AEM推出新的使用者介面，稱為「觸控式UI」（也稱為「觸控式UI」），其與Adobe Marketing Cloud和整體Adobe使用者介面准則相一致。 接近功能部分時，這便成為AEM中的標準UI，其舊版案頭導向介面稱為「傳統UI」。

雖然大部分的功能都存在於觸控式UI中，但有些功能尚未完整，且將會在未來版本中新增。

下列清單顯示AEM 6.4中實作之功能的目前狀態。

如需升級至AEM 6.4的客戶建議，請參閱 [適用於客戶的使用者介面Recommendations](/help/sites-deploying/ui-recommendations.md) 以取得詳細資訊。

>[!NOTE]
>
>請注意，本頁面僅涵蓋傳統UI的同等功能。
>
>傳統UI中未包含的觸控式UI新增和獨特的功能並未列出。

>[!NOTE]
>
>這份清單力求完整，但不應被視為詳盡無遺。

## 圖例 {#legend}

* **完成**:觸控式UI已完全提供此功能
* **多數**:此功能大多可在觸控式UI中使用。
* **遺失**:觸控式UI中不存在此功能，必須使用傳統UI執行此動作。
* **已更換**:功能已更換為運作方式不同的新實作。
* **已移除**:觸控式UI中已不存在此功能，且將不會取代。

## 功能狀態：網站管理員 {#feature-status-sites-admin}

這是傳統UI網站管理員( `/siteadmin`)在觸控式UI中具有和狀態( `/sites.html`)。

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
   <td>AEM 6.4導入 <a href="/help/sites-authoring/basic-handling.md#content-tree">內容樹視圖</a>.</td> 
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
   <td>建立新啟動</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>建立新LiveCopy <br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>建立資料夾</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>顯示發佈狀態</td> 
   <td>多數</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>搜尋</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>複製/貼上頁面（複製）</td> 
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
   <td>沒有復寫權限的發佈頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>稍後發佈</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>發佈樹</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消發佈頁面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消發佈頁面，不具有復寫權限</td> 
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
   <td>鎖定/解除鎖定</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>檢視/編輯屬性</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>在頁面上設定權限</td> 
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
   <td>還原樹並還原已刪除的頁</td> 
   <td>遺失</td> 
   <td>使用傳統UI。</td> 
  </tr>
  <tr>
   <td>顯示舊版和當前版本之間的差異<br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Livecopy動作（轉出）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>請參閱語言副本</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>尋找和取代</td> 
   <td>遺失<br /> </td> 
   <td>使用傳統UI。</td> 
  </tr>
  <tr>
   <td>通知收件匣（JCR事件）</td> 
   <td>遺失</td> 
   <td>使用傳統UI。 將取代為不同的實作。</td> 
  </tr>
  <tr>
   <td>引用</td> 
   <td>多數</td> 
   <td>2019年版AEM將新增傳入頁面連結的顯示。</td> 
  </tr>
 </tbody>
</table>

## 功能狀態：頁面編輯器 {#feature-status-page-editor}

這是傳統UI頁面編輯器( `/cf#`)具有且狀態為觸控式( `/editor.html`)。

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
   <td>編輯透過設計匯入工具匯入的內容<br /> </td> 
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
   <td>編輯Forms</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯選件</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>編輯工作流程模型<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>代碼：編輯和預覽</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>回應式預覽<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：編輯設計</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：支架</td> 
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
   <td>轉出頁面</td> 
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
   <td>多數</td> 
   <td>可在觸控式UI中完全存取。 傳統UI中仍會顯示多個工作流程裝載。<br /> </td> 
  </tr>
  <tr>
   <td>鎖定/解除鎖定頁面</td> 
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
   <td>使用網站管理員 <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">複製頁面</a>.<br /> </td> 
  </tr>
  <tr>
   <td>移動頁面</td> 
   <td>已移除</td> 
   <td>使用網站管理員 <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">移動頁面</a>.<br /> </td> 
  </tr>
  <tr>
   <td>刪除頁面</td> 
   <td>已移除</td> 
   <td>使用網站管理員 <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">刪除頁面</a>.<br /> </td> 
  </tr>
  <tr>
   <td>顯示偏好設定</td> 
   <td>已移除</td> 
   <td>使用網站管理員 <a href="/help/sites-authoring/author-environment-tools.md#references">請參閱詳細參考清單</a>.<br /> </td> 
  </tr>
  <tr>
   <td>稽核記錄</td> 
   <td>已移除</td> 
   <td>使用網站管理員和 <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">開啟活動邊欄</a>.<br /> </td> 
  </tr>
  <tr>
   <td>建立版本</td> 
   <td>已移除</td> 
   <td>使用網站管理員 <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">建立新版本</a>.<br /> </td> 
  </tr>
  <tr>
   <td>還原版本</td> 
   <td>已移除</td> 
   <td>使用網站管理員 <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">還原版本</a>.</td> 
  </tr>
  <tr>
   <td>交換機啟動</td> 
   <td>已移除</td> 
   <td>使用網站管理員 <a href="/help/sites-authoring/launches-promoting.md">切換啟動</a>.<br /> </td> 
  </tr>
  <tr>
   <td>翻譯頁面</td> 
   <td>已移除</td> 
   <td>使用網站管理員 <a href="/help/sites-administering/tc-manage.md">新增頁面至翻譯專案</a>.<br /> </td> 
  </tr>
  <tr>
   <td>時間扭曲（選擇日期/時間，並依看到的方式瀏覽網站）<br /> </td> 
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
   <td>已更換</td> 
   <td>使用 <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> UI之後。</td> 
  </tr>
  <tr>
   <td>各種媒體類型的內容尋找器<br /> </td> 
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
   <td>還原/取消復原</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>將內容拖放至元件預留位置</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>透過元件自動建立，將內容直接拖放至parsys預留位置<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 功能狀態：文字、表格和影像編輯器 {#feature-status-text-table-and-image-editors}

這是傳統UI文字、表格和影像編輯器所具備的功能清單，以及觸控式UI中的狀態。

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
   <td>就地、對話方塊和全螢幕皆可使用。</td> 
  </tr>
  <tr>
   <td>啟用/停用RTE外掛程式</td> 
   <td>完成<br /> </td> 
   <td>可使用 <a href="/help/sites-authoring/templates.md">範本編輯器</a>.</td> 
  </tr>
  <tr>
   <td>使用RTE進行純文字檔案</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：連結與錨點</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：字元圖</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：複製/貼上</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：從Microsoft Word貼上<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：查找和替換</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：文字格式（粗體、 ...）</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：子和上標</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：正文</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：清單（項目符號/數字）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：段落格式</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：文字樣式</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：原始碼編輯器(編輯HTML)<br /> </td> 
   <td>完成<br /> </td> 
   <td>僅限對話方塊和全螢幕使用。<br /> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：拼字檢查程式</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：表（嵌入式表編輯器）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：還原/重做<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE外掛程式：允許線上影像</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>表格編輯器</td> 
   <td>完成</td> 
   <td>就地、對話方塊和全螢幕皆可使用。<br /> </td> 
  </tr>
  <tr>
   <td>將影像拖放至表格儲存格<br /> </td> 
   <td>完成</td> 
   <td>可用線上</td> 
  </tr>
  <tr>
   <td>影像編輯器<br /> </td> 
   <td>完成</td> 
   <td>就地、對話方塊和全螢幕皆可使用。<br /> </td> 
  </tr>
  <tr>
   <td>啟用/禁用IPE插件</td> 
   <td>完成</td> 
   <td>現在， <a href="/help/sites-authoring/templates.md">範本編輯器</a>.</td> 
  </tr>
  <tr>
   <td>IPE插件：裁切</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：翻轉</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：還原/重做</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：影像圖</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：旋轉</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：縮放</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 功能狀態：工具 {#feature-status-tools}

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
   <td>已更換</td> 
   <td>6.0導入 <a href="/help/sites-authoring/projects.md">專案和工作</a>.<br /> </td> 
  </tr>
  <tr>
   <td>工作流程收件匣<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>頁面範本設定的工作流程(<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>遺失<br /> </td> 
   <td>使用傳統UI。</td> 
  </tr>
  <tr>
   <td>標籤管理員UI<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>MSM/Blueprint控制中心</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Blueprint管理器UI</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>轉出設定UI</td> 
   <td>遺失</td> 
   <td>使用傳統UI。</td> 
  </tr>
  <tr>
   <td>使用者、群組和權限UI<br /> </td> 
   <td>基本完成<br /> </td> 
   <td>若要進行進階權限編輯，請使用傳統UI。<br /> </td> 
  </tr>
  <tr>
   <td>清除版本(<code>/etc/versioning/purge.html</code>)</td> 
   <td>遺失</td> 
   <td>使用傳統UI。</td> 
  </tr>
  <tr>
   <td>外部連結檢查程式 (<code>/etc/linkchecker.html</code>)</td> 
   <td>遺失</td> 
   <td>使用傳統UI。<br /> </td> 
  </tr>
  <tr>
   <td>大量編輯器(<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>遺失<br /> </td> 
   <td>使用傳統UI。</td> 
  </tr>
 </tbody>
</table>
