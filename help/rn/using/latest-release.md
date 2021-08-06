---
product: campaign
title: 最新版本
description: 最新的 Campaign Classic 發行說明
feature: 概覽
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: c59529a0a4d72ecb795569591d62a68f030a0ac7
workflow-type: tm+mt
source-wordcount: '1951'
ht-degree: 99%

---

# 最新發行版本{#latest-release}

本頁列出&#x200B;**最新Campaign Classic版本**&#x200B;的新功能、改善和修正。

>[!NOTE]
>
>Campaign **一般可用性 (GA) 版本**&#x200B;包括：[[!DNL Gold Standard] 11 版本](../../rn/using/gold-standard.md#gs-11)和[Campaign 21.1.3 版本](../../rn/using/latest-release.md#release-21-1-3-build-9330)。

## ![](assets/do-not-localize/green_2.png) 發行版本 21.1.3 - 版本編號 9330 {#release-21-1-3-build-9330}

_2021 年 6 月 5 日_

**新增功能？**

<table>
<thead>
<tr>
<th><strong>與 Adobe Journey Orchestration 整合</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Journey Orchestration 與 Adobe Campaign Classic 的整合現已正式推出。 它可讓 Journey Orchestration 使用 Adobe Campaign Classic 異動訊息功能來傳送電子郵件、推播通知和 SMS。</p>
<p>Journey Orchestration 與 Campaign Classic 執行個體之間的連線在佈建時由 Adobe 設定。</p>
<p>如需詳細資訊，請參閱 <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=zh-Hant">Journey Orchestration 文件</a>。<a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=zh-Hant">本節</a>中提供了逐步使用案例</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>LINE 頻道增強功能</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>LINE 頻道已新增下列改良功能：
</p>
<ul> 
<li><p>支援 LINE 視訊訊息類型</p></li>
<li><p>支援 LINE 合作夥伴註冊 API</p></li>
<li><p>支援在出現 LINE 伺服器端錯誤或網路逾時時重試傳送訊息</p></li>
</ul>
<p>如需詳細資訊，請參閱<a href="../../delivery/using/line-channel.md">詳細文件</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA 連接器</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您現在可以將 Adobe Campaign Classic 執行個體連線至 Vertica 外部資料庫。 此連線透過新的外部帳戶進行管理。</p>
<p>如需詳細資訊，請參閱<a href="../../installation/using/configure-fda-vertica.md">詳細文件</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA 連接器</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您現在可以將 Adobe Campaign Classic 執行個體連線至 Google Big Query 外部資料庫。 此連線透過新的外部帳戶進行管理。
</p>
<p>如需詳細資訊，請參閱<a href="../../installation/using/configure-fda-google-big-query.md">詳細文件</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增強功能**

* 傳回完整資料庫連線詳細資訊的 **xtk:session#GetCnxInfo** API 方法現在僅限管理員使用者存取。 (NEO-27779)
* 在 CRM 相關的 JavaScript 檔案中，已棄用的 decryptString 函式已取代為 decryptPassword。
* 已改善追蹤簽章功能，以在第三方工具 (電子郵件用戶端、網際網路瀏覽器、安全連結安全工具) 修改追蹤連結時，降低追蹤重新導向錯誤的風險。
* 修正了當包含大寫字元時，追蹤的 URL 無法運作的問題。 追蹤的 URL 簽署機制現在區分大小寫。 (NEO-28414)

**相容性更新**

下列系統現在已支援 Campaign：
* Google Big Query FDA 連接器
* Vertica FDA 連接器
* PostgreSQL 13

瞭解更多與[ Campaign 相容性矩陣相關的資訊](../../rn/using/compatibility-matrix.md)。

**棄用的功能**

* 自 Campaign 第 21.1 發行版本開始，已棄用 Adobe Analytics 資料連接器。 如果您使用此連接器，則需使用新連接器 Adobe Analytics 連接器，據以調整實施。
如需詳細資訊，請參閱[詳細文件](../../technotes/aa-connector-migration.md)。
* 不再支援 Debian 8。
* 在 20.3 版中淘汰 Oracle CRM 後，相關外部帳戶已從介面中移除。

瞭解更多[與已棄用和已移除的功能頁面相關的資訊](../../rn/using/deprecated-features.md)。

**功能改善**

* 儲存工作流程時已新增額外檢查，以確定活動名稱是唯一的，且轉變後一律會有活動。
* **「帳單」 (帳單)**&#x200B;技術工作流程現在包含原本由&#x200B;**活動帳單設定檔數**(billingActiveContactCount) 工作流程執行的任務，此工作流程已移除。 工作流程每月傳送的電子郵件報告現在會提供執行個體上主要設定檔數目的資訊。 [顯示全文](../../workflow/using/about-technical-workflows.md)。
* 已新增新的 **_keyOnMData** 屬性，以便能夠使用鍵對備忘錄資料進行操作。

**其他變更**

* 適用於 Windows 的 openssl 協力廠商已更新至 1.1.1h 版。
* 在 Debian 套件說明中，nlserver 已變更為 Adobe Campaign Classic 伺服器。

**修補程式**

* 針對當在編輯工作階段逾時以在特定時間之後登出使用者時，修正使用者在設定的事件之後仍維持登入狀態的問題。
* 針對顯示為唯讀的傳送，修正仍可編輯傳送屬性的問題。
* 修正當設計 Web 應用程式時造成編輯工具列消失的錯誤。
* 針對當在電子郵件新增連結時，修正在電子郵件顯示文字版 Adobe Campaign Classic 標題的錯誤。 (NEO-29211
* 使用 FDA 透過 HTTP 連線時，**中間來源 (傳送記錄檔)**(defaultMidSourcingLog) 工作流程卡在&#x200B;**NmsMidSourcing_LogsPeriodHour**&#x200B;選項所設定的時間範圍內。 此舉會造成在此設定的時間範圍之後的資料無法更新至記錄中。 (NEO-30833)
* 修正在執行訊息中心同步工作流程之後所發生的問題。 每次將傳送對象資料夾移至自訂資料夾時，工作流程都會將傳送移回一般&#x200B;**異動訊息歷史記錄**&#x200B;資料夾。 (NEO-27445)
* 修正當嘗試顯示&#x200B;**廣播統計資料**、**追蹤指標**&#x200B;和&#x200B;**共用活動統計資料**&#x200B;報告時顯示錯誤訊息的問題。
* **Oracle 隨選**&#x200B;工作流程活動已在 OracleCRM 連接器淘汰後從介面中移除。
* 針對在每日重新啟動工作流程伺服器 (wfserver) 模組之後，修正停止執行處理工作流程的問題。 (NEO-30047)
* 修正無法更新 MX 管理文件的問題，這可能對 IP 信譽造成負面影響。 (NEO-29897)
* 修正當收到 SOAP 呼叫時導致 Web 流程當機的問題。 (NEO-28796) (NEO-29600)
* 修正導致建立 SAP HANA FDA 索引失敗的問題。 (NEO-29664)
* 針對當執行包含標題的 SOAP 呼叫時，修正異動訊息可能維持在&#x200B;**等待中**&#x200B;狀態的問題。 (NEO-28737)
* 修正使用 Teradata FDA 連接器時發生的問題：所有臨時表格都只建立在叢集的一個節點上，這最終會佔用整個多工緩衝空間並導致 Teradata 當機。 現在會在許多節點上產生臨時表格。 (NEO-28230)
* 修正了使用 Web 應用程式時，追蹤標記在 **nms:trackingURL** 綱要中產生錯誤主鍵的問題。 (NEO-27931)
* 與 ODBC 3.x 的相容性已增強，以確保錯誤訊息的準確性。
* 修正當電子郵件傳送中使用自訂內容範本時，可能導致主控台當機的問題。 (NEO-31547)
* 修正了因連線速度緩慢或大規模回應而導致 Tomcat 無法傳送有效回應的問題。
* 修正從 PostgreSQL 資料庫讀取 UUID 時可能發生的問題。
* 修正搜尋連結至優惠方案的主張資料時，可能導致效能問題的問題。 (NEO-27554)
* 修正了在啟動 IMS 服務但未回應時，導致 Web 程式未回應的問題。
* 修正由於傳送個人化失敗的特定加入機制，您無法傳送包含一組校樣的傳送的問題。 (NEO-14391)
* 修正了當查詢和擴充活動以傳送表格為目標時，無法連同警報活動傳送警報的問題。 (NEO-25157)

## ![](assets/do-not-localize/red_2.png) 發行版本 21.1.2 - 版本編號 9282 {#release-21-1-2-build-9282}

_2021年 4 月 15 日_

* 密碼管理已經過改善，而可最佳化安全性。
* 修正可能導致 MTA 當機的問題。

## ![](assets/do-not-localize/red_2.png) 發行版本 21.1.1 - 版本編號 9277 {#release-21-1-1-build-9277}

_2021 年 2 月 22 日_

**安全性增強功能**

* 控制台驗證機制已經改善，以最佳化安全性。 (NEO-26944)
* 修正了安全性問題，針對伺服器端請求偽造 (SSRF) 問題加強保護。(NEO-28532)

**相容性更新**

下列系統現在已支援 Campaign：

* 使用 Salesforce CRM 外部帳戶時，現在已支援 Salesforce API 的 49 版本。

**已棄用功能**

 **技術傳遞能力監控**&#x200B;報告現在已被取代。

瞭解更多[與已棄用和已移除的功能頁面相關的資訊](../../rn/using/deprecated-features.md)。

**功能改善**

**電子郵件回饋服務 (EFS)**&#x200B;是一種可擴展的服務，它直接從增強型 MTA 中擷取回饋，從而提高報告的準確性。這項功能會以私人測試版發佈，未來發佈的版本將逐步提供給所有客戶。

* 現在，您可擷取所有類別的回饋，以進行完整精確的報告。
* 已傳遞指標的計算現在以增強型 MTA 的即時回饋為依據，以改進精確度和反應度。
* EFS 可解決同步軟退回的延遲問題。

如需詳細資訊，請參閱[詳細文件](../../delivery/using/sending-with-enhanced-mta.md#efs)。
如果您有興趣參與此私人測試版，請填妥此[表單](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我們將會與您聯絡。

**其他變更**

* 透過使用壓縮功能，已改善大型追蹤記錄的傳輸速度。
* Workflow Heatmap 已經過改善，可避免在執行包含多個活動的工作流程時逾時。 (NEO-27423)。
* 即使優惠方案結束日期已過，卻仍可能顯示的問題已修正。 Campaign Classic 現在會考慮結束日期的整個時間標記，而非僅考慮日期。 (NEO-27590)
* Google+ 連結已從&#x200B;**社交網路共用連結**&#x200B;個人化區塊中移除。
* 修正上一版本中實施錯誤修正後的問題。 使用 SSL/TLS 連線時，在主機名稱上新增檢查，導致 SMS 傳遞失敗。 已針對大多數通訊協定停用主機名稱驗證，例如使用 proxy 的 POP3、SMS 和 HTTP，而 SMS 外部帳戶的憑證檢查已改進為使用三個值 (NEO-29581)。 [進一步了解](../../delivery/using/sms-protocol.md#skip-tls)

**修補程式**

* 修正 Tab、Enter 和 Escape 鍵盤快速鍵無法在新登入畫面上運作的問題。
* 已修正重新整理問題，此問題會導致儲存後，新建立的工作流程名稱被預設值取代 (NEO-26106)。
* 修正在執行工作流程時，使用&#x200B;**外部檔案**&#x200B;目標對應在&#x200B;**傳遞**&#x200B;活動之前作為&#x200B;**擴充**&#x200B;活動的一部分新增新欄位的問題：不需要的欄位已新增到&#x200B;**外部檔案**&#x200B;目標對應。 (NEO-27687)
* 修正在重新開啟先前建立和儲存的 Web 應用程式時，造成原始程式碼中某些字元變更的問題。 (NEO-27597)
* 修正升級至包含追蹤連結 (來自 Build 19.1.4 和 Campaign 20.2) 之新簽名機制的建置時可能發生的問題：當多個範本與事件相關聯時，升級可能會導致在傳送異動訊息時選擇錯誤的範本。 (NEO-28326)
* 修正 MTA 在未重新啟動時無法回應且無法處理傳遞的問題。 (NEO-27455)
* 修正 MSSQL 資料庫在日期時間輸入欄位的大量載入作業期間，與時間標記管理相關的問題。
* 修正使用 Redshift xtk 函式時的工作流程查詢問題。 SubDays、SubSeconds、SubMinutes 和 SubHours 現在接受兩種 Redshift 時間標記類型 (NEO-24962)。
* 修正嘗試預覽具有匿名存取權的報表時，顯示指令碼錯誤訊息的問題。 (NEO-27081)
* 修正執行傳遞分析時，可能會減少伺服器上記憶體使用量的問題。
* 修正嘗試執行特定複雜查詢時，會導致執行個體無法作業的問題。
* 修正可能無法執行&#x200B;**「同步 Twitter 頁面」**&#x200B;的技術工作流程問題。 (NEO-28634)
* 修正嘗試使用&#x200B;**推文 (twitter)**&#x200B;傳遞範本在 Twitter 上發佈時，可能會顯示與 decryptPassword 函式相關的錯誤訊息的問題。 (NEO-28216)
* 修正使用 **Javascript** 活動在工作流程中提出 HTTP 請求時發生的問題。 在主機名稱中定義連接埠號碼後，呼叫將失敗，並出現下列錯誤 (NEO-29146)：

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 針對具有目標資料個人化的新傳遞修正無法傳送的問題 (NEO-30323)。
* 修正行銷執行個體中，發生數次當機所導致的核心檔案問題。
* 修正導致&#x200B;**追蹤**&#x200B;工作流程因下列錯誤而失敗的問題 (NEO-25206)：

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 修正活動的&#x200B;**目標定位與工作流程**&#x200B;標籤中建立和儲存傳遞項時發生的問題：預覽會失敗，並出現下列錯誤 (NEO-29440)：

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 修正在行銷執行個體與 Adobe Campaign Standard 執行個體或 Campaign Classic 中間來源執行個體之間設定外部帳戶，以及使用「DisableFOH2=1」選項時發生的錯誤。 在外部帳戶中使用「DisableFOH2=1」選項時，連線未正確關閉，並會累積導致以下錯誤 (NEO-26258)：

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 修正伺服器與提供者之間發生連線問題時的 SMS 錯誤。 然後，MTA 子項會自動停用連線。 只要尚未啟動新子項，Adobe Campaign Classic 就不會嘗試連線至這個失敗連線。
