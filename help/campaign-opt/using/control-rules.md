---
product: campaign
title: 控制規則
description: 控制規則
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 3%

---

# 控制規則{#control-rules}

![](../../assets/common.svg)

## 分析和仲裁控制規則 {#analysis-and-arbitration-control-rules}

控制規則允許您在傳遞消息之前保證消息的有效性和質量：字元顯示、SMS大小、地址格式等。

一組現成的規則允許您執行常規檢查。 這些檢查（在介面中以粗體顯示）包括：

* **[!UICONTROL Object approval]** （電子郵件）:檢查發件人對象和地址是否不包含可能導致某些郵件代理出現問題的特殊字元。
* **[!UICONTROL URL label approval]** （電子郵件）:檢查每個跟蹤URL是否都有標籤。
* **[!UICONTROL URL approval]** （電子郵件）:檢查跟蹤URL（「&amp;」字元的存在）。
* **[!UICONTROL Message size approval]** （移動）:檢查簡訊的大小。
* **[!UICONTROL Validity period check]** （電子郵件）:檢查傳遞的有效期是否足夠長以發送所有消息。
* **[!UICONTROL Proof size check]** （所有頻道）:如果校樣目標總數超過100個收件人，則生成錯誤消息。
* **[!UICONTROL Wave scheduling check]** （電子郵件）:檢查如果將交貨分解為多個波次，則最後一波交貨是否計畫在有效期結束之前開始。
* **[!UICONTROL Unsubscription link approval]** （電子郵件）:檢查每個內容(HTML和文本)中是否存在至少一個未訂閱(opt-out)URL。

## 建立控制規則 {#creating-a-control-rule}

可以建立新的控制規則以滿足您的需要。 為此，請建立 **[!UICONTROL Control]** 類型規則，並在SQL中輸入控制公式 **[!UICONTROL Code]** 頁籤。

**範例:**

在以下示例中，我們將建立一個規則，以防止向100多個收件人發送SMS服務。 此規則將連結到市場活動類型，然後連結到有關服務的SMS交付。

應用以下步驟：

1. 建立 **[!UICONTROL Control]** 分類規則。 選擇 **[!UICONTROL Warning]** 警報級別。

   ![](assets/campaign_opt_create_control_01.png)

1. 在 **[!UICONTROL Code]** 頁籤，輸入要應用所需閾值的指令碼，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果傳遞目標超過100個聯繫人，此指令碼將觸發警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 將此規則連結到活動類型，並參考相關SMS傳遞中的類型。

   ![](assets/campaign_opt_create_control_03.png)

1. 在交貨分析期間，將應用規則並建立警告（如果適用）。

   ![](assets/campaign_opt_create_control_04.png)

   但是，交貨仍準備發送。

   如果增加警報級別，則會阻止傳遞。

   ![](assets/campaign_opt_create_control_05.png)

   在分析結束時， **[!UICONTROL Confirm delivery]** 按鈕將不可用。

   ![](assets/campaign_opt_create_control_06.png)
