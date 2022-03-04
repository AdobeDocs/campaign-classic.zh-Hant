---
product: campaign
title: 格式
description: 格式
feature: Email Design
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# 格式{#formatting}

![](../../assets/common.svg)

## JavaScript模板 {#javascript-templates}

JavaScript模板是包含JavaScript代碼的HTML或文本文檔。 它的構建方式與傳遞操作中的電子郵件內容相同。

### JavaScript模板的標識 {#identification-of-a-javascript-template}

JavaScript模板由其名稱和命名空間標識，與架構和表單一樣。 但是，建議添加 **.js** 的子菜單。

### JavaScript模板的結構 {#structure-of-a-javascript-template}

基於&quot;cus:book&quot;架構的JavaScriptHTML格式模板示例：

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

各種JavaScript指令以下列形式顯示：

* 合併欄位：顯示資料的內容 **`<%= <source> %>`** 語法 `<source>`是要顯示的資料的源欄位。
* 指令塊：執行&lt;%和%>標籤之間包含的一系列JavaScript指令。

的 **內容** 對象表示輸入XML文檔的主要元素。

在本例中，以下行顯示名稱簿名稱的內容：

```
<h1><%= content.@name %></h1>
```

以下代碼迭代 `<chapter>` 集合元素：

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

內容的屬性和元素被表示為JavaScript對象，並且與源文檔的結構相關。

**範例**:

* **內容。@name**:檢索主元素的&quot;name&quot;屬性值
* **內容。@`['name']`**:與 **內容。@name** 語法
* **cont.chapter.length**:返回上的元素數 `<chapter` 集合元素
* **content.chapter`[0]`。@name**:檢索第一個 `<chapter>` 元素
* **chapter.name()**:返回的名稱 `<chapter>` 元素
* **chapter.parent()。name()**:返回的父元素的名稱 `<chapter>`

>[!CAUTION]
>
>由於「 — 」字元是JavaScript語言中保留的，因此必須通過 `['<field>']` 語法。
>
>例如： `content.@['offer-id']`。

寫程式語言(變數、循環、條件test、函式等)的全部功能。 )可用於構建輸出文檔。 可訪問SOAP API以豐富輸出文檔。

範例:

* 條件test:

   ```
   <% if (content.@number == 1 || content.@language == 'en') { %>
   <!-- Content to be displayed if test is true--> 
   <% } %>
   ```

* 函式調用：

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

* 聲明和變數調用：

   ```
   <%  var counter = 0; %>
   
   <%= counter += 10 %>
   ```

* 使用靜態方法檢索和顯示收件人名稱：

   ```
   <% var recipient = nms.recipient.get(1246); %>
   <%= recipient.lastName %>
   ```

* 使用非靜態方法恢復和顯示收件人名稱：

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

### 包括JavaScript模板 {#including-a-javascript-template}

可以構成函式或變數庫供以後使用。 為此，請使用 **評估** 的子菜單。 這樣，您就可以使用其他JavaScript模板中聲明的附加函式來豐富上下文。

**示例**:導入 **common.jsp** 的下界。

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### 編輯JavaScript模板 {#editing-a-javascript-template}

編輯區域允許您填充JavaScript模板的內容：

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>必須填充關聯的資料模型架構以初始化JavaScript對象。

要隨時生成輸出文檔的預覽，請選擇內容和輸出格式(HTML、文本、XML)，然後按一下 **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>無需保存更改即可預覽輸出文檔。

### 如何建立和使用JavaScript模板的示例 {#example-of-how-to-create-and-use-a-javascript-template}

在下面，您將找到使用JavaScript模板實現以下內容管理所需的配置：

![](assets/d_ncs_content_sample_1.png)

此示例包括以下步驟：

1. 建立以下架構(在本例中為： **新聞**):

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

1. 建立連結 **[!UICONTROL Content management]** 類型窗體&#x200B;**新聞**)

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

1. 建立包含HTML和文本格式消息內容的JavaScript模板。

   * 在本例中，對於HTML:

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

   * 對於文本：

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

1. 現在建立用於兩種格式的發佈模板：

   * HTML:

      ![](assets/d_ncs_content_sample_2.png)

   * 文本：

      ![](assets/d_ncs_content_sample_3.png)

1. 然後，您可以在交貨中使用此內容模板。

   有關此內容的詳細資訊，請參閱 [使用內容模板](using-a-content-template.md)。

## XSL樣式表 {#xsl-stylesheets}

XSLT語言允許您將XML文檔更改為輸出文檔。 根據樣式表的輸出方法，可以在HTML、純文字檔案或其他XML樹中生成結果文檔。

此轉換在稱為樣式表的文檔中以XML形式詳細描述。

### 標識樣式表 {#identifying-a-stylesheet}

樣式表由其名稱和命名空間標識，與架構和表單一樣。 但是，建議您添加 **.xsl** 樣式表名稱的擴展。

樣式表的標識鍵是由命名空間和名稱以冒號分隔的字串；例如： **cus:book.xsl**。

### 樣式表的結構 {#structure-of-a-stylesheet}

基於示例架構&quot;cus:book&quot;的HTML格式樣式表示例：

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

樣式表是遵循以下規則的XML文檔：

* 屬性值介於引號之間，
* 元素必須具有開啟標籤和關閉標籤，
* 將「&lt;」或「&amp;」字元替換為 **「&lt;」** 或 **&#39;&amp;&#39;** 實體，
* 每個XSL元素必須使用 **x** 命名空間。

樣式表必須以XSL根元素標籤開頭 **`<xsl:stylesheet>`** 以 **`</xsl:stylesheet>`** 標籤。 XSL命名空間必須在開啟標籤中定義如下：

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

的 **`<xsl:output>`** 元素指定生成的文檔的格式。 指定所需的字元集和輸出格式。

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

以下說明描述了用於輸出文檔格式化的樣式表的配置。

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

預設情況下，XSLT處理器會查找 **模板** 應用於輸入XML文檔的根節點或主節點。 輸出文檔的構建以此開始 **模板**。

在本例中，通過顯示書名和章節清單，從「cus:book」架構生成HTML頁。

>[!NOTE]
>
>有關XSLT語言的詳細資訊，請參閱XSLT參考文檔。

### 顯示HTML/XML {#displaying-html-xml}

顯示 **html** 欄位，使用 **disable-output-esgein=&quot;是&quot;** 的 **`<xsl:value-of>`** 指令。 這樣，您就可以避免用其XML實體替換字元（例如&lt;與&lt;）。

的 **`<xsl:text>`** 指令 **disable-output-esgein=&quot;是&quot;** 選項，可以為個性化欄位或條件test插入JavaScript標籤。

範例:

* 顯示「html」類型欄位的內容：

   ```
   <xsl:value-of select="summary" disable-output-escaping="yes"/>
   ```

* 插入個性化欄位 **&lt;%=收件人電子郵件%>**:

   ```
   <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
   ```

* 添加條件test **&lt;% if(recipient.language == &#39;en) `{` %>**:

   ```
   <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
   ```

### 包括樣式表 {#including-stylesheets}

可以建立要在多個樣式表之間共用的模板或變數庫。 &quot;longMonth&quot; **模板**&#x200B;上面介紹的是一個典型示例，說明了在樣式表中遠程定位模板以便以後可以重新使用這一優勢。

的 **`<xsl:include>`** 指令指示要包含在文檔中的樣式表的名稱。

**示例**:包括「common.xsl」樣式表。

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

## 映像管理 {#image-management}

### 影像引用 {#image-referencing}

在HTML輸出文檔中輸入的影像可以用絕對或相對引用來引用。

相對引用允許您輸入包含以下影像的伺服器的URL: **Ncm資源目錄** 和 **NcmRessourcesDirPreview** 頁籤 這些選項包含在Adobe Campaign客戶端控制台中用於發佈和預覽的影像的位置。

通過中的選項管理螢幕，可以訪問這兩個選項 **[!UICONTROL Administration > Platform > Options]** 的子菜單。

**範例**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

在樣式表處理期間， **_res路徑** 根據上下文（預覽或發佈），輸入XML文檔的主元素上的屬性會自動用一個或多個選項填充。

如何使用影像放置選項及其與影像的使用示例：

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>我們建議聲明一個變數，該變數包含儲存影像的伺服器的引用（本例中為「resPath」）。

### 使用公共資源 {#using-public-resources}

您還可以使用 **[!UICONTROL Public resources]** 根據部署嚮導中輸入的實例設定聲明映像並將其上載到伺服器。

然後，可以在內容中調用這些影像。 為此，請在內容管理架構中使用以下語法：

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

在窗體中，將通過以下語法添加用於選擇影像的欄位：

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>更多內容 **[!UICONTROL Public resources]** 以及如何配置和使用它們，請參閱 [此部分](../../installation/using/deploying-an-instance.md#managing-public-resources)。

## 日期顯示 {#date-display}

在XML輸入文檔中，日期以內部XML格式儲存： **YYYY/MM/DD HH:MM:SS** (例2018/10/01 12):23:30)。

Adobe Campaign為JavaScript模板和XSL樣式表提供日期格式函式，詳見下文。

### JavaScript日期格式 {#javascript-date-formatting}

要以所需格式顯示日期，Adobe Campaign提供 **格式日期** 函式，該函式用作輸入日期的內容，並使用以下語法指定輸出格式的字串： **%4y/%2m/%2d %2h%2n%2s**

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

XSLT語法中沒有標準日期管理功能。 要以所需格式顯示日期，Adobe Campaign提供外部函式 **日期格式**。 此函式作為其輸入，使用以下語法指定輸出格式的字串： **%4y/%2m/%2d %2h%2n%2s**

範例:

* 在中顯示日期 **01/10/2018** 格式：

   ```
   <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
   ```

* 在中顯示日期 **2018年7月** 格式：

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
