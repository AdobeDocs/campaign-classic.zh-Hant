---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 7f24c8be599d6dece41de848d64feb8079b10ff3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 最新版本{#latest-release}

![](../../assets/v7-only.svg)

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## ![](assets/do-not-localize/limited_2.png)版本 7.3.1 - 版本編號 9352 {#release-7-3-1}

_2022年7月1日_

**有哪些新功能？**

<table> 
<thead>
<tr> 
<th> <strong>有時效性的通知</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>在 iOS15 ，Apple 增加了具時效性通知的概念，當通知被視為具時效性，需要即時聯絡使用者時，可以讓應用程式開發人員繞過專注模式。</p>
<p>瞭解如何在 <a href="../../delivery/using/create-notifications-ios.md">詳細文檔</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

**相容性更新**

* Adobe CampaignSDK現在支援Android 12和iOS15的推送通知。
* Adobe Campaign現在與MySQL 8相容。
* Adobe Campaign 現在相容於 Windows 11。 
* Adobe Campaign現在與德比11相容。

請參閱 [Campaign 相容性對照表](../../rn/using/compatibility-matrix.md#OperatingSystems)。

**功能改進**

* 在Internet Explorer 11生命週期結束後，控制台中Adobe Services的HTML呈現引擎現在使用Edge Crr。 此外，任何客戶端控制台安裝(從Campaign Classic7.3生成版本)現在都需要安裝Microsoft邊緣Webview 2運行時。 [閱讀全文](../../installation/using/installing-the-client-console.md)
* 為了優化穩定性，Adobe Campaign的資料庫連接管理得到了改進。
* Microsoft Exchange Online OAuth 2.0 在 Campaign 中支援 POP3 驗證。 [閱讀全文](../../installation/using/external-accounts.md#bounce-mails-external-account)
* 在使用包含外部資料的濃縮工作流活動時，已解決各種問題。 (NEO-38069)
* SAP Hana FDA連接器已更新，以使用最新的SAP Hana資料庫版本(2.x)運行。
* teradataFDA連接器已更新為使用最新的Teradata版本(17)。
* 20.2為新的遞送和遞送模板引入了對iOS遞送的基於令牌的驗證的支援。 在7.2中，向配置程式中添加了一個修補程式，以將基於令牌的身份驗證支援應用於最多10,000個以前建立的交付和交付模板。 在7.3中，已對修補程式進行了改進，並且已刪除了限制。

**修補程式**

* 已修復上一生成中的錯誤，該錯誤阻止用戶調整IMS登錄頁的大小。
* 已修復在現有實例上安裝內容管理器包時出錯。
* 已修復 **市場活動** 菜單，其中持續顯示「操作正在進行」消息。
* 啟用Adobe Analytics後，在發送帶有URL的電子郵件時修復了從URL中刪除BID(Broadlog ID)和CID(Campig ID)而不保存傳遞的問題。
* 在具有消息中心特定配置的實例的「公共資源」資料夾中上載映像時，已修復問題。 將顯示以下錯誤消息：&quot;無法將映像上載到跟蹤伺服器&quot;。
* 修正了在重新產生設定時，如果設定檔案錯誤，會導致系統當機的問題。
* 已修復可能導致交貨指標未正確更新的問題。 (NEO-44827)
* 已修復在使用複雜查詢時可能導致錯誤的問題。 (NEO-43648)
* 已修復可能阻止WebApps預覽工作的問題。 (NEO-43242)
* 修復了在具有資料載入（檔案）活動的工作流中使用外部目標映射檔案時可能導致交付準備失敗的問題。 (NEO-43691)
* 修復了可能導致崩潰並需要完全重新啟動實例的問題。 (NEO-44645)
* 已修復可能阻止工作流熱圖載入任何結果的問題。 (NEO-43360)
* 已修復在使用FDA外部連接器時可能導致連接問題的問題。 (NEO-42722)
* 使用地址替換和控制組排除時，已修復帶有證明的問題。 (NEO-39695)
* 已修復因Snowflake連接器問題而可能導致工作流失敗的問題。 (NEO-46299)
* 已修復由於個性化塊中的無效字元而可能凍結客戶端控制台的問題。 (NEO-45761)
* 已修復在建立外部帳戶作為外部資料庫Snowflake時可能導致連接問題的問題。 (NEO-45744)
* 已修復可能導致顯示受visibleIf屬性保護的表資訊的問題。 (NEO-37865)
* 修復了在傳遞分析階段顯示「$ is not defined」錯誤消息的問題。 (NEO-32940)
* 已修復導致交貨與錯誤的eventType關聯的問題。 (NEO-45743)
* 已修復由於間歇性核心轉儲而導致崩潰的問題(NEO-30549)
* 修復了在傳遞中使用錯誤HTML代碼時可能導致崩潰的問題。 (NEO-40385)
* 修復了可能阻止非管理員用戶訪問 **分析** 頁籤。 (NEO-34025)

## ![](assets/do-not-localize/green_2.png)版本 7.2.2 - 版本編號 9349 {#release-7-2-2}

_2022 年 3 月 1 日_

>[!NOTE]
>
> 此版本相容於 v7.2.1 用戶端主控台。

**修補程式**

* 修正下列問題，在設定&#x200B;**網站分析**&#x200B;外部帳戶時，即使發生錯誤，整合狀態也始終顯示「整合成功」。 (NEO-36672)
* 修復若干有關序列 ID 機制在升級後的錯誤（ID 為負值）。 (NEO-43205、NEO-42846、NEO-42845)
* 修復下列問題，當使用包含重複及連續的傳遞的&#x200B;**網站分析**&#x200B;外部帳戶時，導致遺失部分外部帳戶資料。 (NEO-38548)
* 修復在更新 NmsActiveContact 表格時升級後速度變慢的問題。 (NEO-43206)
* 修復下列升級後的問題，當出廠預裝資料夾從&#x200B;**管理**&#x200B;節點移動到任何其他位置時發生問題。 (NEO-42875)
* 修正下列問題，當使用&#x200B;**更新資料**&#x200B;工作流程活動時，可能會使收件者綱要無法從 Google 雲端外部資料庫更新收件者資料。 (NEO-42343)
* 修復了與 Adobe Analytics 連接器相關的升級後的問題。 (NEO-43318、NEO-38136)
* 修復在升級後期間「VALUE_TO_CHANGE」覆寫 CUID 的問題。 (NEO-43267)
* 修復下列問題，在多個中間設定上同步中間來源和行銷執行個體時導致錯誤。 (NEO-10432)
* 修復下列問題，在同時具有 1000 多個 broadlog 時重新整理傳遞性工作流程導致錯誤。 (NEO-40276)
* 修復下列問題，無法自動更新未結比例及點選比例傳遞指示器。 (NEO-43253)

## ![](assets/do-not-localize/limited_2.png)版本 7.2.1 - 版本編號 9346 {#release-7-2-1}

_2022 年 1 月 10 日_

**安全性增強功能**

已對 FDA 帳戶加強幾項安全性改進：

* 當設定 FDA 外部帳戶時，您現在可以使用金鑰組驗證來登入 Snowflake 帳戶，以增強驗證安全性。 [閱讀全文](../../installation/using/configure-fda-snowflake.md)
* 當設定 FDA 外部帳戶時，您現在可以使用系統指派的受管理身分登入您的 Azure Synapse Analytics 帳戶。 [閱讀全文](../../installation/using/configure-fda-synapse.md#azure-external)
* 已從 Campaign 移除對 log4j 程式庫的所有參考，以確保最佳安全性。

**相容性更新**

Adobe Campaign 現在相容於 Windows Server 2019。 請參閱 [Campaign 相容性對照表](../../rn/using/compatibility-matrix.md#OperatingSystems)。

**功能改進**

* Microsoft Dynamics CRM 365 連接器

   已套用有關 Microsoft Dynamics 連接器網頁 API 的重要修正：

   * 修正在工作流程觸發的匯入期間，字串類型欄位的 Null 值儲存為 Null 而非空白值的問題。
   * 修正使用網頁 API 呼叫匯入或匯出資料時，導致下列錯誤的問題：「無效的 URI：URI 方案太長」。
   * 針對從 Microsoft Dynamics 365 匯入資料時，修正因包含查閱欄位而導致的各種問題。

* Google BigQuery FDA 連結器

   * Google BigQuery FDA 連結器現在可用於托管部署。 [閱讀全文](../../installation/using/configure-fda-google-big-query.md)
   * 新增支援，以便啟用 Google BigQuery FDA 連接器的代理伺服器連線。 可透過外部帳戶設定的「選項」欄位設定所需的代理選項。 [閱讀全文](../../installation/using/configure-fda-google-big-query.md#google-external)

**其他變更**

* 棄用後，Microsoft CRM、Salesforce、Oracle CRM 隨選操作活動已從介面中移除。若要設定 Adobe Campaign 與 CRM 系統之間的資料同步，您可以使用 CRM 連接器活動。[閱讀全文](../../workflow/using/crm-connector.md)
* **[!UICONTROL Encrypted identifier]** 欄位已新增至訪客方案 (nms:visitor)。 此欄位已經過計算，將用於網路應用程式。當在中間來源執行個體上設定 Line 頻道時，即適用。
* CRM 資料來源現在可用於&#x200B;**變更資料來源**&#x200B;活動。
* 已在&#x200B;**錯誤管理**&#x200B;工作流程活動中新增屬性：**錯誤時中止**&#x200B;選項會自動停止工作流程。 之後將無法重新啟動 (NEO-29661)。 [閱讀全文](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* 專用序列現在用於產生 nmsGroup 表的主要金鑰，此表用於建立收件者的統計分組。 之前使用 xtknewId 序列。 (NEO-30832)
* 新增支援，以便使用 CRM 連接器活動批次更新作業。
* 改進傳送交易訊息的處理時間。 (NEO-40370)

**修補程式**

* 修正在建立傳遞時，導致&#x200B;**追蹤與影像**&#x200B;視窗的&#x200B;**影像**&#x200B;標籤發生錯誤的問題。 使用自動代理設定時會發生此問題。 (NEO-33260)
* 修正可能導致您無法在同步模式下，在 Debian 10 伺服器 (HTTPS) 上傳檔案的問題。
* 修正在刪除相關傳遞後，可能導致無法在資料庫清理期間從中間來源執行個體中清除傳遞統計資訊表 (`nmsDeliveryLogStats`) 記錄的問題。(NEO-31034)
* 修正在使用權杖進行身份驗證時，導致無法在 iOS 上傳送行動應用程式通知的問題 (NEO-38640)。
* 修正在嘗試建立和設定報表時，可能導致顯示指令碼錯誤訊息的問題 (NEO-38393)。
* 修正在同時更新大量傳送指標時，導致 Oracle 追蹤工作流程失敗的問題 (NEO-39653)。
* 修正問題，在執行控制類型時，該問題導致錯誤而無法送出傳遞 (NEO-39833)。
* 修正登陸頁面上，可能導致線上意見調查回覆 HTML 頁面無法正確顯示特殊字元的問題 (NEO-39438)。
* 修正在 Explorer 標籤以滑鼠右鍵按一下任何資料夾時，可能導致 Campaign Classic 主控台無法運作的問題 (NEO-38884)。
* 修正在新傳遞中使用先前建立的傳遞範本時，導致缺少 Web Analytics 設定的錯誤。(NEO-28666)
* 修正可能導致您無法預覽附加至工作流程的行動傳遞問題。
* 修正在啟用追蹤連結的 URL 簽章機制時，發生無法重新導向個人化追蹤 URL 的錯誤。
* 修正因索引管理問題在升級後導致失敗的問題。
* 修正在&#x200B;**匯入**&#x200B;或&#x200B;**匯出**&#x200B;工作流程活動中使用 Microsoft Dynamics CRM 查閱欄位資料類型時產生的錯誤。
* 修復因代理設定問題而無法登入主控台的問題。(NEO-38388)
* 修正了妨礙&#x200B;**清除資料夾**&#x200B;功能正常運作的問題。 (NEO-37459)
* 修復在搭配 Microsoft Dynamics CRM 帳戶使用 xml 資料欄位時，因參考的 xml 包含雙引號導致錯誤要求的問題。
* 修復在網路逾時，導致不正確記錄為指令碼中斷而非網路錯誤的問題。 如果 HTTP 要求包含在 JavaScript 活動中，會發生此問題。(NEO-38079)
* 修正了在嘗試提取時間元件時，執行 Amazon Redshift HoursDiff 和 MinutesDiff 函式時傳回錯誤結果的問題。(NEO-31673)
* 修正自版本編號 9182 以來，無法載入傳遞&#x200B;**熱門點擊**&#x200B;報告的問題。 (NEO-28900)
* 修復在以字元實體參照 (`&amp;`) 取代 URL 中的 &amp; 符號時，導致使用者無法存取連結至 QR 碼 URL 的錯誤。(NEO-28621)
* 修復當使用者建立新促銷活動工作流程並連結至 Web Analytics 帳戶的傳遞活動時，會建立新外部帳戶的問題。這是因為 webAnalyticsAccount 傳遞物件中缺少 ID 所致。 (NEO-39691)
* 修正了&#x200B;**讀取清單** 在資料庫中以負 ID 識別清單時，工作流程活動無法運作的問題。 (NEO-39607)
* 修正可能導致&#x200B;**中間來源 (傳遞記錄)**&#x200B;工作流程失敗的問題。(NEO-39662)
* 修正可能導致無法預覽附加至工作流程的電子郵件傳遞的問題。(NEO-37840)
* 修正可能導致資料庫清理工作流程刪除包含清單值的有效表格的問題。 (NEO-34911)
* 修正可能導致計費工作流程在行銷執行個體中造成當機的問題。
