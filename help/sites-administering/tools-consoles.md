---
title: 工具主控台
description: 了解Adobe Experience Manager中各種不同的工具主控台。
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
exl-id: 7566e1bc-8571-4b3c-b420-4324026bd4dd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 19%

---

# 工具主控台{#tools-consoles}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

**「工具」**&#x200B;主控台可供存取多種特殊工具，協助您管理網站、數位資產和內容存放庫的其他方面。目前有兩種 **工具** 主控台取決於您使用的UI:

* [工具 — 傳統UI](#tools-classic-ui)
* [工具 — 觸控最佳化UI](#tools-touch-optimized-ui)

## 工具 — 傳統UI {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>頁面或資料夾</th> 
   <th> </th> 
   <th>用途</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM控制中心</a></td> 
   <td> </td> 
   <td>用於管理多個站點的集中點。</td> 
  </tr> 
  <tr> 
   <td>用戶端內容設定<br /> </td> 
   <td> </td> 
   <td>此 <a href="/help/sites-developing/client-context.md">用戶端內容</a> 代表動態組合的使用者資料集合。 預設和Marketing Cloud設定保留在此處。<br /> </td> 
  </tr> 
  <tr> 
   <td>Cloud Services配置<br /> </td> 
   <td> </td> 
   <td>保持與 <a href="/help/sites-administering/marketing-cloud.md">與Adobe Marketing Cloud整合</a>.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">商務</a></td> 
   <td> </td> 
   <td>提供匯入工具和各種產品資料的存取權。</td> 
  </tr> 
  <tr> 
   <td>DAM -Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>提供對數字版權資訊和許可證的訪問。</td> 
  </tr> 
  <tr> 
   <td>DAM — 健康情況檢查程式<br /> </td> 
   <td> </td> 
   <td>比較 <code>/var/dam</code> 和 <code>/content/dam</code> 和檢查<br /> 任何不一致之處。 然後，可以同步或刪除列出的任何檔案/資料夾。 資料夾比較的節點類型可在Web控制台中配置。</td> 
  </tr> 
  <tr> 
   <td>DAM -AdobeIndesign<br /> </td> 
   <td> </td> 
   <td>與AdobeIndesign搭配使用的指令碼。</td> 
  </tr> 
  <tr> 
   <td>DAM — 視訊設定檔<br /> </td> 
   <td> </td> 
   <td>用於ffmpeg轉碼的可配置配置檔案。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">控制面板</a></td> 
   <td> </td> 
   <td>可讓您建立報表控制面板；這些提供可自訂的方式來定義顯示統一資料的頁面。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">設計</a></td> 
   <td> </td> 
   <td>保留已定義的設計清單，包括要使用的圖形和css檔案。</td> 
  </tr> 
  <tr> 
   <td>自訂檔案</td> 
   <td> </td> 
   <td>用於擴充說明檔案和線上說明。</td> 
  </tr> 
  <tr> 
   <td>表單提交</td> 
   <td> </td> 
   <td>保留收到的表單提交清單。</td> 
  </tr> 
  <tr> 
   <td>匯入工具 —  <a href="/help/sites-administering/bulk-editor.md">大量編輯器</a></td> 
   <td> </td> 
   <td>可讓您搜尋項目並大量編輯。 您也可以將內容（大量）匯出並匯入存放庫。</td> 
  </tr>
  <tr> 
   <td>匯入工具 — 摘要匯入工具</td> 
   <td> </td> 
   <td><p>摘要匯入工具是一個架構，可從外部來源重複匯入內容至您的存放庫。 摘要匯入工具的構想是以指定的間隔輪詢遠端資源、進行剖析，以及在內容存放庫中建立代表遠端資源內容的節點。</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">外部連結檢查程式</a></td> 
   <td> </td> 
   <td>掃描AEM例項內的所有內容頁面，並檢查任何外部連結。 隨即顯示有效和無效連結的清單。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">行動</a></td> 
   <td> </td> 
   <td>協助您建立為行動裝置設計的網站。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>處理多語言和跨國內容，協助您在集中品牌與本地化內容之間取得平衡。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">通知</a></td> 
   <td> </td> 
   <td>通知範本。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">套件</a></td> 
   <td> </td> 
   <td>套件管理器的替代連結，可顯示已為AEM WCM載入的套件。 類似於CRX的套件管理器中顯示的資訊。</td> 
  </tr> 
  <tr> 
   <td>復寫 —  <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">復寫代理</a></td> 
   <td> </td> 
   <td>用於在發佈頁面時將資料從作者複製到發佈，或透過反向復寫將使用者評論從發佈環境傳回給作者。</td> 
  </tr> 
  <tr> 
   <td>匯入工具 —  <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">激活樹</a></td> 
   <td> </td> 
   <td>從「網站」標籤，您可以啟動個別頁面。 當您輸入或更新相當多的內容頁面時（所有頁面都位於相同的根頁面下），在一個動作中啟動整個樹狀結構會較為容易。 您也可以執行「乾式執行」來模擬啟動，並反白顯示要啟動的頁面。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">報告</a></td> 
   <td> </td> 
   <td>AEM提供一系列自訂報表，可讓您建立自訂報表及/或開發您自己的報表。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">預設頁面支架</a></td> 
   <td> </td> 
   <td>透過支架，您可以建立表單（支架），其欄位可反映您想要的頁面結構，然後使用此表單根據此結構輕鬆建立頁面。</td> 
  </tr> 
  <tr> 
   <td>安全性 —  <a href="/help/sites-administering/notification.md">自助服務配置 </a> </td> 
   <td> </td> 
   <td>可讓您設定使用者在建立帳戶或重設密碼時，自動收到的電子郵件，以及確認已重設的密碼。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">Segmentation</a></td> 
   <td> </td> 
   <td>網站訪客來到網站時，其興趣和目標不同。 了解這些目標並滿足期望是線上行銷的重要成功因素。 分段透過分析訪客的詳細資料並加以特徵化，有助於達成此目標。<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>預設SRP配置。 請參閱 <a href="/help/communities/srp-config.md">儲存配置</a> 控制台。</td> 
  </tr> 
  <tr> 
   <td>任務管理</td> 
   <td> </td> 
   <td>沒有與此條目相關的活動功能。</td> 
  </tr> 
  <tr> 
   <td>租戶</td> 
   <td> </td> 
   <td>沒有與此條目相關的活動功能。</td> 
  </tr> 
  <tr> 
   <td>版本設定 —  <a href="/help/sites-deploying/version-purging.md">清除版本</a></td> 
   <td> </td> 
   <td>可讓您視需要清除頁面版本。</td> 
  </tr> 
  <tr> 
   <td>虛擬儲存庫</td> 
   <td> </td> 
   <td>您可以使用工作區裝載功能來設定虛擬存放庫，以便為啟用JCR的內容應用程式提供基於CRX和JCR連接器的JCR內容基礎架構的簡化存取。</td> 
  </tr> 
  <tr> 
   <td>觀看詞</td> 
   <td> </td> 
   <td>已棄用. 請參閱 <a href="/help/communities/moderate-ugc.md#watchwords">調節社群內容</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">工作流程</a></td> 
   <td> </td> 
   <td>工作流程可控制支援任何編輯程式的頁面或數位資產上的一系列動作。</td> 
  </tr> 
 </tbody> 
</table>

## 工具 — 觸控最佳化UI {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>章節</th> 
   <th>選項</th> 
   <th>用途</th> 
  </tr> 
  <tr> 
   <td>編寫</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-classic-ui-authoring/classic-personalization-campaigns.md">行銷活動</a></td> 
   <td>管理您的行銷活動。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/launches.md">Launch</a></td> 
   <td>管理您的行銷啟動項。</td> 
  </tr> 
  <tr> 
   <td>任務</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/task-content.md">收件匣</a></td> 
   <td>管理您的收件匣項目。</td> 
  </tr> 
  <tr> 
   <td>運作</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/security.md">使用者和群組</a></td> 
   <td>管理使用者和群組。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/tags.md">標記管理</a></td> 
   <td>組織您的標記及其命名空間。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">雲端服務</a></td> 
   <td>連線到 Adobe Marketing Cloud.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/workflows.md">工作流程</a></td> 
   <td>模型和管理工作流程.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">複製</a></td> 
   <td>建立並管理多個網站。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/reporting.md">報告</a></td> 
   <td>建立和監測自訂報表.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/hobbes.md">測試</a></td> 
   <td>執行為應用程式定義的測試.</td> 
  </tr> 
  <tr> 
   <td>Granite 操作</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE Lite</a></td> 
   <td>使用 Web 型 IDE 開發應用程式.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md">套件</a></td> 
   <td>封裝和共用應用程式.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md#package-share">套件共用</a></td> 
   <td>從 Adobe 及社群下載應用程式.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md#administering-topologies">拓樸瀏覽器</a></td> 
   <td>檢視例項拓樸.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md">正在卸載瀏覽器</a></td> 
   <td>管理卸載。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#backups">備份</a></td> 
   <td>執行備份任務.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Web 主控台<br /> </td> 
   <td>設定和管理應用程式平台.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Web 控制台設定傾印<br /> </td> 
   <td>從Web控制台下載配置狀態。<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>使用者</td> 
   <td>管理使用者.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>群組</td> 
   <td>管理群組.</td> 
  </tr> 
  <tr> 
   <td>外部資源<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>文件</td> 
   <td>檢視 Web Experience Management 文件.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>開發人員資源</td> 
   <td>開發人員資源和下載.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>上述部分選項實際上會連結至傳統UI。
