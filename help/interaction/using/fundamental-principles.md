---
product: campaign
title: 基本原則
description: 基本原則
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# 基本原則{#fundamental-principles}

## 部署環境{#deploying-environments}

管理選件時，每個目標維度會使用兩個環境：

* 一種設計環境，優惠方案管理員會負責建立和分類優惠方案、編輯優惠方案，以及啟動核准程式以便使用。 此環境中也會定義每個類別的規則、可呈現優惠方案的優惠方案空間，以及用來定義優惠方案資格的預先定義篩選器。

   您也可以線上上環境中手動發佈類別。

   核准優惠方案的程式在[核准和啟用優惠方案](../../interaction/using/approving-and-activating-an-offer.md)一節中有詳細說明。

* 一個即時環境，其中可找到設計環境中已核准的選件，以及設計環境中設定的各種選件空間、篩選器、類別和規則。 在呼叫優惠方案引擎期間，引擎將一律使用即時環境中的優惠方案。

優惠方案只會部署在核准程式期間選取的優惠方案空間上。 因此，選件可能是即時的，但在同樣即時的選件空間上則無法使用。

![](assets/architecture_interaction1.png)

## 交互類型和聯繫方法{#interaction-types-and-contact-methods}

互動有兩種可能的類型：入站互動（由聯絡人起始）和出站互動（由優惠方案製作人起始）。

這兩種互動可以在統一模式（針對單一聯絡計算選件）或批次模式（針對一組聯絡計算選件）中執行。 通常，入站互動以統一模式執行，而出站互動以批次模式執行。 然而，對於交易式訊息，例如，在統一模式下執行出站互動時，可能會有某些例外（請參閱[此部分](../../message-center/using/about-transactional-messaging.md)）。

一旦能夠或必須呈現優惠方案（根據執行的設定），優惠方案引擎就會扮演中介角色：它通過組合接收的關於聯繫人的資料和可以應用應用程式中指定的不同規則，自動計算可用聯繫人中的最佳可能選件。

![](assets/architecture_interaction2.png)
