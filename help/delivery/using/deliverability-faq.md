---
product: campaign
title: 在Adobe Campaign Classic中管理傳遞能力時的關鍵點
description: 在Adobe Campaign Classic中管理傳遞能力時，需檢查哪些要點？
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 2%

---

# 傳遞能力疑難排解{#deliverability-faq}

![](../../assets/common.svg)

您是否遇到傳遞能力問題？ 你可以在這裡找到解決方案。

## MX規則錯誤 {#mx-rule-error}

**「配額滿足」錯誤消息是什麼意思？**

此消息表示您已達到特定MX的配額限制，並且您必須等待才能向此提供程式發送另一電子郵件。

在Adobe Campaign中，會針對每小時可傳送的電子郵件數量進行設定。 此設定必須保持警惕，因為例項中定義的數字與與ISP執行的連線數量有關，而非實際傳送的電子郵件數量。

這表示連線可以使用MX規則，但不會成功傳送電子郵件。 在此情況下，具有IP或信譽低的網域的設定必須先嘗試數個連線，才能傳送電子郵件。 對於每次嘗試，都會使用每小時評分的訊息。 因此，行銷活動績效將受到重大影響。

因此，「達到配額」不僅是配置問題，而且還可以與信譽連結。 分析[SMTP日誌](../../production/using/monitoring-processes.md#smtp-errors-per-domain)中的錯誤消息非常重要。

有關MX配置的詳細資訊，請參閱[此部分](../../installation/using/email-deliverability.md#mx-configuration)。

## ISP的相同錯誤訊息 {#same-error-for-an-isp}

**為何對特定ISP一律會收到相同的錯誤訊息？**

如果您一律收到ISP的相同錯誤訊息，則ISP可能已偵測到您的電子郵件或IP有問題。 執行下列建議：
* 檢查您是否收到連結到不存在的電子郵件地址的大百分比故障（**用戶未知**&#x200B;故障）。
* 更新訂閱表單以偵測輸入的網域名稱中的任何錯誤(例如：gmaul.com或yaho.com)。
* 如果您發現錯誤，指出您的郵件被宣告為垃圾郵件，或您的郵件被持續阻止，請嘗試排除在目標前12個月內未開啟或點擊您其中一條郵件的收件人。

如果問題仍然存在，請聯絡商業或傳遞能力服務，[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 封鎖清單與隔離 {#denylist-versus-quarantine}

* **封鎖清單上的電子郵件地址與隔離的電子郵件地址之間有何差異？**

   * 狀態&#x200B;**[!UICONTROL Denylisted]**&#x200B;是反饋循環的結果（當某人將郵件報告為垃圾郵件時）。

   * 狀態&#x200B;**[!UICONTROL Quarantined]**&#x200B;是軟退信或硬退信的結果。
   如需詳細資訊，請參閱[本節](understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔離錯誤原因代表什麼？**

   原因有10個：未定義，用戶未知，無效域，拒絕，忽略錯誤，無法訪問，帳戶已禁用，郵箱已滿，未連接。

   有關詳細資訊，請參閱[了解隔離管理](understanding-quarantine-management.md)。

## 從封鎖清單中移除 {#remove-from-denylist}

* **我的一個收件者被誤添加到封鎖名單中。如何從封鎖清單中移除這些郵件，以便開始再次傳送郵件？**

   * 前往&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在相應記錄的詳細資訊中，將&#x200B;**[!UICONTROL Status]**&#x200B;欄位的值設定為&#x200B;**[!UICONTROL Valid]**。
   * 保存記錄。

* **如何找出我的其中一個IP是否列在封鎖清單中？如何從封鎖清單中移除我的IP?**

   若要檢查您的IP位址是否列在封鎖清單中，您可以使用各種網站來驗證，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP地址是什麼](https://whatismyipaddress.com)

   一般而言，IP位址檢查的結果會傳回一份清單，其中包含封鎖清單的詳細資訊，以及拒絕IP位址的網站名稱。

   按一下對應的連結，即可存取網站詳細資訊。 然後，您可以請求將您的網站從將IP位址新增至封鎖清單的網站中除名。

   >[!NOTE]
   >
   >除名程式可能會因網站而異。 有些網站會要求您建立帳戶，有些網站則只需要您提供IP位址。
