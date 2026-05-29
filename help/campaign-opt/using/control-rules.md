---
product: campaign
title: 控制規則
description: 瞭解如何使用Adobe Campaign中的控制規則
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
TQID: https://experienceleague.adobe.com/zeKJZ7Y-qtGpPtZ6tUPN42ISVU6Fh6wpOuhfcXDsyAA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
subfeature_v2: id: e5fb657f-3c0a-4fcc-9980-3589a23ab4de
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 2%

---

# 控制規則{#control-rules}

## 分析和仲裁控制規則 {#analysis-and-arbitration-control-rules}

控制規則可讓您在傳送之前保證訊息的有效性和品質：字元顯示、簡訊大小、位址格式等。

一組現成的規則可讓您執行一般的檢查。 這些檢查（在介面中以粗體顯示）包括：

* **[!UICONTROL Object approval]** （電子郵件）：檢查寄件者物件與地址是否不包含特殊字元，這可能造成某些郵件代理程式發生問題。
* **[!UICONTROL URL label approval]** （電子郵件）：檢查每個追蹤URL是否有標籤。
* **[!UICONTROL URL approval]** （電子郵件）：檢查追蹤URL （是否有「&amp;」字元）。
* **[!UICONTROL Message size approval]** （行動裝置）：檢查SMS訊息的大小。
* **[!UICONTROL Validity period check]** （電子郵件）：檢查傳遞的有效期是否足夠長，以傳送所有訊息。
* **[!UICONTROL Proof size check]** （所有管道）：如果校訂目標母體超過100個收件者，則產生錯誤訊息。
* **[!UICONTROL Wave scheduling check]** （電子郵件）：如果傳遞劃分為數個批次，則檢查最後一個傳遞批次是否已排程在有效期間結束前開始。
* **[!UICONTROL Unsubscription link approval]** （電子郵件）：檢查每個內容（HTML和文字）中是否有至少一個取消訂閱（選擇退出） URL。

## 建立控制規則 {#creating-a-control-rule}

您可以建立新的控制規則以符合您的需求。 若要這麼做，請建立&#x200B;**[!UICONTROL Control]**&#x200B;型別規則，並在&#x200B;**[!UICONTROL Code]**&#x200B;索引標籤的SQL中輸入控制項公式。

**範例：**

在以下範例中，我們將建立規則以防止SMS選件傳送給超過100個收件者。 此規則將連結至行銷活動型別，然後連結至可使用相關選件的SMS傳送。

應用以下步驟：

1. 建立&#x200B;**[!UICONTROL Control]**&#x200B;型別規則。 選取&#x200B;**[!UICONTROL Warning]**&#x200B;警示等級。

   ![](assets/campaign_opt_create_control_01.png)

1. 在&#x200B;**[!UICONTROL Code]**&#x200B;索引標籤中，輸入指令碼以套用所需的臨界值，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果傳送目標超過100個連絡人，此指令碼會觸發警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 將此規則連結至行銷活動型別，並參考相關SMS傳送中的型別。

   ![](assets/campaign_opt_create_control_03.png)

1. 在傳遞分析期間，會套用規則並建立警告（如適用）。

   ![](assets/campaign_opt_create_control_04.png)

   但是，傳遞仍可傳送。

   如果您提高警示等級，將無法開始傳遞。

   ![](assets/campaign_opt_create_control_05.png)

   分析結束時，**[!UICONTROL Confirm delivery]**&#x200B;按鈕將不可用。

   ![](assets/campaign_opt_create_control_06.png)
