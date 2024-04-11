---
product: campaign
title: 「使用案例：建立內容管理」
description: 「使用案例：建立內容管理」
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Delivery Templates
exl-id: b0d1cf0e-656e-4d24-9a31-16fef4cd40d0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---

# 使用案例：建立內容管理{#use-case-creating-content-management}



若要在Adobe Campaign中建立內容管理，必須執行下列步驟：

* [步驟1 — 分析要產生的內容](#step-1---analyzing-the-content-to-be-produced)，
* [步驟2 — 建立資料結構](#step-2---creating-the-data-schema)，
* [步驟3 — 建立輸入表單](#step-3---creating-the-input-form)，
* [步驟4 — 建立建構範本](#step-4---creating-the-construction-template)，
* [步驟5 — 建立發佈範本](#step-5---creating-the-publication-template)，
* [步驟6 — 建立內容](#step-6---creating-contents).

## 步驟1 — 分析要產生的內容 {#step-1---analyzing-the-content-to-be-produced}

開始之前，您需要對要產生的內容進行精確分析：識別要顯示的元素、研究與其連結的限制、定義每個元素的型別等。 您也需要區分靜態元素和變數元素。

例如，若要建立具有以下內容型別的HTML電子報：

![](assets/s_ncs_content_newsletter.png)

此電子報包含三種型別的元素：

1. 變數元素，其內容可由使用者在建立傳遞期間透過輸入表單輸入或選取。

   ![](assets/s_ncs_content_define_element_types.png)

1. 根據資料庫中儲存的資訊（在此例中是收件者的名字和姓氏）動態輸入的個人化欄位。

   ![](assets/s_ncs_content_define_dynamics.png)

1. 靜態元素，所有電子報都相同。

   ![](assets/s_ncs_content_define_statics.png)

此Newsletter的各種元素會根據JavaScript範本中定義的規則組合在一起，該範本會參照所有要插入的元素並將其版面概念化。

這些元素是透過專用結構描述所建立，並為每個內容指定下列元素：名稱、標籤、型別、大小，以及與在Adobe Campaign中處理相關的任何其他資訊。

## 步驟2 — 建立資料結構 {#step-2---creating-the-data-schema}

資料結構描述是與內容相關聯的XML檔案。 它描述此內容中資料的XML結構。

>[!NOTE]
>
>如需在Adobe Campaign中建立和設定資料結構的詳細資訊，請參閱 [本節](../../configuration/using/about-schema-edition.md).
>
>有關內容管理特定的設定元素詳情，請參閱 [資料結構描述](data-schemas.md).

若要建立資料結構，請套用下列步驟：

1. 開啟Adobe Campaign Explorer並選取 **[!UICONTROL Administration > Configuration > Data schemas]** 節點。

   按一下 **[!UICONTROL New]** 圖示位於資料結構清單上方。

1. 選取 **[!UICONTROL Create a schema]** 內容管理的選項，然後按一下 **[!UICONTROL Next]**.

   ![](assets/s_ncs_content_create_schema.png)

1. 在適當的欄位中輸入結構描述的名稱和標籤。 您可以新增說明，並視需要連結特定影像。

   ![](assets/s_ncs_content_param_schema.png)

   按一下 **[!UICONTROL Next]** 以進行驗證。

1. 在中輸入結構描述的內容 **[!UICONTROL Edit schema]** 視窗。

   使用 **[!UICONTROL Insert]** 按鈕以建立結構描述內容。

   ![](assets/s_ncs_content_param_schema_step2.png)

   有關詳細資訊，請參閱 [編輯方案](data-schemas.md#editing-schemas).

   對於內容中參照的每個元素，您需要選取相符的型別。

   在此範例中，已識別的內容、格式和型別如下：

<table> 
 <thead> 
  <tr> 
   <th> <strong>內容</strong> <br /> </th> 
   <th> <strong>格式</strong> <br /> </th> 
   <th> <strong>型別</strong> <br /> </th> 
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
   <td> 簡介段落<br /> </td> 
   <td> 元素<br /> </td> 
   <td> HTML<br /> </td> 
   <td> 概觀<br /> </td> 
  </tr> 
  <tr> 
   <td> 作者的像片<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 字串<br /> </td> 
   <td> URL<br /> </td> 
  </tr> 
  <tr> 
   <td> 作者<br /> </td> 
   <td> 元素<br /> </td> 
   <td> 備忘錄<br /> </td> 
   <td> 作者<br /> </td> 
  </tr> 
  <tr> 
   <td> 頁首標誌(儲存在Adobe Campaign公共資源中)<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 連結<br /> </td> 
   <td> 影像<br /> </td> 
  </tr> 
 </tbody> 
</table>

結構描述將包含下列資訊：

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

1. 按一下 **[!UICONTROL Save]** 以建立資料結構描述。

## 步驟3 — 建立輸入表單 {#step-3---creating-the-input-form}

輸入表單可讓您透過Adobe Campaign使用者端主控台的輸入介面編輯內容執行個體。

表單的說明是結構化XML檔案，可遵循「xtk：form」表單結構描述的語法。

>[!NOTE]
>
>有關在Adobe Campaign中建立和設定表單的詳細資訊，請參閱 [本節](../../configuration/using/identifying-a-form.md).
>
>有關內容管理特定的設定元素詳情，請參閱 [輸入表單](input-forms.md).

若要建立內容管理的輸入表單，請套用下列步驟：

1. 開啟Adobe Campaign Explorer並選取 **[!UICONTROL Administration > Configuration > Input forms]** 節點。

   按一下 **[!UICONTROL New]** 圖示加以儲存。

1. 輸入表單的名稱和連結至表單的標籤，然後選取 **[!UICONTROL Content management]** 型別。

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >若要讓這兩個元素自動相符，我們建議使用與連結資料結構描述相同的名稱。 使用 **[!UICONTROL Insert]** 按鈕來新增連結至表單之結構描述中的欄位。

   ![](assets/s_ncs_content_param_form_edit_step2.png)

1. 在編輯器的中間，指定您要在輸入表單中顯示的欄位。

   在此範例中，我們將擁有下列資訊型別：

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

   此 **[!UICONTROL Preview]** 索引標籤可讓您在編輯表單時檢查表單的轉譯：

   ![](assets/s_ncs_content_param_form_preview.png)

1. 按一下 **[!UICONTROL Save]** 以建立輸入表單。

## 步驟4 — 建立建構範本 {#step-4---creating-the-construction-template}

XSLT語言可讓您將XML檔案轉換為另一個輸出檔案。 在稱為樣式表的檔案中，以XML描述此轉換。

在此範例中，我們想要使用JavaScript範本來定義產生檔案中的資料建構和版面配置模式。

>[!NOTE]
>
>連結至檔案建置（JavaScript或XSL範本）的限制詳述於 [格式化](formatting.md).

若要在Adobe Campaign中使用JavaScript範本，請套用下列步驟：

1. 開啟Adobe Campaign Explorer並選取 **[!UICONTROL Administration > Configuration > JavaScript Templates]** 節點。

   按一下 **[!UICONTROL New]** 圖示加以識別。

1. 輸入範本名稱，並選取您為內容管理建立的綱要。
1. 匯入您要在訊息中顯示的設定內容。

   新增變數元素，同時遵循中詳述的語法 [javascript範本](formatting.md#javascript-templates).

   若要顯示範例中所顯示的內容，JavaScript範本必須包含以下元素：

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

   在範本開始時呼叫函式，可讓您設定對從Adobe Campaign資料庫擷取的個人化資料的呼叫（在此案例中為：recipient.firstName和recipient.lastName），以便在用於傳遞時加以解譯。 有關詳細資訊，請參閱 [包含JavaScript範本](formatting.md#including-a-javascript-template).

   在此範例中，函式將包含下列程式碼：

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

   為了讓JavaScript範本有效，必須預先從 **[!UICONTROL JavaScript codes]** 樹狀結構中的節點，如下所示：

   ![](assets/contentmgt_jscode_perso_sample.png)

## 步驟5 — 建立發佈範本 {#step-5---creating-the-publication-template}

下一個步驟包括建立內容發佈範本，以連結架構、表單和內容建構範本。 此出版物範本可以有多種輸出格式。

>[!NOTE]
>
>有關內容發佈範本的詳細資訊，請參閱 [發佈範本](publication-templates.md).

在此範例中，步驟如下：

1. 透過建立新的出版物範本 **[!UICONTROL Administration > Configuration > Publication templates]** 節點。
1. 輸入名稱和標籤，然後選取要使用的結構描述和表單。
1. 然後輸入範本的名稱，並選擇要套用的演算模式。 在此，我們有 **[!UICONTROL JavaScript]** 根據上述建立的範本進行型別轉譯。

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >此 **[!UICONTROL DOM interface]** 選項預設為核取，這表示如果您使用E4X語法，將無法存取此檔案。 勾選此選項時，必須使用DOM介面，且這是建議的語法。
   >
   >您仍然可以使用E4X語法。 若是如此，請務必取消勾選此選項。

   使用 **[!UICONTROL Add]** 按鈕以建立其他轉換範本。

1. 按一下 **[!UICONTROL Save]** 以建立出版物範本。

## 步驟6 — 建立內容 {#step-6---creating-contents}

您現在可以根據此出版物範本建立內容。

>[!NOTE]
>
>有關建立內容的詳細資訊，請參閱 [使用內容範本](using-a-content-template.md).

### 在傳遞精靈中建立內容 {#creating-content-in-the-delivery-wizard}

若要直接在傳送中建立內容，請套用下列步驟：

1. 首先，請透過 **[!UICONTROL Advanced]** 傳遞屬性的索引標籤。

   ![](assets/s_ncs_content_in_delivery.png)

   傳遞精靈會新增一個額外索引標籤，以便透過內容管理表單定義內容。

1. 輸入Newsletter的變數資訊。

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. 按一下 **[!UICONTROL HTML preview]** 標籤以檢視轉譯。 您必須選取收件者以測試個人化。

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
