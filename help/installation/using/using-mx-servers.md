---
product: campaign
title: 以 Campaign 使用 MX 伺服器
description: 瞭解MX伺服器如何與Adobe Campaign Classic協作。
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 6740b5eed33612bd7a3b217a8f53b07518f879fb
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# 以 Campaign 使用 MX 伺服器 {#using-mx-servers}

![](../../assets/v7-only.svg)

瞭解MX伺服器如何與Adobe Campaign Classic協作。

## MX伺服器 {#mx-servers}

### 什麼是MX伺服器？

郵件交換器記錄（MX記錄）是域名系統(DNS)中資源記錄的類型，指定負責代表域接受電子郵件的郵件伺服器。

### MX伺服器是如何工作的？

當您發送電子郵件時，軟體伺服器將與收件人域伺服器建立連接。 兩個伺服器之間的通信使用SMTP語言，並且一個域可以具有多個MX伺服器。 到此域的連接將從最高優先順序（最小數字）開始，其他伺服器稱為「備份」伺服器。 必須遵守連接協定。

### MX伺服器如何與Adobe Campaign協作？

在連接協定中，必須遵守規則以防止垃圾郵件和壟斷伺服器。 最重要的是：

* **允許的最大連接數**:如果尊重此數字，則IP不在密碼清單中，並且電子郵件不會因額外連接而被拒絕。
* **最大消息數**:在連接期間，必須定義允許發送的消息數。 如果未定義此數字，則伺服器將發送盡可能多的資料。 這將導致被標識為垃圾郵件製造者，並被ISP添加到密尼清單中。
* **每小時消息**:為了與您的電子聲譽相匹配，Adobe Campaign將控制您的IP每小時能夠發送的電子郵件數量。 此系統將保護您免受電子郵件拒絕或/和拒絕清單的影響。

## 無法彈出電子郵件

### 什麼是Inbounce電子郵件？

是Adobe Campaign在伺服器通信過程中處理錯誤的過程。

### Inbounce電子郵件是如何工作的？

錯誤地址將處理ISP發回的回報。 該過程將分析不同的SMTP錯誤代碼，並根據RegEx標準應用正確的操作。

例如，電子郵件地址有ISP發送的「550用戶未知」反饋。 此錯誤代碼由Adobe Campaign錯誤地址（返迴路徑地址）處理。 然後將此錯誤與RegEx標準進行比較，並應用正確的規則。 電子郵件被視為 *硬彈* （匹配類型） *用戶未知* （與原因匹配），並在第一個循環進入系統後被推入隔離。

### Adobe Campaign是如何管理的？

Adobe Campaign通過錯誤類型和原因之間的匹配來管理此過程：

* **[!UICONTROL User Unknown]**:語法正確但不存在的地址。 此錯誤被分類為硬彈跳，並在第一個錯誤內推入隔離。
* **[!UICONTROL Mailbox full]**:已達到最大容量的郵箱。 此錯誤還可能表明用戶不再使用此郵箱。 此錯誤被分類為軟彈跳，並在第三個錯誤內推入隔離，在30天後從隔離中刪除。
* **[!UICONTROL Inactive User]**:由於過去6個月中有一個非活動用戶， ISP已停用郵箱。 此錯誤被分類為軟彈跳，並在第三個錯誤內推入隔離。
* **[!UICONTROL Invalid domain]**:電子郵件地址中的域不存在。 此錯誤被分類為軟彈跳，並在第三個錯誤內推入隔離。
* **[!UICONTROL Refused]**:ISP拒絕將電子郵件發送給其用戶。 此錯誤被分類為軟彈跳，並且未推入隔離，因為錯誤未連結到電子郵件地址，而是IP或/和域信譽。

>[!NOTE]
>
>要瞭解有關交付失敗類型和原因的詳細資訊，請參閱此 [節](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

## 可交付性實例 {#deliveratbility-env}

MX規則和輸入規則的每日更新由客戶端實例中的特定工作流管理，該工作流連接到這些規則的可交付性實例所有者。

此每日更新正在為希望通過透明流程使實例保持最新的所有客戶端運行。

MX規則有6個不同的吞吐量級別，這些級別主要在升級過程中使用：

![](assets/mx-rules-throughput.png)

「自定義」模式適用於希望設定自己MX規則的高級客戶端。 激活自定義模式後，客戶端將不會由Deliverability實例更新，因為同步將關閉。

## 彈跳示例

* **用戶未知** （硬反彈）:550 5.1.1 ...用戶未知{mx003}
* **郵箱已滿** （軟反彈）:550 5.2.2超過用戶配額
* **非活動郵箱** （軟反彈）:550 5.7.1 :收件人地址被拒絕：非活動MailBox，超過6個月未加電
* **域無效** （軟反彈）:「ourdan.com」的DNS查詢失敗
* **拒絕** （軟反彈）:入站電子郵件反饋（規則「Feedback_loop_Hotmail」已與此反饋匹配）
* **無法訪問** （軟反彈）:421 4.16.55 [TS01] 由於用戶投訴過多，x.x.x.x的消息暫時被延遲

**相關主題：**
* [MX配置](../../installation/using/email-deliverability.md#mx-configuration)
* [技術電子郵件配置](../../installation/using/email-deliverability.md)
* [瞭解交付失敗](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic — 技術Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
