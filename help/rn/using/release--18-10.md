---
solution: Campaign Classic
product: campaign
title: Campaign 18.10發行說明
description: Campaign 18.10的發行說明
feature: 概覽
role: Business Practitioner
level: Beginner
exl-id: 57996f77-4ac2-402a-95db-b75d4bea4eeb
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '2372'
ht-degree: 7%

---

# 18.10 發行版本{#release-18-10}

## 發行版本 18.10.6 - Build 8985{#release-18-10-6-build-8985}

2019年7月12日

**功能改善**

* 現在，我們允許在匯入工作流程期間刪除在Microsoft Dynamics中建立的虛擬記錄。
* 修正「檔案收集器」工作流程活動在檔案存取遭拒時，可能會在回圈記錄錯誤的問題。 (NEO-12085)
* 修正造成使用者活動與未結傳送指標的追蹤報表不一致的問題。 (NEO-11742)
* 改進使用內部帳戶時執行安全區套件的權限。
* 修正可能導致像片記錄檔錯誤的問題。 (NEO-8978)

## 發行版本 18.10.5 - Build 8984{#release-18-10-5-build-8984}

2019年4月23日

**功能改善**

* 修正在同時分析／傳送（同時分析兩個傳送）時，導致傳送分析失敗的SQL死鎖問題。 (NEO-13026)
* 已移除「工作流程熱圖」中的10,000個記錄限制，以修正遺失的資料問題。 (NEO-12329)
* 修正在擴充工作流程活動中使用「保留主集的所有其他資料」選項的問題。 (NEO-13291)

## 發行版本 18.10.4 - Build 8983{#release-18-10-4-build-8983}

2019年4月15日

**功能改善**

* 修正交易訊息追蹤指標的計算程式問題。 （NEO-12529、NEO-12581）
* 修正HTTPRequest API未等待所有回呼完成的問題。 (NEO-12628)
* 已在抵用券臨時表格中新增索引，以最佳化傳送。 (NEO-12437)
* 修正分析日文(.JP)網域的目標收件者訊息時的問題。 (NEO-12246)
* 在Analytics整合中，現在允許擷AAM取含有%字元的區段資料。 (NEO-12025)
* 修正使用HTTP2傳送推播通知時的Tomcat當機問題。 (NEO-12701)

## 發行版本 18.10.3 - Build 8981{#release-18-10-3-build-8981}

2019年1月29日

>[!CAUTION]
>
>這個建築已經召回。 請[升級至最新版本](../../production/using/build-upgrade.md)或與[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)聯絡。

**功能改善**

* 修正s3檔案傳輸工作流程活動的問題。 (NEO-12473)
* 修正「追蹤」工作流程可能失敗的問題。 (NEO-12520)
* 修正IMS登入的問題。
* 修正使用大型選件ID時，「交易式」訊息中的預覽和內容核准問題。
* 修正中間採購（傳送計數器）工作流程的問題。
* 修正資料庫結構更新導致NmsRecipient上新索引遺失的問題。
* 修正當使用傳送之主要目標之外部檔案中的「定義」選項時，可能會發生的主控台當機問題。 (NEO-12349)
* 已修正數次InMail當機。
* 修正使用「更新」資料工作流程活動來刪除FDATeradata資料庫中儲存的記錄時的問題。
* 已修正密鑰管理中的不一致問題。
* 修正將欄位輸入為：xml=true和calculated=true
* 修正在行動應用程式上傳送推播通知時的字元逸出問題。
* 修正Mid-Sourcing外部帳戶無法從FDA切換至SOAP同步方法的問題。

## 發行版本 18.10.2 - Build 8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>這個建築已經召回。 請[升級至最新版本](../../production/using/build-upgrade.md)或與[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)聯絡。

**功能改善**

* 已修正使用FDA上的MySQL執行工作流程時的各種問題。 (NEO-11652)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正傳送中使用種子位址時的ID耗盡問題。 (NEO-11842)
* 修正使用複雜工作流程時可能發生的用戶端凍結問題。 (NEO-11847)
* 修正使用1:N連結的值分佈時的顯示問題。 (NEO-11820)
* 修正Worflow Heatmap中的Oracle錯誤。
* 修正在擴充活動中新增選件提案時的正確問題。
* 修正SQL資料管理連線問題。
* 修正產生暫時工作流程表格名稱（若為負ID）的問題。
* 修正Workflow HeatMap中計算工作流持續時間的問題。


## 發行版本 18.10 - Build 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>這個建築已經召回。 請[升級至最新版本](../../production/using/build-upgrade.md)或與[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)聯絡。

**新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 推播通知改進<br /> </td> 
   <td> Adobe Campaign已針對推播通知實作多項增強功能：<br /> 
    <ul> 
     <li> <p>在iOS中追蹤無訊息通知 </p> </li> 
     <li> <p>在iOS中實作註冊呼叫的意見回應</p> </li> 
     <li> <p>改善iOS傳送準備速度</p> </li> 
    </ul> <p>Android V2連接器現在僅允許與FCM伺服器連接，這是Google GCM折舊的一部分。</p><p>如需詳細資訊，請參閱<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">相關的文件</a>，以瞭解詳情。本<a href="https://helpx.adobe.com/tw/campaign/kb/migrate-to-fcm.html">文章</a>中詳細說明了對FCM的手動升級。 </p> </td> 
  </tr> 
  <tr> 
   <td> SQL資料管理活動<br /> </td> 
   <td> <p>新增了資料管理工作流程活動。 <strong>SQL資料管理</strong>活動允許您編寫或複製貼上自己的SQL指令碼以建立和填充工作表（僅限FDA）。 </p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/sql-data-management.md">相關的文件</a>，以瞭解詳情。</p></td> 
  </tr> 
  <tr> 
   <td> 監視工作流程<br /> </td> 
   <td> <p>使用全新的Adobe Campaign工作流熱圖，平台管理員可快速以圖形化方式呈現所有併發工作流，以便監控實例的負載並據此規劃工作流。</p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/heatmap.md">相關的文件</a>，以瞭解詳情。</p> <p>Workflow HeatMap套件也可依需求在8977（從組建8700開始）之前建立。 有關請求和安裝它的詳細資訊，請參閱<a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">本頁</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 已修正可能導致伺服器端偽造要求(SSRF)攻擊和拒絕服務(DoS)攻擊弱點的安全性問題。 (NEO-11453)
* 內容（追蹤重新導向、鏡像頁面、調查等） 現在由Campaign搭配X-Robots-Tag提供：無快取標頭。 這可防止Internet搜尋引擎對此內容進行索引。 (NEO-11101)
* 修正訂閱API（nms:subscription:Unsubscribe和nms:subscribe:Subscribe）中的XTK植入問題。
* 已修正取消訂閱Web應用程式中的XTK植入問題。
* 已移除某些SMS記錄檔中無法安全顯示的密碼。

**功能改善**

* 現在針對 Campaign Classic API 推出[專屬頁 面](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。如果您使用 jsapi.chm 檔案，請參考新的線上版本。
* 現在支援PostgreSQL 10、Debian 9和Teradata16.20。 請參閱「[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)」。
* 建立SFTP連線時，您現在可以使用代理驗證。 有關詳細資訊，請參閱[詳細說明檔案](../../installation/using/file-res-management.md)(NEO-9868)
* 當使用直接郵件傳送模板建立單次傳送時，**日期計算公式**&#x200B;選項現在可用於傳送屬性。 (NEO-9792)
* Cookie追蹤和Web應用程式的網域名稱管理已改善。 如需詳細資訊，請參閱下方的「技術演變」一節。
* Adobe Marketing Cloud在交付或登陸頁面中的共用資產的導入在安全性和效能方面都得到改進。
* Mobile channel外部帳戶中有一個新的複選框，用於在日誌檔案中啟用詳細的SMPP跟蹤，使此輸出可直接從Adobe Campaign介面訪問。
* 在廣播中，現在可以區分每小時最大連接數和最大消息數。 當達到限制時，便可知道為什麼吞吐量受到限制。 以前，這兩種情況都會套用相同的訊息（「符合配額」）。
* 現在，您可以指定從池中獲取連接時要執行的SQL指令碼。 此指令碼可用於設定預設模式。 此指令碼將在查詢條帶化後應用。 (NEO-11256)
* 促銷活動SDK不再儲存使用者ID以符合我們的PII規定。 資料現在會儲存為雜湊。
* 匯入封裝匯出XML檔案時，Campaign現在支援檔案中存在BOM，即使已明確宣告編碼亦然。

**技術演變**

用戶端與伺服器升級

>[!CAUTION]
>
>如果您的伺服器已更新為18.10，則必須使用18.10用戶端才能存取您的伺服器。 18.10用戶端將可連接至舊版伺服器。

域名管理

Cookie追蹤和Web應用程式的網域名稱管理已改善。

現在，預設支援所有雙字母的二級網域名稱（例如。aa.com）。 對於更複雜的網域名稱（例如，三個字母的二級網域，如。com.au），您需要在serverConf的&#x200B;**cookieDomains**&#x200B;選項（在重新導向標籤下）中新增這些網域。 以下是範例：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增強功能

NmsRecipient上的索引已重新編寫。 這應會改善使用此表格的查詢的效能。 如果已擴展了NmsRecipient ，則可能需要驗證是否沒有與新索引重複的索引（以最大限度地減少資料庫伺服器上的空間使用）。 (NEO-8228)

在使用UTF-8歸類時的PostgreSql上，現在可以建立索引，以優化「LIKE &#39;string%&#39;」（或「starts with」）操作。 如果對同一列執行其他操作（例如按順序或聯接），則需要另一個標準索引。 在架構方面，這將通過在索引定義上添加indexOption=&quot;searchFromStart&quot;來完成（它將建立varchar_pattern_ops索引，而不是標準btree索引）。 例如（在NmsRecipient上）:

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

新索引已添加到NmsRtEvent和NmsEventHisto（在&quot;Scheduled&quot;列上），這應該改進相應表單(NEO-11738)上的顯示時間。

這些索引更改可能會增加執行升級後所需的時間。

**修補程式**

* 修正無法下載&#x200B;**Web download**&#x200B;工作流程活動中檔案的錯誤。 (NEO-11105)
* 修正偶爾會將&#x200B;**傳送指示符和促銷活動屬性**&#x200B;工作流程保留為「失敗」狀態的錯誤(NEO-10820)。
* 修正在工作流程中執行「清單更新」活動後，刪除所建立之收件者清單的問題。 (NEO-11696)
* 修正在「促銷活動」日曆（在日文例項上）中，提前一個月錯誤顯示促銷活動的問題。 (NEO-11445)
* 修正Analytics設定無法顯示在傳送屬性的「Web Analytics」標籤中的問題。 (NEO-11619)
* 修正嘗試編輯並儲存nms:delivery輸入表單時顯示的錯誤。 (NEO-10973)
* 修正執行包含檔案傳輸活動的工作流程時發生的外部帳戶設定問題。 (NEO-11012)
* 修正使用zcat函式在「資料載入」活動中載入檔案時傳回空白行的問題。 (NEO-11273)
* 修正在分析傳送期間產生重複廣泛記錄檔的問題。 (NEO-11360)
* 修正在工作流程中執行Enrichment活動後，由於遺失外來連結金鑰而導致傳送失敗的問題。 (NEO-11537)
* 修正當安裝路徑包含特定GB18030中文字元時，無法正確解除安裝或修復Adobe Campaign的問題。
* 已修正某些追蹤記錄連結至錯誤傳送的問題。 (NEO-11412)
* 修正可能導致傳送記錄的某些部分保留擱置狀態的時間比預期長的問題。 (NEO-11336)
* 修正編輯查詢以新增抵用券至傳送時發生的錯誤。 (NEO-11037)
* 修正報表中，無論選取哪個匯整運算子，圖表都會計算值總和的問題。 (NEO-10913)
* 當&quot;request.scheme&quot;函式已過時時，它已從JSAPI檔案中移除。 (NEO-10828)
* 修正某些具有特定時區組態的使用者無法登入Adobe Campaign的問題。 (NEO-10712)
* 修正使用Extended一般SMPP連接器設定行動頻道外部帳戶時發生的問題：如果您為接收器指定了不同的參數，則發射器會錯誤地使用這些參數而不是自己的參數。
* 修正在設定壓力規則的頻率時，排程的傳送會失敗的問題，因為傳送會在第一次仲裁後持續重新計算。 (NEO-10016)
* 修正在應用程式池回收程式（在nlsrvmod.dll程式庫中）期間，造成IIS網站伺服器當機的問題。 (NEO-10862)
* 修正無法在&#x200B;**描述檔和Target**&#x200B;畫面中搜尋收件者的問題。 (NEO-8228)
* 修正在存取「事件歷史記錄」檔案夾時，若記錄數量較多，可能導致逾時錯誤的問題。 (NEO-11738)
* 修正可能導致LINE傳送收件者錯誤地傳回為「無法存取」的問題。 (NEO-10833)
* 修正在Oracle上執行附加列的工作流程查詢時的問題。 (NEO-11615)
* 已對連接池進行了增強，以確保關閉的連接不會在連接池中保存太長時間。 (NEO-11392)
* 修正使用定位工作流程活動(查詢、資料載入(RDBMS)等)時的問題 透過FDA連線至包含UTF8字元的外部Oracle表（在表名、欄位名稱等） 其中也包含具有系統生成的預設約束名的主鍵約束。 (NEO-10714)
* 修正無法刪除傳送之HTML內容的問題。 (NEO-11327)
* 修正促銷活動執行後，直接郵件中XML和CSV檔案預覽的問題。 (NEO-11290)
* 修正在擴充工作流程活動中排序資料的問題。 (NEO-11394)
* 修正在自訂報表中排序資料的問題。 (NEO-10896)
* 修正使用useVault設定搭配Teradata時導致錯誤的問題。 (NEO-11399)
* 修正刪除多個查詢行時造成Adobe Campaign客戶端控制台當機的問題。 (NEO-10744)
* 修正傳送直接郵件時，在某些情況下無法套用壓力規則的問題。 (NEO-9004)
* 修正使用「資料載入」活動匯入資料類型為「時間」的欄時發生的問題：即使在移除後，時間分隔符也會重設。 (NEO-10743)
* 修正編輯循環傳送時，「傳送」資料夾無法從「傳送」屬性的「執行」資料夾清單中顯示的問題。 (NEO-11094)
* 修正「檢視人口族群」視窗無法將超過200個記錄顯示為工作流程中查詢活動結果目標的問題。 (NEO-11195)
* 修正Oracle中無法在選取超過1000個元素時執行DELETE查詢的問題。 (NEO-11171)
* 修正導致在Android推播通知傳送的其他參數中，將URL編碼為追蹤URL的問題。 (NEO-11468)
* 修正將參數設為「一天間隔」和「開啟」時，在「使用者活動」報表中發生的指令碼錯誤。 (NEO-11655)
* 修正透過已驗證的Web Proxy連線至中端採購伺服器或訊息中心時發生的問題。 (NEO-11309)
* 修正在根據SQL視圖&#x200B;**選擇特定方案**&#x200B;的元素後保存新傳送組合時發生的Oracle錯誤。 (NEO-11682)
* 修正當透過使用解壓縮選項的載入檔案活動處理包含。csv的zip檔案時，產生包含誤報的拒絕檔案的問題。
* xtkjoblog現在會被清除。
