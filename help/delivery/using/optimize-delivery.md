---
product: campaign
title: 最佳化訊息傳送
description: 瞭解如何最佳化您的訊息傳送
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Deliverability
role: User
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 4%

---

# 最佳化傳遞 {#optimize-delivery}

在開始建立傳遞之前，您可以採取數個動作來保護上游的傳送流程並加以最佳化。

以下章節概述Adobe Campaign最佳設定的最佳實務和建議程式。 遵循這些實務將最大程度減少您可能在下游遇到的問題。

## 平台效能

有幾個因素會直接影響伺服器效能並拖慢平台速度：

* 個人化元素的數量和型別：電子郵件中的個人化會將每個收件者的資料從資料庫中提取。 如果有許多個人化元素，會增加準備傳送所需的資料量。  在[本節](about-personalization.md)中進一步瞭解個人化

* 伺服器載入：行銷伺服器同時處理許多不同工作時，可能會減慢效能。 行銷伺服器需要協調所有傳遞的所有傳入和傳出資料，以確保資料正確且準時。

  **秘訣** — 若要避免此問題，請與團隊的其他成員協調傳送排程，以確保最佳效能。

* 工作流程執行：監控工作流程是避免平台效能問題的關鍵。 請遵循此檔案](../../workflow/using/workflow-best-practices.md#execution-and-performance)中列出的准則[。

* 如果您符合資格，可以使用[效能監視](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=zh-Hant)功能，利用[Campaign控制面板功能](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)來監視您的平台。

## 檢查網路設定 {#network-config}

若要在處理大量電子郵件時最佳化傳遞，並避免誤認為垃圾郵件傳送者，請確定您有合法的網路設定，不會嘗試隱藏伺服器的身分。

**秘訣**：使用與品牌網站對應的透明寄件者地址。 例如，TravelAgency公司管理Valentino連鎖酒店。 其擁有其網站的valentino.com網域。 為了推廣巴黎的Valentino飯店，它使用paris.valentino.com子網域。 因此，相關寄件者地址可以是hotel@paris.valentino.com。

## 傳遞能力管理 {#deliverability-management}

若要在不退回或標示為垃圾訊息的情況下觸及收件者的收件匣，您需要改善訊息的可傳遞率。

* 什麼是傳遞能力？

   * 它是指決定電子郵件為收件者伺服器接受之能力的電子郵件因素。 ISP （網際網路服務提供者）會篩選掉他們認為是垃圾郵件的電子郵件，或封鎖影像的下載。 如果他們判斷某個網域傳送的電子郵件數量過多，就會限制其將接受來自該寄件者的電子郵件數量。

   * 在檢查電子郵件是否可傳遞時，您想要將焦點放在四個主要類別上：資料品質、訊息和內容、傳送基礎結構和信譽。 如需深入瞭解此主題，請參閱[本節](about-deliverability.md)。

* 套用此檔案](about-deliverability.md)中詳細[的建議。

* 請聯絡您的Adobe代表以尋求協助。

## 隔離管理 {#quarantine-management}

維持良好的隔離管理流程符合您的最佳利益。

開始在新平台上傳送電子郵件時，您可能會使用未完全限定的地址清單。 如果您傳送至無效的位址或蜜罐位址（僅用來欺騙垃圾郵件寄件者的信箱），將開始降低平台的聲譽。 良好的隔離管理流程有助於：維持地址品質、避免網際網路存取提供者列入封鎖清單，以及降低錯誤率、加快傳遞速度與輸送量。

**提示**

* 如果您有無效地址清單，Adobe建議透過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**，將其匯入隔離表格。

* 在傳遞分析期間，預設情況下會排除其地址被隔離的收件者：他們並非目標收件者。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。 舉例來說，當收件匣已滿或地址不存在時，可以隔離電子郵件地址。 [了解更多](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign會根據傳回的錯誤型別管理錯誤地址。 如需詳細資訊，請參閱[本章節](understanding-quarantine-management.md)。


* 如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者新增到封鎖清單中。

* 隔離管理還能將錯誤的電話號碼排除在遞送服務之外，有助於降低簡訊傳送成本。

## 雙重加入機制 {#double-opt-in}

為避免傳送訊息至無效地址、限制不當通訊並改善寄件者信譽，Adobe建議對訂閱後確認實施雙重選擇加入機制。 這有助於確保收件者有意識地訂閱。

實作此機制的詳細資訊在[本節](../../web/using/use-cases-web-forms.md)中概述。
