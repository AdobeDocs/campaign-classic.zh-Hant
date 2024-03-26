---
product: campaign
title: AB測試使用案例
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 4%

---

# AB測試： A/B測試此使用案例 {#ab-testing-use-case}

在此使用案例中，我們將透過定位工作流程比較兩個電子郵件傳遞內容。 訊息和文字在兩個傳送中均相同：只有版面配置會變更。

目標母體分為三組：兩個測試群組及剩餘母體。 會將不同版本的傳遞傳送傳送至每個測試群組。

傳送後，在收集最佳開啟率結果之前，會設定5天的等待期間。 接著，指令碼會復原分數最高的傳遞內容，並傳送給未作為測試群組的母體。

請注意，將決定哪個傳送是最佳傳送的條件可能會根據您的需求而改變。 可以是開放率、點進率、訂閱率、反應率等。

此外，此使用案例中詳細說明的測試僅與兩個傳送有關，但您可以視需要測試儘可能多的版本。 只需將活動新增至工作流程即可。

執行此使用案例的主要步驟為：

* [步驟1：建立目標定位工作流程](a-b-testing-uc-targeting-workflow.md)
* [步驟2：設定母體樣本](a-b-testing-uc-population-samples.md)
* [步驟3：建立兩個傳遞範本](a-b-testing-uc-delivery-templates.md)
* [步驟4：在工作流程中設定傳送](a-b-testing-uc-configuring-deliveries.md)
* [步驟5：建立指令碼](a-b-testing-uc-script.md)
* [步驟6：定義最終傳遞](a-b-testing-uc-final-delivery.md)
* [步驟7：啟動工作流程](a-b-testing-uc-start-workflow.md)
* [步驟8：分析結果](a-b-testing-uc-analyzing.md)

**相關主題：**

* [開始使用 A/B 測試](get-started-a-b-testing.md)
* [設定 A/B 測試](configuring-a-b-testing.md)
