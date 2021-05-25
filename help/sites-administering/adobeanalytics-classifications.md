---
title: Adobe分類
seo-title: Adobe分類
description: 了解Adobe分類。
seo-description: 了解Adobe分類。
uuid: 57fb59f4-da90-4fe7-a5b1-c3bd51159a16
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6787511a-2ce0-421a-bcfb-90d5f32ad35e
exl-id: 25e58c68-5c67-4894-9a54-1717d90d7831
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 6%

---

# Adobe分類{#adobe-classifications}

Adobe分類會以排程方式將分類資料匯出至[Adobe Analytics](/help/sites-administering/adobeanalytics.md)。 導出器是&#x200B;**com.adobe.cq.scheduled.exporter.Exporter**&#x200B;的實現。

若要設定：

1. 透過&#x200B;**工具， Cloudservices**&#x200B;導覽至&#x200B;**Adobe Analytics**&#x200B;區段。
1. 新增設定。 您會看到&#x200B;**Adobe Analytics分類**&#x200B;設定範本顯示在&#x200B;**Adobe Analytics架構**&#x200B;設定下方。 視需要提供&#x200B;**Title**&#x200B;和&#x200B;**Name**:

   ![aa-25](assets/aa-25.png)

1. 按一下&#x200B;**建立**&#x200B;以配置設定。

   ![chlimage_1](assets/chlimage_1.png)

   屬性包括下列項目：

   | **欄位** | **說明** |
   |---|---|
   | 已啟用 | 選取&#x200B;**Yes**&#x200B;以啟用Adobe分類設定。 |
   | 發生衝突時覆寫 | 選擇&#x200B;**Yes**&#x200B;以覆蓋任何資料衝突。 預設情況下，此值設為&#x200B;**No**。 |
   | 刪除已處理的項目 | 如果設為&#x200B;**Yes**，則在導出已處理的節點後將其刪除。 預設值為&#x200B;**False**。 |
   | 匯出工作說明 | 輸入Adobe分類作業的說明。 |
   | 通知電子郵件 | 輸入Adobe分類通知的電子郵件地址。 |
   | 報表套裝 | 輸入報表套裝以執行的匯入作業。 |
   | 資料集 | 輸入要為其運行導入作業的資料集關係ID。 |
   | 轉換程式 | 從下拉式選單中選取變壓器實施。 |
   | 資料來源 | 導覽至資料容器的路徑。 |
   | 匯出排程 | 選取匯出排程。 預設為每30分鐘。 |

1. 按一下&#x200B;**OK**&#x200B;以儲存設定。

## 修改頁面大小{#modifying-page-size}

記錄會在頁面中處理。 依預設，「Adobe分類」會建立頁面大小為1000的頁面。

Adobe分類中每個定義的頁面大小最25000，可從Felix主控台修改。 在匯出期間，「Adobe分類」會鎖定來源節點，以防止同時修改。 導出後、出錯時或會話關閉時，該節點處於解鎖狀態。

若要變更頁面大小：

1. 導覽至&#x200B;**https://&lt;host>:&lt;port>/system/console/configMgr**&#x200B;的OSGI主控台，然後選取&#x200B;**AdobeAEM分類匯出器**。

   ![aa-26](assets/aa-26.png)

1. 視需要更新&#x200B;**匯出頁面大小**，然後按一下&#x200B;**儲存**。

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe分類先前稱為SAINT匯出工具。

出口商可以使用變壓器將出口資料轉換為特定格式。 針對Adobe分類，已提供實作轉換器介面的子介面`SAINTTransformer<String[]>`。 此介面用於將資料類型限制為`String[]`(SAINTAPI使用)，並具有標籤介面以查找要選擇的此類服務。

在預設實施SAINTDefaultTransformer中，導出源的子資源被視為具有屬性名稱作為鍵的記錄，而屬性值作為值。 系統會自動將&#x200B;**Key**&#x200B;欄新增為第一欄 — 其值將是節點名稱。 不考慮名稱節奏的屬性（包含：）。

*節點結構：*

* id-classification `nt:unstructured`

   * 1 `nt:unstructured`

      * Product =我的產品名稱（字串）
      * 價格= 120.90（字串）
      * 大小= M（字串）
      * 顏色=黑色（字串）
      * Color^Code = 101（字串）

**SAINT標題和記錄：**

| **關鍵** | **產品** | **價格** | **大小** | **彩色** | **Color^Code** |
|---|---|---|---|---|---|
| 1 | 我的產品名稱 | 120.90 | M | black | 101 |

屬性包括下列項目：

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性路徑</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>變壓器</td> 
   <td>SAINTransfer實施的類名</td> 
  </tr> 
  <tr> 
   <td>電子郵件</td> 
   <td>通知電子郵件地址。</td> 
  </tr> 
  <tr> 
   <td>報表套裝</td> 
   <td>報表套裝ID，用於執行匯入作業。 </td> 
  </tr> 
  <tr> 
   <td>資料集</td> 
   <td>要為運行導入作業的資料集關係ID。 </td> 
  </tr> 
  <tr> 
   <td>說明</td> 
   <td>工作說明。<br /> </td> 
  </tr> 
  <tr> 
   <td>覆寫</td> 
   <td>覆寫資料衝突的標幟。 預設值為<strong>false</strong>。</td> 
  </tr> 
  <tr> 
   <td>分支</td> 
   <td>此旗標可檢查報表套裝的相容性。 預設值為<strong>true</strong>。</td> 
  </tr> 
  <tr> 
   <td>deleteprocessed</td> 
   <td>用於在導出後刪除已處理節點的標籤。 預設值為<strong>false</strong>。</td> 
  </tr> 
 </tbody> 
</table>

## 自動Adobe分類匯出{#automating-adobe-classifications-export}

您可以建立自己的工作流程，讓任何新匯入都會啟動工作流程，以在&#x200B;**/var/export/**&#x200B;中建立適當且結構正確的資料，以便匯出至Adobe分類。
