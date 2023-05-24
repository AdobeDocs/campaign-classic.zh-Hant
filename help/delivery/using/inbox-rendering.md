---
product: campaign
title: Campaign中的收件匣轉譯
description: 瞭解如何擷取電子郵件呈現，並在專用報告中提供
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: e011333411af79b985166a4e73592a1860749cf1
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 9%

---

# 收件匣轉譯{#inbox-rendering}



## 關於收件匣轉譯 {#about-inbox-rendering}

點按「 」之前 **傳送** 按鈕，確定您的訊息會以最佳方式顯示在各種Web使用者端、網頁郵件和裝置上的收件者。

為此，Adobe Campaign會利用 [Litmus](https://litmus.com/email-testing) 網路型電子郵件測試解決方案，用於擷取轉譯並提供在專用報表中。 這可讓您在可能接收訊息的不同內容中預覽傳送的訊息，並檢查主要桌上型電腦和應用程式中的相容性。

>[!CAUTION]
>收件匣轉譯與不相容 [週期性傳遞](communication-channels.md#recurring-delivery).

Litmus是功能豐富的電子郵件驗證和預覽應用程式。 它可讓電子郵件內容建立者在70多個電子郵件轉譯器中預覽其訊息內容，例如Gmail收件匣或Apple Mail使用者端。

適用於的行動裝置、傳訊與網頁郵件使用者端 **收件匣轉譯** 列於Adobe Campaign的 [Litmus網站](https://litmus.com/email-testing) (按一下 **檢視所有電子郵件使用者端**)。

>[!NOTE]
>
>測試傳遞中的個人化時，不需要收件匣轉譯。 可使用Adobe Campaign工具(例如 **[!UICONTROL Preview]** 和 [校樣](steps-validating-the-delivery.md#sending-a-proof).

## 正在啟用收件匣轉譯 {#activating-inbox-rendering}

[!BADGE 內部部署和混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}

對於託管和混合型使用者端，收件匣轉譯是由Adobe技術支援和顧問在執行個體上設定。 如需詳細資訊，請聯絡您的Adobe客戶主管。

對於內部部署安裝，請依照下列步驟設定收件匣轉譯。

1. 安裝 **[!UICONTROL Inbox rendering (IR)]** 透過以下方式封裝 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 功能表。 如需詳細資訊，請參閱 [安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md).
1. 透過以下方式設定HTTP型別的外部帳戶： **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** 節點。 如需詳細資訊，請參閱 [建立外部帳戶](../../installation/using/external-accounts.md#creating-an-external-account).
1. 設定外部帳戶引數，如下所示：
   * **[!UICONTROL Label]**：傳遞伺服器資訊
   * **[!UICONTROL Internal name]**：deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**： https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: 無
   * 核取 **[!UICONTROL Enabled]** 選項。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 前往 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 節點。 搜尋 **[!UICONTROL DmRendering_cuid]** 選項和聯絡支援人員，以取得需要複製到 **[!UICONTROL Value (text)]** 欄位。
1. 編輯 **serverConf.xml** 允許呼叫Litmus伺服器的檔案。 將下列行新增至 `<urlPermission>` 區段：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用下列命令重新載入設定：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能必須從主控台登出並重新登入，才能使用收件匣轉譯。

## 關於Litmus Token {#about-litmus-tokens}

由於Litmus是協力廠商服務，因此能以每次使用點數的模式運作。 每次使用者呼叫Litmus功能時，評分都會被扣除。

在Adobe Campaign中，評分與可用轉譯（稱為Token）的數量相對應。

>[!NOTE]
>
>可用的Litmus Token數量取決於您購買的Campaign授權。 檢查您的授權合約。

每次您使用 **[!UICONTROL Inbox rendering]** 傳送中的功能，每個產生的轉譯都會將您的可用Token減少一。

>[!IMPORTANT]
>
>Token會說明各個轉譯專案，而非整個收件匣轉譯報告，這表示：
>
>* 每次產生收件匣轉譯報告時，每個傳訊使用者端都會扣除一個權杖：一個Outlook 2000轉譯權杖、一個Outlook 2010轉譯權杖、一個Apple Mail 9轉譯權杖等。
>* 對於相同的傳送，如果您再次產生收件匣轉譯，可用權杖的數量會再次減少產生的轉譯數量。
>


剩餘的可用Token數量會顯示在 **[!UICONTROL General summary]** 的 [收件匣轉譯報告](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

收件匣轉譯功能通常用於測試新設計電子郵件的HTML架構。 每個轉譯最多需要大約70個權杖（取決於通常測試的環境數量）。 但是，在某些情況下，您可能需要多個收件匣轉譯報告才能完整測試您的傳送。 因此，可能需要更多權杖才能完成幾項檢查。

## 存取收件匣轉譯報告 {#accessing-the-inbox-rendering-report}

在您建立電子郵件傳送並定義其內容以及目標定位人口族群後，請遵循下列步驟。

如需建立、設計和鎖定傳送目標的詳細資訊，請參閱 [本節](about-email-channel.md).

1. 在傳遞的頂端列上，按一下 **[!UICONTROL Inbox rendering]** 按鈕。
1. 選取 **[!UICONTROL Analyze]** 以啟動擷取處理作業。

   ![](assets/s_tn_inbox_rendering_button.png)

   已傳送證明。 傳送電子郵件數分鐘後，即可在該校樣中存取轉譯縮圖。 有關傳送校樣的詳細資訊，請參閱 [本節](steps-validating-the-delivery.md#sending-a-proof).

1. 傳送後，證明會出現在傳送清單中。 連按兩下。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 前往 **收件匣轉譯** 索引標籤中。

   ![](assets/s_tn_inbox_rendering_tab.png)

   此時會顯示「收件匣轉譯」報告。

## 收件匣轉譯報告 {#inbox-rendering-report}

此報表會顯示收件者看到的收件匣呈現。 根據收件者開啟電子郵件傳遞的方式，呈現可能會有所不同：在瀏覽器中、行動裝置上或透過電子郵件應用程式。

此 **[!UICONTROL General summary]** 透過圖形色彩編碼表示法，以清單形式顯示已接收、不想要（垃圾郵件）、未接收或待接收的訊息數量。

![](assets/s_tn_inbox_rendering_summary.png)

將滑鼠停留在圖表上以顯示每種顏色的詳細資訊。

報告的主體分為三個部分： **[!UICONTROL Mobile]**， **[!UICONTROL Messaging clients]**、和 **[!UICONTROL Webmails]**. 向下捲動報告，以顯示分為這三種類別的所有呈現。

![](assets/s_tn_inbox_rendering_report.png)

若要取得每個報告的詳細資料，請按一下相對應的卡片。會針對所選取接收方法來顯示呈現。

![](assets/s_tn_inbox_rendering_example.png)
