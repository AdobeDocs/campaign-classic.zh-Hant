---
title: 複製環境
seo-title: 複製環境
description: 複製環境
seo-description: null
page-status-flag: never-activated
uuid: b8fb8083-e3ec-4b1c-9449-73ac03508d89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 9f7118f4-aef0-469c-bbe1-b62bed674faa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cb44d439c6866d94f8e1201575ab3d3094d6ad79
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---


# 複製環境{#duplicating-environments}

## 簡介 {#introduction}

### 概觀 {#overview}

>[!CAUTION]
>
>如果您沒有對伺服器和資料庫（托管環境）的訪問權限，則將無法執行下面所述的過程。 請聯絡Adobe。

使用Adobe Campaign需要安裝和設定一或多個環境： 開發、測試、預製、生產等。

每個環境都包含一個Adobe Campaign實例，每個Adobe Campaign實例都連結到一個或多個資料庫。 應用伺服器可以執行一個或多個進程： 幾乎所有這些都可以直接訪問實例資料庫。

本節詳細說明要應用於複製Adobe Campaign環境（即將源環境還原到目標環境）的過程，從而產生兩個相同的工作環境。

若要這麼做，請套用下列步驟：

1. 在源環境中的所有實例上建立資料庫副本，
1. 在目標環境的所有實例上恢復這些拷貝，
1. 在啟動 **** 目標環境之前，先在目標環境上運行nms:freezeInstance.js燒灼指令碼。

   此過程不會影響伺服器及其配置。

   >[!NOTE]
   >
   >在Adobe Campaign中，燒灼會結 **合動作** ，讓您停止所有程式與外部互動： 記錄檔、追蹤、傳送、促銷活動工作流程等。\
   >必須執行此步驟，以避免多次傳送訊息（一次是從名義環境傳送，一次是從複製的環境傳送）。

   >[!CAUTION]
   >
   >一個環境可以包含多個實例。 每個Adobe Campaign實例都需遵守授權合約。 查看您的授權合約，瞭解您可擁有的環境數。\
   >以下過程可讓您傳輸環境，而不影響您安裝的環境和實例數。

### 開始之前 {#before-you-start}

>[!CAUTION]
>
>我們強烈建議在啟動傳輸過程之前，對源和目標環境的所有實例運行資料庫的完整備份。 這樣，如果出現問題，您將能夠恢復備份並返回初始配置。

為了讓此程式運作，源環境和目標環境必須具有相同的實例數、相同的用途（行銷實例、交付實例）和類似的配置。 技術配置必須符合軟體先決條件。 這兩個環境都必須安裝相同的元件。

## 實作 {#implementation}

### 轉移程式 {#transfer-procedure}

本節將幫助您瞭解通過案例研究將源環境傳輸到目標環境所需的步驟： 我們的目標是將生產環境(**prod** instance)還原到開發環境(**dev** instance)，以便在盡可能接近「即時」平台的環境中工作。

必須謹慎執行下列步驟： 複製源環境資料庫時，某些進程可能仍在進行中。 燒灼（下面的步驟3）可防止訊息傳送兩次，並維持資料的一致性。

>[!CAUTION]
>
>* 以下過程在PostgreSQL語言中有效。 如果SQL語言不同（例如Oracle），則必須調整SQL查詢。
>* 以下命令適用於 **prod** **instance和PostgreSQL下** dev instance的上下文。
>



### 步驟1 —— 備份源環境(prod)資料 {#step-1---make-a-backup-of-the-source-environment--prod--data}

複製資料庫

首先，複製所有源環境資料庫。 操作取決於資料庫引擎，是資料庫管理員的責任。

在PostgreSQL下，命令為：

```
pg_dump mydatabase > mydatabase.sql
```

### 步驟2 —— 導出目標環境配置(dev) {#step-2---export-the-target-environment-configuration--dev-}

每個環境的大多數配置元素都不同： 外部帳戶（中部採購、路由等）、技術選項（平台名稱、資料庫ID、電子郵件地址和預設URL等）。

在目標資料庫上保存源資料庫之前，您需要導出目標環境（開發）配置。 若要這麼做，請匯出這兩個表格的內容： **xtkoption** 和 **nmsextaccount**。

此匯出功能可讓您保留開發設定，並只重新整理開發資料（工作流程、範本、Web應用程式、收件者等）。

要執行此操作，請對以下兩個元素執行包導出：

* 將 **xtk:option** 表匯出至&#39;options_dev.xml&#39;檔案，而沒有下列內部名稱的記錄： 「WdbcTimeZone」、「NmsServer_LastPostUpgrade」和「NmsBroadcast_RegexRules」。
* 在&#39;extaccount_dev.xml&#39;檔案中，針對ID不是0(@id &lt;> 0)的所有記錄，匯出 **nms:extAccount** 表。

檢查導出的選項／帳戶數是否等於每個檔案中要導出的行數。

>[!NOTE]
>
>要在包導出中導出的行數為1000行。 如果選項或外部帳戶數超過1000個，則必須執行數個導出。
> 
>有關更多資訊，請參見[本節](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>導出nmsexaccount表時，與外部帳戶相關的密碼（例如中間採購、消息中心執行、SMPP、IMS和其他外部帳戶的密碼）不會導出。 請確定您事先擁有正確密碼的存取權，因為在將外部帳戶匯入環境後，可能需要重新輸入這些密碼。

### 步驟3 —— 停止目標環境（開發） {#step-3---stop-the-target-environment--dev-}

您必須停止所有目標環境伺服器上的Adobe Campaign程式。 此操作取決於您的作業系統。

您可以停止所有進程，或僅停止寫入資料庫的進程。

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
>在Windows中， **webmdl** 進程仍可處於活動狀態，而不會影響其他操作。

您也可以檢查系統進程是否仍在運行。

若要這麼做，請使用下列程式：

* 在Windows中： 開啟 **Task manager** ，並檢查是否沒有 **nlserver.exe** 進程。
* 在Linux中： 運行 **ps aux | grep nlserver** 命令，並檢查沒有 **nlserver** 進程。

### 步驟4 —— 恢復目標環境中的資料庫(dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

要恢復目標環境中的源資料庫，請使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 步驟5 —— 保護目標環境（開發） {#step-5---cauterize-the-target-environment--dev-}

為避免故障，在激活目標環境時，不能自動執行連結到交付發送和工作流執行的進程。

要執行此操作，請運行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 步驟6 —— 檢查燒灼 {#step-6---check-cauterization}

1. 檢查唯一的傳送部件是ID設為0的部件：

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

### 步驟7 —— 重新啟動目標環境Web進程（開發） {#step-7---restart-the-target-environment-web-process--dev-}

在目標環境中，重新啟動所有伺服器的Adobe Campaign程式。

>[!NOTE]
>
>在開發環境中重新啟動Adobe Campaign **之前** ，您可以套用其他安全程式： 僅啟 **動web** 模組。
>  
>若要這麼做，請編輯執行個體的設定檔案(**config-dev.xml**)，然後在每個模組（mta、stat等）的autoStart=&quot;true&quot;選項前加入&quot;_&quot;字元。

運行以下命令以啟動Web進程：

```
nlserver start web
```

使用以下命令檢查是否只啟動了Web進程：

```
nlserver pdump
```

檢查對客戶機控制台功能的訪問。

### 步驟8 —— 將選項和外部帳戶導入目標環境（開發） {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>此步驟僅應啟動Web程式。 如果不是這樣，請在繼續之前停止其他正在運行的進程

首先，在匯入前先檢查數行檔案的值(例如： 選項表的&#39;NmsTracking_Pointer&#39;和外部帳戶表的交付帳戶或中部來源帳戶)

要從目標環境資料庫(dev)導入配置：

1. 開啟資料庫的管理控制台並清除其ID不是0(@id &lt;> 0)的外部帳戶（表nms:extAccount）。
1. 在Adobe Campaign主控台中，匯入先前透過匯入套件功能建立的options_dev.xml套件。

   檢查節點中的選項是否確實已更 **[!UICONTROL Administration > Platform > Options]** 新。

1. 在Adobe Campaign主控台中，匯入先前透過匯入套件功能建立的extaccount_dev.xml

   檢查外部資料庫是否確實已匯入至 **[!UICONTROL Administration > Platform > External accounts]** 。

### 步驟9 —— 重新啟動所有流程並變更用戶（開發） {#step-9---restart-all-processes-and-change-users--dev-}

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
