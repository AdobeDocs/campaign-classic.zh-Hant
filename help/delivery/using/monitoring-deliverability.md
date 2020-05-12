---
title: 監控Adobe Campaign Classic中的傳遞能力
description: 瞭解Adobe Campaign Classic中傳送性監控的工具與准則。
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 74e1a883088d347cb1aab05d76b630c912411fc4
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---


# 監控傳送能力{#monitoring-deliverability}

以下是Adobe Campaign提供的不同監控工具的詳細資訊，以及傳送性監控的其他相關准則。

## 監控工具 {#monitoring-tools}

使用Adobe Campaign提供的功能監控平台的傳遞能力。

Deliverability套件可讓您存取：

* 技術追蹤報告，提供日常傳送能力效能（技術監控）。 此報表可隨選提供，讓您透過指定位址的電子郵件接收每日報表。 如需詳細資訊，請聯絡Adobe客戶服務團隊。
* 「收 [件匣」轉換報表](../../delivery/using/inbox-rendering.md) ，可讓您在主要電子郵件用戶端上預覽訊息，以掃描內容和聲譽。
* 訊息品質（收件匣、垃圾訊息）概觀。

您也可以使用下列工具：

* 報 **[!UICONTROL Delivery throughput]** 表提供特定時段內整個平台的總處理能力。 For more on this, see [this section](../../reporting/using/global-reports.md#delivery-throughput).
* 報 **[!UICONTROL Technical deliverability monitoring]** 表包含許多平台的傳遞能力品質指標。 For more on this, see [this section](#technical-deliverability-monitoring).
* 每個傳送都會針對不同的網際網路服務供應商(ISP)產生廣播統計報告。 它會顯示一些可能影響傳遞能力的資料品質和信譽度量，包括下列數字：
   * **[!UICONTROL Hard bounces]** 指出資料品質。 此數字應小於2%。
   * **[!UICONTROL Soft bounces]** 表明信譽。 對於任何給定的ISP，此數字都不應高於10%。
   如需詳細資訊，請參閱「傳送統 [計資料](../../reporting/using/global-reports.md#delivery-statistics) 」區段。
* 更一般而言，傳送 [控制面板](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) 可讓您存取：
   * 交 [付摘要](../../delivery/using/monitoring-a-delivery.md#delivery-summary)，顯示發送的詳細資訊和發送 [、處理和發送的消息數](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent) ;
   * 傳 [送記錄和歷史記錄](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)，顯示哪些目標已被排除及原因；
   * 追蹤 [記錄檔](../../delivery/using/monitoring-a-delivery.md#tracking-logs)，其中顯示追蹤資訊，例如開啟和點按。

## 監控准則 {#monitoring-guidelines}

以下是有關交付能力監控的一些附加准則：

* 定期檢查 [整個平台的傳送總處理能力](../../reporting/using/global-reports.md#delivery-throughput) ，以確認其是否與原始設定一致。
* 檢查傳 [送範本](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 中是否已正確設定重試次數（30分鐘重試，超過20次重試）。
* 定期確認彈 [回郵箱](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) ，且帳戶不會過期。
* 檢查每個傳送吞吐量，以確定其與傳送內容的有效性一致(例如： &#39;flash銷售&#39;應在幾分鐘內完成，而非數天內完成)。
* 使用波 [時](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)，請確認每個波在觸發下一波之前有足夠的時間完成。
* 檢查錯誤數和新隔離的 [數量](../../delivery/using/understanding-quarantine-management.md) ，與其他遞送一致。
* 請仔細 [查閱傳送記錄](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) ，以檢查反白顯示的錯誤類型（灰色或黑名單、DNS問題、反垃圾郵件規則等）。

## Signal Spam {#signal-spam}

Signal Spam是法國服務，為法國ISP(Orange、SFR)提供匿名回饋迴路報告。

* 本服務可讓您追蹤法國ISP的聲譽，並追蹤客戶的活動演變。

* Signal Spam也提供直接投訴，讓使用者透過專用介面登入。 然後，這些投訴會被隔離在電子郵件地址資料庫中。

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) 是Adobe可傳送性內部工具的輔助監控解決方案，提供IP、網域黑名單和信譽指標。

提供的資訊是即時的，可提供主動幫助。

## 技術交付能力監控報告 {#technical-deliverability-monitoring}

技術傳遞能力監控報告會每日更新，您可導覽至 **[!UICONTROL Monitoring]** >並 **[!UICONTROL Overview]** 按一下 **[!UICONTROL Technical monitoring]** Adobe Campaign標籤中的連結以取 **[!UICONTROL Home]** 得。 它包含許多平台的傳遞能力品質指標。

這些指標每天上午9點更新。

>[!NOTE]
>
>此外，您還可以透過電子郵件，在指定的位址接收每日報表。 透過電子郵件或Adobe Campaign Extranet，告訴我們所要求的電子郵件地址。

![](assets/s_tn_del_monitoring.png)

報表中使用下列指標：

* **[!UICONTROL Reverse DNS]** : Adobe Campaign會檢查是否提供反向DNS來識別IP位址，且這會正確指向IP。

* **[!UICONTROL SPF]** （發件人策略框架）: 一種驗證機制，可讓ISP和郵箱提供者檢查電子郵件傳送者是否在傳送網域獲得授權。

* **[!UICONTROL DomainKeys]** : 由Yahoo開發、旨在認證電子郵件傳送者身分的服務。

* **[!UICONTROL IP and RBL domain]** （即時黑洞清單）: 區塊清單組織標籤為發送信譽不佳的IP地址和域的清單。 這些清單由專屬組織維護，例如Spamhaus、Spamcop、SURBL/URIBL等。 Adobe Campaign目前會處理對RBL進行檢查，這些RBL對傳遞能力有重大影響。 這些RBL反映傳送的信譽，ISP可能會在接收您的電子郵件前參考這些信譽。

* **[!UICONTROL SNDS]** （智慧網路資料服務）: Windows [Live Hotmail反垃圾郵件服務](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)。 Hotmail是唯一提供此類資訊的ISP。 基準分數是綠色篩選結果，投訴率低於0.1%，而且零垃圾訊息陷阱。

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
