---
product: campaign
title: 移轉至Adobe Analytics Connector
description: Campaign - Analytics Connector常見問題集
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 5%

---

# 如何將現有Genesis整合移轉至Adobe Analytics Connector {#acc-aa-faq}



自Campaign Classicv7 21.1.3發行版本開始，已棄用Adobe Analytics Data Connector。 [了解更多](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

2021年8月1日起，Adobe Campaign Classic已從舊版Data Connectors UI中移除，不過，現有的Campaign整合將持續收集資料，並將資料傳遞至Adobe Analytics，直到2022年8月17日為止。 在當天以後，整合將停止收集資料並傳遞至Adobe Analytics。

您 **必須實作** 全新Adobe Analytics Connectors整合於AdobeExchange，取代舊版Data Connectors整合。 若要深入了解Adobe Analytics Connector，請參閱 [本頁](../../platform/using/adobe-analytics-connector.md).

若對這些變更有任何疑問，請閱讀 [常見問題集](#faq-aa). 如需詳細資訊，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>如果您從現有的Adobe Analytics Data Connector(先前稱為Genesis整合)移轉並使用Adobe Analytics中的新分類架構，您需要從7.3.1或8.4.1開始的組建版本，才能移轉至新的Adobe Analytics Connector。

## 有什麼改變？

現已推出Campaign Classicv7與Adobe Analytics之間的新整合。 主要變更列於下方。

* 此 **聯繫日期** Adobe Analytics已棄用可設為日期類型的分類。 對於移轉的整合，仍會維持相同類型。 適用於任何 **聯繫日期** 由Campaign建立，類型將 **字串**.

* **處理規則** 由Adobe Campaign建立，作為新整合的一部分。 其中 **處理規則** 應從Adobe Analytics手動建立，或直接使用用戶端Javascript實作。 **處理規則** 在現有整合中將保持不變。

* 內建的技術工作流程及其行為維持不變。 僅變更了工作流程用於向Adobe Analytics推送/提取資料的後端API。

* 請注意， `nlserver` 程式應已設定IMS技術帳戶使用者，新連接器才能運作。 此變更必須由Adobe完成。 若要實作此功能，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* 如果您是Adobe Genesis API，且工作流程自訂可從Adobe Analytics提取和推送資料，現在需要使用新的Adobe Analytics 1.4/2.0 API。 [了解更多](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 您有受到影響嗎？

如果您使用現有的Adobe Analytics Data Connector(先前稱為Genesis整合)，而整合是在低於Campaign 21.1.3的組建上實作，則會影響您。

了解如何檢查您的版本 [在本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## 如何更新？

您需要升級至Campaign 21.1.3（或更新版本） **2022年8月17日前**.

身為托管客戶，Adobe會與您合作，將您的執行個體升級至較新版本。 之後，您便能使用 [Adobe Analytics連接器](../../platform/using/adobe-analytics-connector.md).

身為內部部署/混合部署客戶，您需要升級至其中一個較新版本，才能從新整合中獲益。
升級所有執行個體後，您就能 [實作新整合](../../platform/using/adobe-analytics-provisioning.md) 至Adobe Analytics Connector，並確保順暢轉換。

## 常見問答集{#faq-aa}

**如何取得日誌？**

使用者介面設定和工作流程已配備 **verbose** 記錄。

在詳細模式中，也會針對每個向Adobe Analytics提出的API請求列印請求和回應標題。

身為內部部署使用者，您可以依照下列方式實作詳細模式：

* 為用戶介面啟用詳細模式：重新執行 `web` 在詳細模式下進行。
* 為啟用詳細模式 **webAnalytics** 工作流程：選取 **在引擎中執行** 選項，然後重新運行 `wfserver` 在詳細模式下。

**「整合擁有者非管理員」錯誤代表什麼？**

深入了解Data Connectors `Integration Owner Not Admin` 錯誤 [本頁](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**移轉至新連接器後，舊資料和報表套裝會發生什麼事？**

移轉後，新連接器（從舊連接器移轉）將開始推送資料至相同的報表套裝，而現有資料將不受影響：它會新增至現有資料。

**Analytics中存在的某些現有evar/事件/報表套裝在Campaign中不會顯示。 我應該怎麼做？**

整合仰賴日常作業的技術帳戶代號資料。 如果與技術帳戶使用者相關聯的產品設定檔缺少維度/量度/報表套裝的權限，我們使用的API就會因這些請求而動搖。

如果我們正在閱讀Analytics元件的詳細資訊（例如量度/維度/區段/報表套裝）,API將不會在結果中傳回這些元件（這看起來可能像Analytics端已刪除的項目，或不存在）。 Analytics API會拒絕這些請求並傳出錯誤。

解決方案是更新 **產品設定檔** 新建立/遺失元件的Analytics使用者代號中，將這些元件新增至 [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}。 如需詳細指引，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 實用連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓使用者能使用新的用戶端主控台](../../installation/using/client-console-availability-for-windows.md)
* [安裝 Campaign 用戶端控制台](../../installation/using/installing-the-client-console.md)
