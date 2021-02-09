---
solution: Campaign Classic
product: campaign
title: 開始使用A/B測試
description: 進一步瞭解Campaign Classic中的A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# 開始使用A/B測試{#get-started-a-b-testing}

A/B測試可讓您比較多個版本的傳送，以找出哪個版本對目標群體的影響最大。

若要這麼做，您首先需要定義多個傳送變數。 然後，每個變型都會傳送至人口樣本，以根據您選擇的標準（開啟、垃圾訊息投訴、點按特定連結……）來判斷哪個變型的效能較佳。

在以下範例中，傳送目標已分割為兩個群組，每個群組代表目標人口的50%。 每個群組會收到兩個版本的傳送，並有兩個不同的促銷優惠。 傳送後，根據促銷優惠的點按次數，推斷變數A的執行效果較佳。

![](assets/a-b-testing-schema.png)

使用Campaign Classic,A/B測試會透過工作流程實作，您可在此指定要定位的人口族群以及將接收每個變數的群組（請參閱[設定a/b測試](../../delivery/using/configuring-a-b-testing.md)）。

主要步驟為：

1. **定** 位所需人口。
1. **將人口** 族群分割為子集，您將測試其上的傳遞變數。

   例如，您可以傳送一個傳送版本至目標人口的一小部分，而另一個版本則傳送至其餘人口。 這可讓您測試新版本的傳送，而不是通常傳送給客戶的傳送。 您也可以將目標人口分為3個群組，以便傳送3個不同的傳送版本。

1. **建立與** 每個子集對應之傳送的多個版本。要測試的變體可以是主題、消息內容、發送者名稱等。
1. 啟動工作流，然後使用&#x200B;**傳送日誌**&#x200B;分析每個變體的子集的行為。

>[!NOTE]
>
>工作流程也可讓您自動識別執行成效較佳的傳送變體，然後將其傳送至剩餘人口，以自動化您的流程。 有關詳細資訊，請參閱此專用[使用案例](../../delivery/using/a-b-testing-use-case.md)。
