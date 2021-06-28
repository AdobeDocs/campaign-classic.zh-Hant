---
product: campaign
title: 移轉至Adobe Analytics Connector
description: Campaign - Analytics Connector常見問題集
hide: true
hidefromtoc: true
source-git-commit: 41478c656ffd4e113788149e6cca9ed00602789e
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 5%

---

# 如何移轉至Adobe Analytics Connector {#acc-aa-faq}

自Campaign Classicv7 21.1.3發行版本開始，已棄用Adobe Analytics Data Connector。 [深入瞭解](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

2021年8月1日起，Adobe Campaign Classic將從舊版Data Connectors UI中移除，不過現有的Campaign整合將持續收集資料，並將資料傳遞至Adobe Analytics，直到2022年3月1日為止。 2022年3月1日起，整合將停止收集資料，並將資料傳遞至Adobe Analytics。

您必須移轉至AdobeExchange上的新Adobe Analytics Connector整合，以取代舊版Data Connectors整合，如[本頁面](../platform/using/adobe-analytics-connector.md)所述。


>[!NOTE]
>
>如有關於這些變更的任何問題，請參閱[FAQ](#faq-aa)。 如需詳細資訊，請聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。


## 有什麼改變？

現已推出Campaign Classicv7與Adobe Analytics之間的新整合。 主要變更列於下方。

* Adobe Campaign Classic與Adobe Analytics驗證的整合已從使用者/密碼移至AdobeIdentity Management服務(IMS)。 因此，您必須實作AdobeIMS，並透過Adobe ID](../integrations/using/about-adobe-id.md)連線至促銷活動[，再開始實作Analytics Connector。

* **連絡日期**&#x200B;分類（原為日期類型）已由Adobe Analytics淘汰。 對於移轉的整合，仍會維持相同類型。 對於Campaign建立的任何&#x200B;**連絡日期**，類型將為&#x200B;**字串**。

* **處理** 規則是由Adobe Campaign在新整合中建立。應從Adobe Analytics手動建立&#x200B;**處理規則**，或直接使用用戶端Javascript實作。 **處理** 規則對現有整合將維持不變。

* 內建的技術工作流程及其行為維持不變。 僅變更了工作流程用於向Adobe Analytics推送/提取資料的後端API。

* 請注意，`nlserver`程式應以IMS技術帳戶使用者設定，新連接器才能運作。 此變更必須由Adobe完成。 若要實作此功能，請連絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

* 如果您是Adobe Genesis API，且工作流程自訂可從Adobe Analytics提取和推送資料，現在需要使用新的Adobe Analytics 1.4/2.0 API。 [深入瞭解](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 您有受到影響嗎？

如果您使用現有的Adobe Analytics Data Connector(先前稱為Genesis整合)，而整合是在低於Campaign 21.1.3的組建上實作，則會影響您。

在本小節](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何檢查您的版本[。

## 如何更新？

在2022年3月1日之前，您需要升級至Campaign 21.1.3（或更新版本）**。**

身為托管客戶，Adobe會與您合作，將您的執行個體升級至較新版本。

身為內部部署/混合部署客戶，您需要升級至其中一個較新版本，才能從新整合中獲益。

升級所有執行個體後，您將能[實作新的整合](../platform/using/adobe-analytics-connector.md)至Adobe Analytics Connector，並確保順暢轉換。


## 常見問答集{#faq-aa}

**如何取得日誌？**

使用者介面設定和工作流程皆具備&#x200B;**verbose**&#x200B;記錄功能。

在詳細模式中，也會針對每個向Adobe Analytics提出的API請求列印請求和回應標題。

身為內部部署使用者，您可以依照下列方式實作詳細模式：

* 為用戶介面啟用詳細模式：以詳細模式重新運行`web`進程。
* 若要為&#x200B;**webAnalytics**&#x200B;工作流程啟用詳細模式：從工作流屬性中選擇&#x200B;**在引擎中執行**&#x200B;選項，然後在詳細模式下重新運行`wfserver`。

**「整合擁有者非管理員」錯誤代表什麼？**

深入了解[本頁面](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error)中的Data Connectors `Integration Owner Not Admin`錯誤。

**移轉至新連接器後，舊資料和報表套裝會發生什麼事？**

移轉後，新連接器（從舊連接器移轉）將開始推送資料至相同的報表套裝，而現有資料將不受影響：它會新增至現有資料。

**Analytics中存在的某些現有evar/事件/報表套裝在Campaign中不會顯示。我該做什麼？**

整合需仰賴技術帳戶代號上的日常操作資料。 如果與技術帳戶使用者相關聯的產品設定檔缺少維度/量度/報表套裝的權限，我們使用的API就會因這些請求而動搖。

如果我們正在閱讀Analytics元件的詳細資訊（例如量度/維度/區段/報表套裝）,API將不會在結果中傳回這些元件（這看起來可能像Analytics端已刪除的項目，或不存在）。 Analytics API會拒絕這些請求並傳出錯誤。

解決方案是透過在[Adobe Admin Console](https://adminconsole.adobe.com/)中新增這些元件，以新建立/遺失的元件，更新Analytics技術使用者代號的&#x200B;**產品設定檔**。 如需詳細指引，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 實用連結

* [升級您的環境](../production/using/build-upgrade.md)
* [建置升級常見問答集](../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓使用者能使用新的用戶端主控台](../installation/using/client-console-availability-for-windows.md)
* [安裝 Campaign 用戶端控制台](../installation/using/installing-the-client-console.md)
