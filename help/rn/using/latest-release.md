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
source-git-commit: cb55216e75559e1ce7eefa24d2302fe2c2224d40
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 1%

---


# 最新版本{#latest-release}

[建立升級](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) |控 [制面板版本](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) |文 [件更新](../../rn/using/documentation-updates.md) |舊 [版](../../rn/using/release--20-1.md) |已過 [時的功能](../../rn/using/deprecated-features.md)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>一般可用性</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>發行候選人</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>不再提供</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>已過時</strong></td> 
  </tr> 
   <tr> 
   <td>提供最新的穩定版本。 在生產環境中經過驗證。<br> </td>
   <td>經Adobe驗證的建置。 等待生產校對。<br> </td>
   <td>更新的版本已修正錯誤。 需要更新。<br> </td>
   <td>包含已知的回歸。 更新是必備的。<br> </td>
  </tr> 
 </tbody> 
</table>

最 **後一個穩定版** 本是9032(3a9dc9c)。 按一 [下](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) 版本20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_2020年6月8日_

**新增功能?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>支援表情符號</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>在Campaign中設計訊息時，您現在可以使用專用按鈕，輕鬆將表情符號插入訊息內文。 您也可以在電子郵件主旨行中新增這些主題。 您可以自訂介面中可用表情的清單。</p>
    <p>如需新增表情符號的詳細資訊，請參閱詳 <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">細檔案</a>。 瞭解如何在本節中自訂 <a href="../../delivery/using/customizing-emoticon-list.md">表情清單</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA連接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您現在可以將Campaign例項連線至Azure Synapse外部資料庫。 此連線是透過新外部帳戶管理。</p>
    <p>Azure Synapse僅適用於混合式和內部部署環境。 如需詳細資訊，請參閱<a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">詳細文件</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>泰國和巴西隱私權法</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>泰國的個人資料保護法(PDPA)是新的隱私權法，協調並現代化泰國的資料保護要求。 </p>
   <p>巴西的Lei Geral de Proteção de Dados(LGPD)將於8月16日對巴西所有收集或處理個人資料的公司生效。</p>
   <p>這些規定適用於持有這些國家／地區之資料主體資料的Adobe Campaign客戶。 除了Campaign中已提供的隱私權功能（包括許可管理、資料保留設定和使用者角色）外，我們還將利用此機會加入其他功能，以協助您做好PDPA和LGPD的準備：</p>
   <ul> 
     <li><p>存取權與刪除權： 我們運用了GDPR和CCPA新增的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">詳細內容</a></p></li> 
     <li> <p>使用促銷活動介面或API建立隱私權要求時，您現在會選取規 <strong>則類型</strong> : PDPA、LGPD、GDPR、CCPA。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">詳細內容</a>。</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 已改善所有客戶預設會啟用電子郵件中追蹤連結的安全性。 另外還提供增強的安全性功能，可聯絡客戶服務。 有關非托管客戶啟用此功能的詳細資訊和步驟，請參閱「安全性與隱私權」核 [對清單](https://helpx.adobe.com/campaign/kb/acc-security.html)。 (NEO-24232)

* 為了最佳化安全性，用於產生檔案名稱的MD5雜湊演算法已增強沙256，以用於公開檔案上傳。 (NEO-17044)

* 為了增強XSS攻擊的安全性，在執行鏡像頁面時會禁用客戶端指令碼。 (NEO-17987)

* 修正「隱私權要求清除」 **** 技術工作流程無法刪除協調資料的問題。 (NEO-25168、NEO-21004)

* 修正「檔案傳輸 **** 」活動導致SFTP金鑰驗證無法在Debian 9上運作的問題。 (NEO-23183)

**相容性增強功能**

促銷活動現在支援下列系統：
* 作業系統： 德比亞10
* RDBMS: Oracle 18c和Oracle 19c
* FDA: Azure突觸分析

進一步瞭解促銷活 [動相容性矩陣](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

**改進**

* 交易式訊息已改善，提供更佳的使用者體驗。 您現在可以取消發佈事務性消息模板，該模板會從執行實例中刪除該模板。 [進一步瞭解](../../message-center/using/template-unpublication.md)。

* 有新的選項可用來設定傳送包含影像或附件的電子郵件時的限制。 這些防護措施可以避免效能問題，這對於事務性消息傳遞特別有用。 [詳細內容](../../installation/using/configuring-campaign-options.md#delivery)

* 新的「 **在資料庫中準備交付部件** 」選項允許直接在資料庫中執行交付準備，這可顯著加快分析。 此選項僅適用於特定配置。 [進一步瞭解](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)。 (NEO-23886)

* Microsoft Dynamics的 [CRM Connector活動](../../workflow/using/crm-connector.md) ，其效能已改善。 (NEO-13303、NEO-12710)

* 已增加共用記憶體版本。

   >[!WARNING]
   >
   >執行升級後，此項改進需要額外的步驟。 請參閱下 **面的「技術** 演變」一節。

* 清除工作流程已增強。 所有已刪除工作流程的孤立工作表現在也會由清除工作流程自動刪除。 [進一步瞭解](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)。

* 使用iOS HTTP2連接器的iOS行動應用程式憑證現在會在傳送推播通知之前進行驗證，因此可避免傳送因過期憑證而失敗。

* HTTP代理連線的管理已改善。 [進一步瞭解](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)。

**其他變更**

* 舊版SMS連接器現已過時。 請參閱「已過時 [的功能」頁](../../rn/using/deprecated-features.md)。

* 您無法再使用自己的Litmus帳戶來布建和使用Adobe Campaign中的收件匣轉換。 [進一步瞭解](../../delivery/using/inbox-rendering.md)。

* 為了更好地區分視圖和資料夾，視圖名稱的顏色已從深藍色更改為深藍色。 [詳細內容](../../platform/using/access-management.md#about-views)

* Campaign Classic現在可以連線至英國、印度和加拿大地區代管的Microsoft Dynamics CRM帳戶。 這適用於Office 365和內部部署(Dynamics 2015)部署類型。

* Campaign現在會執行TLS驗證，以檢查伺服器的主機名稱是否符合所提供憑證中的主機名稱。

* 「傳送與追蹤」統計資料表格現在會針對SMS頻道在每次傳送時顯示一個項目，而非每個傳送收件者顯示一個項目。

* 在記錄檔中新增錯誤訊息，以在下載的檔案大於磁碟空間時警告使用者。

* Snowflake連接器現在提供下列功能： MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo。

**技術變革**

此新建版本會更新共用記憶體，並需要執行升級的其他步驟。 身為促銷活動管理員，您需要移除記憶體區段。 這些步驟是必備的，因為舊段將阻止nlserver/nlsrvmod啟動。

在Windows上，需要重新啟動系統。

在Debian/CentOs上，需要刪除共用記憶體。 以下是步驟：

在升級之前，您需要遵循下列步驟：

1. 停止apache2（CentOS上的http2）服務（如果服務正在運行）。
1. 停止運行nlserver（舊版組建的nlserver6）服務。

升級後：

1. 如果版本早於當 **前版本** ，請使用ipcrm命令刪除共用記憶體。
1. 如果nlserver服務正在運行，請啟動該服務。
1. 啟動apache2服務（如果正在運行）。

以下是Debian的命令行：

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop
```

```
for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done
```

```
for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done
```

```
for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done
```

```
for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done
```

```
/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

本頁提供Linux的示 [例](../../configuration/using/additional-parameters.md#redirection-server-configuration)。

**修補程式**

* 修正清除工作流程記錄檔中的次要回歸。
* 修正了剖析WSDL檔案時 **工作流程載入(SOAP)** 活動的問題。
* 修正使用「調查」活動升級許多工作流程以有效處理大量工作流程時 **發生錯誤** 。
* 已修正處理來自增強MTA的inMail訊息時的間歇性連線問題。 (NEO-20380)
* 修正當HTML中以100%寬度顯示影像時，無法正確顯示熱點按百分比的問題。 (NEO-23203)
* 修正無法將傳送的條件內容完全顯示在熱門點按報表中的問題。 (NEO-18729)
* 修正當繼續工作流程傳送循環傳送時，跳過目標核准步驟的問題。 (NEO-18166)
* 修正修正工作流程中 **錯誤後，「重新開始訊息準備** 」按鈕無法繼續傳送的問題。 (NEO-13488)
* 修正在加速階段中，目標收件人包含日文電子郵件格式的收件者時，可能導致中端來源補充模式傳送失敗的問題。 (NEO-23846)
* 修正雪花連接器的時區轉換問題(NEO-20105)
* 修正使用FTP over SSL的外部帳戶的問題。 (NEO-20498)
* 修正無法在「行」傳送中顯示影像的問題。 (NEO-23207)
* 修正發佈選件時造成錯誤的問題。 (NEO-23312)
* 修正推播通知的問題，即使憑證已過期，測試連線仍可在行動應用程式中運作。 (NEO-22991)
* 已修正在高頻率傳送時，可能會影響推播通知的問題。 (NEO-20516)
* 修正即使追蹤記錄未包含重複項目，追蹤資料仍會包含重複項目的問題。 (NEO-20040)
* 修正追蹤伺服器通訊失敗後，傳送重複交易電子郵件的問題。 (NEO-23640)
* 修正從追蹤URL重新導向時刪除編碼參數值的問題。 (NEO-25637)
* 修正比較浮點數字時，查詢無法運作的問題。 (NEO-23243)
* 修正「修改者」欄內容在重新啟 **動工作流程後無法顯示** 的問題。 (NEO-23035)
* 修正從第二個容器下載記錄檔時，追蹤技術工作流程失敗的問題。 (NEO-23159)
* 修正執行Enrichment活動時，工作流程可能會失敗 **的問題** 。 (NEO-17338)
* 已在重複資料消除工作流活 **動的** 「雙值」(Doubles)中添加了一個檢查， **** 以保留欄位，以防止輸入空值或負值。
* 已從循環 **性促銷活動移除** 「排程器」精靈，以避免提及數小時和數分鐘。 只考慮日期。
* 修正透過「指令碼工作流程」活動中的「依指令碼計算」 **選項建立傳送時** ，其他儲存欄位 **的問題** 。 (NEO-20609)
* 修正無法在資料庫清除工作中刪除Ghost工作流程的問題。
* 修正帳單(作用中描述 **檔)技術工作流程失敗** 的問題。 (NEO-19777)
* 修正測試acsDefaultAccount外部帳戶連線時的問題。 (NEO-23433)
* 修正無法在具有Hadoop表的多列的主鍵上建立模式擴展的問題。 (NEO-17390)
* 修正「載入(SOAP) **」活動中** ，無法從URL載入WSDL檔案的問題。 (NEO-16924)
* 修正當多個作用中工作流程伺服器負載平衡時，無法 **透過主控台執行** 「無條件」停止的問題。 (NEO-19556)
* 修正導致清除工作流程當機的回歸。
* 修正在執行例項上發佈範本時可能發生的問題。
* 修正collectPrivacyRequests技術工作流程無法執行的問題。 (NEO-20513、NEO-25169)
* 修正在更新至9080後嘗試連線至Audience Manager時可能發生的問題。 (NEO-20511、NEO-25167)
* 修正匯出PDF或XLS格式報表時可能發生的問題。 (NEO-20982、NEO-23493、NEO-23348)
* 修正傳送清單後，傳送清單中可能顯示兩次的問題。
* 修正傳送準備問題，當傳送設定設為透過中間來源傳送傳送時，可能會發生此問題。
* 修正按一下「行」訊息內的Web應用程式連結時，可能顯示錯誤訊息的問題。
* 修正Microsoft Dynamics CRM無法擷取所有實體的問題。 (NEO-24528)
* 修正執行清除工作流程後 **刪除「增量查詢** 」活動歷史記錄的問題。
* 修正建立NmsMidSourcing_LastBroadLog_&lt;InternalName>選項遺失的中間採購外部帳戶問題
