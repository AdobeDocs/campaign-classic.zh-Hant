---
solution: Campaign Classic
product: campaign
title: 透過工作流程自動化
description: 透過工作流程自動化
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 0%

---


# 使用工作流程自動化{#automating-via-workflows}

## 內容管理活動{#content-management-activity}

使用透過Adobe Campaign用戶端介面設定的工作流程，可自動建立、編輯和發佈內容。

**內容管理**&#x200B;活動可通過工作流圖的&#x200B;**[!UICONTROL Tools]**&#x200B;工具欄訪問。

活動屬性分為四個步驟：

* **[!UICONTROL Content]** :可讓您輸入現有內容或建立內容，
* **[!UICONTROL Update content]** :可讓您修改內容的主題或透過XML資料流量更新內容，
* **[!UICONTROL Action to execute]** :可讓您儲存或產生內容，
* **[!UICONTROL Transition]** :可讓您選擇是否要產生輸出轉換，並為其指定名稱。

![](assets/d_ncs_content_wf.png)

### 內容{#content}

* **由轉換指定**

   要使用的內容是先前建立的。 進程將涉及傳入事件所傳播的內容實例。 內容識別碼是透過事件的&quot;contentId&quot;變數存取。

* **明確**

   可讓您選擇先前建立的內容。

* **由指令碼計算**

   根據JavaScript範本選擇內容例項。 要評估的程式碼可讓您擷取內容識別碼。

* **新增，透過出版物範本建立**

   透過出版物範本建立新內容。 內容例項將儲存在填入的「字串」檔案夾中。

### 更新內容{#update-the-content}

* **主旨**

   可讓您在發佈時修改傳送動作的主題。

* **從XML饋送存取資料**

   從外部來源的XML饋送更新內容。 必須輸入URL，才能下載資料。

   XSL樣式表可用於轉換傳入的XML資料。

### 執行{#action-to-execute}的動作

* **儲存**

   儲存已建立或已修改的內容。 儲存內容的識別碼會傳播至傳出事件的「contentId」變數中。

* **產生**

   為每個具有「檔案」類型發佈的轉換模板生成輸出檔案。 系統會針對每個產生的檔案啟用傳出轉場，並使用以下參數：儲存在&quot;contentId&quot;變數中的內容識別碼，以及&quot;filename&quot;變數中的檔案名稱。

### 轉變 {#transition}

**產生輸出轉變**&#x200B;選項可讓您新增輸出轉變至&#x200B;**[!UICONTROL Content management]**&#x200B;活動，以連結新活動與工作流程執行。 勾選此選項後，輸入轉場的標籤。

## 範例 {#examples}

### 自動化內容建立和傳送{#automating-content-creation-and-delivery}

以下範例會自動建立和傳送內容區塊。

![](assets/d_ncs_content_workflow2.png)

內容是透過「內容管理」活動來設定：

![](assets/d_ncs_content_workflow3.png)

透過出版物模型和內容字串資料夾建立新的內容例項。

在我們的例子中，我們超載了交貨對象。 它將被考慮在內，而不是在&#x200B;**[!UICONTROL Delivery]**&#x200B;模板中輸入的。

內容會由輸入之URL的XML摘要自動填入：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

資料格式與在出版物模板中輸入的資料模式不匹配（在本例中為&#x200B;**cus:book**）;**`<section>`**&#x200B;元素必須以&#x200B;**`<chapter>`**&#x200B;元素取代。 我們需要套用&quot;cus:book-workflow.xsl&quot;樣式表，以進行必要的變更。

使用的XSLT樣式表的原始碼：

```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
 <xsl:output indent="yes" method="xml"  encoding="ISO-8859-1"/>

 <xsl:template match="text()|@*"/>

  <xsl:template match="*">
    <xsl:variable name="element.name" select="name(.)"/>
    <xsl:element name="{$element.name}">
      <xsl:copy-of select="text()|@*"/>
      <xsl:apply-templates/>
    </xsl:element>
  </xsl:template>

  <xsl:template match="book">
  <book name="test">
     <xsl:apply-templates/>
    <book>
 </xsl:template>

  <xsl:template match="section">
    <chapter>
      <xsl:for-each select="@*">
        <xsl:copy-of select="."/>
      </xsl:for-each>
       <xsl:apply-templates/>
    </chapter>
  </xsl:template>
  
</xsl:stylesheet>
```

活動的最終動作是儲存內容例項並繼續下一個工作。

定位是透過&#x200B;**Query**&#x200B;活動執行。

已新增&#x200B;**AND-join**&#x200B;活動，以確保只有在目標查詢和內容更新完成後，才啟動傳送。

傳送動作是透過&#x200B;**傳送**&#x200B;活動來設定：

![](assets/d_ncs_content_workflow4.png)

根據範本建立新的傳送動作。

活動的交付模板用於選擇出版物模板的轉換模板。 內容產生會考慮所有HTML和文字範本，而不需傳送範本，或與活動相同範本所參照的範本。

要傳送的目標是通過傳入事件輸入的。

傳送內容會透過傳入事件填入。

完成活動的最後一個步驟是準備然後啟動傳送。

### 建立內容以供稍後發佈{#creating-content-and-publishing-it-later}

此範例會建立內容區塊，並在特定時間延遲後啟動檔案發佈。

![](assets/d_ncs_content_workflow5.png)

第一個&#x200B;**內容管理**&#x200B;任務建立內容實例。

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>必須在轉換模板窗口的&#x200B;**[!UICONTROL Publication]**&#x200B;頁籤中填入要生成的目標位置。

會新增等待活動，以暫停下一個轉場一週。

![](assets/d_ncs_content_workflow7.png)

此時段內會手動輸入內容。

下一個任務將啟動內容生成。

![](assets/d_ncs_content_workflow8.png)

要發佈的內容是透過傳入的轉場輸入。

最後的動作是強制發佈目錄來產生此內容。

**JavaScript代碼**&#x200B;活動會擷取每個產生檔案的完整名稱。

![](assets/d_ncs_content_workflow9.png)

### 建立傳送及其內容{#creating-the-delivery-and-its-content}

此範例使用與第一個範例相同的概念，只會在第一個步驟中建立傳送動作。

![](assets/d_ncs_content_workflow10.png)

第一個&#x200B;**建立交付**&#x200B;任務將建立交付操作。

fork活動可讓您並行啟動目標計算和內容實例的建立。

執行完任務後，AND-join框將激活&#x200B;**Delivery**&#x200B;任務，以啟動以前建立的內容和目標傳送。

![](assets/d_ncs_content_workflow11.png)

要啟動的傳送動作會透過轉場填入。

要傳送的目標是通過傳入事件輸入的。

傳送內容會透過傳入事件填入。

活動的最終動作是準備並啟動傳送。

### 從FTP {#importing-content-from-ftp}匯入內容

如果您的傳送內容位於FTP或SFTP伺服器上的HTML檔案中，您就可輕鬆將此內容載入Adobe Campaign傳送。 請參閱[此示例](../../workflow/using/loading-delivery-content.md)。

### 從Amazon簡單儲存服務(S3)連接器{#importing-content-from-amazon-simple-storage-service--s3--connector}導入內容

如果您的傳送內容位於Amazon簡單儲存服務(S3)儲存區，您可輕鬆將此內容載入Adobe Campaign傳送。 請參閱[此示例](../../workflow/using/loading-delivery-content.md)。

## 半自動更新{#semi-automatic-update}

內容資料可在「半自動」模式中更新。 資料會透過URL從XML饋送中復原。

資料恢復的激活是通過輸入表單手動執行的。

其目的是聲明&#x200B;**editBtn**&#x200B;類型&#x200B;**`<input>`**&#x200B;的欄位。 該控制包括編輯區和啟動處理的按鈕。

編輯區可讓您填入變數資料，用以建構要擷取之資料之XML饋送的URL。

按鈕會執行填入&#x200B;**`<input>`**&#x200B;標籤下的&#x200B;**GetAndTransform** SOAP方法。

形式中的控制聲明如下：

```
<input type="editbtn" xpath="<path>">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="<url>" type="string"/>
      <param exprIn="'xtk:xslt|<style sheet>'" type="string"/>
      <param type="DOMElement" xpathOut="<output path>"/>
    </soapCall>
  </enter>
</input>
```

**GetAndTransform**&#x200B;方法必須在&#x200B;**`<input>`**&#x200B;標籤的&#x200B;**`<enter>`**&#x200B;元素下宣告。 此標籤會作為從動態建構的運算式中恢復XML資料的URL參數。 函式的第二個參數是可選的，當傳入的XML資料與內容格式不同時，引用用於中間轉換的樣式表。

輸出會根據最後一個參數中輸入的路徑更新內容。

**範例**:為了說明此範例，我們從&quot;cus:book&quot;架構開始。

添加了半自動更新編輯控制輸入表單：

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://myserver.adobe.com/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

編輯區域可讓您輸入要檢索的檔案的名稱。 URL是根據此名稱建構，例如：https://myserver.adobe.com/incomin/data.xml

要擷取的資料格式與工作流程自動化範例1中的格式相同。 我們將使用此範例中顯示的「cus:book-workflow.xsl」樣式表。

作業執行的結果會從路徑&#39;.&#39;更新內容例項。
