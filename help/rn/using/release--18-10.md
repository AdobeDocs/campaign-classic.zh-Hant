---
product: campaign
title: Campaign 18.10發行說明
description: Campaign 18.10發行說明
feature: Overview
role: User
level: Beginner
exl-id: 57996f77-4ac2-402a-95db-b75d4bea4eeb
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '2366'
ht-degree: 7%

---

# 第 18.10 發行版本{#release-18-10}

![](../../assets/v7-only.svg)

## 發行版本 18.10.6 - 版本編號 8985{#release-18-10-6-build-8985}

2019年7月12日

**功能改善**

* 現在，我們允許在匯入工作流程期間刪除在Microsoft Dynamics中建立的虛擬記錄。
* 修正了檔案收集器工作流程活動在拒絕存取檔案時可能會在回圈中記錄錯誤的問題。 (NEO-12085)
* 修正造成使用者活動與未結傳送指標的追蹤報表不一致的問題。 (NEO-11742)
* 改善使用內部帳戶時執行安全區域套件的權限。
* 修正了可能導致母體記錄檔發生錯誤的問題。 (NEO-8978)

## 發行版本 18.10.5 - 版本編號 8984{#release-18-10-5-build-8984}

2019年4月23日

**功能改善**

* 修正了在同時分析/傳送時（同時分析兩個傳送時），導致傳送分析失敗的SQL鎖死問題。 (NEO-13026)
* 移除「工作流程熱度圖」中的10,000筆記錄限制，以修正遺失的資料問題。 (NEO-12329)
* 修正在擴充工作流程活動中使用「從主要集保留所有其他資料」選項的問題。 (NEO-13291)

## 發行版本 18.10.4 - 版本編號 8983{#release-18-10-4-build-8983}

2019年4月15日

**功能改善**

* 修正交易式訊息追蹤指標的運算程式問題。 （NEO-12529、NEO-12581）
* 修正HTTPRequest API未等待所有回呼完成的問題。 (NEO-12628)
* 已在抵用券臨時表格中新增索引，以最佳化傳送。 (NEO-12437)
* 修正分析以日文(.JP)網域的收件者為目標的訊息時的問題。 (NEO-12246)
* 在Analytics整合中，現在允許擷取包含%字元的AAM區段資料。 (NEO-12025)
* 修正了使用HTTP2傳送推播通知時，發生Tomcat當機問題。 (NEO-12701)

## 發行版本 18.10.3 - 版本編號 8981{#release-18-10-3-build-8981}

2019年1月29日

>[!CAUTION]
>
>這棟建築已召回。 請 [升級至最新版本編號](../../production/using/build-upgrade.md)  或聯絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**功能改善**

* 修正s3檔案傳輸工作流程活動的問題。 (NEO-12473)
* 修正了「追蹤」工作流程可能失敗的問題。 (NEO-12520)
* 修正IMS登入的問題。
* 修正使用大型優惠方案ID時，交易式訊息中的預覽和內容核准問題。
* 修正中間來源補充（傳送計數器）工作流程的問題。
* 修正了資料庫結構更新導致NmsRecipient上新索引掉落的問題。
* 修正針對傳送的主要目標使用外部檔案中的已定義選項時，可能會發生主控台當機的問題。 (NEO-12349)
* 修正數次InMail當機。
* 修正使用更新資料工作流程活動來刪除FDATeradata資料庫中儲存的記錄時的問題。
* 修正密鑰管理中的不一致問題。
* 修正將欄位輸入為時，「擴充」活動的問題：xml=true, calculated=true
* 修正在行動應用程式上傳送推播通知時的字元逸出問題。
* 修正無法在中間來源外部帳戶中從FDA切換至SOAP同步方法的問題。

## 發行版本 18.10.2 - 版本編號 8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>這棟建築已召回。 請 [升級至最新版本編號](../../production/using/build-upgrade.md) 或聯絡人 [Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**功能改善**

* 修正在FDA上使用MySQL執行工作流程時的各種問題。 (NEO-11652)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正了在傳送中使用種子地址時，ID耗盡的問題。 (NEO-11842)
* 修正使用複雜工作流程時可能發生的用戶端凍結問題。 (NEO-11847)
* 修正搭配1:N連結使用值分佈時的顯示問題。 (NEO-11820)
* 修正「工作流程熱度圖」的Oracle錯誤。
* 修正在擴充活動中新增優惠方案主張時的正確問題。
* 修正SQL資料管理連線問題。
* 修正了若為負ID，會產生暫時工作流程表格名稱的問題。
* 修正了在「工作流程熱度圖」中計算工作流程持續時間的問題。


## 發行版本 18.10 - 版本編號 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>這棟建築已召回。 請 [升級至最新版本編號](../../production/using/build-upgrade.md) 或聯絡人 [Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**有哪些新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 推播通知改善<br /> </td> 
   <td> 已在Adobe Campaign中針對推播通知實作數項增強功能：<br /> 
    <ul> 
     <li> <p>在iOS中追蹤靜默通知 </p> </li> 
     <li> <p>在iOS中實作註冊呼叫的意見反應</p> </li> 
     <li> <p>改善iOS傳送準備速度</p> </li> 
    </ul> <p>現在起，受到Google停用GCM的影響，Android V2連接器僅能連接FCM伺服器。</p><p>如需詳細資訊，請參閱<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">詳細文件</a>以瞭解詳情。FCM的手動升級詳見本節 <a href="https://helpx.adobe.com/tw/campaign/kb/migrate-to-fcm.html">文章</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL資料管理活動<br /> </td> 
   <td> <p>已新增新的資料管理工作流程活動。 此 <strong>SQL資料管理</strong> 活動可讓您撰寫或複製貼上自己的SQL指令碼，以建立和填入工作表格（僅限FDA）。 </p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/sql-data-management.md">詳細文件</a>以瞭解詳情。</p></td> 
  </tr> 
  <tr> 
   <td> 監視工作流程<br /> </td> 
   <td> <p>透過新的Adobe Campaign工作流程熱度圖，平台管理員可快速以圖形化方式呈現所有同時進行的工作流程，借此監控執行個體的負載並據此規劃工作流程。</p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/heatmap.md">詳細文件</a>以瞭解詳情。</p> <p>8977之前（從組建8700開始）的組建版本，也可依需求提供工作流程熱度圖套件。 有關請求和安裝的詳細資訊，請參閱 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">本頁</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 修正了可能導致伺服器端請求偽造(SSRF)攻擊和拒絕服務(DoS)攻擊漏洞的安全問題。 (NEO-11453)
* 內容（追蹤重新導向、鏡像頁面、調查等） 現在由Campaign搭配X-Robots-Tag提供：無快取標題。 這防止了Internet搜索引擎對此內容進行索引。 (NEO-11101)
* 修正訂閱API(nms)中的XTK插入問題:subscription:取消訂閱和nms:subscription:訂閱)。
* 修正取消訂閱Web應用程式中的XTK插入問題。
* 移除某些SMS記錄檔中無法安全顯示的密碼。

**功能改善**

* 現在針對 Campaign Classic API 推出[專屬頁 面](https://experienceleague.adobe.com/developer/campaign-api/api/index.html)。如果您使用 jsapi.chm 檔案，請參考新的線上版本。
* 現在支援PostgreSQL 10、Debian 9和Teradata16.20。 請參閱「[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)」。
* 建立SFTP連線時，您現在可以使用Proxy驗證。 如需詳細資訊，請參閱 [詳細檔案](../../installation/using/file-res-management.md) (NEO-9868)
* 此 **日期計算公式** 使用直接郵件傳送範本建立單一傳送時，「傳送」屬性中現在可使用選項。 (NEO-9792)
* Cookie追蹤和網頁應用程式的網域名稱管理已得到改善。 如需詳細資訊，請參閱下方的「技術演變」一節。
* 在安全性和效能方面，已改善在傳送或登陸頁面中匯入Adobe Marketing Cloud共用資產的功能。
* 行動通道外部帳戶中有新的核取方塊，可在記錄檔中啟用詳細的SMPP追蹤，如此便能直接從Adobe Campaign介面存取輸出。
* 在broadlogs中，現在會區分每小時的連線數量上限和訊息數量上限。 當達到限制時，就可以知道吞吐量為何受到限制。 以前，這兩種情況都會套用相同的訊息（「符合配額」）。
* 現在，可以指定從池獲取連接時要執行的SQL指令碼。 此指令碼可用於設定預設架構。 此指令碼將在查詢段落後應用。 (NEO-11256)
* Campaign SDK不再儲存使用者ID以符合PII法規。 資料現在會以雜湊形式儲存。
* 匯入套件匯出XML檔案時，Campaign現在支援檔案中是否存在BOM，即使已明確宣告編碼亦然。

**技術演變**

客戶端和伺服器升級

>[!CAUTION]
>
>如果您的伺服器已更新為18.10，則必須使用18.10用戶端才能存取您的伺服器。 18.10客戶端將能夠連接到較舊的伺服器版本。

域名管理

Cookie追蹤和網頁應用程式的網域名稱管理已得到改善。

現在，預設支援所有雙字母的二級網域名稱（例如.aa.com）。 若是更複雜的網域名稱（例如.com.au等三字母的二級網域），您必須將其新增至 **cookieDomains** serverConf的選項（在重新導向標籤下）。 以下是範例：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增強功能

NmsRecipient上的索引已重新工作。 這應該能改善使用此表格的查詢的效能。 如果您已擴展了NmsRecipient，則可能希望驗證您沒有重複新索引的索引（以最大限度地減少資料庫伺服器上的空間使用）。 (NEO-8228)

在使用UTF-8歸類時的PostgreSql上，現在可以建立將優化「LIKE &#39;string%&#39;」（或「starts with」）操作的索引。 如果對同一列執行其他操作（例如按順序或聯接），則需要另一個標準索引。 在架構端，將在索引定義上新增indexOption=&quot;searchFromStart&quot;來完成此操作（將建立varchar_pattern_ops索引，而非標準btree索引）。 例如（在NmsRecipient上）:

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

NmsRtEvent和NmsEventHisto已新增新索引（在「已排程」欄），這應可改善對應表單的顯示時間(NEO-11738)。

這些索引更改可能導致執行升級後所需時間增加。

**修補程式**

* 修正無法將檔案從 **網頁下載** 工作流程活動。 (NEO-11105)
* 修正偶爾離開 **傳送指標和行銷活動屬性** 處於「失敗」狀態的工作流(NEO-10820)。
* 修正在工作流程中執行「清單」更新活動後，刪除所建立收件者清單的問題。 (NEO-11696)
* 修正在「促銷活動」日曆（日文執行個體）中，未將促銷活動提前一個月正確顯示的問題。 (NEO-11445)
* 修正傳送屬性的「Web Analytics」標籤無法顯示Analytics設定的問題。 (NEO-11619)
* 修正嘗試編輯和儲存nms:delivery輸入表單時顯示的錯誤。 (NEO-10973)
* 修正執行包含檔案傳輸活動的工作流程時發生的外部帳戶設定問題。 (NEO-11012)
* 修正使用zcat函式在「資料載入」活動中載入檔案時，傳回空行的問題。 (NEO-11273)
* 修正分析傳送期間產生重複之廣泛記錄的問題。 (NEO-11360)
* 修正在工作流程中執行擴充活動後，外部連結金鑰遺失而導致傳送失敗的問題。 (NEO-11537)
* 修正當安裝路徑包含特定的GB18030中文字元時，無法正確解除安裝或修復Adobe Campaign的問題。
* 修正將部分追蹤記錄連結至錯誤傳送的問題。 (NEO-11412)
* 修正傳送記錄中某些部分的擱置狀態可能比預期更長的問題。 (NEO-11336)
* 修正編輯查詢以新增抵用券至傳送時發生的錯誤。 (NEO-11037)
* 修正報表中，無論選取的是匯總運算子，圖表一律會計算值總和的問題。 (NEO-10913)
* 由於「request.scheme」函式已遭取代，因此已從JSAPI檔案中移除。 (NEO-10828)
* 修正某些具有特定時區設定的使用者無法登入Adobe Campaign的問題。 (NEO-10712)
* 修正使用Extended generic SMPP連接器設定行動通道外部帳戶時發生的問題：如果您為接收器指定了不同的參數，則發送器將錯誤地使用這些參數，而不是使用它自己的參數。
* 修正為壓力規則設定頻率時，排程傳送失敗的問題，因為傳送會在第一次仲裁後持續重新計算。 (NEO-10016)
* 修正了在應用程式池循環過程（在nlsrvmod.dll庫中）期間導致IIS Web伺服器崩潰的問題。 (NEO-10862)
* 修正無法搜尋 **設定檔與目標** 螢幕。 (NEO-8228)
* 修正了在存取「事件歷史記錄」資料夾時，若有大量記錄，可能會導致逾時錯誤的問題。 (NEO-11738)
* 修正可能導致LINE傳送收件者誤傳為「無法連線」的問題。 (NEO-10833)
* 修正執行工作流程查詢時，在Oracle上加上其他欄的問題。 (NEO-11615)
* 已增強功能，以確保連接池中的已關閉連接不會保留太長時間。 (NEO-11392)
* 修正使用目標工作流程活動(查詢、資料載入(RDBMS)等)時的問題 透過FDA連線至包含UTF8字元的外部Oracle表（在表格名稱、欄位名稱等中） 並且還包含一個主鍵約束，該主鍵約束具有系統生成的預設約束名。 (NEO-10714)
* 修正無法刪除傳遞HTML內容的問題。 (NEO-11327)
* 修正了執行促銷活動後，直接郵件中XML和CSV檔案的預覽問題。 (NEO-11290)
* 修正排序擴充工作流程活動中資料的問題。 (NEO-11394)
* 修正排序自訂報表中資料的問題。 (NEO-10896)
* 修正搭配Teradata使用useVault設定時導致錯誤的問題。 (NEO-11399)
* 修正刪除多個查詢行時，造成Adobe Campaign用戶端主控台當機的問題。 (NEO-10744)
* 修正傳送直接郵件時，在某些情況下無法套用壓力規則的問題。 (NEO-9004)
* 修正使用資料載入活動匯入資料類型為「time」的欄時發生的問題：即使移除時間分隔符號後，也會重設。 (NEO-10743)
* 修正編輯循環傳送時，無法從「傳送」屬性的「執行」資料夾清單中顯示「傳送」資料夾的問題。 (NEO-11094)
* 修正「檢視母體」視窗無法在工作流程中將超過200筆記錄顯示為查詢活動之結果目標的問題。 (NEO-11195)
* 修正Oracle中無法在選取超過1000個元素時執行DELETE查詢的問題。 (NEO-11171)
* 修正導致在Android推播通知傳送的其他參數中，將URL編碼為追蹤URL的問題。 (NEO-11468)
* 修正將參數設為「一天間隔」和「開啟」時，在「使用者」活動報表中發生的指令碼錯誤。 (NEO-11655)
* 修正透過已驗證的Web Proxy連線至中間來源伺服器或訊息中心時發生的問題。 (NEO-11309)
* 修正選取特定結構的元素後，儲存新傳送組合時發生的Oracle錯誤 **基於SQL視圖**. (NEO-11682)
* 修正了透過使用解壓縮選項的載入檔案活動處理包含.csv的zip檔案時，導致產生包含誤判的拒絕檔案的問題。
* xtkjoblog現在會由清除清除。
