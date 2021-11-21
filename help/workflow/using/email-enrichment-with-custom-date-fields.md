---
product: campaign
title: 使用自訂日期欄位擴充電子郵件
description: 了解如何使用自訂日期欄位豐富電子郵件內容
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---

# 使用自訂日期欄位擴充電子郵件{#email-enrichment-with-custom-date-fields}

![](../../assets/common.svg)

在此範例中，我們想傳送包含自訂資料欄位的電子郵件給將於本月慶祝生日的收件者。 電子郵件將包含優惠券，其有效期限為生日前後一週。

我們需要將目標鎖定於本月將以 **[!UICONTROL Split]** 活動。 然後，使用 **[!UICONTROL Enrichment]** 活動中，自訂資料欄位將作為客戶特殊優惠方案電子郵件中的有效日期。

![](assets/uc_enrichment.png)

若要建立此範例，請套用下列步驟：

1. 在 **[!UICONTROL Targeting and workflows]** 標籤，拖放 **[!UICONTROL Read list]** 活動來定位收件者清單。
1. 可根據此處定義的選項和參數，顯式指定要處理的清單，由指令碼計算或動態地本地化。

   ![](assets/uc_enrichment_1.png)

1. 新增 **[!UICONTROL Split]** 活動可區分本月要慶祝生日的收件者與其他收件者。
1. 若要分割清單，請在 **[!UICONTROL Filtering of selected records]** 類別，選擇 **[!UICONTROL Add a filtering condition on the inbound population]**. 然後，按一下 **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. 選擇 **[!UICONTROL Filtering conditions]** 然後按一下 **[!UICONTROL Edit expression]** 按鈕，以篩選收件者生日的月份。

   ![](assets/uc_enrichment_3.png)

1. 按一下 **[!UICONTROL Advanced Selection]** then **[!UICONTROL Edit the formula using an expression]** 並新增下列運算式：月(@birthDate)。
1. 在 **[!UICONTROL Operator]** 欄，選取 **[!UICONTROL equal to]**.
1. 借由新增 **[!UICONTROL Value]** 當前日期的月份：Month(GetDate())。

   這將查詢生日月份與當月相對應的收件者。

   ![](assets/uc_enrichment_4.png)

1. 按一下 **[!UICONTROL Finish]**。然後，在 **[!UICONTROL General]** 標籤 **[!UICONTROL Split]** 活動，按一下 **[!UICONTROL Generate complement]** 在 **[!UICONTROL Results]** 類別。

   使用 **[!UICONTROL Complement]** 結果，您可以新增傳送活動或更新清單。 在此，我們剛新增 **[!UICONTROL End]** 活動。

   ![](assets/uc_enrichment_6.png)

您現在需要設定 **[!UICONTROL Enrichment]** 活動：

1. 新增 **[!UICONTROL Enrichment]** 活動，以新增自訂日期欄位。

   ![](assets/uc_enrichment_7.png)

1. 開啟 **[!UICONTROL Enrichment]** 活動。 在 **[!UICONTROL Complementary information]** 類別，按一下 **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. 選擇 **[!UICONTROL Data linked to the filtering dimension]** then **[!UICONTROL Data of the filtering dimension]**.
1. 按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/uc_enrichment_9.png)

1. 新增 **[!UICONTROL Label]**. 然後，在 **[!UICONTROL Expression]** 欄，按一下 **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. 首先，我們需要將出生日期前一週作為 **有效開始日期** 與下列 **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. 然後，若要建立自訂日期欄位 **有效結束日期** 目標是出生日期之後的一週，您需要新增 **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   您可以將標籤新增至運算式。

   ![](assets/uc_enrichment_12.png)

1. 按一下 **[!UICONTROL Ok]**。您的擴充功能現已準備就緒。

在 **[!UICONTROL Enrichment]** 活動，您可以新增傳送。 在此情況下，我們新增了電子郵件傳送，以傳送特殊優惠方案給收件者，其有效日期可讓客戶在本月慶祝他們的生日。

1. 拖放 **[!UICONTROL Email delivery]** 在 **[!UICONTROL Enrichment]** 活動。

   ![](assets/uc_enrichment_15.png)

1. 按兩下您的 **[!UICONTROL Email delivery]** 活動，開始個人化您的傳送。
1. 新增 **[!UICONTROL Label]** 傳送，按一下 **[!UICONTROL Continue]**.
1. 按一下 **[!UICONTROL Save]** 來建立電子郵件傳送。
1. 簽入 **[!UICONTROL Approval]** 電子郵件傳送的索引標籤 **[!UICONTROL Properties]** the **[!UICONTROL Confirm delivery before sending option]** 已勾選。

   然後，啟動您的工作流程，以使用目標資訊豐富您的出站轉變。

   ![](assets/uc_enrichment_18.png)

您現在可以開始使用在 **[!UICONTROL Enrichment]** 活動。

1. 按兩下您的 **[!UICONTROL Email delivery]** 活動。
1. 將您的目標擴充功能新增至電子郵件。 它應位於下列運算式內，以設定有效日期的格式：

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. 按一下![](assets/uc_enrichment_16.png)。選擇 **[!UICONTROL Target extension]** 之後，先前建立的自訂有效日期會搭配 **[!UICONTROL Enrichment]** 活動，將擴充功能新增至formatDate運算式。

   ![](assets/uc_enrichment_19.png)

1. 視需要設定您的電子郵件內容。

   ![](assets/uc_enrichment_17.png)

1. 預覽您的電子郵件，以檢查自訂日期欄位是否已正確設定

   ![](assets/uc_enrichment_20.png)

您的電子郵件現已準備就緒。 您可以開始傳送校樣並確認傳送內容，以傳送生日電子郵件。
