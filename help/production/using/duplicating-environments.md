---
product: campaign
title: 複製環境
description: 複製環境
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 1%

---

# 複製環境{#duplicating-environments}



## 簡介 {#introduction}

### 概覽 {#overview}

>[!IMPORTANT]
>
>如果您沒有訪問伺服器和資料庫（托管環境）的權限，則將無法執行下面所述的過程。 請與Adobe聯繫。

使用Adobe Campaign需要安裝和配置一個或多個環境：開發、test、預生產、生產等。

每個環境都包含一個Adobe Campaign實例，每個Adobe Campaign實例都連結到一個或多個資料庫。 應用伺服器可以執行一個或多個進程：幾乎所有這些都可以直接訪問實例資料庫。

本節詳細介紹要應用於複製Adobe Campaign環境（即將源環境恢復到目標環境）的過程，從而產生兩個相同的工作環境。

若要這麼做，請套用下列步驟：

1. 在源環境中的所有實例上建立資料庫的副本，
1. 在目標環境的所有實例上恢復這些副本，
1. 運行 **nms:freezeInstance.js** 在目標環境上建立指令碼，然後再啟動它。

   此過程不會影響伺服器及其配置。

   >[!NOTE]
   >
   >在Adobe Campaign, **燒灼** 組合使您停止所有進程與外部交互的操作：日誌、跟蹤、交付、活動工作流等\
   >此步驟是避免多次傳遞消息（一次從標稱環境傳遞，一次從重複環境傳遞）所必需的。

   >[!IMPORTANT]
   >
   >一個環境可以包含多個實例。 每個Adobe Campaign案件都須遵守許可證合同。 檢查您的許可協定，瞭解您可以擁有多少個環境。\
   >下面的過程允許您傳輸環境，而不影響已安裝的環境和實例數。

### 開始之前 {#before-you-start}

>[!IMPORTANT]
>
>我們強烈建議在啟動傳輸過程之前，為源和目標環境的所有實例運行資料庫的完整備份。 這樣，如果出現問題，您就可以恢復備份並返回到初始配置。

要使此流程正常運行，源環境和目標環境必須具有相同數量的實例、相同的用途（營銷實例、交付實例）和類似的配置。 技術配置必須符合軟體先決條件。 必須在兩個環境上安裝相同的元件。

## 實作 {#implementation}

### 轉移過程 {#transfer-procedure}

本節將幫助您通過案例研究瞭解將源環境傳輸到目標環境所需的步驟：我們的目標是恢復生產環境(**收縮** 實例)到開發環境(**開發** 實例)在盡可能接近「live」平台的上下文中工作。

必須小心執行以下步驟：複製源環境資料庫時，某些進程可能仍在進行中。 燒灼（下面步驟3）可防止兩次發送消息並保持資料一致性。

>[!IMPORTANT]
>
>* 以下過程在PostgreSQL語言中有效。 如果SQL語言不同(例如Oracle)，則必須調整SQL查詢。
>* 下面的命令適用於 **收縮** 實例和 **開發** 實例。
>


### 步驟1 — 備份源環境(prod)資料 {#step-1---make-a-backup-of-the-source-environment--prod--data}

複製資料庫

首先複製所有源環境資料庫。 該操作取決於資料庫引擎，並由資料庫管理員負責。

在PostgreSQL下，命令為：

```
pg_dump mydatabase > mydatabase.sql
```

### 步驟2 — 導出目標環境配置(dev) {#step-2---export-the-target-environment-configuration--dev-}

每個環境的大多數配置元素都不同：外部帳戶（中間採購、路由等）、技術選項（平台名稱、資料庫ID、電子郵件地址和預設URL等）。

在目標資料庫上保存源資料庫之前，需要導出目標環境(dev)配置。 為此，請導出以下兩個表的內容： **xtk選項** 和 **nmsexaccount**。

通過此導出，您可以保留開發配置並只刷新開發資料（工作流、模板、Web應用程式、收件人等）。

為此，請對以下兩個元素執行包導出：

* 導出 **xtk：選項** 表格到「options_dev.xml」檔案中，但沒有具有以下內部名稱的記錄：「WdbcTimeZone」、「NmsServer_LastPostUpgrade」和「NmsBroadcast_RegexRules」。
* 在「extaccount_dev.xml」檔案中，導出 **nms:extAccount** ID不為0(@id &lt;> 0)的所有記錄的表。

檢查導出的選項/帳戶數是否等於每個檔案中要導出的行數。

>[!NOTE]
>
>要在包導出中導出的行數為1000行。 如果選項或外部帳戶的數量超過1000，則必須執行多個導出。
> 
>如需詳細資訊，請參閱[本區段](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>導出nmsexaccount表時，與外部帳戶相關的密碼（例如，中間採購、消息中心執行、SMPP、IMS和其他外部帳戶的密碼）不會導出。 請確保您提前擁有正確密碼的訪問權限，因為在將外部帳戶導入回環境中後可能需要重新輸入這些密碼。

### 步驟3 — 停止目標環境（開發） {#step-3---stop-the-target-environment--dev-}

您需要停止所有目標環境伺服器上的Adobe Campaign進程。 此操作取決於您的作業系統。

您可以停止所有進程，或只停止寫入資料庫的進程。

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
>在Windows中， **網路模型** 進程仍可處於活動狀態，而不會影響其他操作。

您還可以檢查是否沒有系統進程仍在運行。

要執行此操作，請使用以下過程：

* 在Windows中：開啟 **任務管理器** 並檢查是否 **nlserver.exe** 進程。
* 在Linux中：運行 **ps aux | grep nlserver** 命令並檢查 **nlserver** 進程。

### 步驟4 — 恢復目標環境中的資料庫（開發） {#step-4---restore-the-databases-in-the-target-environment--dev-}

要在目標環境中恢復源資料庫，請使用以下命令：

```
psql mydatabase < mydatabase.sql
```

### 步驟5 — 保護目標環境（開發） {#step-5---cauterize-the-target-environment--dev-}

為避免故障，在目標環境被激活時，不能自動執行連結到傳遞發送和工作流執行的進程。

為此，請運行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 步驟6 — 檢查燒灼 {#step-6---check-cauterization}

1. 檢查唯一的交貨部件是ID設定為0的部件：

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. 檢查交貨狀態更新是否正確：

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. 檢查工作流狀態更新是否正確：

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### 步驟7 — 重新啟動目標環境Web進程（開發） {#step-7---restart-the-target-environment-web-process--dev-}

在目標環境中，重新啟動所有伺服器的Adobe Campaign進程。

>[!NOTE]
>
>在重新啟動Adobe Campaign之前 **開發** 環境中，您可以應用附加的安全過程：開始 **網** 僅模組。
>  
>為此，請編輯實例的配置檔案(**config-dev.xml**)，然後在每個模組（mta、stat等）的autoStart=&quot;true&quot;選項前添加&quot;_&quot;字元。

運行以下命令以啟動Web進程：

```
nlserver start web
```

使用以下命令檢查是否只啟動了Web進程：

```
nlserver pdump
```

檢查對客戶端控制台功能的訪問。

### 步驟8 — 將選項和外部帳戶導入目標環境（開發） {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>在此步驟中只應啟動Web進程。 如果不是這樣，請停止其他正在運行的進程，然後繼續

最重要的是，在導入前檢查檔案的幾行值(例如：選項表和外部帳戶表的交貨帳戶或中間採購帳戶的「NmsTracking_Pointer」)

要從目標環境資料庫(dev)導入配置：

1. 開啟資料庫的管理控制台並清除ID不為0的外部帳戶（表nms:extAccount）(@id &lt;> 0)。
1. 在Adobe Campaign控制台中，導入以前通過導入包功能建立的options_dev.xml包。

   檢查選項是否確實已在 **[!UICONTROL Administration > Platform > Options]** 的下界。

1. 在Adobe Campaign控制台中，導入以前通過導入包功能建立的extaccount_dev.xml

   檢查外部資料庫是否確實已導入 **[!UICONTROL Administration > Platform > External accounts]** 。

### 步驟9 — 重新啟動所有進程並更改用戶（開發） {#step-9---restart-all-processes-and-change-users--dev-}

要啟動Adobe Campaign進程，請使用以下命令：

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

更改用戶以查找已存在於開發平台上的用戶。
