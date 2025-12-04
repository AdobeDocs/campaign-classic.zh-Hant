---
product: campaign
title: 瞭解傳遞失敗
description: 瞭解如何瞭解傳送失敗
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 2%

---

# 瞭解傳遞失敗{#understanding-delivery-failures}

>[!NOTE]
>
>有關瞭解傳遞失敗的完整指引記錄在[Campaign v8瞭解傳遞失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures)頁面中。 本內容適用於Campaign Classic v7和Campaign v8使用者，內容包括：
>
>* 傳送失敗型別和原因（硬、軟、已忽略）
>* 同步與非同步錯誤
>* 退回郵件資格
>* 電子郵件、推播通知和簡訊錯誤型別
>* 重試管理和有效期
>* 疑難排解常見傳送故障
>
>此頁面會記錄用於混合部署和內部部署中退回郵件管理的&#x200B;**Campaign Classic v7特定設定**。

如需常見的傳送失敗概念、錯誤型別和疑難排解指南，請參閱[Campaign v8瞭解傳送失敗檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}。

## 退回郵件設定 {#v7-bounce-mail-config}

下列組態選項適用於&#x200B;**Campaign Classic v7混合/內部部署**，以管理退信處理。

### 彈回信箱設定 {#bounce-mailbox-configuration}

對於內部部署安裝，退回信箱的設定在[此區段](../../installation/using/deploying-an-instance.md#managing-bounced-emails)中有詳細說明。

非同步錯誤訊息由Adobe Campaign平台透過退信箱收集，並由inMail程式限定，以擴充電子郵件管理規則的清單。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，彈回信箱設定是由Adobe執行和管理。 不需要設定。

### 彈回郵件資格管理 {#bounce-mail-qualification-management}

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，當電子郵件傳送失敗時，Adobe Campaign傳送伺服器會從傳訊伺服器或遠端DNS伺服器收到錯誤訊息。 錯誤清單是由遠端伺服器傳回之訊息中所包含的字串所組成。 系統會為每個錯誤訊息指定失敗型別和原因。

此清單可透過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;節點取得。 它包含Adobe Campaign用來限定傳送失敗的所有規則。 內容並非詳盡無遺，且會由Adobe Campaign定期更新，使用者也可自行管理。

![](assets/tech_quarant_rules_qualif.png)

此錯誤型別第一次出現時，遠端伺服器傳回的訊息會顯示在&#x200B;**[!UICONTROL First text]**&#x200B;資料表的&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;資料行中。 如果未顯示此欄，請按一下清單右下方的&#x200B;**[!UICONTROL Configure list]**&#x200B;按鈕以選取它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign篩選此郵件以刪除變數內容（例如ID、日期、電子郵件地址、電話號碼等），並在&#x200B;**[!UICONTROL Text]**&#x200B;欄中顯示篩選結果。 變數已取代為&#x200B;**`#xxx#`**，但取代為&#x200B;**`*`**&#x200B;的位址除外。

此程式允許將相同型別的所有失敗集合在一起，並避免傳送記錄資格表格中出現多個類似錯誤的專案。

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]**&#x200B;欄位會顯示清單中訊息的出現次數。 僅限100,000次發生。 例如，如果您想要重設欄位，可以編輯該欄位。

退回郵件可能具有下列資格狀態：

* **[!UICONTROL To qualify]**：無法限定退回郵件。 資格必須指派給傳遞團隊，以確保有效的平台傳遞能力。 只要不符合，跳出郵件就不會用來擴充電子郵件管理規則的清單。
* **[!UICONTROL Keep]**：退信已合格，將由&#x200B;**重新整理傳遞能力**&#x200B;工作流程使用，以與現有電子郵件管理規則比較，並擴充清單。
* **[!UICONTROL Ignore]**： Campaign MTA會忽略退信郵件，這表示此退信絕對不會導致收件者的地址被隔離。 **重新整理傳遞能力**&#x200B;工作流程不會使用此專案，也不會傳送給使用者端執行個體。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>如果ISP發生中斷，透過Campaign傳送的電子郵件將會錯誤地標示為跳出。 若要修正此問題，您需要更新退回資格。 如需詳細資訊，請參閱[此頁面](update-bounce-qualification.md)。

### 電子郵件管理規則設定 {#email-management-rules}

透過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;節點存取郵件規則。 電子郵件管理規則會顯示在視窗的下方。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的預設引數是在部署精靈中設定的。 如需進一步資訊，請參閱[本節](../../installation/using/deploying-an-instance.md)。

預設規則如下：

>[!IMPORTANT]
>
>* 如果引數已變更，則必須重新啟動傳遞伺服器(MTA)。
>* 管理規則的修改或建立僅供專家使用者使用。

#### 傳入電子郵件 {#inbound-email}

這些規則包含可由遠端伺服器傳回的字串，可讓您限定錯誤（**Hard**、**Soft**&#x200B;或&#x200B;**Ignored**）。

電子郵件失敗時，遠端伺服器會傳回退回訊息至平台引數中指定的位址。 Adobe Campaign會比較每個退回訊息的內容與規則清單中的字串，然後為其指派三種錯誤型別之一。

>[!NOTE]
>
>使用者可以建立自己的規則。 當匯入套件以及透過&#x200B;**重新整理傳遞能力**&#x200B;工作流程更新資料時，使用者建立的規則會被覆寫。

有關退信限定的詳細資訊，請參閱[本節](#bounce-mail-qualification-management)。

#### 網域管理 {#domain-management}

對於內部部署安裝，MTA會將單一&#x200B;**網域管理**&#x200B;規則套用至所有網域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以選擇是否啟用某些識別標準和加密金鑰來檢查網域名稱，例如&#x200B;**寄件者識別碼**、**網域金鑰**、**DKIM**&#x200B;和&#x200B;**S/MIME**。
* **SMTP轉送**&#x200B;引數可讓您為特定網域設定轉送伺服器的IP位址和連線埠。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果您的郵件在寄件者地址中顯示&#x200B;**[!UICONTROL on behalf of]**，請確定不要使用&#x200B;**寄件者識別碼**&#x200B;簽署電子郵件，這是Microsoft過時的專有電子郵件驗證標準。 如果&#x200B;**[!UICONTROL Sender ID]**&#x200B;選項已啟用，請取消核取相對應的方塊並聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 您的傳遞能力不受影響。

#### MX 管理 {#mx-management}

對於內部部署安裝，MX管理規則是用來針對特定網域規範傳出電子郵件的流程。

<!--![](assets/tech_quarant_domain_rules_01.png)-->

這些規則可在部署精靈中使用，並可進行自訂：

* **[!UICONTROL MX Management]**：此規則用來控制網域外寄電子郵件的流程。 它會適時取樣退回訊息和傳送區塊。

* **[!UICONTROL Period]**：調整或封鎖訊息的時間範圍。

* **[!UICONTROL Limit]**：每個時段允許的最大訊息數。

* **[!UICONTROL Type]**：用來判斷傳送行為的錯誤型別（硬式、軟式或略過）。 如需錯誤型別定義，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}。

有關MX管理的詳細資訊，請參閱[本節](../../installation/using/email-deliverability.md#about-mx-rules)。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，MX規則和電子郵件流程管理是由Adobe作為受管理基礎結構的一部分進行管理。 如果您需要針對特定使用案例調整MX設定，請聯絡Adobe客戶服務。

## 相關主題

* [瞭解傳遞失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} （Campaign v8檔案）
* [傳遞狀態](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} （Campaign v8檔案）
* [隔離管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} （Campaign v8檔案）
* [隔離設定](understanding-quarantine-management.md) （v7混合/內部部署）
* [更新退信資格](update-bounce-qualification.md) （v7混合/內部部署）
* [電子郵件傳遞能力設定](../../installation/using/email-deliverability.md) （v7混合式/內部部署）
* [正在部署執行個體](../../installation/using/deploying-an-instance.md#managing-bounced-emails) （v7混合/內部部署）
