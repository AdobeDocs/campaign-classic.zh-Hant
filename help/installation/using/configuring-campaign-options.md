---
product: campaign
title: 設定Campaign選項
description: 了解如何設定Campaign選項
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '3991'
ht-degree: 0%

---

# Campaign Classic 選項清單{#configuring-campaign-options}

![](../../assets/v7-only.svg)

此 **[!UICONTROL Administration / Platform / Options]** 節點可讓您設定Adobe Campaign選項。 其中有些是內建的Campaign，有些則可視需要手動新增。 可用選項會依執行個體所安裝的套件而有所不同。


>[!CAUTION]
>
>* 本頁面中未列出的選項僅為內部，且 **不得修改**.
>
>* 修改或更新Adobe Campaign選項只能由專家使用者執行。


## 傳遞 {#delivery}

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
   <td> 從傳遞能力實例檢索的上次broadLogMsg的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> 傳送至傳遞性例項的最後broadLogMsg日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 傳送報表識別碼。 請連絡支援人員以取得您的識別碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 要將測試地址用於收件箱呈現的結構清單。 （元素名稱以逗號分隔）例如：custom_nms_recipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> Enhanced MTA將傳送已傳送電子郵件原始副本的密件副本電子郵件地址。 <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 如果指定特定運算子或運算子群組，以在傳送的屬性中開始傳送，則可讓您允許負責傳送的運算子確認傳送。</p><p> 若要這麼做，請輸入"1"作為值，以啟動選項。 要停用此選項，請輸入"0"。</p><p> 接著，傳送確認程式將依預設運作：在傳送屬性（或管理員）中，只有為傳送指定的運算子或運算子群組才能確認和執行傳送。 請參閱<a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">本節</a>。</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign使用「Nms_DefaultRcpSchema」全域變數來與預設收件者資料庫(nms:recipient)對話。<br /> 選項值必須與與外部收件人表匹配的架構的名稱相對應。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 最低收件者人數，以便將傳送視為計費報表中的主要傳送。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 新模板的預設路由服務提供程式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 一次為傳送建立的廣泛記錄數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> 為每個交易插入（表格中）日誌(broadLogs):每批處理的行數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 分析中間來源交貨時對交貨部件的分組大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 傳送的預設傳送期間（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 標準化傳送訊息的規則運算式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 輸入"1"作為值，即可排除不想再聯絡的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> 輸入"1"作為值，可讓您自動忽略雙倍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 可讓您定義回覆訊息時使用的錯誤位址語法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 可讓您定義傳送訊息時使用之寄件者位址的語法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 可讓您定義逾時限制（以秒為單位），以在擷取從個人化URL下載並附加至電子郵件的影像時，從伺服器取得回應。 如果超過此值，則無法傳送訊息。 預設值為60秒。<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 可讓您定義從個人化URL下載並附加至電子郵件之影像的允許大小上限（以位元組為單位）。 預設值為100,000位元組。 傳送校樣並下載影像以處理電子郵件時，如果影像大小超過此值，或如果發生下載問題，傳送記錄檔中會顯示錯誤，校樣傳送將會失敗。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 可讓您在電子郵件或交易式電子郵件範本中設定最大數量的附件。 如果超過此值，則傳送分析記錄或發佈交易式電子郵件範本時，將會顯示警告。 預設值為1個附件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> 分析期間的最大重試次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> 發佈指令碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> 停用推送訊息的broadLogMsg計數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> 在傳遞精靈中顯示訊息權重。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> 如果使用者保留為空白，則在執行個體層級用於電子郵件傳送的預設「錯誤」電子郵件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 如果使用者保留為空白，則在用於電子郵件傳送的例項層級的預設「寄件者」電子郵件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 如果使用者保留為空白，則在執行個體層級的預設「回覆」電子郵件地址用於電子郵件傳送。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 客戶的常見名稱。 用於向收件者顯示的某些警告訊息。<br /> 「你收到這條資訊是因為你與*****或一家關聯公司有聯繫。 不再從*****」接收消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 如果使用者保留為空白，則在用於電子郵件傳送的例項層級預設的「寄件者」電子郵件標籤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 如果使用者保留為空白，則在用於電子郵件傳送的例項層級預設的「回覆」電子郵件標籤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 電子郵件訊息兩次重試之間的時段（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 電子郵件訊息的重試期間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeight公式</span> <br /> </td> 
   <td> 用於計算臨時傳送之訊息的加權的公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 已授權轉送電子郵件地址的清單（來自入站郵件處理模組）。 地址必須用逗號分隔（或*以允許全部）。 例如xyz@abc.com、pqr@abc.com。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> 「lineImage」servlet中使用的AES索引鍵來編碼URL（LINE通道）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> 在通道「電子郵件」上（預設使用）:接收者進入隔離之前，在發送期間發生SOFT錯誤時，接受的最大錯誤數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailApprientErrorDelay</span> <br /> </td> 
   <td> 在通道「電子郵件」上（預設使用）:自上次引用SOFT錯誤後所花費的最短時間，再考慮新的SOFT錯誤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> 在頻道「行動」上：接收者進入隔離之前，在發送期間發生SOFT錯誤時，接受的最大錯誤數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileApprientErrorDelay</span> <br /> </td> 
   <td> 在頻道「行動」上：自上次引用SOFT錯誤後所花費的最短時間，再考慮新的SOFT錯誤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 允許將最大期間（以小時表示）指定為，以限制每次執行同步工作流時恢復的廣播數量。</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> MidSourcing工作階段中可同時執行的呼叫數上限（預設為3）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 自訂延遲（以分鐘為單位），之後傳送會視為「延遲」，預設為30分鐘。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>此選項由 <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> 計算執行中的傳送數量時的技術工作流程。</p>它可讓您定義狀態不一致的傳送在多少天內，才會從執行中的傳送計數中排除。</p><p>根據預設，值會設為「7」，這表示會排除7天以前的不一致傳送。</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> 發件人地址的第1行。<br /> </td> 
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
   <td> 發件人地址的第6行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> 發件人地址的第7行。<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> 鏡像頁面伺服器的URL（預設情況下，應與NmsTracking_ServerUrl相同）。<br /> 若未在路由定義中指定URL，則此為電子郵件傳送的預設值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> 已傳送SMS訊息的參數：發送到SMS網關以指示消息優先順序的資訊。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> 傳送SMS訊息時的重試次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> 將執行SMS訊息重試的期間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> 上次合併日期 <span class="uicontrol">NmsUserAgent</span> 統計資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> 包含Web區段及其狀態之選項的名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> 啟用/停用對Code128特殊字元的支援。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 電子郵件地址的有效字元。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 將此選項與「0」值一起新增，以停用傳送的XML程式碼版本(按一下滑鼠右鍵/ <span class="uicontrol">編輯XML源</span> 或 <span class="uicontrol">CTRL + F4</span> 快速鍵)。<br /> </td> 
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
   <td> 在Adobe Campaign用戶端主控台中發佈的資源位置。 請參閱<a href="../../delivery/using/formatting.md#image-referencing">本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> 在Adobe Campaign用戶端主控台中預覽的資源位置。 請參閱<a href="../../delivery/using/formatting.md#image-referencing">本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 上傳期間略過之影像的URL遮罩清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 影像上傳的設定。 值可以是「無」/「追蹤」/「指令碼」/清單（可由運算子的選用設定覆寫）。 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 儲存伺服器上映像的資料夾。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 顯示徽標的空間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 發佈的根資料夾。<br /> 有關HTML和文本內容生成的詳細資訊，請參閱 <a href="../../delivery/using/using-a-content-template.md">本節</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 可讓您定義傳送中使用之影像儲存所在的伺服器，以便瀏覽器取得影像。<br /> 對於版本&lt;= 5098，我們使用上傳至執行個體之影像的URL。<br /> 若為組建版本&gt; 5098，我們會改用傳送的公用URL或 <span class="uicontrol">XtkFileRes_Public_URL</span> 選項的URL。<br /> </td> 
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
   <td> 公用資源檔案的新URL。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 行銷活動與工作流程管理 {#campaign-e-workflow-management}

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
   <td> 針對此月數顯示的行銷記錄。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> 促銷活動的預設有效期（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> 可由operationMgt工作流程啟動的一次處理的傳送/工作流程/假設/模擬作業的最大數量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> 可讓您監視 <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a> 技術工作流程執行。 啟動後（值「1」），執行資訊會記錄在工作流程稽核記錄中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 以排程模式鎖定目標和擷取條件的時段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 自動重新計算表統計資訊的受影響記錄數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 要在匯出報表的右上角顯示的標誌。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 檢查已暫停的工作流程之間等待的天數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 輸入"1"作為值，由操作所有者激活傳送驗證。 要停用此選項，請輸入"0"。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> 要在工作流程活動「行銷資源通知」中載入的其他JS程式庫。<br /> </td> 
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
   <td> <span class="uicontrol">RestrictEditingOOTBSchema</span> <br /> </td> 
   <td> （從21.1.3版開始）如果選取1（預設值），此選項會停用內建結構的版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> （從21.1.3版開始）如果選取1（預設值），此選項會停用內建JavaScript程式碼的版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (安裝相容性模式：build&gt;6000)激活時（值「1」），此選項允許使用資料庫中儲存的舊密碼來連接到外部帳戶或實例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 此密鑰用於加密資料庫中的大多數密碼。 （外部帳戶、LDAP密碼……）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 如果選取1，則此選項可允許JavaScript中的privilegeEscalation。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 如果選中1，則此選項在檔案下載期間（通過fileDownload.jsp）禁用ACL控制。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 如果選取1，此選項會停用Javascript中的檔案沙箱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> 如果設為「true」，則授權非管理員運算子透過部署精靈更新xtkOption值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> 如果選中1，則此選項允許使用decryptString解密某些密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> 輸入"1"值，在刪除記錄之前，通過修改其"modified by"欄位，跟蹤刪除mData中具有審計跟蹤資訊的元素。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 訊息中心 {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_ExcrentCustomJs</span> <br /> </td> 
   <td> 個人化以豐富事件的JavaScript程式庫。 必須包含這兩個函式的實作：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enchresingRtEvents(aiEventId);</span> :豐富和保存資料庫中的事件(其中 <span class="uicontrol">aiEventId</span> 與已處理的即時事件表格相對應)。</p> </li> 
     <li> <p> <span class="uicontrol">enchresingBatchEvents(aiEventId);</span> :豐富和保存資料庫中的事件(其中 <span class="uicontrol">aiEventId</span> 與已處理批次事件的ID表格相對應)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 透過傳送記錄檔更新上次事件狀態的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> 要針對路由事件個人化的JavaScript程式庫。 必須包含這兩個函式的實作：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> :傳回選取要處理即時事件的交易式訊息的內部名稱(其中 <span class="uicontrol">iEventId</span> 與所處理即時事件的ID相對應)。</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> :傳回所選處理批事件的交易式訊息的內部名稱(其中 <span class="uicontrol">iEventId</span> 與已處理批次事件的ID相對應)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> 即時事件平均傳送時間的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> 即時事件平均傳送時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> 即時事件平均處理時間的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> 即時事件平均處理時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> 排隊即時事件平均數的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 即時事件平均排隊時間的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 即時事件平均排隊時間的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 排隊即時事件平均數的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> 處理即時事件錯誤的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> 處理即時事件錯誤的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> 排隊即時事件數上限的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 排隊即時事件數上限的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 排隊即時事件最小數的警報閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 排隊即時事件最少數的警告閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 掛起即時事件隊列的臨界條件之前的閾值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 掛起即時事件佇列的警告前臨界值。<br /> </td> 
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
   <td> 事件路由的重新分組大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> 更新RtEvent狀態的指標（擷取資料之前的最後日期）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> 用於發送歡迎郵件的郵件中心伺服器URL（LINE通道）。<br /> </td> 
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
   <td> 定義上次執行清除程式的時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除廣播的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除事件歷史記錄的延遲。</p><p>
   在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除事件後的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除事件統計資料的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PostitionPurgeDelay</span> <br /> </td> 
   <td><p> 允許您定義從資料庫中清除命題的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除隔離的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Lets you define the delay after which recycled deliveries are erased from the database.</p><p> 在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除拒絕的延遲。</p><p>This option is automatically created once the delay is modified within the interface. 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除追蹤記錄的延遲。</p><p>在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義從資料庫中清除追蹤統計資料的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除訪客的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫中清除工作流結果的延遲。</p><p> 在介面中修改延遲後，會自動建立此選項。 如果從選項清單修改值，應以秒錶示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse連接器選項。<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>允許您根據以下潛在值影響所有工作流和PostgreSQL資料庫查詢上的無條件停止行為：<ul>
    <li><p>0 — 預設值：停止工作流進程，不影響資料庫<p></li>
    <li><p>1 - pg_cancel_backend:停止工作流進程並取消資料庫中的查詢<p></li>
    <li><p>2 - pg_terminate_backend:停止工作流進程並終止資料庫中的查詢<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> 用於包含Adobe Campaignootb表資料的表空間的名稱。<br />請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和配置資料庫</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> 用於包含Adobe Campaignootb表索引的表空間的名稱。<br />請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和配置資料庫</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> 用於包含Adobe Campaign工作表資料的表空間的名稱。<br />請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和配置資料庫</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> 用於包含Adobe Campaign工作表索引的表空間的名稱。<br />請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和配置資料庫</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> 允許您為Microsoft SQL Server上的工作表配置單獨的資料庫，以優化備份和複製。 該選項與臨時資料庫的名稱相對應：如果指定，則將在此資料庫中寫入工作表。 範例：'tempdb.dbo' （請注意，名稱必須以點結尾）。 <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">閱讀全文</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Adobe Campaign執行個體的時區。 請參閱 <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">設定</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> 資料庫的字串欄位是否使用NChar定義？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> 資料庫的「datetime」欄位是否儲存時區資訊？<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> 資料庫的ID。 以'u'開頭，用於Unicode DataBase。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 自動為內部名稱添加前置詞。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> 查詢在xtk:schema和xtk:srcSchema上傳回的結果數上限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 在此之後建立的所有自訂結構（使用autopk="true"且不使用屬性"pkSequence"）將獲得自動生成的序列"auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq。 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 在移轉期間，樹狀結構會根據新版本標準自動重新組織。<br /> 此選項可讓您停用導覽樹的自動移轉。 如果您使用它，則在遷移後，您必須刪除過時的資料夾、添加新資料夾並運行所有必要的檢查。<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Data type:</span> Integer</p> </li> 
     <li> <p> <span class="uicontrol">值（文字）</span> :1 </p> </li> 
    </ul> 只有在現成可用的導覽樹已進行太多變更時，才應使用此選項。<br /> For more on this, refer to <a href="../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> 上次處理日期： <span class="uicontrol">NmsEmailErrorStat</span> 表格清理。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> 遵循下列語法，提供Postupgrade中發生錯誤的相關資訊：<br /> <strong>{Build number}:{mode:pre/post/...}:{發生錯誤的'lessThan'/'greaterOrEquelThan' +子步驟}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> 輸入"1"值，以便不會通過清理工作流執行統計資訊的更新。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 整合 {#integration}

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
   <td> 可在Adobe Campaign中使用的AEM資源類型。 值必須以逗號分隔。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> 可讓您設定Experience Cloud觸發器。 資料類型為「長文字」，且必須為JSON格式。 請參閱 <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">如何搭配Adobe Campaign Classic使用Experience Cloud觸發程式</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> 透過CRM連接器從協力廠商系統匯入資料時，會使用此選項。 啟用選項可讓您僅收集自上次匯入後修改的物件。 此選項必須手動建立並填入，如下所示： 
    <ul> 
     <li> <p> <span class="uicontrol">內部名稱</span> :LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">值（欄位）</span> :上次匯入的日期，為yyyy/MM/dd hh:mm:ss格式。 </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> 用於整合的Adobe Target伺服器。 預設已選取此選項。 此值與Adobe Target域伺服器相對應，後跟/m2值。 例如：tt.omtrdc.net/m2。<br /> 請參閱 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">本節</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target組織名稱。 此值對應至Adobe Target用戶端的名稱。<br /> 請參閱 <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">本節</a>.<br /> </td> 
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
   <td> 配置單元連接器選項。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 選件 {#offers}

<table> 
 <thead> 
  <tr> 
   <th> 選項名稱 </th> 
   <th> 說明 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCouns_MaxPerTransac</span> <br /> </td> 
   <td> 每個SQL交易更新的抵用券數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompositionSynchControl_</span> <br /> </td> 
   <td> 「+ [主張的架構] + "_" + extAccountSource。@executionInstanceId + [主張的架構] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastCompationSynchExec_</span> <br /> </td> 
   <td> 「+ [命題的架構] + "_" + extAccountSource。@executionInstanceId + "_" + extAccountTarget。@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 同步工作流程追蹤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 啟用/停用非同步命題寫入（「0」禁用，「1」啟用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CounsEnabled</span> <br /> </td> 
   <td> 可讓您啟用抵用券。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 伺服器 {#server}

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
   <td> Internal base URL to access the application server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> 上次升級前的AC實例的生成號。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> Base URL of the public web application server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> 可讓您在移轉後繼續使用未宣告的舊SQL函式。 由於此選項會帶來安全風險，我們強烈建議不要使用此選項。<br /> </td> 
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
   <td> 追蹤的URL計算指令碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> 可讓您定義追蹤伺服器的外部帳戶。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> 可讓您定義追蹤伺服器上的執行個體名稱。<br /> </td> 
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
   <td> 如果選取選項1，您必須在第二個步驟中，手動確認介面中的刪除。 否則，資料將刪除而不進行確認。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 請求之間的延遲等待刪除確認，請求被取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> 處理/刪除隱私權請求時允許的錯誤數上限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> 請求之間的延遲會在佇列上建立，並刪除請求資料。<br /> </td> 
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
   <td> Enable LDAP server to be used to authenticate users and provide authorizations to users.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Application login to contact the server for various searches.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Encrypted password for the application login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> 在Adobe Campaign中啟用自動建立運算子和權限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> 基於登錄的LDAP DN計算公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> 啟用目錄中的DN搜索。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> 搜索庫。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN search filter.<br /> </td> 
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
   <td> 啟用從LDAP目錄到Adobe Campaign中已命名權限的授權和組同步。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 包含授權名稱的LDAP屬性。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 搜索庫。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 搜索用戶授權篩選器。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> 從LDAP授權擷取Adobe Campaign權限名稱的運算式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> 搜索範圍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP伺服器地址（可以通過指定「：」作為分隔符來指定埠）。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 網路表單 {#web-forms}

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
   <td> 值設為1可讓捲軸新增至詳細表單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> 在「其他伺服器」模式中用於Web表單失效的實例。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> 要在「其他伺服器」模式下用於Web表單無效的實例的密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 可讓您指定網路表單的無效模式的選項：依預設，如果選項為「tracking」，則使用追蹤伺服器，並搭配「其他伺服器」選項使用個人化清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span> <br /> </td> 
   <td> 要因Web表單失效而聯繫的伺服器的個性化地址清單（「其他伺服器」模式）。<br /> </td> 
  </tr> 
 </tbody> 
</table>
