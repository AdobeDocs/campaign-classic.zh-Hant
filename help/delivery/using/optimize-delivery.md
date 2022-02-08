---
product: campaign
title: 優化消息傳遞
description: 瞭解如何優化郵件傳遞
feature: Deliverability
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 8%

---

# 最佳化傳遞 {#optimize-delivery}

![](../../assets/common.svg)

甚至在開始建立交貨之前，您可以採取多項操作來保護並優化上游發送流程。

下節概述了最佳配置Adobe Campaign的最佳做法和建議程式。 遵循這些做法將最小化您可能面臨的下游問題。

## 平台效能

幾個因素直接影響伺服器效能並減緩平台運行：

* 個性化元素的數量和類型：電子郵件中的個性化功能可將每個收件人的資料從資料庫中取出。 如果存在許多個性化元素，則會增加準備交付所需的資料量。  瞭解有關中個性化的詳細資訊 [此部分](about-personalization.md)

* 伺服器載入：當營銷伺服器同時處理許多不同的任務時，會降低效能。 市場營銷伺服器需要協調所有交貨的所有傳入和傳出資料，以確保資料正確且準時。

   **提示**  — 為避免這種情況，請與您團隊的其他成員協調交貨時間安排以確保效能最佳。

* 工作流執行：監控您的工作流對於避免平台效能問題至關重要。 遵循所列准則 [在](../../workflow/using/workflow-best-practices.md#execution-and-performance)。

* 如果您符合條件，您可以利用 [市場活動控制面板功能](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant) 監視您的平台，使用 [效能監控](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=zh-Hant) 功能。

## 檢查網路配置 {#network-config}

要優化處理大量電子郵件時的傳遞，並避免被誤認為垃圾郵件製造者，請確保您擁有不會試圖隱藏伺服器身份的合法網路配置。

**提示**:使用與品牌網站對應的透明發件人地址。 例如，旅行社公司管理著華倫天奴連鎖酒店。 它擁有其網站的valentino.com域。 為了推廣巴黎的華倫天奴酒店，它使用paris.valentino.com子域。 因此，相關發件人地址可以是hotel@paris.valentino.com。

## 傳遞性管理 {#deliverability-management}

若要訪問收件人的收件箱而不反彈或標籤為垃圾郵件，您需要提高郵件的傳送率。

* 什麼是傳遞性?

   * 它指決定電子郵件是否能被收件人的伺服器接受的因素。 ISP（Internet服務提供商）會過濾他們認為是垃圾郵件的電子郵件，或阻止下載影像。 如果他們確定某個域發送的電子郵件過多，他們將對從該發件人接收的電子郵件數量設定一個限制。

   * 在檢查電子郵件的可交付性時，您要重點關注以下四個主要類別：資料質量、消息和內容、發送基礎架構和信譽。 有關此主題的更深入的瞭解，請參閱 [此部分](about-deliverability.md)。

* 應用詳細建議 [在](about-deliverability.md)。

* 請與Adobe代表聯繫以獲得幫助。

## 隔離管理 {#quarantine-management}

保持良好的隔離管理流程符合您的最大利益。

在新平台上開始發送電子郵件時，您可能會使用未完全限定的地址清單。 如果您發送到無效地址或蜜罐地址（僅為欺騙垃圾郵件製造者而建立的郵箱），這將開始降低您的平台的聲譽。 良好的隔離管理流程有助於：維護地址質量，避免網際網路訪問提供商的拒絕清單，並降低錯誤率，加快交付和吞吐量。

**提示**

* 如果您有無效地址清單，Adobe建議將其導入隔離表，通過 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**。

* 在傳遞分析期間，預設排除地址被隔離的收件人：他們不是目標。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。例如，當收件箱已滿或地址不存在時，可以隔離電子郵件地址。 [了解更多](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign根據返回的錯誤類型管理錯誤地址。 如需詳細資訊，請參閱[本章節](understanding-quarantine-management.md)。


* 如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離允許您避免被這些提供程式添加到denylist中。

* 隔離管理還有助於減少簡訊發送成本，方法是將錯誤電話號碼排除在遞送服務之外。

## 雙選擇加入機制 {#double-opt-in}

為避免向無效地址發送消息、限制不當通信並改善發送者信譽，Adobe建議採用雙選擇加入機制來確認訂閱後的確認。 這有助於確保收件人有意訂閱。

有關實施此機制的詳細資訊，請參見 [此部分](../../web/using/use-cases--web-forms.md)。
