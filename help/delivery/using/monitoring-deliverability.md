---
product: campaign
title: 監測Adobe Campaign Classic的交付能力
description: 瞭解有關Adobe Campaign Classic可交付性監控的工具和准則。
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---

# 監控您的可交付性{#monitoring-deliverability}

![](../../assets/common.svg)

在下面，您將瞭解Adobe Campaign提供的不同監控工具的詳細資訊，以及一些有關利用Adobe Campaign提供的功能來監控平台可交付性的附加指導。

## 關於可交付性監視 {#about-deliverability-monitoring}

此功能可通過Adobe Campaign的專用軟體包獲得。 要使用它，必須安裝此包。 完成後，重新啟動伺服器以便將包考慮在內。
* 對於托管和混合客戶端， **可交付性監控** 通過Adobe技術支援和顧問在實例上配置。 有關詳細資訊，請與您的Adobe客戶主管聯繫。

* 對於本地安裝，必須安裝 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 通過 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 的子菜單。 有關此的詳細資訊，請參閱 [安裝Campaign Classic標準包](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign Classic, **可交付性監控** 由 **[!UICONTROL Refresh for deliverability]** 工作流。 預設情況下，它安裝在所有實例上，並允許您初始化退回郵件限定規則清單、域清單和MX清單。 一旦 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 軟體包已安裝，此工作流每晚運行以定期更新規則清單，並使您能夠主動管理平台交付能力。

Deliverability包允許您訪問：

* 的 [收件箱呈現報告](inbox-rendering.md) 它使您能夠在主要電子郵件客戶端上預覽您的郵件，以便掃描內容和聲譽。
* 郵件質量（收件箱、垃圾郵件）概述。

## 監控工具 {#monitoring-tools}

您還可以使用以下工具：

* 的 **[!UICONTROL Delivery throughput]** 報告將概述給定時段內整個平台的吞吐量。 如需詳細資訊，請參閱[本節](../../reporting/using/global-reports.md#delivery-throughput)。
* 每個傳送為不同的網際網路服務提供商(ISP)生成廣播統計報告。 它顯示了一些資料質量和信譽度量，這些度量可能會影響您的可交付性，包括以下數字：
   * **[!UICONTROL Hard bounces]** 指示資料質量。 此數字應小於2%。
   * **[!UICONTROL Soft bounces]** 表明信譽。 對於任何給定的ISP，此數字不應高於10%。

   有關此內容的詳細資訊，請參閱 [傳遞統計](../../reporting/using/global-reports.md#delivery-statistics) 的子菜單。
* 更一般地說， [交貨儀表板](about-delivery-monitoring.md) 允許您訪問：
   * 這樣 [交貨摘要](delivery-dashboard.md#delivery-summary)顯示發送的詳細資訊以及成功發送、處理和發送的消息數；
   * 這樣 [交付日誌和歷史記錄](delivery-dashboard.md#delivery-logs-and-history)顯示哪些目標被排除，以及原因；
   * 這樣 [跟蹤日誌](delivery-dashboard.md#tracking-logs)顯示跟蹤資訊，如開啟和按一下。

## 監視指南 {#monitoring-guidelines}

以下是有關交付性監控的一些附加准則：

* 定期檢查 [交付吞吐量](../../reporting/using/global-reports.md#delivery-throughput) 為整個平台驗證其是否與原始設定一致。
* 檢查 [重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 已在傳遞模板中正確設定（重試期為30分鐘，重試次數超過20次）。
* 定期驗證 [彈](understanding-delivery-failures.md#bounce-mail-management) 郵箱可訪問，且帳戶不會過期。
* 檢查每個可從 [交貨儀表板](delivery-dashboard.md)確保其與遞送內容的有效性(例如「快閃銷售」應在幾分鐘內完成，而不是幾天)。
* 使用時 [波](steps-sending-the-delivery.md#sending-using-multiple-waves)，在觸發下一個波之前，驗證每個波次是否有足夠的時間完成。
* 檢查錯誤和新錯誤的數量 [檢疫](understanding-quarantine-management.md) 與其他交貨一致。
* 仔細咨詢 [交貨日誌](delivery-dashboard.md#delivery-logs-and-history) 詳細檢查突出顯示的錯誤類型（denylists、DNS問題、反垃圾郵件規則等）。
