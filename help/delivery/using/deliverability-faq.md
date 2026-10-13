---
product: campaign
title: 在Adobe Campaign Classic中管理傳遞能力時的關鍵點
description: 瞭解在Adobe Campaign中管理傳遞能力時需檢查的關鍵點
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
TQID: 'https://experienceleague.adobe.com/ZRai7Bd-IRaWUQQmkuUYwXhNXp2BI-B4k-4cGq1k6uk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: 63876777-85c3-57e1-a2da-81f02956c63c
    internal-label: Deliverability
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
    internal-label: Troubleshooting
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 2%
---
# 傳遞能力疑難排解{#deliverability-faq}

您是否遇到傳遞能力問題？ 您可以在這裡找到解決方案。

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要瞭解隔離、封鎖清單以及如何從中移除地址，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target=_blank}

## MX規則錯誤 {#mx-rule-error}

**錯誤訊息「符合配額」是什麼意思？**

此訊息表示您已達到特定MX的配額限制，而且您必須等候才能傳送另一封電子郵件給此提供者。

Adobe Campaign中針對每小時可傳送的電子郵件數量進行設定。 使用此設定時務必謹慎，因為例項中定義的數字與透過ISP進行的連線數量有關，而不是與實際傳送的電子郵件數量有關。

這表示連線可以使用MX規則，而不需要成功傳送電子郵件。 在這種情況下，具有IP或信譽低的網域的設定在傳送電子郵件之前必須嘗試多個連線。 對於每次嘗試，將會使用每小時點數訊息。 因此，行銷活動的績效將會受到顯著影響。

因此，「滿足配額」不僅是設定問題，也可以與信譽連結。 在[SMTP記錄檔](../../production/using/monitoring-processes.md#smtp-errors-per-domain)中分析錯誤訊息很重要。

有關MX組態的詳細資訊，請參閱[本節](../../installation/using/email-deliverability.md#mx-configuration)。

## ISP的相同錯誤訊息 {#same-error-for-an-isp}

**為什麼我總是收到特定ISP的相同錯誤訊息？**

如果您一律收到ISP的相同錯誤訊息，則ISP可能會偵測到您的電子郵件或IP有錯誤。 請遵循下列建議：
* 檢查您是否收到大量連結到不存在電子郵件地址的失敗百分比（**使用者未知**&#x200B;個失敗）。
* 更新您的訂閱表單，以偵測所輸入網域名稱中的任何錯誤（例如：gmaul.com或yaho.com）。
* 如果您發現錯誤，指出您的訊息被宣告為垃圾訊息，或您的訊息被持續封鎖，請嘗試排除過去12個月內未開啟或點按您訊息之一的收件者，使其離開目標。

如果問題仍然存在，請連絡商業或傳遞服務，[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 從封鎖清單移除IP {#remove-from-denylist}

* **如何找出我的IP是否位於封鎖清單中？ 如何從封鎖清單移除我的IP？**

  若要檢查您的IP位址是否位於封鎖清單上，您可以使用各種網站來進行驗證，例如：
  * [MX Toolbox](https://mxtoolbox.com/)
  * [我的IP位址是什麼](https://whatismyipaddress.com)

  一般而言，IP位址檢查的結果會傳回包含封鎖清單詳細資訊以及拒絕IP位址之網站名稱的清單。

  按一下對應的連結，即可存取網站詳細資訊。 接著，您可以要求將您的網站從新增IP位址至封鎖清單的網站中除名。

  >[!NOTE]
  >
  >除名程式可能會因網站而異。 有些網站會要求您建立帳戶，有些則只需要您提供IP位址。
