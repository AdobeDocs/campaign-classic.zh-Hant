---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '993'
ht-degree: 100%

---

# 最新版本{#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本 7.3.3 - 版本編號 9359 {#release-7-3-3}

[!BADGE 一般可用性]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

>[!CAUTION]
>
>用戶端主控台升級為強制。 透過本[頁面](../../installation/using/installing-the-client-console.md)了解如何升級您的用戶端主控台。

_2023 年 3 月 20 日_

**安全性增強功能**

* 為了最佳化安全性，已將 Tomcat 從 8.5.81 版更新至 8.5.85 版。(NEO-56936)

**功能改進**

* 已改善「帳單」工作流程以最佳化效能。(NEO-47658)
* 已改善追蹤工作流程，以在傳送大小較大的情況下最佳化效能。(NEO-45064)
* 已改善追蹤管理，以修正 URL 中動態參數可能出現的問題。追蹤管理 v3 現在可處理 ajax 類型的 URL (參數在「#」之後)，並避免協力廠商工具修改追蹤 URL。若要套用此變更，您必須聯絡 Adobe。(NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**修補程式**

* 修正了可能無法從控制項執行個體 (交易式訊息內容) 傳送 iOS 校訂推播通知的問題。(NEO-54713)
* 修正了無法在數位內容編輯器 (DCE) 捲動&#x200B;**編輯**&#x200B;索引標籤的問題。 (NEO-54474)
* 修正當兩個擴充活動在其連結中使用相同名稱識別碼時，導致第二個擴充活動使用第一個活動的連結問題。(NEO-48851)

## 版本 7.3.2 - 版本編號 9356 {#release-7-3-2}

[!BADGE 有限可用性]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="有限可用性"}

_2022 年 11 月 21 日_

>[!CAUTION]
>
>用戶端主控台升級為強制。 透過本[頁面](../../installation/using/installing-the-client-console.md)了解如何升級您的用戶端主控台。

**相容性更新**

* Adobe Campaign 現在相容於 PostgreSQL 14。 如需詳細資訊，請參閱本[技術說明](../../technotes/using/tech-stack-upgrade.md)。

* Microsoft Internet Explorer 11 生命週期結束後，用戶端主控台中的儀表板轉譯引擎現在使用 Edge Chromium。(NEO-20741)

瞭解更多與[ Campaign 相容性矩陣相關的資訊](../../rn/using/compatibility-matrix.md#RDBMSservers)。

**功能改進**

* Google BigQuery 連接器現在完全支援布林欄位。 (NEO-49181)
* 您現在可以在 serverConf.xml 檔案的 `Configuration for the redirection service` 區段設定 IMS Cookie 有效期間。 這適用於下列 Cookie：`uuid230`、`nllastdelid` 和 `AMCV_` (NEO-42541)
* 現在，您可以透過將 serverConf.xml 檔案的重新導向節點中的 `showSourceIP` 設定為 false，IP 可以隱藏在 &quot;/r/test&quot; 請求中。 [閱讀全文](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**已棄用功能**

* 使用 Facebook 的社交行銷現已棄用。您可以使用 Twitter 整合在社交媒體上發佈貼文，或使用 Adobe 建立自訂頻道。
* ACS Connector (Prime 產品) 現已棄用。 您可以使用 Campaign 匯出/匯入功能，在兩個產品中擷取和插入資料。

在[與已棄用和已移除的功能頁面](deprecated-features.md)瞭解更多相關的資訊。

**其他變更**

* 網頁記錄已改善：現在只會針對具有管理員權限的使用者顯示 `logonEscalation` 警告。 (NEO-47167)
* 為避免錯誤， **收集熱度圖服務的資料** (collectDataHeatMapService) 工作流程現在預設為停止。 (NEO-33959)
* 已實施各種改善，以最佳化行銷活動儀表板的 CPU 使用量。 (NEO-46417)
* 為避免當機，已移除 loadLibraryDebug JS 方法。 (NEO-46968)
* 對 log4j 程式庫的其餘參考已從 Windows 上安裝的 Campaign 中移除。 (NEO-44851)

**修補程式**

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
