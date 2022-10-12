---
product: campaign
title: Campaign中的收件匣轉譯
description: 了解如何擷取電子郵件呈現，並在專屬報告中提供
feature: Inbox Rendering, Monitoring, Email Rendering
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: 048189f49623cf00f4c3f1f34ff4b795d80391ef
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 8%

---

# 收件匣轉譯{#inbox-rendering}

![](../../assets/common.svg)

## 關於收件匣轉譯 {#about-inbox-rendering}

在點擊 **傳送** 按鈕，確保您的郵件將以最佳方式顯示在各種Web客戶端、Web郵件和設備上。

為了允許此情況，Adobe Campaign會運用 [利特穆斯](https://litmus.com/email-testing) 網頁型電子郵件測試解決方案，可擷取呈現內容，並在專屬報表中提供。 這使您能夠在可能接收郵件的不同上下文中預覽所發送的郵件，並檢查主要案頭和應用程式的相容性。

>[!CAUTION]
>收件箱呈現與不相容 [循環傳送](communication-channels.md#recurring-delivery).

Litmus是功能豐富的電子郵件驗證和預覽應用程式。 它可讓電子郵件內容建立者在超過70個電子郵件轉譯器中預覽其郵件內容，例如Gmail收件匣或Apple Mail用戶端。

可用於的移動、郵件和Web郵件客戶端 **收件匣轉譯** 在Adobe Campaign中， [Litmus網站](https://litmus.com/email-testing) (按一下 **查看所有電子郵件客戶端**)。

>[!NOTE]
>
>在傳送中測試個人化不需要收件匣轉譯。 您可以使用Adobe Campaign工具(例如 **[!UICONTROL Preview]** 和 [校樣](steps-validating-the-delivery.md#sending-a-proof).

## 啟用收件匣轉譯 {#activating-inbox-rendering}

對於托管和混合式用戶端，收件匣轉譯是由Adobe技術支援和顧問在您的執行個體上設定。 如需詳細資訊，請連絡您的Adobe帳戶高階主管。

若為內部部署安裝，請依照下列步驟設定收件匣轉譯。

1. 安裝 **[!UICONTROL Inbox rendering (IR)]** 透過 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 功能表。 有關詳細資訊，請參閱 [安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md).
1. 透過 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** 節點。 有關詳細資訊，請參閱 [建立外部帳戶](../../installation/using/external-accounts.md#creating-an-external-account).
1. 按如下方式設定外部帳戶參數：
   * **[!UICONTROL Label]**:傳遞能力伺服器資訊
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: 無
   * 核取 **[!UICONTROL Enabled]** 選項。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 前往 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 節點。 搜尋 **[!UICONTROL DmRendering_cuid]** 選項和聯絡支援，取得需要複製到的傳送報表識別碼 **[!UICONTROL Value (text)]** 欄位。
1. 編輯 **serverConf.xml** 檔案，允許呼叫Litmus伺服器。 將下列行新增至 `<urlPermission>` 小節：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用以下命令重新載入配置：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能必須從主控台登出並重新登入，才能使用收件匣呈現。

## 關於Litmus權杖 {#about-litmus-tokens}

由於Litmus是第三方服務，因此其運作模式是按使用計分。 每次使用者呼叫Litmus功能時，都會扣除評分。

在Adobe Campaign中，評分對應至可用呈現的數量（稱為代號）。

>[!NOTE]
>
>可用的Litmus權杖數量取決於您購買的Campaign授權。 檢查您的授權合約。

每次您使用 **[!UICONTROL Inbox rendering]** 功能，每次產生的呈現都會將可用的Token減少一。

>[!IMPORTANT]
>
>代號會用於每個個別呈現，而非整個收件匣呈現報表，這表示：
>
>* 每次產生收件匣呈現報表時，每個傳訊用戶端會扣除一個代號：一個Outlook 2000呈現的代號、一個Outlook 2010呈現的代號、一個Apple Mail 9呈現的代號，以此類推。
>* 對於相同的傳送，如果您再次產生收件匣轉譯，可用代號的數量會再次減少為產生的轉譯數量。
>


剩餘的可用權杖數量會顯示在 **[!UICONTROL General summary]** 的 [收件匣呈現報告](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

收件匣轉譯功能通常用於測試新設計之電子郵件的HTML架構。 每次轉譯最多需要70個代號（視通常測試的環境數量而定）。 不過，在某些情況下，您可能需要多個收件匣呈現報表，才能完整測試您的傳送。 因此，可能需要更多代號才能完成數個檢查。

## 存取收件匣呈現報告 {#accessing-the-inbox-rendering-report}

在您建立電子郵件傳送並定義其內容以及目標定位人口族群後，請遵循下列步驟。

如需建立、設計和鎖定傳送的詳細資訊，請參閱 [本節](about-email-channel.md).

1. 在傳送的頂端列上，按一下 **[!UICONTROL Inbox rendering]** 按鈕。
1. 選擇 **[!UICONTROL Analyze]** 以啟動捕獲進程。

   ![](assets/s_tn_inbox_rendering_button.png)

   已傳送校樣。 傳送電子郵件後幾分鐘，即可在該校樣中存取呈現的縮圖。 如需傳送校樣的詳細資訊，請參閱 [本節](steps-validating-the-delivery.md#sending-a-proof).

1. 傳送後，校樣會顯示在傳送清單中。 按兩下。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 前往 **收件匣轉譯** 校樣的標籤。

   ![](assets/s_tn_inbox_rendering_tab.png)

   隨即顯示收件匣呈現報告。

## 收件匣呈現報告 {#inbox-rendering-report}

此報表會以收件者看到的方式顯示收件匣呈現。 呈現會因收件者開啟電子郵件傳送的方式而異：在瀏覽器、行動裝置或透過電子郵件應用程式。

此 **[!UICONTROL General summary]** 以清單和圖形顏色編碼表示方式呈現接收、不想要（垃圾郵件）、未接收或待接收的郵件數。

![](assets/s_tn_inbox_rendering_summary.png)

將滑鼠指標暫留在圖表上，可顯示每種顏色的詳細資訊。

報告正文分為三部分： **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]**，和 **[!UICONTROL Webmails]**. 向下捲動報告，以顯示分為這三種類別的所有呈現。

![](assets/s_tn_inbox_rendering_report.png)

若要取得每個報告的詳細資料，請按一下相對應的卡片。會針對所選取接收方法來顯示呈現。

![](assets/s_tn_inbox_rendering_example.png)
