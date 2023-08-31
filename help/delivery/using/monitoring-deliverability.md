---
product: campaign
title: 在Adobe Campaign中監視傳遞能力
description: 瞭解Adobe Campaign中傳遞能力監視的工具和准則
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 2%

---

# 監視您的傳遞能力{#monitoring-deliverability}

在下方，您會找到Adobe Campaign所提供各種監控工具的詳細資訊，以及運用Adobe Campaign所提供功能來監控平台傳遞能力的一些其他准則。

## 關於傳遞能力監視 {#about-deliverability-monitoring}

此功能透過Adobe Campaign中的專用套件提供。 若要使用它，必須安裝此套件。 完成後，請重新啟動伺服器以納入考量的套件。
* 針對託管及混合式使用者端， **傳遞能力監視** 由Adobe技術支援和顧問在執行個體上設定。 如需詳細資訊，請聯絡您的Adobe客戶主管。

* 對於內部部署安裝，您必須安裝 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 封裝，透過 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 功能表。 有關詳細資訊，請參閱 [安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md).

在Adobe Campaign Classic中， **傳遞能力監視** 由管理 **[!UICONTROL Refresh for deliverability]** 工作流程。 依預設，它安裝在所有執行個體上，可讓您初始化退回郵件限定規則清單、網域清單和MX清單。 一旦 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 安裝套件後，此工作流程會在夜間執行，以定期更新規則清單，並讓您主動管理平台傳遞能力。

傳遞能力套件可讓您存取：

* 此 [收件匣轉譯報告](inbox-rendering.md) 可讓您預覽主要電子郵件使用者端上的訊息，以掃描內容和信譽。
* 訊息品質（收件匣、垃圾郵件）的概觀。

## 監控工具 {#monitoring-tools}

您也可以使用下列工具：

* 此 **[!UICONTROL Delivery throughput]** 報表提供指定期間內整個平台輸送量的概觀。 如需詳細資訊，請參閱[本節](../../reporting/using/global-reports.md#delivery-throughput)。
* 每次傳送都會產生不同網際網路服務提供者(ISP)的廣播統計報表。 它會顯示一些可能影響您傳送能力的資料品質和信譽量度，包括下列數字：
   * **[!UICONTROL Hard bounces]** 表示資料品質。 此數字應小於2%。
   * **[!UICONTROL Soft bounces]** 表示信譽。 任何特定ISP的這個數字都不應超過10%。

  有關詳細資訊，請參閱 [傳遞統計資料](../../reporting/using/global-reports.md#delivery-statistics) 區段。
* 一般而言， [傳遞儀表板](about-delivery-monitoring.md) 可讓您存取：
   * 此 [傳遞摘要](delivery-dashboard.md#delivery-summary)，顯示傳送的詳細資訊，以及成功傳送、處理和傳送的訊息數目；
   * 此 [傳遞記錄和歷史記錄](delivery-dashboard.md#delivery-logs-and-history)，顯示已排除的目標以及排除原因；
   * 此 [追蹤記錄](delivery-dashboard.md#tracking-logs)，會顯示開啟和點按次數等追蹤資訊。

## 監視指南 {#monitoring-guidelines}

以下是傳遞能力監視的其他准則：

* 定期檢視 [傳遞總處理能力](../../reporting/using/global-reports.md#delivery-throughput) 以便整個平台驗證其是否與原始設定一致。
* 檢查 [重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 已在傳遞範本中正確設定（重試期間為30分鐘，重試次數超過20次）。
* 定期確認 [跳出](understanding-delivery-failures.md#bounce-mail-management) 信箱可存取，且帳戶不會過期。
* 檢查每個傳遞輸送量，可從 [傳遞儀表板](delivery-dashboard.md)，以確保其與傳送內容的有效性一致（例如「flash sales」應在幾分鐘內傳送，而非幾天）。
* 使用時 [波段](steps-sending-the-delivery.md#sending-using-multiple-waves)，確認每個波段都有足夠的時間完成，才能觸發下一個波段。
* 檢查錯誤數及新的 [隔離](understanding-quarantine-management.md) 與其他傳遞一致。
* 請仔細查閱 [傳遞記錄](delivery-dashboard.md#delivery-logs-and-history) 詳細檢查反白顯示的錯誤型別（封鎖清單、DNS問題、反垃圾郵件規則等）。
