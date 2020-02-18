---
title: 使用自訂日期欄位擴充電子郵件
seo-title: 使用自訂日期欄位擴充電子郵件
description: 使用自訂日期欄位擴充電子郵件
seo-description: null
page-status-flag: never-activated
uuid: 6dd240b1-f995-4e12-90a5-55aeb584bcdc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9cb3be65-6652-47fa-b8a4-e088530aab4a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c4b5b7c44bbc74f56d3c70b93b131bba4d78c6f

---


# 使用自訂日期欄位擴充電子郵件{#email-enrichment-with-custom-date-fields}

在此範例中，我們想傳送包含自訂資料欄位的電子郵件給將於本月過生日的收件者。 電子郵件將包含一週前後有效的抵用券。

我們需要從清單中鎖定本月參加活動慶祝生日的收 **[!UICONTROL Split]** 件者。 然後，使用活 **[!UICONTROL Enrichment]** 動，自訂資料欄位將作為客戶特別優惠電子郵件的有效日期。

![](assets/uc_enrichment.png)

若要建立此範例，請套用下列步驟：

1. 在促銷 **[!UICONTROL Targeting and workflows]** 活動的標籤中，拖放活動以 **[!UICONTROL Read list]** 定位收件者清單。
1. 可根據此處定義的選項和參數，明確指定要處理的清單，由指令碼計算或動態本地化。

   ![](assets/uc_enrichment_1.png)

1. 新增活 **[!UICONTROL Split]** 動，以區分本月將慶祝生日的收件者與其他收件者。
1. 要拆分清單，請在類別中 **[!UICONTROL Filtering of selected records]** 選擇 **[!UICONTROL Add a filtering condition on the inbound population]**。 然後，按一下 **[!UICONTROL Edit]**。

   ![](assets/uc_enrichment_2.png)

1. 選 **[!UICONTROL Filtering conditions]** 取，然後按一 **[!UICONTROL Edit expression]** 下按鈕以篩選收件者生日的月份。

   ![](assets/uc_enrichment_3.png)

1. 按一 **[!UICONTROL Advanced Selection]** 下， **[!UICONTROL Edit the formula using an expression]** 然後新增下列運算式：Month(@borthDate)。
1. 在列中 **[!UICONTROL Operator]** ，選擇 **[!UICONTROL equal to]**。
1. 進一步篩選條件，方法是新增 **[!UICONTROL Value]** 目前日期的月份：Month(GetDate())。

   這將查詢其生日月份與當月對應的收件者。

   ![](assets/uc_enrichment_4.png)

1. 按一下 **[!UICONTROL Finish]**. 然後，在活動 **[!UICONTROL General]** 的標籤 **[!UICONTROL Split]** 中，按一下類 **[!UICONTROL Generate complement]** 別中的 **[!UICONTROL Results]** 。

   結果 **[!UICONTROL Complement]** 是，您可以新增傳送活動或更新清單。 在這裡，我們新增了活 **[!UICONTROL End]** 動。

   ![](assets/uc_enrichment_6.png)

您現在需要設定您的 **[!UICONTROL Enrichment]** 活動：

1. 在子集 **[!UICONTROL Enrichment]** 之後新增活動，以新增自訂日期欄位。

   ![](assets/uc_enrichment_7.png)

1. 開啟您的 **[!UICONTROL Enrichment]** 活動。 在類別 **[!UICONTROL Complementary information]** 中，按一下 **[!UICONTROL Add data]**。

   ![](assets/uc_enrichment_8.png)

1. 然後 **[!UICONTROL Data linked to the filtering dimension]** 選擇 **[!UICONTROL Data of the filtering dimension]**。
1. Click the **[!UICONTROL Add]** button.

   ![](assets/uc_enrichment_9.png)

1. 新增 **[!UICONTROL Label]**。 然後，在欄中 **[!UICONTROL Expression]** 按一下 **[!UICONTROL Edit expression]**。

   ![](assets/uc_enrichment_10.png)

1. 首先，我們需要將出生日期前的一週定位為有效 **性開始日期** ，並執行下列動作 **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`。

   ![](assets/uc_enrichment_11.png)

1. 然後，要建立自定義日期欄位 **Validity結束日期** （將定位在出生日期後的一週），您需要添加 **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`。

   您可以新增標籤至運算式。

   ![](assets/uc_enrichment_12.png)

1. 按一下 **[!UICONTROL Ok]**. 你的濃縮活動已經準備好了。

活動 **[!UICONTROL Enrichment]** 完成後，您可以新增傳送。 在這種情況下，我們新增了電子郵件傳送，以傳送特別優惠給收件者，其有效日期會寄送給本月過生日的客戶。

1. 在活動後拖 **[!UICONTROL Email delivery]** 放活 **[!UICONTROL Enrichment]** 動。

   ![](assets/uc_enrichment_15.png)

1. 連按兩下您的活 **[!UICONTROL Email delivery]** 動，即可開始個人化傳送內容。
1. 將新增 **[!UICONTROL Label]** 至傳送，然後按一下 **[!UICONTROL Continue]**。
1. 按一 **[!UICONTROL Save]** 下以建立您的電子郵件傳送。
1. 請登入已 **[!UICONTROL Approval]** 勾選之電子郵件傳送 **[!UICONTROL Properties]** 的標 **[!UICONTROL Confirm delivery before sending option]** 簽。

   然後，開始您的工作流程，以目標資訊豐富您的對外轉場。

   ![](assets/uc_enrichment_18.png)

您現在可以使用活動中建立的自訂日期欄位，開始設計電子郵件 **[!UICONTROL Enrichment]** 傳送。

1. 連按兩下您的 **[!UICONTROL Email delivery]** 活動。
1. 將您的目標擴充功能新增至電子郵件。 它應位於下列運算式中，以設定有效日期的格式：

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. 按一下 ![](assets/uc_enrichment_16.png) . 然後 **[!UICONTROL Target extension]** 選取先前建立的自訂有效日期與活 **[!UICONTROL Enrichment]** 動，以將副檔名新增至formatDate運算式。

   ![](assets/uc_enrichment_19.png)

1. 視需要設定您的電子郵件內容。

   ![](assets/uc_enrichment_17.png)

1. 預覽您的電子郵件以檢查您的自訂日期欄位是否已正確設定

   ![](assets/uc_enrichment_20.png)

您的電子郵件現已準備就緒。 您可以開始傳送校樣，並確認寄送的是生日電子郵件。
