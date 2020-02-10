---
title: 收件箱呈現
seo-title: 收件箱呈現
description: 收件箱呈現
seo-description: null
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 30f313cecf1c3d7c65f6524a3f86a1c28b35f679

---


# 收件箱呈現{#inbox-rendering}

## 關於收件箱呈現 {#about-inbox-rendering}

在點擊「 **傳送** 」按鈕之前，請確定您的訊息會以最佳方式顯示在各種網頁用戶端、網頁郵件和裝置上。

為此，Adobe Campaign運用 [Litmus](https://litmus.com/email-testing) web電子郵件測試解決方案來擷取轉譯，並在專用報表中提供。 這樣，您就可以在接收郵件的不同上下文中預覽發送的郵件，並檢查主要台式機和應用程式的相容性。

Litmus是功能豐富的電子郵件驗證和預覽應用程式。 它可讓電子郵件內容建立者在超過70種電子郵件轉譯器（例如Gmail收件匣或Apple mail用戶端）中預覽其訊息內容。

Adobe Campaign中可轉換 **Inbox的行動裝置、訊息傳送和網路郵件用戶端列在** Litmus網站 [(按一下「](https://litmus.com/email-testing) 檢視所有電子郵件用戶端 ****」)。

>[!NOTE]
>
>在傳送中測試個人化時，不需要產生收件匣。 您可以使用Adobe Campaign工具（例如校樣）來檢查個 **[!UICONTROL Preview]** 人 [化](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

## 啟用收件箱呈現{#activating-inbox-rendering}

對於代管和混合式用戶端，Adobe技術支援和顧問會在您的例項上設定「收件匣」轉譯。 如需詳細資訊，請洽詢您的Adobe銷售代表。

對於內部部署安裝，請遵循以下步驟來配置收件箱呈現。

1. 透過> **[!UICONTROL Inbox rendering (IR)]** >功能表 **[!UICONTROL Tools]** 安裝 **[!UICONTROL Advanced]** 套件 **[!UICONTROL Import package]** 。 如需詳細資訊，請參閱安 [裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md)。
1. 透過> **[!UICONTROL Administration]** >節點設定HTTP類型的外部 **[!UICONTROL Platform]****[!UICONTROL External Accounts]** 帳戶。 如需詳細資訊，請參 [閱建立外部帳戶](../../platform/using/external-accounts.md#creating-an-external-account)。
1. 按如下方式設定外部帳戶參數：
   * **[!UICONTROL Label]**:傳遞性伺服器資訊
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**:HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**:無
   * 勾選 **[!UICONTROL Enabled]** 選項。
   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 前往 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** >節 **[!UICONTROL Options]** 點。 搜尋選項 **[!UICONTROL DmRendering_cuid]** 和連絡支援，以取得需要複製至欄位的傳送報表識別 **[!UICONTROL Value (text)]** 碼。
1. 編輯 **serverConf.xml檔案** ，以允許對Litmus伺服器的調用。 將下列行添加到節 `<urlPermission>` 中：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用以下命令重新載入配置：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能需要從控制台登出並重新登入，才能使用「收件箱」轉換。

## 關於Litmus Token {#about-litmus-tokens}

由於Litmus是第三方服務，因此其運作模式是按使用量計分。 每次使用者呼叫Litmus功能時，就會扣除評分。

在Adobe Campaign中，評分與可用轉譯（稱為預付碼）的數目相對應。

>[!NOTE]
>
>可用的Litmus Token數目視您購買的促銷活動授權而定。 檢查您的授權合約。

每次您在傳送中使 **[!UICONTROL Inbox rendering]** 用功能時，產生的每個轉換都會將可用的Token減少一。

>[!IMPORTANT]
>
>Token帳戶是每個個別轉譯，而非整個「收件匣」轉譯報表，這表示：
>
>* 每次產生「收件匣」轉譯報表時，會扣除每個訊息傳送用戶端一個代號：一個Outlook 2000轉譯的Token、一個Outlook 2010轉譯的Token、一個Apple Mail 9轉譯的Token，等等。
>* 對於相同的傳送，如果您再次產生「收件匣」轉譯，則可用的Token數量會依產生的轉譯數量再次減少。
>



剩餘的可用代號數會顯示在「收件匣」 **[!UICONTROL General summary]** 呈現報 [表中](#inbox-rendering-report)。

![](assets/s_tn_inbox_rendering_tokens.png)

通常，「收件匣」轉換功能會用來測試新設計之電子郵件的HTML架構。 每個轉譯最多需要70個Token（視一般測試的環境數量而定）。 不過，在某些情況下，您可能需要多個收件匣轉換報表來完整測試傳送。 因此，可能需要更多的Token才能完成數項檢查。

>[!NOTE]
>
>如果您是Litmus客戶，則可以使用您自己的Litmus帳戶來布建和使用Adobe Campaign中的收件匣轉換。 如需詳細資訊，請洽詢您的Adobe銷售代表。
>
>請注意，變更您的Litmus認證可能會在Adobe Campaign中造成驗證問題。

## 訪問收件箱呈現報告 {#accessing-the-inbox-rendering-report}

在您建立電子郵件傳送並定義其內容以及目標群體後，請遵循下列步驟。

如需建立、設計和定位傳送的詳細資訊，請參閱 [本節](../../delivery/using/about-email-channel.md)。

1. 在傳送的頂端列上，按一下按 **[!UICONTROL Inbox rendering]** 鈕。
1. 選擇 **[!UICONTROL Analyze]** 以啟動捕獲進程。

   ![](assets/s_tn_inbox_rendering_button.png)

   會傳送證據。 在傳送電子郵件後幾分鐘內，就可在校對中存取轉換縮圖。 For more on sending proofs, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. 傳送後，證明會顯示在傳送清單中。 按兩下它。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 轉至校樣 **的「收件箱** 」轉換頁籤。

   ![](assets/s_tn_inbox_rendering_tab.png)

   此時將顯示「收件箱」呈現報告。

## 收件匣轉換報表 {#inbox-rendering-report}

此報告會在收件者看到收件箱時顯示它們。 轉譯會因收件者開啟電子郵件傳送的方式而有所不同：在瀏覽器、行動裝置上，或透過電子郵件應用程式。

所 **[!UICONTROL General summary]** 述消息以清單和通過圖形顏色編碼表示來呈現接收的消息、不想要的（垃圾郵件）、未接收的或待處理的接收的數量。

![](assets/s_tn_inbox_rendering_summary.png)

將滑鼠指標暫留在圖表上，可顯示每種顏色的詳細資料。

報告的內文分為三部分： **[!UICONTROL Mobile]**、 **[!UICONTROL Messaging clients]**&#x200B;和 **[!UICONTROL Webmails]**。 向下捲動報表，以顯示分成這三個類別的所有轉譯。

![](assets/s_tn_inbox_rendering_report.png)

若要取得每個報表的詳細資訊，請按一下對應的資訊卡。 顯示所選接收方法的渲染。

![](assets/s_tn_inbox_rendering_example.png)
