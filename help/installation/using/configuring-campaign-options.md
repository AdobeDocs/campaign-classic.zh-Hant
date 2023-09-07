---
product: campaign
title: 設定Campaign選項
description: 瞭解如何設定Campaign選項
feature: Installation, Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '4004'
ht-degree: 6%

---

# Campaign Classic 選項清單{#configuring-campaign-options}

此 **[!UICONTROL Administration / Platform / Options]** 節點可讓您設定Adobe Campaign選項。 其中有些是內建在安裝Campaign時，有些則可視需要手動新增。 可用選項會因您執行個體所安裝的套件而異。


>[!CAUTION]
>
>* 此頁面中未列出的選項僅供內部使用，而且 **不得修改**.
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
   <td> 上次從傳遞能力執行個體擷取的broadLogMsg日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> 最後傳送至傳遞能力執行個體的broadLogMsg日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> 傳遞報告識別碼。 請聯絡支援以取得您的識別碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> 您要使用測試位址進行收件匣轉譯的結構描述清單。 （元素名稱以逗號分隔），例如： custom_nms_recipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> Enhanced MTA會傳送已傳送電子郵件原始副本的密件副本電子郵件地址。 <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> 可讓您允許負責傳遞的運運算元確認傳送（若指定的特定運運算元或運運算元群組用於傳遞的屬性中開始傳遞）。</p><p> 若要這麼做，請輸入"1"作為值來啟動選項。 若要停用此選項，請輸入「0」。</p><p> 然後，傳送確認程式將依預設運作：只有傳送屬性中針對傳送指定的操作員或操作員群組（或管理員）才能確認並執行傳送。 請參閱<a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">本節</a>。</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign使用「Nms_DefaultRcpSchema」全域變數與預設收件者資料庫(nms：recipient)對話。<br /> 選項值必須對應至符合外部收件者表格的結構描述名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> 為了將傳遞視為計費報告中的主要傳遞而允許的最小收件者人數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> 新範本的預設路由服務提供者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> 在傳送準備期間插入broadLog的最小批次大小（列數）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> 批次持續時間臨界值（毫秒數），在準備傳送期間，插入broadLogs的批次大小會加倍。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> 分析中間來源傳遞時傳遞部分的群組大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> 傳送的預設傳送期間（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> 標準化傳遞訊息的規則運算式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> 輸入"1"作為值可讓您排除不想再被聯絡的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> 輸入「1」作為值可讓您自動忽略雙面。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> 可讓您定義回複訊息時使用的錯誤位址語法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> 可讓您定義傳送訊息時所用寄件者地址的語法。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> 可讓您定義逾時限制（以秒為單位），以便在擷取從個人化URL下載並附加至電子郵件的影像時，從伺服器取得回應。 如果超過此值，則無法傳送訊息。 預設值為60秒。<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> 可讓您定義從個人化URL下載並附加至電子郵件的影像允許的大小上限（以位元組為單位）。 預設值為100,000位元組(100 KB)。 傳送校樣並下載影像以處理電子郵件時，如果影像大小超過此值或發生下載問題，傳送記錄中會顯示錯誤，且校樣傳送將失敗。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> 可讓您設定電子郵件或交易式電子郵件範本中的最大附件數量。 如果超過此值，則傳送分析記錄檔或發佈交易式電子郵件範本時，會顯示警告。 預設值為1個附件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> 分析期間的最大重試次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> 發佈指令碼.<br /> </td> 
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
   <td> 使用者留空時，執行個體用於電子郵件傳遞層級的預設「錯誤」電子郵件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> 使用者留空時，執行個體用於電子郵件傳遞層級的預設「寄件者」電子郵件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> 使用者留空時，執行個體用於電子郵件傳遞層級的預設「回覆」電子郵件地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> 客戶的一般名稱. 用於顯示給收件者的部分警告訊息。<br /> 「您收到此訊息是因為您曾與'Organization'或附屬公司聯絡。 不再接收來自「組織」的訊息<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> 使用者留空時，在用於電子郵件傳遞的執行個體層級預設「寄件者」電子郵件標籤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> 使用者留空時，在用於電子郵件傳遞的執行個體層級預設「回覆」電子郵件標籤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> 電子郵件訊息兩次重試之間的期間（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> 電子郵件訊息的重試期間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> 用於計算臨時傳遞之訊息重量的公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> 授權轉寄電子郵件地址的清單（來自傳入郵件處理模組）。 位址必須以逗號分隔（或*以允許全部）。 例如xyz@abc.com、pqr@abc.com。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> 「lineImage」servlet中用於編碼URL （LINE頻道）的AES金鑰。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> 頻道「電子郵件」（使用作為預設值） ：在傳送期間發生SOFT錯誤，將收件者置於隔離之前接受的最大錯誤數量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignalErrorDelay</span> <br /> </td> 
   <td> 頻道「電子郵件」（使用作為預設值） ：計及新的SOFT錯誤之前，自上次參考的SOFT錯誤以來的最短逗留時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> 在頻道「行動」 ：對於在傳送期間將收件者放入隔離區之前的SOFT錯誤，可接受的最大錯誤數量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignalErrorDelay</span> <br /> </td> 
   <td> 頻道「行動」 ：計及新的SOFT錯誤之前，自上次參考的SOFT錯誤以來的最短逗留時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> 允許指定最大時段（以小時表示）以限制每次執行同步工作流程時復原的broadlog數目。</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> MidSourcing工作階段中可同時執行的最大呼叫數（預設為3）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> 自訂延遲（以分鐘為單位），過了這段時間，傳送會視為「延遲」，預設為30分鐘。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>此選項由 <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> 計算執行中傳送數量時的技術工作流程。</p>它可讓您定義天數，超過該天后，狀態不一致的傳送會從執行中的傳送計數中排除。</p><p>預設情況下，此值會設為「7」，這表示將排除超過7天的不一致傳送。</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> 寄件者地址的第1行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> 寄件者地址的第3行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> 寄件者地址的第4行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> 寄件者地址的第6行。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> 寄件者地址的第7行。<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> 映象頁面伺服器的URL （預設應與NmsTracking_ServerUrl相同）。<br /> 若未在路由定義中指定URL，此為電子郵件傳送的預設值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS優先順序</span> <br /> </td> 
   <td> 已傳送SMS訊息的引數：傳送至SMS閘道的資訊，用以指出訊息優先順序。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> 傳送SMS訊息時的重試次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> 將執行SMS訊息重試的時段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> 上次合併日期 <span class="uicontrol">NmsUserAgent</span> 統計資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> 包含網頁區段及其狀態的選項名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> 啟用/停用Code128的特殊字元支援。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> 電子郵件地址的有效字元。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> 使用「0」值新增此選項，以停用傳遞的XML程式碼版本(按一下右鍵/ <span class="uicontrol">編輯XML來源</span> 或 <span class="uicontrol">CTRL + F4</span> 捷徑)。<br /> </td> 
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
   <td> <span class="uicontrol">NcmResourcesDir</span> <br /> </td> 
   <td> 在Adobe Campaign使用者端主控台中發佈的資源位置。 請參閱<a href="../../delivery/using/formatting.md#image-referencing">本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmResourcesDirPreview</span> <br /> </td> 
   <td> 在Adobe Campaign使用者端主控台中預覽的資源位置。 請參閱<a href="../../delivery/using/formatting.md#image-referencing">本節</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> 上傳期間略過的影像的 URL 遮罩清單.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> 影像上傳的設定. 值可為無/追蹤/指令碼/清單（可由運運算元的選用設定覆寫）。 </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> 伺服器上的影像將要儲存到的資料夾.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> 顯示圖志的空間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> 出版物的根資料夾。<br /> 有關HTML和文字內容產生的詳細資訊，請參閱 <a href="../../delivery/using/using-a-content-template.md">本節</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> 可讓您定義儲存傳送中所用影像的伺服器，讓瀏覽器能夠取得。<br /> 若為組建版本&lt;= 5098，我們會使用已上傳至執行個體的影像URL。<br /> 若為組建版本&gt; 5098，我們改為使用傳送的公用URL或 <span class="uicontrol">XtkFileRes_Public_URL</span> 選項的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> 可讓您設定影像上傳的執行個體名稱。<br /> </td> 
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
   <td> 傳遞的線上資源的預設有效期間（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> 公用資源檔案的新 URL.<br /> </td> 
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
   <td> 顯示這個月份的行銷記錄。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> 行銷活動的預設有效期（以秒為單位）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> 由operationMgt工作流程啟動的一次可處理的最大傳遞/工作流程/假設/模擬工作數量。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> 可讓您監視 <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a> 技術工作流程執行。 啟動時（值為「1」），執行資訊會記錄在工作流程稽核記錄中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> 在排程模式中鎖定和擷取條件的時段。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> 受影響的記錄數目，之後會自動重新計算表格統計資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> 將在匯出報表的右上角顯示的標誌。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> 檢查暫停的工作流程之間要等候的天數。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> 輸入「1」作為值，由作業的擁有者啟動傳遞驗證。 若要停用此選項，請輸入「0」。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> 要載入工作流程活動「行銷資源通知」的其他JS程式庫。<br /> </td> 
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
   <td> （自21.1.3發行版本開始）如果選取1 （預設值），此選項會停用內建結構的版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> （自21.1.3發行版本開始）如果選取1 （預設值），此選項會停用內建JavaScript程式碼的版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> （安裝相容性模式： build&gt;6000）啟動時（值「1」），此選項允許使用儲存在資料庫中的舊密碼，以連線至外部帳戶或執行個體。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> 此金鑰用來加密資料庫中大部分的密碼。 （外部帳戶，LDAP密碼……）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> 如果選取1，此選項會允許JavaScript中的privilegeEscalation。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> 如果選取1，此選項會在檔案下載期間（透過fileDownload.jsp）停用ACL控制項。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> 如果選取1，此選項會停用Javascript中的檔案沙箱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> 若設為「true」，則授權的非管理員運運算元可透過部署精靈更新xtkOption值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> 如果選取1，此選項允許使用decryptString來解密某些密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> 輸入「1」值，在刪除記錄之前，透過修改其「修改者」欄位，追蹤mData中具有「稽核軌跡」資訊之元素的刪除作業。<br /> </td> 
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
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> 要個人化的JavaScript程式庫，以豐富事件。 必須包含這兩個函式的實作：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">extendedRtEvents(aiEventId)；</span> ：豐富並儲存資料庫中的事件(其中 <span class="uicontrol">aiEventId</span> 對應於已處理的即時事件表格)。</p> </li> 
     <li> <p> <span class="uicontrol">extendedBatchEvents(aiEventId)；</span> ：豐富並儲存資料庫中的事件(其中 <span class="uicontrol">aiEventId</span> 對應於已處理批次事件的ID表格)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> 透過傳遞記錄檔進行上次事件狀態更新的日期。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> 將個人化路由事件的JavaScript資料庫。 必須包含這兩個函式的實作：<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId)；</span> ：傳回選取用來處理即時事件的交易式訊息的內部名稱(其中 <span class="uicontrol">iEventId</span> 與處理的即時事件ID相對應)。</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId)；</span> ：傳回所選用來處理批次事件的交易式訊息的內部名稱(其中 <span class="uicontrol">iEventId</span> 對應於已處理批次事件的ID)。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> 即時事件的平均傳送時間的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> 即時事件的平均傳送時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> 即時事件的平均處理時間的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> 即時事件的平均處理時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> 已排入佇列的即時事件之平均數量的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> 即時事件的平均佇列時間的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> 即時事件的平均佇列時間的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> 已排入佇列的即時事件之平均數量的警告臨界值。<br /> </td> 
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
   <td> 已排入佇列的即時事件之最大數量的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> 已排入佇列的即時事件之最大數量的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> 已排入佇列的即時事件之最小數量的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> 已排入佇列的即時事件之最小數量的警告臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> 待處理即時事件佇列的危急情況之前的臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> 針對待處理即時事件佇列發出警告之前的臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> 即時事件輸送量的警報臨界值。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> 即時事件輸送量的警告臨界值。<br /> </td> 
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
   <td> 用於傳送歡迎訊息的Message Center伺服器URL （LINE通道）。<br /> </td> 
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
   <td> 定義上次執行清理程式的時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義延遲，過了此延遲後broadlog就會從資料庫中清除。</p><p>在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義延遲，之後事件歷史記錄會從資料庫中清除。</p><p>
   在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義延遲時間，之後事件會從資料庫中清除。</p><p>在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義延遲，之後事件統計資料會從資料庫中清除。</p><p>在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義延遲，之後會從資料庫中清除主張。</p><p> 在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫清除隔離的延遲。</p><p> 在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義延遲，之後會從資料庫中清除循環傳送。</p><p> 在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義延遲，之後會從資料庫中清除拒絕專案。</p><p>在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義延遲，過了此延遲後，追蹤記錄就會從資料庫中清除。</p><p>在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> 可讓您定義延遲，過了此延遲後，追蹤統計資料就會從資料庫中清除。</p><p> 在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義從資料庫清除訪客之後的延遲。</p><p> 在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>可讓您定義延遲時間，過了這段時間，工作流程結果就會從資料庫中清除。</p><p> 在介面中修改延遲後，就會自動建立此選項。 如果您修改選項清單中的值，該值應以秒為單位表示。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse聯結器選項。<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>可讓您根據下列潛在值，影響所有工作流程和PostgreSQL資料庫查詢的無條件停止行為：<ul>
    <li><p>0 — 預設：停止工作流程處理，對資料庫沒有影響<p></li>
    <li><p>1 - pg_cancel_backend：停止工作流程處理並取消資料庫中的查詢<p></li>
    <li><p>2 - pg_terminate_backend：停止工作流程處理並終止資料庫中的查詢<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> 用來包含Adobe Campaign ootb表格資料的表格空間名稱。<br />另請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和設定資料庫</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> 用來包含Adobe Campaign ootb表格索引的表格空間名稱。<br />另請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和設定資料庫</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> 用來包含Adobe Campaign工作表資料的表格空間名稱。<br />另請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和設定資料庫</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> 用來包含Adobe Campaign工作表索引的表格空間名稱。<br />另請參閱 <a href="../../installation/using/creating-and-configuring-the-database.md">建立和設定資料庫</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> 可讓您為Microsoft SQL Server上的工作表格設定個別的資料庫，以最佳化備份與復寫。 選項與暫存資料庫的名稱相對應：如果指定，會將工作表寫入此資料庫。 範例： 'tempdb.dbo.' （請注意，名稱必須以點結尾）。 <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">深入了解</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Adobe Campaign例項的時區。 另請參閱 <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">設定</a>.<br /> </td> 
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
   <td> 資料庫的ID。 Unicode資料庫的開頭是'u'。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> 新增到自動產生的內部名稱的前置詞.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> 查詢在xtk：schema和xtk：srcSchema上傳回的結果數上限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> 在此時間之後建立的所有自訂結構描述，若具有autopk="true"且沒有屬性"pkSequence"，將會取得自動產生的序列"auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       序列(_S) 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> 在移轉期間，樹狀結構會根據新版本標準自動重新組織。<br /> 此選項可讓您停用導覽樹狀結構的自動移轉。 如果您使用它，移轉後您必須刪除過時的資料夾、新增資料夾並執行所有必要的檢查。<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">資料型別：</span> 整數</p> </li> 
     <li> <p> <span class="uicontrol">值（文字）</span> ：1 </p> </li> 
    </ul> 只有在現成可用的導覽樹狀結構已發生太多變更時，才應使用此選項。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> 的上次處理日期 <span class="uicontrol">NmsEmailErrorStat</span> 表格清理。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> 依照下列語法，取得有關升級後所發生錯誤的資訊：<br /> <strong>{組建編號}：{mode： pre/post/...}：{發生錯誤的'lessThan'/'greaterOrEquelThan' +子步驟}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> 輸入「1」值，使統計資料的更新不透過清除工作流程執行。<br /> </td> 
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
   <td> 可在Adobe Campaign中使用的AEM資源型別。 值必須以逗號分隔。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> 可讓您設定Experience Cloud觸發器。 資料型別為「長文字」，且必須採用JSON格式。 另請參閱 <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">如何搭配Adobe Campaign Classic使用Experience Cloud觸發程式</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> 透過CRM聯結器從協力廠商系統匯入資料時，會使用此選項。 啟用選項可讓您僅收集自上次匯入後修改的物件。 此選項必須手動建立並填入，如下所示： 
    <ul> 
     <li> <p> <span class="uicontrol">內部名稱</span> ： LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">值（欄位）</span> ：上次匯入的日期，格式為yyyy/MM/dd hh:mm:ss格式。 </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> 用於整合的Adobe Target伺服器。 依預設，已選取此選項。 此值對應至Adobe Target網域伺服器，然後是值/m2。 例如： tt.omtrdc.net/m2。<br /><a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> 請參閱本章節</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target組織名稱。 此值對應至Adobe Target使用者端的名稱。<br /><a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> 請參閱本章節</a>.<br /> </td> 
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
   <td> teradata聯結器選項。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Hive聯結器選項。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 優惠 {#offers}

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
   <td> 每個SQL交易更新的優惠券數目。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [主張的結構描述] + "_" + extAccountSource。@executionInstanceId + [主張的結構描述] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [主張的結構描述] + "_" + extAccountSource。@executionInstanceId + "_" + extAccountTarget。@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> 同步工作流程追蹤。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> 啟用/停用非同步主張寫入（"0"為停用，"1"為啟用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> 可讓您啟用優惠券。<br /> </td> 
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
   <td> 執行實例識別碼.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> 傳送計費報告時使用的客戶識別碼.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> 存取應用程式伺服器的內部基底URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> 上次升級前AC執行個體的版本編號。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> 公用Web應用程式伺服器的基底URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkpassunknowledsqlfunctionsToRDBMS</span> <br /> </td> 
   <td> 可讓您在移轉後繼續使用舊的未宣告SQL函式。 由於此選項會帶來安全性風險，因此強烈建議不要使用此選項。<br /> </td> 
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
   <td> 追蹤的 URL 計算指令碼.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> 可讓您定義追蹤伺服器的外部帳戶。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> 可讓您在追蹤伺服器上定義執行個體名稱。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> 上次已使用新資料合併追蹤資訊的時間。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> 開啟 URL 計算指令碼.<br /> </td> 
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
   <td> 前端追蹤伺服器的安全URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> 前端追蹤伺服器的URL。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> 用於聯絡追蹤伺服器的URL清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> 瀏覽器識別規則集。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> 用來計算網頁追蹤標籤的指令碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> 為網站追蹤管理所設計的虛擬傳遞名稱。<br /> </td> 
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
   <td> 如果選取選項1，則必須在第二個步驟中在介面中手動確認刪除。 否則，將會刪除資料而不進行確認。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> 請求等待刪除確認與請求被取消之間的延遲。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> 處理/刪除隱私權請求時允許的錯誤數上限。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> 在佇列上建立請求之間的延遲會刪除請求資料。<br /> </td> 
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
   <td> 啟用LDAP伺服器，以用來驗證使用者並向使用者提供授權。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> 應用程式登入以連絡伺服器以進行各種搜尋。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> 應用程式登入的加密密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> 在Adobe Campaign中啟用自動建立操作者和許可權。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> 根據登入的LDAP DN計算公式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> 啟用目錄中的DN搜尋。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> 搜尋基礎。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN搜尋篩選器。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> 搜尋範圍.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> 用於聯絡LDAP伺服器的驗證型別(plain、md5、lds、ntlm、dpa)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> 啟用授權和群組從LDAP目錄到Adobe Campaign中已命名許可權的同步。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> 包含授權名稱的LDAP屬性。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> 搜尋基礎。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> 搜尋篩選器以取得使用者授權。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> 從LDAP授權中擷取Adobe Campaign許可權名稱的運算式。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> 搜尋範圍.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP伺服器位址（可以透過指定'：'作為分隔符號來指定連線埠）。<br /> </td> 
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
   <td> 值設為1可讓詳細資料表單新增卷軸。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> 在「其他伺服器」模式下用於綢頁表單失效的執行個體。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> 在「其他伺服器」模式下用於綢頁表單失效的執行個體密碼。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> 可讓您指定網路表單失效模式的選項：預設情況下為本機，如果選項為「追蹤」，則使用追蹤伺服器，並使用提供其他「伺服器」選項的個人化清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> 為Web表單失效而聯絡的伺服器個人化位址清單（「其他伺服器」模式）。<br /> </td> 
  </tr> 
 </tbody> 
</table>
