---
product: campaign
title: 開始進行版本編號升級
description: 了解升級至新組建的關鍵步驟
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2353'
ht-degree: 3%

---

# 執行版本編號升級{#performing-a-build-upgrade}

![](../../assets/v7-only.svg)

本節將提供升級流程的深入逐步說明，以及識別和解決衝突的步驟。

建設升級必須謹慎進行，其影響必須事先充分考慮，程式必須有高度的紀律。 若要確保升級成功，請確保只有專家使用者才能執行下列步驟。 此外，我們強烈建議您先與[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)聯絡，再開始進行任何升級。

需要下列必要條件：

* 了解Campaign架構
* 系統和伺服器端知識
* 管理權限和權限

您可以在以下章節找到詳細資訊：[更新Adobe Campaign](../../production/using/upgrading.md), [移轉至新版本](../../migration/using/about-migration.md)。

對於托管和混合執行個體，您必須向Adobe技術營運團隊要求組建升級。 如需詳細資訊，請參閱底部的「常見問題」區段（若此頁面）。 另請參閱[版本編號升級常見問題集](../../platform/using/faq-build-upgrade.md)。

## 準備升級

![](assets/do-not-localize/icon_planification.png)

開始進行組建升級之前，您必須依照下列說明執行完整準備。
一旦系統準備好升級，版本升級至少需要**** 2小時。

建置升級程式需要下列資源：

* Adobe架構師 — 了解資料庫結構（現成的架構和任何已新增的其他架構、行銷活動設計，以及必須依特定順序啟動和測試的任何重要路徑功能）。
* 項目經理 — 如果組建升級涉及許多不同的實例（生產、測試、測試）和其他第三方伺服器和應用程式（資料庫、SFTP站點、報文傳送服務提供商），則使用項目經理來協調所有測試被認為是最佳做法。
* Adobe Campaign管理員 — 您的管理員了解伺服器的設定，包括但不限於：安全性、資料夾佈局、報告和導入/導出要求。 沒有管理員，請勿執行版本編號升級。
* Adobe Campaign運算子（行銷使用者） — 成功的升級需仰賴使用者成功執行其日常工作的能力。 因此，在測試升級的伺服器時，請一律至少包含您的每日操作員之一。

### 規劃

以下是如何規劃組建版本升級的關鍵點：

1. 請至少預留2小時進行升級。
1. 分發Adobe和客戶員工的聯繫詳細資訊。
1. 對於托管例項：Adobe和客戶人員將協調升級的時間以及執行人員。
1. 針對內部部署例項：客戶員工負責管理整個流程 — 如果需要在測試自定義工作流和交付邏輯方面的幫助，應引入咨詢服務。
1. 決定並確認您要升級至哪個Adobe Campaign版本 — 請參閱[Adobe Campaign Classic發行說明](../../rn/using/rn-overview.md)。
1. 確認擁有升級執行檔。

### 重要人員

組建升級程式需要下列人員參與：

* Adobe架構師：對於托管架構或混合架構，架構師必須與Adobe Campaign Client Care協調。

* 項目經理：
   * 針對內部部署安裝：客戶的內部項目領導者負責升級並管理生命週期測試。

   * 對於托管安裝：托管團隊會與Adobe Campaign客戶服務團隊及客戶合作，協調所有執行個體的升級時間軸。

* Adobe Campaign管理員：
   * 針對內部部署安裝：管理員執行升級。

   * 對於托管安裝：托管團隊會執行升級。

* Adobe Campaign運營商\市場營銷用戶：運算子會對開發、測試和生產執行個體執行測試。

### 準備版本編號升級

內部部署客戶在開始進行組建升級前，必須先執行下列準備：

1. 在升級前，請確保可匯出任何開發工作，並以套件形式匯出。

1. 對源環境和目標環境的所有實例執行資料庫的完全備份。

1. 獲取[伺服器配置檔案](../../installation/using/the-server-configuration-file.md)的最新版本。

1. [下載最新版本編號](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。[深入瞭解](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)。

在開始版本編號升級之前，您還需要知道所有的[有用的命令行](../../installation/using/command-lines.md):

* **nlserver pdump**:列出正在運行的進程
* **nlserver pdump -who**:列出活動客戶端會話
* **nlserver監視器 — 缺少**:清單缺少屬性
* **nlserver開始process@instanceName**:啟動進程
* **nlserver stop process@instanceName**:停止進程
* **nlserver重新啟動process@instanceName**:重新啟動進程
* **nlserver shutdown**:停止所有Campaign程式
* **nlserver watchdog -svc**:啟動監視程式（僅UNIX）

## 執行升級

![](assets/do-not-localize/icon_process.png)

以下程式僅由&#x200B;**內部部署**&#x200B;客戶執行。 若為托管客戶，則由托管團隊負責處理。 若要將Adobe Campaign更新為新組建，下方會說明詳細程式。

### 複製環境

以下是複製Adobe Campaign環境的方式，以便將源環境還原到目標環境，從而產生兩個相同的工作環境。

要執行此操作，請遵循下列步驟：

1. 在源環境中的所有實例上建立資料庫的副本。

1. 在目標環境的所有實例上還原這些副本。

1. 在啟動之前，先在目標環境上執行&#x200B;**nms:freezeInstance.js**&#x200B;燒灼指令碼。 這將停止所有進程與外部交互：記錄、追蹤、傳送、行銷活動工作流程等。

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 檢查燒灼，如下所示：

   * 檢查唯一的傳送部分是ID設定為&#x200B;**0**&#x200B;的傳送部分：

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * 檢查傳送狀態更新是否正確：

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * 檢查工作流狀態更新是否正確：

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### 關閉服務

要用新版本替換所有檔案，需要關閉nlserverservice的所有實例。

1. 關閉以下服務：

   * Web服務(IIS):**iisreset /stop**
   * Adobe Campaign服務：**net stop nlserver6**

   >[!NOTE]
   >
   >確保已停止重定向伺服器(webmdl)，以便IIS使用的nlsrvmod.dll檔案可以替換為新版本。

1. 通過運行&#x200B;**nlserver pdump**&#x200B;命令，驗證沒有任務處於活動狀態。 如果沒有任務，則輸出應與以下內容相似：

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 檢查Windows任務管理器以確認所有進程已停止。

### 升級Adobe Campaign伺服器應用程式

1. 運行&#x200B;**Setup.exe**&#x200B;檔案。 如果您需要下載此檔案，請訪問[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。

1. 選擇安裝模式：**更新**&#x200B;或&#x200B;**修復**。

1. 按一下&#x200B;**Next**。

1. 按一下&#x200B;**完成**:安裝程式會複製新檔案。

1. 操作完成後，按一下&#x200B;**完成**。

### 同步資源

1. 開啟命令列。

1. 運行&#x200B;**nlserver config -postupgrade -allinstances**&#x200B;以執行以下操作：

   * 同步資源
   * 更新結構
   * 更新資料庫

   >[!NOTE]
   >
   >此操作只應在nlserverweb應用程式伺服器上執行一次且執行。

   要僅同步一個資料庫，請運行以下命令：

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 檢查同步是否生成了任何錯誤或警告。

### 重新啟動服務

需要重新啟動以下服務：

* Web服務(IIS):**issreset /start**
* Adobe Campaign服務：**net start nlserver6**

### 用戶端主控台更新

客戶端控制台必須與伺服器實例位於同一個版本。

在安裝Adobe Campaign應用程式伺服器的電腦上(nlserverweb)，下載並複製檔案：

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

下次連接客戶端控制台時，窗口將通知用戶新更新的可用性，並為用戶提供下載和安裝該更新的可能性。

### 特定其他任務

某些設定需要特定的額外工作才能更新至新組建。

#### 傳送異動訊息

當您的Campaign執行個體上啟用交易式訊息（訊息中心）時，您需要執行以下額外步驟才能升級：

1. 將Message Center生產伺服器更新為所選版本。
1. 執行升級後指令碼。
1. 執行測試，並確保通過郵件中心生產實例成功接收電子郵件。
1. 升級客戶端並清除快取。
1. 導出包：
   * 使用客戶端包導出工具導出包
   * 導入架構包
   * 斷開連接並重新連接客戶端
   * 更新資料庫
   * 斷開連接並重新連接
   * 匯入管理套件
   * 匯入內容套件
   * 匯入內容管理套件
   * 斷開連接並重新連接
   * 對工作流程執行快速的健全性檢查

1. 發佈訊息中心範本，以確保伺服器與訊息中心執行個體之間的介面正常運作。
1. 運行測試以確保通過郵件中心生產實例成功接收電子郵件。
1. 在生產環境中執行工作流程測試，以確保收到傳送。

#### 中間來源

在中間來源環境中，您需要執行以下額外步驟才能升級：

1. 請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以協調中間來源伺服器的升級。
1. 執行測試連結以驗證版本已更新。 例如：

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>中間來源伺服器必須一律執行與行銷伺服器相同的版本（或更新版本）。

## 發生衝突

### 識別衝突

您需要檢查同步結果。 此程式僅由內部部署客戶執行。 若為托管客戶，則由托管團隊負責處理。 查看同步結果有兩種方法：

在命令行介面中，錯誤會以三>形字元「>>」實現，並且同步會自動停止。 警告由雙>形字元「>>」實現，並且必須在同步完成後進行解析。 在升級後的結尾處，命令提示符中將顯示一個摘要。 可能如下所示：

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

如果警告涉及資源衝突，則需要用戶注意才能解決該問題。

**postupgrade_ServerVersionNumber_TimeOfPostupgrade.log**&#x200B;檔案包含同步結果。 預設可在下列目錄中使用：**installationDirectory/var/instanceName/postupgrade**。 錯誤和警告由錯誤和警告屬性指示。

### 分析衝突

**如何找到衝突？**

您可以在相關伺服器的postupgrade.log內或Campaign用戶端介面（管理>設定>套件管理>編輯衝突）內找到衝突。

標識符為「stockOverview」且類型為「nms:webApp」的文檔與新版本衝突。

如果發現衝突，請檢查以下條件是否匹配：

* 客戶是否已修改或自訂物件？
* 物件在產品中是否已變更？

如果這兩種條件均不適用，則為誤判。 如果這兩種情況都適用，則發現了真正的衝突。

**客戶是否已修改物件？**

1. 識別衝突的對象。
1. 詢問客戶是否已修改物件。
1. 這物件有什麼不尋常的嗎？
1. 上次修改日期是否在物件的程式碼中設定？
1. 從衝突中檢查「_conflict」屬性的XML代碼。 它看起來像是自訂嗎？

**新組建中物件是否已變更？**

1. 有「通常的疑犯？」 內建Web應用程式或報告(例如：&#39;deliveryValidation&#39;、&#39;deliveryOverview&#39;、&#39;budget&#39;)。
1. 檢查變更日誌中是否有任何更新。
1. 問問Adobe Campaign專家。
1. 對代碼執行「差異」。

### 解決衝突

要解決衝突，請應用以下進程：

1. 在Adobe Campaign資源管理器中，轉至&#x200B;**管理>配置>包管理>編輯衝突**。

1. 在清單中選擇要解決的衝突。
解決衝突有三種選項：**接受新版本**、**保留當前版本**、**合併代碼（並聲明為已解析）**、**忽略衝突（不建議）**。

**何時可以接受新版本？**

* 如果您想要標準功能。
* 如果您沒有自訂（所有自訂都會移除）

**何時可以保留最新版本？**

* 如果您有自訂
* 如果您不想合併
* 如果您不需要從升級中修正衝突的物件

**何時執行合併？**

* 只能合併表單、報表和網頁應用程式。
* 若不了解程式碼，就可解決某些次要合併。
* 更複雜的合併應由具備適當技能和能力的人執行。
* 請參閱[執行合併](#perform-a-merge)。

**如果我忽視衝突呢？**

* 衝突將繼續
* 不升級對象
* 長期影響：版本不相容，客戶將不會受益於錯誤修正。

>[!IMPORTANT]
>強烈建議解決衝突。

### 執行合併{#perform-a-merge}

合併的類型不同：

1. 輕鬆合併：自訂和新元素既小又不相關，不需要編碼。
1. 無更改：接受新版本，僅更改上次更新日期，僅修改注釋、制表符、空格或新行。 範例：意外儲存。
1. 小小的變化：只變更了一行。 範例：xpathToLoad
1. 複雜合併：需要編碼時。 需要發展技能。 請參閱[複雜合併](#complex-merges)。

#### 如何合併？

1. 取得所有三個版本：原始版本、新版本和自訂版本。
1. 在原始版本和新版本之間執行「差異」。
1. 隔離變更。
1. 如果沒有變更，請保留最新版本以解決。

#### 在哪裡找到代碼？

1. 內建程式碼會儲存在資料集資料夾的XML檔案中。 查找與衝突對象匹配的XML檔案。 範例：installationDirectory\datakit\nms\fra\form\recipient.xml
1. 檢索原始版本：通過[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或其他未升級的產品安裝。
1. 擷取新版本：透過[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或客戶安裝的檔案。
1. 擷取自訂版本：從Campaign用戶端內擷取物件的原始碼。

### 如何進行比較？

1. 安裝文本或合併編輯器，例如記事本++、AraxisMerge、WinMerge。
1. 在編輯器中開啟原始檔案和新檔案。
1. 運行差異（比較兩個檔案）。
1. 識別任何差異。

### 如何合併？

1. 從自訂版本開始。
1. 套用變更。
1. 將衝突聲明為已解決，以解決衝突。
1. 檢查非回歸。

如果選擇手動解決衝突，請按以下步驟繼續：

1. 在窗口的下半部分，搜索&#x200B;**_conflict_string_**&#x200B;以查找具有衝突的實體。 隨新版本安裝的實體包含新引數，而符合舊版的實體包含自訂引數。
1. 刪除您不想保留的版本。 刪除要保留的實體的&#x200B;**_conflict_argument_**&#x200B;字串。
1. 轉到已解決的衝突。 按一下&#x200B;**Actions**&#x200B;圖示，然後選取&#x200B;**Declare as resolved**。
1. 儲存您的變更：衝突現在已經解決。

#### 複雜合併{#complex-merges}

1. 了解變更的功能：反向設計變更、檢查變更記錄、跟進Adobe Campaign專家。
1. 決定該如何處理變更。
1. 了解自訂功能：反向工程更改

執行複雜合併的步驟如下：

1. 從更改集複製代碼位
1. 貼到自訂版本
1. 定製的非回歸測試
1. 測試變更的功能
1. 執行用戶接受測試
1. 在測試環境中執行


>[!IMPORTANT]
>執行複雜合併需要開發技能。

**相關主題**

* [建置升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic發行說明](../../rn/using/rn-overview.md)
* [Campaign Classic的說明和支援選項](../../support.md)
* [[!DNL Gold Standard] 方案](../../rn/using/gs-overview.md)
