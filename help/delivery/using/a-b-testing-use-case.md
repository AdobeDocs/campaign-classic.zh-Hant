---
solution: Campaign Classic
product: campaign
title: 關於此使用案例
description: 瞭解如何透過專屬的使用案例來執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# 關於此使用案例{#about-use-case}

在此使用案例中，我們將透過定位工作流程來比較兩個電子郵件傳送內容。 訊息和文字在兩個傳送中都相同：只會變更版面。

目標人口分為三：兩個測試群組和其餘人口。 傳送的不同版本會傳送至每個測試群組。

傳送後，會先設定5天的等待期，再收集最佳開放率的結果。 具有最高分數的傳送內容接著會由指令碼復原，並傳送至未用作測試群組的人口族群。

請注意，將決定哪個傳送方式最佳的准則，可能會因應您的需求而改變。 可以是開放率、點進率、訂閱率、反應性等。

此外，本使用案例中詳述的測試僅與兩個傳送有關，但您可以視需要測試任意多個版本。 只需將活動新增至工作流程即可。

執行此使用案例的主要步驟為：

* [步驟1:建立定位工作流程](#step-1--creating-a-targeting-workflow)
* [步驟2:配置人口樣本](#step-2--configuring-population-samples)
* [步驟3:建立兩個傳送範本](#step-3--creating-two-delivery-templates)
* [步驟4:在工作流程中設定傳送](#step-4--configuring-the-deliveries-in-the-workflow)
* [步驟5:建立指令碼](#step-5--creating-the-script)
* [步驟7:啟動工作流程](#step-7--starting-the-workflow)
* [步驟8:分析結果](#step-8--analyzing-the-result)。

**相關主題：**

* [開始使用A/B測試](../../delivery/using/get-started-a-b-testing.md)
* [設定A/B測試](../../delivery/using/configuring-a-b-testing.md)
