---
product: campaign
title: 格式
description: 格式
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# 格式{#formatting}

![](../../assets/common.svg)

## JavaScript範本 {#javascript-templates}

JavaScript範本是包含JavaScript程式碼的HTML或文字檔案。 其建構方式與傳送動作中的電子郵件內容相同。

### JavaScript範本的識別 {#identification-of-a-javascript-template}

JavaScript範本的名稱和命名空間與結構和表單相同。 不過，建議將 **.js** 選項。

### JavaScript範本的結構 {#structure-of-a-javascript-template}

以「cus:book」架構為基礎的JavaScriptHTML格式範本範例：

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

各種JavaScript指令會以下列形式顯示：

* 合併欄位：使用 **`<%= <source> %>`** 語法 `<source>`是要顯示的資料的來源欄位。
* 指令塊：會執行&lt;%和%>標籤之間包含的一系列JavaScript指示。

此 **內容** 對象表示輸入XML文檔的主要元素。

在我們的範例中，下列行顯示名稱帳簿名稱的內容：

```
<h1><%= content.@name %></h1>
```

下列程式碼會反覆在 `<chapter>` 集合元素：

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

內容的屬性和元素會以JavaScript物件表示，並遵循來源檔案的結構。

**範例**:

* **內容。@name**:擷取主要元素的「name」屬性值
* **內容。@`['name']`**:與相同 **內容。@name** 語法
* **content.chapter.length**:傳回 `<chapter` 集合元素
* **content.chapter`[0]`.@name**:擷取第一個 `<chapter>` 元素
* **chapter.name()**:傳回的名稱 `<chapter>` 元素
* **chapter.parent()。name()**:傳回的父元素名稱 `<chapter>`

>[!CAUTION]
>
>由於「 — 」字元是以JavaScript語言保留，因此必須透過 `['<field>']` 語法。
>
>例如： `content.@['offer-id']`.

寫程式語言（變數、循環、條件測試、函式等）的所有力量。 )可用來建構輸出檔案。 SOAP API可供存取，以豐富輸出檔案。

範例:

* 條件測試：

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

* 宣告與變數呼叫：

   ```
   <%  var counter = 0; %>
   
   <%= counter += 10 %>
   ```

* 使用靜態方法擷取和顯示收件者名稱：

   ```
   <% var recipient = nms.recipient.get(1246); %>
   <%= recipient.lastName %>
   ```

* 使用非靜態方法恢復和顯示收件者名稱：

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

您可以建立函式或變數的程式庫，以供日後使用。 若要這麼做，請使用匯入JavaScript範本 **eval** 函式。 這可讓您透過在其他JavaScript範本中宣告的其他函式來擴充內容。

**範例**:匯入 **common.jsp** 範本。

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### 編輯JavaScript範本 {#editing-a-javascript-template}

編輯區域可讓您填入JavaScript範本的內容：

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>必須填入關聯的資料模型架構，以初始化JavaScript物件。

要隨時生成輸出文檔的預覽，請選擇內容和輸出格式(HTML、文本、XML)，然後按一下 **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>無需保存更改即可預覽輸出文檔。

### 如何建立和使用JavaScript範本的範例 {#example-of-how-to-create-and-use-a-javascript-template}

以下是使用JavaScript範本實作下列內容管理所需的設定：

![](assets/d_ncs_content_sample_1.png)

此範例包含下列步驟：

1. 建立下列結構(在此例中為： **neo：新聞**):

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

1. 建立連結的 **[!UICONTROL Content management]** 類型表單(**neo：新聞**)

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

1. 以HTML和文字格式建立包含訊息內容的JavaScript範本。

   * 在我們的範例中，針對HTML:

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

   * 文字：

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

1. 現在，建立用於兩種格式的發佈模板：

   * HTML:

      ![](assets/d_ncs_content_sample_2.png)

   * 文字：

      ![](assets/d_ncs_content_sample_3.png)

1. 然後，您可以在傳送中使用此內容範本。

   有關詳細資訊，請參閱 [使用內容範本](using-a-content-template.md).

## XSL樣式表 {#xsl-stylesheets}

使用XSLT語言，可以將XML文檔更改為輸出文檔。 根據樣式表的輸出方法，可以在HTML、純文字檔案或其他XML樹中生成生成的文檔。

此轉換在稱為樣式表的文檔中以XML形式詳細描述。

### 標識樣式表 {#identifying-a-stylesheet}

樣式表由其名稱和命名空間來識別，就像結構和表單一樣。 不過，建議您新增 **.xsl** 樣式表名稱的擴展。

樣式表的標識鍵是由命名空間和冒號分隔的名稱組成的字串；例如： **cus:book.xsl**.

### 樣式表的結構 {#structure-of-a-stylesheet}

基於示例架構「cus:book」的HTML格式樣式表的示例：

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

樣式表是遵循下列規則的XML文檔：

* 屬性值在引號之間，
* 元素必須具有開頭標籤和結尾標籤，
* 將「&lt;」或「&amp;」字元替換為 **&#39;&lt;&#39;** 或 **&#39;&amp;&#39;** 實體，
* 每個XSL元素都必須使用 **xsl** 命名空間。

樣式表必須以XSL根元素標籤開頭 **`<xsl:stylesheet>`** 結尾是 **`</xsl:stylesheet>`** 標籤。 XSL命名空間必須定義在開頭標籤中，如下所示：

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

此 **`<xsl:output>`** 元素指定生成的文檔的格式。 指定所需的字元集和輸出格式。

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

以下說明說明了輸出文檔格式化的樣式表的配置。

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

預設情況下，XSLT處理器將搜索 **範本** 應用於輸入XML文檔的根或主節點。 輸出文檔的構建從以下內容開始 **範本**.

在我們的範例中，透過顯示書籍名稱和章節清單，從「cus:book」架構產生HTML頁面。

>[!NOTE]
>
>有關XSLT語言的詳細資訊，請參閱XSLT參考文檔。

### 顯示HTML/XML {#displaying-html-xml}

若要顯示 **html** 欄位，使用 **disable-output-escine=&quot;yes&quot;** 選項 **`<xsl:value-of>`** 指令。 這可讓您避免以其XML實體取代字元（例如，&lt;為&lt;）。

此 **`<xsl:text>`** 指令 **disable-output-escine=&quot;yes&quot;** 選項可讓您插入個人化欄位或條件測試的JavaScript標籤。

範例:

* 顯示「html」類型欄位的內容：

   ```
   <xsl:value-of select="summary" disable-output-escaping="yes"/>
   ```

* 插入個人化欄位 **&lt;%= recipient.email %>**:

   ```
   <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
   ```

* 新增條件式測試 **&lt;% if(recipient.language == &#39;en&#39;) `{` %>**:

   ```
   <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
   ```

### 包括樣式表 {#including-stylesheets}

可以建立要在多個樣式表之間共用的模板或變數庫。 「longMonth」 **範本**，上面介紹的是一個典型示例，說明了在樣式表中遠程定位模板以便以後可以重複使用的優點。

此 **`<xsl:include>`** 指令指明要包含在文檔中的樣式表的名稱。

**範例**:包括「common.xsl」樣式表。

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
>不能在要包括的樣式表的引用中輸入命名空間的名稱。 作為標準，此樣式表是使用用戶命名空間建立的。

### 編輯樣式表 {#editing-a-stylesheet}

編輯區域允許您填充樣式表的內容：

![](assets/d_ncs_content_form14.png)

要隨時生成輸出文檔的預覽，請選擇內容實例和格式(HTML、文本、XML)，然後按一下 **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>無需在樣式表中保存更改即可查看輸出文檔預覽。

## 影像管理 {#image-management}

### 影像參考 {#image-referencing}

輸入在HTML輸出文檔中的影像可以用絕對參照或相對參照參照。

相對引用可讓您輸入包含 **NcmRessourcesDir** 和 **NcmRessourcesDirPreview** 選項。 這些選項包含要發佈和在Adobe Campaign用戶端主控台中預覽的影像位置。

可透過 **[!UICONTROL Administration > Platform > Options]** 檔案夾。

**範例**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

在樣式表處理期間， **_resPath** 根據上下文（預覽或發佈），輸入XML文檔的主要元素上的屬性將自動填充一個或多個選項。

如何使用影像放置選項及其與影像搭配使用的範例：

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>建議聲明一個變數，其中包含儲存影像的伺服器的參考（在本例中為「resPath」）。

### 使用公共資源 {#using-public-resources}

您也可以使用 **[!UICONTROL Public resources]** 根據在部署嚮導中輸入的實例設定來聲明映像並將其上傳到伺服器。

然後，您可以在內容中呼叫這些影像。 要執行此操作，請在內容管理架構中使用下列語法：

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

在表單中，會透過下列語法新增選取影像的欄位：

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>如需詳細資訊 **[!UICONTROL Public resources]** 以及如何設定及使用，請參閱 [本節](../../installation/using/deploying-an-instance.md#managing-public-resources).

## 日期顯示 {#date-display}

在XML輸入文檔中，日期以內部XML格式儲存： **YYYY/MM/DD HH:MM:SS** (範例2018/10/01 12:23:30)。

Adobe Campaign為JavaScript範本和XSL樣式表提供日期格式功能，如下所述。

### JavaScript日期格式 {#javascript-date-formatting}

若要以所需格式顯示日期，Adobe Campaign提供 **formatDate** 函式，此函式會作為日期內容的輸入，以及使用下列語法指定輸出格式的字串： **%4Y/%2M/%2D %2H%2N%2S**

範例:

* 在 **31/10/2018** 格式：

   ```
    <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
   ```

* 在 **2018年7月** 格式：

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

XSLT語法中沒有標準日期管理功能。 若要以所需格式顯示日期，Adobe Campaign提供外部功能 **日期格式**. 此函式會作為其輸入，並使用下列語法指定輸出格式的字串： **%4Y/%2M/%2D %2H%2N%2S**

範例:

* 若要在 **01/10/2018** 格式：

   ```
   <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
   ```

* 若要在 **2018年7月** 格式：

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
