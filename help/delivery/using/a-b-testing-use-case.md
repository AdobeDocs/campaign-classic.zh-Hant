---
product: campaign
title: AB測試使用案例
description: 透過專屬的使用案例了解如何執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 6%

---

# 關於此使用實例 {#about-use-case}

![](../../assets/common.svg)

在此使用案例中，我們將透過目標工作流程來比較兩個電子郵件傳送內容。 訊息和文字在兩個傳送中都相同：只有版面會變更。

目標人口分為三個：兩個測試群組和剩餘母體。 傳送的不同版本會傳送至每個測試群組。

傳送後，會先設定5天的等候期，再收集最佳開放率的結果。 分數最高的傳送內容接著會由指令碼復原，並傳送至未作為測試群組使用的母體。

請注意，將決定哪個傳送方式最佳的條件，可能會根據您的需求而變更。 它可以是開放率、點進率、訂閱率、再活性等。

此外，此使用案例中詳細說明的測試僅與兩個傳送相關，但您可以視需要測試多個版本。 只需將活動新增至工作流程即可。

執行此使用案例的主要步驟為：

* [步驟1:建立目標工作流程](a-b-testing-uc-targeting-workflow.md)
* [步驟2:設定母體樣本](a-b-testing-uc-population-samples.md)
* [步驟3:建立兩個傳遞範本](a-b-testing-uc-delivery-templates.md)
* [步驟4:在工作流程中設定傳送](a-b-testing-uc-configuring-deliveries.md)
* [步驟5:建立指令碼](a-b-testing-uc-script.md)
* [步驟6:定義最終傳送](a-b-testing-uc-final-delivery.md)
* [步驟7:啟動工作流程](a-b-testing-uc-start-workflow.md)
* [步驟8:分析結果](a-b-testing-uc-analyzing.md)

**相關主題：**

* [開始使用 A/B 測試](get-started-a-b-testing.md)
* [設定 A/B 測試](configuring-a-b-testing.md)
