---
title: AEM 6.4中的電子商務存放庫重新調整
seo-title: E-Commerce Repository Restructuring in AEM 6.4
description: 了解如何進行必要的變更，以移轉至AEM 6.4 for E-Commerce的新存放庫結構。
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for E-Commerce.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
feature: Upgrading
exl-id: 6adcc1a4-eb0f-4410-8219-dbd7e6bbe469
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 4%

---

# AEM 6.4中的電子商務存放庫重新調整{#e-commerce-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

如父項所述 [AEM 6.4中的存放庫重新調整架構](/help/sites-deploying/repository-restructuring.md) 頁面中，升級至AEM 6.4的客戶應使用此頁面評估與影響AEM電子商務解決方案的存放庫變更相關的工作量。 AEM 6.4升級程式中有些變更需要付出大量工作，有些則可延後至6.5升級。

## 使用6.4升級 {#with-upgrade}

### 產品、訂單、收集、分類、發運方法和付款方法資料 {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>重組指導</strong></td> 
   <td><p>您可以使用 <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">延遲移轉</a> 遷移電子商務資料的任務。</p> <p>它會執行下列步驟：</p> 
    <ul> 
     <li>調整對舊位置的引用以指向新位置</li> 
     <li>將內容從舊位置移動到新位置</li> 
     <li>刪除舊位置，最終激活整個系統中新位置的使用</li> 
    </ul> <p>任務涵蓋的位置包括：</p> 
    <ul> 
     <li>/etc/commerce/products</li> 
     <li>/etc/commerce/collections<br /> </li> 
     <li>/etc/commerce/orders<br /> </li> 
     <li>/etc/commerce/payment-methods<br /> </li> 
     <li>/etc/commerce/shipping-methods<br /> </li> 
    </ul> <p>對於較大的目錄，會借由將下列Java系統屬性傳遞至AEM，以個別執行商務移轉任務：</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>移轉AEM後需要重新啟動。</p> </td> 
  </tr>
  <tr>
   <td><strong>附註</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>
