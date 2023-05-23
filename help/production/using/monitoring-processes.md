---
product: campaign
title: 監控流程
description: 瞭解如何監控市場活動流程
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '3598'
ht-degree: 0%

---

# 監控流程{#monitoring-processes}


應用程式伺服器和重定向伺服器(**跟蹤**)可以手動或自動監視。

## 手動監控 {#manual-monitoring}

要訪問Adobe Campaign進程監視頁面，請瀏覽至 **[!UICONTROL Monitoring]** ，然後按一下 **[!UICONTROL Overview]** 的子菜單。

![](assets/d_ncs_monitoring.png)

顯示的頁面允許您查看連接的實例的狀態，即：

* 實例資訊：版本，名稱，資料庫引擎，已安裝的軟體包，伺服器系統指示符，
* 缺少的進程和執行資訊清單（開始日期、PID等）,
* 工作流和交貨的視圖。

下面介紹了監測活動流程的其他方法 [此頁](../../production/using/monitoring-guidelines.md)。

### 日誌日誌 {#log-journal}

要顯示與進程相關的日誌日誌，請按一下該進程， **門** 例如，然後選擇 **[!UICONTROL Open the log journal]** 。

![](assets/d_ncs_monitoring2.png)

### 系統指示器 {#system-indicators}

瀏覽到系統指示器清單以顯示有關電腦的資訊，如物理和虛擬記憶體、活動進程和可用磁碟空間。 Linux和Windows作業系統的指示器不同。 轉到 **[!UICONTROL Instance Monitoring]** 的 **[!UICONTROL Display]** 連結以開啟指示器清單。

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]**:指示符 **消息中心**。 [了解更多](../../message-center/using/additional-configurations.md#monitoring-thresholds)

* **[!UICONTROL Memory]**:有關物理記憶體(RAM)的資訊。

   **[!UICONTROL Current value]**:當前記憶體消耗。

   **[!UICONTROL Max Value]**:已安裝的記憶體總量。

   **[!UICONTROL Available]**:可用記憶體量。

   **[!UICONTROL Warning]**:當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]**:當記憶體消耗達到總量的90%時，將顯示此指示器。

   當 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 顯示指示器，您可以通過向安裝Adobe Campaign伺服器的電腦添加RAM來解決此問題。 您還可以決定在專用電腦上安裝Adobe Campaign伺服器。

* **[!UICONTROL Swap Memory]**:與與分頁檔案匹配的虛擬記憶體相關的資訊：Windows使用的硬碟上的一個區域，就好像它是RAM。

   **[!UICONTROL Current value]**:實際記憶體消耗。

   **[!UICONTROL Max Value]**:記憶體總量。

   **[!UICONTROL Available]**:可用記憶體量。

   **[!UICONTROL Warning]**:當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]**:當記憶體消耗達到總量的90%時，將顯示此指示器。

   當 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 指示器顯示，您可以通過在高級Windows設定中增加exchange檔案的大小來解決此問題。

* **[!UICONTROL Disk XXX]**:有關機器讀取器的資訊。

   **[!UICONTROL Current value]**:實際使用的磁碟空間。

   **[!UICONTROL Max Value]**:磁碟總容量。

   **[!UICONTROL Available]**:磁碟空間可用。

   **[!UICONTROL Used]**:已用磁碟的百分比。

   **[!UICONTROL Warning]**:當可用磁碟空間達到總容量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]**:當可用磁碟空間達到總容量的90%時，將顯示此指示燈。

* **[!UICONTROL Number of processes too old]**:關於Adobe Campaign進程的資訊，這些進程已活動超過一天。

   **[!UICONTROL Current value]**:當前活動的進程數。

   **[!UICONTROL Max Value]**:最大授權進程數(1)。

   **[!UICONTROL Alert]**:如果進程數等於1，則顯示此指示器。

   當 **[!UICONTROL Alert]** 指示器顯示，可能是相關進程被SQL資料庫引擎鎖定，或者它卡在無限循環中。 的 **監視** 由Adobe Campaign提供的進程每天自動重新啟動所有進程，使您能夠解決此問題。 但是，您也可以自行停止相關進程以強制重新啟動。

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]**:指示符 **消息中心**。 請參閱 [此部分](../../message-center/using/additional-configurations.md#monitoring-thresholds) 的子菜單。

* **[!UICONTROL Load average (1/5/15 minutes)]**:有關負載的資訊，即電腦上運行的進程在最後一分鐘、五分鐘或十五分鐘內的處理器使用率

   **[!UICONTROL Current value]**:機器的實際負載。

   **[!UICONTROL Max value]**:電腦上進程的最大使用負載

   **[!UICONTROL Warning]**:當負載在最後一分鐘、五分鐘或十五分鐘內達到最大授權值的80%時，將顯示此指示器。

   **[!UICONTROL Alert]**:當負載達到最後一分鐘、五分鐘或十五分鐘的最大授權值的90%時，將顯示此指示器。

* **[!UICONTROL Memory]**  有關物理記憶體(RAM)的資訊。

   **[!UICONTROL Current value]**:實際記憶體消耗。

   **[!UICONTROL Max Value]**:已安裝的記憶體總量。

   **[!UICONTROL Available]**:可用記憶體量。

   **[!UICONTROL Warning]**:當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]**:當記憶體消耗達到總量的90%時，將顯示此指示器。

   當 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 顯示指示器，您可以通過向安裝Adobe Campaign伺服器的電腦添加RAM來解決此問題。 您還可以決定在專用電腦上安裝Adobe Campaign伺服器。

* **[!UICONTROL Swap Memory]**:與與分頁檔案匹配的虛擬記憶體相關的資訊：Windows使用的硬碟上的一個區域，就好像它是RAM。

   **[!UICONTROL Current value]**:實際記憶體消耗。

   **[!UICONTROL Max Value]**:記憶體總量。

   **[!UICONTROL Available]**:可用記憶體量。

   **[!UICONTROL Warning]**:當記憶體消耗達到總量的80%時，將顯示此指示器。

   **[!UICONTROL Alert]**:當記憶體消耗達到總量的90%時，將顯示此指示器。

   當 **[!UICONTROL Warning]** 和 **[!UICONTROL Alert]** 指示器顯示，您可以通過增加exchange檔案的大小來解決問題。

* **[!UICONTROL Core Files]**:有關在Adobe Campaign進程崩潰後生成的檔案的資訊。 這些檔案使您能夠診斷崩潰的原因。

   **[!UICONTROL Current Value]**:現有檔案數。

   **[!UICONTROL Max Value]**:最大授權檔案數(1)。

   **[!UICONTROL Warning]**:當檔案數接近1時，將顯示此指示器。

   **[!UICONTROL Alert]**:當檔案數等於1時，將顯示此指示器。

   當因崩潰而丟失進程時，該進程在進程清單中以紅色顯示，並由 **監視** 由Adobe Campaign提供。

* **[!UICONTROL Number of shared memory segments]**:關於所有Adobe Campaign進程共用的記憶體段的資訊。

   **[!UICONTROL Current value]**:當前使用的記憶體段數。

   **[!UICONTROL Max Value]**:已授權的最大記憶體段數(2)。

   **[!UICONTROL Warning]**:當記憶體段數達到1時，將顯示此指示器。

   **[!UICONTROL Alert]**:當記憶體段數達到2時，將顯示此指示器。

* **[!UICONTROL Number of processes too old]**:已活動超過一天的進程的相關資訊。

   **[!UICONTROL Current value]**:當前活動的進程數。

   **[!UICONTROL Max Value]**:授權進程的最大數量。

   **[!UICONTROL Warning]**:當進程數達到授權閾值的80%時，將顯示此指示器。

   **[!UICONTROL Alert]**:當進程數達到授權閾值的90%時，將顯示此指示器。

* **[!UICONTROL File Handles]**:有關檔案描述符的資訊，即每個進程開啟的檔案數。

   **[!UICONTROL Current value]**:當前檔案描述符數。

   **[!UICONTROL Max Value]**:作業系統授權的檔案描述符的最大數量。

   **[!UICONTROL Warning]**:當授權檔案描述符數達到80%閾值時，將顯示此指示器。

   **[!UICONTROL Alert]**:當授權檔案描述符數達到90%閾值時，將顯示此指示器。

* **[!UICONTROL Processes]**:有關機器進程的資訊。

   **[!UICONTROL Current value]**:當前活動的進程數。

   **[!UICONTROL Max Value]**:授權進程的最大數量。

   **[!UICONTROL Active Processes]**:活動進程數。

   **[!UICONTROL Inactive Processes]**:非活動進程數。

   **[!UICONTROL Warning]**:當授權進程數達到80%閾值時，將顯示此指示器。

   **[!UICONTROL Alert]**:當授權進程數達到90%閾值時，將顯示此指示器。

* **[!UICONTROL Zombie Processes]**:有關已停止但仍具有進程標識符(PID)且在進程表中仍可見的進程的資訊。

   **[!UICONTROL Current value]**:當前處於活動狀態的僵屍進程數。

   **[!UICONTROL Max Value]**:授權僵屍進程的最大數量(2)。

   **[!UICONTROL Warning]**:當僵屍進程數接近2時，將顯示此指示器。

   **[!UICONTROL Alert]**:當僵屍進程數達到2時，將顯示此指示器。

#### 自定義指示器 {#customized-indicators}

Adobe Campaign允許您自定義指標，詳見如下：

1. 建立 **.sh** 檔案和名稱 **[!UICONTROL cust_indicators.sh]** 。
1. 將自定義指示器添加到此檔案。 例如：

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

1. 將檔案保存到 **[!UICONTROL usr/local/neolane/nl6]** 的子菜單。

此檔案由Adobe Campaign調用。

## SMTP報告 {#smtp-reports}

SMTP傳遞監控報告已整合到Adobe Campaign平台。 可通過控制台或Web訪問訪問。

這些報告按域顯示SMTP傳遞統計資訊和SMTP錯誤。 要訪問它們，操作員必須 **管理** 。

它們被分組在 **監視** >「SMTP監視」。

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* 只有在激活了電子郵件通道後，與SMTP監視相關的資訊才可用。
>* 的 **[!UICONTROL SMTP sending statistics]** 僅在實例上啟動統計伺服器時提供。
>


### SMTP正在發送統計資訊 {#smtp-sending-statistics}

的 **[!UICONTROL SMTP sending statistics]** 報告用於控制伺服器活動。 它顯示每個匹配子的綜合。

![](assets/smtp_stats_report.png)

此報告的指標清單如圖表下所示。

1. 已傳送的訊息總數.
1. 表示輸入/輸出消息：

   * 藍線：已準備好發送的郵件已到達Spiger，即發送SMTP之前的最後一個階段（與傳入資料一致）。

   * 綠線：消息已成功發送（與傳出資料一致）。

   * 紅線：由牛頭刨刀放棄的消息，返回給 **門** （與此恢復中拒絕的資料一致）。

   這些值以每小時的消息數表示。

1. 表示插齒器的兩個隊列：

   * 藍色曲線：活動消息的隊列。 這些消息將盡快發送。

   * 卡基曲線：「延遲」隊列。 由於限制或目標連接不可用，暫時無法返回這些消息。 每5秒、10秒、20秒、40秒、2分鐘等重試一次。 定義 **最大年齡秒** 才被拋棄。

1. 此圖表顯示已放棄消息的詳細資訊（第2個圖表上的紅色曲線）:它顯示未重試(mauve)而放棄的消息與發送失敗（紅色）的消息的比例。 這允許您查看由於統計伺服器的限制（限制）或由於遠程伺服器不可用而在授予的時間段內未處理的消息比例。
1. 開啟或正在開啟SMTP連接。
1. 估計 **母體**。

>[!NOTE]
>
>此報告與電子郵件流量整形器元件的狀態相關。

### 每個域的SMTP錯誤 {#smtp-errors-per-domain}

此報表允許您查看按域分列的在設定期間內的傳遞錯誤。

>[!NOTE]
>
>的 **minConnectionsToLog**。 **minErrorsToLog** 和 **minMessagesToLog** 選項 **serverConf.xml** 檔案定義將連接統計資訊考慮到的閾值。

![](assets/smtp_error_report.png)

本報告的指標清單如下表所示。

* 的 **域** 列包含發送消息的域的名稱（例如，yahoo.com的實際域名）,
* 的 **康克斯** 列顯示為此域開啟的SMTP連接數，
* 的 **已發送** 列與發送到此域的消息數相對應，
* 的 **卷** 列顯示已嘗試發送到此域的消息量（近似值）,
* 的 **錯誤** 列顯示該域上在該期間的錯誤的卷指示符，
* 的 **上次響應** 列顯示該域收到的最後一條SMTP響應消息，
* 的 **日期** 列顯示該域上次收到的SMTP響應的日期。

>[!NOTE]
>
>顯示在 **康克斯**。 **已發送**, **卷** 按照在 **[!UICONTROL Period]** 的子菜單。

按一下域名可查看其錯誤。

它們按PublicId分類：此標識符對應於路由器後面幾個Adobe Campaignmtas共用的IP地址。 統計伺服器使用此標識符來儲存此起始點和目標伺服器之間的連接和傳遞統計資訊。

![](assets/smtp_error_report_details.png)

的 **[!UICONTROL Owner of domain]** 欄位中，您可以在同一標籤下對多個域名進行分組。 在初始報告視圖中，所有MX域名都將與此所有者關聯。

按一下PublicId標識符可查看更多詳細資訊。

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>錯誤百分比由兩個圖表表示。 第一個是黑色背景上的水準進度條。 第二張圖表是按時間順序排列的。 所選期間被分成十二個時間間隔，每個時間間隔由垂直進度條表示。 在這兩種表示法中，如果未檢測到任何錯誤，則條為黑色。 條的顏色取決於遇到的錯誤百分比（黃色、橙色，最後是紅色）。 顏色灰度表示未發現任何顯著的資料卷。 通過將游標置於圖表上，可以顯示錯誤的確切百分比。

>[!NOTE]
>
>有關SMTP錯誤以及在Adobe Campaign管理這些錯誤的詳細資訊，請參閱 [此部分](../../installation/using/email-deliverability.md)。

## 計費報告 {#billing-report}

的 **[!UICONTROL Billing]** 技術工作流通過電子郵件將系統活動報告發送給「開單」操作員。 預設情況下，它會在每月25日的市場營銷實例上觸發。

在以下節點的子資料夾中可以找到技術工作流： **管理** > **生產** > **技術工作流**。

![](assets/billing.png)

一旦每月25日啟動工作流，您的計費操作員將在其收件箱中收到以下報告。

![](assets/billing_2.png)

以下指標可用於跟蹤交貨：

* **[!UICONTROL Start date]** :交貨的開始日期。 請注意，它可以早於報表的「自」日期。
* **[!UICONTROL Label]** :交貨的標籤。 要發送的郵件少於100條的遞送被認為太小，因此按開始日期聚合，在這種情況下，標籤顯示聚合的數量，例如， [3個小型交貨的合計]。
* **[!UICONTROL Total volume]** :傳送的位元組總數。
* **[!UICONTROL Avg volume]** :傳輸的平均位元組數。 這是以下公式的結果 **（總卷/消息）**，是計算 **[!UICONTROL Multiplier]** 度量。
* **[!UICONTROL Messages]** :已發送郵件數。 這包括成功發送的消息和重試（在從聯繫的伺服器接收到彈回消息後）。
* **[!UICONTROL Multiplier (x)]** :從消息的平均體積中推導出乘法器的值。
* **[!UICONTROL Count]** :消息和乘法器的乘法結果。

## 自動監控 {#automatic-monitoring}

Adobe Campaign提供了幾種自動監測方法，如下所示。

### 命令列 {#command-line}

命令

**nlserver監視器**

用於列出Adobe Campaign模組和系統上的一組指示器。

它以易於處理的XML格式生成輸出。

此命令也可與 **缺少** 參數，其中列出當配置檔案表示應執行這些進程時，此實例中缺少的進程。

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### 伺服器發佈的資訊 {#information-published-by-the-server}

#### /r/test {#r-test}

的 **http(s)://`<application>`/r/test** 頁用於test重定向伺服器。 我們建議使用相同的方法test用於跟蹤的前面伺服器。 此頁還可用於test負載調度程式。

它以XML格式顯示如下行：

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**頻率**:此test不使用任何負載，因此可以經常運行（例如每秒一次）。

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

此 **http(s)://`<Application server url>`/nl/jsp/ping.jsp**  頁面的操作方式與網路對應方相同：它通過apache/tomcat/web模組/資料庫test一個完整的查詢，並上傳到客戶端。 如果一切正常，則返回「OK」。 我們建議在具有資料庫訪問權限的電腦上運行此test（例如，mtas和調查）。

**用法**:必須將與操作員登錄關聯的會話令牌作為參數傳遞以便遠程登錄（請參見中的提示） [通過Adobe Campaign指令碼自動監視](#automatic-monitoring-via-adobe-campaign-scripts))。

例如：

![](assets/ncs_monitoring_ping.png)

操作員名稱和登錄名需要在Adobe Campaign客戶端控制台中預先配置有資料庫權限。

![](assets/ncs_operators_rights_01.png)

**頻率**:這是一種使用很少頻寬的test。 因此，它可以經常運行，但每分鐘不超過一次。

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

這是一種test，用來檢查操作員是否可以通過網頁訪問Adobe Campaign伺服器；與通過客戶端控制台菜單訪問的網頁相同。 您可以從監視工具（Tivoli 、 Nagios等）中調用此頁。

![](assets/ncs_monitoring_web.png)

**用法**:與運算子登錄關聯的會話令牌，用於連接到實例，需要用作參數(請參見中的提示 [通過Adobe Campaign指令碼自動監視](#automatic-monitoring-via-adobe-campaign-scripts))。

操作員及其登錄名需要先在Adobe Campaign客戶端控制台中配置相應的資料庫權限和限制。

**頻率**:這是一個完整的伺服器test，不需要經常運行（例如，可以每10分鐘執行一次）。

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

此 **jsp** 表示Adobe Campaign應用程式API的入口點。 因此，它可以提供對應用的詳細監控。 還可用於監控Adobe CampaignWeb服務。 它用於我們的監視指令碼，但請注意，它僅用於高級用戶。

### 基於部署類型的監視 {#monitoring-based-on-deployment-types}

Adobe Campaign啟用各種部署配置(有關詳細資訊，請參閱 [此部分](../../installation/using/hosting-models.md))。 本節詳細介紹根據安裝類型應用的各種自動監控技術。

<table> 
 <thead> 
  <tr> 
   <th> 部署類型 </th> 
   <th> 監視 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 獨立 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/monitor.jsp</span> 在Adobe Campaign伺服器上</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 標準 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/ping.jsp</span> 正面伺服器上</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> 在應用程式伺服器上</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 企業 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/ping.jsp</span> 正面伺服器上</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> 和 <span class="uicontrol">/nl/jsp/monitor.jsp</span> 在應用程式伺服器上</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 中間來源 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> 在應用程式伺服器上</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 通過Adobe Campaign指令碼自動監視 {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign可以提供實例監視工具(netreport)，讓您通過電子郵件發送有關檢測到的異常情況的報告。

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>此工具可用於監視實例，但Adobe Campaign不支援。 有關詳細資訊，請與市場活動管理員聯繫。

### 必需元素 {#required-elements}

自動監控需要以下預安裝注意事項：

* 您必須 **netreport.tgz** （Linux安裝）或 **netreport.zip** （Windows安裝）檔案，
* 我們強烈建議您不要在要監視的電腦上安裝監視，
* 它必須安裝在具有JRE或JDK的電腦上，
* 在Linux中，要監視的電腦必須 **不列顛** 檔案。 如需詳細資訊，請參閱[本章節](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages)。

### 安裝過程 {#installation-procedure}

安裝過程如下：

1. 在控制台中，如有必要，請建立新操作員（「監視」用戶已存在），但不分配任何權限。
1. 運行存檔提取。
1. 閱讀 **自述** 的子菜單。
1. 更新 **netconf.xml** 配置檔案。
1. 更新 **netreport.bat** (Windows)或 **netreport.sh** (Linux)檔案。

### 配置netconf.xml檔案 {#configuring-the-netconf-xml-file}

XML配置檔案包含以下元素：

* [「屬性」元素](#properties--element)
* [「Instance」元素](#instance--element)
* [「Host」元素](#host--element)
* [子元素](#sub-elements)

下面是一個配置示例：

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
>可通過向 **netconf.xml** 例如， **netconf-dev-xml**。 **netconf-prod-xml**&#x200B;的子菜單。 然後，在中指定用於執行netreport的配置 **netreport.bat** 或 **netreport.sh** 通過添加 **$JAVA_HOME/bin/javanetport開發** 或 **@%JAVA_HOME%binjava直接埠產品** 例如。

>[!IMPORTANT]
>
>對於 **監控** 要工作的操作員，執行netreport的電腦必須位於安全區域中 **會話TokenOnly** 的子菜單。 如果尚未為此操作員指定可信IP掩碼，則安全區域還必須在 **allowEmptyPassword** 和 **allowUserPassword** 的子菜單。

#### 「屬性」元素 {#properties--element}

此元素用於填充電子郵件的配置，即

* **郵件伺服器**:用於發送電子郵件的SMTP伺服器(例如：smtp.domain.net)。
* **郵件發件人**:報表發件人的電子郵件地址(例如：monitoring@domain.net)。
* **收件人清單**:監視收件人的電子郵件地址清單。 地址必須用逗號分隔（無空格）。
* &quot;**夜**「 mode（可選）」用於避免在指定時間段之間發送電子郵件。 相反，資料會被整合，並在結束時間（預設為7:00）後發送有關夜間活動的電子郵件。
* 的 **buildRange** 子元素（可選）用於指定最小和最大生成號。 將為內部版本號不在此範圍內的所有電腦生成錯誤

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* 可以添加 **`<sla>`** （可選） **屬性** 的子菜單。 每次執行netreport時都會生成日誌檔案。 檔案名稱包含配置名稱以及日期和時間，例如 **dev_06_12_13_16_47_05.tmp**。 該檔案包含以下資訊：實例名稱、電腦名稱、嚴重性級別、（0到3，從最不重要到最關鍵）、日期（時間戳格式）、查詢與響應之間的已用時間（以毫秒為單位）、使用的服務(http、ncs、ncsex、redir)。 此資訊在每項服務結束時由表格標籤和換行分隔。

>[!NOTE]
>
>的 **persistHtmlFile** 屬性上的值為&quot;true&quot; **`<property>`** 元素用於在檔案中記錄最新的監視狀態 **netreport.md**。 此檔案保存在安裝目錄中。

#### 「Instance」元素 {#instance--element}

此元素允許您將多台電腦（主機）重新組合到同一實例中。 實例名稱顯示在監視電子郵件的第一部分中。 您可以按一下實例的名稱以訪問有關每台電腦的詳細資訊。

```
instance name="instance-name" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **名稱**:將出現在電子郵件第一部分中的實例名稱。
* **收件人清單** （可選）:允許您通過電子郵件發送有關特定實例的監視報告。

#### 「Host」元素 {#host--element}

此元素配置主機上給定伺服器的監視，即

* **名稱**:要監視的電腦的名稱。
* **別名** （可選）:監視的電腦的名稱，如報告中所示。
* **會話令牌**:通過授權會話令牌提供登錄驗證。

   要配置會話令牌，請選擇 **監控** 操作員。 在 **訪問權限** 頁籤，指定授權監視此實例的電腦的IP地址。 然後，您將能夠使用 **監控** 標識符，無需指定密碼。

   ![](assets/ncs_operators_rights_02.png)

* **關鍵級別** （可選）:允許您按嚴重性級別對要顯示的錯誤進行排序。 可能的值為「0」（顯示所有級別）、「1」（僅顯示高錯誤和嚴重錯誤）和「2」（僅顯示嚴重錯誤）。 如果未提供此屬性，則顯示所有錯誤級別。
* **濾波器** （可選）:例如， **filter=&quot;wkf;wkf1&quot;**。 工作流標籤必須用分號分隔。

#### 子元素 {#sub-elements}

* **tcp**:檢查伺服器是否處於開啟或關閉狀態。 必須輸入埠號。
* **http**:檢查Web伺服器是否存在（應用程式伺服器可操作）。
* **nc**:檢查在「instance」屬性中輸入的實例上的進程（工作流錯誤、記憶體使用情況等）。 的 **包括** （強制）屬性允許您選擇顯示死進程（「true」或「false」值）。
* **重定向**:檢查跟蹤。

在大多數情況下，只有 **nc** 和 **重定向** 子元素可以保留。

在任何情況下，某些節點可以在子元素（例如，節點）中過載 **埠=75** 重載用於http、ncs或redir連接的埠):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

在 **nc**。 **重定向** 和 **http** 子元素，可以 **是安全的** attribute（可選）選擇是否使用https協定（「true」或「false」值）。 如果未提供此屬性，則使用http協定。

### 配置netreport.bat或netreport.sh檔案 {#configuring-the-netreport-bat-or-netreport-sh--file}

要配置該檔案，請編輯該檔案並指明JRE或JDK安裝在的目錄。

### 啟動監視 {#launching-monitoring}

要啟動監視，請執行 **netreport.bat** 或 **netreport.sh** 通過指令碼以定期的間隔發送檔案。 在第一次執行後，僅在狀態發生變化時才發送報告。

### 測試監控 {#testing-monitoring}

要test監視，請執行 **netreport.bat** 或 **netreport.sh** 的子菜單。

電子郵件將發送給 **收件人清單** 的 **netconf.xml** 的子菜單。
