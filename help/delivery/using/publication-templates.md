---
product: campaign
title: 發佈範本
description: 發佈範本
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Templates
role: User
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
source-git-commit: a94774daa4005fe95066b85f921d9baa981b2a7c
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 1%

---

# 發佈範本{#publication-templates}

## 關於發佈範本 {#about-publication-templates}

發佈範本會參考發佈程式中使用的資源，即：

* 資料結構描述，
* 輸入表單，
* 每個輸出檔案的轉換範本。

## 出版物範本的識別 {#identification-of-a-publication-template}

發佈範本由其名稱和名稱空間識別。

樣式表的識別索引鍵是由名稱空間和名稱組成的字串，以冒號分隔；例如： **cus：newsletter**。

>[!NOTE]
>
>實際上，建議對結構描述、表單和發佈範本使用相同的索引鍵。

## 建立及設定範本 {#creating-and-configuring-the-template}

發佈範本預設會儲存在&#x200B;**[!UICONTROL Administration > Configuration > Publication templates]**&#x200B;節點中。 若要建立新範本，請按一下範本清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

若要設定發佈範本，請填入範本的名稱（即包含名稱和名稱空間的識別鍵）、其標籤、資料結構描述及其連結的輸入表單。

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>每次根據此出版物範本建立內容時，標籤都會出現。

**Check status to validate content generation**&#x200B;選項會強制檢查內容執行個體的「已驗證」狀態，以授權產生檔案。 如需詳細資訊，請參閱[出版物](#publication)。

必須為每個輸出檔案新增轉換範本。 您可以視需要建立儘可能多的轉換範本。

**[!UICONTROL Name of template]**&#x200B;欄位是自由標籤，說明輸出時的轉譯型別。 對於每個轉換範本，出版物設定都可在標籤中使用。

### 呈現 {#rendering}

**[!UICONTROL Rendering]**&#x200B;索引標籤，選擇：

* 用於投影輸出檔案的演算型別：XSL樣式表或JavaScript範本，
* 輸出檔案的格式：HTML、文字、XML或RTF、
* 包含建構資料的範本，即要使用的樣式表或JavaScript範本。

### 出版物 {#publication}

如果選取的型別是&#x200B;**[!UICONTROL File]**，則發行會以檔案形式產生輸出檔案。

![](assets/d_ncs_content_model2.png)

下列發佈選項可供使用：

* 可透過&#x200B;**[!UICONTROL Encoding]**&#x200B;欄位強制輸出檔案編碼字元集。 依預設，會使用拉丁文1 (1252)字元集。
* **[!UICONTROL Multi-file generation]**&#x200B;選項會啟動特殊檔案發佈模式。 此選項包括在輸出檔案每一頁的開頭填入分割標籤。 產生內容將會為每個填入的分割標籤產生檔案。 此模式用於從內容區塊產生迷你網站。 如需詳細資訊，請參閱[多重檔案產生](#multi-file-generation)。
* **[!UICONTROL Location]**&#x200B;欄位包含輸出檔案的名稱。 名稱可由變陣列成，以產生自動檔案名稱。

  變數會以下列格式填入： **`$(<xpath>)`**，其中&#x200B;**`<xpath>`**&#x200B;是發行集範本資料結構描述的欄位路徑。

  檔案名稱可由日期型別欄位組成。 若要正確格式化此欄位，請使用&#x200B;**$date-format**&#x200B;函式，將欄位路徑和輸出格式當作引數。

  依預設，檔案名稱的建構格式使用「@name」和「@date」欄位上的變數：

  ```xml
  ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
  ```

  產生的檔案名稱如下： ct_news12_20110901.htm。

  >[!NOTE]
  >
  >如需內容產生的詳細資訊，請參閱[建立內容執行個體](using-a-content-template.md#creating-a-content-instance)。

### 傳遞 {#delivery}

此索引標籤可讓您選取案例，以直接在內容上啟動傳送。 電子郵件內容將會根據輸出格式(HTML或文字)自動填入。

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>如需根據內容建立傳遞的範例，請參閱[傳遞內容執行個體](using-a-content-template.md#delivering-a-content-instance)。

### 彙總 {#aggregator}

從指令碼或查詢清單彙總資料，可讓您以內容資料擴充XML檔案。 其目的是要補充連結所參考的特定資訊，或從資料庫新增元素。

### 多檔案產生 {#multi-file-generation}

若要啟用多重檔案產生，請在發行集模型中選取&#x200B;**[!UICONTROL Multi-file generation]**&#x200B;選項。 此選項可讓您在樣式表中指定輸出檔案每一頁開頭的分割標籤。 產生內容時，會針對每個遇到的分割標籤產生檔案。

要整合在樣式表中的分割標籤如下：

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`**，其中&#x200B;**`<name_of_file>`**&#x200B;是要產生之頁面的檔案名稱。

**範例：**&#x200B;使用&quot;cus：book&quot;結構描述產生多個檔案。

其原理是產生一個列出章節的首頁面，並可能在外部頁面中顯示章節的詳細資訊。

![](assets/d_ncs_content_chunk.png)

對應的樣式表(「cus：book.xsl」)如下：

```xml
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

需要第二個樣式表(「cus：chapter.xsl」)來產生章節的詳細資訊：

```xml
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

分割標籤會填入在頁面的開頭處，以包含在要產生的檔案中。

```xml
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

檔案名稱是以&#x200B;**$（路徑）**&#x200B;變數建構的，該變數包含發佈路徑和&#x200B;**`<xsl:value-of select="@id" />`**，且符合輸入檔案中章節的識別碼。

出版物模型必須填入兩個樣式表「cus：book.xsl」和「cus：chapter.xsl」。

**[!UICONTROL Multi-file generation]**&#x200B;選項在章節轉換模型上必須是作用中：

![](assets/d_ncs_content_chunk2.png)

**[!UICONTROL Location]**&#x200B;欄位並未用於產生多個檔案，但您仍必須填入此欄位以避免發佈時發生錯誤。
