---
product: campaign
title: 以 Campaign 使用 MX 伺服器
description: 瞭解MX伺服器如何與Adobe Campaign Classic搭配運作
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 1%

---

# 以 Campaign 使用 MX 伺服器 {#using-mx-servers}



瞭解MX伺服器如何搭配Adobe Campaign Classic使用。

## MX伺服器 {#mx-servers}

### MX伺服器是什麼？

郵件交換器記錄（MX記錄）是網域名稱系統(DNS)中的一種資源記錄，指定負責代表網域接受電子郵件訊息的郵件伺服器。

### MX伺服器如何運作？

當您傳送電子郵件時，軟體伺服器會與收件者網域伺服器建立連線。 兩個伺服器之間的通訊使用SMTP語言，而且網域可以有一部以上的MX伺服器。 這個網域的連線將從最高優先順序（最小數字）開始，而其他伺服器則稱為「備份」伺服器。 必須遵循連線通訊協定。

### MX伺服器如何與Adobe Campaign搭配運作？

在連線通訊協定中，必須遵循規則以防止傳送垃圾訊息和壟斷伺服器。 最重要的內容如下：

* **允許的連線數目上限**：接受此數目時，IP不在封鎖清單中，且電子郵件不會因為額外的連線而遭到拒絕。
* **訊息數目上限**：在連線期間，必須定義允許傳送的訊息數目。 如果未定義此號碼，伺服器將會傳送儘可能多的號碼。 這會導致系統識別為垃圾訊息傳送者，並由ISP新增至封鎖清單。
* 每小時&#x200B;**則訊息**：為符合您的電子信譽，Adobe Campaign將控制您的IP每小時可傳送的電子郵件數量。 此系統將保護您免受電子郵件拒絕或/和封鎖清單的侵擾。

## 傳入電子郵件

### 什麼是退回電子郵件？

這是Adobe Campaign在伺服器通訊期間處理錯誤的程式。

### 內送電子郵件如何運作？

錯誤位址將處理ISP傳回的退信。 該程式將分析不同的SMTP錯誤代碼，並根據RegEx標準套用正確的動作。

例如，電子郵件地址有由ISP傳送的意見反應「550使用者未知」。 此錯誤碼會由Adobe Campaign錯誤位址（returnpath位址）處理。 然後將此錯誤與RegEx標準進行比較，並套用正確的規則。 電子郵件會視為&#x200B;*硬退信* （符合型別），然後是&#x200B;*使用者未知* （符合原因），並在第一個回圈進入系統後推送至隔離區。

### Adobe Campaign如何管理該功能？

Adobe Campaign會透過錯誤型別和原因之間的比對來管理此程式：

* **[!UICONTROL User Unknown]**：語法正確但不存在的位址。 此錯誤會分類為硬退信，並在第一次錯誤時推送至隔離區。
* **[!UICONTROL Mailbox full]**：已達最大容量的信箱。 此錯誤也可能表示使用者已不再使用此信箱。 此錯誤會分類為軟退信，並在第三個錯誤中推送至隔離區，然後在30天後從隔離區中移除。
* **[!UICONTROL Inactive User]**：由於過去6個月的使用者不在使用中，ISP已停用信箱。 此錯誤會分類為軟退信，並在第三個錯誤中推送至隔離區。
* **[!UICONTROL Invalid domain]**：電子郵件地址中的網域不存在。 此錯誤會分類為軟退信，並在第三個錯誤中推送至隔離區。
* **[!UICONTROL Refused]**： ISP拒絕傳送電子郵件給使用者。 此錯誤會分類為軟退信且不會推送至隔離區，因為錯誤不會連結至電子郵件地址，而是IP或/網域信譽。

>[!NOTE]
>
>若要進一步瞭解傳送失敗型別和原因，請參閱此[區段](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

## 傳遞能力執行個體 {#deliveratbility-env}

MX規則和退回規則的每日更新是由使用者端執行個體中的特定工作流程管理，該工作流程已連線至這些規則的「傳遞能力」執行個體擁有者。

此每日更新正在執行中，適用所有希望透過透明度程式保持最新執行個體的使用者端。

MX規則有6個不同的輸送量層級，主要是在提升過程中使用：

![](assets/mx-rules-throughput.png)

自訂模式適用於想要設定自己MX規則的進階使用者端。 當啟動自訂模式時，使用者端將不會由傳遞能力執行個體更新，因為同步將會關閉。

## 退回範例

* **使用者不明** （硬退回）： 550 5.1.1 ...使用者未知{mx003}
* **信箱已滿** （軟退信）：超過550 5.2.2使用者配額
* **非使用中信箱** （軟退信）： 550 5.7.1 ：收件者地址已拒絕：非使用中信箱，超過6個月未使用Pop
* **網域無效** （軟退信）： &#39;ourdan.com&#39;的DNS查詢失敗
* **已拒絕** （軟退信）：傳入電子郵件退信（規則「Feedback_loop_Hotmail」符合此退信）
* **無法連線** （軟退信）： 421 4.16.55 [TS01]來自x.x.x.x的訊息因使用者過多投訴而暫時延遲

**相關主題：**
* [MX組態](../../installation/using/email-deliverability.md#mx-configuration)
* [技術電子郵件設定](../../installation/using/email-deliverability.md)
* [瞭解傳遞失敗](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic — 技術Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=zh-Hant)
