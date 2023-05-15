---
product: campaign
title: 設定 A/B 測試
description: 了解如何在Campaign中設定A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---

# 設定 A/B 測試 {#configuring-a-b-testing}



本節詳細說明如何建立工作流程以執行A/B測試。

1. 建立新工作流程，然後設定 [查詢](../../workflow/using/query.md) 活動來定位所需的母體。

1. 新增 [分割](../../workflow/using/split.md) 活動，將目標母體劃分為多個子集。

1. 開啟活動，然後根據您的需求設定每個子集。 如需如何設定 **[!UICONTROL Split]** 活動，請參閱 [本節](../../workflow/using/split.md).

   在此範例中，我們想透過將每個主題呈現給目標人口的10%，來測試電子報中的2個新主題。

   ![](assets/ab-testing-split.png)

1. 新增轉變，以便將包含目前主題的電子報傳送給剩餘母體。 若要這麼做，請啟用 **[!UICONTROL Generate complement]** 選項 **[!UICONTROL General]** 標籤。

   ![](assets/ab-testing-complement.png)

1. 針對每個子集，新增要測試的傳送版本。

   ![](assets/ab-testing-delivery.png)

您現在可以啟動工作流程。 傳送完畢後，您就可以追蹤傳送記錄中三個子集的行為，以查看哪個主題最成功。

工作流程也可讓您自動識別執行得較好的傳送變體，然後將其傳送至剩餘母體，借此自動化您的流程。 如需詳細資訊，請參閱此專屬 [使用案例](a-b-testing-use-case.md).
