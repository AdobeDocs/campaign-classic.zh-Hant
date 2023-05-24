---
product: campaign
title: 移轉至Adobe Analytics聯結器
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

在2021年8月1日，Adobe Campaign Classic已從舊版Data Connectors UI中移除，但在2022年8月17日之前，現有的Campaign整合將繼續收集資料並傳遞至Adobe Analytics。 在此日期之後，整合將會停止收集及傳遞資料給Adobe Analytics。

您 **必須實作** Adobe Exchange上的新Adobe Analytics Connector整合，取代舊版Data Connectors整合。 若要深入瞭解Adobe Analytics Connector，請參閱 [此頁面](../../platform/using/adobe-analytics-connector.md).

若對這些變更有任何疑問，請閱讀 [常見問題集](#faq-aa). 如需詳細資訊，請連絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>如果您要從現有的Adobe Analytics Data Connector (先前稱為Genesis整合)移轉並在Adobe Analytics中使用新分類架構，您需要從7.3.1或8.4.1開始的組建版本才能移轉至新的Adobe Analytics Connector。

## 哪些部分有所變更？

Campaign Classic v7與Adobe Analytics之間的新整合現已推出。 主要變更列於下方。

* 此 **聯絡日期** Adobe Analytics已棄用原本為日期型別的分類。 對於已移轉的整合，仍會維持相同型別。 針對任何 **聯絡日期** 由Campaign建立，型別將為 **字串**.

* **處理規則** 由Adobe Campaign建立，作為新整合的一部分。 兩者之一 **處理規則** 應從Adobe Analytics手動建立，或直接使用使用者端Javascript實作。 **處理規則** 對於現有整合，將維持不變。

* 內建的技術工作流程及其行為維持不變。 只有工作流程用來將資料推送/提取至/自Adobe Analytics的後端API已變更。

* 請注意 `nlserver` 應使用IMS技術帳戶使用者設定流程，新聯結器才能運作。 此變更必須由Adobe完成。 若要實作此專案，請連絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* 如果您在自訂工作流程中是Adobe Genesis API，可從Adobe Analytics提取和推送資料，現在必須使用新的Adobe Analytics 1.4/2.0 API。 [了解更多](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 您有受到影響嗎？

如果您使用現有的Adobe Analytics Data Connector (先前稱為Genesis整合)，而且整合是在低於Campaign 21.1.3的組建版本上實作，則您會受到影響。

瞭解如何檢查您的版本 [在本節中](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## 如何更新？

您需要升級至Campaign 21.1.3 （或更多） **2022年8月17日之前**.

作為託管客戶，Adobe將與您合作，將您的執行個體升級至較新版本。 之後，您便能夠使用 [Adobe Analytics聯結器](../../platform/using/adobe-analytics-connector.md).

身為內部部署/混合部署客戶，您需要升級至較新版本之一，才能受益於新的整合。
升級所有執行個體後，您將能夠 [實作新的整合](../../platform/using/adobe-analytics-provisioning.md) 至Adobe Analytics Connector，並確保順暢轉換。

## 常見問答集{#faq-aa}

**如何取得記錄檔？**

使用者介面設定和工作流程配備 **詳細資訊** 記錄。

在詳細模式中，也會針對向Adobe Analytics發出的每個API請求列印請求和回應標頭。

作為內部部署使用者，您可以實作詳細模式，如下所示：

* 若要啟用使用者介面的詳細模式：重新執行 `web` 詳細模式下的程式。
* 啟用詳細模式： **網站分析** 工作流程：選取 **在引擎中執行** 工作流程屬性中的選項，然後重新執行 `wfserver` 詳細模式。

**「整合擁有者不是管理員」錯誤是什麼意思？**

進一步瞭解Data Connectors `Integration Owner Not Admin` 中的錯誤 [此頁面](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**移轉至新聯結器後，舊資料和報表套裝會發生什麼事？**

移轉後，新聯結器（從舊聯結器移轉）會開始將資料推送至相同的報表套裝，而現有資料不會受到影響：它會新增至現有資料。

**Analytics中存在的一些現有evar/事件/報表套裝在Campaign中不可見。 我應該怎麼做？**

整合仰賴技術帳戶Token的資料進行日常操作。 如果與技術帳戶使用者相關聯的產品設定檔中缺少對維度/量度/報表套裝的許可權，我們使用的API將會因這些請求而失敗。

如果我們正在讀取Analytics元件的詳細資訊（例如量度/維度/區段/報表套裝），API不會在結果中傳回這些元件（這可能看起來像Analytics端已刪除或不存在某些元件）。 Analytics API將拒絕這些請求並出錯。

解決方案是更新 **產品設定檔** 技術使用者權杖的Analytics使用者內容中具有新建立/缺少的元件，方法是在以下專案新增這些元件： [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}。 如需更多指引，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 有用的連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic建置](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓使用者可以使用新的使用者端主控台](../../installation/using/client-console-availability-for-windows.md)
* [安裝 Campaign 用戶端控制台](../../installation/using/installing-the-client-console.md)
