---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 96%

---

# 最新版本 {#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 發行版本 7.4.2  {#release-7-4-2}

### 建置9391 {#build-9391}

[!BADGE 有限可用性]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="有限可用性"}

_2025年5月12日_

此版本編號包含以下修正：

* 修正了在非Oracle設定中遇到的升級後問題。 (NEO-87012)
* 修正同時影響使用者端主控台和伺服器的TLS / HTTPS後端問題。 (NEO-87432)

### 建置9390 {#build-9390}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

_2025 年 4 月 2 日_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**安全性改善**

此版本附帶幾個安全修正。

透過 **[!UICONTROL Adobe Experience Cloud]** 外部帳戶與 Adobe 解決方案和應用程式的連線已更新，以加強安全性。

**主要修正**

此版本包含下列主要修正：

* TLS / SMPP 連線 — 修正 SMPP 穩定性問題

* Google BigQuery 修正：

   * 修正 BOOLEAN 資料類型的回歸問題
   * 修正 Proxy 設定問題
   * 修正 DATETIME 資料類型的回歸問題
   * 固定大量負載穩定性
   * 改善 ODBC 版本的內部測試
   * 修正連接字串特殊字元的問題
   * 已移除 Google BigQuery 查詢的預設逾時 (5 分鐘)

* 郵件傳輸代理程式 (MTA) — 已修正孤立 MTA 子代理卡在 **[!UICONTROL Start pending]** 狀態的問題。


**其他修正**

此版本還修正下列問題：

* 修正&#x200B;**資料載入 (檔案)** 活動無法將檔案上傳至伺服器<!--after an upgrade to version 8.3.8-->的問題。 使用者現在可以成功上傳檔案，並且不會遇到進度卡住或控制台錯誤的問題。(NEO-47269)

* 已解決 Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349--> 中的分段錯誤問題。此修正可防止核心檔案產生，並確保伺服器穩定運作。 (NEO-59059)

* 已解決與 Google BigQuery 資料庫 <!--after upgrading to version 7.3.3 build 9359--> 的連線問題。 使用者現在可以使用 GCP 外部帳戶成功測試連線。 (NEO-62455)

* 增強與使用同盟資料存取 (FDA) Google BigQuery 表格中布林值和日期時間欄更新的相容性。 此修正可確保在插入/更新作業期間正確處理資料類型。(NEO-65774)

* 修正了允許攻擊者將 HTML 元素插入電子郵件端點的資源插入漏洞。 此安全性增強功能可防止未經授權的存取和網路釣魚攻擊。(NEO-66462)

* 解決因 HTTP 內容或傳輸編碼問題而導致插入資料至 Google BigQuery 資料表時出現的間歇性錯誤。此修正可確保穩定的資料載入工作流程。 (NEO-66989)

* 已解決工作流程中`File.list()`方法的路徑周遊漏洞。此安全性增強功能可防止未經授權的目錄存取並保護敏感檔案。 (NEO-77898)

* 修正 SMS 傳送記錄檔未正確更新為「在行動裝置上接收」狀態的問題。 此增強功能可確保傳送報告的準確性。 (NEO-78843)

* 解決在使用 Azure 同盟資料存取 (FDA) 時，Adobe Campaign Classic 登入錯誤的問題。使用者現在可以透過使用者端主控台成功登入。 (NEO-79373)

* 修正由 `CCurlAzureBlobStorage::UploadStream()` 方法造成的工作流程當機問題。 此增強功能可確保穩定的工作流程執行。 (NEO-79598)

* 在 Windows 上啟用兩個重要編譯旗標 (`ControlFlowGuard`和`StackProtection`)，以增強產品安全性並降低利用風險。 (NEO-80145)

* 已修復在 Broadlog 處於失敗狀態時，事件狀態傳送不正確的問題。此增強功能可確保提供準確的事件報告。 (NEO-80245)

* POP3 OAuth 重新整理和存取權杖現在儲存在資料庫中，重新整理權杖過期後，`Authentication failure: unknown user name or bad password` 錯誤不再出現。 (NEO-80683)

* 選項 `XApiKey` 現在可用來作為使用者端 ID 的值，以連線至 Adobe Analytics，而不是使用 Marketing Cloud (MAC) 外部帳戶的使用者端 ID。 (NEO-80434)

* 解決 inMail 使用者因權杖過期而發生驗證錯誤的問題。 使用者現在可以測試連線並重新啟動伺服器以解決類似問題。 (NEO-80683)

* 改善分析 API 功能，確保所有分析呼叫使用一致的 API 金鑰 (Campaign1) 進行驗證，即使切換至隨機用戶端 ID 亦然。 這可確保順暢的分析追蹤。 (NEO-80434)

* 增強 BigQuery 同盟資料存取 (FDA) 連接器，允許使用者調整查詢逾時期間。 此項改善可防止長時間執行查詢時發生逾時錯誤。 (NEO-81222)

* 更新 Campaign <!--7.4.1--> 版本升級程式，以包含必要的相依性。 此增強功能簡化了使用者的升級流程。 (NEO-81433)

* 修正搭配 `enum` 欄位使用子工作流程時的主控台當機問題。 此增強功能可確保穩定的工作流程執行。 (NEO-81864)

* 解決 MTA 下層處理序卡住、封鎖傳送槽的問題。 此修正可確保推播和 WhatsApp 通訊的順暢傳送作業。 (NEO-82351)

* 修正傳送因暫停傳送活動而卡在個人化待處理狀態的問題。此增強功能可確保成功執行傳送。 (NEO-82781)

* 運用 CampaignIO 端點進行驗證，增強了 IMS 登入功能。此項改善能簡化登入過程。(NEO-82838)

* 重新處理了 Google BigQuery 同盟資料存取 (FDA) 逾時錯誤，確保熱修復部署後查詢執行穩定。(NEO-82923)

* 解決將大型資料磁碟區載入 Teradata 表格時的空間問題。 此增強功能可確保穩定的資料載入作業。 (NEO-83252)

* 修正由於日期和時間戳記比較不相符而導致 GCP 查詢失敗的問題<!--after upgrading to version 9383-->。 此增強功能可確保查詢相容性。 (NEO-83826)

* 已解決因繼續暫停的傳送活動所導致的傳送失敗問題。 此修正可確保成功執行傳送。 (NEO-83809)

* 修正在使用私密金鑰認證時，Snowflake 同盟資料存取 (FDA) 連接器的驗證錯誤。 此增強功能可確保成功的資料庫連線。 (NEO-84024)

* 實施了監控程式變更，以解決因程式停滯所導致的 MTA 下層插槽封鎖。 此增強功能可確保順暢的傳送作業。 (NEO-84553)

* 增強了 JavaScript 等待檢查，以解決由處於工作狀態的處理序所導致的 MTA 下層插槽封鎖問題。此修正可確保穩定傳送作業。 (NEO-85150)

