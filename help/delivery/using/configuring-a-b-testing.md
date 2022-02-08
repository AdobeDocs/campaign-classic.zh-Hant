---
product: campaign
title: 設定 A/B 測試
description: 瞭解如何在Campaign Classic中配置A/B測試。
feature: A/B Testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 3%

---

# 設定 A/B 測試 {#configuring-a-b-testing}

![](../../assets/common.svg)

本節詳細介紹如何構建工作流以執行A/B測試。

1. 建立新工作流，然後配置 [查詢](../../workflow/using/query.md) 活動，以針對所需人口。

1. 添加 [拆分](../../workflow/using/split.md) 活動，將目標種群劃分為多個子集。

1. 開啟活動，然後根據需要配置每個子集。 有關如何配置的詳細資訊 **[!UICONTROL Split]** 活動，請參閱 [此部分](../../workflow/using/split.md)。

   在本例中，我們希望通過向目標人口的10%介紹每個主題，為新聞稿test2個新主題。

   ![](assets/ab-testing-split.png)

1. 增加一個過渡，以便向剩餘人群發送有關當前主題的新聞稿。 為此，請激活 **[!UICONTROL Generate complement]** 的 **[!UICONTROL General]** 頁籤。

   ![](assets/ab-testing-complement.png)

1. 對於每個子集，將交貨的版本添加到test。

   ![](assets/ab-testing-delivery.png)

現在可以啟動工作流。 發送交貨後，您將能夠跟蹤交貨日誌中三個子集的行為，以便查看哪個主題最成功。

工作流還允許您通過自動識別執行更好的傳遞變數，然後將其發送給剩餘人群來自動化流程。 有關詳細資訊，請參閱此專用 [用例](a-b-testing-use-case.md)。
