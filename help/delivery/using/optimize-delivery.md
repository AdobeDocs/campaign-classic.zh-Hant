---
solution: Campaign Classic
product: campaign
title: 最佳化訊息傳送
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 6%

---


# 最佳化傳遞 {#optimize-delivery}

在開始建立傳送之前，您可以採取數個動作來保護並最佳化上游傳送程式。

下節概述了Adobe Campaign最佳配置的最佳做法和建議程式。 遵循這些實務可將下游可能遇到的問題降到最低。

## 平台效能

數個因素會直接影響伺服器效能並減緩平台速度：

* 個人化元素的數量和類型：電子郵件中的個人化會從資料庫中提取每個收件者的資料。 如果有許多個人化元素，會增加準備傳送所需的資料量。  在[本節](../../delivery/using/about-personalization.md)中進一步瞭解個人化

* 伺服器載入：當行銷伺服器同時處理許多不同的工作時，可能會降低效能。 行銷伺服器需要協調所有傳送的所有傳入和傳出資料，以確保資料正確且準時。

   **提示** -為避免此問題，請與團隊中的其他成員協調交貨的排程，以確保獲得最佳效能。

* 工作流執行：監控工作流程是避免平台效能問題的關鍵。 遵循本檔案](../../workflow/using/workflow-best-practices.md#execution-and-performance)中所列的准則。[

* 身為代管客戶，您可運用[促銷活動控制面板功能](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html)，使用[效能監控](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html)功能來監控您的平台。

## 正在檢查網路配置{#network-config}

若要在處理大量電子郵件時最佳化傳送，並避免被誤認為是垃圾郵件發送者，請確定您有合法的網路組態，不會嘗試隱藏伺服器的身分。

**提示**:使用與您品牌網站對應的透明寄件者位址。例如，這家旅行社管理著華倫天奴連鎖酒店。 它擁有其網站的valentino.com網域。 為推廣巴黎的華倫天奴酒店，它使用paris.valentino.com子網域。 因此，相關的發件人地址可以是hotel@paris.valentino.com。

## 傳遞能力管理{#deliverability-management}

若要在不反彈或標示為垃圾訊息的情況下進入收件者的收件匣，您必須改善訊息的傳遞率。

* 什麼是傳遞能力？

   * 它是指決定電子郵件是否能被收件者伺服器接受的因素。 ISP（網際網路服務供應商）會過濾掉其識別為垃圾訊息的電子郵件，或封鎖影像下載。 如果他們判斷某個網域傳送的電子郵件過多，他們會設定接受該寄件者寄送之電子郵件的數量限制。

   * 在檢查您的電子郵件是否具有傳遞能力時，您希望將重點放在四個主要類別：資料品質、訊息和內容、傳送基礎架構和聲譽。 有關本主題的深入探討，請參閱[本節](../../delivery/using/about-deliverability.md)。

* 套用本檔案](../../delivery/using/about-deliverability.md)中詳細說明的建議。[

* 請洽詢您的Adobe代表以取得協助。

## 隔離管理{#quarantine-management}

維護良好的隔離管理流程符合您的最大利益。

當您開始在新平台上傳送電子郵件時，可能會使用未完全限定的位址清單。 如果您發送到無效地址或蜜罐地址（郵箱僅用於誘騙垃圾郵件發送者），這將開始削弱您平台的聲譽。 良好的隔離管理流程有助於：維持位址品質、避免網際網路存取供應商的拒絕清單，並降低錯誤率、加速傳送和總處理能力。

**提示**

* 如果您有無效地址清單，Adobe建議通過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**&#x200B;將其導入隔離表。

* 在傳送分析期間，預設會排除隔離地址的收件者：它們不是目標。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。例如，當收件箱已滿或地址不存在時，可以隔離電子郵件地址。 [進一步了解](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign根據傳回的錯誤類型管理錯誤地址。 如需詳細資訊，請參閱[本章節](../../delivery/using/understanding-quarantine-management.md)。


* 如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者添加到拒絕清單。

* 隔離管理也有助於降低SMS傳送成本，將錯誤的電話號碼排除在傳送途中。

## 雙選機制{#double-opt-in}

為避免將訊息傳送至無效位址、限制不當通訊並改善寄件者信譽，Adobe建議實作訂閱後確認的雙重選擇機制。 這有助於確保收件者有意訂閱。

實施此機制的詳細資訊請見[本節](../../web/using/use-cases--web-forms.md)。
