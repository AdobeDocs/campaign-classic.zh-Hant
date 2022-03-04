---
product: campaign
title: 「用例：建立內容管理
description: 「用例：建立內容管理
feature: Delivery Templates
exl-id: b0d1cf0e-656e-4d24-9a31-16fef4cd40d0
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 1%

---

# 用例：建立內容管理{#use-case-creating-content-management}

![](../../assets/common.svg)

要在Adobe Campaign建立內容管理，需要執行以下步驟：

* [步驟1 — 分析要生成的內容](#step-1---analyzing-the-content-to-be-produced)。
* [步驟2 — 建立資料架構](#step-2---creating-the-data-schema)。
* [步驟3 — 建立輸入表單](#step-3---creating-the-input-form)。
* [步驟4 — 建立構造模板](#step-4---creating-the-construction-template)。
* [步驟5 — 建立發佈模板](#step-5---creating-the-publication-template)。
* [步驟6 — 建立內容](#step-6---creating-contents)。

## 步驟1 — 分析要生成的內容 {#step-1---analyzing-the-content-to-be-produced}

在開始之前，您需要對要生成的內容進行精確分析：標識要顯示的元素，研究連結到這些元素的約束，為每個元素定義類型等。 還需要區分靜態元素和可變元素。

例如，要建立與以下類型內容HTML的新聞簡報：

![](assets/s_ncs_content_newsletter.png)

本新聞稿包含三種類型的要素：

1. 可變元素，其內容由用戶在交付建立期間通過輸入表單輸入或選擇。

   ![](assets/s_ncs_content_define_element_types.png)

1. 根據資料庫中保存的資訊（本例中是收件人的名字和姓氏）動態輸入的個性化欄位。

   ![](assets/s_ncs_content_define_dynamics.png)

1. 靜態元素，對於所有新聞稿都是相同的。

   ![](assets/s_ncs_content_define_statics.png)

本新聞稿的各個元素是根據JavaScript模板中定義的規則組合在一起的，該模板引用了要插入的所有元素並將其佈局概念化。

這些元素是通過專用架構建立的，該架構為每個內容指定以下元素：名稱、標籤、類型、大小，以及與其在Adobe Campaign的處理有關的任何其他資訊。

## 步驟2 — 建立資料架構 {#step-2---creating-the-data-schema}

資料模式是與內容關聯的XML文檔。 它描述了此內容中資料的XML結構。

>[!NOTE]
>
>有關在Adobe Campaign建立和配置資料架構的詳細資訊，請參閱 [此部分](../../configuration/using/about-schema-edition.md)。
>
>有關內容管理的特定配置元素的詳細資訊，請參見 [資料架構](data-schemas.md)。

要建立資料架構，請應用以下步驟：

1. 開啟Adobe Campaign瀏覽器，然後選擇 **[!UICONTROL Administration > Configuration > Data schemas]** 的下界。

   按一下 **[!UICONTROL New]** 表徵圖，位於資料架構清單的上方。

1. 選擇 **[!UICONTROL Create a schema]** 選項，然後按一下 **[!UICONTROL Next]**。

   ![](assets/s_ncs_content_create_schema.png)

1. 在相應欄位中輸入方案的名稱和標籤。 如有必要，可以添加說明並連結特定影像。

   ![](assets/s_ncs_content_param_schema.png)

   按一下 **[!UICONTROL Next]** 驗證。

1. 在 **[!UICONTROL Edit schema]** 的子菜單。

   使用 **[!UICONTROL Insert]** 按鈕以建立架構內容。

   ![](assets/s_ncs_content_param_schema_step2.png)

   有關此內容的詳細資訊，請參閱 [編輯架構](data-schemas.md#editing-schemas)。

   對於內容中引用的每個元素，需要選擇匹配類型。

   在本示例中，標識的內容、其格式和類型為：

<table> 
 <thead> 
  <tr> 
   <th> <strong>內容</strong> <br /> </th> 
   <th> <strong>格式</strong> <br /> </th> 
   <th> <strong>類型</strong> <br /> </th> 
   <th> <strong>標籤</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 標題<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 標題<br /> </td> 
  </tr> 
  <tr> 
   <td> 子標題<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 名稱<br /> </td> 
  </tr> 
  <tr> 
   <td> 事件日期<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> 導言段落<br /> </td> 
   <td> 元素<br /> </td> 
   <td> HTML<br /> </td> 
   <td> 概觀<br /> </td> 
  </tr> 
  <tr> 
   <td> 作者的照片<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 字串<br /> </td> 
   <td> URL<br /> </td> 
  </tr> 
  <tr> 
   <td> 作者<br /> </td> 
   <td> 元素<br /> </td> 
   <td> 備忘<br /> </td> 
   <td> 作者<br /> </td> 
  </tr> 
  <tr> 
   <td> 標題徽標(儲存在Adobe Campaign公共資源中)<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 連結<br /> </td> 
   <td> 影像<br /> </td> 
  </tr> 
 </tbody> 
</table>

架構將包含以下資訊：

```
<element label="Invitation" name="invitation" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    <attribute label="Title" length="40" name="title" type="string"/>
    <element label="Presentation" name="presentation" type="html"/>
    <attribute label="Date" name="date" type="date"/>
    <attribute label="Name" length="10" name="name" type="string"/>
    <attribute label="URL" name="url" type="string"/>
    <element label="Author" name="author" type="memo"/>
    <element label="Image" name="image" target="xtk:fileRes" type="link"/>
  </element>
```

1. 按一下 **[!UICONTROL Save]** 建立資料架構。

## 步驟3 — 建立輸入表單 {#step-3---creating-the-input-form}

通過輸入表單，您可以通過Adobe Campaign客戶端控制台的輸入介面編輯內容實例。

表單的描述是一種結構化XML文檔，它遵守「xtk:form」表單模式的語法。

>[!NOTE]
>
>有關在Adobe Campaign建立和配置表單的詳細資訊，請參閱 [此部分](../../configuration/using/identifying-a-form.md)。
>
>有關內容管理的特定配置元素的詳細資訊，請參見 [輸入表單](input-forms.md)。

要為內容管理建立輸入表單，請應用以下步驟：

1. 開啟Adobe Campaign瀏覽器，然後選擇 **[!UICONTROL Administration > Configuration > Input forms]** 的下界。

   按一下 **[!UICONTROL New]** 表徵圖

1. 輸入表單的名稱和連結到表單的標籤，然後選擇 **[!UICONTROL Content management]** 的雙曲餘切值。

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >要使兩個元素自動匹配，建議使用與連結資料架構相同的名稱。 使用 **[!UICONTROL Insert]** 按鈕，在輸入區域上方添加連結到窗體的架構中的欄位。

   ![](assets/s_ncs_content_param_form_edit_step2.png)

1. 在編輯器的中部，指定要在輸入表單中顯示的欄位。

   在本示例中，我們將提供以下類型的資訊：

   ```
    <input xpath="@title"/>
     <input xpath="@date"/>
     <input xpath="presentation"/>
     <input xpath="@name"/>
     <input xpath="@url"/>
     <input xpath="author"/>
     <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
       <sysFilter>
         <condition expr="@isImage = true"/>
       </sysFilter>
     </input>
   ```

   的 **[!UICONTROL Preview]** 頁籤中，您可以在編輯窗體時檢查其呈現：

   ![](assets/s_ncs_content_param_form_preview.png)

1. 按一下 **[!UICONTROL Save]** 的子菜單。

## 步驟4 — 建立構造模板 {#step-4---creating-the-construction-template}

使用XSLT語言，可以將XML文檔轉換為另一個輸出文檔。 此轉換在稱為樣式表的文檔中以XML進行描述。

在本示例中，我們希望使用JavaScript模板來定義生成的文檔中的資料構造和佈局模式。

>[!NOTE]
>
>連結到文檔構建（JavaScript或XSL模板）的約束在中詳細介紹 [格式](formatting.md)。

要在Adobe Campaign使用JavaScript模板，請應用以下步驟：

1. 開啟Adobe Campaign瀏覽器，然後選擇 **[!UICONTROL Administration > Configuration > JavaScript Templates]** 的下界。

   按一下 **[!UICONTROL New]** 表徵圖。

1. 輸入模板名稱並選擇為內容管理建立的架構。
1. 導入要在消息中顯示的設定內容。

   在遵守中詳細描述的語法時添加變數元素 [JavaScript模板](formatting.md#javascript-templates)。

   要顯示示例中顯示的內容，JavaScript模板必須包含以下元素：

   ```
   <html>
   <% eval(xtk.javascript.load("xac:perso").data); %>
   <head>
     <title>Invitation to an exceptional dedication session</title>
   </head>
   <body link="#0E59AE" vlink="#0E59AE" alink="#0E59AE" style="background-color:white;">
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-top: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td colspan="3">
             <%= generateImgTag(content.@["image-id"]) %>
           </td>
         </tr>
       </table>
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td>
             <table border="0" cellspacing="0" cellpadding="5">
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:2em; padding-bottom:2em;" width="730" align="middle">
                   <b>
                     <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:14px; color:#800080;">
                       <span style="FONT-VARIANT: small-caps"><%= content.@title %> - <%= content.@name %></span>
                     </font>
                   </b>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     Hello <%= perso('recipient.firstName') %> <%= perso('recipient.lastName') %>,
                     <p>
                       <%= content.presentation %>
                     </p>               
                     <center>
                       <b><%= formatDate(content.@date, "%2D %Bl %4Y") %></b> come to our Book Fair and meet our favorite authors and illustrators.<br>
                       <br>
                       <a href="https://www.site.web.com/registration" target="_blank"><b>REGISTER</b></a>
                     </center>
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                    <img style="float:left;margin-right:10px" border="0" src="<%= content.@url %>" width="70" height="70">
                     <b><%= content.author %></b>, will be signing their book between 2
   and 5:30PM.
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>            
                   <tr>
                 <td width="10"> </td>
                 <td width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">                  
                 </td>
                 <td width="10"> </td>
               </tr>           
               <tr>
                 <td width="10"> </td>
                 <td>
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     <center>
                       <p>
                         <a href="https://www.site.web.com/program" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Program</b></span></a>
                          | 
                         <a href="https://www.site.web.com/information" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Useful information</b></span></a>
                          | 
                       <a href="https://www.site.web.com/registration" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Register</b></span></a></p>
                       </center>
                     </font>
                   </td>
                   <td width="10"> </td>
                 </tr>
               </table>
               <br>
             </td>
           </tr>
         </table>
   </body>
   </html>
   ```

   在模板開始時調用函式，可以設定對從Adobe Campaign資料庫獲取的個性化資料的調用(在本例中：recipient.firstName和recipient.lastName)，以便在傳遞中使用時可以對其進行解釋。 有關此內容的詳細資訊，請參閱 [包括JavaScript模板](formatting.md#including-a-javascript-template)。

   在本示例中，函式將包含以下代碼：

   ```
   function perso(strPerso)
   {
     var strStart = '<' + '%' + '=';
     var strEnd = '%' + '>';
     return strStart + strPerso + strEnd;
   }
     function bloc(strPerso)
   {
     var strStart = '<' + '%' + '@ include view="';
     var strEnd = '" %' + '>';
     return strStart + strPerso + strEnd;
   }
   ```

   要使JavaScript模板有效，必須事先從 **[!UICONTROL JavaScript codes]** 樹結構中的節點，如下所示：

   ![](assets/contentmgt_jscode_perso_sample.png)

## 步驟5 — 建立發佈模板 {#step-5---creating-the-publication-template}

下一步包括建立內容發佈模板以連結架構、表單和內容構建模板。 此發佈模板可以有多種輸出格式。

>[!NOTE]
>
>有關內容發佈模板的詳細資訊，請參閱 [出版物模板](publication-templates.md)。

在本示例中，步驟如下：

1. 通過 **[!UICONTROL Administration > Configuration > Publication templates]** 的下界。
1. 輸入名稱和標籤，然後選擇要使用的方案和表單。
1. 然後輸入模板的名稱，然後選擇要應用的呈現模式。 這裡，我們有 **[!UICONTROL JavaScript]** 基於上面建立的模板鍵入rending。

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >的 **[!UICONTROL DOM interface]** 選項，這意味著如果使用E4X語法，則無法訪問此文檔。 選中此選項時必須使用DOM介面，並且是推薦的語法。
   >
   >您仍然可以使用E4X語法。 如果是，請確保取消選中此選項。

   使用 **[!UICONTROL Add]** 的子菜單。

1. 按一下 **[!UICONTROL Save]** 建立發佈模板。

## 步驟6 — 建立內容 {#step-6---creating-contents}

您現在可以基於此發佈模板建立內容。

>[!NOTE]
>
>有關建立內容的詳細資訊，請參閱 [使用內容模板](using-a-content-template.md)。

### 在傳遞嚮導中建立內容 {#creating-content-in-the-delivery-wizard}

要直接在交貨中建立內容，請應用以下步驟：

1. 從通過 **[!UICONTROL Advanced]** 的子菜單。

   ![](assets/s_ncs_content_in_delivery.png)

   在傳遞嚮導中添加一個附加頁籤，以便通過內容管理表單定義內容。

1. 輸入新聞稿的可變資訊。

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. 按一下 **[!UICONTROL HTML preview]** 頁籤 您需要選擇收件人以test個性化。

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
