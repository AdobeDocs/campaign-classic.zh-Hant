---
product: campaign
title: 認識隔離管理
description: 認識隔離管理
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# 認識隔離管理{#understanding-quarantine-management}

>[!NOTE]
>
>隔離管理的全面指引記錄在[Campaign v8隔離管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines)頁面中。 本內容適用於Campaign Classic v7和Campaign v8使用者，內容包括：
>
>* 隔離與封鎖清單概念
>* 為何將地址傳送到隔離區（硬/軟錯誤）
>* 軟性錯誤管理和錯誤計數器臨界值
>* 如何存取及識別隔離的地址
>* 如何從隔離中移除地址（自動、手動、大量）
>* 隔離管理報告
>
>此頁面會記錄用於混合部署和內部部署隔離管理的&#x200B;**Campaign Classic v7特定設定**。

如需完整的隔離管理指南，請參閱[Campaign v8隔離管理檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}。

## 隔離設定 {#v7-quarantine-config}

下列組態選項可用於&#x200B;**Campaign Classic v7混合/內部部署**&#x200B;來自訂隔離行為。

### 軟性錯誤臨界值設定 {#soft-error-threshold}

對於使用舊版Campaign MTA的內部部署，您可以在隔離地址之前修改錯誤數量以及兩個錯誤之間的期間。

若要配置這些設定：

1. 從&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**&#x200B;存取部署精靈
2. 導覽至&#x200B;**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. 設定：
   * **錯誤數**：隔離位址前的軟錯誤數上限（預設值： 5）
   * **兩個重大錯誤之間的期間**：錯誤計數的時間範圍（以秒為單位） （預設值： 86,400秒= 1天）

當錯誤計數器達到臨界值時，就會隔離該地址。 如果上次重大錯誤發生在10天以前，則會重新初始化錯誤計數器。

如需詳細資訊，請參閱[傳送傳遞](communication-channels.md) > **設定重試**&#x200B;下的&#x200B;**此頁面**。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，重試設定和錯誤臨界值由Adobe根據IP效能和網域信譽進行管理。 不需要設定。

### 資料庫清除工作流程 {#database-cleanup-workflow}

對於內部部署安裝，**[!UICONTROL Database cleanup]**&#x200B;技術工作流程會自動移除符合特定條件的隔離地址。

從&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**&#x200B;存取此工作流程。

在下列情況下，工作流程會從隔離中移除地址：

* 成功傳遞後處於&#x200B;**[!UICONTROL With errors]**&#x200B;狀態的地址
* 如果上次軟退信發生於10天以前，則是&#x200B;**[!UICONTROL With errors]**&#x200B;狀態的地址
* 30天後出現&#x200B;**[!UICONTROL With errors]**&#x200B;錯誤且處於&#x200B;**[!UICONTROL Mailbox full]**&#x200B;狀態的地址

確保此工作流程定期執行（建議：每天）以維持隔離清單衛生。

如需資料庫清理的詳細資訊，請參閱[本節](../../production/using/database-cleanup-workflow.md)。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，資料庫清理工作流程會由Adobe監控和管理。

### 推播通知隔離細節 {#push-quarantine-specifics}

對於Campaign Classic v7，推播通知隔離會遵循一般隔離機制，包含一些通道專屬行為。

對於&#x200B;**iOS**&#x200B;和&#x200B;**Android**&#x200B;推播通知，隔離機制會使用裝置代號，而非電子郵件地址。 解除安裝或重新安裝行動應用程式時，會隔離關聯的Token。

如需推播通知隔離情況(iOS和Android錯誤型別、重試行為等)的詳細資訊，請參閱[瞭解傳送失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}檔案，其中包括完整的推播通知錯誤型別表格。

### 簡訊隔離細節 {#sms-quarantine-specifics}

對於Campaign Classic v7，SMS隔離遵循一般隔離機制，某些通道特定行為與電話號碼而不是電子郵件地址有關。

SMS隔離機制會因使用的聯結器而異：

* **標準SMPP聯結器**： **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;中定義的錯誤資格規則適用於SMS傳遞。

* **延伸通用SMPP聯結器**：錯誤管理使用規則運算式(regexes)以不同的方式處理，以剖析SMSC提供者傳回的狀態報告(SR)訊息。

如需SMS隔離案例和錯誤型別的詳細資訊，請參閱[瞭解傳送失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}檔案，其中包含完整的SMS錯誤型別表格。

## 相關主題

* [隔離管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} （Campaign v8檔案）
* [瞭解傳遞失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} （Campaign v8檔案）
* [傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} （Campaign v8檔案）
* [資料庫清理工作流程](../../production/using/database-cleanup-workflow.md) （v7混合/內部部署）
* [設定傳遞重試](communication-channels.md) （v7混合/內部部署）
