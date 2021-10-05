---
product: campaign
title: 設定 A/B 測試
description: 了解如何在Campaign Classic中設定A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 3%

---

# 設定 A/B 測試 {#configuring-a-b-testing}

![](../../assets/common.svg)

本節詳細說明如何建立工作流程以執行A/B測試。

1. 建立新工作流程，然後設定[Query](../../workflow/using/query.md)活動以鎖定所需的母體。

1. 新增[Split](../../workflow/using/split.md)活動，將目標母體劃分為多個子集。

1. 開啟活動，然後根據您的需求設定每個子集。 有關如何配置&#x200B;**[!UICONTROL Split]**&#x200B;活動的詳細資訊，請參閱[此部分](../../workflow/using/split.md)。

   在此範例中，我們想透過將每個主題呈現給目標人口的10%，來測試電子報中的2個新主題。

   ![](assets/ab-testing-split.png)

1. 新增轉變，以便將包含目前主題的電子報傳送給剩餘母體。 要執行此操作，請從&#x200B;**[!UICONTROL General]**&#x200B;標籤啟動&#x200B;**[!UICONTROL Generate complement]**&#x200B;選項。

   ![](assets/ab-testing-complement.png)

1. 針對每個子集，新增要測試的傳送版本。

   ![](assets/ab-testing-delivery.png)

您現在可以啟動工作流程。 傳送完畢後，您就可以追蹤傳送記錄中三個子集的行為，以查看哪個主題最成功。

工作流程也可讓您自動識別執行得較好的傳送變體，然後將其傳送至剩餘母體，借此自動化您的流程。 有關詳細資訊，請參閱此專用[使用案例](a-b-testing-use-case.md)。
