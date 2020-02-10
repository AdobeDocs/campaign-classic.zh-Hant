---
title: 技術監控
seo-title: 技術監控
description: 技術監控
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# 技術監控{#technical-monitoring}

## 技術交付能力監控報告 {#technical-deliverability-monitoring}

技術傳遞能力監控報告會每日更新，您可導覽至 **[!UICONTROL Monitoring]** >並 **[!UICONTROL Overview]** 按一下 **[!UICONTROL Technical monitoring]** Adobe Campaign標籤中的連結以取 **[!UICONTROL Home]** 得。 它包含許多平台的傳遞能力品質指標。

這些指標每天上午9點更新。

>[!NOTE]
>
>此外，您還可以透過電子郵件，在指定的位址接收每日報表。 請透過電子郵件或Adobe Campaign Extranet，告訴我們要求的電子郵件地址。

![](assets/s_tn_del_monitoring.png)

報表中使用下列指標：

* **[!UICONTROL Reverse DNS]** :Adobe Campaign會檢查是否提供反向DNS來識別IP位址，且這會正確指向IP。

* **[!UICONTROL SPF]** （發件人策略框架）:一種驗證機制，可讓ISP和郵箱提供者檢查電子郵件傳送者是否在傳送網域獲得授權。

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** :由Yahoo開發、旨在認證電子郵件傳送者身分的服務。

* **[!UICONTROL IP and RBL domain]** （即時黑洞清單）:區塊清單組織標籤為發送信譽不佳的IP地址和域的清單。 這些清單由專屬組織維護，例如Spamhaus、Spamcop、SURBL/URIBL等。 Adobe Campaign目前會處理對RBL進行檢查，這些RBL對傳遞能力有重大影響。 這些RBL反映傳送的信譽，ISP可能會在接收您的電子郵件前參考這些信譽。

* **[!UICONTROL SNDS]** （智慧網路資料服務）:Windows [Live Hotmail反垃圾郵件服務](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)。 Hotmail是唯一提供此類資訊的ISP。 基準分數是綠色篩選結果，投訴率低於0.1%，而且零垃圾訊息陷阱。

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
