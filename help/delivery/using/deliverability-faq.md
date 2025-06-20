---
product: campaign
title: 在Adobe Campaign Classic中管理傳遞能力時的關鍵點
description: 瞭解在Adobe Campaign中管理傳遞能力時需檢查的關鍵點
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 1%

---

# 傳遞能力疑難排解{#deliverability-faq}

您是否遇到傳遞能力問題？ 您可以在這裡找到解決方案。

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
* 更新您的訂閱表單，以偵測所輸入網域名稱中的任何錯誤(例如：gmaul.com或yaho.com)。
* 如果您發現錯誤，指出您的訊息被宣告為垃圾訊息，或您的訊息被持續封鎖，請嘗試排除過去12個月內未開啟或點按您訊息之一的收件者，使其離開目標。

如果問題仍然存在，請連絡商業或傳遞服務，[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 封鎖清單與隔離 {#denylist-versus-quarantine}

* **封鎖清單上的電子郵件地址與隔離的電子郵件地址有何不同？**

   * 狀態&#x200B;**[!UICONTROL Denylisted]**&#x200B;是回饋回圈（當某人回報訊息為垃圾訊息時）的結果。

   * 狀態&#x200B;**[!UICONTROL Quarantined]**&#x200B;是軟退信或硬退信的結果。

  如需詳細資訊，請參閱[本節](understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔離錯誤原因代表什麼意思？**

  可能的原因有10個：未定義、使用者不明、網域無效、加入封鎖清單、已拒絕、已忽略錯誤、無法連線、帳戶已停用、信箱已滿、未連線。

  如需詳細資訊，請參閱[瞭解隔離管理](understanding-quarantine-management.md)。

## 從封鎖清單移除 {#remove-from-denylist}

* **我的其中一個收件者被誤新增至封鎖清單。 如何將他們從封鎖清單中移除，以便我可以再次向他們傳送訊息？**

   * 移至&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在對應的記錄的詳細資訊中，將&#x200B;**[!UICONTROL Status]**&#x200B;欄位的值設定為&#x200B;**[!UICONTROL Valid]**。
   * 儲存記錄。

* **如何找出我的IP是否位於封鎖清單中？ 如何從封鎖清單移除我的IP？**

  若要檢查您的IP位址是否位於封鎖清單上，您可以使用各種網站來進行驗證，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP位址是什麼](https://whatismyipaddress.com)

  一般而言，IP位址檢查的結果會傳回包含封鎖清單詳細資訊以及拒絕IP位址之網站名稱的清單。

  按一下對應的連結，即可存取網站詳細資訊。 接著，您可以要求將您的網站從新增IP位址至封鎖清單的網站中除名。

  >[!NOTE]
  >
  >除名程式可能會因網站而異。 有些網站會要求您建立帳戶，有些則只需要您提供IP位址。
