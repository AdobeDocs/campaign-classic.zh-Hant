---
product: campaign
title: AB測試使用案例
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 4%

---

# A/B測試此使用案例 {#ab-testing-use-case}



在此使用案例中，我們將透過目標定位工作流程比較兩個電子郵件傳遞內容。 訊息和文字在兩個傳遞中完全相同：只有版面會變更。

目標母體分為三組：兩個測試群組及剩餘母體。 會傳送不同版本的傳遞至每個測試群組。

傳送後，在收集最佳開啟率結果之前，會設定5天的等待期間。 接著，指令碼會復原分數最高的傳遞內容，並傳送給未作為測試群組的母體。

請注意，決定哪個傳送是最佳傳送的條件可能會根據您的需求而改變。 可以是開放率、點進率、訂閱率、反應性等。

此外，此使用案例中詳述的測試僅與兩個傳送相關，但您可以視需要測試儘可能多的版本。 只需將活動新增至工作流程即可。

執行此使用案例的主要步驟為：

* [步驟1：建立目標定位工作流程](a-b-testing-uc-targeting-workflow.md)
* [步驟2：設定母體樣本](a-b-testing-uc-population-samples.md)
* [步驟3：建立兩個傳遞範本](a-b-testing-uc-delivery-templates.md)
* [步驟4：在工作流程中設定傳送](a-b-testing-uc-configuring-deliveries.md)
* [步驟5：建立指令碼](a-b-testing-uc-script.md)
* [步驟6：定義最終傳遞](a-b-testing-uc-final-delivery.md)
* [步驟7：開始工作流程](a-b-testing-uc-start-workflow.md)
* [步驟8：分析結果](a-b-testing-uc-analyzing.md)

**相關主題：**

* [開始使用 A/B 測試](get-started-a-b-testing.md)
* [設定 A/B 測試](configuring-a-b-testing.md)
