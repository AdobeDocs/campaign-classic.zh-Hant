---
product: campaign
title: AB測試用例
description: 瞭解如何通過專用使用案例執行A/B測試。
feature: A/B Testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 4%

---

# A/B測試此使用案例 {#ab-testing-use-case}

![](../../assets/common.svg)

在此使用情形中，我們將通過目標工作流比較兩個電子郵件傳遞內容。 消息和文本在兩個遞送中都相同：只更改佈局。

目標人口分為三：兩個test群體和其餘人口。 將不同版本的傳遞發送到每個test組。

在交貨後，在收集最佳開啟速率的結果之前，將配置5天的等待期。 最高分數的傳遞內容隨後由指令碼恢復併發送到未被用作test組的群體。

請注意，可能會更改將決定哪種交付方式最好的標準，以滿足您的需要。 可以是開放率、點擊率、訂閱率、反應性等。

此外，此使用案例中詳細描述的test僅涉及兩個交貨，但您可以根據需要test任意多個版本。 只需將活動添加到工作流。

要執行此使用情形，主要步驟如下：

* [步驟1:建立目標工作流](a-b-testing-uc-targeting-workflow.md)
* [步驟2:配置填充樣本](a-b-testing-uc-population-samples.md)
* [第3步：建立兩個交貨模板](a-b-testing-uc-delivery-templates.md)
* [第4步：在工作流中配置交貨](a-b-testing-uc-configuring-deliveries.md)
* [第5步：建立指令碼](a-b-testing-uc-script.md)
* [步驟6:定義最終交貨](a-b-testing-uc-final-delivery.md)
* [第7步：啟動工作流](a-b-testing-uc-start-workflow.md)
* [第8步：分析結果](a-b-testing-uc-analyzing.md)

**相關主題：**

* [開始使用 A/B 測試](get-started-a-b-testing.md)
* [設定 A/B 測試](configuring-a-b-testing.md)
