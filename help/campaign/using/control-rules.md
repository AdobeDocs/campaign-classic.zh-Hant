---
product: campaign
title: 控制規則
description: 控制規則
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 3%

---

# 控制規則{#control-rules}

## 分析和仲裁控制規則{#analysis-and-arbitration-control-rules}

控制規則可讓您在傳送前保證訊息的有效性和品質：字元顯示、SMS大小、位址格式等。

一組現成的規則可讓您執行一般的檢查。 這些檢查（在介面中以粗體顯示）包括：

* **[!UICONTROL Object approval]** （電子郵件）:檢查發件人對象和地址是否不包含可能在某些郵件代理上造成問題的特殊字元。
* **[!UICONTROL URL label approval]** （電子郵件）:檢查每個追蹤URL是否有標籤。
* **[!UICONTROL URL approval]** （電子郵件）:檢查追蹤URL（是否有&quot;&amp;&quot;字元）。
* **[!UICONTROL Message size approval]** （行動）:檢查SMS訊息的大小。
* **[!UICONTROL Validity period check]** （電子郵件）:檢查傳送的有效期是否夠長，足以傳送所有訊息。
* **[!UICONTROL Proof size check]** （所有通道）:如果校樣目標母體超過100個收件者，則會產生錯誤訊息。
* **[!UICONTROL Wave scheduling check]** （電子郵件）:檢查如果傳送分為數個批次，上一波傳送是否排程在有效期結束前開始。
* **[!UICONTROL Unsubscription link approval]** （電子郵件）:檢查每個內容（HTML和文字）中是否至少有一個取消訂閱（選擇退出）URL。

## 建立控制規則{#creating-a-control-rule}

您可以建立新的控制規則以符合您的需求。 要執行此操作，請建立&#x200B;**[!UICONTROL Control]**&#x200B;類型規則，並在&#x200B;**[!UICONTROL Code]**&#x200B;索引標籤的SQL中輸入控制公式。

**範例:**

在下列範例中，我們將建立規則，以防止將SMS選件傳送給超過100個收件者。 此規則將連結至行銷活動類型，然後連結至可使用相關優惠方案的SMS傳送。

應用以下步驟：

1. 建立&#x200B;**[!UICONTROL Control]**&#x200B;類型規則。 選擇&#x200B;**[!UICONTROL Warning]**&#x200B;警報級別。

   ![](assets/campaign_opt_create_control_01.png)

1. 在&#x200B;**[!UICONTROL Code]**&#x200B;標籤中，輸入要應用所需閾值的指令碼，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果傳送目標超過100個連絡人，此指令碼將觸發警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 將此規則連結至行銷活動類型，並在相關SMS傳送中參考類型。

   ![](assets/campaign_opt_create_control_03.png)

1. 在傳送分析期間，會套用規則並建立警告（若適用）。

   ![](assets/campaign_opt_create_control_04.png)

   不過，傳送仍可供傳送。

   如果您提高警報層級，則無法開始傳送。

   ![](assets/campaign_opt_create_control_05.png)

   分析結束時，將無法使用&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;按鈕。

   ![](assets/campaign_opt_create_control_06.png)
