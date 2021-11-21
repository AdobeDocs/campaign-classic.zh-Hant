---
product: campaign
title: 發佈範本
description: 發佈範本
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# 發佈範本{#publication-templates}

![](../../assets/common.svg)

## 關於發佈範本 {#about-publication-templates}

發佈範本是要發佈的內容的身分卡。 它會參考發佈程式中使用的資源，例如：

* 資料結構，
* 輸入表格，
* 每個輸出文檔的轉換模板。

## 出版物模板的標識 {#identification-of-a-publication-template}

發佈範本的名稱和命名空間可供識別。

樣式表的標識鍵是由命名空間和用冒號分隔的名稱組成的字串；例如： **cus:newsletter**.

>[!NOTE]
>
>實際上，建議對結構、表單和發佈範本使用相同的索引鍵。

## 建立和設定範本 {#creating-and-configuring-the-template}

發佈範本預設會儲存在 **[!UICONTROL Administration > Configuration > Publication templates]** 節點。 若要建立新範本，請按一下 **[!UICONTROL New]** 按鈕。

若要設定發佈範本，請填入範本名稱（即由名稱和命名空間組成的識別索引鍵）、其標籤、資料結構，以及連結的輸入表單。

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>每當根據此發佈範本建立內容時，就會顯示標籤。

此 **檢查狀態以驗證內容生成** 選項會強制檢查內容例項的「已驗證」狀態，以授權產生檔案。 有關詳細資訊，請參閱 [發佈](#publication).

必須為每個輸出文檔添加轉換模板。 您可以視需要建立任意數量的轉換範本。

此 **[!UICONTROL Name of template]** 欄位是自由標籤，用於說明輸出處的呈現類型。 對於每個轉換範本，發佈設定都可在索引標籤中使用。

### 轉譯 {#rendering}

此 **[!UICONTROL Rendering]** 頁簽，選擇

* 用於投影輸出文檔的渲染類型：XSL樣式表或JavaScript範本，
* 輸出文檔的格式：HTML、文本、XML或RTF,
* 包含構造資料的模板，即要使用的樣式表或JavaScript模板。

### 發佈 {#publication}

如果所選類型為，則發佈涉及以檔案形式生成輸出文檔 **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

可使用下列發佈選項：

* 輸出檔案編碼字元集可透過 **[!UICONTROL Encoding]** 欄位。 預設會使用拉丁文1(1252)字元集。
* 此 **[!UICONTROL Multi-file generation]** 選項將激活特殊文檔發佈模式。 此選項包括在輸出文檔的每個頁面的開頭填入分區標籤。 產生內容會為每個填入的分割標籤產生檔案。 此模式用於從內容區塊產生迷你網站。 有關詳細資訊，請參閱 [產生多檔案](#multi-file-generation).
* 此 **[!UICONTROL Location]** 欄位包含輸出檔案的名稱。 名稱可由變陣列成，以產生自動檔案名稱。

   變數會填入下列格式： **`$(<xpath>)`**，其中 **`<xpath>`** 是發佈範本資料架構欄位的路徑。

   檔案的名稱可以由日期類型欄位組成。 若要正確設定此欄位的格式，請使用 **$date-format** 函式，使用欄位的路徑和輸出格式作為參數。

   依預設，檔案名稱的建構格式會使用「@name」和「@date」欄位上的變數：

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   產生的檔案名稱將如下所示：ct_news12_20110901.htm。

   >[!NOTE]
   >
   >如需內容產生的詳細資訊，請參閱 [建立內容例項](using-a-content-template.md#creating-a-content-instance).

### 傳遞 {#delivery}

此索引標籤可讓您選取案例，以便直接在內容上啟動傳送。 電子郵件的內容將根據輸出格式(HTML或文字)自動填入。

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>如需根據內容建立傳送的範例，請參閱 [傳遞內容例項](using-a-content-template.md#delivering-a-content-instance).

### 匯總器 {#aggregator}

通過從指令碼或查詢清單聚合資料，可以使XML文檔與內容資料進行擴展。 其目的是補充連結所參考的特定資訊或從資料庫中新增元素。

### 產生多檔案 {#multi-file-generation}

若要啟動多個檔案產生，請選取 **[!UICONTROL Multi-file generation]** 選項。 此選項允許您在樣式表中指定輸出文檔每個頁面的開頭的分區標籤。 內容的產生會針對遇到的每個分割標籤產生檔案。

要整合到樣式表中的分區標籤如下：

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** where **`<name_of_file>`** 是要產生之頁面的檔案名稱。

**範例：** 使用「cus:book」架構生成多個檔案。

原則是產生列出章節的主要頁面，並可在外部頁面中顯示章節的詳細資訊。

![](assets/d_ncs_content_chunk.png)

相應的樣式表(&quot;cus:book.xsl&quot;)如下：

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

需要第二個樣式表(&quot;cus:chapter.xsl&quot;)來生成章節的詳細資訊：

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

分割標籤會填入至要包含在要產生之檔案中的頁面開頭。

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

檔案名稱是以 **$(path)** 包含發佈路徑和 **`<xsl:value-of select="@id" />`**，會比對輸入檔案中章節的識別碼。

必須用兩個樣式表&quot;cus:book.xsl&quot;和&quot;cus:chapter.xsl&quot;填充發佈模型。

此 **[!UICONTROL Multi-file generation]** 選項必須在章節轉換模型上處於作用中狀態：

![](assets/d_ncs_content_chunk2.png)

此 **[!UICONTROL Location]** 欄位不會用於產生多個檔案，但您仍必須填入此欄位，以避免發佈時發生錯誤。
