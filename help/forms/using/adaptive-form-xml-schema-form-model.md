---
title: 使用XML結構建立最適化表單
seo-title: Creating adaptive forms using XML Schema
description: 適用性表單可以使用XML結構作為表單模型，讓您運用現有的XSD範本建立適用性表單。 您可以從XSD拖放架構元素至最適化表單。
seo-description: Adaptive forms can use XML schema as form model, allowing you to leverage existing XSD templates to create adaptive forms. You can drag-and-drop schema elements from XSD onto your adaptive form.
uuid: a5f5d423-9b83-47e8-b0fa-88210d0d18d9
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a1070d9e-fb7c-4134-b6d5-ffa2d3e9718d
feature: Adaptive Forms
exl-id: 5f6d23b2-ab8b-48fd-b853-eea7d6c9d651
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 3%

---

# 使用XML結構建立最適化表單 {#creating-adaptive-forms-using-xml-schema}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 必備條件 {#prerequisites}

使用XML架構作為表單模型來製作最適化表單，需要基本了解XML架構。 此外，建議在本文之前閱讀下列內容。

* [建立最適化表單](/help/forms/using/creating-adaptive-form.md)
* [XML架構](https://www.w3.org/TR/xmlschema-2/)

## 使用XML架構作為表單模型 {#using-an-xml-schema-as-form-model}

AEM Forms支援使用現有XML結構作為表單模型來建立最適化表單。 此XML架構表示組織中的後端系統產生或使用資料的結構。

使用XML架構的主要功能包括：

* XSD的結構在最適化表單的製作模式中，在「內容尋找器」索引標籤中會顯示為樹狀結構。 您可以將元素從XSD階層拖曳並新增至最適化表單。
* 您可以使用符合相關架構的XML預先填入表單。
* 提交時，用戶輸入的資料將以符合關聯架構的XML形式提交。

XML架構由簡單和複雜的元素類型組成。 元素具有將規則新增至元素的屬性。 將這些元素和屬性拖曳至最適化表單時，會自動對應至對應的最適化表單元件。

此XML元素與最適化表單元件的對應如下：

<table> 
 <tbody> 
  <tr> 
   <th><strong>XML元素或屬性 </strong></th> 
   <th><strong>最適化表單元件</strong></th> 
  </tr> 
  <tr> 
   <td><code>xs:string</code></td> 
   <td>文字方塊</td> 
  </tr> 
  <tr> 
   <td><code>xs:boolean</code></td> 
   <td>核取方塊</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li><code>xs:unsignedInt</code></li> 
     <li><code>xs:xs:int</code></li> 
     <li><code class="code">xs:decimal 
        </code></li> 
     <li>所有數值類型</li> 
    </ul> </td> 
   <td>數值方塊</td> 
  </tr> 
  <tr> 
   <td><code>xs:date</code></td> 
   <td>日期選擇器</td> 
  </tr> 
  <tr> 
   <td><code class="code">xs:enumeration
      </code></td> 
   <td>下拉式清單</td> 
  </tr> 
  <tr> 
   <td>任何複雜類型元素</td> 
   <td>面板</td> 
  </tr> 
 </tbody> 
</table>

## 範例XML架構 {#sample-xml-schema}

以下是XML架構的範例。

```xml
<?xml version="1.0" encoding="utf-8" ?> 
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>
        
        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartBirth" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails" 
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```

>[!NOTE]
>
>確保XML架構只有一個根元素。 不支援具有多個根元素的XML架構。

## 使用XML架構向欄位添加特殊屬性 {#adding-special-properties-to-fields-using-xml-schema}

您可以將下列屬性新增至XML結構元素，以將特殊屬性新增至相關適用性表單的欄位。

<table> 
 <tbody> 
  <tr> 
   <th><strong>結構屬性</strong></th> 
   <th><strong>在最適化表單中使用</strong></th> 
   <th><strong>支援 </strong></th> 
  </tr> 
  <tr> 
   <td><code>use=required </code></td> 
   <td>將欄位標示為必填欄位<br /> </td> 
   <td>屬性</td> 
  </tr> 
  <tr> 
   <td><code>default="default value"</code></td> 
   <td>新增預設值</td> 
   <td>元素和屬性</td> 
  </tr> 
  <tr> 
   <td><code>minOccurs="3"</code></td> 
   <td><p>指定最小發生次數</p> <p>(適用於可重複的子表單（複雜類型）)</p> </td> 
   <td>元素（複雜類型）</td> 
  </tr> 
  <tr> 
   <td><code class="code">maxOccurs="10"
      </code></td> 
   <td><p>指定最大發生次數</p> <p>(適用於可重複的子表單（複雜類型）)</p> </td> 
   <td>元素（複雜類型）</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>將結構元素拖曳至最適化表單時，會產生預設標題：
>
>* 大寫元素名稱的第一個字元
>* 在駝峰大小寫邊界插入空白字元。
>
>例如，若您新增 `userFirstName` 綱要元素，最適化表單中產生的註解為 `User First Name`.

## 限制最適化表單元件的可接受值 {#limit-acceptable-values-for-an-adaptive-form-component}

您可以將下列限制新增至XML架構元素，以限制最適化表單元件可接受的值：

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> 結構屬性</strong></p> </td> 
   <td><p><strong>資料類型</strong></p> </td> 
   <td><p><strong>說明</strong></p> </td> 
   <td><p><strong>Component</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><code>totalDigits</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定元件中允許的位數上限。 指定的位數必須大於零。</p> </td> 
   <td> 
    <ul> 
     <li>數值方塊</li> 
     <li>數值步進器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>maximum</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定數值和日期的上界。 預設會包含最大值。</p> </td> 
   <td> 
    <ul> 
     <li>數值方塊</li> 
     <li>數值步進器<br /> </li> 
     <li>日期挑選器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minimum</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定數值和日期的下限。 預設會包含最小值。</p> </td> 
   <td> 
    <ul> 
     <li>數值方塊</li> 
     <li>數值步進器</li> 
     <li>日期挑選器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMaximum</code></p> </td> 
   <td><p>布林值</p> </td> 
   <td><p>如果為true，則表單元件中指定的數值或日期必須小於為maximum屬性指定的數值或日期。</p> <p>如果為false，則表單元件中指定的數值或日期必須小於或等於為最大屬性指定的數值或日期。</p> </td> 
   <td> 
    <ul> 
     <li>數值方塊</li> 
     <li>數值步進器</li> 
     <li>日期挑選器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMinimum</code></p> </td> 
   <td><p>布林值</p> </td> 
   <td><p>如果為true，則表單元件中指定的數值或日期必須大於為最小屬性指定的數值或日期。</p> <p>如果為false，則表單元件中指定的數值或日期必須大於或等於為最小屬性指定的數值或日期。</p> </td> 
   <td> 
    <ul> 
     <li>數值方塊</li> 
     <li>數值步進器</li> 
     <li>日期挑選器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minLength</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定元件中允許的字元數量最小。 最小長度必須等於或大於零。</p> </td> 
   <td> 
    <ul> 
     <li>文字方塊</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>maxLength</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定元件中允許的字元數上限。 最大長度必須大於零。</p> </td> 
   <td> 
    <ul> 
     <li>文字方塊</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>length</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定元件中允許的字元數。 長度必須等於或大於零。</p> </td> 
   <td> 
    <ul> 
     <li>文字方塊</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>fractionDigits</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定元件中允許的最大小數位數。 fractionDigits必須等於或大於零。</p> </td> 
   <td> 
    <ul> 
     <li> 具有資料類型浮點數或小數的數值框</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>pattern</code></p> </td> 
   <td><p>字串</p> </td> 
   <td><p>指定字元的順序。 如果字元符合指定的模式，元件將接受字元。</p> <p>模式屬性映射到相應自適應表單元件的驗證模式。</p> </td> 
   <td> 
    <ul> 
     <li>對應至XSD架構的所有適用性表單元件 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 常見問題 {#frequently-asked-questions}

**如何知道樹中的哪個元素與哪個XML元素關聯？**

當您連按兩下「內容尋找器」中的元素時，快顯視窗會顯示欄位名稱和名為 `bindRef`. 此屬性會將樹元素映射到架構中的元素或屬性。

![XML架構元素的bindref欄位](assets/dblclick.png)

bindRef</code> 欄位顯示樹元素與架構中的元素或屬性之間的關聯。

>[!NOTE]
>
>屬性具有 `@` 符號 `bindRef`值來區分元素。 例如， `/config/projectDetails/@duration`.

**為什麼我無法為可重複的子表單拖曳子表單的個別元素（從任何複雜類型產生的結構）（minOccours或maxOccurs值大於1）?**

在可重複的子表單中，您必須使用完整的子表單。 如果您只想要選擇性欄位，請使用整個結構並刪除不需要的結構。

**我在「內容尋找器」中有一個長而複雜的結構。 如何尋找特定元素？**

您有兩個選項：

* 滾動瀏覽樹結構
* 使用「搜尋」方塊來尋找元素

**什麼是bindRef?**

A `bindRef` 是適用性表單元件與結構元素或屬性之間的連線。 這決定了 `XPath` 其中，從此元件或欄位捕獲的值在輸出XML中可用。 A `bindRef`從預填（預填）的XML預填欄位值時，也會使用。
