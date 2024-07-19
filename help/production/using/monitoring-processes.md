---
product: campaign
title: 監控流程
description: 瞭解如何監視Campaign流程
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '3643'
ht-degree: 0%

---

# 監控流程{#monitoring-processes}


可以手動或自動監視應用程式伺服器和重新導向伺服器（**追蹤**）。

## 手動監視 {#manual-monitoring}

若要存取Adobe Campaign處理序監視頁面，請瀏覽至&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Overview]**&#x200B;連結。

![](assets/d_ncs_monitoring.png)

顯示的頁面可讓您檢視已連線執行處理的狀態，即：

* 執行處理的資訊：版本、名稱、資料庫引擎、已安裝的套件、伺服器系統指示器、
* 遺失的處理程式和執行資訊（開始日期、PID等）的清單，
* 工作流程和傳遞的檢視。

監視Campaign處理的其他方法顯示在[此頁面](../../production/using/monitoring-guidelines.md)中。

### 記錄日誌 {#log-journal}

若要顯示與程式相關的記錄日誌，請按一下程式，例如&#x200B;**mta**，然後選取&#x200B;**[!UICONTROL Open the log journal]**。

![](assets/d_ncs_monitoring2.png)

### 系統指標 {#system-indicators}

瀏覽至系統指示器清單，以顯示關於機器的資訊，例如其實體和虛擬記憶體、作用中的處理作業以及可用的磁碟空間。 Linux和Windows作業系統的指標不同。 移至&#x200B;**[!UICONTROL Instance Monitoring]**&#x200B;頁面，然後按一下&#x200B;**[!UICONTROL Display]**&#x200B;連結以開啟指標清單。

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]**： **訊息中心**&#x200B;的特定指標。 [了解更多](../../message-center/using/additional-configurations.md#monitoring-thresholds)

* **[!UICONTROL Memory]**：關於實體記憶體(RAM)的資訊。

  **[!UICONTROL Current value]**：目前的記憶體耗用量。

  **[!UICONTROL Max Value]**：安裝的記憶體總數。

  **[!UICONTROL Available]**：可用的記憶體數量。

  **[!UICONTROL Warning]**：當記憶體耗用量達到總數量的80%時，會顯示此指標。

  **[!UICONTROL Alert]**：當記憶體耗用量達到總數量的90%時，會顯示此指標。

  顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指標時，您可以將RAM新增至安裝Adobe Campaign伺服器的電腦來解決問題。 您也可以決定在專屬電腦上安裝Adobe Campaign伺服器。

* **[!UICONTROL Swap Memory]**：與符合分頁檔的虛擬記憶體相關的資訊：Windows在硬碟上使用的區域，就好像是RAM一樣。

  **[!UICONTROL Current value]**：實際的記憶體耗用量。

  **[!UICONTROL Max Value]**：記憶體總數。

  **[!UICONTROL Available]**：可用的記憶體數量。

  **[!UICONTROL Warning]**：當記憶體耗用量達到總數量的80%時，會顯示此指標。

  **[!UICONTROL Alert]**：當記憶體耗用量達到總數量的90%時，會顯示此指標。

  顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指標時，您可以在進階Windows設定中增加Exchange檔案的大小來解決問題。

* **[!UICONTROL Disk XXX]**：關於電腦讀取器的資訊。

  **[!UICONTROL Current value]**：實際使用的磁碟空間。

  **[!UICONTROL Max Value]**：磁碟總容量。

  **[!UICONTROL Available]**：磁碟空間可用。

  **[!UICONTROL Used]**：已使用磁碟的百分比。

  **[!UICONTROL Warning]**：當可用磁碟空間達到總容量的80%時，會顯示此指標。

  **[!UICONTROL Alert]**：當可用磁碟空間達到總容量的90%時，會顯示此指標。

* **[!UICONTROL Number of processes too old]**：有關已啟動超過一天的Adobe Campaign處理序的資訊。

  **[!UICONTROL Current value]**：目前作用中的處理序數目。

  **[!UICONTROL Max Value]**：授權處理序的數目上限(1)。

  **[!UICONTROL Alert]**：如果處理序數等於1，則會顯示此指示器。

  顯示&#x200B;**[!UICONTROL Alert]**&#x200B;指示器時，可能是相關處理序被SQL資料庫引擎鎖定，或是卡在無限回圈中。 Adobe Campaign提供的&#x200B;**watchdog**&#x200B;程式每天都會自動重新啟動所有程式，讓您解決此問題。 不過，您也可以自行停止相關程式，以強制重新啟動。

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]**： **訊息中心**&#x200B;的特定指標。 如需詳細資訊，請參閱[本節](../../message-center/using/additional-configurations.md#monitoring-thresholds)。

* **[!UICONTROL Load average (1/5/15 minutes)]**：關於負載的資訊，也就是在機器上執行之處理作業在最後一分鐘、五分鐘或十五分鐘內的處理器使用率

  **[!UICONTROL Current value]**：電腦的實際負載。

  **[!UICONTROL Max value]**：電腦上處理程式的最大使用負載

  **[!UICONTROL Warning]**：當負載在最近1分鐘、5分鐘或15分鐘達到最大授權值的80%時，會顯示此指標。

  **[!UICONTROL Alert]**：當負載達到最後一分鐘、五分鐘或十五分鐘最大授權值的90%時，會顯示此指標。

* 有關實體記憶體(RAM)的&#x200B;**[!UICONTROL Memory]**&#x200B;資訊。

  **[!UICONTROL Current value]**：實際的記憶體耗用量。

  **[!UICONTROL Max Value]**：安裝的記憶體總數。

  **[!UICONTROL Available]**：可用的記憶體數量。

  **[!UICONTROL Warning]**：當記憶體耗用量達到總數量的80%時，會顯示此指標。

  **[!UICONTROL Alert]**：當記憶體耗用量達到總數量的90%時，會顯示此指標。

  顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指標時，您可以將RAM新增至安裝Adobe Campaign伺服器的電腦來解決問題。 您也可以決定在專屬電腦上安裝Adobe Campaign伺服器。

* **[!UICONTROL Swap Memory]**：與符合分頁檔的虛擬記憶體相關的資訊：Windows在硬碟上使用的區域，就好像是RAM一樣。

  **[!UICONTROL Current value]**：實際的記憶體耗用量。

  **[!UICONTROL Max Value]**：記憶體總數。

  **[!UICONTROL Available]**：可用的記憶體數量。

  **[!UICONTROL Warning]**：當記憶體耗用量達到總數量的80%時，會顯示此指標。

  **[!UICONTROL Alert]**：當記憶體耗用量達到總數量的90%時，會顯示此指標。

  顯示&#x200B;**[!UICONTROL Warning]**&#x200B;和&#x200B;**[!UICONTROL Alert]**&#x200B;指標時，您可以增加Exchange檔案的大小來解決問題。

* **[!UICONTROL Core Files]**： Adobe Campaign處理序當機後所產生檔案的相關資訊。 這些檔案可讓您診斷當機的原因。

  **[!UICONTROL Current Value]**：現有檔案數目。

  **[!UICONTROL Max Value]**：授權檔案數上限(1)。

  **[!UICONTROL Warning]**：當檔案數接近1時，會顯示此指標。

  **[!UICONTROL Alert]**：當檔案數等於1時顯示此指示器。

  當處理程式因當機而遺失時，會在處理程式清單中以紅色顯示，並由Adobe Campaign提供的&#x200B;**看門狗**&#x200B;處理程式自動重新啟動。

* **[!UICONTROL Number of shared memory segments]**：關於所有Adobe Campaign處理序共用的記憶體區段的資訊。

  **[!UICONTROL Current value]**：目前正在使用的記憶體區段數目。

  **[!UICONTROL Max Value]**：授權的記憶體區段數上限(2)。

  **[!UICONTROL Warning]**：當記憶體區段數達到1時，會顯示此指示器。

  **[!UICONTROL Alert]**：當記憶體區段數達到2時，就會顯示此指示器。

* **[!UICONTROL Number of processes too old]**：已啟動超過一天的處理序相關資訊。

  **[!UICONTROL Current value]**：目前作用中的處理序數目。

  **[!UICONTROL Max Value]**：授權處理序的數目上限。

  **[!UICONTROL Warning]**：當處理程式數達到授權臨界值的80%時，會顯示此指標。

  **[!UICONTROL Alert]**：當處理序數目達到授權臨界值的90%時，會顯示此指標。

* **[!UICONTROL File Handles]**：關於檔案描述元的資訊，即每個處理程式開啟的檔案數。

  **[!UICONTROL Current value]**：目前的檔案描述元數目。

  **[!UICONTROL Max Value]**：作業系統授權的檔案描述元數目上限。

  **[!UICONTROL Warning]**：當授權的檔案描述元數目達到80%臨界值時，會顯示此指標。

  **[!UICONTROL Alert]**：當授權的檔案描述元數目達到90%臨界值時，會顯示此指標。

* **[!UICONTROL Processes]**：關於電腦處理程式的資訊。

  **[!UICONTROL Current value]**：目前作用中的處理序數目。

  **[!UICONTROL Max Value]**：授權處理序的數目上限。

  **[!UICONTROL Active Processes]**：使用中的處理序數目。

  **[!UICONTROL Inactive Processes]**：非作用中處理序的數目。

  **[!UICONTROL Warning]**：當授權處理的數量達到80%臨界值時，會顯示此指標。

  **[!UICONTROL Alert]**：當授權處理的數量達到90%臨界值時，會顯示此指標。

* **[!UICONTROL Zombie Processes]**：關於已停止但仍具有處理序識別碼(PID)且仍顯示在處理序表格中的處理序資訊。

  **[!UICONTROL Current value]**：目前作用中的殭屍處理序數目。

  **[!UICONTROL Max Value]**：授權殭屍處理程式的數量上限(2)。

  **[!UICONTROL Warning]**：當殭屍處理數目接近2時，會顯示此指標。

  **[!UICONTROL Alert]**：當殭屍處理序數目達到2時，會顯示此指示器。

#### 自訂指標 {#customized-indicators}

Adobe Campaign可讓您自訂指標，如下所述：

1. 建立&#x200B;**.sh**&#x200B;檔案並將其命名為&#x200B;**[!UICONTROL cust_indicators.sh]**。
1. 將您的自訂指標新增到此檔案。 例如：

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

1. 將檔案儲存在&#x200B;**[!UICONTROL usr/local/neolane/nl6]**&#x200B;資料夾中。

此檔案由Adobe Campaign呼叫。

## SMTP報告 {#smtp-reports}

SMTP傳遞監視報告已整合至Adobe Campaign平台。 可透過主控台或網頁存取來存取。

這些報告會依網域顯示SMTP傳遞統計資料和SMTP錯誤。 操作員必須擁有&#x200B;**管理**&#x200B;許可權才能存取這些專案。

它們會分組在&#x200B;**監視** > &#39;SMTP監視&#39;下。

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* 只有在已啟動電子郵件通道時，才能使用SMTP監視的相關資訊。
>* 只有在執行個體上啟動統計伺服器時，才會提供&#x200B;**[!UICONTROL SMTP sending statistics]**。
>

### SMTP傳送統計資料 {#smtp-sending-statistics}

**[!UICONTROL SMTP sending statistics]**&#x200B;報表可讓您控制伺服器活動。 它會顯示每個配對的合成。

![](assets/smtp_stats_report.png)

此報告的指標清單顯示在圖表下方。

1. 已傳送的訊息總數。
1. 代表輸入/輸出訊息：

   * 藍線：已準備好傳送且已到達Shaper的訊息，即傳送SMTP之前的最後一個階段（與傳入資料一致）。

   * 綠線：已成功傳送訊息（與傳出資料一致）。

   * 紅線：由Shaper捨棄的訊息，已傳回&#x200B;**mta** （與此復原中拒絕的資料一致）。

   這些值以每小時的訊息數表示。

1. 代表兩個配置器佇列：

   * 藍色曲線：作用中訊息的佇列。 將會儘快傳送這些訊息。

   * Kaki曲線：「延遲」佇列。 由於節流或沒有可用的目標連線，目前無法傳回這些訊息。 每5秒、10秒、20秒、40秒、2分鐘等會進行重試。 所定義的&#x200B;**MaxAgeSec**&#x200B;時間，在放棄之前。

1. 此圖表顯示捨棄訊息的詳細資訊（第2個圖表的紅色曲線）：它顯示捨棄而未重試的訊息(Mauve)與傳送失敗（紅色）的訊息之間的比例。 這可讓您檢視在授權期間內因統計伺服器（節流）的限制或遠端伺服器無法使用而未處理的訊息比例。
1. SMTP連線已開啟或正在開啟。
1. **mtachild**&#x200B;數目的預估值。

>[!NOTE]
>
>此報表與電子郵件流量整形器元件的狀態有關。

### 每個網域的SMTP錯誤 {#smtp-errors-per-domain}

此報表可讓您檢視在設定期間內依網域劃分的傳送錯誤。

>[!NOTE]
>
>**serverConf.xml**&#x200B;檔案的&#x200B;**minConnectionsToLog**、**minErrorsToLog**&#x200B;和&#x200B;**minMessagesToLog**&#x200B;選項定義閾值，超過閾值時，連線統計資料就會納入考量。

![](assets/smtp_error_report.png)

此報告的指標清單如下表所示。

* **網域**&#x200B;欄包含訊息傳送至的網域名稱(或真正的網域名稱，例如yahoo.fr為yahoo.com)，
* **Cnx**&#x200B;欄會顯示此網域開啟的SMTP連線數目。
* **Sent**&#x200B;資料行對應到傳送至此網域的訊息數目，
* **磁碟區**&#x200B;欄顯示嘗試傳送至此網域的訊息數量（約略值），
* **Errors**&#x200B;欄會顯示此網域上在這段期間發生錯誤的磁碟區指示器，
* **上次回應**&#x200B;欄會顯示此網域收到的最後一個SMTP回應訊息，
* **Date**&#x200B;欄會顯示此網域收到的最後一個SMTP回應日期。

>[!NOTE]
>
>顯示在&#x200B;**Cnx**、**Sent**&#x200B;和&#x200B;**Volume**&#x200B;欄中的值是根據&#x200B;**[!UICONTROL Period]**&#x200B;欄位中選取的期間來計算的。

按一下網域名稱以檢視其錯誤。

它們會依PublicId分類：此識別碼會對應到路由器後面數個Adobe Campaign中繼資料所共用的IP位址。 統計資料伺服器會使用此識別碼來記憶此起始點和目標伺服器之間的連線和傳遞統計資料。

![](assets/smtp_error_report_details.png)

**[!UICONTROL Owner of domain]**&#x200B;欄位可讓您將不同的網域名稱群組在相同的標籤下。 在初始報告檢視中，所有MX網域名稱都將與此擁有者相關聯。

按一下PublicId識別碼以檢視詳細資訊。

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>錯誤百分比由兩個圖表表示。 第一個是在黑色背景上的水準進度列。 第二個圖表是按時間順序排列的。 選取的期間分為12個時間間隔，每個間隔以垂直的進度列表示。 在這兩種表示中，如果未偵測到任何錯誤，則表示該列為黑色。 長條的顏色取決於遇到的錯誤百分比（黃色、然後是橙色，最後是紅色）。 灰色表示找不到重要的資料量。 將游標放在圖表上，即可顯示錯誤的確切百分比。

>[!NOTE]
>
>如需在Adobe Campaign中管理SMTP錯誤及錯誤的詳細資訊，請參閱[本節](../../installation/using/email-deliverability.md)。

## 計費報告 {#billing-report}

**[!UICONTROL Billing]**&#x200B;技術工作流程會透過電子郵件將系統活動報告傳送給「帳單」操作員。 預設會在行銷執行個體上每月25日觸發。

您可以在下列節點的子資料夾中找到技術工作流程： **管理** > **生產** > **技術工作流程**。

![](assets/billing.png)

工作流程在每月的25日啟動後，您的帳單操作員將在收件匣中收到以下報告。

![](assets/billing_2.png)

下列量度可用來追蹤您的傳送內容：

* **[!UICONTROL Start date]** ：傳遞的開始日期。 請注意，日期可能早於報表的「起始」日期。
* **[!UICONTROL Label]** ：傳遞的標籤。 要傳送少於100個訊息的傳遞被視為太小，因此會依開始日期彙總，在這種情況下，標籤會顯示彙總的數量，例如[3個小型傳遞的彙總]。
* **[!UICONTROL Total volume]** ：為傳遞傳輸的位元組總數。
* **[!UICONTROL Avg volume]** ：傳輸的平均位元組數量。 這是下列公式&#x200B;**（總數量/訊息）**&#x200B;的結果，這是&#x200B;**[!UICONTROL Multiplier]**&#x200B;量度的計算基礎。
* **[!UICONTROL Messages]** ：已傳送的訊息數。 這包括成功傳送的訊息和重試（在收到來自連絡伺服器的退回訊息後）。
* **[!UICONTROL Multiplier (x)]** ：乘數的值是從訊息的平均磁碟區推算出來。
* **[!UICONTROL Count]** ：訊息與乘數相乘的結果。

## 自動監視 {#automatic-monitoring}

Adobe Campaign提供數種自動監視方法，如下所示。

### 命令列 {#command-line}

命令

**nlserver監視器**

可讓您在Adobe Campaign模組和系統上列出一組指標。

它會以易於處理的XML格式產生輸出。

此命令也可以使用&#x200B;**-missing**&#x200B;引數執行，這會列出組態檔表示應該執行時此執行個體中遺漏的處理序。

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### 伺服器發佈的資訊 {#information-published-by-the-server}

#### /r/test {#r-test}

**http(s)：//`<application>`/r/test**&#x200B;頁面是用來測試重新導向伺服器。 我們建議使用此相同的方法測試用於追蹤的前端伺服器。 此頁面也可用來測試負載Dispatcher。

它以XML格式顯示如下行：

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**頻率**：此測試未使用任何負載，因此可以經常執行（例如每秒執行一次）。

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

此&#x200B;**http(s)：//`<Application server url>`/nl/jsp/ping.jsp**&#x200B;頁面的運作方式與其網路對應頁面相同：它會測試透過apache/tomcat/web module/database上傳至使用者端的完整查詢。 如果一切正常運作，則會傳回「OK」。 我們建議在可以存取資料庫（例如中繼資料和調查）的電腦上執行此測試。

**使用方式**：與操作員登入關聯的工作階段權杖必須傳遞為引數，才能從遠端登入(請參閱[透過Adobe Campaign指令碼自動監視](#automatic-monitoring-via-adobe-campaign-scripts)中的提示)。

例如：

![](assets/ncs_monitoring_ping.png)

運運算元名稱和登入必須先在Adobe Campaign使用者端主控台中設定資料庫許可權。

![](assets/ncs_operators_rights_01.png)

**頻率**：這是使用很少頻寬的測試。 因此，其執行頻率相當高，不過不會超過每分鐘一次。

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

這是一項測試，可檢查操作員是否可透過網頁存取Adobe Campaign伺服器；該網頁與透過使用者端主控台功能表存取的網頁相同。 您可以從您的監視工具（Tivoli、Nagios等）呼叫此頁面。

![](assets/ncs_monitoring_web.png)

**使用方式**：與操作員登入關聯的工作階段權杖必須作為引數使用，以便您連線至執行個體(請參閱[透過Adobe Campaign指令碼自動監視](#automatic-monitoring-via-adobe-campaign-scripts)中的提示)。

運運算元及其登入需要在先前的Adobe Campaign使用者端主控台中，以適當的資料庫許可權和限制進行設定。

**頻率**：這是完整的伺服器測試，不需要經常執行（例如，每10分鐘可以執行一次）。

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

此&#x200B;**jsp**&#x200B;代表Adobe Campaign應用程式API的進入點。 因此，它可以提供應用程式的詳細監視。 它也可以用來監視Adobe Campaign Web服務。 我們的監控指令碼會使用此功能，但請注意，此功能僅供進階使用者使用。

### 根據部署型別監視 {#monitoring-based-on-deployment-types}

Adobe Campaign會啟用各種部署設定（如需詳細資訊，請參閱[本區段](../../installation/using/hosting-models.md)）。 本節根據您的安裝型別，詳細說明要套用的各種自動監視技術。

<table> 
 <thead> 
  <tr> 
   <th> 部署型別 </th> 
   <th> 監視 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 獨立 </td> 
   <td> 
    <ul> 
     <li><p> Adobe Campaign伺服器上的<span class="uicontrol">/r/test</span>和<span class="uicontrol">/nl/jsp/monitor.jsp</span></p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 標準 </td> 
   <td> 
    <ul> 
     <li><p> 前端伺服器上的<span class="uicontrol">/r/test</span>和<span class="uicontrol">/nl/jsp/ping.jsp</span></p> </li> 
     <li><p> 應用程式伺服器上的<span class="uicontrol">/nl/jsp/monitor.jsp</span></p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 企業 </td> 
   <td> 
    <ul> 
     <li><p> 前端伺服器上的<span class="uicontrol">/r/test</span>和<span class="uicontrol">/nl/jsp/ping.jsp</span></p> </li> 
     <li><p> 應用程式伺服器上的<span class="uicontrol">/r/test</span>和<span class="uicontrol">/nl/jsp/monitor.jsp</span></p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 中間來源 </td> 
   <td> 
    <ul> 
     <li><p> 應用程式伺服器上的<span class="uicontrol">/nl/jsp/monitor.jsp</span></p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 透過Adobe Campaign指令碼自動監視 {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign可提供執行個體監控工具(netreport)，讓您透過電子郵件傳送有關偵測到的異常的報告。

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>此工具可用於監視您的執行個體，但Adobe Campaign不支援。 如需詳細資訊，請聯絡Campaign管理員。

### 必要元素 {#required-elements}

進行自動監視時，需要下列安裝前預防措施：

* 您必須有&#x200B;**netreport.tgz** （Linux安裝）或&#x200B;**netreport.zip** （Windows安裝）檔案，
* 我們強烈建議您不要在要監視的電腦上安裝監視，
* 它必須安裝在具有JRE或JDK的電腦上，
* 在Linux中，要監視的電腦必須有&#x200B;**bc**&#x200B;封裝。 如需詳細資訊，請參閱[本章節](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages)。

### 安裝程式 {#installation-procedure}

安裝程式如下：

1. 在主控台中，視需要建立新運運算元（「監視」使用者已存在），但不指派任何權利。
1. 執行封存擷取。
1. 讀取&#x200B;**讀我檔案**。
1. 更新&#x200B;**netconf.xml**&#x200B;組態檔。
1. 更新&#x200B;**netreport.bat** (Windows)或&#x200B;**netreport.sh** (Linux)檔案。

### 設定netconf.xml檔案 {#configuring-the-netconf-xml-file}

XML組態檔包含下列元素：

* [&#39;Properties&#39;元素](#properties--element)
* [&#39;Instance&#39;元素](#instance--element)
* [&#39;主機&#39;元素](#host--element)
* [子元素](#sub-elements)

以下是設定範例：

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
>您可以將尾碼新增至&#x200B;**netconf.xml**&#x200B;檔案來指定各種設定，例如&#x200B;**netconf-dev.xml**、**netconf-prod.xml**&#x200B;等。 然後指定用於執行&#x200B;**netreport.bat**&#x200B;或&#x200B;**netreport.sh**&#x200B;檔案中的netreport的設定，例如新增&#x200B;**$JAVA_HOME/bin/java netreport dev**&#x200B;或&#x200B;**@%JAVA_HOME%binjava netreport prod**。

>[!IMPORTANT]
>
>若要讓&#x200B;**監視**&#x200B;運運算元運作，執行Netreport的電腦必須位於&#x200B;**sessionTokenOnly**&#x200B;模式的安全性區域。 如果沒有為此運運算元指定信任的IP遮罩，則安全性區域也必須是&#x200B;**allowEmptyPassword**&#x200B;和&#x200B;**allowUserPassword**&#x200B;模式。

#### &#39;Properties&#39;元素 {#properties--element}

此元素用於填入電子郵件的設定，例如

* **mailServer**：用來傳送電子郵件的SMTP伺服器(例如： smtp.domain.net)。
* **mailFrom**：報告寄件者的電子郵件地址(例如：monitoring@domain.net)。
* **recipientList**：監視收件者的電子郵件地址清單。 位址必須以逗號分隔（無空格）。
* &#39;**night**&#39;模式（選擇性）用於避免在指定的時段之間傳送電子郵件。 相反地，資料會經過合併，並在結束時間後傳送一封有關夜間活動的電子郵件（預設為7:00）。
* **buildRange**&#x200B;子專案（選擇性）可讓您指定最小和最大組建編號。 組建編號未落在此範圍的所有電腦都會產生錯誤

  ```
  <buildRange minimum="0000" maximum="9999"/>
  ```

* 您可以在&#x200B;**properties**&#x200B;元素中新增&#x200B;**`<sla>`** （選擇性）子元素。 每次執行netreport時都會產生記錄檔。 檔案名稱包含組態名稱以及日期和時間，例如&#x200B;**dev_06_12_13_16_47_05.tmp**。 檔案包含下列資訊：執行個體名稱、電腦名稱、嚴重性層級、（0到3，從最低臨界到最嚴重）、日期（時間戳記格式）、查詢與回應之間的經過時間（毫秒）、使用的服務(http、ncs、ncsex、redir)。 這項資訊會以製表標籤和每個服務結尾的分行符號來分隔。

>[!NOTE]
>
>**`<property>`**&#x200B;專案上值為「true」的&#x200B;**persistHtmlFile**&#x200B;屬性是用來記錄檔案&#x200B;**netreport.md**&#x200B;中的最新監視狀態。 此檔案儲存在安裝目錄中。

#### &#39;Instance&#39;元素 {#instance--element}

此元素可讓您將多部機器（主機）重新分組為相同的執行個體。 執行個體名稱會顯示在監控電子郵件的第一部分。 您可以按一下執行個體的名稱，以存取有關每台機器的詳細資訊。

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

* **name**：執行個體名稱會出現在電子郵件的第一部分。
* **recipientList** （選用）：可讓您透過電子郵件傳送特定執行個體的相關監視報告。

#### &#39;主機&#39;元素 {#host--element}

此元素可設定主機上指定伺服器的監視，例如

* **名稱**：要監視的電腦名稱。
* **alias** （選擇性）：監視的電腦在報表中顯示的名稱。
* **sessionToken**：透過授權的工作階段權杖提供登入驗證。

  若要設定工作階段權杖，請在Adobe Campaign主控台中選取&#x200B;**監視**&#x200B;運運算元。 在&#x200B;**存取許可權**&#x200B;索引標籤中，指定授權監視此執行個體之電腦的IP位址。 然後，您就可以使用&#x200B;**監視**&#x200B;識別碼從這些電腦連線到監視頁面，而不需要指定密碼。

  ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** （選擇性）：可讓您依嚴重性層級排序要顯示的錯誤。 可能的值為「0」（顯示所有層級）、「1」（僅顯示高度和嚴重錯誤）和「2」（僅顯示嚴重錯誤）。 如果未提供此屬性，則會顯示所有錯誤層級。
* **篩選器** （選用）：可讓您排除某些工作流程錯誤，例如&#x200B;**篩選器=&quot;wkf；wkf1&quot;**。 工作流程標籤必須以分號分隔。

#### 子元素 {#sub-elements}

* **tcp**：檢查伺服器是否已啟動。 您必須輸入連線埠號碼。
* **http**：檢查Web伺服器是否存在（應用程式伺服器運作中）。
* **ncs**：檢查在「執行個體」屬性中輸入的執行個體上的處理序（工作流程錯誤、記憶體使用量等）。 **包含** （必要）屬性可讓您選擇顯示無效處理序（&#39;true&#39;或&#39;false&#39;值）。
* **redir**：檢查追蹤。

在大多數情況下，只能保留&#x200B;**ncs**&#x200B;和&#x200B;**redir**&#x200B;子元素。

在任何情況下，子元素中某些節點可能會超載（例如，節點&#x200B;**連線埠=75**&#x200B;會超載http、ncs或redir連線所使用的連線埠）：

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

在&#x200B;**ncs**、**redir**&#x200B;和&#x200B;**http**&#x200B;子元素中，您可以新增&#x200B;**isSecure**&#x200B;屬性（選擇性）來選擇是否使用https通訊協定（&#39;true&#39;或&#39;false&#39;值）。 如果未提供此屬性，則會使用http通訊協定。

### 設定netreport.bat或netreport.sh檔案 {#configuring-the-netreport-bat-or-netreport-sh--file}

若要進行設定，請編輯此檔案，並指出JRE或JDK的安裝目錄。

### 正在啟動監視 {#launching-monitoring}

若要啟動監視，請透過指令碼定期執行&#x200B;**netreport.bat**&#x200B;或&#x200B;**netreport.sh**&#x200B;檔案。 報表會在首次執行後傳送，且僅在狀態變更時傳送。

### 測試監視 {#testing-monitoring}

若要測試監視，請執行&#x200B;**netreport.bat**&#x200B;或&#x200B;**netreport.sh**&#x200B;檔案。

已傳送電子郵件給&#x200B;**netconf.xml**&#x200B;檔案的&#x200B;**recipientList**&#x200B;中指定的收件者。
