---
title: 出版物範本
seo-title: 出版物範本
description: 出版物範本
seo-description: null
page-status-flag: never-activated
uuid: 1976f70c-b2d8-44ca-8fc3-6451fb67d18b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 279b0ae6-2578-4f1f-af59-13a1a9c80b32
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 出版物範本{#publication-templates}

## 關於出版物範本 {#about-publication-templates}

發佈範本是要發佈的內容的識別卡。 它引用了發佈過程中使用的資源，即：

* 資料模式，
* 輸入表格，
* 每個輸出文檔的轉換模板。

## 出版物模板的標識 {#identification-of-a-publication-template}

出版物範本由其名稱和命名空間來識別。

樣式表的標識鍵是由命名空間和名稱以冒號分隔的字串組成；例如： **自訂：電子報**。

>[!NOTE]
>
>在實踐中，建議對架構、表單和發佈模板使用相同的鍵。

## 建立和配置模板 {#creating-and-configuring-the-template}

依預設，出版物範本會儲存在節 **[!UICONTROL Administration > Configuration > Publication templates]** 點中。 若要建立新範本，請按一 **[!UICONTROL New]** 下範本清單上方的按鈕。

要配置發佈模板，請填入模板的名稱（即由名稱和名稱空間組成的標識鍵）、其標籤、資料模式及其連結的輸入表單。

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>每當根據此出版物範本建立內容時，標籤就會出現。

「檢 **查狀態以驗證內容產生** 」選項強制檢查內容例項的「已驗證」狀態，以授權檔案產生。 For more on this, refer to [Publication](#publication).

必須為每個輸出文檔添加一個轉換模板。 您可以根據需要建立任意數量的轉換模板。

該 **[!UICONTROL Name of template]** 欄位是一個自由標籤，用於描述輸出時的渲染類型。 對於每個轉換模板，都可以在頁籤中使用出版物設定。

### 演算 {#rendering}

選 **[!UICONTROL Rendering]** 擇：

* 用於投影輸出文檔的渲染類型：XSL樣式表或JavaScript範本，
* 輸出文檔的格式：HTML、文字、XML或RTF、
* 包含構造資料的模板，即要使用的樣式表或JavaScript模板。

### 出版物 {#publication}

發佈包括以檔案形式生成輸出文檔（如果選擇的類型為） **[!UICONTROL File]**。

![](assets/d_ncs_content_model2.png)

可使用下列出版物選項：

* 輸出檔案編碼字元集可通過欄位強制 **[!UICONTROL Encoding]** 執行。 預設情況下使用拉丁文1(1252)字元集。
* 此選 **[!UICONTROL Multi-file generation]** 項可激活特殊的文檔發佈模式。 此選項包括在輸出文檔的每個頁面的開頭填充分區標籤。 產生內容會針對每個填入的分區標籤產生檔案。 此模式用於從內容區塊產生迷你網站。 for more on this, refer to [Multi-file generation](#multi-file-generation).
* 該 **[!UICONTROL Location]** 欄位包含輸出檔案的名稱。 名稱可由變陣列成，以產生自動檔案名稱。

   變數會填入下列格式：**`$(<xpath>)`，其中 `<xpath>` 是發佈模板資料架構的欄位的路徑。

   檔案的名稱可由日期類型欄位組成。 若要正確格式化此欄位，請使 **用$date-format** 函式，使用欄位路徑和輸出格式作為參數。

   預設情況下，檔案名的構造格式使用「@name」和「@date」欄位上的變數：

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   產生的檔案名稱如下所示：ct_news12_20110901.htm。

   >[!NOTE]
   >
   >如需內容產生的詳細資訊，請參 [閱建立內容例項](../../delivery/using/using-a-content-template.md#creating-a-content-instance)。

### 傳送 {#delivery}

此標籤可讓您選取藍本，以便直接在內容上啟動傳送。 電子郵件的內容會根據輸出格式（HTML或文字）自動填入。

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>如需根據內容建立傳送的範例，請參閱「傳送 [內容例項」](../../delivery/using/using-a-content-template.md#delivering-a-content-instance)。

### 匯整器 {#aggregator}

從指令碼或查詢清單匯整資料，可讓您以內容資料豐富XML檔案。 其目的是補充連結引用的某些資訊或從資料庫中添加元素。

### 多檔案產生 {#multi-file-generation}

若要啟動多個檔案產生，請選取 **[!UICONTROL Multi-file generation]** 出版物模型中的選項。 此選項可讓您在樣式表中指定輸出文檔的每個頁面開始的分區標籤。 內容的產生將為遇到的每個分區標籤生成一個檔案。

要整合在樣式表中的分區標籤如下：

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** 其中 **`<name_of_file>`** 是要產生之頁面的檔案名稱。

**範例：**使用「cus:book」架構產生多個檔案。

其原則是產生一個列出章節的首頁面，並可在外部頁面中顯示章節的詳細資訊。

![](assets/d_ncs_content_chunk.png)

對應的樣式表(&quot;cus:book.xsl&quot;)如下：

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

需要第二個樣式表(&quot;cus:chapter.xsl&quot;)才能生成各章的詳細資訊：

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

分區標籤會填入至要包含在檔案中以產生的頁面的開頭處。

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

檔案名稱是使用 **包含發佈路徑和的$(path)** 變數來建構的 **`<xsl:value-of select="@id" />`**，這些變數會符合輸入檔案中章節的識別碼。

出版物模型必須填入兩個樣式表&quot;cus:book.xsl&quot;和&quot;cus:chapter.xsl&quot;。

在章 **[!UICONTROL Multi-file generation]** 節轉換模型上，該選項必須處於活動狀態：

![](assets/d_ncs_content_chunk2.png)

此 **[!UICONTROL Location]** 欄位不用於產生多個檔案，但您仍必須填入此欄位，以避免發佈時發生錯誤。
