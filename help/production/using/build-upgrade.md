---
product: campaign
title: 開始進行內部升級
description: 瞭解升級到新版本的關鍵步驟
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 3%

---

# 執行版本編號升級{#performing-a-build-upgrade}



本節將為您提供有關升級過程以及識別和解決衝突的步驟的深入介紹。

建設升級必須謹慎進行，其影響必須事先充分考慮，程式必須嚴格執行。 要確保成功升級，請確保只有專家用戶才能執行下面介紹的步驟。 此外，我們強烈建議與 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 開始升級。

需要以下先決條件：

* 對活動結構的理解
* 系統和伺服器端知識
* 管理權限

您可以在以下幾節中查找詳細資訊： [更新Adobe Campaign](../../production/using/upgrading.md)。 [遷移到新版本](../../migration/using/about-migration.md)。

對於托管實例和混合實例，必須請求將生成升級至Adobe技術運營團隊。 有關此內容的詳細資訊，請參閱底部的「常見問題」部分（如果此頁面）。 另請咨詢 [構建升級常見問題](../../platform/using/faq-build-upgrade.md)。

## 準備升級

![](assets/do-not-localize/icon_planification.png)

在開始生成升級之前，必須執行完整準備，如下所述。
一旦系統準備好升級，就需要進行生成升級 **至少** 2小時。

生成升級過程需要以下資源：

* Adobe架構師 — 瞭解資料庫結構（現成架構和添加的任何其他架構、市場活動設計以及必須按特定順序啟動和測試的任何關鍵路徑功能）。
* 項目經理 — 在生成升級涉及許多不同實例（生產、試運行、測試）和其他第三方伺服器和應用程式（資料庫、SFTP站點、消息服務提供程式）的情況下，由項目經理來協調所有測試被認為是一種最佳做法。
* Adobe Campaign管理員 — 您的管理員瞭解伺服器的配置，包括但不限於：安全性、資料夾佈局、報告和導入\導出要求。 請在沒有管理員的情況下不執行生成升級。
* Adobe Campaign運營商（營銷用戶） — 成功升級依賴於用戶成功執行其日常任務的能力。 因此，在測試升級的伺服器時，始終至少包括您的日常操作員之一。

### 規劃

以下是如何規劃生成升級的關鍵點：

1. 至少保留2小時進行升級。
1. 為Adobe和客戶員工分發聯繫人詳細資訊。
1. 對於托管實例：Adobe和客戶員工將協調升級的時間和執行人員。
1. 對於內部實例：客戶員工管理整個流程 — 如果需要在測試定制工作流和交付邏輯方面的幫助，則應引入咨詢服務。
1. 確定並確認要升級到的Adobe Campaign版本 — 請參考 [Adobe Campaign Classic發佈說明](../../rn/using/rn-overview.md)。
1. 確認對升級執行檔的擁有。

### 關鍵人物

生成升級過程需要以下人員參與：

* Adobe建築師：對於托管或混合體系結構，架構師必須與Adobe Campaign客戶服務部協調。

* 項目經理：
   * 對於本地安裝：客戶的內部項目領導者負責升級並管理生命週期test。

   * 對於托管安裝：托管團隊將與Adobe Campaign客戶服務團隊和客戶合作協調所有實例的升級時間表。

* Adobe Campaign管理員：
   * 對於本地安裝：管理員執行升級。

   * 對於托管安裝：主機組執行升級。

* Adobe Campaign運營商\營銷用戶：運營商運行開發、test和生產實例的test。

### 準備生成升級

在開始生成升級之前，內部客戶需要執行以下準備：

1. 確保在升級之前可以導出任何開發工作，以包形式導出。

1. 對源環境和目標環境的所有實例執行資料庫的完全備份。

1. 獲取您的 [伺服器配置檔案](../../installation/using/the-server-configuration-file.md)。

1. [下載最新版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 [了解更多](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)。

你還需要知道 [有用的命令行](../../installation/using/command-lines.md) 開始生成升級之前：

* **nlserver pdump**:列出運行進程
* **nlserver pdump -who**:列出活動客戶端會話
* **nlserver監視器 — 缺少**:列出缺少的屬性
* **nlserver啟動process@instance-name**:啟動進程
* **nlserver停止process@instance-name**:停止進程
* **nlserver restart process@instance-name**:重新啟動進程
* **伺服器關閉**:停止所有市場活動流程
* **nlserver監視程式 — svc**:啟動監視程式（僅限UNIX）

## 執行升級

![](assets/do-not-localize/icon_process.png)

以下過程僅由 **現場** 客戶。 對於托管客戶，托管團隊負責處理。 要將Adobe Campaign更新為新生成，詳細步驟如下。

### 複製環境

以下是複製Adobe Campaign環境的方法，以便將源環境恢復到目標環境，從而產生兩個相同的工作環境。

要執行此操作，請遵循下列步驟：

1. 在源環境中的所有實例上建立資料庫的副本。

1. 在目標環境的所有實例上恢復這些副本。

1. 運行 **nms:freezeInstance.js** 在目標環境上建立指令碼，然後再啟動它。 這將停止所有進程與外部交互：日誌、跟蹤、交付、活動工作流等

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 檢查燒灼，如下所示：

   * 檢查唯一的交貨部件是ID設定為 **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * 檢查交貨狀態更新是否正確：

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

   * Web服務(IIS): **isreset /stop**
   * Adobe Campaign社： **網站停止nlserver6**

   >[!NOTE]
   >
   >確保重定向伺服器(webmdl)已停止，以便IIS使用的nlsrvmod.dll檔案可以替換為新版本。

1. 通過運行 **nlserver pdump** 的子菜單。 如果沒有任務，則輸出應與以下內容類似：

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 檢查Windows任務管理器以確認所有進程已停止。

### 升級Adobe Campaign伺服器應用程式

1. 運行 **Setup.exe** 的子菜單。 如果需要下載此檔案，請訪問 [下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。

1. 選擇安裝模式： **更新** 或 **修復**。

1. 按一下 **下一個**。

1. 按一下 **完成**:安裝程式會複製新檔案。

1. 操作完成後，按一下 **完成**。

### 同步資源

1. 開啟命令行。

1. 運行 **nlserver config - postupgrade -allinstances** 執行以下操作：

   * 同步資源
   * 更新架構
   * 更新資料庫

   >[!NOTE]
   >
   >此操作只應在nlserverweb應用程式伺服器上執行一次且僅執行一次。

   要僅同步一個資料庫，請運行以下命令：

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 檢查同步是否生成了任何錯誤或警告。

### 重新啟動服務

需要重新啟動以下服務：

* Web服務(IIS): **issreset /start**
* Adobe Campaign社： **nlserver6**

### 客戶端控制台更新

客戶端控制台必須與伺服器實例位於同一生成中。

在安裝Adobe Campaign應用程式伺服器的電腦(nlserverweb)上，下載並複製檔案：

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

下次連接客戶端控制台時，窗口將通知用戶新更新的可用性，並提供下載和安裝該更新的可能性。

### 特定的其他任務

某些配置需要特定的附加任務才能更新到新生成。

#### 傳送異動訊息

在您的市場活動實例上啟用事務性消息傳遞（消息中心）時，您需要執行以下附加步驟來升級：

1. 將消息中心生產伺服器更新為所選版本。
1. 運行postupgrade指令碼。
1. 運行test，並確保通過消息中心生產實例成功接收電子郵件。
1. 升級客戶端並清除快取。
1. 導出包：
   * 使用客戶端包導出工具導出包
   * 導入架構包
   * 斷開連接並重新連接客戶端
   * 更新資料庫
   * 斷開連接並重新連接
   * 導入管理包
   * 導入內容包
   * 導入內容管理包
   * 斷開連接並重新連接
   * 對工作流執行快速健全檢查

1. 發佈消息中心模板，以確保伺服器和消息中心實例之間的介面工作正常。
1. 運行test，確保通過郵件中心生產實例成功接收電子郵件。
1. 在生產中運行工作流test以確保接收交貨。

#### 中間來源

在中間採購環境中，您需要執行以下附加步驟來升級：

1. 聯繫人 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 協調中間採購伺服器的升級。
1. 通過運行test連結驗證版本是否已更新。 例如：

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>中間採購伺服器必須始終運行與市場營銷伺服器相同（或更新）的版本。

## 在發生衝突時

### 確定衝突

您需要檢查同步結果。 此過程僅由內部客戶執行。 對於托管客戶，托管團隊負責處理。 查看同步結果有兩種方法：

在命令行介面中，錯誤由三字形「>>>」實現，同步將自動停止。 警告由雙字形「>>」實現，並且必須在同步完成後解決。 在postupgrade的末尾，將在命令提示符下顯示摘要。 它可以是這樣的：

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

如果警告涉及資源衝突，則需要用戶注意才能解決。

的 **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** 檔案包含同步結果。 預設情況下，它可在以下目錄中使用： **installationDirectory/var/`<instance-name>`/postugrade**。 錯誤和警告屬性指示錯誤和警告。

### 分析衝突

**如何發現衝突？**

衝突可在有問題的伺服器上的postupgrade.log中或市場活動客戶端介面（「管理」>「配置」>「包管理」>「編輯衝突」）中找到。

標識符為「stockOverview」且鍵入「nms:webApp」的文檔與新版本衝突。

如果發現衝突，請檢查以下條件是否匹配：

* 客戶是否已修改或自定義對象？
* 該對象在產品中是否已更改？

如果這兩種情況都不適用，這是誤報。 如果這兩種情況都適用，則發現了真正的衝突。

**客戶是否修改了對象？**

1. 標識衝突對象。
1. 詢問客戶是否修改了對象。
1. 這東西有什麼不尋常的嗎？
1. 是否在對象代碼中設定上次修改日期？
1. 檢查衝突中的XML代碼「_conflict」屬性。 看起來像是定制嗎？

**在新生成中對象是否已更改？**

1. 有&quot;慣犯&quot;嗎。 內置Web應用程式或報告(例如：「deliveryValidation」、「deliveryOverview」、「budget」)。
1. 檢查更改日誌以瞭解任何更新。
1. 問問Adobe Campaign專家。
1. 對代碼執行「diff」。

### 解決衝突

要解決衝突，請應用以下流程：

1. 在Adobe Campaign探險家中，轉到 **管理>配置>包管理>編輯衝突**。

1. 在清單中選擇要解決的衝突。
解決衝突有三種選擇： **接受新版本**。 **保留當前版本**。 **合併代碼（並聲明為已解析）**。 **忽略衝突（不建議）**。

**我什麼時候才能接受新版本？**

* 的下界。
* 如果沒有自定義項（將刪除所有自定義項）

**我什麼時候才能保留當前版本？**

* 如果您有自定義項
* 如果不想合併
* 如果升級時不需要對衝突對象進行任何修復

**何時執行合併？**

* 只能合併表單、報表和Web應用程式。
* 某些次合併可以在不理解代碼的情況下解決。
* 更複雜的合併應該由具備適當技能和能力的人執行。
* 請參閱 [執行合併](#perform-a-merge)。

**如果我忽視衝突呢？**

* 衝突將繼續
* 將不升級對象
* 長期影響：版本不相容，客戶不會從錯誤修復中獲益。

>[!IMPORTANT]
>強烈建議解決衝突。

### 執行合併{#perform-a-merge}

合併類型不同：

1. 輕鬆合併：定制元素和新元素都很小且互不相關，不需要編碼。
1. 無更改：接受新版本，僅更改上次更新日期，只接受注釋、制表符、空格或新行。 示例：意外保存。
1. 小小的更改：只換了一行。 示例：xpathToLoad
1. 複雜合併：當需要編碼時。 需要發展技能。 請參閱 [複雜合併](#complex-merges)。

#### 如何合併？

1. 獲取所有三個版本：原始版本、新版本和自定義版本。
1. 在原始版本和新版本之間運行「差異」。
1. 隔離更改。
1. 如果沒有更改，請通過保留當前版本來解決。

#### 從哪裡找到代碼？

1. 內置代碼儲存在datakit資料夾中的XML檔案中。 查找與衝突對象匹配的XML檔案。 示例：installationDirectory\datakit\nms\fra\form\recipient.xml
1. 檢索原始版本：通過 [下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 或另一個未升級的產品安裝。
1. 檢索新版本：通過 [下載中心](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 或客戶安裝的檔案。
1. 檢索自定義版本：從市場活動客戶端中檢索對象的原始碼。

### 怎麼比較？

1. 安裝文本或合併編輯器，例如記事本++、AraxisMerge、WinMerge。
1. 在編輯器中開啟原始檔案和新檔案。
1. 運行差異（比較兩個檔案）。
1. 識別任何差異。

### 如何合併？

1. 從自定義版本開始。
1. 應用更改。
1. 通過聲明衝突已解決來解決衝突。
1. 檢查不回歸。

如果選擇手動解決衝突，請按如下方式繼續：

1. 在窗口的下部，搜索 **_衝突字串_** 查找具有衝突的圖元。 隨新版本安裝的實體包含新參數，與先前版本匹配的實體包含自定義參數。
1. 刪除不想保留的版本。 刪除 **_衝突參數_** 所保留實體的字串。
1. 轉到您已解決的衝突。 按一下 **操作** 表徵圖 **聲明為已解決**。
1. 保存更改：衝突現已解決。

#### 複雜合併{#complex-merges}

1. 瞭解更改的作用：對更改進行反向工程，檢查更改日誌，跟進Adobe Campaign專家。
1. 決定如何處理更改。
1. 瞭解自定義操作：反向工程更改

執行複雜合併的步驟如下：

1. 從更改集複製代碼位
1. 貼上到自定義版本
1. 定制非回歸test
1. Test更改函式
1. 執行用戶驗收測試
1. 在test環境中執行


>[!IMPORTANT]
>執行複雜合併需要開發技能。

**相關主題**

* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic發行說明](../../rn/using/rn-overview.md)
* [幫助和支援選項，用於Campaign Classic](../../support.md)
* [市場活動年度升級計畫](../../rn/using/rn-overview.md)
