---
product: campaign
title: 遷移到Adobe Analytics連接器
description: 市場活動 — 分析連接器常見問題
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
source-git-commit: c072cb5b2d33f93ff395e4670507744b0d20c9bc
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 5%

---

# 如何將現有Genesis整合遷移到Adobe Analytics連接器 {#acc-aa-faq}

![](../../assets/v7-only.svg)

正在啟動Campaign Classicv7 21.1.3版，不建議使用Adobe Analytics資料連接器。 [了解更多](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

2021年8月1日，Adobe Campaign Classic已從舊式資料連接器用戶介面中刪除，但是，現有市場活動整合將繼續收集資料並將資料傳遞給Adobe Analytics，直到2022年8月17日。 在此日期之後，整合將停止收集資料並將資料轉給Adobe Analytics。

你 **必須** 新的Adobe Analytics連接器在Adobe交換上的整合，取代了舊式資料連接器整合。 要瞭解有關Adobe Analytics連接器的詳細資訊，請參閱 [此頁](../../platform/using/adobe-analytics-connector.md)。

>[!NOTE]
>
>有關這些更改的任何問題，請閱讀 [常見問題](#faq-aa)。 有關詳細資訊，請聯繫 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 什麼變了？

Campaign Classicv7和Adobe Analytics之間的新整合現已推出。 下面列出了主要更改。

* 的 **聯繫日期** Classification（使用為日期類型）已被Adobe Analytics棄用。 對於遷移的整合，它仍將保持相同類型。 對於任何 **聯繫日期** 由市場活動建立，類型將 **字串**。

* **處理規則** 由Adobe Campaign建立，作為新整合的一部分。 要麼 **處理規則** 應從Adobe Analytics手動建立，或直接使用客戶端Javascript實現。 **處理規則** 將保持原樣。

* 內置的技術工作流及其行為保持不變。 只有工作流用於向/從Adobe Analytics推送/拉入資料的後端API已更改。

* 請注意 `nlserver` 應使用IMS技術帳戶用戶配置進程，以便新連接器工作。 此更改必須由Adobe完成。 要實現此功能，請與 [Adobe客戶關懷](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

* 如果您是Adobe GenesisAPI，在自定義工作流中用於從Adobe Analytics提取和推送資料，則現在需要使用新的Adobe Analytics1.4/2.0 API。 [了解更多](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 您有受到影響嗎？

如果您使用現有的Adobe Analytics資料連接器(以前稱為Genesis整合)，並且整合是在比市場活動21.1.3更低的版本上實施的，則您會受到影響。

瞭解如何檢查您的版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

## 如何更新？

您需要升級到市場活動21.1.3（或更多） **2022年8月17日前**。

作為托管客戶，Adobe將與您合作，將您的實例升級到較新的版本。 然後你就能 [Adobe Analytics連接器](../../platform/using/adobe-analytics-connector.md)。

作為內部/混合型客戶，您需要升級到其中一個較新的版本，以便從新的整合中獲益。
升級所有實例後，您將能夠 [實施新的整合](../../platform/using/adobe-analytics-provisioning.md) 到Adobe Analytics連接器，並確保無縫過渡。

## 常見問答集{#faq-aa}

**我怎麼才能得到日誌？**

用戶介面配置和工作流都配備 **詳細** 日誌記錄。

在詳細模式下，還會為每個API請求打印到Adobe Analytics的請求和響應頭。

作為內部用戶，您可以按如下方式實現詳細模式：

* 要為用戶介面啟用詳細模式：重新運行 `web` 在詳細模式下進行。
* 為啟用冗餘模式 **WebAnalytics** 工作流：選擇 **在引擎中執行** 選項，然後重新運行 `wfserver` 在詳細模式下。

**「整合所有者不是管理員」錯誤意味著什麼？**

瞭解有關資料連接器的詳細資訊 `Integration Owner Not Admin` 錯誤 [此頁](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error)。

**遷移到新連接器後，舊資料和報告套件會發生什麼變化？**

遷移後，新連接器（從舊連接器遷移）將開始將資料推送到同一報告套件，並且現有資料將不受影響：它將添加到現有資料中。

**分析中存在的某些現有事件/事件/報告套件在市場活動中不可見。 我該怎麼辦？**

整合依賴於技術帳戶令牌上的日常操作資料。 如果缺少與技術帳戶用戶關聯的產品配置檔案中對維/度量/報表套件的權限，則我們使用的API將對這些請求產生動搖。

如果我們正在讀取分析元件（如度量/維/段/報表套件）的詳細資訊，則API將不會在結果中返回這些元件（這可能看起來像是在分析端刪除的內容或不存在）。 分析API將拒絕這些請求並錯誤。

解決方案是更新 **產品配置檔案** 在Analytics User Context of Technical User Token中添加新建立/缺少的元件，方法是： [Adobe Admin Console](https://adminconsole.adobe.com/)。 如需更多指導，請與 [Adobe客戶關懷](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 有用連結

* [升級環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic內部版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [使新客戶端控制台可供用戶使用](../../installation/using/client-console-availability-for-windows.md)
* [安裝 Campaign 用戶端控制台](../../installation/using/installing-the-client-console.md)
