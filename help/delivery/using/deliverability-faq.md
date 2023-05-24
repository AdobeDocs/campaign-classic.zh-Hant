---
product: campaign
title: 在Adobe Campaign Classic中管理傳遞能力時的關鍵點
description: 瞭解在Adobe Campaign中管理傳遞能力時要檢查的要點
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 2%

---

# 傳遞能力疑難排解{#deliverability-faq}



您是否遇到傳遞問題？ 您可以在這裡找到解決方案。

## MX規則錯誤 {#mx-rule-error}

**「已達配額」錯誤訊息是什麼意思？**

此訊息指出您已達到特定MX的配額限制，而且您必須等候才能傳送另一封電子郵件給此提供者。

在Adobe Campaign中，有每小時可傳送電子郵件數目的設定。 此設定必須謹慎使用，因為例項中定義的數字與透過ISP執行的連線數量有關，而不是與實際傳送的電子郵件數量有關。

這表示連線可以使用MX規則，而不需要成功傳送電子郵件。 在這種情況下，具有IP或信譽較低的網域的設定在傳送電子郵件之前必須嘗試多個連線。 對於每次嘗試，將會使用每小時點數訊息。 因此，行銷活動的績效將會受到顯著影響。

因此，「滿足配額」不僅是設定問題，也可以連結到信譽。 請務必分析以下專案中的錯誤訊息： [SMTP記錄](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

如需MX設定的詳細資訊，請參閱 [本節](../../installation/using/email-deliverability.md#mx-configuration).

## ISP的相同錯誤訊息 {#same-error-for-an-isp}

**為什麼我總是收到針對特定ISP的相同錯誤訊息？**

如果您一律收到ISP的相同錯誤訊息，則您的電子郵件或IP可能被ISP偵測到有錯誤。 執行下列建議：
* 檢查您是否收到大量連結至不存在電子郵件地址的失敗(**使用者不明** 失敗)。
* 更新您的訂閱表單，以偵測所輸入網域名稱中的任何錯誤(例如：gmaul.com或yaho.com)。
* 如果您發現指出您的訊息被宣告為垃圾訊息的錯誤，或您的訊息持續遭到封鎖，請嘗試排除過去12個月內未開啟或點按您訊息之一的收件者，使其離開目標。

如果問題仍然存在，請聯絡商業或傳遞服務， [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 封鎖清單與隔離 {#denylist-versus-quarantine}

* **封鎖清單上的電子郵件地址與隔離的電子郵件地址有何不同？**

   * 狀態 **[!UICONTROL Denylisted]** 是回饋迴路（當個人將訊息回報為垃圾訊息時）的結果。

   * 狀態 **[!UICONTROL Quarantined]** 是軟退信或硬退信的結果。
   如需詳細資訊，請參閱[本節](understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔離錯誤原因代表什麼意思？**

   有10個可能的原因：未定義、使用者不明、網域無效、加入封鎖清單、已拒絕、已忽略錯誤、無法連線、帳戶已停用、信箱已滿、未連線。

   如需詳細資訊，請參閱 [瞭解隔離管理](understanding-quarantine-management.md).

## 從封鎖清單移除 {#remove-from-denylist}

* **我的一名收件者被錯誤地新增至封鎖清單。 如何將他們從封鎖清單中移除，以便我可以開始再次向他們傳送訊息？**

   * 前往 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * 在對應記錄的詳細資訊中，設定 **[!UICONTROL Status]** 欄位至 **[!UICONTROL Valid]**.
   * 儲存記錄。

* **如何找出我的IP是否位於封鎖清單中？ 如何從封鎖清單移除我的IP？**

   若要檢查您的IP位址是否在封鎖清單上，您可以使用各種網站來驗證它，例如：
   * [MX Toolbox](https://mxtoolbox.com/)
   * [我的IP位址是什麼](https://whatismyipaddress.com)

   一般而言，IP位址檢查的結果會傳回一個清單，其中包含封鎖清單的詳細資訊以及拒絕IP位址的網站名稱。

   按一下對應的連結，即可存取網站詳細資訊。 然後，您可以要求從新增IP位址至封鎖清單的網站將您的網站從封鎖清單中除名。

   >[!NOTE]
   >
   >除名程式可能會因網站而異。 有些網站會要求您建立帳戶，有些則只需要您提供IP位址。
