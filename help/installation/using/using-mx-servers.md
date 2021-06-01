---
product: campaign
title: 以 Campaign 使用 MX 伺服器
description: 了解MX伺服器如何與Adobe Campaign Classic搭配運作。
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 1%

---

# 以 Campaign 使用 MX 伺服器 {#using-mx-servers}

了解MX伺服器如何與Adobe Campaign Classic搭配運作。

## MX伺服器{#mx-servers}

### 什麼是MX伺服器？

郵件交換器記錄（MX記錄）是域名系統(DNS)中的一種資源記錄，它指定負責代表域接受電子郵件的郵件伺服器。

### MX伺服器如何運作？

發送電子郵件時，軟體伺服器將與收件人域伺服器建立連接。 兩台伺服器之間的通信使用SMTP語言，而一個域可以有多台MX伺服器。 此域的連接將從最高優先順序（最小的圖）開始，而其他伺服器稱為「備份」伺服器。 必須遵守連接協定。

### MX伺服器如何與Adobe Campaign搭配運作？

在連接協定中，必須遵守規則以防止垃圾郵件和壟斷伺服器。 最重要的是：

* **允許的最大連接數**:若遵守此編號，IP就不會列在封鎖清單中，而且電子郵件不會因為額外的連線而遭到拒絕。
* **最大消息數**:在連線期間，必須定義允許傳送的訊息數。如果未定義此編號，伺服器將盡可能發送。 這會導致被識別為垃圾郵件發送者，並被ISP添加到封鎖清單中。
* **每小時報文**:為了符合您的電子信譽，Adobe Campaign將控制您IP每小時可傳送的電子郵件數量。此系統可保護您不受電子郵件拒絕或/和拒絕。

## 退回電子郵件

### 什麼是Inbounce電子郵件？

這是Adobe Campaign在伺服器通訊期間用來處理錯誤的程式。

### Inbounce電子郵件如何運作？

錯誤地址將處理ISP傳回的退信。 此程式將分析不同的SMTP錯誤碼，並根據RegEx標準套用正確的動作。

例如，電子郵件地址含有ISP傳送的「550使用者未知」意見。 此錯誤碼會由Adobe Campaign錯誤位址（傳迴路徑位址）處理。 然後會將此錯誤與RegEx標準進行比較，並套用正確的規則。 電子郵件會被視為&#x200B;*硬退信*（與類型相符），然後是&#x200B;*使用者未知*（符合原因），並在第一個回圈進入系統後推送到隔離區。

### Adobe Campaign如何管理？

Adobe Campaign會以錯誤類型與原因之間的相符項目來管理此程式：

* **[!UICONTROL User Unknown]**:語法正確但不存在的地址。此錯誤會分類為硬退信，並在第一個錯誤內推送至隔離區。
* **[!UICONTROL Mailbox full]**:已達到最大容量的郵箱。此錯誤也可能表示使用者不再使用此信箱。 此錯誤會分類為軟退信，並在第三個錯誤內推送至隔離，並在30天後從隔離中移除。
* **[!UICONTROL Inactive User]**:由於過去6個月內使用者不活躍，ISP已停用信箱。此錯誤會分類為軟退信，並在第三個錯誤內推送至隔離。
* **[!UICONTROL Invalid domain]**:電子郵件地址中的域不存在。此錯誤會分類為軟退信，並在第三個錯誤內推送至隔離。
* **[!UICONTROL Refused]**:ISP拒絕將電子郵件傳送給其使用者。此錯誤會分類為軟退信，且不會推送至隔離區，因為錯誤未連結至電子郵件地址，而是IP或/和網域信譽。

>[!NOTE]
>
>若要進一步了解傳送失敗類型和原因，請參閱此[區段](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

## 傳遞能力例項

MX規則和入站規則的每日更新由客戶端實例中的特定工作流管理，該工作流連接到這些規則的「傳遞」實例所有者。

所有希望透過透明程式使其執行個體保持最新的用戶端，都會執行此每日更新。

MX規則有6個不同的吞吐量級別，這些級別主要用於升級過程：

![](assets/mx-rules-throughput.png)

「自定義」模式適用於想要設定自己的MX規則的高級客戶端。 啟動自訂模式時，傳遞能力實例不會更新客戶端，因為同步將關閉。

## 跳出範例

* **使用者未知** （硬退信）:550 5.1.1 ...用戶未知{mx003}
* **郵箱已滿** （軟跳出）:550 5.2.2超出用戶配額
* **非活動郵箱** （軟跳出）:550 5.7.1 :收件人地址被拒絕：非活動MailBox，超過6個月沒有開啟
* **網域無效** （軟跳出）:&#39;ourdan.com&#39;的DNS查詢失敗
* **拒絕** （軟反彈）:入站電子郵件退信（規則「Feedback_loop_Hotmail」已符合此退信）
* **無法連線** （軟跳出）:421 4.16.55  [TS01] 來自x.x.x.x的報文由於用戶投訴過多而暫時推遲

**相關主題：**
* [MX配置](../../installation/using/email-deliverability.md#mx-configuration)
* [技術電子郵件設定](../../installation/using/email-deliverability.md)
* [了解傳送失敗](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic — 技術Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)
