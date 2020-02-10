---
title: 控制規則
seo-title: 控制規則
description: 控制規則
seo-description: null
page-status-flag: never-activated
uuid: a83e56d0-573a-4592-b2b1-0d3b3e52b03f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: be037a80-3f94-465c-ba7d-ae7d50f70e36
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 控制規則{#control-rules}

## 分析與仲裁控制規則 {#analysis-and-arbitration-control-rules}

控制規則可讓您在傳送訊息之前，先保證訊息的有效性和品質：字元顯示、SMS大小、位址格式等。

一組現成可用的規則可讓您執行一般檢查。 這些檢查（在介面中以粗體顯示）包括：

* **[!UICONTROL Object approval]** （電子郵件）:檢查發件人對象和地址是否不包含某些郵件代理上可能出現問題的特殊字元。
* **[!UICONTROL URL label approval]** （電子郵件）:檢查每個追蹤URL是否有標籤。
* **[!UICONTROL URL approval]** （電子郵件）:檢查追蹤URL（存在&quot;&amp;&quot;字元）。
* **[!UICONTROL Message size approval]** （行動裝置）:檢查SMS訊息的大小。
* **[!UICONTROL Validity period check]** （電子郵件）:檢查傳送的有效期是否足夠長，以傳送所有訊息。
* **[!UICONTROL Proof size check]** （所有頻道）:如果校對目標人口超過100個收件者，則會產生錯誤訊息。
* **[!UICONTROL Wave scheduling check]** （電子郵件）:檢查如果傳送分成若干波，最後一波傳送是否排程在有效期結束前開始。
* **[!UICONTROL Unsubscription link approval]** （電子郵件）:檢查每個內容（HTML和文字）中是否至少有一個未訂閱（選擇退出）URL。

## 建立控制規則 {#creating-a-control-rule}

您可以建立符合您需求的新控制規則。 要執行此操作，請建立一 **[!UICONTROL Control]** 個分類規則，並在頁籤的SQL中輸入控制 **[!UICONTROL Code]** 公式。

**例如：**

在下列範例中，我們將建立規則，以防止SMS選件傳送給超過100個收件者。 此規則將連結至促銷活動類型，然後連結至有相關選件可用的SMS傳送。

應用以下步驟：

1. 建立類 **[!UICONTROL Control]** 型規則。 選擇警 **[!UICONTROL Warning]** 報級別。

   ![](assets/campaign_opt_create_control_01.png)

1. 在標籤 **[!UICONTROL Code]** 中，輸入要應用所需閾值的指令碼，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果傳送目標超過100個連絡人，此指令碼會觸發警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 將此規則連結至促銷活動類型學，並參考相關SMS傳遞中的類型學。

   ![](assets/campaign_opt_create_control_03.png)

1. 在傳送分析期間，會套用規則並建立警告（如果適用）。

   ![](assets/campaign_opt_create_control_04.png)

   不過，傳送仍可供傳送。

   如果您提高警報級別，則會阻止傳送。

   ![](assets/campaign_opt_create_control_05.png)

   分析結束時，按鈕 **[!UICONTROL Confirm delivery]** 將無法使用。

   ![](assets/campaign_opt_create_control_06.png)

