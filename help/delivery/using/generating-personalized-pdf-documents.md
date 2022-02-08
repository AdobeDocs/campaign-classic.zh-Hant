---
product: campaign
title: 產生個人化 PDF 文件
description: 瞭解如何生成個性化PDF文檔
feature: Personalization
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---

# 產生個人化 PDF 文件{#generating-personalized-pdf-documents}

![](../../assets/common.svg)

## 關於變數PDF文檔 {#about-variable-pdf-documents}

Adobe Campaign允許您為來自LibreOffice或MicrosoftWord文檔的電子郵件附件生成可變PDF文檔。

支援以下擴展：&quot;。docx&quot;、&quot;。doc&quot;和&quot;。odt&quot;。

要個性化您的文檔，可以使用與電子郵件個性化功能相同的JavaScript功能。

您需要激活 **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** 的雙曲餘切值。 將檔案附加到傳遞電子郵件時，此選項可訪問。 有關附加計算檔案的詳細資訊，請參閱 [附加檔案](attaching-files.md) 的子菜單。

發票題頭個性化實例：

![](assets/s_ncs_pdf_simple.png)

要通過URL生成動態表或包含影像，需要遵循特定的流程。

## 生成動態表 {#generating-dynamic-tables}

生成動態表的過程如下：

* 建立包含三行和所需列的表，然後配置其佈局（邊框等）。
* 將游標置於表上，然後按一下 **[!UICONTROL Table > Table properties]** 的子菜單。 轉到 **[!UICONTROL Table]** 頁籤，並輸入名稱 **NlJs表**。
* 在第一行的第一個單元格中，定義一個循環（例如，&quot;for&quot;），該循環允許對要在表中顯示的值進行迭代。
* 在表第二行的每個單元格中，插入返回要顯示的值的指令碼。
* 關閉表的第三行和最後一行中的循環。

   動態表定義示例：

   ![](assets/s_ncs_pdf_table.png)

## 插入外部影像 {#inserting-external-images}

例如，如果希望使用在收件人欄位中輸入URL的影像個性化文檔，則插入外部影像非常有用。

為此，您需要配置個性化塊，然後在附件中包括對個性化塊的調用。

**示例：根據收件人所在國家/地區插入個性化徽標**

**步驟1:建立附件：**

* 插入對個性化設定塊的調用： **&lt;%@ include view=&quot;blockname %>**。
* 將您的內容（無論是否個性化）插入檔案正文。

![](assets/s_ncs_open_office_blocdeperso.png)

**步驟2:建立個性化塊：**

* 轉到 **[!UICONTROL Resources > Campaign management > Personalization blocks]** 菜單。
* 建立新的「我的徽標」個性化塊，其中「我的徽標」為內部名稱。
* 按一下 **[!UICONTROL Advanced parameters...]** 連結，然後檢查 **[!UICONTROL "The content of the block is included in an attachment"]** 的雙曲餘切值。 這允許您將個性化塊的定義直接複製到OpenOffice檔案的內容中。

   ![](assets/s_ncs_pdf_bloc_option.png)

   您需要區分個性化塊中的兩種聲明類型：

   * 「開啟」和「關閉」雪佛蘭必須用轉義字元替換的個性化域的Adobe Campaign代碼（分別） `&lt;` 和 `&gt;`)。
   * 整個OpenOffice XML代碼將複製到OpenOffice文檔中。

在示例中，個性化塊如下所示：

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

根據收件國家/地區的不同，在連結到交貨的文檔中可以看到個性化：

![](assets/s_ncs_pdf_result.png)
