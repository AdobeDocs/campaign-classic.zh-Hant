---
product: campaign
title: Campaign Classic 2023 版本
description: 進一步瞭解 Campaign Classic 2023 版本
feature: Release Notes
role: User
level: Beginner
exl-id: 8ed11e96-9f23-4e2e-bae2-25c51cfb549a
source-git-commit: f39dc6077a7ddc3fb9b53d4082c08e65e7683f10
workflow-type: tm+mt
source-wordcount: '2337'
ht-degree: 100%

---

# 2023 版本{#release-2023}

## 版本 7.3.5 - 版本編號 9368 {#release-7-3-5}

[!BADGE 有限可用性]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="有限可用性"}

_2023 年 12 月 5 日_

### 安全性增強功能 {#release-7-3-5-security}


* 透過 Campaign Classic v7.3.5，驗證流程已獲得改善並提高安全性。技術操作者現在應使用 Adobe Identity Management System (IMS) 來連線至 Campaign。透過[此技術說明](../../technotes/using/ims-migration.md)了解如何移轉您現有的技術帳戶。

* 此外，為了強化安全性和驗證流程，Adobe Campaign 強烈建議將一般使用者驗證模式從登入/密碼原生驗證移轉至 Adobe Identity Management System (IMS)。閱讀此[技術說明](../../technotes/using/migrate-users-to-ims.md)，了解如何移轉操作者。

* 現在，當網頁表單具有&#x200B;**待發佈**&#x200B;狀態，其不會自動上線。為了防止安全性問題，務必在&#x200B;**上線**&#x200B;之前予以發佈，並透過網頁瀏覽器中的網頁表單 URL 存取。[深入了解](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### 其他增強功能 {#release-7-3-5-other}

自此版本開始，已傳送電子郵件上的追蹤連結在升級期間仍可運作。 [閱讀更多](../../platform/using/faq-build-upgrade.md)

### 修補程式 {#release-7-3-5-patches}

* 修正使用來自 Google Big Query 資料庫的資料並更新 Oracle 資料庫中的資料時的問題： 工作流程暫存表格中所有金鑰皆設為 `0`。 (NEO-65091)
* 修正將 Google Big Query 資料庫上的兩個查詢合併到&#x200B;**聯合**&#x200B;工作流程活動時，導致工作流程執行失敗的問題。(NEO-63705)
* 修正了在按一下 Campaign 報告中的 `Back` 按鈕時要求使用者重新驗證的問題。(NEO-65087)
* 修正資料庫清理工作流程中，在傳遞校樣之前刪除傳遞時所發生的錯誤。 (NEO-48114)
* 修正連線至用戶端主控台時的問題：最近 TLS 驗證更新導致連線錯誤。(NEO-50488)
* 修正 Campaign 升級至 7.3.1 後 HTTP Proxy 驗證的問題。行銷活動工作流程中的 HTTP 請求失敗，因為 `error 407 – proxy auth required is returned`。 (NEO-49624)
* 修正&#x200B;**指令碼**&#x200B;工作流程活動中 GPG 解密的間歇性失敗。相關的錯誤訊息為：`gpg: decryption failed: No secret key`。(NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->




## 版本 7.3.4 - 版本編號 9364 {#release-7-3-4}

[!BADGE 有限可用性]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="有限可用性"}


>[!CAUTION]
>
>用戶端主控台升級為強制。 透過本[頁面](../../installation/using/installing-the-client-console.md)了解如何升級您的用戶端主控台。
>
>如果您使用 [Campaign - Microsoft Dynamics CRM 連接器](../../platform/using/crm-connectors.md)，您必須使用此新版本升級行銷和中間來源伺服器。

_2023 年 9 月 7 日_

### 安全性增強功能 {#release-7-3-4-security}

* 已改善 IMS API 中的安全性。 已從 URL 參數中移除用戶端敏感資訊 (即存取權杖) 這些認證現在會以 POST 資料或授權標頭傳送，以確保通訊程序更加安全。 (NEO-63045)
* 已改善網頁應用程式中的安全性，以防止 DDOS 攻擊。 (NEO-50757)
* 已增強安全性，以防止在網頁記錄錯誤中公開 PII 資料。 (NEO-46827)
* 已最佳化安全性，以防止在 Campaign 首頁 URL 中包含安全性權杖。 (NEO-38519)

### 相容性更新  {#release-7-3-4-compat}

* Tomcat 已更新至 8.5.91 版
* libexpat 程式庫已更新至 2.5.0 以改善安全性。 (NEO-51023)

### 功能改進 {#release-7-3-4-improvements}

* 已修改伺服器設定檔案 (serverConf.xml) 中的 MaxWorkingSetMb 參數，以最佳化傳遞的記憶體配置。 (NEO-49204)
* 已增強 BigQuery 外部帳戶，並新增用於設定 GCloud SDK 的選項。 (NEO-63879) [閱讀全文](../../installation/using/configure-fda-google-big-query.md#google-external)
* 已在伺服器設定檔案 (serverConf.xml) 中新增 `cusHeader` 區段。其可讓您從外部伺服器上傳檔案時新增自訂標頭。 (NEO-58339) [閱讀全文](../../installation/using/the-server-configuration-file.md#cusheaders)。
* 已改善追蹤記錄管理，以避免 lastMsgId 出現負值的 ID。 其已從 int32 變更為 int64。 (NEO-52290)
* 已新增現成可用的中間來源 (傳遞統計資料) 工作流程。 這個新的工作流程會將傳遞統計資料 (nms:deliveryStat) 從 MID 同步至行銷執行個體。 (NEO-36802)

### 修補程式 {#release-7-3-4-patches}

* 已修正服務要求呼叫驗證若使用服務權杖，在 IMS 登入前提出服務要求時可能發生的問題。 (NEO-64903)
* 已修正使用數位內容編輯器時可能導致捲動問題的迴歸問題。 (NEO-64671、NEO-59256)
* 已修正將 Excel 中的內容貼至數位內容編輯器時發生的迴歸問題。 (NEO-63287)
* 已修正無法在 v5 相容性模式中正確顯示網頁應用程式的問題。 (NEO-63174)
* 已修正非管理員操作者無法傳送 webAnalytics 傳遞的問題。 (NEO-62750)
* 已修正瀏覽器使用傳遞中的條件式內容時，無法新增額外空格的問題。 (NEO-62132)
* 已修正使用與多個記錄結構描述相關聯的目標結構描述時，有效聯絡人計算無法在帳單工作流程中正確運作的問題。 (NEO-61468)
* 已修正可能導致發生錯誤，以及讓您無法在編輯傳遞內容時進行捲動的問題。 (NEO-61364)
* 已修正在電子郵件內容編輯器中按一下影像時，造成快顯視窗開啟的問題。 (NEO-60752)
* 已修正可能導致傳遞的 HTML 內容中的特殊字元在數種瀏覽器中編碼錯誤的問題。 (NEO-60081)
* 已修正使用 in簡訊工作流程活動時可能發生的同步問題。 (NEO-59544)
* 已修正使用具有時間戳記或日期時間欄位的 Big Query 連結器時所發生的問題。 (NEO-59502、NEO-49768)
* 已修正無法使用累積傳遞報告的問題。 (NEO-59211)
* 已修正與人員核心服務共用對象時可能導致發生錯誤的問題。 (NEO-58637)
* 已修正顯示傳遞鏡像頁面時的問題。 (NEO-58325)
* 已修正導致 XtkLibrary.Right() xtk 運算式無法運作的問題。 (NEO-57870)
* 已修正在數位內容編輯器上傳影像時，導致內文標籤的樣式屬性有所變更的問題。 (NEO-57697)
* 已修正使用 CRM 連結器活動執行批次匯出時發生的特殊字元問題。 (NEO-54300)
* 已修正使用資料載入活動和 Big Query 連結器時，導致無法使用「字串」資料類型進行大量載入的問題。 (NEO-53748)
* 已修正可能導致活動內容轉譯問題的快取金鑰問題。 (NEO-51516、NEO-49995)
* 已修正使用 targetMapping 搭配核准來傳送直接郵件傳遞時，可能導致發生驗證錯誤的問題。 (NEO-50758)
* 已修正可能影響傳遞效能的查詢管理問題。 (NEO-49991)
* 已修正在行銷活動工作流程傳遞活動中使用外部帳戶時，可能導致發生外部帳戶設定問題的問題。 (NEO-49959)
* 已修正傳送推播通知時發生的效能問題。 (NEO-49953)
已修正匯出報告時，可能導致日文字元無法正確顯示的問題。(NEO-49308)
* 已修正造成 Tomcat 錯誤報告顯示過多錯誤詳細資料的問題。 (NEO-49029)
* 已修正使用大量活動內容時，可能導致發生傳遞錯誤的問題。 (NEO-48807)
* 已修正可能導致&#x200B;**更新資料**&#x200B;工作流程活動無法正常運作的問題。(NEO-48140)
* 已修正使用與電子郵件不同的外部帳戶無法對傳遞同步點擊追蹤資料的問題。(NEO-47277)
* 已修正無法在訊息中心行銷執行個體上同步即時追蹤記錄的問題。 (NEO-42540)
* 已修正 Snowflake 資料庫資料表無法在結構描述的探索視窗中顯示工作區前置詞的問題。 (NEO-40297)
* 已修正導致 `<img-amp>` 標記無法在電子郵件內容中運作的問題。 (NEO-38685)
* 已修正使用 HTTP 轉送時，可能導致訊息中心封存工作流程失敗的問題。 (NEO-33783)
* 已修正電子郵件內容編輯器中可能導致字型名稱和大小錯誤的問題。 (NEO-61342)

## 版本 7.3.3 - 版本編號 9359 {#release-7-3-3}

[!BADGE 有限可用性]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="有限可用性"}

>[!AVAILABILITY]
>
>此版本提供特定的 Campaign v7.3.3.IMS 修補程式升級 - 如果沒有其他修補程式套用至您的環境。它帶來了 [Adobe Identity Management System (IMS) 安全性更新，包含 v7.3.5](#release-7-3-5-security) 至現有的 v7.3.3 環境。


_2023 年 3 月 20 日_


### 安全性增強功能 {#release-7-3-3-security}

* 為了最佳化安全性，已將 Tomcat 從 8.5.81 版更新至 8.5.85 版。(NEO-56936)


### 功能改進 {#release-7-3-3-improvements}

* 已改善「帳單」工作流程以最佳化效能。(NEO-47658)
* 已改善追蹤工作流程，以在傳送大小較大的情況下最佳化效能。(NEO-45064)
* 已改善追蹤管理，以修正 URL 中動態參數可能出現的問題。追蹤管理 v3 現在可處理 ajax 類型的 URL (參數在「#」之後)，並避免協力廠商工具修改追蹤 URL。若要套用此變更，您必須聯絡 Adobe。(NEO-46535)
* 自此版本開始，已傳送電子郵件上的追蹤連結在升級期間仍可運作。 [閱讀更多](../../platform/using/faq-build-upgrade.md)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>用戶端主控台升級為強制。 透過本[頁面](../../installation/using/installing-the-client-console.md)了解如何升級您的用戶端主控台。

### 修補程式 {#release-7-3-3-patches}

* 修正了可能無法從控制項執行個體 (交易式訊息內容) 傳送 iOS 校訂推播通知的問題。(NEO-54713)
* 修正了無法在數位內容編輯器 (DCE) 捲動&#x200B;**編輯**&#x200B;索引標籤的問題。 (NEO-54474)
* 修正當兩個擴充活動在其連結中使用相同名稱識別碼時，導致第二個擴充活動使用第一個活動的連結問題。(NEO-48851)

## 版本 7.3.2 - 版本編號 9356 {#release-7-3-2}

[!BADGE 有限可用性]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="有限可用性"}


>[!AVAILABILITY]
>
>此版本提供特定的 Campaign v7.3.2.IMS 修補程式升級 - 如果沒有其他修補程式套用至您的環境。它帶來了 [Adobe Identity Management System (IMS) 安全性更新，包含 v7.3.5](#release-7-3-5-security) 至現有的 v7.3.3 環境。

_2022 年 11 月 21 日_

### 相容性更新 {#release-7-3-2-compat}

* Adobe Campaign 現在相容於 PostgreSQL 14。 如需詳細資訊，請參閱本[技術說明](../../technotes/using/tech-stack-upgrade.md)。

* Microsoft Internet Explorer 11 生命週期結束後，用戶端主控台中的儀表板轉譯引擎現在使用 Edge Chromium。(NEO-20741)

瞭解更多與[ Campaign 相容性矩陣相關的資訊](../../rn/using/compatibility-matrix.md#RDBMSservers)。

>[!CAUTION]
>
>用戶端主控台升級為強制。 透過本[頁面](../../installation/using/installing-the-client-console.md)了解如何升級您的用戶端主控台。

### 功能改進 {#release-7-3-2-improvements}

* Google BigQuery 連接器現在完全支援布林欄位。 (NEO-49181)
* 您現在可以在 serverConf.xml 檔案的 `Configuration for the redirection service` 區段設定 IMS Cookie 有效期間。 這適用於下列 Cookie：`uuid230`、`nllastdelid` 和 `AMCV_` (NEO-42541)
* 現在，您可以透過將 serverConf.xml 檔案的重新導向節點中的 `showSourceIP` 設定為 false，IP 可以隱藏在 &quot;/r/test&quot; 請求中。 [閱讀全文](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)
* 自此版本開始，已傳送電子郵件上的追蹤連結在升級期間仍可運作。 [閱讀更多](../../platform/using/faq-build-upgrade.md)


### 已棄用功能  {#release-7-3-2-deprecated}

* 使用 Facebook 的社交行銷現已棄用。您可以使用 X (原 Twitter) 整合在社交媒體上發佈貼文，或使用 Adobe 建立自訂通道。
* ACS Connector (Prime 產品) 現已棄用。 您可以使用 Campaign 匯出/匯入功能，在兩個產品中擷取和插入資料。

在[與已棄用和已移除的功能頁面](deprecated-features.md)瞭解更多相關的資訊。

### 其他變更  {#release-7-3-2-other}

<!--* Web logs have been improved: `logonEscalation` warnings are now only displayed for users with admin privileges. (NEO-47167)-->
* 為避免錯誤， **收集熱度圖服務的資料** (collectDataHeatMapService) 工作流程現在預設為停止。 (NEO-33959)
* 已實施各種改善，以最佳化行銷活動儀表板的 CPU 使用量。 (NEO-46417)
* 為避免當機，已移除 loadLibraryDebug JS 方法。 (NEO-46968)
* 對 log4j 程式庫的其餘參考已從 Windows 上安裝的 Campaign 中移除。 (NEO-44851)

### 修補程式 {#release-7-3-2-patches}

* 修正無法使用&#x200B;**合併所選行**&#x200B;工作流程選項的問題。 (NEO-48488)
* 當使用 Adobe Campaign Enhanced MTA 時，**成功**&#x200B;傳送指標無法正確更新，該問題已修正。 (NEO-50462)
* 修正重設電子郵件傳送中的內容核准時，無法重新核准的問題。 (NEO-44259)
* 修正可能阻止&#x200B;**傳遞核准**&#x200B;按鈕顯示的問題。 (NEO-47547)
* 修正傳送 HTML 標籤中，大型 HTML 程式碼可能發生的效能問題。 (NEO-47440)
* 修正啟用`FeatureFlag_GZIP_Compression`選項時，影響 MID 執行個體上傳送記錄狀態更新的問題。 (NEO-49183)
* 修正了使用權杖式驗證時，無法從執行實例傳送 iOS 行動應用程式通知的問題。 (NEO-45961)
* 修正當有太多要同步的 broadlog 時，**傳遞能力重新整理**&#x200B;工作流程 (deliverabilityUpdate) 卡住的問題。 (NEO-48287)
* 修正封鎖&#x200B;**訊息中心同步** (mcSynch) 工作流程的事件類型問題。
* 修正在&#x200B;**查詢** 工作流程活動的其他資料中新增&#x200B;**已開啟的收件者**  (estimatedRecipientOpen) 指標導致錯誤的問題。(NEO-46665)
* 修正在同一執行個體上安裝訊息中心控制和執行套件時失敗的&#x200B;**帳單**&#x200B;工作流程的問題。 (NEO-47674)
* 修正將主要金鑰定義為字串而非整數的表格時失敗的&#x200B;**帳單**&#x200B;工作流程的問題。 (NEO-46254)
* 修正工作流程名稱太長時的熱度圖篩選器問題。 (NEO-46301)
* 修正 7.3.1 中針對 Snowflake FDA 連接器所引入的問題，此問題在擴充期間使用「0 或 1 基數簡單加入」時，會導致記錄遭到捨棄。 (NEO-48737)
* 修正使用&#x200B;**分割**&#x200B;工作流程活動中的排序參數時 Snowflake FFDA 的問題。 (NEO-45899)
* 修正了無法儲存外部帳戶設定的問題。 現在，具有剖析器功能的連接器 (Snowflake 和 Google BigQuery) 的外部帳戶會在連線測試後自動儲存。 (NEO-47636)
* 修正無法 MSSQL 上的&#x200B;**資料更新** 工作流程活動中插入時間資料類型的問題。 (NEO-47763)
* 修正未設定 (MSSQL 專用) 引擎時區時，導致 MTA 程式當機的問題。 (NEO-46619)
* 修正當影像節點 (img) 包含具有個人化欄位的 URL 時，HTML 檔案匯入的問題。 (NEO-48396)
* 修正嘗試連線至執行個體時，未在 serverConf.xml 檔案中設定`limit`節點，發生 HTTP 500 錯誤的問題。
* 修正在未啟用的 NChar的Oracleunicode 資料庫中使用某些函式 (例如 `to_nclob`) 時可能導致「字元集不匹配」錯誤的問題。 (NEO-49361)
* 修正了當 nmsDeliveryMapping 資料夾上具有讀取存取權限的使用者嘗試執行行銷活動或工作流程時，導致錯誤的問題。 (NEO-48230)
* 修正使 `JSPContext.sqlExecWithOneParam` 函式無法運作的問題。 (NEO-50066)
* 修正了各種重新導向錯誤。 (NEO-50030)
