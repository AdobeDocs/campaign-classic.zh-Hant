---
product: campaign
title: 版本編號升級常見問答集
description: 與活動構建升級相關的常見問題
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 85e2135d-a1a3-44f0-a4f9-de38db5c8726
source-git-commit: 56ff1f02e614a91200a8f2ca106dcc76e82f122d
workflow-type: tm+mt
source-wordcount: '2031'
ht-degree: 3%

---

# 構建升級常見問題 {#build-upgrade-faq}

![](../../assets/v7-only.svg)

Adobe Campaign 會定期更新。如果你熟悉我們的出版物 [發行說明](../../rn/using/rn-overview.md)您可能已經意識到，平均每年都會發佈2/3的小版本，其中包含新功能、改進和修復。 此外，我們定期發行只累積修正的版本編號。這種定期更新程式旨在讓您掌握最新、最好的資訊，讓您的環境保持完全安全，並明顯改進您使用我們產品的體驗。

我們的客戶必須運行最新版本的Adobe Campaign。 它還使Adobe能夠在遇到問題時更高效地提供幫助 — 在舊版本上確定、複製和修復問題通常需要更多時間，更不用說您可能遇到的某些問題很可能已在最近版本中得到解決了。

作為托管用戶，您可以自動從市場活動年度升級中獲益，而無需執行任何操作。 本地客戶和混合型客戶也可以從此版本中獲益。 如果您從舊的建置中遷移，我們建議您先升級至此版本。[了解更多資訊](../../rn/using/rn-overview.md)。

## 什麼是生成升級？

「生成升級」是指將Adobe Campaign Classic軟體更新為最新的安全生成號，但仍保持相同的主/次生成級別。 例如：Campaign Classicv7內部版本9026到營銷活動v7內部版本9032。

瞭解更多資訊 [此部分](../../rn/using/rn-overview.md)。

## 最新版的Adobe Campaign Classic是什麼？

最新Campaign Classic版本（包括新功能和文檔）在最新版本中詳細說明 [發行說明](../../rn/using/latest-release.md)。

## 我如何知道我運行的版本？

檢查您的版本 **[!UICONTROL Help > About...]** 菜單開啟它。 的 **[!UICONTROL About]**  框包含您正在為控制台和伺服器運行的版本和版本的詳細資訊。

瞭解更多資訊 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

## 生成狀態是什麼意思？

從Campaign Classic19.2開始，狀態與每個生成相關聯。

瞭解更多資訊 [此部分](../../rn/using/rn-overview.md)。

## 生成升級與版本升級是否相同？

沒有。生成升級是給定主版本內的增量更新，而版本升級是從一個主版本到另一個主版本的更改。 構建升級非常簡單，因為它們通常不涉及任何重大的體系結構、技術或資料模型更改。

另一方面，版本升級通常伴隨著重大的技術更改，而且，根據給定客戶的配置深度，可能需要進行重大配置更改和/或部分重新實施。

例如，使用上一節螢幕抓圖中的伺服器資訊：

* 構建升級將涉及從構建6880遷移到任何大於6880的構建。 例如，v6.1.1build 8222到v6.1.1build 8666

* 版本升級需要從6.0.2版移到任何大於6.0.2的版本。例如：v6.0.1build 222到v6.1.1build 8666

## 是否應在更新之前備份資料？

Adobe將在進行任何更改之前備份您的系統。 但是，如果非生產系統（開發或臨時伺服器）中存在關鍵的自定義工作，則強烈建議您在進行任何升級之前將其導出為一個軟體包。

![](assets/do-not-localize/how-to-video.png) 有關詳細資訊， [看這個視頻](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html)。

## 何時進行升級？

將為客戶提供一個日期範圍供選擇。 生產系統更改不會在節假日執行。

可以在星期一到星期四進行生成升級，星期五僅用於非生產實例。

## 生成升級需要多長時間？

執行生成升級所需的時間取決於以下幾個因素：

* 要備份或還原的資料庫大小（較大的資料庫需要更多的升級時間）
* 環境的規模（我們的許多客戶都擁有多台不同的伺服器，每台伺服器都負責特定的功能，而較大的環境需要更多的升級時間）
* 系統的複雜性（有些系統具有更多的依賴服務和連接來驗證，因此需要驗證此類系統的穩定性和效能）

生成升級是一個兩步過程：

1. 準備系統升級 — 考慮到您環境的特殊性，此階段基本上會導致在非生產環境上進行完全合格的升級。 從技術和功能角度看，升級後的環境已經過綠化，第2階段就可能發生。 第一階段，視上述因素而定，可能需要幾天到幾週。

1. 升級本身 — 生產環境已升級。 此階段通常在幾小時內執行。 對於非常複雜的環境，應該期望更長的停機時間。 在出現問題時，定義並可以執行回滾策略。

有關詳細資訊， [參閱此文檔](https://helpx.adobe.com/tw/campaign/kb/acc-build-upgrade.html)。

## 生成升級需要哪些資源？

生成升級過程需要以下資源：

* Adobe架構師 — 對於托管或雲消息/混合體系結構，架構師必須與客戶服務部協調。
* 項目經理 — 托管：托管團隊將與客戶服務團隊和客戶合作協調所有實例的升級時間表。
* Adobe Campaign管理員 — 托管：主機組執行升級。
* Adobe Campaign運營商\營銷用戶 — 運營商運行開發、test和生產實例的test。

## 如何準備生成升級？

在開發和試運行系統中，導出任何重要且必須保留的工作。 有關詳細資訊，請 [看這個視頻](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html)。

通過查看在實施結束時提供給您的團隊的文檔，來更新您對運行手冊（或由咨詢團隊/合作夥伴）中開發的關鍵路徑工作流和交付的瞭解。

確定適合維護窗口的低流量或低流量時間，因為這些時間對業務影響最小。

查看我們的 [在下面構建升級核對表](#check-list) 以及您的test計畫，並確保可以執行這些test的資源在24至48小時內可用。 完成升級。

有關詳細資訊， [參閱此文檔](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html)。

## 能否在夜間或業務非工作時間執行構建升級？

升級可以在非工作時間執行。 始終建議在沒有業務用戶連接到實例時在業務非工作時間升級環境。

## 與構建升級相關的成本是多少？

為托管客戶安裝生成升級不需要任何成本。 如果系統中有自定義開發，客戶將需要確定在升級後test這些開發所需的資源，並糾正與這些自定義開發相關的任何問題。

## 在升級過程中是否可以訪問該實例？

沒有。伺服器在升級期間關閉，以確保在升級產品時保留資料完整性。 完成後，它將重新啟動，所有服務都將恢復。

## 在升級過程中，是否會繼續從郵件中心發送這些電子郵件？

當消息中心(RT)進行升級時，它不會從實例發送電子郵件。 注意，當市場活動系統關閉時停止的所有流程在系統重新啟動時自動恢復。 這包括先前發送的交貨的活動或計畫交貨、跟蹤和度量計算。

## 工作流是否會繼續運行併發送交貨？

沒有。在生成升級期間，工作流和郵件服務都停止。 這意味著工作流將不運行，並且不會發送交貨。 系統重新啟動後，系統將恢復。 但是，Adobe強烈建議在升級後檢查所有關鍵路徑工作流以確保它們正在運行並且運行正常。

## 我的跟蹤連結在升級期間是否仍然有效？

在升級期間，跟蹤已發送的電子郵件的連結將無法正常工作，因為所有伺服器都已停止。 升級完成並重新啟動伺服器後，它們將重新運行。

## 是否需要在生成升級過程中可用？

是. 客戶應在升級其生產實例期間或之後立即向Adobe提供聯繫點。  Adobe將通過電子郵件與此人聯繫，除非作出其他安排。 這將確保關鍵任務的平穩過渡和即時驗證。 Adobe將在生成升級完成後與客戶聯繫以確認。

## 是否需要更新客戶端控制台？

是. 客戶端控制台必須與伺服器實例位於同一生成中。 升級完成後，客戶端控制台應提示您升級到最新的版本，以確保它與伺服器版本保持一致。

## 回滾計畫是什麼？ 是否保留了資料備份？

回滾計畫是使用最新的可用備份還原系統。 備份為資料中心客戶儲存7天，為AmazonWeb服務(AWS)客戶儲存14天。

## 回滾需要多長時間？

它取決於資料庫備份大小。 平均完成時間為4小時。

## 升級後，在我的系統上執行了哪些類型的test?

請參閱 [在下面構建升級核對表](#check-list)。

## 升級後必須執行哪種test?

開發和階段環境按順序或一起升級，但在升級生產實例之前需要簽收。 這允許每個客戶在簽署對生產的任何更改之前進行徹底測試。

請參閱清單 [在下面構建升級核對表](#check-list)。 客戶應運行類似的test，以及他們可能需要的環境。

## 我需要多長時間執行構建升級？

為確保系統的最佳效能、可用性和安全性，Adobe將與客戶合作，確保系統至少每年升級一次。

## 是否在進行生成升級時關閉？

是. 伺服器在升級期間關閉，以確保在升級產品時保留資料完整性。 完成後，它將重新啟動，所有服務都將恢復。

## 我應聯繫誰以開啟生成升級票證？

如果在生成升級後遇到問題，請聯繫 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 客戶服務計畫生成日期並開啟與生成升級相關的票證。

瞭解詳情 [幫助和支援選項，用於Campaign Classic](../../support.md)

## 生成升級核對表 {#check-list}

### 雲消息伺服器升級後核對表

1. 發送test遞送
   1. 驗證交貨日誌和相關工作流
   1. 驗證跟蹤日誌是否已更新
   1. 驗證鏡像頁和跟蹤連結
1. 確認所有技術工作流都處於啟動狀態
1. 驗證所有進程是否都處於活動狀態

### 營銷伺服器升級後核對清單

* 您能登錄到伺服器嗎？ 檢查市場活動客戶端控制台工作正常，沒有出現任何錯誤/警告彈出窗口。
* 確保在升級後使用與生成版本相同的控制台版本。
* 您有沒有將資料插入市場活動資料庫的Web應用程式？ 如果是，請運行它們並驗證它們是否可以通過API插入新記錄。
* 您能否成功發送test電子郵件？ 使用已知模板建立新交貨，將其發送到一個test收件人，驗證個性化，不明嫌犯連結，鏡像頁面所有工作。
* 您的所有關鍵路徑工作流是否都在運行？ 檢查工作流，開啟工作流日記帳，驗證是否沒有錯誤。
* 您的所有資料夾都存在、可見和可訪問嗎？ 瀏覽不同的資料夾並檢查。
所有內容都會顯示和顯示。
* 您的交貨是否帶有正確的時區？

   * 使用時間戳和時區驗證建立日期和修改日期
   * 驗證調度程式的執行是否在指定時間內在工作流中工作
   * 提取處於「暫停」和「失敗」狀態的工作流清單。 啟動並監視它們
   * 運行AB Testing以實現一個方案
   * Test推送通知及其深度連結跟蹤功能
   * Test發送簡訊
   * 如果連接了任何外部FDA，則test資料是否雙向發送
   * 如果你使用Adobe Campaign-Adobe Experience Manager、Adobe Campaign-Adobe Analytics、test等整合，如果它們仍像以前一樣工作

**另請參閱**

* [執行版本編號升級](../../production/using/build-upgrade.md)
* [Campaign Classic發行說明](../../rn/using/rn-overview.md)
* [幫助和支援選項，用於Campaign Classic](../../support.md)
* [每年升級計畫](../../rn/using/rn-overview.md#yearly-upgrade)
