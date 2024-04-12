---
product: campaign
title: 複製環境
description: 複製環境
feature: Monitoring
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 1%

---

# 複製環境{#duplicating-environments}



## 簡介 {#introduction}

### 概覽 {#overview}

>[!IMPORTANT]
>
>如果您沒有伺服器和資料庫（託管環境）的存取權，便無法執行下列所述的程式。 請聯絡Adobe。

使用Adobe Campaign需要安裝和設定一個或多個環境：開發、測試、預生產、生產等。

每個環境都包含一個Adobe Campaign執行個體，而每個Adobe Campaign執行個體都連結至一或多個資料庫。 應用程式伺服器可以執行一或多個處理作業：幾乎所有處理作業都可直接存取執行處理資料庫。

本節詳細說明套用於複製Adobe Campaign環境的程式，即將來源環境還原到目標環境，這會產生兩個相同的工作環境。

若要這麼做，請套用下列步驟：

1. 在來源環境的所有執行個體上建立資料庫復本，
1. 在目標環境的所有執行個體上還原這些復本，
1. 執行 **nms：freezeInstance.js** 啟動之前，先對目標環境執行燒灼程式檔。

   此程式不會影響伺服器及其設定。

   >[!NOTE]
   >
   >在Adobe Campaign的情境下， **燒灼化** 結合可讓您停止所有與外部互動之處理程式的動作：記錄、追蹤、傳遞、行銷活動工作流程等。\
   >此步驟是避免傳送訊息多次（一次來自名義環境，另一次來自重複環境）所必需的。

   >[!IMPORTANT]
   >
   >一個環境可以包含多個例項。 每個Adobe Campaign執行個體都要遵守授權合約。 檢查您的授權合約，瞭解您可以擁有多少環境。\
   >以下程式可讓您傳輸環境，而不會影響您已安裝的環境和例項數量。

### 開始之前 {#before-you-start}

>[!IMPORTANT]
>
>我們強烈建議您在開始傳輸程式之前，先針對來源和目標環境的所有執行個體執行資料庫的完整備份。 如此一來，如果發生問題，您就可以還原備份並返回初始設定。

為了讓此程式發揮作用，來源和目標環境必須具有相同的執行個體數量、相同的目的（行銷執行個體、傳遞執行個體）和類似的設定。 技術設定必須符合軟體先決條件。 兩個環境中都必須安裝相同的元件。

## 實施 {#implementation}

### 傳輸程式 {#transfer-procedure}

本節將協助您透過案例研究，瞭解將來源環境轉移至目標環境所需的步驟：我們的目標是還原生產環境(**prod** 執行個體)至開發環境(**開發** 執行個體)，以便在儘可能接近「即時」平台的內容中運作。

必須謹慎執行下列步驟：複製來源環境資料庫時，某些程式可能仍在進行中。 燒製（下方的步驟3）可防止訊息傳送兩次，並維持資料的一致性。

>[!IMPORTANT]
>
>* 下列程式在PostgreSQL語言中有效。 如果SQL語言不同(例如Oracle)，則必須調整SQL查詢。
>* 以下命令適用於的 **prod** 執行個體和 **開發** PostgreSQL下的執行個體。
>

### 步驟1 — 備份來源環境(prod)資料 {#step-1---make-a-backup-of-the-source-environment--prod--data}

複製資料庫

從複製所有來源環境資料庫開始。 作業取決於資料庫引擎，由資料庫管理員負責。

在PostgreSQL底下，命令為：

```
pg_dump mydatabase > mydatabase.sql
```

### 步驟2 — 匯出目標環境設定(dev) {#step-2---export-the-target-environment-configuration--dev-}

每個環境的大多數設定元素不同：外部帳戶（中間來源、路由等）、技術選項（平台名稱、DatabaseId、電子郵件地址和預設URL等）。

將來源資料庫儲存在目標資料庫之前，您需要匯出目標環境(dev)組態。 要執行此操作，請匯出這兩個表格的內容： **xtkoption** 和 **nmsextaccount**.

此匯出可讓您保留開發設定，並僅重新整理開發資料（工作流程、範本、Web應用程式、收件者等）。

為此，請針對下列兩個元素執行封裝匯出：

* 匯出 **xtk：option** 資料表放入&#39;options_dev.xml&#39;檔案中，不含具有下列內部名稱的記錄：&#39;WdbcTimeZone&#39;、&#39;NmsServer_LastPostUpgrade&#39;和&#39;NmsBroadcast_RegexRules&#39;。
* 在&#39;extaccount_dev.xml&#39;檔案中，匯出 **nms：extAccount** ID不是0 (@id &lt;> 0)的所有記錄表格。

檢查匯出的選項/帳戶數目是否等於每個檔案中要匯出的行數。

>[!NOTE]
>
>套件匯出中要匯出的行數為1000行。 如果選項數或外部帳戶數超過1000，您必須執行數個匯出。
> 
>如需詳細資訊，請參閱[本區段](../../platform/using/working-with-data-packages.md#exporting-packages)。

>[!NOTE]
>
>匯出nmsextaccount表格時，與外部帳戶相關的密碼（例如中間來源、訊息中心執行、SMPP、IMS和其他外部帳戶的密碼）不會匯出。 請確定您事先可以存取正確的密碼，因為在外部帳戶匯入迴環境後，可能需要重新輸入密碼。

### 步驟3 — 停止目標環境（開發） {#step-3---stop-the-target-environment--dev-}

您必須停止所有目標環境伺服器上的Adobe Campaign程式。 此作業取決於您的作業系統。

您可以停止所有處理作業，或僅停止寫入資料庫的處理作業。

若要停止所有程式，請使用下列命令：

* 在Windows中：

  ```
  net stop nlserver6
  ```

* 在Linux中：

  ```
  /etc/init.d/nlserver6 stop
  ```

使用下列命令來檢查所有處理程式是否已停止：

```
nlserver pdump
```

>[!NOTE]
>
>在Windows中， **webmdl** 程式仍可正常運作，而不會影響其他作業。

您也可以檢查是否有任何系統處理序仍在執行中。

要執行此操作，請使用下列程式：

* 在Windows中：開啟 **任務管理員** 並檢查是否有 **nlserver.exe** 程式。
* 在Linux：執行 **ps aux | grep nlserver** 命令，並檢查是否有 **nlserver** 程式。

### 步驟4 — 還原目標環境（開發）中的資料庫 {#step-4---restore-the-databases-in-the-target-environment--dev-}

若要還原目標環境中的來源資料庫，請使用下列命令：

```
psql mydatabase < mydatabase.sql
```

### 步驟5 — 燒灼目標環境（開發） {#step-5---cauterize-the-target-environment--dev-}

為了避免發生故障，在啟動目標環境時，連結至傳遞傳送和工作流程執行的程式不得自動執行。

要執行此操作，請執行以下命令：

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 步驟6 — 檢查燒灼化 {#step-6---check-cauterization}

1. 檢查唯一的deliverypart是否為ID設為0的部分：

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. 檢查交貨狀態更新是否正確：

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. 檢查工作流程狀態更新是否正確：

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### 步驟7 — 重新啟動目標環境Web程式(dev) {#step-7---restart-the-target-environment-web-process--dev-}

在目標環境中，為所有伺服器重新啟動Adobe Campaign程式。

>[!NOTE]
>
>在上重新啟動Adobe Campaign之前 **開發** 環境，您可以套用其他安全程式：啟動 **網頁** 僅限模組。
>  
>若要這麼做，請編輯您執行個體的設定檔(**config-dev.xml**)，然後為每個模組（mta、stat等）在autoStart=&quot;true&quot;選項前新增&quot;_&quot;字元。

執行以下命令以啟動Web程式：

```
nlserver start web
```

使用下列命令來檢查是否只有Web處理序啟動：

```
nlserver pdump
```

檢查對使用者端主控台的存取權功能。

### 步驟8 — 將選項和外部帳戶匯入目標環境（開發） {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>在此步驟只應啟動Web程式。 如果不是這種情況，請先停止其他正在執行的程式，然後再繼續

首先，在匯入之前，檢查檔案數行的值（例如：選項表格的「NmsTracking_Pointer」，以及外部帳戶表格的傳遞或中間來源帳戶）

若要從目標環境資料庫(dev)匯入組態：

1. 開啟資料庫的Admin Console，並清除識別碼不是0 (@id &lt;> 0)的外部帳戶（表格nms：extAccount）。
1. 在Adobe Campaign主控台中，匯入先前透過匯入套件功能建立的options_dev.xml套件。

   檢查選項是否確實已在下列欄位中更新： **[!UICONTROL Administration > Platform > Options]** 節點。

1. 在Adobe Campaign主控台中，匯入先前透過匯入套件功能建立的extaccount_dev.xml

   檢查外部資料庫是否確實已匯入 **[!UICONTROL Administration > Platform > External accounts]** .

### 步驟9 — 重新啟動所有程式並變更使用者(dev) {#step-9---restart-all-processes-and-change-users--dev-}

若要啟動Adobe Campaign程式，請使用下列命令：

* 在Windows中：

  ```
  net start nlserver6
  ```

* 在Linux中：

  ```
  /etc/init.d/nlserver6 start
  ```

使用下列命令來檢查是否已啟動程式：

```
nlserver pdump
```

變更使用者以尋找已在開發平台上存在的使用者。
