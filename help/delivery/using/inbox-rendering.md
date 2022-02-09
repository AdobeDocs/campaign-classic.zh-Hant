---
product: campaign
title: 市場活動中的收件箱呈現
description: 瞭解如何捕獲電子郵件呈現並在專用報告中提供
feature: Inbox Rendering, Monitoring, Email Rendering
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---

# 收件匣轉譯{#inbox-rendering}

![](../../assets/common.svg)

## 關於收件箱呈現 {#about-inbox-rendering}

在 **發送** 按鈕，確保在各種Web客戶端、Web郵件和設備上以最佳方式向收件人顯示您的郵件。

為了實現這一點，Adobe Campaign利用 [斜石](https://litmus.com/email-testing) 基於web的電子郵件測試解決方案，可捕獲呈現內容並將它們提供到專用報告中。 這樣，您就可以在接收消息的不同上下文中預覽發送的消息，並檢查主要台式機和應用程式的相容性。

Litmus是一種功能豐富的電子郵件驗證和預覽應用程式。 它允許電子郵件內容建立者在70多個電子郵件發送器中預覽其郵件內容，如Gmail收件箱或Apple郵件客戶端。

可用於 **收件箱呈現** 在Adobe Campaign，列在 [利特穆斯網站](https://litmus.com/email-testing) 按一下 **查看所有電子郵件客戶端**)。

>[!NOTE]
>
>在傳遞中test個性化功能不需要收件箱呈現。 可以使用Adobe Campaign工具(如 **[!UICONTROL Preview]** 和 [校樣](steps-validating-the-delivery.md#sending-a-proof)。

## 激活收件箱呈現 {#activating-inbox-rendering}

對於托管和混合客戶端，通過Adobe技術支援和顧問在實例上配置收件箱呈現。 有關詳細資訊，請與您的Adobe客戶主管聯繫。

對於內部安裝，請按照以下步驟配置收件箱呈現。

1. 安裝 **[!UICONTROL Inbox rendering (IR)]** 通過 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 的子菜單。 有關此的詳細資訊，請參閱 [安裝Campaign Classic標準包](../../installation/using/installing-campaign-standard-packages.md)。
1. 通過 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** 的下界。 有關此的詳細資訊，請參閱 [建立外部帳戶](../../installation/using/external-accounts.md#creating-an-external-account)。
1. 按如下方式設定外部帳戶參數：
   * **[!UICONTROL Label]**:可傳送性伺服器資訊
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: 無
   * 核取 **[!UICONTROL Enabled]** 選項。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 轉到 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 的下界。 搜索 **[!UICONTROL DmRendering_cuid]** 選項和聯繫支援，以獲取需要複製到的交貨報告標識符 **[!UICONTROL Value (text)]** 的子菜單。
1. 編輯 **serverConf.xml** 檔案，以允許調用Litmus伺服器。 將以下行添加到 `<urlPermission>` 部分：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用以下命令重新載入配置：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能必須從控制台註銷並重新登錄才能使用收件箱呈現。

## 關於Litmus令牌 {#about-litmus-tokens}

由於利特穆斯是第三方服務，因此它採用的是按使用量計的信用模式。 每次用戶調用Litmus功能時，都會扣除信用。

在Adobe Campaign，信用額與可用租金（稱為令牌）的數目相對應。

>[!NOTE]
>
>可用的Litmus令牌數取決於您購買的Campaig許可證。 檢查您的許可協定。

每次使用 **[!UICONTROL Inbox rendering]** 每個生成的呈現功能都會將可用令牌減少一個。

>[!IMPORTANT]
>
>標籤用於每個單獨的呈現，而不是整個收件箱呈現報告，這意味著：
>
>* 每次生成收件箱呈現報告時，都會為每個消息傳送客戶端扣除一個令牌：Outlook 2000呈現的一個令牌，Outlook 2010呈現的一個令牌，Apple郵件9呈現的一個令牌，等等。
>* 對於同一傳遞，如果再次生成收件箱呈現，則可用令牌的數量將再次減少。
>


剩餘的可用令牌數顯示在 **[!UICONTROL General summary]** 的 [收件箱呈現報告](#inbox-rendering-report)。

![](assets/s_tn_inbox_rendering_tokens.png)

通常，收件箱呈現功能用於test新設計電子郵件的HTML框架。 每次渲染需要大約70個令牌（具體取決於通常測試的環境數量）。 但是，在某些情況下，您可能需要使用多個收件箱來呈現報告，以完全test傳遞。 因此，可能需要更多的令牌才能完成幾項檢查。

## 訪問收件箱呈現報告 {#accessing-the-inbox-rendering-report}

在您建立電子郵件傳送並定義其內容以及目標定位人口族群後，請遵循下列步驟。

有關建立、設計和定位交貨的詳細資訊，請參閱 [此部分](about-email-channel.md)。

1. 在交貨的頂欄上，按一下 **[!UICONTROL Inbox rendering]** 按鈕
1. 選擇 **[!UICONTROL Analyze]** 啟動捕獲進程。

   ![](assets/s_tn_inbox_rendering_button.png)

   發送證據。 在發送電子郵件後幾分鐘內，可以在該證明中訪問呈現縮略圖。 有關發送校樣的詳細資訊，請參閱 [此部分](steps-validating-the-delivery.md#sending-a-proof)。

1. 發送後，證據將顯示在交貨清單中。 按兩下它。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 轉到 **收件箱呈現** 證明的標籤。

   ![](assets/s_tn_inbox_rendering_tab.png)

   將顯示「收件箱」呈現報告。

## 收件箱呈現報告 {#inbox-rendering-report}

此報告顯示收件人看到的收件箱呈現。 根據收件人開啟電子郵件傳遞的方式，呈現方式可能不同：瀏覽器、移動設備或電子郵件應用程式。

的 **[!UICONTROL General summary]** 以清單和圖形顏色編碼表示形式顯示接收、不需要的（垃圾郵件）、未接收或掛起接收的消息數。

![](assets/s_tn_inbox_rendering_summary.png)

將滑鼠懸停在圖表上，顯示每種顏色的詳細資訊。

報告主體分為三部分： **[!UICONTROL Mobile]**。 **[!UICONTROL Messaging clients]**, **[!UICONTROL Webmails]**。 向下捲動報告，以顯示分為這三種類別的所有呈現。

![](assets/s_tn_inbox_rendering_report.png)

若要取得每個報告的詳細資料，請按一下相對應的卡片。會針對所選取接收方法來顯示呈現。

![](assets/s_tn_inbox_rendering_example.png)
