---
title: 「使用案例：建立內容管理」
seo-title: 「使用案例：建立內容管理」
description: 「使用案例：建立內容管理」
seo-description: null
page-status-flag: never-activated
uuid: 204a63eb-40dd-446d-a847-4e55ad23b2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: a4c62580-664d-47fe-87f5-cfe608b05e6f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用案例：建立內容管理{#use-case-creating-content-management}

若要在Adobe Campaign中建立內容管理，必須執行下列步驟：

* [步驟1 —— 分析要製作的內容](#step-1---analyzing-the-content-to-be-produced),
* [步驟2 —— 建立資料架構](#step-2---creating-the-data-schema),
* [步驟3 —— 建立輸入表單](#step-3---creating-the-input-form),
* [步驟4 —— 建立構造模板](#step-4---creating-the-construction-template),
* [步驟5 —— 建立出版物模板](#step-5---creating-the-publication-template),
* [步驟6 —— 建立內容](#step-6---creating-contents)。

## 步驟1 —— 分析要製作的內容 {#step-1---analyzing-the-content-to-be-produced}

在開始之前，您必須對要製作的內容進行精確分析：確定要顯示的元素、研究與其連結的約束、為每個元素定義類型等。 您也需要區分靜態元素和變數元素。

例如，若要建立HTML格式的電子報，並包含下列內容類型：

![](assets/s_ncs_content_newsletter.png)

本電子報包含三種元素：

1. 變數元素，其內容由使用者在傳送建立期間透過輸入表單輸入或選取。

   ![](assets/s_ncs_content_define_element_types.png)

1. 根據儲存在資料庫中的資訊（此例中為收件者的名字和姓氏）動態輸入的個人化欄位。

   ![](assets/s_ncs_content_define_dynamics.png)

1. 靜態元素，所有電子報都相同。

   ![](assets/s_ncs_content_define_statics.png)

本電子報的各項元素會根據JavaScript範本中定義的規則加以組合，這些規則會參照所有要插入的元素並將其版面概念化。

這些元素是透過專用的架構建立的，該架構會為每個內容指定下列元素：名稱、標籤、類型、大小，以及任何其他與Adobe Campaign中其處理相關的資訊。

## 步驟2 —— 建立資料架構 {#step-2---creating-the-data-schema}

資料架構是與內容相關聯的XML檔案。 它描述了此內容中資料的XML結構。

>[!NOTE]
>
>如需在Adobe Campaign中建立和設定資料結構描述的詳細資訊，請參 [閱本節](../../configuration/using/about-schema-edition.md)。
>
>「資料」結構描述中詳細說明了內容管理 [的特定設定元素](../../delivery/using/data-schemas.md)。

要建立資料方案，請應用以下步驟：

1. 開啟「Adobe Campaign Explorer」並選取節 **[!UICONTROL Administration > Configuration > Data schemas]** 點。

   按一下 **[!UICONTROL New]** 資料結構清單上方的圖示。

1. 選取內容 **[!UICONTROL Create a schema]** 管理的選項，然後按一下 **[!UICONTROL Next]**。

   ![](assets/s_ncs_content_create_schema.png)

1. 在相應欄位中輸入方案的名稱和標籤。 您可以新增說明並視需要連結特定影像。

   ![](assets/s_ncs_content_param_schema.png)

   Click **[!UICONTROL Next]** to validate.

1. 在窗口中輸入方案的內 **[!UICONTROL Edit schema]** 容。

   使用按 **[!UICONTROL Insert]** 鈕可建立架構內容。

   ![](assets/s_ncs_content_param_schema_step2.png)

   For more on this, refer to [Editing schemas](../../delivery/using/data-schemas.md#editing-schemas).

   對於內容中引用的每個元素，您需要選擇一個匹配類型。

   在此示例中，標識的內容、其格式和類型為：

<table> 
 <thead> 
  <tr> 
   <th> <strong>內容</strong><br /> </th> 
   <th> <strong>格式</strong><br /> </th> 
   <th> <strong>類型</strong><br /> </th> 
   <th> <strong>標籤</strong><br /> </th> 
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
   <td> 標題標誌（儲存在Adobe Campaign公共資源中）<br /> </td> 
   <td> 屬性<br /> </td> 
   <td> 連結<br /> </td> 
   <td> Image<br /> </td> 
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

## 步驟3 —— 建立輸入表單 {#step-3---creating-the-input-form}

輸入表單可讓您透過Adobe Campaign用戶端主控台的輸入介面編輯內容例項。

表單的描述是一種結構化XML文檔，它觀察&quot;xtk:form&quot;表單模式的語法。

>[!NOTE]
>
>如需在Adobe Campaign中建立和設定表單的詳細資訊，請參 [閱本節](../../configuration/using/identifying-a-form.md)。
>
>內容管理專用的設定元素在輸入表單中 [有詳細說明](../../delivery/using/input-forms.md)。

若要建立內容管理的輸入表單，請套用下列步驟：

1. 開啟「Adobe Campaign Explorer」並選取節 **[!UICONTROL Administration > Configuration > Input forms]** 點。

   按一下 **[!UICONTROL New]** 表單清單上方的圖示。

1. 輸入表單的名稱和連結至表單的標籤，然後選取類 **[!UICONTROL Content management]** 型。

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >若要啟用兩個元素自動比對，建議使用與連結資料結構相同的名稱。 使用輸 **[!UICONTROL Insert]** 入區域上方的按鈕，從連結至表單的架構新增欄位。

   ![](assets/s_ncs_content_param_form_edit_step2.png)

1. 在編輯器的中間部分，指定要在輸入表單中顯示的欄位。

   在此範例中，我們將提供下列類型的資訊：

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

   此標 **[!UICONTROL Preview]** 簽可讓您在編輯表單時檢查表單的轉換：

   ![](assets/s_ncs_content_param_form_preview.png)

1. 按一 **[!UICONTROL Save]** 下以建立輸入表單。

## 步驟4 —— 建立構造模板 {#step-4---creating-the-construction-template}

XSLT語言可讓您將XML文檔轉換為另一個輸出文檔。 此轉換在稱為樣式表的文檔中的XML中描述。

在此範例中，我們想使用JavaScript範本來定義產生檔案中的資料建構和版面模式。

>[!NOTE]
>
>連結至檔案建立（JavaScript或XSL範本）的限制在格式設定中有詳 [細說明](../../delivery/using/formatting.md)。

若要在Adobe Campaign中使用JavaScript範本，請套用下列步驟：

1. 開啟「Adobe Campaign Explorer」並選取節 **[!UICONTROL Administration > Configuration > JavaScript Templates]** 點。

   按一下 **[!UICONTROL New]** 範本清單上方的圖示。

1. 輸入模板名稱並選擇為內容管理建立的方案。
1. 匯入您要在訊息中顯示的設定內容。

   新增變數元素，同時遵守 [JavaScript範本中詳述的語法](../../delivery/using/formatting.md#javascript-templates)。

   若要顯示範例中顯示的內容，JavaScript範本必須包含下列元素：

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

   在範本開始時呼叫函式可讓您設定對從Adobe Campaign資料庫擷取之個人化資料的呼叫(在此例中：recipient.firstName和recipient.lastName)，以便在傳送中使用時加以解譯。 如需詳細資訊，請參閱「 [包含JavaScript範本」](../../delivery/using/formatting.md#including-a-javascript-template)。

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

   為了讓JavaScript範本有效，必須事先從樹狀結構中的節點 **[!UICONTROL JavaScript codes]** 建立此函式，如下所示：

   ![](assets/contentmgt_jscode_perso_sample.png)

## 步驟5 —— 建立出版物模板 {#step-5---creating-the-publication-template}

下一步包括建立內容發佈模板以連結架構、表單和內容構建模板。 此發佈範本可以有幾種輸出格式。

>[!NOTE]
>
>有關內容出版物模板的詳細資訊，請參閱出版物 [模板](../../delivery/using/publication-templates.md)。

在此範例中，步驟如下：

1. 通過節點建立新的發佈 **[!UICONTROL Administration > Configuration > Publication templates]** 模板。
1. 輸入名稱和標籤，然後選擇要使用的方案和表單。
1. 然後輸入範本的名稱，並選擇要套用的演算模式。 在這裡，我們提供 **[!UICONTROL JavaScript]** 了基於上面建立的模板的類型轉換。

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >預 **[!UICONTROL DOM interface]** 設會勾選此選項，這表示如果您使用E4X語法，將無法存取此檔案。 勾選此選項時，必須使用DOM介面，且是建議的語法。
   >
   >您仍可使用E4X語法。 如果是，請確定取消勾選此選項。

   使用該 **[!UICONTROL Add]** 按鈕可建立其他轉換模板。

1. 按一 **[!UICONTROL Save]** 下以建立出版物範本。

## 步驟6 —— 建立內容 {#step-6---creating-contents}

您現在可以根據此出版物範本建立內容。

>[!NOTE]
>
>有關建立內容的詳細資訊，請參 [閱使用內容模板](../../delivery/using/using-a-content-template.md)。

### 在傳送精靈中建立內容 {#creating-content-in-the-delivery-wizard}

若要直接在傳送中建立內容，請套用下列步驟：

1. 首先，透過傳送屬性的標籤 **[!UICONTROL Advanced]** 來參考出版物範本。

   ![](assets/s_ncs_content_in_delivery.png)

   傳送精靈中會新增一個額外的標籤，以透過內容管理表單來定義內容。

1. 輸入電子報的變數資訊。

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. 按一下標 **[!UICONTROL HTML preview]** 簽以檢視演算。 您需要選擇收件者來測試個人化。

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
