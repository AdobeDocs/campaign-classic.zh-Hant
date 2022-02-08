---
product: campaign
title: 管理Adobe Campaign Classic可交付性的要點
description: 管理Adobe Campaign Classic的可交付性時，需要檢查哪些關鍵點？
feature: Deliverability
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 2%

---

# 可交付性故障排除{#deliverability-faq}

![](../../assets/common.svg)

您是否遇到交付能力問題？ 你可以在這裡找到解決辦法。

## MX規則錯誤 {#mx-rule-error}

**錯誤消息「quotas met」表示什麼？**

此消息表明您已達到特定MX的配額限制，您必須等待才能向此提供程式發送其他電子郵件。

在Adobe Campaign，有一個關於每小時可發送的電子郵件數的配置。 此配置必須引起警惕，因為實例中定義的數字與與ISP進行的連接數量有關，而不是實際發送的電子郵件數量。

這意味著連接可以使用MX規則而不能成功發送電子郵件。 在這種情況下，IP或信譽低的域的配置在發送電子郵件之前必須嘗試多個連接。 對於每次嘗試，將使用每小時信用資訊。 因此，市場推廣活動表現將受到重大影響。

因此，&quot;滿額&quot;不僅是配置問題，還可以與信譽掛鈎。 分析中的錯誤消息非常重要 [SMTP日誌](../../production/using/monitoring-processes.md#smtp-errors-per-domain)。

有關MX配置的詳細資訊，請參見 [此部分](../../installation/using/email-deliverability.md#mx-configuration)。

## ISP的相同錯誤資訊 {#same-error-for-an-isp}

**為什麼對於特定的ISP，我總是收到相同的錯誤消息？**

如果您總是收到ISP的相同錯誤消息，則ISP可能已檢測到您的電子郵件或IP有故障。 執行以下建議：
* 檢查您是否收到連結到不存在的電子郵件地址的大比例失敗(**用戶未知** 失敗)。
* 更新訂閱表單以檢測輸入的域名中的任何錯誤(例如：gmaul.com或yaho.com)。
* 如果您注意到錯誤，指出您的郵件被聲明為垃圾郵件，或者您的郵件經常被阻止，請嘗試從目標端排除在過去12個月中未開啟或按一下您其中一條郵件的收件人。

如果問題仍然存在，請聯繫商業或交付服務， [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 德尼列斯特與隔離 {#denylist-versus-quarantine}

* **denylist上的電子郵件地址與隔離的電子郵件地址之間有何區別？**

   * 狀態 **[!UICONTROL Denylisted]** 是反饋循環的結果（當某人將郵件報告為垃圾郵件時）。

   * 狀態 **[!UICONTROL Quarantined]** 是軟的或硬的反彈的結果。
   如需詳細資訊，請參閱[本節](understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔離錯誤原因意味著什麼？**

   以下是10個可能的原因：未定義，用戶未知，無效域，在denylist上，被拒絕，錯誤被忽略，無法訪問，帳戶已禁用，郵箱已滿，未連接。

   有關此的詳細資訊，請參閱 [瞭解隔離管理](understanding-quarantine-management.md)。

## 從密文清單刪除 {#remove-from-denylist}

* **我的一個收件人被誤添加到密尼清單。 如何從密文者中刪除這些郵件，以便我可以再次發送郵件？**

   * 轉到 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在相應記錄的詳細資訊中，設定 **[!UICONTROL Status]** 欄位 **[!UICONTROL Valid]**。
   * 保存記錄。

* **如何查明我的IP是否在密碼清單中？ 如何從密碼清單中刪除我的IP?**

   要檢查您的IP地址是否在密碼清單中，您可以使用各種網站來驗證它，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP地址是什麼](https://whatismyipaddress.com)

   通常，IP地址檢查的結果將返回一個清單，其中包含拒絕IP地址的denylist的詳細資訊以及拒絕該IP地址的網站的名稱。

   通過按一下相應的連結，可以訪問網站詳細資訊。 然後，您可以請求從將IP地址添加到其denylist的網站中刪除您的網站。

   >[!NOTE]
   >
   >除名過程可能因網站而異。 有些站點要求您建立帳戶，而另一些站點則只需要您提供IP地址。
