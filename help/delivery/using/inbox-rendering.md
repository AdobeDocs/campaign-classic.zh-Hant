---
solution: Campaign Classic
product: campaign
title: Campaign中的收件箱呈現
description: 瞭解如何擷取電子郵件轉譯，並在專屬報表中提供
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---


# 收件匣轉譯{#inbox-rendering}

## 關於收件箱呈現{#about-inbox-rendering}

在點擊&#x200B;**Send**&#x200B;按鈕之前，請確定您的訊息會以最佳方式顯示給收件者，在各種網頁用戶端、網頁郵件和裝置上。

為此，Adobe Campaign運用[Litmus](https://litmus.com/email-testing)網路型電子郵件測試解決方案來擷取轉譯，並將其提供在專屬報表中。 這樣，您就可以在接收郵件的不同上下文中預覽發送的郵件，並檢查主要台式機和應用程式的相容性。

Litmus是功能豐富的電子郵件驗證和預覽應用程式。 它可讓電子郵件內容建立者在超過70種電子郵件轉譯器（例如Gmail收件匣或Apple Mail用戶端）中預覽其訊息內容。

Adobe Campaign中&#x200B;**收件箱轉換**&#x200B;的行動裝置、傳訊和網站用戶端列在[Litmus網站](https://litmus.com/email-testing)（按一下&#x200B;**檢視所有電子郵件用戶端**）。

>[!NOTE]
>
>在傳送中測試個人化時，不需要產生收件匣。 您可以使用Adobe Campaign工具（例如&#x200B;**[!UICONTROL Preview]**&#x200B;和[Rodiops](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)）來檢查個人化。

## 激活收件箱渲染{#activating-inbox-rendering}

對於代管和混合式用戶端，Adobe技術支援和顧問會在您的例項上設定「收件匣」轉譯。 如需詳細資訊，請洽詢您的Adobe銷售代表。

對於內部部署安裝，請遵循以下步驟來配置收件箱呈現。

1. 通過&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;菜單安裝&#x200B;**[!UICONTROL Inbox rendering (IR)]**&#x200B;軟體包。 如需詳細資訊，請參閱[安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md)。
1. 通過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**&#x200B;節點配置HTTP類型的外部帳戶。 有關詳細資訊，請參閱[建立外部帳戶](../../installation/using/external-accounts.md#creating-an-external-account)。
1. 按如下方式設定外部帳戶參數：
   * **[!UICONTROL Label]**:傳遞性伺服器資訊
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**:無
   * 核取 **[!UICONTROL Enabled]** 選項。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;節點。 搜尋&#x200B;**[!UICONTROL DmRendering_cuid]**&#x200B;選項並連絡支援，以取得需要複製至&#x200B;**[!UICONTROL Value (text)]**&#x200B;欄位的傳送報表識別碼。
1. 編輯&#x200B;**serverConf.xml**&#x200B;檔案，以允許呼叫Litmus伺服器。 將以下行添加到`<urlPermission>`部分：

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

## 關於Litmus token {#about-litmus-tokens}

由於Litmus是第三方服務，因此其運作模式是按使用量計分。 每次使用者呼叫Litmus功能時，就會扣除評分。

在Adobe Campaign中，評分與可用轉譯（稱為預付碼）的數目相對應。

>[!NOTE]
>
>可用的Litmus Token數目視您購買的促銷活動授權而定。 檢查您的授權合約。

每次您在傳送中使用&#x200B;**[!UICONTROL Inbox rendering]**&#x200B;功能時，產生的每個轉譯都會將可用的Token減少一。

>[!IMPORTANT]
>
>Token帳戶是每個個別轉譯，而非整個「收件匣」轉譯報表，這表示：
>
>* 每次產生「收件匣」轉譯報表時，會扣除每個訊息傳送用戶端一個代號：一個Outlook 2000轉譯的Token、一個Outlook 2010轉譯的Token、一個Apple Mail 9轉譯的Token，等等。
>* 對於相同的傳送，如果您再次產生「收件匣」轉譯，則可用的Token數量會依產生的轉譯數量再次減少。
>



剩餘的可用標籤數顯示在[收件箱呈現報告](#inbox-rendering-report)的&#x200B;**[!UICONTROL General summary]**&#x200B;中。

![](assets/s_tn_inbox_rendering_tokens.png)

通常，「收件匣」轉換功能會用來測試新設計之電子郵件的HTML架構。 每個轉譯最多需要70個Token（視一般測試的環境數量而定）。 不過，在某些情況下，您可能需要多個收件匣轉換報表來完整測試傳送。 因此，可能需要更多的Token才能完成數項檢查。

## 訪問收件箱呈現報告{#accessing-the-inbox-rendering-report}

在您建立電子郵件傳送並定義其內容以及目標定位人口族群後，請遵循下列步驟。

如需建立、設計和定位傳送的詳細資訊，請參閱[本節](../../delivery/using/about-email-channel.md)。

1. 在傳送的頂端列上，按一下&#x200B;**[!UICONTROL Inbox rendering]**&#x200B;按鈕。
1. 選擇&#x200B;**[!UICONTROL Analyze]**&#x200B;以啟動捕獲進程。

   ![](assets/s_tn_inbox_rendering_button.png)

   會傳送證據。 在傳送電子郵件後幾分鐘內，就可在校對中存取轉換縮圖。 有關發送校樣的詳細資訊，請參閱[本節](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

1. 傳送後，證明會顯示在傳送清單中。 按兩下它。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 轉到校樣的&#x200B;**收件箱呈現**&#x200B;頁籤。

   ![](assets/s_tn_inbox_rendering_tab.png)

   此時將顯示「收件箱」呈現報告。

## 收件箱呈現報告{#inbox-rendering-report}

此報告會在收件者看到收件箱時顯示它們。 轉譯會因收件者開啟電子郵件傳送的方式而有所不同：在瀏覽器、行動裝置上，或透過電子郵件應用程式。

**[!UICONTROL General summary]**&#x200B;以清單形式和通過圖形顏色編碼表示方式顯示接收的、不想要的（垃圾郵件）、未接收或待處理接收的消息數。

![](assets/s_tn_inbox_rendering_summary.png)

將滑鼠指標暫留在圖表上，可顯示每種顏色的詳細資料。

報告的內文分為三部分：**[!UICONTROL Mobile]**、**[!UICONTROL Messaging clients]**&#x200B;和&#x200B;**[!UICONTROL Webmails]**。 向下捲動報告，以顯示分為這三種類別的所有呈現。

![](assets/s_tn_inbox_rendering_report.png)

若要取得每個報告的詳細資料，請按一下相對應的卡片。會針對所選取接收方法來顯示呈現。

![](assets/s_tn_inbox_rendering_example.png)
