---
product: campaign
title: 開始使用 A/B 測試
description: 進一步了解Campaign中的A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 3%

---

# 開始使用 A/B 測試 {#get-started-a-b-testing}



A/B測試可讓您比較多個傳送版本，以識別哪個版本對目標母體影響最大。

若要這麼做，您必須先定義傳送的多個變體。 然後，每個變體都會傳送至母體範例，以根據您選擇的標準（開啟、垃圾訊息投訴、點按特定連結……），判斷哪個變體的效能較佳。

在以下範例中，傳送目標已分割為兩個群組，每個分別代表目標母體的50%。 每個群組會收到兩個版本的傳送，並提供兩個不同的促銷優惠。 傳送後，根據促銷優惠方案的點按次數，得出變體A的效能較佳的結論。

![](assets/a-b-testing-schema.png)

透過Campaign Classic,A/B測試會透過工作流程實作，您可在其中指定要定位的母體，以及將接收每個變體的群組(請參閱 [設定a/b測試](configuring-a-b-testing.md))。

主要步驟為：

1. **目標** 所需人口。
1. **分割母體** 進入子集，您將在其中測試傳送的變體。

   例如，您可以將一個傳送版本傳送至目標母體的一小部分，並將另一個版本傳送至剩餘母體。 這可讓您測試新版本的傳送，而非通常傳送給客戶的傳送。 您也可以將目標母體分割為3個群組，以便傳送三個不同版本的傳送。

1. **建立多個版本** 每個子集的傳送。 要測試的變體可以是主旨、訊息內容、寄件者名稱等。
1. 啟動工作流程，然後使用 **傳遞記錄** 分析每個變體的子集行為。

>[!NOTE]
>
>工作流程也可讓您自動識別執行得較好的傳送變體，然後將其傳送至剩餘母體，借此自動化您的流程。 如需詳細資訊，請參閱此專屬 [使用案例](a-b-testing-use-case.md).
