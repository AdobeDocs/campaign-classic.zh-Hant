---
product: campaign
title: Campaign Classic 常見問題集
description: Adobe Campaign Classic v7架構、部署和功能的特定問題
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 2%

---

# Campaign Classic v7常見問題集 {#campaign-classic-v7-faq}

此常見問題集解決Adobe Campaign Classic v7架構、部署模式和v7特定功能的特定問題。

**如需Campaign常見問題的完整解答** （工作流程、傳送、對象、報表、個人化等），請參閱&#x200B;[**Campaign v8完整常見問答集**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}，此問答集提供依主題整理的詳細解答。

## Campaign Classic v7架構和部署 {#v7-architecture}

### Campaign Classic v7提供哪些託管模型？ {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7提供三種部署模式：

* **託管(Managed Services)** — 由Adobe基礎結構上的Adobe完全管理
* **內部部署** — 已在您自己的基礎結構上安裝和管理
* **混合** — 混合雲端和內部部署元件的中間來源架構

每個部署模型都有不同的功能和管理責任。 模組、選項和設定的可用性取決於您的部署型別。

[按一下這裡以深入瞭解](../../installation/using/hosting-models.md)託管模式及其差異。

**注意：** Campaign v8僅以Managed Cloud Services的形式提供。 [瞭解行銷活動v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=zh-Hant){target="_blank"}。

### 在內部部署環境與託管環境中運作有何不同？ {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7隨附一組模組和選項。 這些模組及其組態是否可用取決於安裝的[部署型別](../../installation/using/hosting-models.md)：託管(Managed Services)、混合或內部部署。

主要差異：

* **內部部署** — 完全控制安裝、基礎結構和設定。 需要內部IT資源才能進行維護、升級和安全性作業。
* **託管/Managed Services** - Adobe管理的基礎結構和維護。 自動升級並增強安全性。 有限制的直接伺服器存取。
* **Hybrid** — 結合這兩個模型的優點。 由Adobe託管的行銷執行個體，執行/中間來源分開管理。

[按一下這裡以取得完整功能矩陣](../../installation/using/capability-matrix.md)。

### 如何從內部部署/混合部署移轉至Adobe Managed Services？ {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

移轉至Adobe Managed Services可改善擴充性、安全性，並降低IT負荷。 在轉換至Campaign v8之前，這通常是踏腳石。

**關鍵點：**

* 沒有可用的自動化移轉工具 — 需要手動規劃和執行
* 強烈建議Adobe Professional Services支援
* 優點包括雲端基礎建設、自動安全性修補程式、專家支援，以及更輕鬆的v8存取途徑
* 移轉涉及盡職調查、環境稽核、資料清理、中繼移轉和生產轉換

**快速入門：**&#x200B;請聯絡您的Adobe代表，評估您的環境並透過Adobe Professional Services制定詳細的移轉計畫。

深入瞭解[移轉至Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}。

## 組建版本升級(Campaign Classic v7) {#build-upgrades-v7}

### 什麼是Campaign Classic v7的組建版本升級？ {#what-is-a-build-upgrade-v7}

組建版本升級指的是Adobe Campaign Classic v7軟體更新至最新的安全組建編號，但仍維持相同的主要/次要組建層級。 例如： Campaign Classic v7版本編號9026至Campaign v7版本編號9032。

Adobe Campaign 會定期更新。次要版本已發行，其中包含新功能、改進和修正。 此外，僅具有累積修正的組建版本會定期發行。

在本節[瞭解更多](../../rn/using/rn-overview.md)。

### 如何將Campaign Classic v7升級至最新版本？ {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic使用多種技術來傳遞價值。 這種技術組合，需要您定期升級Campaign Classic v7執行個體，以確保使用最新版本來提供優越的安全性、穩定性和效能。

**對於託管客戶：**&#x200B;您會透過最新穩定版本，自動受益於Campaign的年度升級。 Adobe會管理升級程式並協調與您進行的時機。

**對於內部部署/混合部署客戶：**&#x200B;您負責執行升級。 Adobe強烈建議每年升級至少一次。

[閱讀本節](../../production/using/build-upgrade.md)以瞭解如何更新您的環境，並閱讀[組建升級常見問答集](../../platform/using/faq-build-upgrade.md)以瞭解有關此特定主題的詳細問題。

### Adobe Campaign Classic v7的最新版本是什麼？ {#what-is-the-latest-version-v7}

最新Campaign Classic v7版本（包括新功能和檔案）已在最新[發行說明](../../rn/using/latest-release.md)中詳細說明。

### 如何知道我執行的是哪個Campaign Classic v7版本？ {#how-do-i-know-which-version-v7}

從Adobe Campaign使用者端主控台的&#x200B;**[!UICONTROL Help > About...]**&#x200B;功能表檢查您的版本和組建編號。 **[!UICONTROL About]**&#x200B;方塊包含您為主控台和伺服器執行的版本和組建的詳細資訊。

在本節[瞭解更多](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

### 組建版本升級與版本升級是否相同？ {#is-build-upgrade-same-as-version-upgrade}

沒有。組建版本升級是指定主要版本中的累加式更新，而版本升級則是主要版本之間的變更。 組建升級簡單明瞭，通常不會涉及重大的架構、技術或資料模型變更。

版本升級（例如v7到v8）通常伴隨著重大的技術變更，並且根據您的自訂，可能需要設定變更或部分重新實施。

## Campaign Classic v7設定 {#v7-configuration}

### 我可以變更Campaign Classic v7介面的語言嗎？ {#can-i-change-language-v7}

建立執行個體時，會選取Campaign Classic v7語言。 **您之後無法變更它。**

Adobe Campaign v7使用者介面提供4種語言版本：英文、法文、德文和日文。 使用者端主控台和伺服器必須設定相同的語言。 每個Campaign Classic v7執行個體只能以一種語言執行。

如果是英文，在安裝Campaign v7時，您可以選取美式英文或英式英文：它們的日期和時間格式有所不同。

[在本章節了解更多資訊](../../installation/using/creating-an-instance-and-logging-on.md)。

**注意：** Campaign v8網頁UI可讓使用者獨立變更其介面語言。 [了解更多](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}。

### 如何在Campaign Classic v7中設定安全性區域？ {#how-can-i-configure-security-zones-v7}

您可以使用Security Zones自助服務介面來管理Adobe Campaign Classic v7部署之VPN Security Zone設定中的專案。 這主要與內部部署和混合部署有關。

閱讀[本節](../../installation/using/security-zones.md)以瞭解Campaign v7中的安全性區域。

[按一下這裡以深入瞭解](https://helpx.adobe.com/tw/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} Security Zone自助服務UI。

**注意：**&#x200B;託管/Managed Services客戶應聯絡Adobe以設定安全性區域。

### Adobe Campaign Classic v7可以與輕型目錄存取協定(LDAP)整合嗎？ {#can-campaign-classic-integrate-with-ldap}

是。 作為&#x200B;**內部部署/混合式客戶**，您可以將Campaign Classic v7與LDAP目錄整合，以進行集中驗證和使用者管理。

此整合可讓您：

* 驗證您的公司LDAP目錄的使用者
* 集中式使用者和許可權管理
* 使用者群組與許可權的自動同步
* 單一登入功能

[按一下這裡以瞭解如何](../../installation/using/connecting-through-ldap.md)在Campaign Classic v7中設定LDAP整合。

**注意：** LDAP整合可用於內部部署和混合部署。 託管客戶使用Adobe IMS進行驗證。

### 內部部署的安全性最佳實務是什麼？ {#security-best-practices-on-premise}

與託管環境相比，內部部署和混合部署需要額外的安全設定和強化。

**重要安全區域：**

* 網路安全性與防火牆設定
* 資料庫存取與安全性
* 作業系統強化
* 檔案許可權與存取控制
* 安全性區域設定
* 加密（靜態和傳輸中的資料）
* 使用者存取管理
* 定期進行安全性修補
* 稽核記錄和監視

閱讀[安全性設定檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html){target="_blank"}，以探索有關安全性設定和強化內部部署的重點要素。

### 如何清除使用者端主控台快取？ {#how-do-i-clear-console-cache}

清除Campaign使用者端主控台快取可解決許多常見的顯示和功能問題。 快取會儲存本機設定檔，這些設定檔有時可能會損毀或過時。

**何時清除快取：**

* 新品牌元素未正確顯示
* 匯出/匯入函式意外失敗
* 組態變更後介面元素未更新
* 效能問題或主控台回應緩慢
* 升級至新的使用者端主控台版本之後

**如何清除快取：**

1. **軟快取已清除（請先試一次）：**
   * 開啟Campaign使用者端主控台
   * 前往&#x200B;**[!UICONTROL File]**&#x200B;功能表
   * 選取&#x200B;**[!UICONTROL Clear the local cache...]**
   * 出現提示時確認動作
   * 重新啟動使用者端主控台

2. **硬快取清除（如果軟清除無法解決問題）：**
   * 先執行軟快取清除
   * 登出並完全關閉使用者端主控台
   * 瀏覽至：
      * Windows 7/10： `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP： `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * 刪除所有名為`nlclient-config-<alphanumerical value>.xml`的XML檔案和相關聯的資料夾
   * **重要：**&#x200B;請勿刪除`nlclient_cnx.xml`檔案
   * 重新啟動使用者端主控台

深入瞭解[Campaign使用者端主控台檔案](../../platform/using/launching-adobe-campaign.md)。

## 取得協助 {#getting-help}

### 何處可以找到有關Campaign Classic v7的詳細資訊？ {#where-to-find-more-info-v7}

**檔案與資源：**

* [Campaign Classic v7檔案](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=zh-Hant){target="_blank"} — 完整檔案
* [Campaign Classic v7發行說明](../../rn/using/latest-release.md) — 最新發行資訊
* [Campaign Classic相容性對照表](../../rn/using/compatibility-matrix.md) — 支援的系統和版本
* [Campaign Classic教學課程](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant){target="_blank"} — 教學課程影片

**常見行銷活動問題：**

請參閱&#x200B;[**Campaign v8完整常見問題集**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}，其中提供下列問題的詳細解答：

* Campaign快速入門
* 輪廓與客群
* 訊息設計與傳遞
* 工作流程與自動化
* 報告與分析
* Campaign設定和配置
* 開發人員資源
* 隱私權與合規性

**社群和支援：**

* [Campaign社群論壇](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Adobe支援](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [控制面板（託管客戶）](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant){target="_blank"}

### 我應該從Campaign Classic v7移轉至Campaign v8嗎？ {#should-i-migrate-to-v8}

Campaign v8是Adobe的策略平台，適用於需要大量行銷活動、現代Web UI、雲端原生優勢和長期支援的組織。 Campaign Classic v7將於未來幾年終止支援。

**如果您：**，請考慮移轉至Campaign v8

* 處理大量資料或體驗效能問題
* 想要減少IT開銷和基礎建設管理（v8僅限於「受管理的雲端服務」）
* 需要現代化的UI和Adobe Experience Platform整合
* 想要具備自動更新功能的未來防護技術
* 目前位於託管/受管理服務上（更簡單的移轉路徑）

**重要考量：**

* Campaign v8是以Managed Cloud Services獨家提供的功能（無內部部署/混合選項）
* 需要規劃自訂和整合的移轉
* FFDA架構帶來效能，但需要某些工作流程/API調整

**後續步驟：**&#x200B;請聯絡您的Adobe代表，評估移轉準備程度並存取移轉工具。

了解更多：

* [Campaign v8總覽](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=zh-Hant){target="_blank"}
* [從Campaign Classic v7轉變到v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Campaign v8完整常見問題集](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**如需工作流程、傳送、對象、報表、個人化等促銷活動相關常見問題的詳細解答**，請造訪[Campaign v8完整常見問題集](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}。
