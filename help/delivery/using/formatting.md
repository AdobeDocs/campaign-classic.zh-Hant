---
solution: Campaign Classic
product: campaign
title: 格式
description: 格式
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 0%

---


# 格式{#formatting}

## JavaScript範本{#javascript-templates}

JavaScript範本是包含JavaScript程式碼的HTML或文字檔案。 其建構方式與傳送動作中的電子郵件內容相同。

### JavaScript範本的識別{#identification-of-a-javascript-template}

JavaScript範本的名稱和名稱空間與結構描述和表單一樣可識別。 不過，建議將&#x200B;**.js**&#x200B;選項新增至範本名稱。

### JavaScript範本的結構{#structure-of-a-javascript-template}

以「cus:book」架構為基礎的JavaScript HTML格式範本範例：

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

各種JavaScript指令會以下列格式顯示：

* 合併欄位：以&#x200B;**`<%= <source> %>`**&#x200B;語法顯示資料內容，其中`<source>`是要顯示資料的源欄位。
* 指令塊：執行&lt;%和%>標籤之間包含的一系列JavaScript指示。

**content**&#x200B;物件代表輸入XML檔案的主要元素。

在我們的範例中，下列行顯示名稱手冊名稱的內容：

```
<h1><%= content.@name %></h1>
```

下列程式碼會重複`<chapter>`系列元素：

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

內容的屬性和元素會以JavaScript物件來表示，並尊重來源檔案的結構。

**範例**:

* **內容。@name**:檢索主要元素的&quot;name&quot;屬性的值
* **內容。@`['name']`**:與&#x200B;**內容相同。@name**&#x200B;語法
* **content.chapter.length**:返回收集元素上的元 `<chapter` 素數
* **content.chapter`[0]`。@name**:檢索第一個`<chapter>`元素的名稱
* **chapter.name()**:返回元素的名 `<chapter>` 稱
* **chapter.parent()。name()**:傳回的父元素名稱  `<chapter>`

>[!CAUTION]
>
>由於&#39;-&#39;字元是以JavaScript語言保留，因此必須透過`['<field>']`語法來復原包含此字元的任何屬性或元素的值。
>
>例如：`content.@['offer-id']`。

程式設計語言（變數、回圈、條件測試、函式等）的全部功能。 )可用於構建輸出文檔。 SOAP API可供存取，讓輸出檔案更豐富。

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

* 聲明和變數呼叫：

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

### 包含JavaScript範本{#including-a-javascript-template}

您可以組成函式或變數的程式庫，以供日後使用。 若要這麼做，請匯入具有&#x200B;**eval**&#x200B;函式的JavaScript範本。 這可讓您運用其他JavaScript範本中宣告的其他函式來豐富內容。

**範例**:導入 **common.** jsptemplate。

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### 編輯JavaScript範本{#editing-a-javascript-template}

編輯區可讓您填入JavaScript範本的內容：

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>必須填入關聯的資料模型架構，才能初始化JavaScript物件。

要隨時生成輸出文檔的預覽，請選擇內容和輸出格式(HTML、Text、XML)，然後按一下&#x200B;**[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>不必保存更改即可預覽輸出文檔。

### 如何建立和使用JavaScript範本{#example-of-how-to-create-and-use-a-javascript-template}的範例

以下是使用JavaScript範本實作下列內容管理所需的設定：

![](assets/d_ncs_content_sample_1.png)

此範例包含下列步驟：

1. 建立以下模式(在本例中為：**neo:news**:

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

1. 建立連結的&#x200B;**[!UICONTROL Content management]**&#x200B;類型表單(**neo:news**)

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

1. 現在，請建立用於兩種格式的出版物範本：

   * HTML:

      ![](assets/d_ncs_content_sample_2.png)

   * 對於文本：

      ![](assets/d_ncs_content_sample_3.png)

1. 然後，您可以在傳送中使用此內容範本。

   有關詳細資訊，請參閱[使用內容模板](../../delivery/using/using-a-content-template.md)。

## XSL樣式表{#xsl-stylesheets}

XSLT語言可讓您將XML檔案變更為輸出檔案。 根據樣式表的輸出方法，可以在HTML、純文字檔案或其他XML樹中生成生成的文檔。

此轉換在XML中，又在稱為樣式表的文檔中詳細介紹。

### 標識樣式表{#identifying-a-stylesheet}

樣式表由其名稱和名稱空間標識，與模式和表單一樣。 不過，建議您將&#x200B;**.xsl**&#x200B;副檔名新增至樣式表的名稱。

樣式表的標識鍵是由命名空間和名稱以冒號分隔的字串；例如：**cus:book.xsl**。

### 樣式表{#structure-of-a-stylesheet}的結構

HTML格式樣式表的示例基於模式&quot;cus:book&quot;:

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

* 屬性的值在引號之間，
* 元素必須有開啟標籤和關閉標籤，
* 以&#x200B;**&#39;**&#x200B;或&#x200B;**&#39;&amp;&#39;**&#x200B;實體取代&#39;&lt;&#39;或&#39;&amp;&#39;字元，
* 每個XSL元素都必須使用&#x200B;**xsl**&#x200B;命名空間。

樣式表必須以XSL根元素標籤&#x200B;**`<xsl:stylesheet>`**&#x200B;開頭，並以&#x200B;**`</xsl:stylesheet>`**&#x200B;標籤結尾。 XSL命名空間必須定義在開啟標籤中，如下所示：

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

**`<xsl:output>`**&#x200B;元素指定生成的文檔的格式。 指定所需的字元集和輸出格式。

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

以下說明輸出文檔格式化樣式表的配置。

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

預設情況下，XSLT處理器會搜索應用於輸入XML文檔的根節點或主節點的&#x200B;**template**。 輸出文檔的構建從此&#x200B;**模板**&#x200B;開始。

在我們的範例中，HTML頁面是透過顯示書籍名稱和章節清單，從「cus:book」架構產生。

>[!NOTE]
>
>有關XSLT語言的詳細資訊，請參閱XSLT參考文檔。

### 顯示HTML/XML {#displaying-html-xml}

若要顯示&#x200B;**html**&#x200B;欄位，請使用&#x200B;**`<xsl:value-of>`**&#x200B;指令中的&#x200B;**disable-output-egleine=&quot;yes&quot;**&#x200B;選項。 這可讓您避免以字元的XML實體取代字元（例如&lt;與&lt;）。

**`<xsl:text>`**&#x200B;指令及&#x200B;**disable-output-egleine=&quot;yes&quot;**&#x200B;選項可讓您插入個人化欄位或條件測試的JavaScript標籤。

範例:

* 顯示&quot;html&quot;類型欄位的內容：

   ```
   <xsl:value-of select="summary" disable-output-escaping="yes"/>
   ```

* 插入個人化欄位&#x200B;**&lt;%= recipient.email %>**:

   ```
   <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
   ```

* 新增條件測試&#x200B;**&lt;% if(recipient.language == &#39;en&#39;)`{` %>**:

   ```
   <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
   ```

### 包括樣式表{#including-stylesheets}

可以建立範本或變數庫，以便在多個樣式表之間共用。 上面顯示的&quot;longMonth&quot; **template**&#x200B;是一個典型的示例，說明了在樣式表中遠程查找模板以便以後可以重複使用的優點。

**`<xsl:include>`**&#x200B;指令指示要包含在文檔中的樣式表的名稱。

**範例**:包括&quot;common.xsl&quot;樣式表。

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
>不能在要包括的樣式表的引用中輸入命名空間的名稱。 作為標準，此樣式表使用用戶命名空間建立。

### 編輯樣式表{#editing-a-stylesheet}

編輯區可讓您填入樣式表的內容：

![](assets/d_ncs_content_form14.png)

要隨時生成輸出文檔的預覽，請選擇內容實例和格式(HTML、Text、XML)，然後按一下&#x200B;**[!UICONTROL Generate]** :

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>無需在樣式表中保存更改即可查看輸出文檔預覽。

## 映像管理{#image-management}

### 影像參照{#image-referencing}

在HTML輸出文檔中輸入的影像可以用絕對或相對參照引用。

相對引用可讓您在&#x200B;**NcmRessourcesDir**&#x200B;和&#x200B;**NcmRessourcesDirPreview**&#x200B;選項中輸入包含影像的伺服器的URL。 這些選項包含影像在Adobe Campaign用戶端主控台中的發佈和預覽位置。

這兩個選項可透過&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;資料夾中的選項管理畫面存取。

**範例**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

在樣式表處理期間，輸入XML文檔主要元素上的&#x200B;**_resPath**&#x200B;屬性會根據上下文（預覽或發佈）自動填充一個或多個選項。

如何使用影像放置選項及其與影像搭配使用的範例：

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>我們建議聲明一個變數，其中包含儲存影像的伺服器參考（在本例中為「resPath」）。

### 使用公共資源{#using-public-resources}

您也可以使用&#x200B;**[!UICONTROL Public resources]**&#x200B;來宣告影像，並根據在部署精靈中輸入的例項設定，將影像上傳至伺服器。

然後，您就可以在內容中呼叫這些影像。 若要這麼做，請在內容管理架構中使用下列語法：

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

在表單中，選取影像的欄位將透過下列語法新增：

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>有關&#x200B;**[!UICONTROL Public resources]**&#x200B;以及如何配置和使用它們的詳細資訊，請參閱[本節](../../installation/using/deploying-an-instance.md#managing-public-resources)。

## 日期顯示{#date-display}

在XML輸入檔案中，日期會以內部XML格式儲存：**YYYY/MM/DD HH:MM:SS**（例如2018/10/01 12:23:30）。

Adobe Campaign提供JavaScript範本和XSL樣式表的日期格式化函式，詳見下文。

### JavaScript日期格式{#javascript-date-formatting}

若要以所需格式顯示日期，Adobe Campaign會提供&#x200B;**formatDate**&#x200B;函式，以輸入日期內容，並提供以下語法指定輸出格式的字串：**%4Y/%2M/%2D %2H%2N%2S**

範例:

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

### XSL日期格式設定{#xsl-date-formatting}

XSLT語法中沒有標準的日期管理功能。 若要以所需格式顯示日期，Adobe Campaign會提供外部函式&#x200B;**date-format**。 此函式會作為其輸入，輸入日期的內容，並使用下列語法指定輸出格式的字串：**%4Y/%2M/%2D %2H%2N%2S**

範例:

* 要以&#x200B;**01/10/2018**&#x200B;格式顯示日期：

   ```
   <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
   ```

* 要以&#x200B;**2018年7月**&#x200B;格式顯示日期：

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
