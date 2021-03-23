---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic可交付性管理要點
description: 在Adobe Campaign Classic管理可交付性時，需要檢查哪些要點？
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# 可傳遞性疑難排解{#deliverability-faq}

您是否遇到交付能力問題？ 您可以在這裡找到解決方案。

## MX規則錯誤{#mx-rule-error}

**錯誤訊息「配額符合」代表什麼意思？**

此訊息指出您已達到特定MX的配額限制，您必須等候才能傳送其他電子郵件給此供應商。

在Adobe Campaign，有一個設定是關於每小時可傳送的電子郵件數。 此配置必須引起警惕，因為實例中定義的數字與與與ISP進行的連接數有關，而與實際發送的電子郵件數無關。

這表示連線可使用MX規則，但無法成功傳送電子郵件。 在這種情況下，使用IP或信譽不佳的網域的組態必須先嘗試數個連線，才能傳送電子郵件。 每次嘗試都會使用每小時評分的訊息。 因此，行銷促銷活動的績效將會受到重大影響。

因此，&quot;配額滿足&quot;不僅是配置問題，還與信譽掛鈎。 分析[SMTP日誌](../../production/using/monitoring-processes.md#smtp-errors-per-domain)中的錯誤消息非常重要。

有關MX配置的詳細資訊，請參見[本節](../../installation/using/email-deliverability.md#mx-configuration)。

## ISP {#same-error-for-an-isp}的錯誤資訊相同

**為什麼對於特定ISP，我總是收到相同的錯誤訊息？**

如果您總是收到相同的ISP錯誤訊息，則ISP可能會偵測到您的電子郵件或IP有故障。 執行下列建議：
* 檢查您是否收到大部分連結至不存在電子郵件地址的失敗（**使用者未知**&#x200B;失敗）。
* 更新訂閱表單以偵測輸入的網域名稱中的任何錯誤(例如：gmaul.com或yaho.com)。
* 如果您發現錯誤，指出您的訊息已宣告為垃圾訊息，或您的訊息經常遭到封鎖，請嘗試將過去12個月中未開啟或點按其中一則訊息的收件者排除在目標位置。

如果問題仍然存在，請與[Adobe客戶服務部門的商業或交付性服務聯繫。](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)

## Denylist與隔離{#denylist-versus-quarantine}

* **拒絕清單上的電子郵件地址和隔離的電子郵件地址之間有何區別？**

   * 狀態&#x200B;**[!UICONTROL Denylisted]**&#x200B;是回饋迴路的結果（當某人將訊息報告為垃圾訊息時）。

   * 狀態&#x200B;**[!UICONTROL Quarantined]**&#x200B;是軟反彈或硬反彈的結果。
   如需詳細資訊，請參閱[本節](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔離錯誤原因意味著什麼？**

   以下是10個可能的原因：未定義、用戶未知、無效域、拒絕、錯誤忽略、無法訪問、帳戶禁用、郵箱已滿、未連接。

   有關詳細資訊，請參見[瞭解隔離管理](../../delivery/using/understanding-quarantine-management.md)。

## 從denylist {#remove-from-denylist}移除

* **我的收件者中有一個被誤加入密尼列斯特。如何從簡歷表中移除它們，以便重新開始傳送訊息？**

   * 前往&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在相應記錄的詳細資訊中，將&#x200B;**[!UICONTROL Status]**&#x200B;欄位的值設定為&#x200B;**[!UICONTROL Valid]**。
   * 保存記錄。

* **我要如何得知我的IP是否列在密文清單上？如何從密文清單移除IP?**

   若要檢查您的IP位址是否在密文清單中，您可以使用各種網站來驗證，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP地址是什麼](https://whatismyipaddress.com)

   通常，IP位址檢查的結果會傳回一個清單，其中包含拒絕IP位址的登入清單和網站名稱。

   按一下對應的連結，即可存取網站詳細資訊。 然後，您可以要求將您的網站從新增IP位址至其登入清單的網站中移除。

   >[!NOTE]
   >
   >除名程式可能因網站而異。 有些網站會要求您建立帳戶，而有些網站則只需您提供IP位址。
