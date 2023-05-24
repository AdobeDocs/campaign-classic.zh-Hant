---
product: campaign
title: Campaign Classic 2018 版本
description: 進一步瞭解 Campaign Classic 2018 版本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 8%

---

# 2018 版本{#release-2018}



## 第 18.10 發行版本

### 版本 18.10.6 - 版本編號 8985{#release-18-10-6-build-8985}

2019年7月12日

**功能改進**

* 我們現在允許在匯入工作流程期間刪除Microsoft Dynamics中建立的虛擬記錄。
* 修正檔案收集器工作流程活動的問題，當檔案存取被拒絕時，該問題可能會記錄回圈中的錯誤。 (NEO-12085)
* 修正造成使用者活動與未完成傳遞指標追蹤報告之間報告不一致的問題。 (NEO-11742)
* 改善使用內部帳戶時執行安全性區域套件的許可權。
* 修正可能導致配對記錄中發生錯誤的問題。 (NEO-8978)

### 版本 18.10.5 - 版本編號 8984{#release-18-10-5-build-8984}

2019年4月23日

**功能改進**

* 修正SQL死鎖的問題，此問題會導致傳遞分析在同時分析/傳送時失敗（同時分析兩個傳遞時）。 (NEO-13026)
* 已移除「工作流程熱度圖」中的10,000筆記錄限制，以修正遺失資料的問題。 (NEO-12329)
* 修正在擴充工作流程活動中使用「保留主要集的所有其他資料」選項的問題。 (NEO-13291)

### 版本 18.10.4 - 版本編號 8983{#release-18-10-4-build-8983}

2019年4月15日

**功能改進**

* 修正交易式訊息追蹤指標的計算程式問題。 (NEO-12529、NEO-12581)
* 修正HTTPRequest API未等待所有回呼完成的問題。 (NEO-12628)
* 在優惠券臨時表格中新增了索引，以最佳化傳送傳遞。 (NEO-12437)
* 修正分析以日文(.JP)網域為目標的收件者時所發生的問題。 (NEO-12246)
* 在Analytics整合中，現在允許擷取含有%字元的AAM區段資料。 (NEO-12025)
* 修正使用HTTP2傳送推播通知時的Tomcat當機問題。 (NEO-12701)

### 版本 18.10.3 - 版本編號 8981{#release-18-10-3-build-8981}

2019年1月29日

>[!CAUTION]
>
>此組建已召回。 請 [升級至最新組建版本](../../production/using/build-upgrade.md)  或連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**功能改進**

* 修正s3檔案傳輸工作流程活動的問題。 (NEO-12473)
* 修正追蹤工作流程可能失敗的問題。 (NEO-12520)
* 修正IMS登入的問題。
* 修正使用大型選件ID時，異動訊息中的預覽和內容核准問題。
* 修正中間來源（傳遞計數器）工作流程的問題。
* 修正資料庫結構更新在NmsRecipient上捨棄新索引的問題。
* 修正針對傳送的主要目標使用「在外部檔案中定義」選項時可能發生的主控台當機問題。 (NEO-12349)
* 修正數個InMail當機問題。
* 修正使用更新資料工作流程活動來刪除儲存在FDATeradata資料庫中的記錄的問題。
* 修正秘密金鑰管理中的不一致問題。
* 修正當輸入欄位為： xml=true和calculated=true時，擴充活動的問題
* 修正在行動應用程式上傳送推播通知時的字元逸出問題。
* 修正了無法在中間來源外部帳戶中從FDA切換到SOAP同步方法的問題。

### 版本 18.10.2 - 版本編號 8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>此組建已召回。 請 [升級至最新組建版本](../../production/using/build-upgrade.md) 或連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**功能改進**

* 修正在FDA上使用MySQL執行工作流程時的各種問題。 (NEO-11652)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正在傳送中使用種子地址時，ID用盡的問題。 (NEO-11842)
* 修正使用複雜工作流程時可能發生的使用者端凍結問題。 (NEO-11847)
* 修正搭配1：N連結使用值分佈時的顯示問題。 (NEO-11820)
* 修正工作流程熱度圖中的Oracle錯誤。
* 修正在擴充活動中新增優惠方案主張時的正確問題。
* 修正SQL資料管理連線問題。
* 修正產生負ID時暫時工作流程表格名稱的問題。
* 修正Workflow HeatMap中工作流程持續時間計算的問題。


### 版本 18.10.1 - 版本編號 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>此組建已召回。 請 [升級至最新組建版本](../../production/using/build-upgrade.md) 或連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**有哪些新功能？**

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
   <td> Adobe Campaign已為推播通知實施許多增強功能：<br /> 
    <ul> 
     <li> <p>在iOS中追蹤無訊息通知 </p> </li> 
     <li> <p>在iOS中實施註冊呼叫的意見回饋</p> </li> 
     <li> <p>提升iOS傳送準備速度</p> </li> 
    </ul> <p>Google棄用GCM時，Android V2聯結器現在只能連線至FCM伺服器。</p><p>如需詳細資訊，請參閱<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
  <tr> 
   <td> SQL資料管理活動<br /> </td> 
   <td> <p>已新增新的資料管理工作流程活動。 此 <strong>SQL資料管理</strong> 活動可讓您撰寫或複製並貼上自己的SQL指令碼，以建立和填入工作表（僅限FDA）。 </p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/sql-data-management.md">詳細文件</a>以瞭解詳情。</p></td> 
  </tr> 
  <tr> 
   <td> 監視工作流程<br /> </td> 
   <td> <p>透過新的Adobe Campaign Workflow HeatMap，平台管理員可以快速以圖形呈現所有並行工作流程，進而監控執行個體的負載並據此規劃工作流程。</p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/heatmap.md">詳細文件</a>以瞭解詳情。</p> <p>Workflow HeatMap套件也可依需求用於8977之前的組建（從組建8700開始）。 如需請求和安裝的詳細資訊，請參閱 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">此頁面</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 修正了可能導致伺服器端請求偽造(SSRF)攻擊和拒絕服務(DoS)攻擊的安全問題。 (NEO-11453)
* 內容（追蹤重新導向、映象頁面、調查等） Campaign現在將提供X-Robots-Tag： nocache標頭。 這可防止網際網路搜尋引擎索引此內容。 (NEO-11101)
* 修正訂閱API (nms)中的XTK插入問題:subscription:取消訂閱和nms:subscription:訂閱)。
* 修正取消訂閱Web應用程式中的XTK插入問題。
* 移除了某些SMS記錄檔中顯示的不安全密碼。

**功能改進**

* 現在針對 Campaign Classic API 推出[專屬頁 面](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。如果您使用 jsapi.chm 檔案，請參考新的線上版本。
* 現已支援PostgreSQL 10、Debian 9和Teradata16.20。 請參閱「[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)」。
* 建立SFTP連線時，您現在可以使用Proxy驗證。 如需詳細資訊，請參閱 [詳細檔案](../../installation/using/file-res-management.md) (NEO-9868)
* 此 **日期計算公式** 現在，使用直接郵件傳遞範本建立單一傳遞時，傳遞屬性中會提供選項。 (NEO-9792)
* Cookie追蹤和Web應用程式的網域名稱管理已經過改良。 如需詳細資訊，請參閱下方的「技術演變」一節。
* 安全性及效能方面，已改善在傳遞或登陸頁面中匯入Adobe Marketing Cloud共用資產的功能。
* 行動管道外部帳戶中有一個新核取方塊，可在記錄檔中啟用詳細的SMPP追蹤，以便直接從Adobe Campaign介面存取此輸出。
* 在broadlog中，現在連線數目上限和每小時訊息數上限之間有所區別。 當達到限制時，就可以知道輸送量為何受限。 先前，相同的訊息（「達到配額」）會套用至這兩種情況。
* 您現在可以指定從集區取得連線時要執行的SQL指令碼。 此指令碼可用於設定預設結構描述。 此指令碼將在查詢分段後套用。 (NEO-11256)
* Campaign SDK不再儲存使用者ID以遵守PII法規。 資料現在會儲存為雜湊。
* 匯入套件匯出XML檔案時，Campaign現在支援檔案中存在BOM，即使檔案中明確宣告編碼亦然。

**技術演變**

使用者端和伺服器升級

>[!CAUTION]
>
>如果您的伺服器更新至18.10，則必須使用18.10使用者端才能存取您的伺服器。 18.10使用者端將可連線到較舊的伺服器版本。

網域名稱管理

Cookie追蹤和Web應用程式的網域名稱管理已經過改良。

現在，預設支援所有兩個字母的第二層網域名稱(例如.aa.com)。 對於更複雜的網域名稱（例如三個字母的第二層網域，例如.com.au），您需要將它們新增到 **cookieDomains** serverConf的選項（在重新導向標籤下）。 範例如下：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增強功能

已重新處理NmsRecipient的索引。 這應該會改善使用此表格的查詢效能。 如果您已經完成NmsRecipient的擴充，您可以確認您沒有複製新索引的索引（以最小化資料庫伺服器上的空間使用量）。 (NEO-8228)

在PostgreSql上使用UTF-8定序時，現在可以建立將最佳化「LIKE &#39;string%&#39;」（或「starts with」）作業的索引。 如果對同一欄執行其他操作（例如，排序依據或聯結），則需要另一個標準索引。 在結構描述端，這是透過在索引定義上新增indexOption=&quot;searchFromStart&quot;來完成的（它會建立varchar_pattern_ops索引而不是標準btree索引）。 例如（在NmsRecipient）：

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

NmsRtEvent和NmsEventHisto已新增新索引（「已排程」欄），這應該可以改善對應表單的顯示時間(NEO-11738)。

這些索引變更可能會導致執行升級後所需的時間增加。

**修補程式**

* 修正檔案無法執行的錯誤 **網頁下載** 工作流程活動。 (NEO-11105)
* 修正偶爾會離開的錯誤 **傳送指標和行銷活動屬性** 處於失敗狀態的工作流程(NEO-10820)。
* 修正刪除在工作流程中執行清單更新活動後建立的收件者清單的問題。 (NEO-11696)
* 修正促銷活動行事曆（在日文執行個體上）中提前一個月不正確顯示促銷活動的問題。 (NEO-11445)
* 修正無法將Analytics設定顯示在傳送屬性的Web Analytics標籤中的問題。 (NEO-11619)
* 修正嘗試編輯及儲存nms：delivery輸入表單時顯示的錯誤。 (NEO-10973)
* 修正執行包含檔案傳輸活動的工作流程時，發生的外部帳戶設定問題。 (NEO-11012)
* 修正使用zcat函式在資料載入活動中載入檔案時傳回空白行的問題。 (NEO-11273)
* 修正在傳送分析期間產生重複廣泛記錄的問題。 (NEO-11360)
* 修正在工作流程中執行擴充活動後，因缺少外部連結索引鍵而導致傳送失敗的問題。 (NEO-11537)
* 修正當安裝路徑包含特定GB18030中文字元時，無法正確解除安裝或修復Adobe Campaign的問題。
* 修正將部分追蹤記錄連結至錯誤傳送的問題。 (NEO-11412)
* 修正可能導致部分傳送記錄擱置狀態的時間比預期更長的問題。 (NEO-11336)
* 修正在編輯查詢以新增優惠券至傳遞時發生的錯誤。 (NEO-11037)
* 修正報表中不論選取哪個彙總運運算元，圖表一律會計算值總和的問題。 (NEO-10913)
* 由於「request.scheme」函式已過時，因此已從JSAPI檔案中將其移除。 (NEO-10828)
* 已修正導致某些具有特定時區設定的使用者無法登入Adobe Campaign的問題。 (NEO-10712)
* 修正使用Extended generic SMPP聯結器設定行動通路外部帳戶時發生的問題：如果您針對接收器使用不同引數指定，傳送器會錯誤地使用這些引數，而不是其自己的引數。
* 修正在設定壓力規則的頻率時，因為排程傳遞在第一次仲裁後會持續重新計算，而造成排程傳遞失敗的問題。 (NEO-10016)
* 修正在應用程式集區回收程式（在nlsrvmod.dll程式庫中）期間，造成IIS Web伺服器當機的問題。 (NEO-10862)
* 修正無法在「 」中搜尋收件者的問題 **設定檔和目標** 畫面。 (NEO-8228)
* 修正在記錄數量多的情況下存取Event History資料夾時可能導致逾時錯誤的問題。 (NEO-11738)
* 修正可能導致LINE傳遞收件者誤傳回「無法聯絡」的問題。 (NEO-10833)
* 修正在Oracle上執行具有額外欄的工作流程查詢時的問題。 (NEO-11615)
* 已進行增強功能，以確保已關閉的連線不會在連線集區中保留太久。 (NEO-11392)
* 修正使用目標工作流程活動(查詢、資料載入(RDBMS)等)時的問題 透過FDA連線至包含UTF8字元的外部Oracle表格（在表格名稱、欄位名稱等） 以及包含主鍵限制，且具有系統產生的預設限制名稱。 (NEO-10714)
* 修正無法刪除傳遞HTML內容的問題。 (NEO-11327)
* 修正行銷活動執行後，直接郵件中的XML和CSV檔案預覽問題。 (NEO-11290)
* 修正在擴充工作流程活動中排序資料時的問題。 (NEO-11394)
* 修正排序自訂報表中的資料時的問題。 (NEO-10896)
* 修正搭配Teradata使用useVault設定時導致錯誤的問題。 (NEO-11399)
* 修正刪除多個查詢行時導致Adobe Campaign使用者端主控台當機的問題。 (NEO-10744)
* 修正了在傳送直接郵件時，在某些情況下無法套用壓力規則的問題。 (NEO-9004)
* 修正使用資料載入活動匯入資料型別為「時間」的欄時發生的問題：時間分隔符號即便在移除後也會重設。 (NEO-10743)
* 修正在編輯循環傳遞時，傳遞資料夾無法從「傳遞」屬性中的「執行」資料夾清單顯示的問題。 (NEO-11094)
* 修正「檢視人口」視窗無法顯示200筆記錄以上作為工作流程中「查詢」活動結果目標的問題。 (NEO-11195)
* 修正Oracle中無法執行選取超過1000個元素之DELETE查詢的問題。 (NEO-11171)
* 修正了導致在Android推播通知傳送的其他引數中將URL編碼為追蹤URL的問題。 (NEO-11468)
* 修正將引數設為「一天間隔」和「開啟」時，使用者活動報表中發生的指令碼錯誤。 (NEO-11655)
* 修正透過已驗證的Web Proxy連線至中間來源伺服器或Message Center時發生的問題。 (NEO-11309)
* 修正在選取特定結構的元素後儲存新傳遞構成時發生的Oracle錯誤 **根據SQL檢視**. (NEO-11682)
* 修正使用「解壓縮」選項透過載入檔案活動處理包含.csv的zip檔案時，導致產生拒絕包含誤判檔案的問題。
* xtkjoblog現在由清除清除。

## 第 18.6 發行版本

### 版本 18.6.2 - 版本編號 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>此組建已召回。 請 [升級至最新組建版本](../../production/using/build-upgrade.md) 或連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**有哪些新功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 查詢級區<br /> </td> 
   <td> <p>當多個Campaign使用者連線至相同的FDATeradata外部帳戶時，您現在可以傳遞每個使用者特定的查詢範圍（索引鍵/值組）。 每當Campaign使用者在Teradata資料庫上執行查詢時，Adobe Campaign現在可以傳送與使用者相關聯的中繼資料。 例如，這些資料（包含於金鑰和值的清單中）可供Teradata管理員用於稽核或管理存取許可權。</p><p>如需詳細資訊，請參閱<a href="../../installation/using/external-accounts.md">詳細文件</a>以瞭解詳情。</p> </td>
  </tr> 
 </tbody> 
</table>

**功能改進**

* 已增強電子郵件封存記錄，讓您更輕鬆且更清楚檢查哪些電子郵件已成功傳遞或透過密件副本封存失敗。 (NEO-10675)
* 修正導致在追蹤broadlog中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正導致傳遞屬性被錯誤覆寫的隨機問題。 (NEO-11015)
* 修正排序擴充活動結果時的語法錯誤。 (NEO-11394)
* 修正在中使用計算欄位時的問題 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-11382)
* Tomcat已更新，以防止弱點利用。 (NEO-11503)
* 修正了使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用時發生的問題 **[!UICONTROL Prepare the personalization data with a workflow]** 傳送選項。 (NEO-11047)
* 修正使用擴充聯結器時，無法傳送簡訊的升級後問題。
* 改良的套件匯入/匯出（已在介面中新增記錄檔和區域）。
* 修正下列問題，升級後記錄檔顯示無用錯誤： **[!UICONTROL Survey answers]** 工作流程活動未完全設定。

**技術演變**

查詢級區

特定金鑰（PROXYUSER或PROXYROLE）可用來將Teradata使用者或角色與Campaign使用者建立關聯。 已新增使用此Proxy使用者/角色的新許可權。 您需要將GRANTCONNECTTHROUGH存取權新增至資料庫帳戶(在Teradata外部帳戶中定義的帳戶)。

已在Teradata外部帳戶中新增索引標籤。 此 **[!UICONTROL Query banding]** 索引標籤包含以下選項：

* **[!UICONTROL Active]**：核取此方塊以啟動功能。
* **[!UICONTROL Default]**：輸入使用者沒有關聯查詢級區時將使用的預設查詢級區。 如果未定義預設查詢級區，則沒有關聯查詢級區的使用者將無法使用Teradata。
* **[!UICONTROL Users]**：為每位使用者指定查詢級區。 您可以視需要新增任意數量的索引鍵/值組。 例如：&#39;priority=1；workload=high；&#39;

如需查詢分段的詳細資訊，請參閱以下文章：

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### 版本 18.6.1 - 版本編號 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>此組建已召回。 請 [升級至最新組建版本](../../production/using/build-upgrade.md) 或連絡人 [技術支援](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**有哪些新功能？**

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
   <td> Campaign Classic已新增一系列安全性改善專案。 以下列出改善與修正。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支援Windows Server 2016<br /> </td> 
   <td> Adobe Campaign 現在相容於 Windows Server 2016。 請參閱 <a href="https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html">Campaign Classic相容性對照表</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

decryptString

此 **decryptString** 函式已過時。 請參閱 [過時和移除的功能](deprecated-features.md) 文章。

對於新客戶，此函式現在僅用於解密登陸頁面中收件者的加密ID。 若要解密儲存在外部帳戶中的密碼，請使用新的 **decryptPassword** 函式。

對於現有客戶，此函式的行為不會變更，但建議您使用 **decryptPassword** 而非 **decryptString**. 此 **XtkSecurity_Unsafe_DecryptString** 相容性選項是在升級後新增，並依預設啟用，好讓您繼續使用函式。 如果您想要停用 **decryptString**，停用選項。

decryptPassword

此 **decryptPassword** 函式已新增。 它可讓您解密儲存在外部帳戶中的密碼。 請參閱 [JSAPI](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html) 說明檔案以取得詳細資訊。

檔案API

若為新的安裝，透過檔案API的資料夾存取權僅限於 **var**， **sftp** 和Adobe Campaign的暫存資料夾。

針對現有客戶，檔案API無法再存取 **conf** Adobe Campaign資料夾。 此 **XtkSecurity_Disable_JSFileSandboxing** 相容性選項由postupgrade新增並依預設啟用，可讓您繼續存取其他資料夾。 如果您想要限制對 **var**， **sftp** 和Adobe Campaign的暫存資料夾，請停用選項。

**修補**

* 修正可能影響SMS交易式訊息效能的問題。 (NEO-9812)

## 第 18.4 發行版本

### 版本 18.4.5 - 版本編號 8937{#release-18-4-5-build-8937}

2018年11月21日

**功能改進**

* 修正在FDA上使用MySQL執行工作流程時的各種問題。 (NEO-11652)
* 修正造成部分傳送母體在特定情況下維持擱置狀態的問題。 (NEO-11336)
* 修正SMS自動回應的間歇性問題。 (NEO-11811)
* 修正在傳送中使用種子地址時，ID用盡的問題。 (NEO-11842)
* 修正在擴充工作流程活動中執行排序時的語法錯誤。 (NEO-11394)
* 修正重新啟動IIS時可能導致Web伺服器當機的問題。 (NEO-10862)
* 修正可能導致追蹤工作流程在建置升級(FDA - SQL)後失敗的問題。 (NEO-11635)
* 修正可能導致工作流程清單資料遺失的問題。 (NEO-11696)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正網站追蹤無法用於「com.au」網域的問題(NEO-4385)。
* 修正使用複雜工作流程時可能發生的使用者端凍結問題。 (NEO-11847)
* 修正在選取特定結構的元素後儲存新傳送時的Oracle錯誤(NEO-11682)。
* 修正查詢包含重音字元(FDA/Teradata)的欄位時的問題。 外部帳戶現在可讓您變更用來與Teradata驅動程式通訊的編碼。 (NEO-11818).
* 修正了在推播通知中傳遞其他變數的URL時，可能導致行動應用程式收到的資料格式錯誤或不正確的追蹤問題。 (NEO-11468、NEO-11960)
* 修正搭配1：N連結使用值分佈時造成顯示問題的問題。 (NEO-11820)
* 修正大量載入無法在Teradata16運作的問題。
* 增加Teradata上時間戳記的緩衝區大小，以避免15.10驅動程式的繫結問題。
* 改善可能導致升級後問題的長名稱索引管理。
* 改善子系廢棄處理(MTA)期間的共用記憶體可用時間。
* 修正Apache （追蹤）中的潛在死結。


### 版本 18.4.4 - 版本編號 8936{#release-18-4-4-build-8936}

2018年8月1日

**功能改進**

* 已增強電子郵件封存記錄，讓您更輕鬆且更清楚檢查哪些電子郵件已成功傳遞或透過密件副本封存失敗。 (NEO-10675)
* 修正導致在追蹤broadlog中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正了使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用時發生的問題 **[!UICONTROL Prepare the personalization data with a workflow]** 傳送選項。 (NEO-11047、NEO-11301)
* 修正導致傳遞屬性被錯誤覆寫的隨機問題。 (NEO-11015)
* 修正在中使用計算欄位時的問題 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-11382)
* 修正使用儲存在XML中的資料時的問題 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-10816)
* 修正使用版本編號8935執行伺服器升級時的問題。
* 修正下列問題，升級後記錄檔顯示無用錯誤： **[!UICONTROL Survey answers]** 工作流程活動未完全設定。
* FDATeradata：修正SQL表格中自動增加欄位和索引的問題。

### 版本 18.4.3 - 版本編號 8935{#release-18-4-3-build-8935}

2018年6月22

**功能改進**

* 修正Microsoft Edge和Internet Explorer的追蹤編碼問題。 (NEO-11257)
* 修正LINE傳遞中的影像連結個人化問題。 (NEO-11077)
* 修正ID序列產生機制無法正常運作的問題。 (NEO-11115)
* 修正當使用具有整數型別調解金鑰的自訂名稱空間時，隱私權(GDPR)請求無法運作的問題。 (NEO-11123)
* 修正使用時可能發生的錯誤 **[!UICONTROL Distribution of values]** 中的選項 **[!UICONTROL Query]** 工作流程活動。 (NEO-10958)
* 修正從行銷執行個體同步優惠方案空間至互動執行個體時的問題。 (NEO-11162)
* 改善升級後期間長名稱索引的管理

### 版本 18.4.2 - 版本編號 8932{#release-18-4-2-build-8932}

2018年5月22

**功能改進**

* 修正Windows Server更新無法正常運作的問題。
* 已修正 **[!UICONTROL Survey Result]** 使用儲存在XML中的資料時的活動。 報告顯示不正確。 (NEO-10816)
* 修正使用退回郵件伺服器時，inMail程式可能發生的效能問題。 (NEO-10641)
* 修正升級1000多個結構描述時可能發生的資料庫升級問題。

### 版本 18.4.1 - 版本編號 8931{#release-18-4-build-8931}

2018年4月24日

**有哪些新功能？**

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
   <td> <p>GDPR是歐盟(EU)的新隱私權法律，協調資料保護要求並以現代化方式加以規範，於2018年5月25日生效。 GDPR 適用於所持有資料的主體居住於歐盟的 Adobe Campaign 客戶。</p> <p>除了Adobe Campaign所提供的隱私權功能（包括同意管理、資料保留設定和使用者角色）之外，我們還將以資料處理者的角色利用此機會，加入其他功能，以協助您做好準備，以利您以資料控制者的身分處理特定GDPR請求：</p> 
    <ul> 
     <li> <p>存取許可權：允許資料主體接收資料控制者所擷取的個人資料副本，可能包括儲存在Adobe Campaign中的資料。</p> </li> 
     <li> <p>刪除權利：賦予資料主體權利，使其有權清除資料控制者所擷取的個人資料，可能包括儲存在Adobe Campaign中的資料。</p> </li> 
    </ul> 如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">詳細文件</a>以瞭解詳情。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的設定檔案<br /> </td> 
   <td> <p>Adobe Campaign現在提供作用中設定檔清單，每月透過專用工作流程更新。</p> <p>如需詳細資訊，請參閱<a href="../../platform/using/about-profiles.md#active-profiles">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推播聯結器增強功能<br /> </td> 
   <td> <p>Android聯結器已增強，可支援更高的輸送量。 </p> <p>如需詳細資訊，請參閱<a href="../../delivery/using/configuring-the-mobile-application.md">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 現在已停用外部實體的擴充，以防止來自未經驗證的使用者的潛在攻擊。 (NEO-10173)
* 加強許可權，以防止標準使用者變更執行個體設定引數，例如應用程式存取URL、LDAP設定等。 (NEO-10171)
* 修正可能透過棧疊追蹤顯示敏感資訊的問題。 錯誤詳細資料現在會記錄於後端，並記錄至無法從外部網路存取的位置。 (NEO-10176)
* 加強許可權，以防止標準使用者檢視管理員上傳的檔案和/或匯出的套件。 (NEO-10170)

**功能改進**

* **LINE頻道 — 架構增強功能**：和Adobe Campaign中的所有其他管道一樣，LINE管道現在也支援所有部署型別：託管、混合和內部部署。
* **序列自動產生**：ID產生機制已增強，以提高具有大量物件之Campaign執行個體的使用期限。

**其他變更**

* 新模式可用於使用命令列匯入套件，允許循環相依性（不建議用於大型套件）。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-8979)
* 改善Teradata中大量資料載入的效能，並修正無法顯示記錄中處理資料的正確值的問題。 (NEO-10429)
* 從Audience Manager匯入對象現在適用於分割檔案。 之前，importSharedAudience技術工作流程只會匯入區段的最後一個檔案。 (NEO-10156)
* 在Windows上，Campaign伺服器預設安裝路徑已變更。 啟動64位元版本安裝程式時，預設安裝路徑現在為： **C:\Program Files\Adobe\AdobeCampaign Classicv7** 而非 **C:\Program檔案(x86)\Adobe\Adobe Campaign Classic v7**
* 已增強預設MX規則，以包含更多網域並最佳化輸送量。
* 對部署精靈SOAP呼叫(xtk：serverOptions#SaveOptions)強制的存取限制。
* 已移除weka.jar過時程式庫，且已更新OpenSSL程式庫以進行安全性最佳化。
* 改善計費技術工作流程，以確保執行個體效能。
* 管理員設定或重設任何操作員密碼的能力已恢復。 若要這麼做，請在運運算元上按一下滑鼠右鍵，然後選取 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 並設定運運算元的新密碼。 建議操作員在第一次重新連線時變更密碼。 如需詳細資訊，請參閱[詳細文件](../../production/using/lost-password.md)以瞭解詳情。
* 為了支援Adobe Target中的新多租使用者功能，現在可在設定與Target整合的選項和外部帳戶時，將新的「at_property」引數新增至URL。 此引數適用的值可在Adobe Target中找到，並供Campaign執行對Target的呼叫時使用。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 您現在可以指定按一下Adobe Target提供的影像時要開啟的預設登陸頁面。 先前，在建立電子郵件時，按一下該影像會導向預設影像集。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 已新增 **啟用SMPP追蹤** 外部帳戶中強制追蹤輸出的核取方塊。 如需詳細資訊，請參閱[詳細文件](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)以瞭解詳情。

**技術演變**

queryDef

已修改&quot;orderBy&quot;子句的queryDef。 在變更之前，查詢表格的主索引鍵會隱含地新增至「orderBy」子句。 在某些資料庫引擎（至少是postgresql）上，這會防止使用索引（orderBy子句的所有欄位都必須由相同的索引涵蓋）。 如果您與此行為相依，則必須在&quot;orderBy&quot;子句中明確新增主索引鍵。

例如，如果您有以下查詢：

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

它會隱含地傳遞為（在18.4變更之前）：

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

&#39;urlEncode&#39; JavaScript函式無法正確用於非ASCII字元。 已修正此錯誤，現在可搭配所有Unicode字元（包括日文字元）使用。 如果您依賴非ASCII字元的「urlEncode」行為，則必須調整程式碼。

套件匯入新模式

新模式可用於使用命令列匯入套件，允許循環相依性（不建議用於大型套件）。 保留現有功能。 對於具有循環相依性的這類套件，會新增一個旗標 **-usejs** 已新增至命令列套件匯入。 在執行時，它會使用JSEngine，就像從介面執行套件匯入時一樣。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修補程式**

* 修正從Adobe Campaign Standard複製傳遞和追蹤記錄到Adobe Campaign Classic時的同步問題。 (NEO-10023)
* 修正了在快速載入作業失敗後恢復ETL工作流程時，處理Teradata中的錯誤和記錄表的問題。 現在，每次繼續工作流程時，都會正確刪除「錯誤」和「記錄」表格。 (NEO-10672)
* 修正了在安裝FDA套件時自動安裝Hive套件(Hadoop所需)的升級後問題。 (NEO-10592)
* 修正將無效網域視為 **未定義** 錯誤。 (NEO-10248)
* 修正傳送android推播傳遞時，deliveryLogStats表格中重複記錄的問題。 (NEO-10234)
* 修正可能導致條碼掃描器無法讀取某些條碼格式的問題。 (NEO-10125)
* 修正使用非ASCII字元時「urlEncode」JavaScript函式的問題。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-10123)
* 修正在Teradata資料庫上執行包含sha256函式的查詢時的問題。 (NEO-10119)
* 修正使用非常大的SalesForce表格時，SalesForce活動中可能發生的工作流程記憶體錯誤。 (NEO-9900)
* 已修正的問題 **產生補充** 使用FDA時定位工作流程活動中的選項。 (NEO-9878)
* 修正可能導致 **已處理** 和 **成功** 使用中間來源時，量度未在行銷執行個體上更新。 (NEO-9454)
* 修正平台中總計超過10,000個選件時的互動不重新主張規則(NEO-9352)
* 修正使用XML外部檔案時，無法指定傳遞目標的問題。 (NEO-9312)
* 修正在優惠方案上執行假設並更新主張的狀態時，可能會導致工作流程錯誤的問題。 (NEO-9304)
* 修正根據Android傳遞對應的屬性使用壓力規則時，傳遞分析期間發生的錯誤。 (NEO-9202)
* 修正對收件者清單中的欄進行排序時，可能導致效能問題的問題。 如需queryDef修改的詳細資訊，請參閱下方的「技術演變」一節。 (NEO-9042)
* 修正核准電子郵件中的連結可能指向不正確的登入URL的問題，尤其是使用Federated ID登入型別時。 (NEO-9011)
* 修正可能導致某些時區報表的日期選擇器中顯示錯誤日期的問題。 (NEO-9007)
* 修正使用FDA SQL資料庫時，無法檢視傳出目標的問題。 (NEO-8924)
* 已修正導致MS Dynamics CRM聯結器無法提取當月前7天的資料的問題。 (NEO-8803)
* 修正Analytics整合中造成使用者無法加入國際字元的錯誤。 (NEO-8719)
* 修正了在沒有適當許可權的情況下可能啟用工作流程編輯的問題。 (NEO-8708)
* 修正在混合架構中使用訊息中心時，FDA透過HTTPs造成連線中斷或連線中斷（逾時）的問題。 (NEO-8438)
* 修正負ID的增量查詢活動中發生的工作流程錯誤。 (NEO-8229)
* 修正可能導致在某些畫面中顯示雙卷軸的問題。 (NEO-8208)
* 修正執行更新資料庫結構精靈時，導致顯示錯誤訊息的問題。 PostUpgrade會執行名稱超過30的索引重新命名。 請注意，對於大型表格，索引取代需要時間。 (NEO-7983)
* 修正未正確從訊息中心執行例項同步追蹤記錄以控制例項的問題。 (NEO-7286)
* 修正優惠方案擴充活動的效能問題。 (NEO-7263)
* 修正透過FDA查詢Redshift資料庫時，無法使用DaysAgo函式的問題。 (NEO-7099)
* 修正了資料管理中導致無法在類似擴充的工作流程活動上建立索引的回歸。
* 修正使用標題@id建立外部資源時可能發生的問題
* 修正透過FTP伺服器上傳壓縮檔案或在檔案名稱中上傳包含萬用字元的檔案時可能發生的問題。
* 修正在Campaign Standard中建立的外部自訂資源中，基底型別列舉較長的問題。
* 修正了可能導致簡訊傳送的問題，即使與提供者的連線失敗而導致簡訊遺失亦然。
* 修正讓SMTP連線無限期停滯的錯誤。
* 修正使用LINE對應或篩選及鎖定目標結構描述不同時，在訊息準備期間發生的壓力型別規則問題。
