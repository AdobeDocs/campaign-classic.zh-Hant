---
product: campaign
title: 最新版本
description: 最新的 Campaign Classic 發行說明
feature: 概覽
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 28083eb0271c8c148955fa33978479dc3683eaed
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 52%

---

# 最新發行版本{#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic 發行候選版本**&#x200B;的新功能、改善和修正。

>[!NOTE]
>
>Campaign **一般可用性 (GA) 版本**&#x200B;包括：[[!DNL Gold Standard] 11 版本](../../rn/using/gold-standard.md#gs-11)和[Campaign 20.2.5 版本](../../rn/using/release--20-2.md)。

## ![](assets/do-not-localize/blue_2.png) 發行版本 21.1.3 - 建置 9330 {#release-21-1-3-build-9330}

_2021年6月5日_

**新增功能？**

<table>
<thead>
<tr>
<th><strong>與AdobeJourney Orchestration整合</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Journey Orchestration與Adobe Campaign Classic的整合現已正式推出。 它可讓Journey Orchestration使用Adobe Campaign Classic交易訊息功能來傳送電子郵件、推播通知和簡訊。</p>
<p>Journey Orchestration與Campaign Classic例項之間的連線是在布建時由Adobe設定。</p>
<p>如需詳細資訊，請參閱<a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html">Journey Orchestration檔案</a>。 本<a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html">節</a>中提供了逐步使用案例</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>LINE頻道增強功能</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>LINE頻道已新增下列改良功能：
</p>
<ul> 
<li><p>支援LINE視訊訊息類型</p></li>
<li><p>支援LINE合作夥伴註冊API</p></li>
<li><p>支援在出現LINE伺服器端錯誤或網路逾時時發送消息的重試</p></li>
</ul>
<p>如需詳細資訊，請參閱<a href="../../delivery/using/line-channel.md">詳細文件</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA連接器</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您現在可以將Adobe Campaign Classic執行個體連線至Vertica外部資料庫。 此連線透過新的外部帳戶進行管理。</p>
<p>如需詳細資訊，請參閱<a href="../../installation/using/configure-fda-vertica.md">詳細文件</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA連接器</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>您現在可以將Adobe Campaign Classic執行個體連線至Google Big Query外部資料庫。 此連線透過新的外部帳戶進行管理。
</p>
<p>如需詳細資訊，請參閱<a href="../../installation/using/configure-fda-google-big-query.md">詳細文件</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增強功能**

* 傳回完整資料庫連線詳細資訊的&#x200B;**xtk:session#GetCnxInfo** API方法現在僅限管理員使用者存取。 (NEO-27779)
* 在CRM相關的JavaScript檔案中，已棄用的decryptString函式已取代為decryptPassword。
* 已改善追蹤簽章功能，以在第三方工具（電子郵件用戶端、網際網路瀏覽器、安全連結安全工具）修改追蹤連結時，降低追蹤重新導向錯誤的風險。
* 修正了當包含大寫字元時，追蹤的URL無法運作的問題。 追蹤的URL簽署機制現在區分大小寫。 (NEO-28414)

**相容性更新**

下列系統現在已支援 Campaign：
* Google Big Query FDA連接器
* Vertica FDA連接器
* PostgreSQL 13

瞭解更多與[ Campaign 相容性矩陣相關的資訊](../../rn/using/compatibility-matrix.md)。

**棄用的功能**

* 自Campaign第21.1發行版本開始，已棄用Adobe Analytics Data Connector。 如果您使用此連接器，則需使用新連接器Adobe Analytics連接器，據以調整實施。
如需詳細資訊，請參閱[詳細文件](../../platform/using/adobe-analytics-connector.md)。
* 不再支援Debian 8。
* 在20.3中淘汰OracleCRM後，相關外部帳戶已從介面中移除。

瞭解更多[與已棄用和已移除的功能頁面相關的資訊](../../rn/using/deprecated-features.md)。

**功能改善**

* 儲存工作流程時已新增額外檢查，以確定活動名稱是唯一的，且轉變後一律會有活動。
* **帳單（帳單）**&#x200B;技術工作流程現在包含原本由&#x200B;**活動帳單設定檔數**(billingActiveContactCount)工作流程執行的任務，此工作流程已移除。 工作流程每月傳送的電子郵件報表現在會提供執行個體上作用中設定檔數目的資訊。 [顯示全文](../../workflow/using/about-technical-workflows.md)。
* 已新增新的&#x200B;**_keyOnMData**&#x200B;屬性，以便能夠對備忘錄資料使用鍵操作。

**其他變更**

* 適用於Windows的openssl協力廠商已更新至1.1.1h版。
* 在Debian套件說明中，nlserver已變更為Adobe Campaign Classic伺服器。

**修補程式**

* 修正在編輯工作階段逾時，在使用者維持登入的特定時間長度後（即使在設定時間後）登出使用者時的問題。
* 修正傳遞顯示為唯讀，但仍可在傳遞屬性中編輯的問題。
* 修正設計Web應用程式時，造成編輯工具列消失的錯誤。
* 修正新增連結至電子郵件時，顯示包含Adobe Campaign Classic標題之電子郵件文字版本的錯誤。 (NEO-29211
* 使用FDA over HTTP連線時，**中間來源（傳送記錄檔）**(defaultMidSourcingLog)工作流程卡在&#x200B;**NmsMidSourcing_LogsPeriodHour**&#x200B;選項所設定的時間範圍內。 這會防止記錄以此設定的時間範圍之後發生的資料更新。 (NEO-30833)
* 修正了執行訊息中心同步工作流程後發生的問題。 每次將傳遞對象資料夾移至自訂資料夾時，工作流程都會將傳遞移回一般&#x200B;**交易式訊息歷史記錄**&#x200B;資料夾。 (NEO-27445)
* 修正了嘗試顯示&#x200B;**廣播統計資料**、**追蹤指標**&#x200B;和&#x200B;**共用活動統計資料**&#x200B;報告時顯示錯誤訊息的問題。
* **Oracle隨選**&#x200B;工作流程活動已在OracleCRM連接器淘汰後從介面中移除。
* 修正了在每日重新啟動工作流程伺服器(wfserver)模組後，停止執行處理工作流程的問題。 (NEO-30047)
* 修正了無法更新MX管理檔案的問題，這可能對IP信譽造成負面影響。 (NEO-29897)
* 修正了在收到SOAP呼叫時導致Web程式當機的問題。 (NEO-28796)(NEO-29600)
* 修正導致SAP HANAFDA索引建立失敗的問題。 (NEO-29664)
* 修正了執行包含標題的SOAP呼叫時，交易式訊息可能維持在&#x200B;**Waiting**&#x200B;狀態的問題。 (NEO-28737)
* 修正使用TeradataFDA連接器時發生的問題：所有臨時表都只建立在群集的一個節點上，這最終會佔用整個捲軸空間並導致Teradata崩潰。 現在會在許多節點上產生臨時表格。 (NEO-28230)
* 修正了使用Web應用程式時，追蹤標籤在&#x200B;**nms:trackingURL**&#x200B;架構中產生錯誤主鍵的問題。 (NEO-27931)
* 與ODBC 3.x的相容性已增強，以確保錯誤訊息的準確性。
* 修正當電子郵件傳送中使用自訂內容範本時，可能導致主控台當機的問題。 (NEO-31547)
* 修正了因連線速度緩慢或回應大而導致Tomcat無法傳送有效回應的問題。
* 修正從PostgreSQL資料庫讀取UUID時可能發生的問題。
* 修正搜尋連結至選件的主張資料時，可能導致效能問題的問題。 (NEO-27554)
* 修正了在啟動IMS服務但未回應時，導致Web程式未回應的問題。
* 修正由於傳送個人化失敗的特定加入機制，您無法傳送包含一組校樣的傳送的問題。 (NEO-14391)
* 修正了當查詢和擴充活動以傳送表格為目標時，無法連同警報活動傳送警報的問題。 (NEO-25157)

## ![](assets/do-not-localize/red_2.png) 發行版本 21.1.2 - 建置 9282 {#release-21-1-2-build-9282}

_2021年 4 月 15 日_

* 密碼管理已經過改善，而可最佳化安全性。
* 修正可能導致 MTA 當機的問題。

## ![](assets/do-not-localize/red_2.png) 發行版本 21.1.1 - 版本 9277 {#release-21-1-1-build-9277}

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
