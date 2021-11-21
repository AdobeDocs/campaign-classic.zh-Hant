---
product: campaign
title: 複製環境
description: 複製環境
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 1%

---

# 複製環境{#duplicating-environments}

![](../../assets/v7-only.svg)

## 簡介 {#introduction}

### 概覽 {#overview}

>[!IMPORTANT]
>
>如果您沒有伺服器和資料庫（托管環境）的存取權，將無法執行以下所述的程式。 請聯繫Adobe。

使用Adobe Campaign需要安裝和設定一或多個環境：開發、測試、預生產、生產等。

每個環境都包含一個Adobe Campaign例項，且每個Adobe Campaign例項都連結至一或多個資料庫。 應用伺服器可以執行一個或多個進程：幾乎所有這些檔案都可直接存取執行個體資料庫。

本節詳細說明要套用至複製Adobe Campaign環境的程式，亦即將來源環境還原至目標環境，導致兩個相同的工作環境。

若要這麼做，請套用下列步驟：

1. 在源環境中的所有實例上建立資料庫的副本，
1. 在目標環境的所有實例上恢復這些副本，
1. 執行 **nms:freezeInstance.js** 在目標環境上將指令碼燒錄，然後再啟動它。

   此程式不會影響伺服器及其設定。

   >[!NOTE]
   >
   >在Adobe Campaign的範疇內， **燒灼** 會結合可讓您停止所有程式與外部互動的動作：記錄、追蹤、傳送、行銷活動工作流程等。\
   >此步驟是避免多次傳送訊息的必要步驟（一次來自名義環境，一次來自重複環境）。

   >[!IMPORTANT]
   >
   >一個環境可包含數個例項。 每個Adobe Campaign執行個體都需遵守授權合約。 檢查您的授權合約，了解您可擁有的環境數量。\
   >以下過程允許您傳輸環境，而不影響已安裝的環境和實例的數量。

### 開始之前 {#before-you-start}

>[!IMPORTANT]
>
>我們強烈建議在啟動傳輸過程之前，對源環境和目標環境的所有實例運行資料庫的完整備份。 這樣，如果出現問題，您將能夠恢復備份並返回到初始配置。

為了讓此程式運作，來源和目標環境必須有相同數量的例項、相同的用途（行銷例項、傳送例項）和類似的設定。 技術配置必須符合軟體必備條件。 這兩個環境都必須安裝相同的元件。

## 實作 {#implementation}

### 轉移程式 {#transfer-procedure}

本節將通過案例研究幫助您了解將源環境傳輸到目標環境所需的步驟：我們的目標是要還原生產環境(**prod** 例項)至開發環境(**dev** 例項)，以在盡可能接近「即時」平台的情境中運作。

請謹慎執行下列步驟：複製源環境資料庫時，某些進程可能仍在進行中。 燒灼（以下步驟3）可防止訊息傳送兩次，並維持資料一致性。

>[!IMPORTANT]
>
>* 以下過程在PostgreSQL語言中有效。 如果SQL語言不同(例如Oracle)，則必須調整SQL查詢。
>* 以下命令適用於 **prod** 例項和 **dev** 例項。

>


### 步驟1 — 備份源環境(prod)資料 {#step-1---make-a-backup-of-the-source-environment--prod--data}

複製資料庫

首先，複製所有源環境資料庫。 操作取決於資料庫引擎，由資料庫管理員負責。

在PostgreSQL下，命令為：

```
pg_dump mydatabase > mydatabase.sql
```

### 步驟2 — 匯出目標環境設定（開發） {#step-2---export-the-target-environment-configuration--dev-}

每個環境的大部分設定元素都不同：外部帳戶（中間來源、路由等）、技術選項（平台名稱、資料庫ID、電子郵件地址和預設URL等）。

在目標資料庫上保存源資料庫之前，您需要導出目標環境（開發）配置。 要執行此操作，請匯出以下兩個表格的內容： **xtkoption** 和 **nmsexaccount**.

此匯出功能可讓您保留開發設定，並只重新整理開發資料（工作流程、範本、網頁應用程式、收件者等）。

要執行此操作，請對以下兩個元素執行套件匯出：

* 匯出 **xtk:option** 表格填入「options_dev.xml」檔案，但沒有具有以下內部名稱的記錄：&#39;WdbcTimeZone&#39;、&#39;NmsServer_LastPostUpgrade&#39;和&#39;NmsBroadcast_RegexRules&#39;。
* 在「extaccount_dev.xml」檔案中，匯出 **nms:extAccount** ID不是0(@id &lt;> 0)的所有記錄的表。

檢查導出的選項/帳戶數是否等於每個檔案中要導出的行數。

>[!NOTE]
>
>在包導出中要導出的行數為1000行。 如果選項或外部帳戶數超過1000，則必須執行數個匯出。
> 
>如需詳細資訊，請參閱[本區段](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>導出nmsexaccount表時，與外部帳戶（例如，中間來源、Message Center Execution、SMPP、IMS和其他外部帳戶的密碼）相關的密碼將不導出。 請務必事先存取正確的密碼，因為外部帳戶匯入回環境後，可能需要重新輸入這些密碼。

### 步驟3 — 停止目標環境（開發） {#step-3---stop-the-target-environment--dev-}

您需要在所有目標環境伺服器上停止Adobe Campaign程式。 此操作取決於您的作業系統。

您可以停止所有進程，或僅停止那些寫入資料庫的進程。

要停止所有進程，請使用以下命令：

* 在Windows中：

   ```
   net stop nlserver6
   ```

* 在Linux中：

   ```
   /etc/init.d/nlserver6 stop
   ```

使用以下命令檢查所有進程是否已停止：

```
nlserver pdump
```

>[!NOTE]
>
>在Windows中， **webmdl** 過程仍可處於活動狀態，而不會影響其他操作。

您也可以檢查系統進程是否仍在運行。

若要這麼做，請使用下列程式：

* 在Windows中：開啟 **任務管理員** 並檢查是否 **nlserver.exe** 程式。
* 在Linux中：執行 **ps aux | grep nlserver** 命令並檢查沒有 **nlserver** 程式。

### 步驟4 — 在目標環境中還原資料庫（開發） {#step-4---restore-the-databases-in-the-target-environment--dev-}

要在目標環境中恢復源資料庫，請使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 步驟5 — 警告目標環境（開發） {#step-5---cauterize-the-target-environment--dev-}

為避免故障，在目標環境啟動時，不得自動執行連結至傳送傳送和工作流程執行的程式。

要執行此操作，請運行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 步驟6 — 檢查燒灼 {#step-6---check-cauterization}

1. 檢查唯一的deliverypart是ID設為0的傳送部分：

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. 檢查傳送狀態更新是否正確：

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. 檢查工作流狀態更新是否正確：

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### 步驟7 — 重新啟動目標環境Web進程（開發） {#step-7---restart-the-target-environment-web-process--dev-}

在目標環境中，重新啟動所有伺服器的Adobe Campaign程式。

>[!NOTE]
>
>在重新啟動Adobe Campaign之前，請前往 **dev** 環境中，您可以套用其他安全程式：開始 **web** 僅模組。
>  
>若要這麼做，請編輯執行個體的設定檔案(**config-dev.xml**)，然後在每個模組（mta、stat等）的autoStart=&quot;true&quot;選項之前新增&quot;_&quot;字元。

運行以下命令以啟動Web進程：

```
nlserver start web
```

使用以下命令檢查是否只啟動Web進程：

```
nlserver pdump
```

檢查對客戶端控制台功能的訪問。

### 步驟8 — 將選項和外部帳戶匯入目標環境（開發） {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>此步驟僅應啟動Web程式。 如果情況並非如此，請在繼續之前停止其他正在運行的進程

最重要的是，在導入前檢查檔案的幾行的值(例如：「NmsTracking_Pointer」，用於選項表，以及外部帳戶表的交付或中間來源帳戶)

要從目標環境資料庫（開發）導入配置：

1. 開啟資料庫的管理控制台並清除ID不是0(@id &lt;> 0)的外部帳戶（表nms:extAccount）。
1. 在Adobe Campaign主控台中，匯入先前透過匯入套件功能建立的options_dev.xml套件。

   檢查 **[!UICONTROL Administration > Platform > Options]** 節點。

1. 在Adobe Campaign主控台中，匯入先前透過匯入套件功能建立的extaccount_dev.xml

   檢查外部資料庫是否確實已匯入 **[!UICONTROL Administration > Platform > External accounts]** .

### 步驟9 — 重新啟動所有程式並變更使用者（開發） {#step-9---restart-all-processes-and-change-users--dev-}

若要啟動Adobe Campaign程式，請使用下列命令：

* 在Windows中：

   ```
   net start nlserver6
   ```

* 在Linux中：

   ```
   /etc/init.d/nlserver6 start
   ```

使用以下命令檢查進程是否已啟動：

```
nlserver pdump
```

變更使用者以尋找已存在於開發平台上的使用者。
