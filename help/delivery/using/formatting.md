---
product: campaign
title: 格式
description: 格式
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Email Design
role: User, Developer, Data Engineer
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# 格式{#formatting}

## JavaScript 範本 {#javascript-templates}

JavaScript範本是包含JavaScript程式碼的HTML或文字檔案。 其建構方式與傳遞動作中的電子郵件內容相同。

### JavaScript範本的識別 {#identification-of-a-javascript-template}

JavaScript範本可由其名稱和名稱空間識別，就如結構描述和表單一樣。 但是，建議將&#x200B;**.js**&#x200B;選項新增至範本名稱。

### JavaScript範本的結構 {#structure-of-a-javascript-template}

根據「cus：book」結構描述的JavaScriptHTML格式範本範例：

```
<html>
  <body>
    <!-- Title of book -->
    <h1><%= content.@name %></h1>
    <ul>
      <% for each(var chapter in content.chapter) { %>
        <li><%= chapter.@name %></li>
      <% }%>
    </ul>
  </body>
</html>
```

各種JavaScript指示詞會以下列形式顯示：

* 合併欄位：以&#x200B;**`<%= <source> %>`**&#x200B;語法顯示資料的內容，其中`<source>`是要顯示資料的來源欄位。
* 指示區塊：執行&lt;%和%>標籤之間包含的一系列JavaScript指示。

**content**&#x200B;物件代表輸入XML檔案的主要專案。

在我們的範例中，下列一行會顯示名稱簿名稱的內容：

```
<h1><%= content.@name %></h1>
```

下列程式碼會在`<chapter>`集合專案上反複執行：

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

內容的屬性和元素以JavaScript物件表示，並遵循來原始檔的結構。

**範例**：

* **內容。@name**：擷取主要專案的「name」屬性值
* **內容。@`['name']`**：與&#x200B;**內容相同。@name**&#x200B;語法
* **content.chapter.length**：傳回`<chapter`集合專案上的專案數
* **content.chapter`[0]`。@name**：擷取第一個`<chapter>`專案的名稱
* **chapter.name()**：傳回`<chapter>`專案的名稱
* **chapter.parent()。name()**：傳回`<chapter>`的父專案名稱

>[!CAUTION]
>
>因為&#39;-&#39;字元保留在JavaScript語言中，所以必須透過`['<field>']`語法復原包含此字元的任何屬性或元素的值。
>
>例如： `content.@['offer-id']`。

程式語言的所有功能（變數、回圈、條件測試、函式等） )可用來建構輸出檔案。 可存取SOAP API以擴充輸出檔案。

範例：

* 條件式測試：

  ```
  <% if (content.@number == 1 || content.@language == 'en') { %>
  <!-- Content to be displayed if test is true--> 
  <% } %>
  ```

* 函式呼叫：

  ```
  <!-- Displays a horizontal bar -->
  ;<% function DisplayHorizontalBar() { %>
    <hr/>
  <% } %> 
  
  <!-- The same function in a block  -->
  <% 
  function DisplayHorizontalBar2()
  {
    document.write('<hr/>');
  }
  %> 
  
  <!-- Returns the value in uppercase -->
  <% 
  function formatName(value)
  { 
    return value.toUpperCase(); 
  }
  %>
  
  <!-- Call functions -->
  <%= DisplayHorizontalBar1() %>
  <%= DisplayHorizontalBar2() %>
  <%= formatName(content.@name) %>
  ```

* 宣告和變數呼叫：

  ```
  <%  var counter = 0; %>
  
  <%= counter += 10 %>
  ```

* 使用靜態方法擷取及顯示收件者名稱：

  ```
  <% var recipient = nms.recipient.get(1246); %>
  <%= recipient.lastName %>
  ```

* 使用非靜態方法復原及顯示收件者名稱：

  ```
  <% var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr="@id=1246"/>
      </where>
    </queryDef>);
  
    var recipient = query.ExecuteQuery();
  %>
  
  <%= recipient.@lastName %>
  ```

### 包含JavaScript範本 {#including-a-javascript-template}

您可以建構函式或變數程式庫以供稍後使用。 若要這麼做，請使用&#x200B;**eval**&#x200B;函式匯入JavaScript範本。 這可讓您使用在其他JavaScript範本中宣告的其他函式豐富內容。

**範例**：匯入&#x200B;**common.jsp**&#x200B;範本。

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### 編輯JavaScript範本 {#editing-a-javascript-template}

編輯區域可讓您填入JavaScript範本的內容：

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>必須填入關聯的資料模型結構描述，才能初始化JavaScript物件。

若要隨時產生輸出檔案的預覽，請選取內容和輸出格式(HTML、文字、XML)，然後按一下&#x200B;**[!UICONTROL Generate]**：

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>不需要儲存變更即可預覽輸出檔案。

### 如何建立及使用JavaScript範本的範例 {#example-of-how-to-create-and-use-a-javascript-template}

在下方，您會找到使用JavaScript範本實作下列內容管理所需的設定：

![](assets/d_ncs_content_sample_1.png)

此範例涉及下列步驟：

1. 建立下列結構描述（在此案例中： **neo：news**）：

   ```
   <srcSchema _cs="Invitation (neo)"   entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Invitation" mappingType="sql" name="news" namespace="neo" xtkschema="xtk:srcSchema">
   
     <enumeration basetype="string" default="en" name="language">
       <value label="Français" name="fr" value="fr"/>
       <value label="English" name="gb" value="gb"/>
     </enumeration>
   
     <enumeration basetype="string" name="css">
       <value label="Blue" name="bl" value="blue"/>
       <value label="Orange" name="or" value="orange"/>
     </enumeration>
   
     <element label="Intervenants" name="attendee">
       <key internal="true" name="id">
         <keyfield xpath="@id"/>
       </key>
       <attribute label="Name" name="name" type="string"/>
       <element label="Image" name="image" target="xtk:fileRes" type="link"/>
       <attribute label="Description" name="description" type="string"/>
       <attribute default="Gid()" label="Id" name="id" type="long"/>
     </element>
   
     <element label="Invitation" name="news" template="ncm:content" xmlChildren="true">
   
       <compute-string expr="@name"/>
       <attribute enum="language" label="Language" name="language" type="string"/>
       <attribute enum="css" label="Stylesheet" name="css" type="string"/>
       <attribute label="Title" name="title" type="string"/>
       <element label="Presentation" name="presentation" type="html"/>
       <attribute label="Date" name="date" type="date"/>
       <element label="Attendees list" name="attendeesList" ordered="true" ref="attendee" unbound="true"/>
   
     </element>
   </srcSchema>
   ```

1. 建立連結的&#x200B;**[!UICONTROL Content management]**&#x200B;型別表單(**neo：news**)

   ```
   <form _cs="News (neo)" entitySchema="xtk:form"  img="xtk:form.png" label="News"  name="news" namespace="neo" type="contentForm" xtkschema="xtk:form">
   
     <container type="iconbox">
       <container label="Invitation">
         <input xpath="@langue"/>
         <input xpath="@css"/>
         <input xpath="@title"/>
         <input xpath="@date"/>
         <input xpath="presentation"/>
       </container>
   
       <container label="Intervenants">
         <container toolbarCaption="Liste des intervenants" type="notebooklist" xpath="attendeesList" xpath-label="@nom">
           <container>
             <input xpath="@nom"/>
             <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
               <sysFilter>
                 <condition expr="@isImage = true"/>
               </sysFilter>
             </input>
             <input xpath="@description"/>
           </container>
         </container>
       </container>
     </container>
   
   </form>
   ```

1. 使用HTML和文字格式的訊息內容建立JavaScript範本。

   * 在我們的範例中，對於HTML：

     ```
     <html>     
       <head>         
         <title>Newsletter</title>
          <style type="text/css">
           .body {font-family:Verdana, Arial, Helvetica, sans-serif; font-size:10px; color:#514c48; margin-left: auto; margin-right: auto;}
           .body table {width:748; border: solid 1px; cellpadding:0; cellspacing:0"}
          </style>
       </head>     
       <body>
         <p><center><%= mirrorPage %></center></p>
         <center>
           <table>      
            <tr>
             <td>                                                         
               <img src="[LOGO]"/>                                   
             </td>
             <td>
               <h1><%= content.@title %></h1>
             </td>
            </tr>
            <tr>
     
            <td>
             <div >                                    
               <h0><%= hello,</h0>                              
               <p><%= content.presentation %></p>                                          
     
               <h0>Useful information</h0>                              
               <p>                                  
                 <img src="[IMAGE 1]"/>When? <br/><%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.</p><br/>                                       
               <p>                                  
                 <img src="[IMAGE 2]"/>Who? <br>Meet our favorite authors and illustrators and get a signed copy of their book.</p><br/>                                                         
               <p>                                  
                 <img src="[IMAGE 3]"/>Attendance is free but there is a limited number of seats: sign up now!</p>
           </div>
           </td>
     
             <td>                                                    
              <div style="text-align:left; width:210; height:400px; background:url([IMAGE DE FOND])">
     
                 <h0><%= participant %></h0>
                 <%
                 var i
                 var iLength = content.attendeesList.length()
                 for (i=0; i<iLength; i++)
                 { %>
                 <p>
                   <%= generateImgTag(content.attendeesList[i].@["image-id"]) %>  <%= content.attendeesList[i].@description %>
                 </p>  
                 <% }  
                 %>                              
              </div2>
             </td>
         </tr>
       </table>
     </center>
     </body>    
     </html>
     ```

   * 對於文字：

     ```
     <%= content.@title %>
     <%= content.presentation %>
     
     *** When? On <%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.
     
     *** Who? Come and meet our favorite authors and illustrators and get a signed copy of their books. 
     
     *** Attendance is free but there is a limited number of seats: sign up now!
     
     Guests:
     ******************
     <%
     var i
     var iLength = content.attendeesList.length()
     //for (i=(iLength-1); i>-1; i--)
     for( i=0 ; i<iLength ; i++ )
       { %>
       Description <%= i %> : <%= content.attendeesList[i].@description %>
       <% }  
     %>
     ```

1. 現在建立用於兩種格式的出版物範本：

   * 對於HTML：

     ![](assets/d_ncs_content_sample_2.png)

   * 針對文字：

     ![](assets/d_ncs_content_sample_3.png)

1. 然後，您就可以在傳送中使用此內容範本。

   如需詳細資訊，請參閱[使用內容範本](using-a-content-template.md)。

## XSL樣式表 {#xsl-stylesheets}

XSLT語言可讓您將XML檔案變更為輸出檔案。 根據樣式表的輸出方法，產生的檔案可以以HTML、純文字或其他XML樹狀結構產生。

在稱為樣式表的檔案中，此轉換又以XML格式詳述。

### 識別樣式表 {#identifying-a-stylesheet}

樣式表會以其名稱和名稱空間來識別，就像結構描述和表單一樣。 不過，建議您將&#x200B;**.xsl**&#x200B;副檔名新增至樣式表的名稱。

樣式表的識別索引鍵是由名稱空間和名稱組成的字串，以冒號分隔；例如： **cus：book.xsl**。

### 樣式表的結構 {#structure-of-a-stylesheet}

根據範例結構描述「cus：book」的HTML格式化樣式表範例：

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>
  <!-- Point of entry of the stylesheet -->
  <xsl:template match="/book">
    <html>
      <body>
        <!-- Book title -->
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <!-- List of chapters -->
          <xsl:for-each select="child::chapter">
            <li><xsl:value-of select="@name"/></li>
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

樣式表是遵循下列規則的XML檔案：

* 屬性的值在引號之間，
* 元素必須有開始標籤和結束標籤，
* 將&#39;&lt;&#39;或&#39;&amp;&#39;字元取代為&#x200B;**&#39;&lt;&#39;**&#x200B;或&#x200B;**&#39;&amp;&#39;**&#x200B;實體，
* 每個XSL專案都必須使用&#x200B;**xsl**&#x200B;名稱空間。

樣式表必須以XSL根專案標籤&#x200B;**`<xsl:stylesheet>`**&#x200B;開頭，並以&#x200B;**`</xsl:stylesheet>`**&#x200B;標籤結尾。 XSL名稱空間必須在開頭標籤中定義，如下所示：

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

**`<xsl:output>`**&#x200B;專案指定所產生的檔案格式。 指定所需的字元集和輸出格式。

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

下列指示說明輸出檔案格式化的樣式表組態。

```
<xsl:template match="/book">
  <html>
    <body>
      <!-- Book title -->
      <h1><xsl:value-of select="@name"/></h1>
      <lu>
        <!-- List of chapters -->
        <xsl:for-each select="child::chapter">
          <li><xsl:value-of select="@name"/></li>
        </xsl:for-each>
      </lu>
    </body>
  </html>
</xsl:template>
```

依預設，XSLT處理器會搜尋套用至輸入XML檔案根或主節點的&#x200B;**範本**。 輸出檔案的建構從此&#x200B;**範本**&#x200B;開始。

在我們的範例中，HTML頁面是從&quot;cus：book&quot;結構描述產生，並顯示書冊名稱和章節清單。

>[!NOTE]
>
>如需XSLT語言的詳細資訊，請參閱XSLT參考檔案。

### 顯示HTML/XML {#displaying-html-xml}

若要顯示&#x200B;**html**&#x200B;欄位，請使用&#x200B;**`<xsl:value-of>`**&#x200B;指示詞中的&#x200B;**disable-output-escaping=&quot;yes&quot;**&#x200B;選項。 這可讓您避免將字元取代為其XML實體（例如&lt;替換為&lt;）。

具有&#x200B;**disable-output-escaping=&quot;yes&quot;**&#x200B;選項的&#x200B;**`<xsl:text>`**&#x200B;指示詞可讓您為個人化欄位或條件測試插入JavaScript標籤。

範例：

* 顯示「html」型別欄位的內容：

  ```
  <xsl:value-of select="summary" disable-output-escaping="yes"/>
  ```

* 插入個人化欄位&#x200B;**&lt;%= recipient.email %>**：

  ```
  <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
  ```

* 正在新增條件式測試&#x200B;**&lt;%，如果(recipient.language == &#39;en&#39;) `{` %>**：

  ```
  <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
  ```

### 包含樣式表 {#including-stylesheets}

您可以建立範本或變數的程式庫，以便在數個樣式表之間共用。 以上顯示的「longMonth」**範本**&#x200B;是典型，說明在樣式表中從遠端尋找範本以便日後重複使用所具有的好處。

**`<xsl:include>`**&#x200B;指示指示要包含在檔案中的樣式表名稱。

**範例**：包含「common.xsl」樣式表。

```
<? xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:include href="common.xsl"/> 
  <xsl:output encoding="ISO-8859-1" method="jsp" indent="yes"/>
  ...
</xsl:stylesheet>
```

>[!NOTE]
>
>不得在要包含的樣式表參照中輸入名稱空間名稱。 作為標準，此樣式表是使用使用者名稱空間建立的。

### 編輯樣式表 {#editing-a-stylesheet}

編輯區域可讓您填入樣式表的內容：

![](assets/d_ncs_content_form14.png)

若要隨時產生輸出檔案的預覽，請選取內容執行個體和格式(HTML、文字、XML)，然後按一下「**[!UICONTROL Generate]**」：

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>不需要在樣式表中儲存變更即可檢視輸出檔案預覽。

## 影像管理 {#image-management}

### 影像引用 {#image-referencing}

在HTML輸出檔案中輸入的影像可以使用絕對或相對參照來參照。

相對參照可讓您輸入包含&#x200B;**NcmResourcesDir**&#x200B;與&#x200B;**NcmResourcesDirPreview**&#x200B;選項中影像的伺服器URL。 這些選項包含在Adobe Campaign使用者端主控台中發佈和預覽的影像位置。

這兩個選項可透過&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;資料夾中的選項管理畫面存取。

**範例**：

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x：/images/&quot;

在樣式表處理期間，輸入XML檔案之主要元素上的&#x200B;**_resPath**&#x200B;屬性會根據內容（預覽或發佈）自動填入一個或其他選項。

如何搭配影像使用影像放置選項及其使用範例：

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>我們建議宣告包含儲存影像之伺服器參考的變數（範例中為「resPath」）。

### 使用公用資源 {#using-public-resources}

您也可以使用&#x200B;**[!UICONTROL Public resources]**&#x200B;來宣告影像，並根據在部署精靈中輸入的執行個體設定將其上傳到伺服器。

然後您可以在內容中呼叫這些影像。 若要這麼做，請在內容管理架構中使用下列語法：

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

在表單中，將透過以下語法新增用於選取影像的欄位：

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>有關&#x200B;**[!UICONTROL Public resources]**&#x200B;以及如何設定和使用它們的詳細資訊，請參閱[本節](../../installation/using/deploying-an-instance.md#managing-public-resources)。

## 日期顯示 {#date-display}

在XML輸入檔案中，日期以內部XML格式儲存： **`YYYY/MM/DD HH:MM:SS`** （範例`2018/10/01 12:23:30`）。

Adobe Campaign為JavaScript範本和XSL樣式表提供日期格式功能，如下所述。

### JavaScript日期格式 {#javascript-date-formatting}

若要以所需格式顯示日期，Adobe Campaign提供&#x200B;**formatDate**&#x200B;函式，該函式接受日期的內容作為輸入，並提供字串，指定使用下列語法的輸出格式： **%4Y/%2M/%2D %2H%2N%2S**

範例：

* 以&#x200B;**31/10/2018**&#x200B;格式顯示日期：

  ```
   <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
  ```

* 以&#x200B;**2018年7月**&#x200B;格式顯示日期：

  ```
  <%
   function displayDate(date)
    {
      var aMonth = 
      [ 'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December' ];
  
      var month = formatDate(content.@date, "%2M")
      var year = formatDate(content.@date, "%4Y")
  
      return aMonth[month-1]+" "+year;
    }
  %>
  
  <%= displayDate(content.@date) %>
  ```

### XSL日期格式 {#xsl-date-formatting}

XSLT語法中沒有標準的日期管理函式。 若要以所需格式顯示日期，Adobe Campaign提供外部函式&#x200B;**date-format**。 此函式將日期的內容和字串當作輸入，並使用下列語法指定輸出格式： **%4Y/%2M/%2D %2H%2N%2S**

範例：

* 若要以&#x200B;**01/10/2018**&#x200B;格式顯示日期：

  ```
  <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
  ```

* 若要以&#x200B;**2018年7月**&#x200B;格式顯示日期：

  ```
  <!-- Returns the month in the form of a string with the month number as input -->
  <xsl:template name="longMonth">
    <xsl:param name="monthNumber"/>
  
    <xsl:choose>
      <xsl:when test="$monthNumber = 1">January</xsl:when>
      <xsl:when test="$monthNumber = 2">February</xsl:when>
      <xsl:when test="$monthNumber = 3">March</xsl:when>
      <xsl:when test="$monthNumber = 4">April</xsl:when>
      <xsl:when test="$monthNumber = 5">May</xsl:when>
      <xsl:when test="$monthNumber = 6">June</xsl:when>
      <xsl:when test="$monthNumber = 7">July</xsl:when>
      <xsl:when test="$monthNumber = 8">August</xsl:when>
      <xsl:when test="$monthNumber = 9">September</xsl:when>
      <xsl:when test="$monthNumber = 10">October</xsl:when>
      <xsl:when test="$monthNumber = 11">November</xsl:when>
      <xsl:when test="$monthNumber = 12">December</xsl:when>
    </xsl:choose>
  </xsl:template> 
  
  <!-- Display date -->
  <xsl:call-template name="longMonth">
    <xsl:with-param name="monthNumber">
      <xsl:value-of select="external:date-format(@date, '%2M')"/>
    </xsl:with-param>
  </xsl:call-template>
   <xsl:value-of select="external:date-format(@date, '%4y')"/>
  ```
