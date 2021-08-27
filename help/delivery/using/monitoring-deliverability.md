---
product: campaign
title: 監控Adobe Campaign Classic中的傳遞能力
description: 了解Adobe Campaign Classic中傳遞能力監控的工具和准則。
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---

# 監視傳遞能力{#monitoring-deliverability}

![](../../assets/common.svg)

以下提供Adobe Campaign所提供不同監控工具的詳細資訊，以及運用Adobe Campaign所提供功能監控平台傳遞能力的其他指引。

## 傳遞能力監視 {#configuration}

此功能可透過Adobe Campaign中的專用套件取得。 若要使用，必須安裝此套件。 完成後，重新啟動伺服器以考慮包。
* 對於托管和混合式用戶端，**傳遞能力監控**&#x200B;是由Adobe技術支援和顧問在您的執行個體上設定。 如需詳細資訊，請連絡您的Adobe帳戶高階主管。

* 若為內部部署安裝，您必須透過&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;功能表安裝&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;套件。 有關詳細資訊，請參閱[安裝Campaign Classic標準包](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign Classic中，**傳遞能力監控**&#x200B;是由&#x200B;**[!UICONTROL Refresh for deliverability]**&#x200B;工作流程管理。 預設情況下，它會安裝在所有實例上，並允許您初始化退信限定規則清單、域清單和MX清單。 安裝&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;套件後，此工作流程會在夜間執行，以定期更新規則清單，並讓您主動管理平台傳遞能力。

傳遞能力套件可讓您存取：

* [收件匣呈現報表](inbox-rendering.md)可讓您在主要電子郵件用戶端上預覽訊息，以掃描內容和信譽。
* 訊息品質概觀（收件匣、垃圾訊息）。

## 監控工具 {#monitoring-tools}

您也可以使用下列工具：

* **[!UICONTROL Delivery throughput]**&#x200B;報表提供指定時段內整個平台吞吐量的概觀。 如需詳細資訊，請參閱[本節](../../reporting/using/global-reports.md#delivery-throughput)。
* 每個傳送都為不同的網際網路服務提供者(ISP)產生廣播統計報表。 它會顯示一些可能會影響傳遞能力的資料品質和信譽度量，包括下列數字：
   * **[!UICONTROL Hard bounces]** 指出資料品質。此數字應小於2%。
   * **[!UICONTROL Soft bounces]** 表明信譽。對於任何指定的ISP，此數字都不應高於10%。

   如需詳細資訊，請參閱[傳送統計資料](../../reporting/using/global-reports.md#delivery-statistics)區段。
* 更一般地， [傳送控制面板](about-delivery-monitoring.md)可讓您存取：
   * [傳送摘要](delivery-dashboard.md#delivery-summary)，顯示傳送的詳細資訊以及成功傳送、處理及傳送的訊息數量；
   * [傳送記錄和history](delivery-dashboard.md#delivery-logs-and-history)，顯示已排除的目標及原因；
   * [追蹤記錄](delivery-dashboard.md#tracking-logs)，會顯示開啟和點按等追蹤資訊。

## 監視指南 {#monitoring-guidelines}

以下是傳遞能力監控的其他准則：

* 定期檢查整個平台的[傳送吞吐量](../../reporting/using/global-reports.md#delivery-throughput)，以確認其是否與原始設定一致。
* 檢查傳送範本中的[重試次數](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)是否已正確設定（重試期為30分鐘，重試次數超過20次）。
* 定期驗證[bounce](understanding-delivery-failures.md#bounce-mail-management)信箱是否可存取，且帳戶不會過期。
* 檢查每個傳送吞吐量，可從[傳送控制面板](delivery-dashboard.md)存取，以確保其與傳送內容的有效性一致(例如「快閃銷售」應在數分鐘（而非數天）內傳送。
* 使用[波段](steps-sending-the-delivery.md#sending-using-multiple-waves)時，請確認每個波段有足夠的時間在觸發下一個波段之前完成。
* 檢查錯誤數量和新的[隔離](understanding-quarantine-management.md)是否與其他傳送一致。
* 請仔細查閱[傳送記錄](delivery-dashboard.md#delivery-logs-and-history)，以檢查醒目提示的錯誤類型（封鎖清單、DNS問題、反垃圾訊息規則等）。

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
