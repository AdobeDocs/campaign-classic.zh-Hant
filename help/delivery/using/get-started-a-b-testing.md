---
product: campaign
title: 開始使用 A/B 測試
description: 進一步瞭解Campaign中的A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 3%

---

# 開始使用 A/B 測試 {#get-started-a-b-testing}


A/B測試可讓您比較多個版本的傳送，以找出哪個版本對目標母體有最大影響。

若要這麼做，您首先需要定義傳送的多個變體。 然後，每個變體會傳送至母體樣本，以根據您選擇的條件（開啟、垃圾郵件投訴、點選特定連結……）確定哪個變體表現更好。

在下列範例中，傳遞目標已分割成兩個群組，每個群組代表目標人口的50%。 每個群組會收到兩個版本的傳遞，以及兩個不同的促銷優惠方案。 傳送傳遞後，根據促銷優惠的點按次數，斷定變體A的表現較佳。

![](assets/a-b-testing-schema.png)

透過Campaign Classic，A/B測試會透過工作流程實作，您可以在此指定要定位的母體以及接收每個變體的群組(請參閱 [設定a/b測試](configuring-a-b-testing.md))。

主要步驟為：

1. **Target** 所需的母體。
1. **分割母體** 放入子集中，您將在該子集上測試傳送的變體。

   例如，您可以將一個版本的傳送傳送傳送傳送給一小部分目標母體，並將另一個版本傳送給其餘母體。 這可讓您測試新版本的傳送，而不是通常傳送給客戶的傳送。 您也可以將目標母體分為3個群組，以便向其傳送三個不同的傳送版本。

1. **建立多個版本** 與每個子集相對應的傳遞內容。 要測試的變體可以是主旨、郵件內容、寄件者名稱等。
1. 啟動工作流程，然後使用 **傳遞記錄** 分析每個變體的子集行為。

>[!NOTE]
>
>工作流程也可讓您藉由自動識別表現較佳的傳送變體，然後將其傳送至剩餘母體，來自動化您的流程。 如需詳細資訊，請參閱本節 [使用案例](a-b-testing-use-case.md).
