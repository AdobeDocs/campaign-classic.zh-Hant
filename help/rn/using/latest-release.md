---
title: 最新版本
description: 最新版本
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2bd946fc0e5b206280a7946e0cbc6fa6d1be90f2
workflow-type: tm+mt
source-wordcount: '2161'
ht-degree: 76%

---


# 最新版本{#latest-release}

![](assets/do-not-localize/cp-icon.png) **新的控制面板 6月 版本**，包含作用中設定檔監控、子網域傳遞送能力稽核及 GPG 金鑰管理。[進一步瞭解](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/release-notes.html)。

## ![](assets/do-not-localize/blue_2.png) 版本 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_2020年9月11日_

* 修正由於傳送部件上單一錯誤功能導致記憶體過載，導致傳送準備被封鎖的回歸。 (NEO-27346)
* 修正在重新發佈Web應用程式之前，關閉Apache和Web伺服器的錯誤升級問題。 (NEO-27155)
* 修正HTML範本管理上的回歸，導致追蹤URL因標籤誤譯而變得可見。 (NEO-25909)
* 修正資料庫清除工作流程因非托管資料來源而可能失敗的問題。 (NEO-23160、NEO-23364)
* 清除工作流程現在會依100批次清除過期清單，而非逐一清除。
* 修正無法修改外部帳戶內部名稱的回歸。 (NEO-27323)
* 修正錯誤升級期間的回歸，導致nlserver（錯誤記錄）啟動錯誤。
* 已改善共用記憶體的更新管理。 20.2中所需的其他步驟不再需要。

## ![](assets/do-not-localize/orange_2.png) 版本 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_2020年7月22日_

* 修正在停用簽名功能時無法運作追蹤的問題。 (NEO-26411)
* 修正造成個人化網域中未簽署的連結在允許時遭到封鎖的問題。 (NEO-25210)
* 修正使用某些舊版Outlook時，無法開啟／按一下追蹤URL的問題。 (NEO-25688)
* 修正導致在電子郵件傳送中錯誤定義鏡像頁面URL（因為ASCII字元控制不當）的問題。 (NEO-26084)
* 修正反網路釣魚服務中編碼URL管理的問題。 (NEO-25283)
* 修正在個人化參數（具有井字型大小的錨記）中使用片段追蹤URL無法運作的問題。 (NEO-25774)
* 修正使用特定自訂追蹤公式時的追蹤問題。 (NEO-25277)修正追蹤「通知點按」無法運作的問題（iOS和Android推播通知）。 (NEO-25965)
* 修正影響工作流程中計算欄位的回歸，導致工作流程失敗。 (NEO-25194)
* 修正無法即時建立網頁追蹤URL的回歸。 (NEO-20999)
* 已修正現成可用的傳送報表回歸問題，在匯出為PDF時，這些報表會出現截斷。 (NEO-25757)
* 修正部署精靈中的當機問題。
* 修正「選件」通知工作流程在設定檔後無法正常運作的問題。
* iOS HTTP2連接器已改善（協力廠商更新和錯誤管理）。 (NEO-25904、NEO-25903)
* catalina.properties中的jarToSkip清單已更新，以刪除對不再使用的jar檔案的引用（iOS通知）。
* 修正了在postupgrade後封鎖傳送準備的問題。
* 在切換至新的序 [列ID機制後](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)，所有更新收件者表格的Web應用程式都會在設定檔期間重新發佈。
* 已修正傳送內容中的潛在XSS弱點。 (NEO-17987、NEO-26073)

## ![](assets/do-not-localize/orange_2.png) 版本 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_2020 年 6 月 8 日_

**新增了哪些功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>支援表情符號</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>在 Campaign 設計訊息時，您現在可以使用專屬按鈕，輕鬆將表情符號插入訊息本文。您也可以在電子郵件主旨列新增表情符號。您可以在介面自訂可用的表情符號清單。</p>
    <p>如需新增表情符號的詳細資訊，請參閱<a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">相關的文件</a>，以瞭解詳情。前往<a href="../../delivery/using/customizing-emoticon-list.md">此章節</a>，瞭解如何自訂表情符號清單。 </p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA 連接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您現在可以將 Campaign 執行個體連線至 Azure Synapse 外部資料庫。此連線透過新的外部帳戶進行管理。</p>
    <p>Azure Synapse 僅適用於混合式和內部部署環境。如需詳細資訊，請參閱<a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">相關的文件</a>，以瞭解詳情。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>泰國及巴西隱私權法</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>泰國的個人資料保護法 (PDPA) 是新的隱私權法令，該法協調泰國的資料保護要求並以現代化方式加以規範。 </p>
   <p>巴西的Lei Geral de Proteção de Dados(LGPD)將於2021年初生效，適用於巴西所有收集或處理個人資料的公司。</p>
   <p>這些法令及規範適用於所持有資料的主體居住於這些國家的 Adobe Campaign 客戶。除了 Campaign 已提供的隱私權功能 (包括許可管理、資料保留設定及使用者角色) 外，我們還將利用此機會加入其他功能，以協助您做好迎接 PDPA 及 LGPD 的準備：</p>
   <ul> 
     <li><p>近用權與刪除全：我們利用了專為 GDPR 和 CCPA 所新增的功能。<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">顯示全文</a></p></li> 
     <li> <p>使用 Campaign 介面或API 建立隱私權要求時，您現在可以選取<strong>法規類型</strong>：PDPA、LGPD、GDPR、CCPA。<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">顯示全文</a>。</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 追蹤電子郵件中的連結已提高安全性，並對所有客戶已是預設功能。另外還提供增強的安全性功能，您可以透過連絡客戶服務來啟用此功能。有關非托管客戶啟用此功能的詳細資訊和步驟，請參閱 [「安全性與隱私權」檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。(NEO-24232)

* 為了最佳化安全性，用於產生檔案名稱的 MD5 雜湊演算法已增強 sha256，以利公開檔案上傳。(NEO-17044)

* 為了增強防範 XSS 攻擊的安全性，執行鏡像頁面時將禁用客戶端指令碼。(NEO-17987)

* 修正&#x200B;**隱私權要求清除**&#x200B;技術工作流程無法刪除調解資料的問題。(NEO-25168、NEO-21004)

* 修正&#x200B;**檔案傳輸**&#x200B;活動使 SFTP 金鑰驗證無法在 Debian 9 運作的問題。(NEO-23183)

**相容性增強功能**

下列系統現在已支援 Campaign：
* 作業系統： Debian 10
* RDBMS：Oracle 18c 及 Oracle 19c
* FDA：Azure Synapse Analytics

進一步瞭解[ Campaign 相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)。

**功能改善**

* 改善交易式傳訊功能，以提供更佳的使用者體驗。您現在可以取消發佈交易式傳訊範本，該範本將從執行實例刪除。[進一步瞭解](../../message-center/using/template-unpublication.md)。

* 提供新的選項，用來設定傳送包含影像或附件之電子郵件時的限制。這些護欄措施可以避免效能問題，對於交易式傳訊特別有用。[顯示全文](../../installation/using/configuring-campaign-options.md#delivery)

* 新的&#x200B;**在資料庫準備傳遞組件**&#x200B;選項，允許直接在資料庫執行傳遞準備，大幅加快分析作業。此選項僅適用於特定配置。[進一步瞭解](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)。(NEO-23886)

* 已改善 Microsoft Dynamics 的 [CRM Connector 活動](../../workflow/using/crm-connector.md) 效能。(NEO-13303、NEO-12710)

* 已增加共用記憶體版本。

   >[!WARNING]
   >
   >此項功能改善需要於執行升級後，進行額外的步驟操作。請參閱下面的&#x200B;**技術演變**&#x200B;一節。

* 加強清理工作流程。現在清理工作流程，也將自動刪除所有已刪除工作流程的孤立工作台。[進一步瞭解](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)。

* 使用 iOS HTTP2連接器的 iOS 行動應用程式憑證，現在將於傳送推播通知前驗證，因此可以避免傳遞因憑證過期而失敗。

* 改善了 HTTP 代理連線的管理機制。[進一步瞭解](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)。

**其他變更**

* 舊版 SMS 連接器現已棄用。請參閱 [已棄用的功能頁面](../../rn/using/deprecated-features.md)。

* 您無法再使用自己的 Litmus 帳戶來佈建及使用 Adobe Campaign 的收件匣轉譯。[進一步瞭解](../../delivery/using/inbox-rendering.md)。

* 為了更好地區分檢視和資料夾，檢視名稱的顏色已從深藍色更改為深青綠色。[顯示全文](../../platform/using/access-management.md#about-views)

* Campaign Classic 現在可以連線至英國、印度和加拿大地區代管的 Microsoft Dynamics CRM 帳戶。此功能適用於 Office 365 和內部部署 (Dynamics 2015) 的部署類型。

* Campaign 現在將執行TLS驗證，以檢查伺服器主機名稱是否符合所提供憑證的主機名稱。

* 「傳遞與追蹤」統計資料表格現在將針對 SMS 通道每次傳遞顯示一個項目，而非每名傳傳收件者顯示一個項目。

* 記錄檔新增了錯誤訊息，以利在下載的檔案大於磁碟空間時警告使用者。

* 下列功能現在可以供 Snowflake 連接器使用：MonthsAgo、DaysAgoInt、ToDateTime、YearsAgo。

**技術演變**

新的組建版本更新了共用記憶體，此更新需要進行額外的步驟。做為 Campaign 管理員，您需要移除記憶體區段。這些步驟為必要操作，因為舊的區段使 nlserver/nlsrvmod 無法成功啟動。

如果是 Windows 系統，需要重新啟動系統。

如果是 Debian/CentOs，則需要刪除共用記憶體。以下是步驟：

升級前，您需要遵循下列步驟操作：

1. 停止 apache2 (CentOS 上的 http2) 服務 (如果服務正在執行)。
1. 如果 nlserver 服務正在運行，停止運行 nlserver (舊組建版本則是 nlserver6) 服務。

升級後：

1. 如果版本早於當前版本，請使用 **ipcrm** 命令刪除共用記憶體。
1. 如果 nlserver 服務先前曾運行，請啟動該服務。
1. 啟動 apache2 服務 (如果先前正在運行)。

以下是 Debian 的命令列：

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

[本頁面](../../configuration/using/additional-parameters.md#redirection-server-configuration)提供 Linux 的示範。

**修補程式**

* 修正了清理工作流程記錄檔的次要迴歸。
* 修正了剖析 WSDL 檔案時，工作流程&#x200B;**載入 (SOAP)** 活動出現的問題。
* 修正使用&#x200B;**調查**&#x200B;活動升級許多工作流程，以有效處理大量工作流程時造成的錯誤 。
* 修正了處理來自 Enhanced MTA 的郵件中訊息時出現的間歇性連線問題。(NEO-20380)
* 修正在 HTML 以100%寬度顯示影像時，無法正確顯示熱門點擊百分比的問題。(NEO-23203)
* 修正無法將傳遞的條件式內容完全顯示於熱門點擊報表的問題。(NEO-18729)
* 修正繼續工作流程以傳送循環傳遞時，跳過目標核准步驟的問題。(NEO-18166)
* 修正了修正工作流程的錯誤後，**重新開始訊息準備**&#x200B;按鈕無法恢復傳遞的問題。(NEO-13488)
* 修正了漸進階段期間，目標包含日文電子郵件格式的收件者時，可能使傳遞在中間來源模式失敗的問題。(NEO-23846)
* 修正 Snowflake Connector 時區轉換的問題 (NEO-20105)
* 修正使用 FTP over SSL 的外部帳戶的問題。(NEO-20498)
* 修正無法在 Line 傳遞顯示影像的問題。(NEO-23207)
* 修正發佈優惠方案時出現錯誤的問題。(NEO-23312)
* 修正推播通知的問題，此問題使測試連線即使憑證已過期，卻仍可以在行動應用程式中運作。(NEO-22991)
* 修正了在高頻率傳送時，可能影響推播通知的問題。(NEO-20516)
* 修正了即使追蹤記錄未包含重複項，追蹤資料仍包含重複項的問題。(NEO-20040)
* 修正了追蹤伺服器通訊失敗經修正後，傳送重複的交易式電子郵件的問題。(NEO-23640)
* 修正從追蹤URL重新導向時刪除編碼參數值（對日文字元的影響）的問題。 (NEO-25637)
* 修正了比較浮點數字時，查詢無法運作的問題。(NEO-23243)
* 修正了重新啟動工作流程後，**修改者**&#x200B;欄位的內容無法顯示的問題。(NEO-23035)
* 修正從第二個容器下載記錄檔時，追蹤技術工作流程失敗的問題。(NEO-23159)
* 修正執行&#x200B;**擴充**&#x200B;活動時，工作流程可能失敗的問題。(NEO-17338)
* 已在&#x200B;**重複資料**&#x200B;刪除工作流程活動的&#x200B;**Doubles to keep** 欄位新增檢查機制，以防止輸入空值或負值。
* 已從循環行銷活動移除&#x200B;**排程器精靈**，以避免提及小時和分鐘。移除後，僅納入日期單位。
* 修正了透過&#x200B;**指令碼**&#x200B;工作流程活動的&#x200B;**依指令碼計算**&#x200B;選項建立傳遞時，其他儲存欄位的問題。(NEO-20609)
* 修正了無法在資料庫清理工作刪除 Ghost 工作流程的問題。
* 修正了造成&#x200B;**帳單 (作用中設定檔)** 技術工作流程失敗的問題。(NEO-19777)
* 修正使用ACS連接器功能時，無法連線至Campaign Standard例項（FOH/FOH2連線管理錯誤）的回歸問題。 (NEO-23433)
* 修正了無法在 Hadoop 表單擁有多欄位的主要金鑰建立綱要擴展的問題。(NEO-17390)
* 修正了&#x200B;**載入 (SOAP)**&#x200B;活動中，無法從 URL 載入 WSDL 檔案的問題。(NEO-16924)
* 修正了當多個作用中工作流程伺服器負載平衡時，無法透過主控台執行&#x200B;**無條件停止**&#x200B;的問題。(NEO-19556)
* 修正了造成清理工作流程當機的迴歸。
* 修正了在執行實例發佈範本時可能發生的問題。
* 修正了 collectPrivacyRequests 技術工作流程無法執行的問題。(NEO-20513、NEO-25169)
* 修正了更新至 9080 組建版本後，嘗試連線至 Audience Manager 時可能發生的問題。(NEO-20511、NEO-25167)
* 修正了匯出 PDF 或 XLS 格式報表時可能發生的問題。(NEO-20982、NEO-23493、NEO-23348)
* 修正了傳送傳遞後，傳遞清單可能顯示傳送兩次的問題。
* 修正了傳遞準備問題，路由設定設為透過中間來源傳送傳遞時，可能會發生此問題。
* 修正了按下在 Line 訊息內的 Web 應用程式連結時，可能顯示錯誤訊息的問題。
* 修正了執行清理工作流程後，刪除了&#x200B;**增量查詢**&#x200B;活動歷史記錄的問題。
* 修正了建立中間來源外部帳戶時，NmsMidSourcing_LastBroadLog_&lt;InternalName> 選項遺失的問題.
* 修正資料庫連線上的回歸問題，造成Web伺服器因資料庫編碼問題而持續重新啟動。 這可能導致過度消費。 (NEO-23264)
