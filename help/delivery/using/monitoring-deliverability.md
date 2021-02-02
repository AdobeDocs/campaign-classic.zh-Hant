---
solution: Campaign Classic
product: campaign
title: 監控Adobe Campaign Classic中的傳遞能力
description: 瞭解Adobe Campaign Classic中傳送性監控的工具與准則。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 11377b0218e20da9b1a5398539ebaa192801b283
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 2%

---


# 監視傳遞能力{#monitoring-deliverability}

以下是Adobe Campaign提供的不同監控工具的詳細資訊，以及傳送性監控的其他相關准則。

## 監控工具{#monitoring-tools}

使用Adobe Campaign提供的功能監控平台的傳遞能力。

Deliverability套件可讓您存取：

* 技術追蹤報告，提供日常傳送能力效能（技術監控）。 此報表可隨選提供，讓您透過指定位址的電子郵件接收每日報表。 如需詳細資訊，請聯絡Adobe客戶服務團隊。
* [收件匣轉換報表](../../delivery/using/inbox-rendering.md)可讓您在主要電子郵件用戶端上預覽訊息，以掃描內容和信譽。
* 訊息品質（收件匣、垃圾訊息）概觀。

您也可以使用下列工具：

* **[!UICONTROL Delivery throughput]**&#x200B;報告提供特定時段內整個平台的總處理能力。 如需詳細資訊，請參閱[本節](../../reporting/using/global-reports.md#delivery-throughput)。
* **[!UICONTROL Technical deliverability monitoring]**&#x200B;報表包含許多平台的傳遞能力品質指標。 如需詳細資訊，請參閱[本節](#technical-deliverability-monitoring)。
* 每個傳送都會針對不同的網際網路服務供應商(ISP)產生廣播統計報告。 它會顯示一些可能影響傳遞能力的資料品質和信譽度量，包括下列數字：
   * **[!UICONTROL Hard bounces]** 指出資料品質。此數字應小於2%。
   * **[!UICONTROL Soft bounces]** 表明信譽。對於任何給定的ISP，該數字都不應高於10%。

   有關詳細資訊，請參閱[傳送統計資訊](../../reporting/using/global-reports.md#delivery-statistics)部分。
* 通常，[傳送控制面板](../../delivery/using/about-delivery-monitoring.md)可讓您存取：
   * [delivery summary](../../delivery/using/delivery-dashboard.md#delivery-summary)，顯示發送的詳細資訊以及成功發送、處理和發送的消息數；
   * [傳送記錄檔和history](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)，顯示已排除的目標及原因；
   * [追蹤記錄檔](../../delivery/using/delivery-dashboard.md#tracking-logs)，顯示開啟和點按等追蹤資訊。

## 監視准則 {#monitoring-guidelines}

以下是有關交付能力監控的一些附加准則：

* 定期檢查整個平台的[傳送吞吐量](../../reporting/using/global-reports.md#delivery-throughput)，以驗證它是否與原始設定一致。
* 檢查傳送範本中的[retries](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)是否已正確設定（30分鐘的重試週期，以及20次以上的重試）。
* 定期驗證[bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)郵箱是否可訪問，且帳戶不會過期。
* 檢查每個傳送吞吐量，以確定其與傳送內容的有效性一致(例如：&#39;flash銷售&#39;應在幾分鐘內完成，而非數天內完成)。
* 使用[waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)時，請確認每個波片有足夠的時間完成，然後再觸發下一個波片。
* 檢查錯誤數和新的[隔離](../../delivery/using/understanding-quarantine-management.md)是否與其他傳送一致。
* 請仔細查閱[傳送記錄](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)，以檢查反白顯示的錯誤類型（登入清單、DNS問題、反垃圾訊息規則等）。

## 信號垃圾郵件{#signal-spam}

Signal Spam是法國服務，為法國ISP(Orange、SFR)提供匿名回饋迴路報告。

* 本服務可讓您追蹤法國ISP的聲譽，並追蹤客戶的活動演變。

* Signal Spam也提供直接投訴，讓使用者透過專用介面登入。 然後，這些投訴會被隔離在電子郵件地址資料庫中。

## 250ok {#deliverability-250ok}

[250](https://250ok.com/) okis是Adobe提供性內部工具的輔助監控解決方案，提供IP和網域密碼清單以及信譽指標。

提供的資訊是即時的，可提供主動幫助。

## 技術交付能力監控報告{#technical-deliverability-monitoring}

**技術傳遞能力監控**&#x200B;報表包含許多平台的傳遞能力品質指標。 您可以透過電子郵件收到此每日報表。 若要請求，請開啟特定的[支援案例](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)並指定：

* 實例的名稱
* 要傳送報表的電子郵件地址

此報表包含下列指標：

* **[!UICONTROL Reverse DNS]** :Adobe Campaign會檢查是否提供反向DNS以取得IP位址，且這會正確指向IP。

* **[!UICONTROL SPF]** （發件人策略框架）:一種驗證機制，可讓ISP和郵箱提供者檢查電子郵件傳送者是否在傳送網域獲得授權。

* **[!UICONTROL DomainKeys]** :由Yahoo開發、旨在認證電子郵件傳送者身分的服務。

* **[!UICONTROL IP and RBL domain]** （即時黑洞清單）:IP位址和網域的清單，這些網域已被拒絕列出的組織標示為傳送信譽不佳。這些清單由專屬組織維護，例如Spamhaus、Spamcop、SURBL/URIBL等。 Adobe Campaign目前會處理對RBL進行檢查，這些RBL對傳遞能力有重大影響。 這些RBL反映傳送的信譽，ISP可能會在接收您的電子郵件前參考這些信譽。

* **[!UICONTROL SNDS]** （智慧網路資料服務）:Windows  [Live Hotmail反垃圾郵件服務](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)。Hotmail是唯一提供此類資訊的ISP。 基準分數是綠色篩選結果，投訴率低於0.1%，而且零垃圾訊息陷阱。

這些指標每天上午9點更新。


<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
