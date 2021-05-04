---
solution: Campaign Classic
product: campaign
title: 設定促銷活動選項
description: 瞭解如何設定促銷活動選項
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '3927'
ht-degree: 0%

---

# Campaign Classic 選項清單{#configuring-campaign-options}

**[!UICONTROL Administration / Platform / Options]**&#x200B;節點允許您配置Adobe Campaign選項。

>[!NOTE]
>
>修改或更新Adobe Campaign選項只能由專家用戶執行。

其中一些是在安裝促銷活動時內建的，其他則可視需要手動新增。 可用選項會根據隨實例安裝的軟體包而有所不同。

## 傳送 {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> 從可傳遞性實例中檢索到的最後一個broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> 上次broadLogMsg發送到可傳遞性實例的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 傳送報表識別碼。 請聯絡支援以取得您的識別碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 要對收件箱渲染使用測試地址的結構清單。 （元素名稱以逗號分隔）例如：custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 可讓您在指定特定運算元或運算元群組以在傳送屬性中開始傳送時，允許負責傳送的運算元確認傳送。</p><p> 若要這麼做，請輸入"1"作為值來啟動選項。 若要停用此選項，請輸入"0"。</p><p> 然後，傳送確認程式會依預設運作：只有為傳送屬性（或管理員）中指定的運算元或運算元群組才能確認並執行傳送。 請參閱<a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">本節</a>。</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign使用「Nms_DefaultRcpSchema」全局變數與預設接收方資料庫(nms:recipient)對話。<br /> 選項值必須與與匹配外部收件人表的方案名稱相對應。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 收件者人數下限，以便將交貨視為計費報表中的主要交貨。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 新模板的預設路由服務提供商。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 為一次傳送而建立的BroadLog數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> 每個事務插入（表格中）日誌(broadLogs):每批要處理的行數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 分析中部來源補充交貨時的交貨部件分組大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 傳送的預設傳送期間（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 用於標準化傳送訊息的規則運算式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 輸入"1"作為值，可以排除不想再聯繫的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> 輸入"1"作為值可讓您自動忽略雙倍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 可讓您定義回覆訊息時使用的錯誤位址語法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 可讓您定義傳送訊息時使用之起始位址的語法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 可讓您定義逾時限制（以秒為單位），以便在擷取從個人化URL下載並附加至電子郵件的影像時，從伺服器取得回應。 如果超出此值，則無法傳送訊息。 預設值為60秒。<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 可讓您定義從個人化URL下載並附加至電子郵件的影像所允許的最大大小（以位元組為單位）。 預設值為100,000位元組。 當傳送校樣並下載影像以處理電子郵件時，如果影像大小超過此值，或發生下載問題，傳送記錄中會顯示錯誤，而校樣傳送將會失敗。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 可讓您在電子郵件或交易式電子郵件範本中設定附件數上限。 如果超過此值，則傳送分析記錄檔或發佈交易式電子郵件範本時會顯示警告。 預設值為1個附件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> 分析期間的最大重試次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> 出版物指令碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> 停用推送訊息的broadLogMsg計數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> 在傳送精靈中顯示訊息權重。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> 如果使用者留空，則預設的例項層級「error」電子郵件地址會用於電子郵件傳送。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 如果使用者留空，則預設的「寄件者」電子郵件位址為例項層級，用於傳送電子郵件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 如果使用者留空，則預設的「回覆」電子郵件位址位於例項層級，用於傳送電子郵件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 客戶的公用名稱。 用於向收件者顯示的某些警告訊息。<br /> 「您收到此訊息是因為您已與*****或附屬公司聯絡。不再接收來自*****"的消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 如果用戶留空，則預設的「from」電子郵件標籤位於用於電子郵件傳送的實例級別。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 如果使用者留空，則預設的「回覆」電子郵件標籤位於電子郵件傳送的例項層級。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 兩次重試電子郵件的間隔（秒）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 電子郵件訊息的重試時段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> 用於計算臨時傳送消息加權的公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 授權轉寄電子郵件地址清單（來自傳入郵件處理模組）。 這些位址必須以逗號（或*）分隔，才能允許全部使用。 例如xyz@abc.com、pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> 用於'lineImage' servlet的AES密鑰，用於編碼URL(LINE channel)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> 在頻道「電子郵件」上（用作預設值）:在將收件人隔離之前發送期間SOFT錯誤時，接受的最大錯誤數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailInvergityErrorDelay</span> <br /> </td> 
   <td> 在頻道「電子郵件」上（用作預設值）:自上次引用的SOFT錯誤以來，在考慮到新的SOFT錯誤之前所花費的最短時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> 在頻道「行動」上：在將收件人隔離之前發送期間SOFT錯誤時，接受的最大錯誤數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileInvergiativeErrorDelay</span> <br /> </td> 
   <td> 在頻道「行動」上：自上次引用的SOFT錯誤以來，在考慮到新的SOFT錯誤之前所花費的最短時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 允許指定最大時間段（以小時為單位），以限制每次執行同步工作流時恢復的廣播數。</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> MidSourcing會話中可以並行運行的最大調用數（預設情況下為3）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 自訂延遲（以分鐘為單位），之後傳送會視為「延遲」，預設為30分鐘。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>在計算正在運行的交貨數時，<span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span>技術工作流將使用此選項。</p>它允許您定義超過天數，以便將狀態不一致的交貨從運行交貨的計數中排除。</p><p>依預設，值會設為"7"，這表示將排除7天前不一致的傳送。</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> 發件人地址的行1。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> 發件人地址的第3行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> 發件人地址的第4行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> 發件人地址行6。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> 發件人地址行7。<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> 鏡像頁伺服器的URL（預設情況下，應與NmsTracking_ServerUrl相同）。<br /> 在傳送定義中未指定URL時，此值是電子郵件傳送的預設值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> 已發送SMS消息的參數：發送到SMS網關以指示消息優先順序的資訊。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> 發送SMS消息時重試的次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> 執行SMS消息重試的期間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> <span class="uicontrol">NmsUserAgent</span>統計資訊的上次合併日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> 包含網頁區段及其狀態的選項的名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> 啟用／停用Code128的特殊字元支援。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 電子郵件地址的有效字元。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 將此選項與"0"值一起添加，以禁用傳送版本的XML代碼（按一下右鍵/ <span class="uicontrol">編輯XML原始碼</span>或<span class="uicontrol">CTRL + F4</span>快捷方式）。<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## 資源 {#resources}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> 在Adobe Campaign客戶端控制台中發佈的資源位置。 請參閱<a href="../../delivery/using/formatting.md#image-referencing">本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> 在Adobe Campaign客戶端控制台中預覽的資源位置。 請參閱<a href="../../delivery/using/formatting.md#image-referencing">本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 上傳期間跳過的影像的URL遮色片清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 影像上傳的設定。 值可以是無／追蹤／指令碼／清單（可以由運算子的選用設定覆寫）。 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 要儲存伺服器上映像的資料夾。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 顯示標誌的空間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 發佈的根資料夾。<br /> 有關產生HTML和文字內容的詳細資訊，請參 <a href="../../delivery/using/using-a-content-template.md">閱本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 可讓您定義儲存傳送中所用影像的伺服器，讓瀏覽器取得這些影像。<br /> 針對建置版本  &lt;&gt;<br /> 對於建置版本&gt; 5098，我們會改用傳送的公用URL或 <span class="uicontrol">XtkFileRes_Public_</span> URL選項的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> 可讓您設定影像上傳的例項名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> 可讓您設定影像上傳的密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> 可讓您設定影像上傳的媒體URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> 傳送之線上資源的預設有效期間（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> 公共資源檔案的新URL。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 促銷活動與工作流程管理{#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> 顯示此月數的行銷歷史記錄。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> 促銷活動的預設有效期（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> 可由operationMgt工作流開始的一次處理的傳送／工作流／假設／模擬作業的最大數量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> 允許您監視<a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>技術工作流執行。 激活（值"1"）後，執行資訊將記錄在工作流審計日誌中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 在排程模式中定位和擷取條件的時段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 自動重新計算表統計資訊之後受影響的記錄數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 要在匯出報表的右上角顯示標誌。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 在檢查已暫停的工作流程之間等待的天數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 通過輸入"1"作為值，激活工序所有者對交貨的驗證。 要停用此選項，請輸入"0"。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> 要載入至工作流程「行銷資源通知」活動中的其他JS程式庫。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 安全性 {#security}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (安裝相容模式：build&gt;6000)啟動時（值"1"），此選項允許使用資料庫中儲存的舊密碼來連接到外部帳戶或實例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 此密鑰用於加密資料庫中的大多數口令。 （外部帳戶、LDAP密碼……）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 如果選取1，此選項可允許javascript中的privilegeEscalation。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 如果選擇1，此選項將在檔案下載期間禁用ACL控制（通過fileDownload.jsp）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 如果選取1，此選項會停用Javascript中的檔案沙盒功能。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> 如果設為'true'，則授權的非管理員運算子會透過部署精靈更新xtkOption值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> 如果選擇1，此選項允許使用decryptString解密某些密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> 輸入"1"值，通過在刪除記錄之前修改其"modified by"欄位，跟蹤刪除mData中具有審計線索資訊的元素。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 消息中心{#message-center}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> 個人化JavaScript程式庫，以豐富事件。 必須包含這兩個函式的實作：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">methingRtEvents(aiEventId);</span> :豐富並儲存資料庫中的事件(其 <span class="uicontrol"></span> 中aiEventId對應於處理的即時事件表)。</p> </li> 
     <li> <p> <span class="uicontrol">menchingBatchEvents(aiEventId);</span> :豐富和保存資料庫中的事件(其中 <span class="uicontrol"></span> aiEventId與已處理批次事件的ID表相對應)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 透過傳送記錄更新上次事件狀態的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> 將JavaScript程式庫個人化，以處理路由事件。 必須包含這兩個函式的實作：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> :傳回所選用以處理即時事件(其中 <span class="uicontrol"></span> iEventId對應於所處理之即時事件的ID)的交易訊息的內部名稱。</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> :傳回選定處理批處理事件的事務性消息的內部名稱(其中 <span class="uicontrol"></span> iEventId與已處理批處理事件的ID相對應)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> 即時事件平均發送時間的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> 即時事件平均傳送時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> 即時事件平均處理時間的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> 即時事件平均處理時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> 排隊即時事件的平均數的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 即時事件的平均排隊時間的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 即時事件平均佇列時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 排隊即時事件的平均數的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> 處理即時事件錯誤的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> 處理即時事件錯誤的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> 排隊即時事件的最大數目的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 排隊即時事件的最大數目的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 排隊即時事件最少數的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 排隊即時事件最少數的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 等待待定即時事件隊列的關鍵條件前的閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 暫掛即時事件佇列的警告前臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> 即時事件吞吐量的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> 即時事件吞吐量的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> 事件路由的重組大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> 更新RtEvent狀態的指標（擷取資料之前的最後一個日期）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> 用於發送歡迎消息的消息中心伺服器URL(LINE channel)。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 資料庫 {#database}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> 定義上次運行清除進程的時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除廣告的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除事件歷史記錄的延遲。</p><p>
   在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除事件的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除事件統計資料的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_CompetionPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中刪除主張的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中擦除隔離的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycleadDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除回收的遞送的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除拒絕的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除追蹤記錄檔的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除追蹤統計資料的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除訪客的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除工作流程結果的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果修改選項清單中的值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse連接器選項。<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>可讓您根據以下潛在值影響所有工作流和PostgreSQL資料庫查詢的「無條件停止」行為：<ul>
    <li><p>0 —— 預設值：停止工作流進程，對資料庫沒有影響<p></li>
    <li><p>1 - pg_cancel_backend:停止工作流進程並取消資料庫中的查詢<p></li>
    <li><p>2 - pg_terminate_backend:停止工作流進程並終止資料庫中的查詢<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> 要包含Adobe Campaignootb表資料的表空間的名稱。<br />請參 <a href="../../installation/using/creating-and-configuring-the-database.md">閱建立和配置資料庫</a>。</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> 要包含Adobe Campaignootb表索引的表空間的名稱。<br />請參 <a href="../../installation/using/creating-and-configuring-the-database.md">閱建立和配置資料庫</a>。</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> 要包含Adobe Campaign工作表資料的表空間的名稱。<br />請參 <a href="../../installation/using/creating-and-configuring-the-database.md">閱建立和配置資料庫</a>。</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> 要包含Adobe Campaign工作表索引的表空間的名稱。<br />請參 <a href="../../installation/using/creating-and-configuring-the-database.md">閱建立和配置資料庫</a>。</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> 允許您為Microsoft SQL Server上的工作表配置單獨的資料庫，以優化備份和複製。 該選項與臨時資料庫的名稱相對應：如果指定，工作表將寫入此資料庫。 範例：'tempdb.dbo'。 （請注意，名稱必須以點結尾）。 <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">顯示全文</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Adobe Campaign實例的時區。 請參閱<a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuration</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> 資料庫的字串欄位是否使用NChar定義？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> 資料庫的'datetime'欄位是否儲存時區資訊？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> 資料庫的ID。 以'u'開頭，用於Unicode資料庫。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 已新增前置詞至自動產生的內部名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> xtk:schema和xtk:srcSchema上的查詢返回的結果數上限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 所有在此時間之後建立的自訂結構描述，若使用autopk="true"而未使用屬性"pkSequence"，將會取得自動產生的序列"auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq。 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 在移轉期間，樹狀結構會根據新版本標準自動重新組織。<br /> 此選項可讓您停用導覽樹的自動移轉。如果您使用它，在遷移後，您必須刪除過時的資料夾，添加新資料夾並運行所有必要的檢查。<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">資料類型：整</span> 數</p> </li> 
     <li> <p> <span class="uicontrol">值（文字）</span> :1 </p> </li> 
    </ul> 只有在現成可用的導覽樹已經過太多變更時，才應使用此選項。<br /> 有關此的詳細資訊，請參 <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">閱本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> <span class="uicontrol">NmsEmailErrorStat</span>表清理的上次處理日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> 有關Postupgrade中發生的錯誤的資訊，請遵循下列語法：<br /> <strong>{Build number}:{mode:pre/post/...}:{發生錯誤的'lessThan'/'greaterOrEquelThan' + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> 輸入"1"值，以便不通過清除工作流執行統計資訊更新。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 整合{#integration}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> 可用於AEMAdobe Campaign的資源類型。 值必須以逗號分隔。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> 可讓您設定Experience Cloud觸發器。 資料類型為「長文字」，且必須為JSON格式。 請參閱<a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">如何搭配Adobe Campaign Classic使用Experience Cloud觸發器。<br /></a> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;&gt;_&lt;&gt;</span> <br /> </td> 
   <td> 當透過CRM連接器從協力廠商系統匯入資料時，會使用此選項。 啟用此選項可讓您僅收集自上次匯入後修改的物件。 必須手動建立並填充此選項，如下所示： 
    <ul> 
     <li> <p> <span class="uicontrol">內部名稱</span> :LASTIMPORT_&lt;&gt;_&lt;&gt;</p> </li> 
     <li> <p> <span class="uicontrol">值（欄位）</span> :上次導入的日期，格式為yyyy/MM/dd hh:mm:ss。 </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Adobe Target伺服器用於整合。 預設已選取此選項。 此值與Adobe Target域伺服器相對應，後面跟著值/m2。 例如：tt.omtrdc.net/m2。<br /> 請參 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">閱本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target組織名稱。 此值與Adobe Target客戶機的名稱相對應。<br /> 請參 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">閱本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> 用於與Adobe Audience Manager整合的選項。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> 用於與Adobe Audience Manager整合的選項。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Teradata連接器選項。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> 配置介面選項。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 選件{#offers}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> 每個SQL事務更新的抵用券數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompetationSynchControl_</span> <br /> </td> 
   <td> '+ [提案的架構] + "_" + extAccountSource。@executionInstanceId + [命題的架構] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompositionSynchExec_</span> <br /> </td> 
   <td> '+ [提案的架構] + "_" + extAccountSource。@executionInstanceId + "_" + extAccountTarget。@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 同步工作流跟蹤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 啟用／停用非同步命題寫入（「0」停用，「1」啟用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> 可讓您啟用抵用券。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 伺服器{#server}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> 執行實例標識符。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> 傳送帳單報表時使用的客戶識別碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> 用於訪問應用程式伺服器的內部基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> 上次升級前的AC實例的構建編號。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> 公用Web應用程式伺服器的基本URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> 可讓您在移轉後繼續使用舊的未宣告SQL函式。 由於此選項會帶來安全風險，我們強烈建議不要使用此選項。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤 {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> 可讓您啟用追蹤的選項。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Tracked-URL計算指令碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> 可讓您定義追蹤伺服器的外部帳戶。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> 可讓您定義追蹤伺服器上的例項名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> 上次將追蹤資訊與新資料整合時。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> 開啟URL計算指令碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> 追蹤伺服器的密碼<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> 指標會追蹤透過其ID和日期處理的最後一個訊息事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> 正面追蹤伺服器的安全URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> 正面追蹤伺服器的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> 用於連絡追蹤伺服器的URL清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> 瀏覽器識別規則集。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> 用於計算網頁追蹤標籤的指令碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> 專為網頁追蹤管理而設計的虛擬傳送名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> 可讓您定義網頁追蹤模式。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 隱私權 {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> 如果選取選項1，您必須在第二個步驟中手動確認介面中的刪除。 否則，將刪除資料，而不進行確認。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 請求之間等待刪除確認的延遲已取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> 處理／刪除隱私請求時允許的最大錯誤數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> 在佇列上建立請求之間的延遲，並刪除請求資料。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> 啟用LDAP伺服器，以驗證用戶並向用戶提供授權。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> 應用程式登錄以聯繫伺服器以進行各種搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> 應用程式登入的加密密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> 啟用在Adobe Campaign自動建立運算子和權限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> 基於登錄的LDAP DN的計算公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> 啟用目錄中的DN搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> 搜索基礎。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN搜索篩選器。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> 搜索範圍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> 用於聯繫LDAP伺服器的身份驗證類型(plain、md5、lds、ntlm、dpa)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> 啟用從LDAP目錄到Adobe Campaign命名權限的授權和組同步。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 包含授權名稱的LDAP屬性。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 搜索基礎。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 搜尋使用者授權篩選。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> 用於從LDAP授權中提取Adobe Campaign權限名稱的表達式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> 搜索範圍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP伺服器地址（通過指定':'作為分隔符可以指定埠）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 網路表單{#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> 設定為1的值將允許將捲動條添加到詳細資訊表單中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> 在「其他伺服器」模式下用於Web表單失效的實例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> 在「其他伺服器」模式下用於Web表單失效的實例的口令。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 可讓您指定Web表單失效模式的選項：本端：若選項為「追蹤」，則使用追蹤伺服器，並搭配「其他伺服器」選項使用個人化清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span> <br /> </td> 
   <td> 要因Web表單失效而聯繫的伺服器的個人地址清單（「其他伺服器」模式）。<br /> </td> 
  </tr> 
 </tbody> 
</table>
