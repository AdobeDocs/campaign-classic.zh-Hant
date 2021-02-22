---
solution: Campaign Classic
product: campaign
title: 開始使用建置升級
description: 瞭解升級至新建版本的關鍵步驟
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 33debcd6e399d2780277644103a620d46c22022e
workflow-type: tm+mt
source-wordcount: '2368'
ht-degree: 2%

---


# 執行版本編號升級{#performing-a-build-upgrade}

本節將提供升級程式的深入說明，以及識別和解決衝突的步驟。

建設升級必須謹慎進行，其影響必須事先充分考慮，程式必須嚴格執行。 為確保成功升級，請確定只有專家使用者才能執行下列步驟。 此外，我們強烈建議您在開始任何升級之前，先聯絡[Adobe客戶服務。](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)

需要下列必要條件：

* 瞭解促銷活動架構
* 系統與伺服器端知識
* 管理權限

您可以在下列章節中找到更多資訊：[更新Adobe Campaign](../../production/using/upgrading.md)、[移轉至新版本](../../migration/using/about-migration.md)。

對於代管和混合型例項，您必須向Adobe技術營運團隊申請組建升級。 如需詳細資訊，請參閱本頁下方的「常見問題」區段。 另請參閱[組建升級常見問答集](../../platform/using/faq-build-upgrade.md)。

## 準備升級

![](assets/do-not-localize/icon_planification.png)

在開始構建版本升級之前，您必須按照以下說明執行完整準備。
一旦系統準備好升級後，構建升級至少需要**** 2小時。

建立升級程式需要下列資源：

* adobe架構設計人員——瞭解資料庫結構（即裝即用的架構和任何已新增的其他架構、促銷活動設計，以及任何必須依特定順序啟動和測試的重要路徑功能）。
* 專案經理——如果建置升級涉及許多不同的例項（生產、測試、測試）和其他協力廠商伺服器和應用程式（資料庫、SFTP網站、傳訊服務供應商），則建議由專案經理來協調所有測試，視為最佳實務。
* adobe Campaign管理員——您的管理員瞭解伺服器的設定，包括但不限於：安全性、檔案夾配置、報告和匯入\匯出需求。 請勿在沒有管理員的情況下執行組建升級。
* adobe Campaign營運商（行銷使用者）-成功升級有賴於使用者成功執行其每日工作的能力。 因此，在測試升級的伺服器時，請務必至少包含您的每日營運商之一。

### 規劃

以下是如何規劃建置升級的關鍵點：

1. 升級至少需要2小時。
1. 為Adobe和客戶員工分發聯絡資訊。
1. 對於托管實例：Adobe和客戶員工將協調升級的時間，以及執行人員。
1. 對於內部部署實例：客戶員工負責管理整個流程——如果需要協助測試自訂工作流程和傳送邏輯，則應提供諮詢服務。
1. 確定並確認您要升級至哪個Adobe Campaign版本——請參閱[Adobe Campaign Classic發行說明](../../rn/using/rn-overview.md)。
1. 確認擁有升級執行檔。

### 關鍵人物

建置升級程式需要以下人員參與：

* Adobe架構設計人員：對於代管或混合式架構，架構設計人員必須與Adobe Campaign Client Care協作。

* 專案經理：
   * 針對內部部署安裝：客戶內部的「項目領導者」負責引導升級並管理生命週期測試。

   * 針對代管安裝：代管團隊將與Adobe Campaign客戶服務團隊及客戶合作，協調所有例項的升級時間。

* Adobe Campaign管理員：
   * 針對內部部署安裝：管理員執行升級。

   * 針對代管安裝：代管團隊會執行升級。

* Adobe Campaign營運商\行銷使用者：營運商會對開發、測試和生產執行個體執行測試。

### 準備構建版本升級

在開始建置升級之前，內部部署客戶需要執行下列準備：

1. 確保在升級前可匯出任何開發工作，並匯出為套件。

1. 對源環境和目標環境的所有實例執行資料庫完整備份。

1. 獲取[伺服器配置檔案](../../installation/using/the-server-configuration-file.md)的最新版本。

1. [下載最新版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。[進一步瞭解](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)。

在開始構建升級之前，您還需要瞭解所有[有用的命令行](../../installation/using/command-lines.md):

* **nlserver pdump**:列出運行進程
* **nlserver pdump -who**:列出活動客戶端會話
* **nlserver監視器-missing**:清單缺少的屬性
* **nlserver啟動process@instanceName**:啟動流程
* **nlserver stop process@instanceName**:停止進程
* **nlserver重新啟動process@instanceName**:重新啟動進程
* **nlserver shutdown**:停止所有促銷活動程式
* **nlserver watchdog -svc**:啟動監視程式（僅限UNIX）

## 執行升級

![](assets/do-not-localize/icon_process.png)

以下過程僅由&#x200B;**on-premise**&#x200B;客戶執行。 對於代管客戶，由代管團隊負責處理。 若要將Adobe Campaign更新為新建版本，詳細程式如下所述。

### 複製環境

以下是複製Adobe Campaign環境的方式，以便將來源環境還原至目標環境，產生兩個相同的工作環境。

要執行此操作，請遵循下列步驟：

1. 在源環境中的所有實例上建立資料庫的副本。

1. 在目標環境的所有實例上恢復這些拷貝。

1. 在啟動目標環境之前，在目標環境上運行&#x200B;**nms:freezeInstance.js**&#x200B;燒灼指令碼。 這將停止所有進程與外部的交互：記錄檔、追蹤、傳送、促銷活動工作流程等。

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 檢查燒灼，如下所示：

   * 檢查唯一的傳送部件是ID設定為&#x200B;**0**&#x200B;的部件：

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

   * 網站服務(IIS):**iisreset /stop**
   * Adobe Campaign服務：**net stop nlserver6**

   >[!NOTE]
   >
   >請確定已停止重定向伺服器(webmdl)，以便IIS使用的nlsrvmod.dll檔案可以替換為新版本。

1. 運行&#x200B;**nlserver pdump**&#x200B;命令，驗證沒有任務處於活動狀態。 如果沒有任務，則輸出應與以下內容類似：

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 檢查Windows任務管理器以確認所有進程都已停止。

### 升級Adobe Campaign Server應用程式

1. 運行&#x200B;**Setup.exe**&#x200B;檔案。 如果您需要下載此檔案，請存取[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。

1. 選擇安裝模式：**Update**&#x200B;或&#x200B;**Repair**。

1. 按一下&#x200B;**Next**。

1. 按一下&#x200B;**完成** :安裝程式會複製新檔案。

1. 操作完成後，按一下&#x200B;**完成**。

### 同步資源

1. 開啟命令行。

1. 運行&#x200B;**nlserver config -postupgrade -allinstances**&#x200B;以執行以下操作：

   * 同步資源
   * 更新結構描述
   * 更新資料庫

   >[!NOTE]
   >
   >此操作僅應在nserverweb應用程式伺服器上執行一次且僅執行一次。

   要僅同步一個資料庫，請運行以下命令：

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 檢查同步是否生成了任何錯誤或警告。

### 重新啟動服務

需要重新啟動以下服務：

* 網站服務(IIS):**issreset /start**
* Adobe Campaign服務：**net start nlserver6**

### 客戶端控制台更新

客戶機控制台必須與伺服器實例位於同一版本。

在安裝Adobe Campaign應用程式伺服器的機器上(nserverweb)，下載並複製檔案：

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

下次連接客戶機控制台時，會出現一個窗口通知用戶新更新的可用性，並為用戶提供下載和安裝該更新的可能性。

### 特定的其他任務

某些配置需要特定的附加任務才能更新為新構建版本。

#### 異動訊息傳送

當您的促銷活動例項啟用「交易式訊息（訊息中心）」時，您必須執行下列其他步驟以升級：

1. 將消息中心生產伺服器更新為選定的版本。
1. 執行postupgrade指令碼。
1. 執行測試，並確保電子郵件能通過郵件中心生產實例成功接收。
1. 升級客戶端並清除快取。
1. 匯出套件：
   * 使用客戶端包導出工具導出包
   * 導入架構包
   * 斷開連接並重新連接客戶端
   * 更新資料庫
   * 斷開連接並重新連接
   * 匯入管理套件
   * 匯入內容套件
   * 匯入內容管理套件
   * 斷開連接並重新連接
   * 對工作流程執行快速的例行性檢查

1. 發佈消息中心模板以確保伺服器和消息中心實例之間的介面工作正常。
1. 執行測試，確保電子郵件能通過郵件中心生產實例成功接收。
1. 在生產中執行工作流程測試，以確保收到傳送。

#### 中部採購

在中端採購環境中，您需要執行以下其他步驟才能升級：

1. 聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以協調Mid-Sourcing伺服器的升級。
1. 執行測試連結以驗證版本已更新。 例如：

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Mid-Sourcing伺服器必須一律執行與行銷伺服器相同的版本（或更新版本）。


## 若有衝突

### 識別衝突

您需要檢查同步結果。 此程式僅由內部部署客戶執行。 對於代管客戶，由代管團隊負責處理。 查看同步結果有兩種方法：

在命令行介面中，錯誤由三個chevron &#39;>>>&#39;實現，並自動停止同步。 警告由雙雪佛龍「>>」實現，並且必須在同步完成後解決。 在postupgrade的末尾，將在命令提示符中顯示一個摘要。 它可能如下所示：

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

如果警告涉及資源衝突，則需要使用者注意才能解決。

**postupgrade_ServerVersionNumber_TimeOfPostupgrade.log**&#x200B;檔案包含同步結果。 預設情況下，它位於以下目錄：**installationDirectory/var/instanceName/postupgrade**。 錯誤和警告由錯誤和警告屬性指示。

### 分析衝突

**如何找到衝突？**

衝突可在相關伺服器的postupgrade.log中，或在促銷活動用戶端介面（「管理>設定>套件管理>編輯衝突」）中找到。

具有「stockOverview」識別碼並鍵入「nms:webApp」的檔案與新版本衝突。

如果發現衝突，請檢查以下條件是否匹配：

* 客戶是否已修改或自訂物件？
* 產品中的物件是否已變更？

如果這兩種情況都不適用，這是假陽性。 如果這兩種情況都適用，就會發現真正的衝突。

**客戶是否已修改物件？**

1. 識別衝突的對象。
1. 詢問客戶是否修改了對象。
1. 這個物體有什麼不尋常的嗎？
1. 對象代碼中是否設定了上次修改日期？
1. 從衝突中檢查「_conflict」屬性的XML代碼。 它看起來像是自訂嗎？

**物件是否已在新建版本中變更？**

1. 有&quot;常客&quot;嗎？ 內建Web應用程式或報表(例如：&#39;deliveryValidation&#39;、&#39;deliveryOverview&#39;、&#39;budget&#39;)。
1. 檢查更改日誌中是否有更新。
1. 向Adobe Campaign專家諮詢。
1. 對代碼執行「比較」。

### 解決衝突

要解決衝突，請應用以下流程：

1. 在Adobe Campaign檔案總管中，前往&#x200B;**管理>設定>封裝管理>編輯衝突**。

1. 在清單中選擇要解決的衝突。
解決衝突有三種選擇：**接受新版**、**保留目前版本**、**合併程式碼（並宣告為已解決）**、**忽略衝突（不建議）**。

**我何時可以接受新版本？**

* 如果您想要標準功能，
* 如果您沒有自訂項目（所有自訂項目都將移除）

**我何時可以保留目前的版本？**

* 如果您有自訂項目
* 如果您不想合併
* 如果您不需要對升級中衝突的物件進行任何修正

**何時執行合併？**

* 只有表單、報表和Web應用程式才能合併。
* 有些次要合併可以解決，而不需瞭解程式碼。
* 更複雜的合併應由具備適當技能和能力的人執行。
* 請參閱[執行合併](#perform-a-merge)。

**如果我忽視衝突呢？**

* 衝突將繼續存在
* 對象將不升級
* 長期影響：版本不相容，客戶將不會從錯誤修正中獲益。

>[!IMPORTANT]
>強烈建議您解決衝突。


### 執行合併{#perform-a-merge}

合併類型不同：

1. 輕鬆合併：自訂和新元素很小且不相關，不需要撰寫程式碼。
1. 無變更：接受新版本，僅更改上次更新日期，只接受注釋、制表符、空格或新行。 範例：意外儲存。
1. 瑣碎變更：只變更了一行。 範例：xpathToLoad
1. 複雜的合併：當需要編碼時。 需要開發技能。 請參閱[複雜合併](#complex-merges)。

#### 如何合併？

1. 取得所有三個版本：原始版本、新版本和自訂版本。
1. 在原始版本和新版本之間執行「差異」。
1. 隔離變更。
1. 如果沒有變更，請保留目前版本以解決。

#### 在哪裡找到代碼？

1. 內建程式碼會儲存在XML檔案的datakit資料夾中。 尋找符合衝突物件的XML檔案。 範例：installationDirectory\datakit\nms\fra\form\recipient.xml
1. 擷取原始版本：透過[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或其他未升級的產品安裝。
1. 擷取新版本：透過[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或客戶安裝的檔案。
1. 擷取自訂版本：從促銷活動用戶端擷取物件的原始碼。

### 如何做比較？

1. 安裝文本或合併編輯器，例如Notepad ++、AraxisMerge、WinMerge。
1. 在編輯器中開啟原始檔案和新檔案。
1. 運行比較（比較兩個檔案）。
1. 識別任何差異。

### 如何合併？

1. 從自訂版本開始。
1. 套用變更。
1. 通過聲明衝突已解決來解決衝突。
1. 檢查是否有未回歸。

如果您選擇手動解決衝突，請按如下步驟進行：

1. 在窗口的下半部分中，搜索&#x200B;**_conflict_string_**&#x200B;以查找具有衝突的實體。 隨新版本安裝的實體包含新引數，與舊版相符的實體包含自訂引數。
1. 刪除您不想保留的版本。 刪除您保留的實體的&#x200B;**_conflict_argument_**&#x200B;字串。
1. 前往您已解決的衝突。 按一下&#x200B;**Actions**&#x200B;表徵圖，然後選擇&#x200B;**Declare as resolved**。
1. 儲存變更：衝突現已解決。

#### 複雜合併{#complex-merges}

1. 瞭解變更的功能：對變更進行逆向工程、檢查變更記錄、向Adobe Campaign專家跟進。
1. 決定如何處理變更。
1. 瞭解自訂功能：逆向工程變更

執行複雜合併的步驟如下：

1. 從更改集複製代碼位
1. 貼至自訂版本
1. 定製的非回歸檢驗
1. 測試變更的功能
1. 執行用戶驗收測試
1. 在測試環境中執行


>[!IMPORTANT]
>執行複雜合併需要具備開發技巧。


**相關主題**

* [建立升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic發行說明](../../rn/using/rn-overview.md)
* [Campaign Classic的說明與支援選項](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Gold Standard計畫](https://helpx.adobe.com/tw/campaign/kb/gold-standard.html)