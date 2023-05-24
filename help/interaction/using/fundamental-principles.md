---
product: campaign
title: 基本原則
description: 基本原則
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# 基本原則{#fundamental-principles}



## 部署環境 {#deploying-environments}

管理優惠方案時，每個目標維度有兩個使用的環境：

* 優惠方案經理負責建立優惠方案並將其分類、編輯和啟動核准程式以便使用的設計環境。 此環境中也會定義每個類別的規則、可顯示優惠的優惠方案空間，以及用於定義優惠方案資格預先定義的篩選器。

   類別也可以線上上環境中手動發佈。

   核准優惠方案的程式詳見 [核准和啟用優惠方案](../../interaction/using/approving-and-activating-an-offer.md) 區段。

* 您可以在即時環境中找到設計環境中的已核准優惠方案，以及設計環境中設定的各種優惠方案空間、篩選器、類別和規則。 在呼叫優惠方案引擎期間，引擎將一律使用即時環境中的優惠方案。

優惠方案只會部署在核准程式期間選取的優惠方案空間。 因此，選件可能是即時的，但無法用於也處於即時狀態的選件空間。

![](assets/architecture_interaction1.png)

## 互動型別和聯絡方式 {#interaction-types-and-contact-methods}

互動有兩種型別：傳入互動（由聯絡人起始）和傳出互動（由優惠方案設計人員起始）。

這兩種互動型別可以在單一模式（單一連絡人的優惠方案計算）或批次模式（一組連絡人的優惠方案計算）中執行。 一般而言，傳入互動會以單一模式執行，而傳出互動則會以批次模式執行。 不過，對於交易式訊息而言，可能會有一些例外情況，例如傳出互動會以單一模式執行(請參閱 [本節](../../message-center/using/about-transactional-messaging.md))。

一旦可以或必須呈現優惠方案（根據執行的設定），優惠方案引擎就會扮演中介角色：它會結合所收到的聯絡人相關資料以及可依應用程式指定套用的不同規則，自動計算可用聯絡人中可能的最佳優惠方案。

![](assets/architecture_interaction2.png)
