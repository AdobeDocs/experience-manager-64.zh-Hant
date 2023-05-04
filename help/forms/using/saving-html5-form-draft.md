---
title: 將HTML5表單儲存為草稿
seo-title: Saving an HTML5 form as a draft
description: 將HTML5表單儲存為草稿，並在稍後階段繼續填寫表單。
seo-description: Save an HTML5 form as a draft and resume filling the form at a later stage.
uuid: 70cd5f6f-f125-470c-8cee-ee14d2127713
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: Mobile Forms
exl-id: 8e4ffda9-ea92-4abc-8746-5d1852e4599b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 6%

---

# 將HTML5表單儲存為草稿 {#saving-an-html-form-as-a-draft}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以將HTML5表單儲存為草稿，並在稍後階段繼續填寫表單。 Forms Portal可讓任何使用者儲存及還原HTML5表單。 若要啟用「另存為草稿」功能，請將下列設定新增至設定檔節點：

## 自訂設定檔以允許另存為草稿功能 {#custom-profile-to-allow-save-as-draft-feature}

立即可用，AEM Forms提供 **另存為草稿** 設定檔。 您可以使用「另存為草稿」配置檔案來呈現表單，以啟用HTML5表單的草稿功能。 您可以在 [Forms經理](/help/forms/using/introduction-managing-forms.md).

若要為您現有的 [自訂設定檔](/help/forms/using/custom-profile.md)，將下列屬性新增至您的自訂設定檔節點：

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性名稱</strong></td> 
   <td><strong>類型</strong></td> 
   <td><strong>值</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>mfAllowFPDraft</td> 
   <td>字串</td> 
   <td>true</td> 
   <td><p>啟用另存為拔模特徵</p> <p>此設定檔。</p> </td> 
  </tr> 
  <tr> 
   <td>mfAllowAttachments</td> 
   <td>字串</td> 
   <td>true</td> 
   <td><p>允許上傳附件</p> <p>和此設定檔。</p> </td> 
  </tr> 
 </tbody> 
</table>

## 草稿儲存和清單 {#drafts-storage-and-listing}

啟用表單的「另存為草稿」功能後；表單儲存時，會列於 [草稿和提交元件](/help/forms/using/draft-submission-component.md). 您可以從草稿和提交元件擷取並開始填寫已儲存的表單。

若要啟用草稿和提交元件的表單清單，請將下列屬性新增至設定檔節點：

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性名稱</strong></td> 
   <td><strong>類型</strong></td> 
   <td><strong>值</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>fp.enablePortalSubmit</td> 
   <td>字串</td> 
   <td>true</td> 
   <td>啟用要在<br /> Forms Portal Drafts &amp; Submissions元件提交後</td> 
  </tr> 
 </tbody> 
</table>

依預設，AEM Forms會將與表單草稿和提交相關的使用者資料儲存在Publish執行個體的/content/forms/fp節點中。 如需詳細資訊，請參閱 [草稿和提交元件的自訂儲存空間](/help/forms/using/adding-custom-storage-provider-forms.md).
