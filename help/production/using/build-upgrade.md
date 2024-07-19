---
product: campaign
title: 開始進行組建版本升級
description: 瞭解升級至新組建版本的關鍵步驟
feature: Monitoring, Upgrade
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '2324'
ht-degree: 1%

---

# 執行建置升級{#performing-a-build-upgrade}



本節將深入介紹升級程式，以及識別和解決衝突的步驟。

組建版本升級必須謹慎進行，必須事先充分考慮其影響，並且程式必須以高度的紀律性完成。 若要確保升級成功，請確定只有專家使用者才能執行下列步驟。 此外，我們強烈建議您在開始任何升級前，先聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

需要下列先決條件：

* 瞭解Campaign架構
* 系統與伺服器端知識
* 管理許可權與許可權

您可在下列章節中找到更多資訊： [更新Adobe Campaign](../../production/using/upgrading.md)、[移轉至新版本](../../migration/using/about-migration.md)。

對於託管和混合式執行個體，您必須向Adobe技術營運團隊請求組建升級。 如需詳細資訊，請參閱底部的「常見問題」區段（若此頁面）。 另請參閱[組建版本升級常見問答集](../../platform/using/faq-build-upgrade.md)。

## 準備升級

![](assets/do-not-localize/icon_planification.png)

在開始組建版本升級之前，您必須依照以下所述執行完整準備。
一旦系統準備好要升級，組建升級至少需要**1}2小時。**

組建版本升級程式需要下列資源：

* Adobe架構師 — 瞭解資料庫結構（現成可用的結構描述和已新增的任何其他結構描述、行銷活動設計，以及必須依特定順序啟動和測試的任何關鍵路徑功能）。
* 專案管理員 — 如果組建升級涉及許多不同的執行個體（生產、測試、測試）和其他協力廠商伺服器和應用程式（資料庫、SFTP站台、傳訊服務提供者），則由專案管理員協調所有測試被視為最佳實務。
* Adobe Campaign管理員 — 您的管理員知道伺服器的設定，包括但不限於：安全性、資料夾配置、報告以及匯入\匯出需求。 沒有您的管理員，請勿執行組建升級。
* Adobe Campaign操作員（行銷使用者） — 成功的升級仰賴使用者成功執行其每日任務的能力。 因此，在升級伺服器的測試中，請務必加入至少一個每日操作員。

### 規劃

以下是如何規劃組建版本升級的關鍵點：

1. 至少保留2小時進行升級。
1. 為Adobe和客戶員工分配聯絡詳細資訊。
1. 對於託管例項：Adobe和客戶員工將協調升級時間以及執行人員。
1. 對於內部部署執行個體：客戶員工管理整個流程 — 如果需要測試自訂工作流程和傳送邏輯的協助，則應引入諮詢服務。
1. 決定並確認您要升級至哪個Adobe Campaign版本 — 請參閱[Adobe Campaign Classic發行說明](../../rn/using/rn-overview.md)。
1. 確認擁有升級可執行檔。

### 重要人員

組建版本升級程式需要以下人員參與：

* Adobe架構師：針對託管或混合式架構，架構師必須與Adobe Campaign Client Care協調。

* 專案經理：
   * 對於內部部署：客戶的內部專案主管會領導升級並管理生命週期測試。

   * 針對託管安裝：託管團隊將與Adobe Campaign客戶服務團隊和客戶合作，協調所有執行個體的升級時間表。

* Adobe Campaign管理員：
   * 對於內部部署安裝：管理員會執行升級。

   * 對於託管安裝：託管團隊會執行升級。

* Adobe Campaign operator\marketing user：此操作員會在開發、測試和生產執行個體上執行測試。

### 準備組建版本升級

在開始進行組建版本升級之前，內部部署客戶需要執行下列準備：

1. 請確保在升級之前可以匯出任何開發工作，並匯出為套件。

1. 針對來源和目標環境的所有執行處理，執行資料庫的完整備份。

1. 取得[伺服器組態檔](../../installation/using/the-server-configuration-file.md)的最新版本。

1. [下載最新的組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 [了解更多](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)。

在開始組建升級之前，您還需要知道所有[有用的命令列](../../installation/using/command-lines.md)：

* **nlserver pdump**：列出執行中的處理序
* **nlserver pdump -who**：列出作用中使用者端工作階段
* **nlserver監視器 — missing**：列出遺失的屬性
* **nlserver啟動process@instance-name**：啟動處理序
* **nlserver stop process@instance-name**：停止處理序
* **nlserver重新啟動process@instance-name**：重新啟動處理序
* **nlserver關機**：停止所有Campaign處理序
* **nlserver watchdog -svc**：啟動監視器（僅限UNIX）

## 執行升級

![](assets/do-not-localize/icon_process.png)

以下程式僅由&#x200B;**內部部署**&#x200B;客戶執行。 對於託管客戶，由託管團隊負責。 若要將Adobe Campaign更新為新組建版本，以下說明詳細程式。

### 複製環境

以下說明如何複製Adobe Campaign環境，以便將來源環境還原到目標環境，從而得到兩個相同的工作環境。

要執行此操作，請遵循下列步驟：

1. 在來源環境的所有執行個體上建立資料庫復本。

1. 在目標環境的所有執行個體上還原這些復本。

1. 在啟動之前，請在目標環境中執行&#x200B;**nms：freezeInstance.js**&#x200B;燒錄指令碼。 這將停止所有與外界互動的流程：記錄、追蹤、傳送、行銷活動工作流程等。

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 檢查燒灼化，如下所示：

   * 檢查唯一傳遞部分是否為識別碼設為&#x200B;**0**&#x200B;的部分：

     ```
     SELECT * FROM neolane.nmsdeliverypart;
     ```

   * 檢查交貨狀態更新是否正確：

     ```
     SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
     ```

   * 檢查工作流程狀態更新是否正確：

     ```
     SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
     SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
     ```

### 關閉服務

若要以新版本取代所有檔案，必須關閉nlserverservice的所有執行個體。

1. 關閉下列服務：

   * Web服務(IIS)： **iisreset /stop**
   * Adobe Campaign服務： **網路停止nlserver6**

   >[!NOTE]
   >
   >請確定重新導向伺服器(webmdl)已停止，以便IIS使用的nlsrvmod.dll檔案可以取代為新版本。
   >

1. 執行&#x200B;**nlserver pdump**&#x200B;命令，驗證沒有作用中的工作。 如果沒有工作，則輸出應類似於以下內容：

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 檢查Windows工作管理員，確認所有處理程式都已停止。

### 升級Adobe Campaign伺服器應用程式

1. 執行&#x200B;**Setup.exe**&#x200B;檔案。 如果您需要下載此檔案，請存取[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。

1. 選取安裝模式： **更新**&#x200B;或&#x200B;**修復**。

1. 按一下&#x200B;**下一步**。

1. 按一下&#x200B;**完成**：安裝程式會複製新檔案。

1. 作業完成後，按一下&#x200B;**完成**。

### 同步資源

1. 開啟命令列。

1. 執行&#x200B;**nlserver config -postupgrade -allinstances**&#x200B;以執行下列動作：

   * 同步資源
   * 更新方案
   * 更新資料庫

   >[!NOTE]
   >
   >此操作只應在nlserverweb應用程式伺服器上執行一次。
   >

   若要僅同步處理一個資料庫，請執行以下命令：

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 檢查同步是否已產生任何錯誤或警告。

### 重新啟動服務

需要重新啟動下列服務：

* Web服務(IIS)： **issreset /start**
* Adobe Campaign服務： **網路啟動nlserver6**

### 使用者端主控台更新

使用者端主控台必須與伺服器執行個體位於相同的組建上。

在安裝Adobe Campaign應用程式伺服器的電腦上(nlserverweb)，下載並複製檔案：

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

下次連線使用者端主控台時，會出現一個視窗，通知使用者是否有新的更新可用，並提供他們下載和安裝更新的可能性。

### 其他特定任務

某些設定需要特定的其他任務才能更新到新的組建。

#### 交易型訊息傳遞功能

在您的Campaign執行個體上啟用異動訊息（訊息中心）時，您需要執行下列額外步驟以進行升級：

1. 將Message Center生產伺服器更新至所選版本。
1. 執行升級後指令碼。
1. 執行測試並確保透過訊息中心生產執行個體成功收到電子郵件。
1. 升級使用者端並清除快取。
1. 匯出套件：
   * 使用使用者端套件匯出工具匯出套件
   * 匯入結構描述套件
   * 中斷使用者端連線並重新連線
   * 更新資料庫
   * 中斷連線並重新連線
   * 匯入管理員套件
   * 匯入內容封裝
   * 匯入內容管理套件
   * 中斷連線並重新連線
   * 執行工作流程的快速健康狀態檢查

1. Publish Message Center範本，確保伺服器與Message Center執行個體之間的介面運作正常。
1. 執行測試以確保透過訊息中心生產執行個體成功接收電子郵件。
1. 在生產環境中執行工作流程測試，以確保接收傳遞。

#### 中間來源

在中間來源環境中，您需要執行這些額外的步驟以進行升級：

1. 聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以協調中間來源伺服器的升級。
1. 執行測試連結以驗證版本是否已更新。 例如：

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>中間來源伺服器必須一律執行與行銷伺服器相同的版本（或更新版本）。
>

## 發生衝突時

### 識別衝突

您需要檢查同步處理結果。 此程式僅由內部部署客戶執行。 對於託管客戶，由託管團隊負責。 檢視同步化結果的方式有兩種：

在命令列介面中，錯誤會以三個V形&#39;>>>&#39;具體化，而且同步會自動停止。 警告會以雙>形箭號具體化，同步處理完成後必須加以解析。 升級後結束時，命令提示字元中會顯示摘要。 如下所示：

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

如果警告與資源衝突有關，則需要使用者注意才能解決。

**postupgrade_ServerVersionNumber_TimeOfPostupgrade.log**&#x200B;檔案包含同步處理結果。 預設可在下列目錄中取得： **installationDirectory/var/`<instance-name>`/postupgrade**。 錯誤和警告屬性會指出錯誤和警告。

### 分析衝突

**如何找到衝突？**

在相關伺服器的postupgrade.log或Campaign使用者端介面（「管理>設定>封裝管理>編輯衝突」）中，可能會發現衝突。

識別碼為「stockOverview」且型別為「nms：webApp」的檔案與新版本發生衝突。

如果發現衝突，請檢查以下條件是否相符：

* 客戶是否已修改或自訂物件？
* 物件在產品中變更了嗎？

若兩者都不適用，則為誤判。 如果這兩個條件都適用，就會發現真正的衝突。

**客戶是否已修改物件？**

1. 識別衝突的物件。
1. 詢問客戶是否修改了物件。
1. 物件是否有任何不尋常之處？
1. 上次修改日期是在物件的程式碼中設定嗎？
1. 檢查衝突中的XML程式碼是否有「_conflict」屬性。 這看起來像自訂嗎？

**在新組建中物件是否已變更？**

1. 有「常見疑點」嗎？ 內建Web應用程式或報表（例如：「deliveryValidation」、「deliveryOverview」、「budget」）。
1. 檢查變更記錄檔是否有任何更新。
1. 詢問Adobe Campaign專家。
1. 對程式碼執行「diff」。

### 解決衝突

若要解決衝突，請套用下列程式：

1. 在Adobe Campaign總管中，移至&#x200B;**管理>設定>封裝管理>編輯衝突**。

1. 在清單中選取要解決的衝突。
有三個選項可解決衝突： **接受新版本**、**保留目前的版本**、**合併程式碼（並宣告為已解決）**、**忽略衝突（不建議）**。

**何時可以接受新版本？**

* 如果您想要標準特徵。
* 如果您沒有自訂（將會移除所有自訂）

**何時可以保留目前的版本？**

* 如果您有自訂
* 如果您不想合併
* 如果您不需要升級時衝突物件的任何修正

**何時執行合併？**

* 只有表單、報表和網頁應用程式可以合併。
* 有些微幅合併無需瞭解程式碼即可解決。
* 應由具備適當技能與能力的人執行更複雜的合併。
* 請參閱[執行合併](#perform-a-merge)。

**如果忽略衝突怎麼辦？**

* 衝突將持續存在
* 將不會升級物件
* 長期影響：版本不相容，客戶將無法受益於錯誤修正。

>[!IMPORTANT]
>強烈建議您解決衝突。
>

### 執行合併{#perform-a-merge}

有不同型別的合併：

1. 輕鬆合併：自訂元素和新元素很小且沒有關聯，不需要編碼。
1. 無變更：接受新版本、僅上次變更更新日期、僅註解、標籤、空格或新行。 範例：意外儲存。
1. 微不足道的變更：只變更了一行。 範例： xpathToLoad
1. 複雜合併：需要編碼時。 需要開發技能。 請參閱[複雜合併](#complex-merges)。

#### 如何合併？

1. 取得全部三個版本：原始版本、新版本和自訂版本。
1. 執行原始版本和新版本之間的「差異」。
1. 隔離變更。
1. 如果沒有變更，請保留目前版本以解決。

#### 在哪裡可以找到程式碼？

1. 內建程式碼儲存在datakit資料夾的XML檔案中。 尋找符合衝突物件的XML檔案。 範例： installationDirectory\datakit\nms\fra\form\recipient.xml
1. 擷取原始版本：透過[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或其他未升級的產品安裝。
1. 擷取新版本：透過[下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)或客戶安裝的檔案。
1. 擷取自訂版本：從Campaign使用者端中擷取物件的原始程式碼。

### 如何進行差異？

1. 安裝文字或合併編輯器，例如Notepad ++、AraxisMerge、WinMerge。
1. 在編輯器中開啟原始檔案和新檔案。
1. 執行差異（比較兩個檔案）。
1. 找出任何差異。

### 如何合併？

1. 從自訂版本開始。
1. 套用變更。
1. 將衝突宣告為已解決，以解決衝突。
1. 檢查無回歸。

如果您選擇手動解決衝突，請按照以下步驟進行：

1. 在視窗的下半部，搜尋&#x200B;**_conflict_string_**&#x200B;以找出有衝突的實體。 與新版本一起安裝的實體包含新引數，符合先前版本的實體包含自訂引數。
1. 刪除您不想要保留的版本。 刪除您要保留之實體的&#x200B;**_conflict_argument_**&#x200B;字串。
1. 移至您已解決的衝突。 按一下&#x200B;**動作**&#x200B;圖示並選取&#x200B;**宣告為已解決**。
1. 儲存變更：衝突現已解決。

#### 複雜合併{#complex-merges}

1. 瞭解變更的作用：對變更進行反向工程、檢查變更記錄，並與Adobe Campaign專家聯絡。
1. 決定如何處理變更。
1. 瞭解自訂的功用：對變更進行反向工程

以下是執行複雜合併的步驟：

1. 從變更集復製程式碼的位元
1. 貼上至自訂版本
1. 測試自訂的不回歸
1. 測試變更的功能
1. 執行使用者驗收測試
1. 在測試環境中執行


>[!IMPORTANT]
>執行複雜的合併需要開發技能。
>

**相關主題**

* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic發行說明](../../rn/using/rn-overview.md)
* [Campaign Classic的說明與支援選項](../../support.md)
* [Campaign年度升級計畫](../../rn/using/rn-overview.md)
