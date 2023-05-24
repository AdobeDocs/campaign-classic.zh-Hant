---
product: campaign
title: 產生個人化 PDF 文件
description: 瞭解如何產生個人化PDF檔案
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---

# 產生個人化 PDF 文件{#generating-personalized-pdf-documents}



## 關於變數PDF檔案 {#about-variable-pdf-documents}

Adobe Campaign可讓您從LibreOffice或Microsoft Word檔案產生電子郵件附件的變數PDF檔案。

支援下列擴充功能：「.docx」、「.doc」和「.odt」。

若要個人化您的檔案，可使用與電子郵件個人化相同的JavaScript功能。

您需要啟動 **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** 選項。 將檔案附加至傳遞電子郵件時，此選項可供存取。 有關附加計算檔案的詳細資訊，請參閱 [附加檔案](attaching-files.md) 區段。

商業發票表頭個人化的範例：

![](assets/s_ncs_pdf_simple.png)

若要透過URL產生動態表格或包含影像，您必須依照特定程式進行。

## 產生動態表格 {#generating-dynamic-tables}

產生動態表格的程式如下：

* 建立包含三行及所需欄數的表格，然後設定其版面配置（框線等）。
* 將游標放在表格上，然後按一下 **[!UICONTROL Table > Table properties]** 功能表。 前往 **[!UICONTROL Table]** 標籤並輸入開頭為的名稱 **NlJs表格**.
* 在第一行的第一個儲存格中，定義一個回圈（例如「for」），讓您在表格中顯示的值上執行反複運算。
* 在表格第二行的每個儲存格中，插入傳回要顯示的值的指令碼。
* 關閉表格第三行和最後一行的回圈。

   動態表格定義的範例：

   ![](assets/s_ncs_pdf_table.png)

## 插入外部影像 {#inserting-external-images}

例如，如果您想要個人化包含其URL已輸入收件者欄位中的影像的檔案，則插入外部影像會很有用。

若要這麼做，您需要設定個人化區塊，然後在附件中包含對個人化區塊的呼叫。

**範例：根據收件者的國家/地區插入個人化標誌**

**步驟1：建立附件：**

* 將呼叫插入個人化區塊： **&lt;%@包含view=&quot;blockname&quot; %>**.
* 將您的內容（無論是否個人化）插入檔案內文。

![](assets/s_ncs_open_office_blocdeperso.png)

**步驟2：建立個人化區塊：**

* 前往 **[!UICONTROL Resources > Campaign management > Personalization blocks]** Adobe Campaign主控台功能表。
* 以「My_Logo」作為內部名稱，建立新的「My Logo」個人化區塊。
* 按一下 **[!UICONTROL Advanced parameters...]** 連結，然後檢查 **[!UICONTROL "The content of the block is included in an attachment"]** 選項。 這可讓您直接將個人化區塊的定義複製到OpenOffice檔案的內容中。

   ![](assets/s_ncs_pdf_bloc_option.png)

   您需要在個人化區塊中區分兩種型別的宣告：

   * 個人化欄位的Adobe Campaign程式碼，其「開啟」和「關閉」V字元必須分別取代為逸出字元 `&lt;` 和 `&gt;`)。
   * 整個OpenOffice XML程式碼將會複製到OpenOffice檔案中。

在範例中，個人化區塊看起來像這樣：

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

根據收件者的國家/地區，個人化會顯示在連結至傳遞的檔案中：

![](assets/s_ncs_pdf_result.png)
