---
product: campaign
title: 使用自訂日期欄位擴充電子郵件
description: 瞭解如何使用自定義日期欄位豐富電子郵件內容
feature: Workflows
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---

# 使用自訂日期欄位擴充電子郵件{#email-enrichment-with-custom-date-fields}

![](../../assets/v7-only.svg)

在此示例中，我們希望向將在本月慶祝生日的收件人發送包含自定義資料欄位的電子郵件。 電子郵件將包含一份優惠券，其有效期為一週，在他們生日之前和之後。

我們需要從一個清單中鎖定收件人，這些收件人本月將用一個 **[!UICONTROL Split]** 的子菜單。 然後，使用 **[!UICONTROL Enrichment]** 活動，自定義資料欄位將作為電子郵件中客戶特別優惠的有效日期。

![](assets/uc_enrichment.png)

要建立此示例，請應用以下步驟：

1. 在 **[!UICONTROL Targeting and workflows]** 頁籤，拖放 **[!UICONTROL Read list]** 活動，以鎖定收件人清單。
1. 可以根據此處定義的選項和參數顯式指定要處理的清單，由指令碼計算或動態本地化。

   ![](assets/uc_enrichment_1.png)

1. 添加 **[!UICONTROL Split]** 活動，以區分本月將慶祝生日的收件人與其他收件人。
1. 要拆分清單，請在 **[!UICONTROL Filtering of selected records]** 類別，選擇 **[!UICONTROL Add a filtering condition on the inbound population]**。 然後，按一下 **[!UICONTROL Edit]**。

   ![](assets/uc_enrichment_2.png)

1. 選擇 **[!UICONTROL Filtering conditions]** 然後按一下 **[!UICONTROL Edit expression]** 按鈕，將選定控制項在Tab鍵次序中下移一個位置。

   ![](assets/uc_enrichment_3.png)

1. 按一下 **[!UICONTROL Advanced Selection]** 然後 **[!UICONTROL Edit the formula using an expression]** 並添加以下表達式：月(@birthDate)。
1. 在 **[!UICONTROL Operator]** 列，選擇 **[!UICONTROL equal to]**。
1. 通過添加 **[!UICONTROL Value]** 當前日期的月份：Month(GetDate())。

   這將查詢其生日月份與當前月份對應的收件人。

   ![](assets/uc_enrichment_4.png)

1. 按一下 **[!UICONTROL Finish]**。然後，在 **[!UICONTROL General]** 頁籤 **[!UICONTROL Split]** 活動，按一下 **[!UICONTROL Generate complement]** 的 **[!UICONTROL Results]** 的子菜單。

   使用 **[!UICONTROL Complement]** 結果，您可以添加交貨活動或更新清單。 這裡，我們剛剛 **[!UICONTROL End]** 的子菜單。

   ![](assets/uc_enrichment_6.png)

您現在需要配置 **[!UICONTROL Enrichment]** 活動：

1. 添加 **[!UICONTROL Enrichment]** 添加自定義日期欄位後的活動。

   ![](assets/uc_enrichment_7.png)

1. 開啟 **[!UICONTROL Enrichment]** 的子菜單。 在 **[!UICONTROL Complementary information]** 類別，按一下 **[!UICONTROL Add data]**。

   ![](assets/uc_enrichment_8.png)

1. 選擇 **[!UICONTROL Data linked to the filtering dimension]** 然後 **[!UICONTROL Data of the filtering dimension]**。
1. 按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/uc_enrichment_9.png)

1. 添加 **[!UICONTROL Label]**。 然後，在 **[!UICONTROL Expression]** 列，按一下 **[!UICONTROL Edit expression]**。

   ![](assets/uc_enrichment_10.png)

1. 首先，我們需要把出生日期之前的一週作為 **有效性開始日期** 下面 **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`。

   ![](assets/uc_enrichment_11.png)

1. 然後，建立自定義日期欄位 **有效期結束日期** 以出生日期後的一週為目標，你需要添加 **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`。

   可以向表達式添加標籤。

   ![](assets/uc_enrichment_12.png)

1. 按一下 **[!UICONTROL Ok]**。你的富裕現在已準備好。

在 **[!UICONTROL Enrichment]** 活動，您可以添加交貨。 在這種情況下，我們添加了一封電子郵件，以向收件人發送一份特別優惠，其有效日期將在本月過生日的客戶。

1. 拖放 **[!UICONTROL Email delivery]** 在 **[!UICONTROL Enrichment]** 的子菜單。

   ![](assets/uc_enrichment_15.png)

1. 按兩下 **[!UICONTROL Email delivery]** 活動以開始個性化交付。
1. 添加 **[!UICONTROL Label]** 到您的交貨，按一下 **[!UICONTROL Continue]**。
1. 按一下 **[!UICONTROL Save]** 建立電子郵件傳遞。
1. 簽入 **[!UICONTROL Approval]** 頁籤 **[!UICONTROL Properties]** 那個 **[!UICONTROL Confirm delivery before sending option]** 的子菜單。

   然後，啟動工作流以利用目標資訊豐富出站轉換。

   ![](assets/uc_enrichment_18.png)

現在，您可以開始設計電子郵件傳遞，並使用在 **[!UICONTROL Enrichment]** 的子菜單。

1. 按兩下 **[!UICONTROL Email delivery]** 的子菜單。
1. 將目標擴展添加到電子郵件。 它應位於以下表達式中，以便配置有效日期的格式：

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. 按一下![](assets/uc_enrichment_16.png)。選擇 **[!UICONTROL Target extension]** 之後，先前建立的自定義有效性日期 **[!UICONTROL Enrichment]** 活動，將副檔名添加到formatDate表達式。

   ![](assets/uc_enrichment_19.png)

1. 根據需要配置您的電子郵件內容。

   ![](assets/uc_enrichment_17.png)

1. 預覽電子郵件以檢查自定義日期欄位是否配置正確

   ![](assets/uc_enrichment_20.png)

您的電子郵件現在已就緒。 您可以開始發送校樣並確認您的寄送，以發送生日電子郵件。
