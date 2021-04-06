---
solution: Campaign Classic
product: campaign
title: 搭配使用MX伺服器與Campaign
description: 瞭解MX伺服器如何與Adobe Campaign Classic搭配運作。
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 0c93193ff30737870803f9fb25019f3162dcc96d
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---


# 搭配使用MX伺服器與Campaign {#using-mx-servers}

瞭解MX伺服器如何與Adobe Campaign Classic搭配運作。

## MX伺服器{#mx-servers}

### 什麼是MX伺服器？

郵件交換器記錄（MX記錄）是域名系統(DNS)中的一種資源記錄，它指定負責代表域接受電子郵件消息的郵件伺服器。

### MX伺服器如何運作？

當您傳送電子郵件時，軟體伺服器會與收件者網域伺服器建立連線。 兩台伺服器之間的通信使用SMTP語言，而一個域可以有多個MX伺服器。 此域的連接將從最高優先順序（最小數字）開始，其他伺服器稱為「備份」伺服器。 必須遵守連接協定。

### MX伺服器如何與Adobe Campaign搭配運作？

在連接協定中，必須遵守規則，以防止寄送垃圾郵件並壟斷伺服器。 最重要的是：

* **允許的最大連接數**:如果尊重此號碼，IP就不會列在密碼清單中，而且電子郵件也不會因為額外的連線而遭到拒絕。
* **最大消息數**:在連接期間，必須定義允許發送的消息數。如果未定義此編號，則伺服器將盡可能多地發送。 這會導致ISP將其識別為垃圾郵件發送者，並將其添加到密鑰清單中。
* **每小時訊息**:為了符合您的電子聲譽，Adobe Campaign將控制您IP每小時可傳送的電子郵件數量。此系統將保護您不受電子郵件拒絕或／和拒絕列入的影響。

## 反彈電子郵件

### 什麼是Inbounce電子郵件？

這是Adobe Campaign用於處理伺服器通信過程中出錯的過程。

### Inbounce電子郵件如何運作？

錯誤地址將處理ISP發回的彈回。 該過程將分析不同的SMTP錯誤代碼，並根據RegEx標準應用正確的操作。

例如，電子郵件位址有ISP傳送的「550使用者未知」回饋。 此錯誤代碼由Adobe Campaign錯誤地址（返迴路徑地址）處理。 然後，將此錯誤與RegEx標準進行比較，並套用正確的規則。 電子郵件會被視為&#x200B;*硬彈回數*（符合類型），然後是&#x200B;*使用者未知*（符合原因），並在第一個回圈進入系統後推送到隔離區。

### Adobe Campaign是如何處理的？

Adobe Campaign利用錯誤類型和原因之間的匹配來管理此過程：

* **[!UICONTROL User Unknown]**:語法正確但不存在的地址。此錯誤會分類為硬反彈，並在第一個錯誤內推送至隔離。
* **[!UICONTROL Mailbox full]**:已達到最大容量的郵箱。此錯誤還可能表示用戶不再使用此郵箱。 此錯誤被分類為軟反彈，並在第三個錯誤內推送到隔離，並在30天後從隔離中刪除。
* **[!UICONTROL Inactive User]**:由於過去6個月中用戶處於非活動狀態，該郵箱已被ISP停用。此錯誤會分類為軟反彈，並在第三個錯誤內推送至隔離。
* **[!UICONTROL Invalid domain]**:電子郵件地址中的網域不存在。此錯誤會分類為軟反彈，並在第三個錯誤內推送至隔離。
* **[!UICONTROL Refused]**:ISP拒絕將電子郵件傳送給其使用者。此錯誤會分類為軟彈回數，不會推送至隔離，因為錯誤並未連結至電子郵件位址，而是IP或／網域信譽。

>[!NOTE]
>
>若要進一步瞭解傳送失敗類型和原因，請參閱此[章節](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

## 可傳遞性實例

MX規則和彈回數規則的每日更新是由用戶端例項中的特定工作流程管理，此工作流程會連接至這些規則的Deliverability例項擁有者。

此每日更新會針對所有希望透過透明度程式更新其執行個體的客戶執行。

MX規則有6種不同的吞吐量等級，主要用於啟動程式：

![](assets/mx-rules-throughput.png)

「自訂」模式適用於想要設定自己MX規則的進階用戶端。 啟動「自訂」模式時，Deliverability實例不會更新客戶端，因為同步將關閉。

## 反彈範例

* **使用者未知** （硬彈回數）:550 5.1.1 ...使用者未知{mx003}
* **郵箱已滿** （軟彈回數）:550 5.2.2超出用戶配額
* **非活動郵箱** （軟反彈）:550 5.7.1 :收件者地址遭拒：非活動MailBox，超過6個月未加電
* **網域無效** （軟彈回數）:&#39;ourdan.com&#39;的DNS查詢失敗
* **拒絕** （軟彈跳）:入站電子郵件彈回數（規則&#39;Feedback_loop_Hotmail&#39;已符合此彈回數）
* **無法到達** （軟彈回數）:421 4.16.55  [TS01] 由於用戶投訴過多，x.x.x.x的消息暫時被延遲

**相關主題：**
* [MX設定](../../installation/using/email-deliverability.md#mx-configuration)
* [技術電子郵件設定](../../installation/using/email-deliverability.md)
* [瞭解傳送失敗](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic-技術Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)