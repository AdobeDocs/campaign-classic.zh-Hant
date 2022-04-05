---
product: campaign
title: Campaign Classic 2018 版本
description: 進一步瞭解 Campaign Classic 2018 版本
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 7%

---

# 2018 版本{#release-2018}

![](../../assets/v7-only.svg)

## 第 18.10 發行版本

### 版本 18.10.6 - 版本編號 8985{#release-18-10-6-build-8985}

2019年7月12日

**功能改進**

* 現在，我們允許在導入工作流期間刪除在MicrosoftDynamics中建立的虛擬記錄。
* 修復了「檔案收集器」工作流活動的問題，當拒絕訪問檔案時，該活動可能會在循環中記錄錯誤。 (NEO-12085)
* 修復了導致用戶活動與未結交付指標跟蹤報告之間報告差異的問題。 (NEO-11742)
* 使用內部帳戶時改進了執行安全區域包的權限。
* 已修復可能導致mtachild日誌錯誤的問題。 (NEO-8978)

### 版本 18.10.5 - 版本編號 8984{#release-18-10-5-build-8984}

2019年4月23日

**功能改進**

* 修復了SQL死鎖問題，該問題導致在同時分析/發送（同時分析兩個傳送時）情況下傳遞分析失敗。 (NEO-13026)
* 已刪除工作流熱度映射中的10,000條記錄限制以修復丟失的資料問題。 (NEO-12329)
* 在濃縮工作流活動中使用「保留主集中的所有其他資料」選項時，已修復問題。 (NEO-13291)

### 版本 18.10.4 - 版本編號 8983{#release-18-10-4-build-8983}

2019年4月15日

**功能改進**

* 解決了事務性消息跟蹤指示符的計算過程的問題。 (NEO-12529、NEO-12581)
* 修復了HTTPRequest API的問題，該API未等待所有回調完成。 (NEO-12628)
* 已在優惠券臨時表中添加索引，以優化交付發送。 (NEO-12437)
* 分析以日文(.JP)域為目標的收件人的郵件時，已修復問題。 (NEO-12246)
* 在分析整合中，現在允AAM許檢索帶%字元的段資料。 (NEO-12025)
* 使用HTTP2發送推送通知時，已修復Tomcat崩潰問題。 (NEO-12701)

### 版本 18.10.3 - 版本編號 8981{#release-18-10-3-build-8981}

2019年1月29日

>[!CAUTION]
>
>此建築已召回。 請 [升級到最新版本](../../production/using/build-upgrade.md)  或聯繫人 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**功能改進**

* 已修復s3「檔案傳輸」工作流活動的問題。 (NEO-12473)
* 修復了跟蹤工作流可能失敗的問題。 (NEO-12520)
* 解決了IMS登錄問題。
* 使用大型優惠ID時，解決了事務性消息傳遞中的預覽和內容審批問題。
* 已修復「中間採購（交貨計數器）」工作流的問題。
* 修復了資料庫結構更新問題，該更新刪除了NmsRecipient上的新索引。
* 已修復當將外部檔案中的「定義」選項用於傳遞的主要目標時可能發生的控制台崩潰。 (NEO-12349)
* 已修復多個InMail崩潰。
* 使用更新資料工作流活動刪除FDATeradata資料庫中儲存的記錄時，已修復問題。
* 解決了密鑰管理中的不一致問題。
* 在將欄位鍵入為時，已修復Exchenting活動的問題：xml=true和calculated=true
* 在移動應用程式上發送推送通知時已修復字元轉義問題。
* 已修復中間採購外部帳戶中無法從FDA切換到SOAP同步方法的問題。

### 版本 18.10.2 - 版本編號 8978{#release-18-10-2-build-8978}

2018年12月6日

>[!CAUTION]
>
>此建築已召回。 請 [升級到最新版本](../../production/using/build-upgrade.md) 或聯繫人 [Adobe客戶關懷](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**功能改進**

* 在FDA上使用MySQL運行工作流時已修復各種問題。 (NEO-11652)
* 已解決發送推送通知時的效能問題。 (NEO-11787)
* 在交貨中使用種子地址時已修復ID耗盡問題。 (NEO-11842)
* 已修復在使用複雜工作流時可能出現的客戶端凍結問題。 (NEO-11847)
* 使用帶有1:N連結的值分佈時，解決了顯示問題。 (NEO-11820)
* 已修復工作流熱度映射中的Oracle錯誤。
* 在濃縮活動中添加報價建議時，解決了一個正確的問題。
* 已修復SQL資料管理連接問題。
* 解決了生成臨時工作流表名（如果為負ID）的問題。
* 在工作流熱度映射中使用工作流持續時間的計算解決了問題。


### 版本 18.10.1 - 版本編號 8977{#release-18-10-build-8977}

2018年11月5日

>[!CAUTION]
>
>此建築已召回。 請 [升級到最新版本](../../production/using/build-upgrade.md) 或聯繫人 [Adobe客戶關懷](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

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
   <td> 推送通知改進<br /> </td> 
   <td> 在Adobe Campaign，為推式通知實施了若干改進：<br /> 
    <ul> 
     <li> <p>跟蹤iOS的靜默通知 </p> </li> 
     <li> <p>在iOS實施登記通知反饋</p> </li> 
     <li> <p>提高iOS投遞準備速度</p> </li> 
    </ul> <p>作為GoogleGCM折舊的一部分，Android V2連接器現在只允許連接到FCM伺服器。</p><p>如需詳細資訊，請參閱<a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
  <tr> 
   <td> SQL資料管理活動<br /> </td> 
   <td> <p>已添加新的資料管理工作流活動。 的 <strong>SQL資料管理</strong> 活動允許您編寫或複製貼上您自己的SQL指令碼以建立和填充工作表（僅限FDA）。 </p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/sql-data-management.md">詳細文件</a>以瞭解詳情。</p></td> 
  </tr> 
  <tr> 
   <td> 監視工作流程<br /> </td> 
   <td> <p>使用新的Adobe Campaign工作流熱圖，平台管理員可以快速以圖形方式表示所有併發工作流，從而可以監視實例上的負載並相應地規劃工作流。</p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/heatmap.md">詳細文件</a>以瞭解詳情。</p> <p>Workflow HeatMap軟體包也可根據需要提供8977之前的版本（從8700開始）。 有關請求和安裝的詳細資訊，請參閱 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">此頁</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 已修復可能導致伺服器端請求偽造(SSRF)攻擊和拒絕服務(DoS)攻擊漏洞的安全問題。 (NEO-11453)
* 內容（跟蹤重定向、鏡像頁面、調查等） 現在將由X-Robots-Tag的Camping提供：無快取頭。 這防止了Internet搜索引擎對此內容進行索引。 (NEO-11101)
* 在訂閱API(nms)中修復XTK注入問題:subscription:取消訂閱和nms:subscription:訂閱)。
* 已修復未訂閱Web應用程式中的XTK注入問題。
* 已刪除某些SMS日誌中不安全顯示的密碼。

**功能改進**

* 現在針對 Campaign Classic API 推出[專屬頁 面](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。如果您使用 jsapi.chm 檔案，請參考新的線上版本。
* 現在支援PostgreSQL 10、Debian 9和Teradata16.20。 請參閱「[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)」。
* 建立SFTP連接時，現在可以使用代理身份驗證。 有關詳細資訊，請參閱 [詳細文檔](../../installation/using/file-res-management.md) (NEO-9868)
* 的 **日期計算公式** 當使用直接郵件傳遞模板建立單個傳遞時，選項現在在傳遞屬性中可用。 (NEO-9792)
* 對Cookie跟蹤和Web應用程式的域名管理已得到改進。 有關詳細資訊，請參閱下面的「技術演變」部分。
* Adobe Marketing Cloud在交付或登錄頁共有資產的進口在安全和業績方面都有所改善。
* 在Mobile通道外部帳戶中可使用一個新複選框，以在日誌檔案中啟用詳細的SMPP跟蹤，這使此輸出可從Adobe Campaign介面直接訪問。
* 在廣播中，現在可以區分最大連接數和每小時最大消息數。 當達到限制時，就可以知道為什麼吞吐量受到限制。 以前，同一消息（「配額滿足」）應用於這兩種情況。
* 現在，可以指定在從池獲取連接時要執行的SQL指令碼。 此指令碼可用於設定預設架構。 此指令碼將在查詢段落後應用。 (NEO-11256)
* 市場活動SDK不再儲存用戶ID以遵守我們的PII管理法規。 資料現在以散列形式儲存。
* 導入包導出XML檔案時，市場活動現在支援檔案中存在BOM，即使在檔案中明確聲明了編碼。

**技術演變**

客戶端和伺服器升級

>[!CAUTION]
>
>如果伺服器已更新為18.10，則必須使用18.10客戶端才能訪問伺服器。 18.10客戶端將能夠連接到較舊的伺服器版本。

域名管理

對Cookie跟蹤和Web應用程式的域名管理已得到改進。

現在，預設情況下支援所有雙字母的二級域名（例如.aa.com）。 對於更複雜的域名（例如，三個字母的二級域，如.com.au），您需要在 **cookie域** 的子菜單。 下面是一個示例：

```
<redirection cookiedomain="http://toureiffel.paris">
```

索引增強

NmsRecipient上的索引已重新處理。 這應會提高使用此表的查詢的效能。 如果已擴展了NmsRecipient ，則可能需要驗證沒有複製新索引的索引（以最大限度地減少資料庫伺服器上的空間使用）。 (NEO-8228)

在使用UTF-8歸類的PostgreSql上，現在可以建立將優化「LIKE &#39;string%&#39;」（或「starts with」）操作的索引。 如果對同一列（例如，按順序或聯接）執行其他操作，則需要另一個標準索引。 在架構方面，將通過在索引定義上添加indexOption=&quot;searchFromStart&quot;來完成此操作（它將建立varchar_pattern_ops索引，而不是標準btree索引）。 例如（在NmsRecipient上）:

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

新索引已添加到NmsRtEvent和NmsEventHisto（在「已調度」列上），這應會縮短相應表單(NEO-11738)上的顯示時間。

這些索引更改可能會導致執行升級後所需的時間增加。

**修補程式**

* 修復了阻止檔案從 **Web下載** 下載工作流活動。 (NEO-11105)
* 修復了偶爾離開 **發送指標和市場活動屬性** 工作流處於失敗狀態(NEO-10820)。
* 已修復刪除在工作流中運行「清單」更新活動後建立的收件人清單的問題。 (NEO-11696)
* 已修復在市場活動日曆（日本實例）中提前一個月錯誤顯示市場活動的問題。 (NEO-11445)
* 已修復導致無法在傳遞屬性的「Web分析」頁籤中顯示分析配置的問題。 (NEO-11619)
* 修復了嘗試編輯和保存nms:delivery輸入表單時顯示的錯誤。 (NEO-10973)
* 已修復運行包含檔案傳輸活動的工作流時發生的外部帳戶配置問題。 (NEO-11012)
* 修復了使用zcat函式在資料載入活動中載入檔案時返回空行的問題。 (NEO-11273)
* 已修復在分析交付期間生成重複廣泛日誌的問題。 (NEO-11360)
* 修復了在工作流中執行Inchremting活動後由於缺少外鍵而導致傳遞失敗的問題。 (NEO-11537)
* 已修復當安裝路徑包含特定GB18030中文字元時導致無法正確卸載或修復Adobe Campaign的問題。
* 已修復將某些跟蹤日誌連結到錯誤傳遞的問題。 (NEO-11412)
* 已修復可能導致交貨日誌的某些部分處於掛起狀態的時間比預期更長的問題。 (NEO-11336)
* 已修復編輯查詢以將優惠券添加到交貨時發生的錯誤。 (NEO-11037)
* 修復了報表中的問題，這些報表使圖表始終計算值之和，而不管選擇了哪個聚合運算子。 (NEO-10913)
* 由於不建議使用&quot;request.scheme&quot;函式，因此已從JSAPI文檔中刪除該函式。 (NEO-10828)
* 已修復導致某些具有特定時區配置的用戶無法登錄Adobe Campaign的問題。 (NEO-10712)
* 已修復使用擴展通用SMPP連接器設定Mobile通道外部帳戶時出現的問題：如果您為接收器指定了不同的參數，則發送器將錯誤地使用這些參數，而不是自己的參數。
* 修復了在為壓力規則設定頻率時導致計畫交貨失敗的問題，因為在第一次仲裁之後，交貨會不斷重新計算。 (NEO-10016)
* 已修復導致IIS Web伺服器在應用程式池回收過程（在nlsrvmod.dll庫中）崩潰的問題。 (NEO-10862)
* 已修復可能無法在中搜索收件人的問題 **配置檔案和目標** 的上界。 (NEO-8228)
* 修復了在記錄數較多的情況下訪問事件歷史記錄資料夾時可能導致超時錯誤的問題。 (NEO-11738)
* 已修復可能導致LINE交貨收件人錯誤返回為「無法訪問」的問題。 (NEO-10833)
* 在執行具有附加列的工作流查詢時，已修復問題Oracle。 (NEO-11615)
* 已進行增強，以確保關閉的連接不會在連接池中保留太長時間。 (NEO-11392)
* 使用目標工作流活動(查詢、資料載入(RDBMS)等)時已修復問題 通過FDA連接到包含UTF8字元（在表名、欄位名等中）的外部Oracle表 並且還包含一個主鍵約束，該主鍵約束具有系統生成的預設約束名。 (NEO-10714)
* 已修復可能無法刪除傳遞的HTML內容的問題。 (NEO-11327)
* 在運行市場活動後，在直郵中修復了XML和CSV檔案預覽問題。 (NEO-11290)
* 修復了在濃縮工作流活動中對資料排序時的問題。 (NEO-11394)
* 在自定義報表中對資料排序時已修復問題。 (NEO-10896)
* 已修復在使用useVault設定和Teradata時導致錯誤的問題。 (NEO-11399)
* 修復了刪除多個查詢行時導致Adobe Campaign客戶端控制台崩潰的問題。 (NEO-10744)
* 已修復導致在傳遞直接郵件時在某些情況下無法應用壓力規則的問題。 (NEO-9004)
* 已修復使用資料載入活動導入資料類型為「time」的列時出現的問題：即使刪除時間分隔符後，也會重置時間分隔符。 (NEO-10743)
* 修復了在編輯循環交貨時阻止「交貨」資料夾從「交貨」屬性的「執行」資料夾清單中顯示的問題。 (NEO-11094)
* 已修復一個問題，該問題使「查看填充」窗口無法將200多條記錄顯示為工作流中查詢活動的結果目標。 (NEO-11195)
* 已修復Oracle中的問題，該問題阻止在選擇1000個以上元素時執行DELETE查詢。 (NEO-11171)
* 已修復導致在Android推送通知傳遞的附加參數中將URL編碼為跟蹤的URL的問題。 (NEO-11468)
* 修復了將參數設定為「一天間隔」和「開啟」時在「用戶活動」報告中出現的指令碼錯誤。 (NEO-11655)
* 已修復通過經過身份驗證的Web代理連接到中間採購伺服器或消息中心時出現的問題。 (NEO-11309)
* 修復在選擇特定架構的元素後保存新傳遞組合時發生的Oracle錯誤 **基於SQL視圖**。 (NEO-11682)
* 通過使用「解壓縮」選項的載入檔案活動處理包含.csv的zip檔案時，修復了導致生成包含誤報的拒絕檔案的問題。
* xtkjoblog現在由清理清除。

## 第 18.6 發行版本

### 版本 18.6.2 - 版本編號 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>此建築已召回。 請 [升級到最新版本](../../production/using/build-upgrade.md) 或聯繫人 [Adobe客戶關懷](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

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
   <td> 查詢段<br /> </td> 
   <td> <p>當多個市場活動用戶連接到同一FDATeradata外部帳戶時，您現在可以傳遞特定於每個用戶的查詢範圍（密鑰/值對）。 每次市場活動用戶在Teradata資料庫上執行查詢時，Adobe Campaign現在都能夠發送與該用戶相關聯的元資料。 這些資料（包含在密鑰和值清單中）然後可供Teradata管理員用於審計或管理訪問權限。</p><p>如需詳細資訊，請參閱<a href="../../installation/using/external-accounts.md">詳細文件</a>以瞭解詳情。</p> </td>
  </tr> 
 </tbody> 
</table>

**功能改進**

* 電子郵件存檔日誌已得到增強，這使檢查哪些電子郵件已成功傳送或通過密件抄送存檔失敗變得更加容易和清晰。 (NEO-10675)
* 已修復導致在跟蹤廣播中顯示負載平衡器IP而不是客戶IP的問題。 (NEO-11295)
* 修復了導致錯誤覆蓋傳遞屬性的隨機問題。 (NEO-11015)
* 在對富集活動結果進行排序時修復語法錯誤。 (NEO-11394)
* 在中使用計算欄位時修復問題 **[!UICONTROL Survey answers]** 工作流活動。 (NEO-11382)
* 已更新Tomcat以防止漏洞利用。 (NEO-11503)
* 使用FDA連接到PostgreSQL資料庫時，已修復LATIN1編碼錯誤。 (NEO-11299)
* 已修復使用 **[!UICONTROL Prepare the personalization data with a workflow]** 「交貨」選項。 (NEO-11047)
* 修復了在使用擴展連接器時無法發送SMS的錯誤級別問題。
* 改進的包導入/導出（在介面中添加了日誌和區域）。
* 修復了在以下情況下在配置級別日誌中顯示無用錯誤的問題： **[!UICONTROL Survey answers]** 工作流活動未完全配置。

**技術演變**

查詢段

特定鍵（PROXYUSER或PROXYROLE）用於將Teradata用戶或角色與市場活動用戶關聯。 已添加新權限以使用此代理用戶/角色。 您需要將GRANTCONNECTTHROUGH訪問權限添加到資料庫帳戶(在Teradata外部帳戶中定義)。

已在Teradata外部帳戶中添加新頁籤。 的 **[!UICONTROL Query banding]** 頁籤包含以下選項：

* **[!UICONTROL Active]**:選中此框以激活特徵。
* **[!UICONTROL Default]**:輸入預設的查詢段落，如果用戶沒有關聯的查詢段落，將使用該段落。 如果沒有定義預設查詢段落，則沒有關聯查詢段落的用戶將無法使用Teradata。
* **[!UICONTROL Users]**:為每個用戶指定查詢段落。 您可以根據需要添加任意數量的鍵/值對。 例如：&#39;priority=1;workload=high&#39;&#39;

有關查詢段落的詳細資訊，請參閱以下文章：

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### 版本 18.6.1 - 版本編號 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>此建築已召回。 請 [升級到最新版本](../../production/using/build-upgrade.md) 或聯繫人 [技術支援](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

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
   <td> 在Campaign Classic中增加了一系列安全改進。 下面列出了改進和修復。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支援Windows Server 2016<br /> </td> 
   <td> Adobe Campaign 現在相容於 Windows Server 2016。 請參閱 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic相容性矩陣</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

decryptString

的 **decryptString** 函式已棄用。 請參閱 [已棄用和已刪除的功能](deprecated-features.md) 文章。

對於新客戶，此函式現在僅用於解密登錄頁中收件人的加密ID。 要解密儲存在外部帳戶中的密碼，請使用 **decryptPassword** 的子菜單。

對於現有客戶，此函式的行為不會更改，但建議您使用 **decryptPassword** 而不是 **decryptString**。 的 **XtkSecurity_Unsafe_DecryptString** 相容性選項由postupgrade添加，並在預設情況下激活，允許您繼續使用函式。 如果要停用 **decryptString**，取消激活選項。

decryptPassword

的 **decryptPassword** 函式。 它允許您解密儲存在外部帳戶中的密碼。 請參閱 [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 的子菜單。

檔案API

對於新安裝，通過檔案API訪問資料夾時， **var**。 **sftp** 和Adobe Campaign的臨時資料夾。

對於現有客戶，檔案API無法再訪問 **會議** Adobe Campaign的資料夾。 的 **XtkSecurity_Disable_JSFileSandboxing** 相容性選項由postupgrade添加，並在預設情況下激活，允許您繼續訪問其他資料夾。 如果要限制訪問 **var**。 **sftp** 和Adobe Campaign的臨時資料夾，取消激活選項。

**修補程式**

* 已修復可能影響SMS事務性消息效能的問題。 (NEO-9812)

## 第 18.4 發行版本

### 版本 18.4.5 - 版本編號 8937{#release-18-4-5-build-8937}

2018年11月21日

**功能改進**

* 在FDA上使用MySQL運行工作流時已修復各種問題。 (NEO-11652)
* 解決了在特定情況下導致部分運送人口處於待決狀態的問題。 (NEO-11336)
* 修復了SMS自動響應的間歇性問題。 (NEO-11811)
* 在交貨中使用種子地址時已修復ID耗盡問題。 (NEO-11842)
* 在富集工作流活動中執行排序時修復了語法錯誤。 (NEO-11394)
* 已修復重新啟動IIS時可能導致Web伺服器崩潰的問題。 (NEO-10862)
* 已修復可能導致生成升級後跟蹤工作流失敗的問題(FDA - SQL)。 (NEO-11635)
* 已修復可能導致工作流清單資料丟失的問題。 (NEO-11696)
* 已解決發送推送通知時的效能問題。 (NEO-11787)
* 已修復導致網頁跟蹤無法用於&quot;com.au&quot;域(NEO-4385)的問題。
* 已修復在使用複雜工作流時可能出現的客戶端凍結問題。 (NEO-11847)
* 在選擇特定架構的元素(NEO-11682)後保存新傳遞時，已修復Oracle錯誤。
* 查詢包含帶重音字元的欄位時，已修復問題(FDA/Teradata)。 現在，外部帳戶允許您更改用於與Teradata驅動程式通信的編碼。 (NEO-11818).
* 在推送通知中以其他變數傳遞URL時，解決了跟蹤問題，這可能導致移動應用程式接收的資料格式錯誤或不正確。 (NEO-11468、NEO-11960)
* 已修復在使用帶1:N連結的值分佈時導致顯示問題的問題。 (NEO-11820)
* 已修復阻止批量負載在Teradata16上工作的問題。
* 已增加Teradata上時間戳的緩衝區大小，以避免與15.10驅動程式發生綁定問題。
* 改進了長名稱索引的管理，這可能導致錯位問題。
* 在子級死區處理(MTA)期間，共用記憶體可用時間得到改善。
* 已修復Apache（跟蹤）中的潛在死鎖。


### 版本 18.4.4 - 版本編號 8936{#release-18-4-4-build-8936}

2018年8月1日

**功能改進**

* 電子郵件存檔日誌已得到增強，這使檢查哪些電子郵件已成功傳送或通過密件抄送存檔失敗變得更加容易和清晰。 (NEO-10675)
* 已修復導致在跟蹤廣播中顯示負載平衡器IP而不是客戶IP的問題。 (NEO-11295)
* 使用FDA連接到PostgreSQL資料庫時，已修復LATIN1編碼錯誤。 (NEO-11299)
* 已修復使用 **[!UICONTROL Prepare the personalization data with a workflow]** 「交貨」選項。 (NEO-11047、NEO-11301)
* 修復了導致錯誤覆蓋傳遞屬性的隨機問題。 (NEO-11015)
* 在中使用計算欄位時修復問題 **[!UICONTROL Survey answers]** 工作流活動。 (NEO-11382)
* 使用XML中儲存的資料時修復了問題 **[!UICONTROL Survey answers]** 工作流活動。 (NEO-10816)
* 使用build 8935執行伺服器升級時已解決問題。
* 修復了在以下情況下在配置級別日誌中顯示無用錯誤的問題： **[!UICONTROL Survey answers]** 工作流活動未完全配置。
* FDATeradata:修復了SQL表中具有自動遞增欄位和索引的問題。

### 版本 18.4.3 - 版本編號 8935{#release-18-4-3-build-8935}

2018年6月22日

**功能改進**

* 已修復Microsoft邊緣和Internet Explorer的跟蹤編碼問題。 (NEO-11257)
* 已解決LINE交貨中影像連結個性化的問題。 (NEO-11077)
* 已修復導致ID序列生成機制無法正常工作的問題。 (NEO-11115)
* 修復了在使用具有整數類型協調密鑰的自定義命名空間時阻止隱私(GDPR)請求工作的問題。 (NEO-11123)
* 修復了使用 **[!UICONTROL Distribution of values]** 選項 **[!UICONTROL Query]** 工作流活動。 (NEO-10958)
* 已修復從市場營銷實例到交互實例同步提供空間時的問題。 (NEO-11162)
* 改進長名稱索引在坡道期間的管理

### 版本 18.4.2 - 版本編號 8932{#release-18-4-2-build-8932}

2018年5月22日

**功能改進**

* 已修復導致Windows Server更新無法正常工作的問題。
* 已修復 **[!UICONTROL Survey Result]** 使用XML中儲存的資料時的活動。 報告顯示不正確。 (NEO-10816)
* 修復了使用彈回郵件伺服器時inMail進程可能出現的效能問題。 (NEO-10641)
* 已修復在升級1000個以上架構時可能發生的資料庫升級問題。

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
   <td> 歐盟一般資料保護條例(GDPR)<br /> </td> 
   <td> <p>GDPR是歐盟(EU)的新隱私法，它協調並現代化將於2018年5月25日生效的資料保護要求。 GDPR 適用於所持有資料的主體居住於歐盟的 Adobe Campaign 客戶。</p> <p>除了Adobe Campaign已經提供的隱私功能（包括同意管理、資料保留設定和用戶角色）外，我們還將利用此機會作為資料處理器角色加入其他功能，以幫助您作為資料控制器就緒，滿足某些GDPR請求：</p> 
    <ul> 
     <li> <p>訪問權限：允許資料主題接收由資料控制器捕獲的個人資料的副本，可能包括儲存在Adobe Campaign的資料。</p> </li> 
     <li> <p>刪除權限：資料使用者有權擦除其資料控制器捕獲的個人資料，可能包括儲存在Adobe Campaign的資料。</p> </li> 
    </ul> 如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">詳細文件</a>以瞭解詳情。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的設定檔案<br /> </td> 
   <td> <p>Adobe Campaign現在提供活動配置檔案清單，並通過專用工作流每月更新。</p> <p>如需詳細資訊，請參閱<a href="../../platform/using/about-profiles.md#active-profiles">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
  <tr> 
   <td> Android Push連接器增強<br /> </td> 
   <td> <p>Android連接器已得到增強，可支援更高的吞吐量。 </p> <p>如需詳細資訊，請參閱<a href="../../delivery/using/configuring-the-mobile-application.md">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 現在禁用了外部實體的擴展，以防止未經身份驗證的用戶發起潛在攻擊。 (NEO-10173)
* 強化的權限，防止標準用戶更改實例配置參數，如應用程式訪問URL、LDAP設定等。 (NEO-10171)
* 已修復可通過堆棧跟蹤顯示敏感資訊的問題。 錯誤詳細資訊現在記錄在從外部網路無法訪問的位置的後端。 (NEO-10176)
* 強化的權限，以防止標準用戶查看管理員上載的文檔和/或導出的包。 (NEO-10170)

**功能改進**

* **LINE通道 — 體系結構增強**:與Adobe Campaign的所有其它通道一樣，LINE通道現在支援所有部署類型：托管、混合和內部部署。
* **序列自動生成**:ID生成機制已得到增強，以增加具有大量對象的Camping實例的壽命。

**其他變更**

* 使用命令行可以使用新模式導入包，從而允許循環依賴項（不建議使用大型包）。 有關詳細資訊，請參閱「技術演變」部分。 (NEO-8979)
* 改進了在Teradata中載入大量資料的效能，並解決了無法顯示日誌中處理資料的正確值的問題。 (NEO-10429)
* 現在，從Audience Manager導入受眾可以處理拆分檔案。 以前，只有段的最後一個檔案是由importSharedAuvience技術工作流導入的。 (NEO-10156)
* 在Windows上，市場活動伺服器預設安裝路徑已更改。 啟動64位版本安裝程式時，預設安裝路徑是： **C:\Program Files\Adobe\Adobe Campaign Classic v7** 而不是 **C:\Program Files (x86)\Adobe\Adobe Campaign Classicv7**
* 預設的MX規則已增強，以包括更多域並優化吞吐量。
* 對部署嚮導SOAP調用(xtk:serverOptions#SaveOptions)強制訪問限制。
* weka.jar過時庫已刪除，OpenSSL庫已更新以進行安全優化。
* 改進計費技術工作流，保證實例效能安全。
* 管理員設定或重置任何操作員密碼的能力已恢復。 要執行此操作，請按一下右鍵運算子，選擇 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 並設定操作員的新密碼。 我們建議操作員在首次重新連接時更改其密碼。 如需詳細資訊，請參閱[詳細文件](../../production/using/lost-password.md)以瞭解詳情。
* 為支援Adobe Target的新多租賃功能，現在可在配置選項和外部帳戶以與目標整合時，將新的&quot;at_property&quot;參數添加到URL中。 此參數的值可在Adobe Target找到，並且在對目標執行呼叫時將由市場活動使用。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 現在，您可以指定在按一下Adobe Target提供的影像時開啟的預設登錄頁。 以前，按一下該影像會導致在建立電子郵件時設定預設影像。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 已添加 **啟用SMPP跟蹤** 複選框以強制跟蹤輸出。 如需詳細資訊，請參閱[詳細文件](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)以瞭解詳情。

**技術演變**

查詢定義

queryDef已針對&quot;orderBy&quot;子句進行修改。 在更改之前，查詢表的主鍵將隱式添加到&quot;orderBy&quot;子句中。 在某些資料庫引擎（至少是postgresql）上，它會阻止索引的使用（orderBy子句的所有欄位都必須由同一索引覆蓋）。 如果您依賴於此行為，則必須在「orderBy」子句中顯式添加主鍵。

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

它將以（在18.4變化之前）的方式暗示：

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

對於非ASCII字元，「urlEncode」 JavaScript函式無法正常工作。 它已經更正，現在應用於所有Unicode字元（包括日文字元）。 如果您依賴非ASCII字元的「urlEncode」行為，則必須調整代碼。

包導入新模式

使用命令行可以使用新模式導入包，從而允許循環依賴項（不建議使用大型包）。 保留現有功能。 對於具有循環依賴項的此類包，新標誌 **-usejs** 已添加到命令行包導入中。 執行時，將像從介面執行包導入時那樣使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修補程式**

* 已修復從Adobe Campaign Standard複製到Adobe Campaign Classic的交付和跟蹤日誌時的同步問題。 (NEO-10023)
* 在快速載入操作失敗後，ETL工作流正在恢復時，已修復Teradata中錯誤和日誌表的處理問題。 現在，每次工作流恢復時，錯誤表和日誌表都會被正確刪除。 (NEO-10672)
* 已修復錯誤級別問題，以便在安裝FDA包時自動安裝Hive包(Hadoop需要)。 (NEO-10592)
* 已修復將無效域視為 **未定義** 錯誤。 (NEO-10248)
* 已修復發送android推送遞送時在deliveryLogStats表中重複日誌的問題。 (NEO-10234)
* 已修復可能導致條形碼掃描器無法讀取某些條形碼格式的問題。 (NEO-10125)
* 使用非ASCII字元時，已修復「urlEncode」 JavaScript函式的問題。 有關詳細資訊，請參閱「技術演變」部分。 (NEO-10123)
* 在Teradata資料庫上執行包含sha256函式的查詢時修復了問題。 (NEO-10119)
* 已修復在使用非常大的SalesForce表時可能在SalesForce活動中發生的工作流記憶體錯誤。 (NEO-9900)
* 已修復 **生成補碼** 選項，以在使用FDA時針對工作流活動。 (NEO-9878)
* 已修復可能導致 **已處理** 和 **成功** 使用中間來源補充時未在市場營銷實例上更新度量。 (NEO-9454)
* 在平台中總提供10k以上時的固定交互非命題規則(NEO-9352)
* 已修復在使用XML外部檔案時無法指定傳遞目標的問題。 (NEO-9312)
* 修復了在對聘用運行假設並更新命題的狀態時可能導致工作流錯誤的問題。 (NEO-9304)
* 在基於Android交付映射的屬性使用壓力規則時在交付分析期間發生的固定錯誤。 (NEO-9202)
* 在對收件人清單中可能導致效能問題的列進行排序時，已修復問題。 有關queryDef修改的詳細資訊，請參閱下面的「技術演化」部分。 (NEO-9042)
* 修復了審核電子郵件中的連結可能指向不正確的登錄URL的問題，特別是在使用Federated ID登錄類型時。 (NEO-9011)
* 已修復可能導致某些時區的報告日期選擇器中顯示錯誤日期的問題。 (NEO-9007)
* 已修復在使用FDA SQL資料庫時無法查看出站目標的問題。 (NEO-8924)
* 已修復導致MS Dynamics CRM連接器在每月前7天無法提取資料的問題。 (NEO-8803)
* 已修復分析整合錯誤，該錯誤阻止用戶包括國際字元。 (NEO-8719)
* 修復了一個問題，該問題可以在沒有適當權限的情況下啟用工作流編輯。 (NEO-8708)
* 在混合體系結構中使用消息中心時，通過HTTP解決了FDA的問題，導致連接斷開或連接丟失（超時）。 (NEO-8438)
* 負ID的增量查詢活動中發生的固定工作流錯誤。 (NEO-8229)
* 已修復可能導致在某些螢幕中顯示雙捲動條的問題。 (NEO-8208)
* 已修復導致在運行更新資料庫結構嚮導時顯示錯誤消息的問題。 PostUpgrade將對名稱超過30的索引執行更名。 請注意，對於大型表，索引替換將需要時間。 (NEO-7983)
* 修復了跟蹤日誌未從消息中心執行實例正確同步以控制實例的問題。 (NEO-7286)
* 解決了與優惠活動相關的效能問題。 (NEO-7263)
* 已修復通過FDA查詢Redshift資料庫時無法使用DaysAgo函式的問題。 (NEO-7099)
* 修復了資料管理中的回歸，該回歸阻止了在類似富集的工作流活動上建立索引。
* 已修復建立標題為@id的外部資源時可能發生的問題
* 修復了通過FTP伺服器上載壓縮檔案或在檔案名中使用通配符上載檔案時可能出現的問題。
* 已修復在建立為Campaign Standard的外部自定義資源中具有長基類型枚舉的問題。
* 已修復一個問題，即使與提供程式的連接失敗導致SMS丟失，也可能導致發送SMS。
* 已修復導致SMTP連接無限期卡住的錯誤。
* 在使用LINE映射或篩選和目標架構不同時，在消息準備期間解決了壓力類型規則問題。
