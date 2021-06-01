---
product: campaign
title: 透過工作流程自動化
description: 透過工作流程自動化
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: bc6ebf5d-cc21-4750-9713-2bf259e7d6bf
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 1%

---

# 使用工作流程自動化{#automating-via-workflows}

## 內容管理活動{#content-management-activity}

使用透過Adobe Campaign用戶端介面設定的工作流程，可自動建立、編輯和發佈內容。

**內容管理**&#x200B;活動通過工作流圖的&#x200B;**[!UICONTROL Tools]**&#x200B;工具欄訪問。

活動屬性可劃分為四個步驟：

* **[!UICONTROL Content]** :可讓您輸入現有內容或建立內容，
* **[!UICONTROL Update content]** :可讓您修改內容的主題，或透過XML資料流量更新內容，
* **[!UICONTROL Action to execute]** :可讓您儲存或產生內容，
* **[!UICONTROL Transition]** :可讓您選擇是否要產生輸出轉變，並為其命名。

![](assets/d_ncs_content_wf.png)

### 內容 {#content}

* **由轉變指定**

   要使用的內容是先前建立的。 程式會與傳入事件所傳播的內容例項有關。 內容識別碼是透過事件的「contentId」變數來存取。

* **明確**

   可讓您選擇先前建立的內容。

* **由指令碼計算**

   根據JavaScript範本選取內容例項。 要評估的程式碼可讓您擷取內容識別碼。

* **新增，透過發佈範本建立**

   透過出版物範本建立新內容。 內容例項會儲存在填入的「字串」資料夾中。

### 更新內容{#update-the-content}

* **主旨**

   可讓您在發佈時修改傳送動作的主旨。

* **從XML摘要存取資料**

   內容從外部來源的XML摘要更新。 必須輸入URL，資料才能下載。

   XSL樣式表可用於轉換傳入的XML資料。

### 要執行{#action-to-execute}的操作

* **儲存**

   保存已建立或已修改的內容。 儲存內容的識別碼會傳播至傳出事件的「contentId」變數。

* **產生**

   為每個具有「檔案」類型發佈的轉換模板生成輸出檔案。 系統會為每個產生的檔案啟用傳出轉變，並使用下列參數：「contentId」變數中儲存的內容識別碼，以及「filename」變數中的檔案名稱。

### 轉變 {#transition}

**產生輸出轉變**&#x200B;選項可讓您將輸出轉變新增至&#x200B;**[!UICONTROL Content management]**&#x200B;活動，以將新活動連結至工作流程執行。 核取此選項後，輸入轉變的標籤。

## 範例 {#examples}

### {#automating-content-creation-and-delivery}自動建立和傳送內容

下列範例會自動建立和傳送內容區塊。

![](assets/d_ncs_content_workflow2.png)

內容是透過「內容管理」活動設定：

![](assets/d_ncs_content_workflow3.png)

會透過發佈模型和內容字串資料夾建立新內容例項。

在我們的範例中，已超載傳送主體。 這將考慮在內，而不是&#x200B;**[!UICONTROL Delivery]**&#x200B;範本中輸入的。

來自輸入URL的XML摘要會自動填入內容：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

資料格式與在發佈範本中輸入的資料架構不匹配（在本例中為&#x200B;**cus:book**）;**`<section>`**&#x200B;元素必須取代為&#x200B;**`<chapter>`**&#x200B;元素。 我們需要應用「cus:book-workflow.xsl」樣式表以進行必要的更改。

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

活動的最終動作是儲存內容例項並繼續執行下一個任務。

透過&#x200B;**Query**&#x200B;活動執行定位。

已新增&#x200B;**AND-join**&#x200B;活動，以確保只有在目標查詢和內容更新完成後，傳送才會開始。

傳遞動作是透過&#x200B;**傳遞**&#x200B;活動設定：

![](assets/d_ncs_content_workflow4.png)

系統會根據範本建立新的傳送動作。

活動的傳送範本用於選取發佈範本的轉換範本。 內容產生會考慮所有不含傳送範本的HTML和文字範本，或與活動參照相同範本的範本。

要傳送的目標是透過傳入事件輸入。

傳遞內容會透過傳入事件填入。

完成活動的最後一個步驟是準備並啟動傳送。

### 建立內容以供稍後發佈{#creating-content-and-publishing-it-later}

此範例會建立內容區塊，並在特定時間延遲後啟動檔案發佈。

![](assets/d_ncs_content_workflow5.png)

第一個&#x200B;**內容管理**&#x200B;任務建立內容實例。

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>必須在轉換模板窗口的&#x200B;**[!UICONTROL Publication]**&#x200B;頁簽中填入要生成的目標的位置。

會新增等候活動，以暫停下一個轉變一週。

![](assets/d_ncs_content_workflow7.png)

在此時段內手動輸入內容。

下一個任務將啟動內容生成。

![](assets/d_ncs_content_workflow8.png)

要發佈的內容是透過傳入的轉變輸入。

最終操作是強制發佈目錄來生成此內容。

**JavaScript代碼**&#x200B;活動會擷取每個產生檔案的完整名稱。

![](assets/d_ncs_content_workflow9.png)

### 建立傳送及其內容{#creating-the-delivery-and-its-content}

此範例使用與第一個範例相同的概念，而只有它會在第一個步驟中建立傳送動作。

![](assets/d_ncs_content_workflow10.png)

第一個&#x200B;**建立傳送**&#x200B;任務會建立傳送動作。

分支活動可讓您同時啟動目標計算和內容例項的建立。

執行任務後，AND-join框將激活&#x200B;**Delivery**&#x200B;任務，以啟動先前建立的內容和目標傳送。

![](assets/d_ncs_content_workflow11.png)

要開始的傳送動作會透過轉變填入。

要傳送的目標是透過傳入事件輸入。

傳遞內容會透過傳入事件填入。

活動的最終動作是準備並啟動傳送。

### 從FTP匯入內容{#importing-content-from-ftp}

如果您的傳送內容以FTP或SFTP伺服器上的HTML檔案提供，您便可輕鬆將此內容載入Adobe Campaign傳送。 請參閱[此範例](../../workflow/using/loading-delivery-content.md)。

### 從Amazon Simple Storage Service(S3)連接器{#importing-content-from-amazon-simple-storage-service--s3--connector}匯入內容

如果您的傳送內容位於Amazon簡單儲存服務(S3)貯體上，您便可輕鬆將此內容載入Adobe Campaign傳送中。 請參閱[此範例](../../workflow/using/loading-delivery-content.md)。

## 半自動更新{#semi-automatic-update}

內容資料可在「半自動」模式中更新。 資料會透過URL從XML摘要中復原。

資料恢復的激活是通過輸入表單手動執行的。

其目的是在表單中聲明&#x200B;**editBtn**&#x200B;類型&#x200B;**`<input>`**&#x200B;欄位。 此控制項包含編輯區域和啟動處理的按鈕。

編輯區域可讓您填入變數資料，以建構要擷取之資料的XML摘要。

按鈕會執行填入&#x200B;**`<input>`**&#x200B;標籤下的&#x200B;**GetAndTransform** SOAP方法。

表格中的控制聲明如下：

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

必須在&#x200B;**`<input>`**&#x200B;標籤的&#x200B;**`<enter>`**&#x200B;元素下宣告&#x200B;**GetAndTransform**&#x200B;方法。 此標籤將作為從動態構建的表達式中恢復XML資料的URL的參數。 函式的第二個參數是可選的，當傳入的XML資料與內容的格式不同時，將引用用於中間轉換的樣式表。

輸出會根據最後一個參數中輸入的路徑更新內容。

**範例**:為了說明此範例，我們從「cus:book」架構開始。

新增半自動更新編輯控制輸入表單：

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

編輯區域可讓您輸入要擷取的檔案名稱。 URL會根據此名稱建構，例如：https://myserver.adobe.com/incomin/data.xml

要擷取的資料格式與工作流程自動化的範例1相同。 我們將使用本示例中所示的「cus:book-workflow.xsl」樣式表。

作業執行結果會從路徑「。」更新內容實例。
