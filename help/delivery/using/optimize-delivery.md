---
solution: Campaign Classic
product: campaign
title: 最佳化訊息傳送
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 7%

---

# 最佳化傳遞 {#optimize-delivery}

在開始建立傳送之前，您可以執行數個動作，以保護並最佳化上游的傳送程式。

以下章節概述最佳配置Adobe Campaign的最佳實務和建議程式。 遵循這些作法，可將下游可能遇到的問題降至最低。

## 平台效能

有幾個因素會直接影響伺服器效能並減緩平台速度：

* 個人化元素的數量和類型：電子郵件中的個人化會將每個收件者的資料從資料庫中提取。 如果有許多個人化元素，會增加準備傳送所需的資料量。  深入了解[此區段](../../delivery/using/about-personalization.md)中的個人化

* 伺服器載入：當行銷伺服器同時處理許多不同的工作時，可能會降低效能。 行銷伺服器需要協調所有傳送的所有傳入和傳出資料，以確保資料正確無誤。

   **提示**  — 為避免此情況，請與團隊的其他成員協調傳送排程，以確保最佳效能。

* 工作流執行：監控工作流程是避免平台效能問題的關鍵。 遵循本文檔](../../workflow/using/workflow-best-practices.md#execution-and-performance)中列出的[指南。

* 如果您符合資格，您可以使用[Campaign控制面板功能](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html)，透過[效能監控](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html)功能來監控您的平台。

## 正在檢查網路配置{#network-config}

要在處理大量電子郵件時優化傳送，並避免被誤認為是垃圾郵件發送者，請確保您擁有不嘗試隱藏伺服器身份的合法網路配置。

**提示**:使用與您品牌網站對應的透明寄件者地址。例如，旅行社公司管理華倫天奴連鎖酒店。 它擁有其網站的valentino.com域。 為了推廣巴黎的華倫天奴酒店，它使用paris.valentino.com子域。 因此，相關寄件者地址可以是hotel@paris.valentino.com。

## 傳遞能力管理{#deliverability-management}

若要在不反彈或標示為垃圾郵件的情況下到達收件者的收件匣，您必須改善訊息的傳遞率。

* 什麼是傳遞能力?

   * 它指的是電子郵件的因素，這些因素決定了收件人伺服器接受電子郵件的能力。 ISP（網際網路服務提供者）會篩選出其識別為垃圾訊息的電子郵件，或封鎖影像下載。 如果他們判斷某個網域傳送的電子郵件過多，將會限制從該寄件者接收的電子郵件數量。

   * 檢查電子郵件的傳遞能力時，您想要著重於四個主要類別：資料質量、訊息和內容、傳送基礎架構和信譽。 有關此主題的更深入的了解，請參閱[此部分](../../delivery/using/about-deliverability.md)。

* 套用本檔案](../../delivery/using/about-deliverability.md)中詳細的[建議。

* 請連絡您的Adobe代表以取得協助。

## 隔離管理{#quarantine-management}

維護良好的隔離管理流程符合您的最大利益。

開始在新平台上傳送電子郵件時，您可能會使用未完全合格的地址清單。 如果發送到無效地址或蜜罐地址（建立的郵箱僅用於欺騙垃圾郵件發送者），這將開始降低您平台的信譽。 良好的隔離管理流程有助於：保持地址質量，避免被網際網路訪問提供商拒絕，並降低錯誤率，加快交付和吞吐量。

**提示**

* 如果您有無效地址的清單，Adobe建議通過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**&#x200B;將其導入隔離表。

* 在傳送分析期間，預設會排除被隔離的收件者：它們不是目標。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。例如，收件匣已滿或地址不存在時，可以隔離電子郵件地址。 [了解更多](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign會根據傳回的錯誤類型來管理錯誤位址。 如需詳細資訊，請參閱[本章節](../../delivery/using/understanding-quarantine-management.md)。


* 如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者新增至封鎖清單。

* 隔離管理也有助於將錯誤的電話號碼排除在傳送之外，以降低簡訊傳送成本。

## 雙重加入機制{#double-opt-in}

為避免傳送訊息至無效位址、限制不當通訊並改善寄件者信譽，Adobe建議實作訂閱後確認的雙重加入機制。 這有助於確保收件者刻意訂閱。

實作此機制的詳細資訊在[本節](../../web/using/use-cases--web-forms.md)中概述。
