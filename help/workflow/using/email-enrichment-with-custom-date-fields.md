---
solution: Campaign Classic
product: campaign
title: 使用自訂日期欄位擴充電子郵件
description: 瞭解如何透過自訂日期欄位豐富電子郵件內容
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# 使用自訂日期欄位擴充電子郵件{#email-enrichment-with-custom-date-fields}

在此範例中，我們想傳送包含自訂資料欄位的電子郵件給將於本月過生日的收件者。 電子郵件將包含一週前後有效的抵用券。

我們需要從清單中鎖定本月會以&#x200B;**[!UICONTROL Split]**&#x200B;活動慶祝生日的收件者。 然後，使用&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動，自訂資料欄位將作為客戶特別優惠電子郵件的有效日期。

![](assets/uc_enrichment.png)

若要建立此範例，請套用下列步驟：

1. 在促銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中，拖放&#x200B;**[!UICONTROL Read list]**&#x200B;活動以定位收件者清單。
1. 可根據此處定義的選項和參數，明確指定要處理的清單，由指令碼計算或動態本地化。

   ![](assets/uc_enrichment_1.png)

1. 新增&#x200B;**[!UICONTROL Split]**&#x200B;活動，以區分本月將慶祝生日的收件者與其他收件者。
1. 要拆分清單，請在&#x200B;**[!UICONTROL Filtering of selected records]**&#x200B;類別中選擇&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**。 然後，按一下&#x200B;**[!UICONTROL Edit]**。

   ![](assets/uc_enrichment_2.png)

1. 選擇&#x200B;**[!UICONTROL Filtering conditions]**，然後按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;按鈕以篩選收件者生日的月份。

   ![](assets/uc_enrichment_3.png)

1. 按一下&#x200B;**[!UICONTROL Advanced Selection]**，然後按一下&#x200B;**[!UICONTROL Edit the formula using an expression]**&#x200B;並新增下列運算式：Month(@borthDate)。
1. 在&#x200B;**[!UICONTROL Operator]**&#x200B;欄中，選擇&#x200B;**[!UICONTROL equal to]**。
1. 進一步篩選條件，新增目前日期的&#x200B;**[!UICONTROL Value]**&#x200B;月份：Month(GetDate())。

   這將查詢其生日月份與當月對應的收件者。

   ![](assets/uc_enrichment_4.png)

1. 按一下 **[!UICONTROL Finish]**。然後，在&#x200B;**[!UICONTROL Split]**&#x200B;活動的&#x200B;**[!UICONTROL General]**&#x200B;標籤中，按一下&#x200B;**[!UICONTROL Results]**&#x200B;類別中的&#x200B;**[!UICONTROL Generate complement]**。

   使用&#x200B;**[!UICONTROL Complement]**&#x200B;結果，您可以新增傳送活動或更新清單。 在這裡，我們新增了&#x200B;**[!UICONTROL End]**&#x200B;活動。

   ![](assets/uc_enrichment_6.png)

您現在需要設定&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動：

1. 在子集後添加&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動以添加自定義日期欄位。

   ![](assets/uc_enrichment_7.png)

1. 開啟您的&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動。 在&#x200B;**[!UICONTROL Complementary information]**&#x200B;類別中，按一下&#x200B;**[!UICONTROL Add data]**。

   ![](assets/uc_enrichment_8.png)

1. 依次選擇&#x200B;**[!UICONTROL Data linked to the filtering dimension]**&#x200B;和&#x200B;**[!UICONTROL Data of the filtering dimension]**。
1. 按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/uc_enrichment_9.png)

1. 新增&#x200B;**[!UICONTROL Label]**。 然後，在&#x200B;**[!UICONTROL Expression]**&#x200B;欄中，按一下&#x200B;**[!UICONTROL Edit expression]**。

   ![](assets/uc_enrichment_10.png)

1. 首先，我們需要將出生日期前的一週定位為&#x200B;**有效開始日期**&#x200B;並包含以下&#x200B;**[!UICONTROL Expression]**:`SubDays([target/@birthDate], 7)`。

   ![](assets/uc_enrichment_11.png)

1. 然後，若要建立自訂日期欄位&#x200B;**有效結束日期**，以定位出生日期後的一週，您必須新增&#x200B;**[!UICONTROL Expression]**:`AddDays([target/@birthDate], 7)`。

   您可以新增標籤至運算式。

   ![](assets/uc_enrichment_12.png)

1. 按一下 **[!UICONTROL Ok]**。你的濃縮活動已經準備好了。

在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動後，您可以新增傳送。 在這種情況下，我們新增了電子郵件傳送，以傳送特別優惠給收件者，其有效日期會寄送給本月過生日的客戶。

1. 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動後拖放&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動。

   ![](assets/uc_enrichment_15.png)

1. 連按兩下您的&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動，開始個人化傳送內容。
1. 將&#x200B;**[!UICONTROL Label]**&#x200B;新增至傳送，然後按一下&#x200B;**[!UICONTROL Continue]**。
1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以建立您的電子郵件傳送。
1. 請登入已勾選&#x200B;**[!UICONTROL Confirm delivery before sending option]**&#x200B;的電子郵件傳送&#x200B;**[!UICONTROL Properties]**&#x200B;的&#x200B;**[!UICONTROL Approval]**&#x200B;標籤。

   然後，開始您的工作流程，以目標資訊豐富您的對外轉場。

   ![](assets/uc_enrichment_18.png)

您現在可以開始設計電子郵件傳送，並使用在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動中建立的自訂日期欄位。

1. 連按兩下您的&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動。
1. 將您的目標擴充功能新增至電子郵件。 它應位於下列運算式中，以設定有效日期的格式：

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. 按一下 ![](assets/uc_enrichment_16.png)。選擇&#x200B;**[!UICONTROL Target extension]**，然後選擇先前建立的具有&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動的自定義有效日期，以將副檔名添加到formatDate表達式中。

   ![](assets/uc_enrichment_19.png)

1. 視需要設定您的電子郵件內容。

   ![](assets/uc_enrichment_17.png)

1. 預覽您的電子郵件以檢查您的自訂日期欄位是否已正確設定

   ![](assets/uc_enrichment_20.png)

您的電子郵件現已準備就緒。 您可以開始傳送校樣，並確認寄送的是生日電子郵件。
