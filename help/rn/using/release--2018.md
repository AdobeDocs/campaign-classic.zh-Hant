---
product: campaign
title: Campaign Classic2018版本
description: 深入了解Campaign Classic2018版本
source-git-commit: eb0e572f0bb6196a58a7dab4999df784d5c4851f
workflow-type: tm+mt
source-wordcount: '5414'
ht-degree: 7%

---

# 2018版本{#release-2018}

![](../../assets/v7-only.svg)

## 第 18.10 發行版本

### 發行版本 18.10.6 - 版本編號 8985{#release-18-10-6-build-8985}

2019年7月12日

**功能改善**

* 現在，我們允許在匯入工作流程期間刪除在Microsoft Dynamics中建立的虛擬記錄。
* 修正了檔案收集器工作流程活動在拒絕存取檔案時可能會在回圈中記錄錯誤的問題。 (NEO-12085)
* 修正造成使用者活動與未結傳送指標的追蹤報表不一致的問題。 (NEO-11742)
* 改善使用內部帳戶時執行安全區域套件的權限。
* 修正了可能導致母體記錄檔發生錯誤的問題。 (NEO-8978)

### 發行版本 18.10.5 - 版本編號 8984{#release-18-10-5-build-8984}

2019年4月23日

**功能改善**

* 修正了在同時分析/傳送時（同時分析兩個傳送時），導致傳送分析失敗的SQL鎖死問題。 (NEO-13026)
* 移除「工作流程熱度圖」中的10,000筆記錄限制，以修正遺失的資料問題。 (NEO-12329)
* 修正在擴充工作流程活動中使用「從主要集保留所有其他資料」選項的問題。 (NEO-13291)

### 發行版本 18.10.4 - 版本編號 8983{#release-18-10-4-build-8983}

2019年4月15日

**功能改善**

* 修正交易式訊息追蹤指標的運算程式問題。 （NEO-12529、NEO-12581）
* 修正HTTPRequest API未等待所有回呼完成的問題。 (NEO-12628)
* 已在抵用券臨時表格中新增索引，以最佳化傳送。 (NEO-12437)
* 修正分析以日文(.JP)網域的收件者為目標的訊息時的問題。 (NEO-12246)
* 在Analytics整合中，現在允許擷取包含%字元的AAM區段資料。 (NEO-12025)
* 修正了使用HTTP2傳送推播通知時，發生Tomcat當機問題。 (NEO-12701)

### 發行版本 18.10.3 - 版本編號 8981{#release-18-10-3-build-8981}

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

### 發行版本 18.10.2 - 版本編號 8978{#release-18-10-2-build-8978}

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


### 發行版本 18.10.1 - 版本編號 8977{#release-18-10-build-8977}

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

* 現在針對 Campaign Classic API 推出[專屬頁 面](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。如果您使用 jsapi.chm 檔案，請參考新的線上版本。
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

## 第 18.6 發行版本

### 發行版本 18.6.2 - 版本編號 8949{#release-18-6-3-build-8949}

2018年8月22日

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
   <td> 查詢區<br /> </td> 
   <td> <p>當多個Campaign使用者連線至相同的FDATeradata外部帳戶時，您現在可以傳遞每個使用者專屬的查詢範圍（索引鍵/值組）。 每次Campaign使用者在Teradata資料庫上執行查詢時，Adobe Campaign現在都能傳送與使用者相關聯的中繼資料。 這些資料包含在索引鍵和值清單中，然後可供Teradata管理員用於稽核或管理存取權限。</p><p>如需詳細資訊，請參閱<a href="../../installation/using/external-accounts.md">詳細文件</a>以瞭解詳情。</p> </td>
  </tr> 
 </tbody> 
</table>

**功能改善**

* 電子郵件封存記錄已增強，讓您更輕鬆更清楚地檢查哪些電子郵件已成功傳送或透過密件副本封存失敗。 (NEO-10675)
* 修正了導致在追蹤廣播中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正傳遞屬性遭錯誤覆寫的隨機問題。 (NEO-11015)
* 修正排序擴充活動結果時的語法錯誤。 (NEO-11394)
* 修正在 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-11382)
* 已更新Tomcat以防止漏洞利用。 (NEO-11503)
* 修正使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用 **[!UICONTROL Prepare the personalization data with a workflow]** 傳遞選項。 (NEO-11047)
* 修正了使用延伸連接器時無法傳送SMS的升級後問題。
* 改善套件匯入/匯出（介面中新增了記錄檔和地區）。
* 修正了在升級後記錄中，若 **[!UICONTROL Survey answers]** 工作流程活動未完全設定。

**技術演變**

查詢區

特定索引鍵（PROXYUSER或PROXYROLE）可用來將Teradata使用者或角色與促銷活動使用者建立關聯。 已新增使用此代理使用者/角色的新權限。 您需要將GRANTCONNECTTHROUGH訪問權限添加到資料庫帳戶(在Teradata外部帳戶中定義的帳戶)。

已在Teradata外部帳戶中新增索引標籤。 此 **[!UICONTROL Query banding]** 索引標籤包含下列選項：

* **[!UICONTROL Active]**:勾選此方塊以啟用功能。
* **[!UICONTROL Default]**:輸入預設的查詢段，如果用戶沒有關聯的查詢段，則將使用該段。 如果沒有定義預設的查詢段落，則沒有關聯的查詢段落的用戶將無法使用Teradata。
* **[!UICONTROL Users]**:為每個使用者指定查詢區段。 您可以視需要新增任意數量的索引鍵/值組。 例如：&#39;priority=1;workload=high;&#39;

如需查詢區隔的詳細資訊，請參閱下列文章：

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### 發行版本 18.6.1 - 版本編號 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>這棟建築已召回。 請 [升級至最新版本編號](../../production/using/build-upgrade.md) 或聯絡人 [技術支援](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> 安全性改善<br /> </td> 
   <td> 已新增一系列安全性改善項目至Campaign Classic。 以下列出改善項目和修正項目。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支援Windows Server 2016<br /> </td> 
   <td> Adobe Campaign現在與Windows Server 2016相容。 請參閱 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic相容性矩陣</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

decryptString

此 **decryptString** 函式已遭取代。 請參閱 [過時和移除的功能](deprecated-features.md) 文章。

若為新客戶，此函式現在僅用於解密登錄頁面中收件者的加密ID。 若要解密儲存在外部帳戶中的密碼，請使用新 **decryptPassword** 函式。

對於現有客戶，此函式的行為不會變更，但建議您使用 **decryptPassword** 而非 **decryptString**. 此 **XtkSecurity_Unsafe_DecryptString** 「相容性」選項是在升級後新增的，預設會啟用，讓您能繼續使用函式。 如果您想停用 **decryptString**，停用選項。

decryptPassword

此 **decryptPassword** 函式。 它可讓您解密儲存在外部帳戶中的密碼。 請參閱 [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 檔案以取得詳細資訊。

檔案API

若為新安裝，透過檔案API存取資料夾的限制為 **var**, **sftp** 和Adobe Campaign的臨時資料夾。

針對現有客戶，檔案API無法再存取 **conf** 資料夾。 此 **XtkSecurity_Disable_JSFileSandboxing** 「相容性」選項由後置升級添加，預設情況下激活，允許您繼續訪問其他資料夾。 如果您想限制 **var**, **sftp** 和Adobe Campaign的臨時資料夾，停用選項。

**修補程式**

* 修正可能影響SMS交易式訊息效能的問題。 (NEO-9812)

## 第 18.4 發行版本

### 發行版本 18.4.5 - 版本編號 8937{#release-18-4-5-build-8937}

2018年11月21日

**功能改善**

* 修正在FDA上使用MySQL執行工作流程時的各種問題。 (NEO-11652)
* 修正特定情況下，傳送母體的一部分仍處於待定狀態的問題。 (NEO-11336)
* 修正SMS自動回應的間歇性問題。 (NEO-11811)
* 修正了在傳送中使用種子地址時，ID耗盡的問題。 (NEO-11842)
* 修正在擴充工作流程活動中執行排序時的語法錯誤。 (NEO-11394)
* 修正了重新啟動IIS時，可能導致Web伺服器當機的問題。 (NEO-10862)
* 修正組建升級(FDA - SQL)後，追蹤工作流程可能失敗的問題。 (NEO-11635)
* 修正可能導致工作流程清單資料遺失的問題。 (NEO-11696)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正網頁追蹤無法用於&quot;com.au&quot;網域(NEO-4385)的問題。
* 修正使用複雜工作流程時可能發生的用戶端凍結問題。 (NEO-11847)
* 修正選取特定結構的元素後儲存新傳送時的Oracle錯誤(NEO-11682)。
* 修正查詢包含重音字元的欄位時的問題(FDA/Teradata)。 外部帳戶現在可讓您變更用於與Teradata驅動程式通訊的編碼。 (NEO-11818).
* 修正在推播通知中傳遞其他變數中的URL時，可能導致行動應用程式收到格式錯誤或資料不正確的追蹤問題。 （NEO-11468、NEO-11960）
* 修正將值分佈與1:N連結搭配使用時，造成顯示問題的問題。 (NEO-11820)
* 修正批量載入無法用於Teradata16的問題。
* 增加Teradata上時間戳記的緩衝區大小，以避免與15.10驅動程式發生捆綁問題。
* 改善了長名稱索引的管理，這可能造成升級後問題。
* 改善子程式死機處理(MTA)期間的共用記憶體可用時間。
* 修正Apache（追蹤）中的潛在鎖死。


### 發行版本 18.4.4 - 版本編號 8936{#release-18-4-4-build-8936}

2018年8月1日

**功能改善**

* 電子郵件封存記錄已增強，讓您更輕鬆更清楚地檢查哪些電子郵件已成功傳送或透過密件副本封存失敗。 (NEO-10675)
* 修正了導致在追蹤廣播中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用 **[!UICONTROL Prepare the personalization data with a workflow]** 傳遞選項。 （NEO-11047、NEO-11301）
* 修正傳遞屬性遭錯誤覆寫的隨機問題。 (NEO-11015)
* 修正在 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-11382)
* 修正在 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-10816)
* 修正了使用版本編號8935執行伺服器升級時的問題。
* 修正了在升級後記錄中，若 **[!UICONTROL Survey answers]** 工作流程活動未完全設定。
* FDATeradata:修正SQL表格中自動增加欄位和索引的問題。

### 發行版本 18.4.3 - 版本編號 8935{#release-18-4-3-build-8935}

2018年6月22日

**功能改善**

* 修正Microsoft Edge和Internet Explorer的追蹤編碼問題。 (NEO-11257)
* 修正LINE傳送中影像連結個人化的問題。 (NEO-11077)
* 修正ID序列產生機制無法正常運作的問題。 (NEO-11115)
* 修正使用具有整數類型調解金鑰的自訂命名空間時，隱私權(GDPR)要求無法運作的問題。 (NEO-11123)
* 修正使用 **[!UICONTROL Distribution of values]** 選項 **[!UICONTROL Query]** 工作流程活動。 (NEO-10958)
* 修正從行銷例項同步選件空間至互動例項的問題。 (NEO-11162)
* 改善升級後期間長名稱索引的管理

### 發行版本 18.4.2 - 版本編號 8932{#release-18-4-2-build-8932}

2018年5月22日

**功能改善**

* 修正Windows Server更新無法正常運作的問題。
* 修正 **[!UICONTROL Survey Result]** 活動。 報告顯示不正確。 (NEO-10816)
* 修正了使用退信郵件伺服器時，inMail程式可能發生的效能問題。 (NEO-10641)
* 修正了升級超過1000個結構時可能發生的資料庫升級問題。

### 發行版本 18.4.1 - 版本編號 8931{#release-18-4-build-8931}

2018年4月24日

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
   <td> 歐盟一般資料保護規範(GDPR)<br /> </td> 
   <td> <p>GDPR是歐盟(EU)的新隱私權法，協調2018年5月25日生效的資料保護要求並以現代化方式規範這些要求。 GDPR 適用於所持有資料的主體居住於歐盟的 Adobe Campaign 客戶。</p> <p>除了Adobe Campaign中已提供的隱私權功能（包括同意管理、資料保留設定和使用者角色）之外，我們也趁此次機會，以資料處理者的角色加入其他功能，以協助您做好準備，以便擔任資料控管單位，處理特定GDPR請求：</p> 
    <ul> 
     <li> <p>訪問權限：可讓資料主體接收資料控制者擷取的個人資料副本，可能包括儲存在Adobe Campaign中的資料。</p> </li> 
     <li> <p>刪除權限：為資料主體賦予權利，讓資料控制者清除其個人資料，可能包括儲存在Adobe Campaign中的資料。</p> </li> 
    </ul> 如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">詳細文件</a>以瞭解詳情。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的設定檔案<br /> </td> 
   <td> <p>Adobe Campaign現在提供作用中設定檔的清單，並透過專用的工作流程每月更新。</p> <p>如需詳細資訊，請參閱<a href="../../platform/using/about-profiles.md#active-profiles">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推播連接器增強功能<br /> </td> 
   <td> <p>已增強Android連接器，以支援更高的吞吐量。 </p> <p>如需詳細資訊，請參閱<a href="../../delivery/using/configuring-the-mobile-application.md">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 現在已停用外部實體的擴充，以防止未驗證使用者發生潛在攻擊。 (NEO-10173)
* 強化權限，以防止標準使用者變更執行個體設定參數，例如應用程式存取URL、LDAP設定等。 (NEO-10171)
* 修正了可能透過堆疊追蹤顯示敏感資訊的問題。 錯誤詳細資訊現在記錄在無法從外部網路存取的位置的後端。 (NEO-10176)
* 強化的權限，以防止標準使用者檢視管理員的已上傳檔案和/或已匯出套件。 (NEO-10170)

**功能改善**

* **LINE通道 — 架構增強**:與Adobe Campaign中的所有其他管道一樣，現在所有部署類型都支援LINE管道：托管、混合和內部部署。
* **序列自動生成**:已增強ID產生機制，以增加具有大量物件之Campaign執行個體的有效期限。 如需詳細資訊，請參閱 [技術檔案](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html).

**其他變更**

* 使用命令行導入包時可使用新模式，允許循環依賴項（對於大型包不建議使用）。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-8979)
* 改善Teradata中載入大量資料的效能，並修正無法顯示記錄中處理之資料的正確值的問題。 (NEO-10429)
* 從Audience Manager匯入對象現在可處理分割檔案。 以前，只有匯入SharedAudience技術工作流程匯入了區段的最後一個檔案。 (NEO-10156)
* 在Windows上，Campaign伺服器的預設安裝路徑已變更。 啟動64位元版本設定時，預設安裝路徑現在為： **C:\Program Files\Adobe\Adobe Campaign Classic v7** 而非 **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 已增強預設的MX規則，以包含更多網域並最佳化輸送量。
* 對部署精靈SOAP呼叫(xtk:serverOptions#SaveOptions)強制存取限制。
* weka.jar淘汰程式庫已移除，OpenSSL程式庫已更新，以最佳化安全性。
* 改善帳單技術工作流程以保護執行個體效能。
* 管理員設定或重設任何運算子密碼的功能已還原。 若要這麼做，請以滑鼠右鍵按一下運算子，選取 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 並設定操作員的新密碼。 建議操作員在首次重新連線時變更其密碼。 如需詳細資訊，請參閱[詳細文件](../../production/using/lost-password.md)以瞭解詳情。
* 為了支援Adobe Target中的新多租用戶功能，現在當設定與Target整合的選項和外部帳戶時，可以將新的「at_property」參數新增至URL。 可在Adobe Target中找到此參數使用的值，且將供Campaign在對Target執行呼叫時使用。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 您現在可以指定在按一下Adobe Target提供的影像時要開啟的預設登陸頁面。 過去，點按該影像會改為建立電子郵件時產生預設影像集。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 新增 **啟用SMPP跟蹤** 外部帳戶中的複選框以強制跟蹤輸出。 如需詳細資訊，請參閱[詳細文件](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)以瞭解詳情。

**技術演變**

queryDef

已針對&quot;orderBy&quot;子句修改queryDef。 在更改前，查詢表的主鍵將隱式添加到「orderBy」子句中。 在某些資料庫引擎（至少是postgresql）上，它會阻止索引的使用（orderBy子句的所有欄位必須由同一索引覆蓋）。 如果您與此行為相依，則必須在「orderBy」子句中明確新增主鍵。

例如，如果您有下列查詢：

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

以（在18.4變更前）的形式隱含：

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode函式

「urlEncode」 JavaScript函式無法正常用於非ASCII字元。 已修正，現在應可搭配所有Unicode字元（包括日文字元）使用。 如果您依賴非ASCII字元的「urlEncode」行為，則必須調整您的代碼。

包導入新模式

使用命令行導入包時可使用新模式，允許循環依賴項（對於大型包不建議使用）。 會保留現有功能。 對於具有循環依賴項的此類包，將添加一個新標籤 **-usejs** 已新增至命令列套件匯入。 執行時，會像從介面執行套件匯入時一樣使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修補程式**

* 修正從Adobe Campaign Standard複製傳送和追蹤記錄檔至Adobe Campaign Classic時的同步問題。 (NEO-10023)
* 修正了在快速載入操作失敗後，ETL工作流程恢復時，處理Teradata中錯誤和記錄表的問題。 現在，每次工作流恢復時，錯誤和日誌表都會被正確刪除。 (NEO-10672)
* 修正了升級後問題，若已安裝FDA套件，則會自動安裝Hive套件(Hadoop所需)。 (NEO-10592)
* 修正將無效網域視為 **未定義** 錯誤。 (NEO-10248)
* 修正傳送android推播傳送時，deliveryLogStats表格中重複記錄的問題。 (NEO-10234)
* 修正條碼掃描器無法讀取某些條碼格式的問題。 (NEO-10125)
* 修正使用非ASCII字元時，「urlEncode」 JavaScript函式的問題。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-10123)
* 修正在Teradata資料庫上執行包含sha256函式的查詢時的問題。 (NEO-10119)
* 修正了使用超大的SalesForce表時，SalesForce活動中可能發生的工作流記憶體錯誤。 (NEO-9900)
* 修正 **生成補充** 選項（使用FDA時在目標工作流程活動中）。 (NEO-9878)
* 修正可能導致 **已處理** 和 **成功** 量度使用中間來源時沒有在行銷執行個體上更新。 (NEO-9454)
* 修正平台總共提供超過10,000個選件時的互動非主張規則(NEO-9352)
* 修正了使用XML外部檔案時無法指定傳送目標的問題。 (NEO-9312)
* 修正在選件上執行假設並更新主張狀態時，可能導致工作流程錯誤的問題。 (NEO-9304)
* 修正根據Android傳送對應的屬性使用壓力規則時，在傳送分析期間發生的錯誤。 (NEO-9202)
* 修正排序收件者清單中的欄時，可能導致效能問題的問題。 有關queryDef修改的詳細資訊，請參閱下面的「技術演變」一節。 (NEO-9042)
* 修正核准電子郵件中的連結可能指向錯誤登入URL的問題，尤其是使用Federated ID登入類型時。 (NEO-9011)
* 修正某些時區的報表日期選擇器顯示錯誤日期的問題。 (NEO-9007)
* 修正使用FDA SQL資料庫時無法檢視傳出目標的問題。 (NEO-8924)
* 修正導致MS Dynamics CRM連接器無法提取前7天資料的問題。 (NEO-8803)
* 修正Analytics整合的錯誤，該錯誤會讓使用者無法加入國際字元。 (NEO-8719)
* 修正了在沒有適當權限的情況下，可能會啟用工作流程編輯的問題。 (NEO-8708)
* 修正在混合架構中使用訊息中心時，導致連線中斷或連線遺失（逾時）的FDA over HTTP問題。 (NEO-8438)
* 修正負ID的增量查詢活動中發生的工作流程錯誤。 (NEO-8229)
* 修正某些畫面中可能顯示雙捲軸的問題。 (NEO-8208)
* 修正了在執行更新資料庫結構精靈時，顯示錯誤訊息的問題。 PostUpgrade將對名稱超過30的索引執行更名。 請注意，對於大型表，替換索引需要時間。 (NEO-7983)
* 修正追蹤記錄無法從Message Center執行例項正確同步至控制例項的問題。 (NEO-7286)
* 修正選件擴充活動的效能問題。 (NEO-7263)
* 修正了透過FDA查詢Redshift資料庫時無法使用DaysAgo函式的問題。 (NEO-7099)
* 修正資料管理中無法在類似擴充的工作流程活動上建立索引的回歸。
* 修正以標題建立外部資源時可能發生的問@id
* 修正透過FTP伺服器上傳壓縮檔案，或上傳檔案名稱中含有萬用字元的檔案時，可能發生的問題。
* 修正外部自訂資源中建立至Campaign Standard的長基本類型列舉問題。
* 修正即使與提供者的連線失敗，仍可能傳送簡訊，導致簡訊遺失的問題。
* 修正導致SMTP連線無限期卡住的錯誤。
* 修正使用LINE對應或篩選及定位結構不同時，訊息準備期間壓力類型規則的問題。
