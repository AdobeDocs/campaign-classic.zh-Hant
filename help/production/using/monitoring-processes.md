---
solution: Campaign Classic
product: campaign
title: 監控流程
description: 瞭解如何監控Campaign流程
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3602'
ht-degree: 0%

---


# 監控流程{#monitoring-processes}

應用伺服器和重定向伺服器(**tracking**)可以手動或自動監控。

## 手動監視{#manual-monitoring}

前往&#x200B;**[!UICONTROL Monitoring]**，然後按一下&#x200B;**[!UICONTROL Overview]**&#x200B;連結以顯示Adobe Campaign流程監控頁面。

![](assets/d_ncs_monitoring.png)

顯示的頁面可讓您檢視連線的例項狀態，例如：

* 例項資訊：版本，名稱，資料庫引擎，已安裝的軟體包，伺服器系統指標，
* 缺少進程和執行資訊（開始日期、PID等）的清單，
* 工作流程和傳送的檢視。

監控不同促銷活動程式的其他方式，請參閱本頁[。](../../production/using/monitoring-guidelines.md)

### 日誌{#log-journal}

可以顯示與進程相關的日誌日誌。 若要這麼做，請按一下程式&#x200B;**mta**，然後按一下&#x200B;**[!UICONTROL Open the log journal]**。

![](assets/d_ncs_monitoring2.png)

### 系統指示燈{#system-indicators}

系統指示器清單使您能夠顯示與電腦相關的資訊，如其物理和虛擬記憶體、活動進程和可用磁碟空間。 Linux和Windows作業系統的指示燈不同。 前往&#x200B;**[!UICONTROL Instance Monitoring]**&#x200B;頁面，然後按一下&#x200B;**[!UICONTROL Display]**&#x200B;連結以開啟指標清單

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]** :消息中心特 **定指示符**。如需詳細資訊，請參閱[本節](../../message-center/using/monitoring-thresholds.md)。
* **[!UICONTROL Memory]** :有關物理記憶體(RAM)的資訊。

   **[!UICONTROL Current value]** :實際記憶體消耗。

   **[!UICONTROL Max Value]** :安裝的記憶體總量。

   **[!UICONTROL Available]** :可用記憶體量。

   **[!UICONTROL Warning]** :當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]** :當記憶體消耗達到總量的90%時，將顯示此指示器。

   當顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示器時，您可以將RAM新增至Adobe Campaign伺服器所在的機器，以解決此問題。 您也可以決定將Adobe Campaign伺服器安裝在專用的機器上。

* **[!UICONTROL Swap Memory]** :與與尋呼檔案匹配的虛擬記憶體相關的資訊：Windows使用的硬碟區域，就像是記憶體一樣。

   **[!UICONTROL Current value]** :實際記憶體消耗。

   **[!UICONTROL Max Value]** :記憶體總量。

   **[!UICONTROL Available]** :可用記憶體量。

   **[!UICONTROL Warning]** :當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]** :當記憶體消耗達到總量的90%時，將顯示此指示器。

   當顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示器時，您可以通過在高級Windows設定中增加交換檔案的大小來解決問題。

* **[!UICONTROL Disk XXX]** :有關機器讀取器的資訊。

   **[!UICONTROL Current value]** :實際使用的磁碟空間。

   **[!UICONTROL Max Value]** :磁碟總容量。

   **[!UICONTROL Available]** :可用磁碟空間

   **[!UICONTROL Used]** :已使用磁碟的百分比。

   **[!UICONTROL Warning]** :當可用磁碟空間達到總容量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]** :當可用磁碟空間達到總容量的90%時，將顯示此指示器。

* **[!UICONTROL Number of processes too old]** :一天以上有效的Adobe Campaign程式相關資訊。

   **[!UICONTROL Current value]** :當前活動的進程數。

   **[!UICONTROL Max Value]** :授權進程數上限(1)。

   **[!UICONTROL Alert]** :如果進程數等於1，則顯示此指示符。

   當顯示&#x200B;**[!UICONTROL Alert]**&#x200B;指示符時，可能是相關進程被SQL資料庫引擎鎖定，或者被卡在無限循環中。 Adobe Campaign提供的&#x200B;**watchdog**&#x200B;程式會自動每天重新啟動所有程式，讓您解決此問題。 不過，您也可以停止相關程式，強制重新啟動。

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]** :消息中心特 **定指示符**。如需詳細資訊，請參閱[本節](../../message-center/using/monitoring-thresholds.md)。
* **[!UICONTROL Load average (1/5/15 minutes)]** :有關負載的資訊，即在機器上運行的進程在最後一分鐘、五分鐘或十五分鐘內的使用率

   **[!UICONTROL Current value]** :機器的實際負載。

   **[!UICONTROL Max value]** :機器上進程的最大使用負載

   **[!UICONTROL Warning]** :當負載在最後一分鐘、五分鐘或十五分鐘內達到最大授權值的80%時，就會顯示此指標。

   **[!UICONTROL Alert]** :當載入達到最後一分鐘、五分鐘或十五分鐘的最大授權值90%時，就會顯示此指標。

* **[!UICONTROL Memory]** :有關物理記憶體(RAM)的資訊。

   **[!UICONTROL Current value]** :實際記憶體消耗。

   **[!UICONTROL Max Value]** :安裝的記憶體總量。

   **[!UICONTROL Available]** :可用記憶體量。

   **[!UICONTROL Warning]** :當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]** :當記憶體消耗達到總量的90%時，將顯示此指示器。

   當顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示器時，您可以將RAM新增至Adobe Campaign伺服器所在的機器，以解決此問題。 您也可以決定將Adobe Campaign伺服器安裝在專用的機器上。

* **[!UICONTROL Swap Memory]** :與與尋呼檔案匹配的虛擬記憶體相關的資訊：Windows使用的硬碟區域，就像是記憶體一樣。

   **[!UICONTROL Current value]** :實際記憶體消耗。

   **[!UICONTROL Max Value]** :記憶體總量。

   **[!UICONTROL Available]** :可用記憶體量。

   **[!UICONTROL Warning]** :當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]** :當記憶體消耗達到總量的90%時，將顯示此指示器。

   當顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指示符時，可以通過增大交換檔案的大小來解決問題。

* **[!UICONTROL Core Files]** :與Adobe Campaign程式當機後產生的檔案相關的資訊。這些檔案可讓您診斷當機的原因。

   **[!UICONTROL Current Value]** :現有檔案數。

   **[!UICONTROL Max Value]** :授權檔案的最大數目(1)。

   **[!UICONTROL Warning]** :當檔案數量接近1時，就會顯示此指標。

   **[!UICONTROL Alert]** :當檔案數等於1時，將顯示此指示器。

   當因當機而遺失程式時，程式清單上會以紅色顯示，並由Adobe Campaign提供的&#x200B;**watchdog**&#x200B;程式自動重新啟動。

* **[!UICONTROL Number of shared memory segments]** :與所有Adobe Campaign程式共用的記憶體區段相關的資訊。

   **[!UICONTROL Current value]** :當前正在使用的記憶體段數。

   **[!UICONTROL Max Value]** :授權的最大記憶體段數(2)。

   **[!UICONTROL Warning]** :當記憶體段數達到1時，將顯示此指示器。

   **[!UICONTROL Alert]** :當記憶體段數達到2時，將顯示此指示器。

* **[!UICONTROL Number of processes too old]** :有關活動超過一天的流程的資訊。

   **[!UICONTROL Current value]** :當前活動的進程數。

   **[!UICONTROL Max Value]** :授權程式的最大數量。

   **[!UICONTROL Warning]** :當進程數達到授權閾值的80%時，將顯示此指示器。

   **[!UICONTROL Alert]** :當進程數達到授權閾值的90%時，將顯示此指示器。

* **[!UICONTROL File Handles]** :有關檔案描述符的資訊，即每個進程開啟的檔案數。

   **[!UICONTROL Current value]** :檔案描述符的當前數。

   **[!UICONTROL Max Value]** :作業系統授權的檔案描述符的最大數量。

   **[!UICONTROL Warning]** :當授權檔案描述符數達到80%閾值時，將顯示此指示器。

   **[!UICONTROL Alert]** :當授權檔案描述符數達到90%閾值時，將顯示此指示器。

* **[!UICONTROL Processes]** :有關機器進程的資訊。

   **[!UICONTROL Current value]** :當前活動的進程數。

   **[!UICONTROL Max Value]** :授權程式的最大數量。

   **[!UICONTROL Active Processes]** :活動進程數。

   **[!UICONTROL Inactive Processes]** :非活動進程數。

   **[!UICONTROL Warning]** :當授權進程數達到80%閾值時，將顯示此指示器。

   **[!UICONTROL Alert]** :當授權進程數達到90%閾值時，將顯示此指示器。

* **[!UICONTROL Zombie Processes]** :與已停止但仍具有進程標識符(PID)且在進程表中仍可見的進程相關的資訊。

   **[!UICONTROL Current value]** :當前活動的僵屍進程數。

   **[!UICONTROL Max Value]** :授權僵屍進程的最大數量(2)。

   **[!UICONTROL Warning]** :當僵屍進程數接近2時，將顯示此指示器。

   **[!UICONTROL Alert]** 當僵屍進程數達到2時，將顯示此指示器。

#### 自訂指標{#customized-indicators}

Adobe Campaign可讓您自訂指標。 操作步驟：

1. 建立&#x200B;**.sh**&#x200B;檔案，並將它命名為&#x200B;**[!UICONTROL cust_indicators.sh]**。
1. 將自訂指標新增至此檔案。 例如：

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   或

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. 將檔案放在&#x200B;**[!UICONTROL usr/local/neolane/nl6]**&#x200B;資料夾中。

此檔案將由Adobe Campaign呼叫。

## SMTP報告{#smtp-reports}

SMTP傳送監控報表已整合至Adobe Campaign平台。 您可透過主控台或使用Web存取來存取。

這些報告按域顯示SMTP傳送統計資訊和SMTP錯誤。

若要存取這些檔案，營運商必須擁有「管理」權限。

它們被分組在&#x200B;**Monitoring** > &#39;SMTP Monitoring&#39;下。

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* 只有在激活了電子郵件通道後，才能獲得與SMTP監視相關的資訊。
>* **[!UICONTROL SMTP sending statistics]**&#x200B;僅在實例上啟動了統計伺服器時提供。
>



### SMTP發送統計資訊{#smtp-sending-statistics}

**[!UICONTROL SMTP sending statistics]**&#x200B;報表可讓您控制伺服器活動。 它顯示每個匹配項的綜合。

![](assets/smtp_stats_report.png)

此報表的指標清單顯示在圖表下方。

1. 已發送的消息總數。
1. 
   * 藍線：已準備好發送的消息已進入Shaper，即發送SMTP（與傳入資料一致）之前的最後一個階段。

   * 綠線：消息成功發送（與傳出資料一致）。

   * 紅線：由Shaper放棄的消息返回到&#x200B;**mta**（與此恢復時拒絕的資料一致）。

   這些值以每小時的消息數表示。

1. 表示兩個Shaper隊列：

   * 藍色曲線：活動消息的隊列。 這些訊息會盡快傳送。

   * Kaki曲線：「延遲」隊列。 由於頻寬限制或沒有可用的目標連接，這些消息暫時無法返回。 重試次數每5秒、10秒、20秒、40秒、2分鐘等。 對於已定義的&#x200B;**MaxAgeSec**&#x200B;放棄前的時間。

1. 此圖表顯示已放棄消息的詳細資訊（第2個圖表上的紅色曲線）:與發送失敗（紅色）的消息相比，它顯示未重試的消息比例(mauve)。 這可讓您檢視由於統計伺服器的限制（調節）或因遠端伺服器不可用而未在授權期間內處理的訊息比例。
1. 開啟或正在開啟SMTP連接。
1. **mtachild**&#x200B;的估計數。

>[!NOTE]
>
>此報告與「電子郵件流量Shaper」元件的狀態相關。

### 每個域的SMTP錯誤{#smtp-errors-per-domain}

此報表可讓您檢視指定時段內的傳送錯誤，並依網域劃分。

>[!NOTE]
>
>**serverConf.xml**&#x200B;檔案的&#x200B;**minConnectionsToLog**、**minErrorsToLog**&#x200B;和&#x200B;**minMessagesToLog**&#x200B;選項定義了將連接統計資訊考慮到上述閾值。

![](assets/smtp_error_report.png)

此報告的指標清單如下表所示。

* **Domain**&#x200B;欄包含傳送訊息的網域名稱（例如，yahoo.fr的實際網域名稱yahoo.com）,
* **Cnx**&#x200B;列顯示此域開啟的SMTP連接數。
* **Sent**&#x200B;欄對應傳送至此網域的訊息數量，
* **Volume**&#x200B;列顯示已嘗試發送到此域的消息量（近似值）,
* **Errors**&#x200B;欄會顯示此網域在該時段內錯誤的卷指示符，
* **Last response**&#x200B;列顯示該域的最後一條SMTP響應消息，
* **Date**&#x200B;列顯示該域上次收到的SMTP響應的日期。

>[!NOTE]
>
>根據在&#x200B;**[!UICONTROL Period]**&#x200B;欄位中選擇的期間計算顯示在&#x200B;**Cnx**、**Sent**&#x200B;和&#x200B;**Volume**&#x200B;列中的值。

按一下網域名稱以檢視其錯誤。

它們依PublicId分類：此識別碼對應於路由器後方數個Adobe Campaign mtas所共用的IP位址。 統計伺服器使用此標識符來儲存此起始點和目標伺服器之間的連接和傳送統計資訊。

![](assets/smtp_error_report_details.png)

**[!UICONTROL Owner of domain]**&#x200B;欄位可讓您將不同的網域名稱群組在相同的標籤下。 在初始報表檢視中，所有MX網域名稱都會與此擁有者相關聯。

按一下PublicId識別碼以檢視詳細資訊。

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>錯誤百分比由兩個圖表表示。 第一個是黑色背景上的水準進度列。 第二張圖表是按時間順序排列的。 所選時段被分成12個時間間隔，每個時間間隔由垂直進度條表示。 在這兩種表示法中，如果未檢測到任何錯誤，則條為黑色。 條的顏色取決於遇到的錯誤百分比（黃色、橙色，最後是紅色）。 顏色灰色表示未發現顯著的資料量。 將游標放在圖表上，可顯示錯誤的確切百分比。

>[!NOTE]
>
>有關SMTP錯誤以及在Adobe Campaign中管理這些錯誤的詳細資訊，請參閱[本節](../../installation/using/email-deliverability.md)。

## 帳單報表{#billing-report}

**[!UICONTROL Billing]**&#x200B;技術工作流程會以電子郵件將系統活動報表傳送給「帳單」營運商。 預設情況下每月25日觸發。

技術工作流程位於下列節點的子資料夾中：**管理** > **生產** > **技術工作流程**。

![](assets/billing.png)

每月25日開始工作後，您的帳單營運商會在其收件匣中收到下列報表。

![](assets/billing_2.png)

下列量度可用於追蹤您的傳送：

* **[!UICONTROL Start date]** :傳送的開始日期。請注意，此日期可早於報表的「起始」日期。
* **[!UICONTROL Label]** :傳送的標籤。要傳送的訊息少於100個的傳送會被視為過小，因此會依開始日期匯總，此時標籤會顯示匯總的數目，例如：[匯總3個小型遞送]。
* **[!UICONTROL Total volume]** :傳送時傳送的位元組總量。
* **[!UICONTROL Avg volume]** :傳輸的平均位元組數。這是下列公式&#x200B;**（總體量／消息）**&#x200B;的結果，它是&#x200B;**[!UICONTROL Multiplier]**&#x200B;度量的計算基礎。
* **[!UICONTROL Messages]** :已發送的消息數。這包括成功傳送和重試的訊息（在從已連絡的伺服器收到彈回訊息後）。
* **[!UICONTROL Multiplier (x)]** :從消息的平均體積推導出乘法器的值。
* **[!UICONTROL Count]** :消息和乘法器的乘法結果。

## 自動監控{#automatic-monitoring}

Adobe Campaign提供數種自動監控方法，如下所示。

### 命令行{#command-line}

命令

**nlserver監視器**

可讓您在Adobe Campaign模組和系統上列出一組指標。

它以易於處理的XML格式產生輸出。

此命令也可以與&#x200B;**-missing**&#x200B;參數一起運行，該參數列出配置檔案表示應執行時此實例中缺少的進程。

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### 伺服器發佈的資訊{#information-published-by-the-server}

#### /r/test {#r-test}

**http(s)://`<application>`/r/test**&#x200B;頁用於測試重定向伺服器。 我們建議使用相同的方法來測試用於追蹤的前端伺服器。 此頁還可用於測試載入調度程式。

它以XML格式顯示如下行：

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**頻率**:此測試不會使用任何負載，因此可以經常執行（例如每秒一次）。

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

此&#x200B;**http(s)://`<Application server url>`/nl/jsp/ping.jsp**&#x200B;頁的操作方式與其網路對應項相同：它通過apache/tomcat/web模組／資料庫測試一個完整的查詢並上傳到客戶端。 如果一切正常運作，則會傳回「正常」。 我們建議在具有資料庫存取權的機器上執行此測試（例如，mta和調查）。

**用法**:必須將與運算子登入相關聯的作業Token傳遞為引數，才能遠端登入(請參閱透過Adobe Campaign指令碼自動監 [控中的提示](#automatic-monitoring-via-adobe-campaign-scripts))。

例如：

![](assets/ncs_monitoring_ping.png)

運算元名稱和登入必須先前在Adobe Campaign用戶端主控台中設定資料庫權限。

![](assets/ncs_operators_rights_01.png)

**頻率**:這個測試使用的頻寬很少。因此，它可以很常運行，但每分鐘不超過一次。

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

這是測試，以檢查營運商是否可透過網頁存取Adobe Campaign伺服器；與透過用戶端主控台功能表存取的網頁相同。 您可以從監視工具（Tivoli、Nagios等）呼叫此頁面。

![](assets/ncs_monitoring_web.png)

**用法**:與運算子登入相關聯的作業Token，可讓您連線至例項時，需要將其用作引數(請參閱「透過Adobe Campaign指令碼自動監 [控」中的提示](#automatic-monitoring-via-adobe-campaign-scripts))。

運算子及其登入必須先前在Adobe Campaign用戶端主控台中設定，並具備適當的資料庫權限和限制。

**頻率**:這是完整的伺服器測試，不需要經常執行（例如，每10分鐘執行一次）。

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

此&#x200B;**jsp**&#x200B;代表Adobe Campaign應用程式API的登入點。 因此，它可以提供應用程式的詳細監控。 它也可用來監控Adobe Campaign網站服務。 它用於我們的監控指令碼中，但請注意，它僅用於超級用戶。

### 根據部署類型進行監控{#monitoring-based-on-deployment-types}

Adobe Campaign可啟用各種部署設定（如需詳細資訊，請參閱[本節](../../installation/using/hosting-models.md)）。 本節詳述根據安裝類型應用的各種自動監控技術。

<table> 
 <thead> 
  <tr> 
   <th> 部署類型 </th> 
   <th> 監控 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 獨立 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/monitor.</span> jspon the Adobe Campaign伺服器</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 標準 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/ping.</span> jspon前端伺服器</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.</span> jspon應用程式伺服器</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 企業 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/ping.</span> jspon前端伺服器</p> </li> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/monitor.</span> jspon應用程式伺服器</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 中部採購 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.</span> jspon應用程式伺服器</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 透過Adobe Campaign指令碼自動監控{#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign可提供例項監控工具(netreport)，讓您透過電子郵件傳送有關偵測異常的報表。

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>此工具可用來監控您的例項，但Adobe Campaign不支援。 如需詳細資訊，請連絡您的促銷活動管理員。

### 所需元素{#required-elements}

自動監控需要下列預安裝預防措施：

* 您必須有&#x200B;**netreport.tgz**（Linux安裝）或&#x200B;**netreport.zip**（Windows安裝）檔案，
* 我們強烈建議您不要在要監控的機器上安裝監控，
* 它必須安裝在具有JRE或JDK的電腦上，
* 在Linux中，要監視的電腦必須具有&#x200B;**bc**&#x200B;軟體包。 如需詳細資訊，請參閱[本章節](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages)。

### 安裝過程{#installation-procedure}

安裝過程如下：

1. 在控制台中，如有必要，請建立新的操作符（「監視」用戶已存在），但不指派任何權限。
1. 運行存檔提取。
1. 閱讀&#x200B;**readme**&#x200B;檔案。
1. 更新&#x200B;**netconf.xml**&#x200B;配置檔案。
1. 更新&#x200B;**netreport.bat**(Windows)或&#x200B;**netreport.sh**(Linux)檔案。

### 配置netconf.xml檔案{#configuring-the-netconf-xml-file}

XML配置檔案包含以下元素：

* [「屬性」元素](#properties--element)
* [「例項」元素](#instance--element)
* [「主機」元素](#host--element)
* [子元素](#sub-elements)

以下是配置示例：

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>您可以通過在&#x200B;**netconf.xml**&#x200B;檔案中添加尾碼來指定各種配置，例如&#x200B;**netconf-dev.xml**、**netconf-prod.xml**&#x200B;等。 然後，通過添加&#x200B;**$JAVA_HOME/bin/java netreport dev**&#x200B;或&#x200B;**@%JAVA_HOME%binjava netreport prod&lt;a7，指定用於在** netreport.bat **或** netreport.sh **檔案中執行netreport的配置/>。**

>[!IMPORTANT]
>
>要使&#x200B;**monitoring**&#x200B;運算子工作，執行Netreport的電腦必須處於&#x200B;**sessionTokenOnly**&#x200B;模式的安全區域中。 如果未為此運算子指定受信任的IP遮色片，則安全區域也必須處於&#x200B;**allowEmptyPassword**&#x200B;和&#x200B;**allowUserPassword**&#x200B;模式。

#### 「屬性」元素{#properties--element}

此元素用於填入電子郵件的設定，即

* **mailServer**:用於發送電子郵件的SMTP伺服器(例如：smtp.domain.net)。
* **mailFrom**:報表傳送者的電子郵件地址(例如：monitoring@domain.net)。
* **recipientList**:監視收件者的電子郵件地址清單。地址必須以逗號分隔（無空格）。
* 「**night**」模式（可選）用於避免在指定時段之間發送電子郵件。 相反，會整合資料，並在結束時間（預設為7:00）後傳送有關夜間活動的電子郵件。
* **buildRange**&#x200B;子元素（可選）可讓您指定最小和最大組建編號。 對於內部版本號不在此範圍內的所有電腦，都將生成錯誤

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* 您可以在&#x200B;**properties**&#x200B;元素中新增&#x200B;**`<sla>`**（選用）子元素。 每次執行Netreport時，都會產生記錄檔。 檔案的名稱包含設定名稱以及日期和時間，例如&#x200B;**dev_06_12_13_16_47_05.tmp**。 檔案包含下列資訊：例項名稱、機器名稱、嚴重性等級（0到3，從最不重要到最關鍵）、日期（時間戳格式）、查詢與回應之間經過的時間（以毫秒為單位）、使用的服務(http、ncs、ncsex、redir)。 這些資訊會以每項服務結束時的表格標籤和分行分隔。

>[!NOTE]
>
>**persistHtmlFile**&#x200B;屬性，在&#x200B;**`<property>`**&#x200B;元素上的值為&quot;true&quot;，用於在檔案&#x200B;**netreport.md**&#x200B;中記錄最新的監控狀態。 此檔案保存在安裝目錄中。

#### &#39;Instance&#39;元素{#instance--element}

此元素可讓您將數部電腦（主機）重新群組至相同的例項。 實例名稱會出現在監控電子郵件的第一部分。 您可以按一下例項名稱，以存取每部機器的詳細資訊。

```
instance name="instanceName" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **名稱**:會出現在電子郵件第一部分的例項名稱。
* **recipientList** （選用）:可讓您透過電子郵件傳送有關特定例項的監控報表。

#### 「Host」元素{#host--element}

此元素配置主機上給定伺服器的監視，即：

* **名稱**:要監視的電腦的名稱。
* **alias** （可選）:被監視電腦的名稱，因為它將顯示在報告中。
* **sessionToken**:透過授權的作業Token提供登入驗證。

   若要設定作業Token，請在Adobe Campaign主控台中選取&#x200B;**monitoring**&#x200B;運算子。 在&#x200B;**存取權限**&#x200B;標籤中，指定授權監控此例項的電腦的IP位址。 然後，您就可以使用&#x200B;**monitoring**&#x200B;識別碼從這些電腦連接到監視頁面，而無需指定密碼。

   ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** （可選）:可讓您依嚴重性等級來排序錯誤。可能的值為&#39;0&#39;（顯示所有層級）、&#39;1&#39;（僅顯示高錯誤和嚴重錯誤）和&#39;2&#39;（僅顯示嚴重錯誤）。 如果未提供此屬性，則會顯示所有錯誤級別。
* **filter** (optional):可讓您排除某些工作流程錯誤， **例如filter=&quot;wkf;wkf1&quot;**。工作流程標籤必須以分號分隔。

#### 子元素{#sub-elements}

* **tcp**:檢查伺服器是否處於開啟或關閉狀態。您必須輸入埠號。
* **http**:檢查Web伺服器是否存在（應用程式伺服器是否工作）。
* **ncs**:檢查在「instance」屬性中輸入的實例（工作流錯誤、記憶體使用情況等）上的進程。**includead**（必備）屬性提供顯示失效進程（&#39;true&#39;或&#39;false&#39;值）的選項。
* **redir**:檢查追蹤。

在大多數情況下，只能保留&#x200B;**ncs**&#x200B;和&#x200B;**redir**&#x200B;子元素。

在任何情況下，某些節點都可以在子元素中過載（例如，節點&#x200B;**port=75** ，以使用於http、ncs或redir連接的埠過載）:

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

在&#x200B;**ncs**、**redir**&#x200B;和&#x200B;**http**&#x200B;子元素中，您可以新增&#x200B;**isSecure**&#x200B;屬性（可選）以選擇是否使用https通訊協定（&#39;true&#39;或&#39;false&#39;值）。 如果未提供此屬性，則使用http協定。

### 配置netreport.bat或netreport.sh檔案{#configuring-the-netreport-bat-or-netreport-sh--file}

要配置它，請編輯此檔案並指明JRE或JDK安裝在哪個目錄中。

### 啟動監視{#launching-monitoring}

要啟動監視，請通過指令碼以定期間隔執行&#x200B;**netreport.bat**&#x200B;或&#x200B;**netreport.sh**&#x200B;檔案。 報表會在第一次執行後傳送，然後僅在狀態變更時傳送。

### 測試監視{#testing-monitoring}

要測試監視，請執行&#x200B;**netreport.bat**&#x200B;或&#x200B;**netreport.sh**&#x200B;檔案。

電子郵件會傳送給&#x200B;**netconf.xml**&#x200B;檔案的&#x200B;**recipientList**&#x200B;中所指定的收件者。
