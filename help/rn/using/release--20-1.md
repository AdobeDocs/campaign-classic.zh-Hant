---
product: campaign
title: 第 20.1 發行版本
description: 第 20.1 發行版本
feature: Overview
role: User
level: Beginner
exl-id: 7e4234c9-3d8f-4014-a870-75e91cfad725
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 19%

---

# 第 20.1 發行版本{#release-20-1}

![](../../assets/v7-only.svg)

## ![](assets/do-not-localize/limited_2.png)發行版本 20.1.4 - 版本編號 9126 {#release-20-1-4-build-9126}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2021年 3 月 22 日_

* 修正迴歸，防止在傳遞中使用主控台的某些元件，例如日期選擇器和影像管理。 （NEO-31453、NEO-31454）

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2020 年 12 月 23 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在 **2021 年 6 月 30 日**&#x200B;後與 Campaign 連線。[深入瞭解](../../technotes/using/ims-updates.md)
>
> * 此版本隨附[安全性修正](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。


* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)

## ![](assets/do-not-localize/red_2.png)發行版本 20.1.3 - 版本編號 9124{#release-20-1-3-build-9124}

_2020年5月6日_

* 修正&#x200B;**檔案傳輸**&#x200B;活動使 SFTP 金鑰驗證無法在 Debian 9 運作的問題。(NEO-23183)

## ![](assets/do-not-localize/red_2.png)發行版本 20.1.2 - 版本編號 9123{#release-20-1-2-build-9123}

_2020 年 3 月 13 日_

* 修正無法在Red Hat 7伺服器上部署版本的問題。 (NEO-23332)

## ![](assets/do-not-localize/red_2.png)發行版本 20.1 - 版本編號 9122{#release-20-1-build-9122}

_2020年2月17日_

**有哪些新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>SnowflakeFDA連接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake是完全受管理的雲資料倉庫，專門用於在儲存和計算級別上擴展。 透過這個新連接器，Adobe Campaign現在可以運用Snowflake的強大功能執行大資料分段。 此連接器可供所有客戶使用，包括由Adobe托管。</p>
    <p>如需詳細資訊，請參閱 <a href="../../installation/using/configure-fda-snowflake.md">詳細檔案</a> 和 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">教學課程影片</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>HadoopFDA連接器增強功能</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>hadoopFDA Connector已經過改良，可支援Hadoop3.0和Cloudera。</p>
    <p>如需詳細資訊，請參閱<a href="../../installation/using/configure-fda-hadoop.md">詳細文件</a>以瞭解詳情。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 改善報表設定的安全性，以防止點按劫持。 這適用於新報表。 對於舊報表，您必須重新發佈以套用變更。 (NEO-13282)

* 修正cryptString中的小記憶體問題。 (NEO-20071)

* 已改善監視器JSP，以修正內部IP洩漏。 (NEO-16821)

* 修正可向非管理員使用者顯示堆疊追蹤資訊的問題。 (NEO-12388)

* 改善對先前工作階段快取資料的管理。 (NEO-17039)

* 修正登入.log檔案無法透過IMS記錄成功登入嘗試的問題。 (NEO-11004)

**功能改善**

* iOS 13現在支援搭配HTTP2連接器使用。

* 改善推播通知功能（nms:address和nms:appSubscriptionRcp）所使用表格的隔離管理和清除。 針對iOS（僅限HTTP2連接器），已停用的Token處理方式與Android相同。 NmsAppSubscriptionRcp表中現在設定了禁用標誌。 [閱讀全文](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 已在 **JavaScript程式碼** 和 **進階JavaScript程式碼** 定義逾時期間的工作流程活動。 這可防止JavaScript執行階段執行太長。 如果經過逾時期間，工作流程就會停止。 預設逾時為1小時。 [閱讀全文](../../workflow/using/sql-code-and-javascript-code.md)

* 在中間來源伺服器上找不到相符的相關性時，現在會停止傳送分析，並顯示對應的錯誤訊息。

* 現在支援Postgres的資料庫故障切換：當資料庫伺服器當機並重新啟動時，Campaign現在會自動重新連線至它。

* 此 **開始掛起** 「管理>稽核>工作流程狀態」節點已新增「檢視」。 這可讓您監視執行個體上等待由啟動的所有工作流程 **operationMgt** 程式。 此檢視隨附行銷活動套件。 [閱讀全文](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**其他變更**

* 在Linux上，nlserver服務啟動現在使用系統單元，而非/etc/init.d/nlserver6指令碼。 安裝20.1包時，會自動遷移到新的啟動方案。 仍提供/etc/init.d/nlserver6，但為了與nlserver服務（啟動、重新啟動、停止等）互動，我們建議您直接使用systemctl命令。

* 最耗用的自訂表格已從 **xtkNewId** 序列至專用序列。 [閱讀全文](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* 改進了可能受不必要資料庫連接影響的查詢效能。

* 改進資料庫更新嚮導的效能，以減少SQL陳述式，以優化響應時間。

* 資料庫記錄管理已增強。

* 連接池的穩健性已得到改善，這可能防止意外連接故障的發生頻率過高。

* 已增強在發生軟錯誤時傳送要隔離之地址的電子郵件地址驗證規則。 [閱讀全文](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 針對Debian，現在當系統PCRE程式庫可用時，Campaign會使用它們。

* Campaign現在允許使用更新的系統ODBC程式庫。

* 開啟連線以載入豐富影像時，已將逾時新增至LINE servlet。 如果影像載入所花的時間過長，Servlet會停止連線，以避免瓶頸。

**修補程式**

* 修正了使用Hadoop連接器時的帳戶金鑰加密問題。

* 修正因實作SSL憑證而導致使用者連線在Windows伺服器上失敗的回歸問題。 (NEO-20629)

* 修正了當工作流程ID為負數時，增量查詢活動的問題。 (NEO-19779)

* 修正透過NetezzaFDA連接器執行查詢時的編碼問題。 (NEO-19594)

* 修正使用中的POST方法時， **網頁下載** 工作流程事件活動。

* 修正產生優惠方案主張的問題。 (NEO-18176)

* 修正使用贏取網路表單範本時的頁尾顯示問題。

* 修正剖析連續傳送內容中的URL時，可能導致當機的問題。 (NEO-16910)

* 修正 **開始** 和 **結束** 建立新促銷活動時不會計算的欄位。

* 修正 **檔案下載** 使用URL時的工作流程活動。

* 修正預覽報表查詢活動中匯入的清單時的問題。 (NEO-13119)

* 修正選取 **由Campaign提供** 電子郵件編輯器中的個人化區塊。

* 客戶端與伺服器之間的網路通信已得到改善。

* 修正在相同行銷活動中建立太多工作流程的問題。 現在，您無法建立超過28個工作流程。 此時會顯示警告。

* 修正使用 **選取的欄** 調解選項(位於 **聯合** 工作流程活動。

* 修正了在工作流程中使用損毀的擴充清單時，可能發生的主控台當機問題。 (NEO-18096)

* 修正工作流程中可能發生的各種主控台當機問題(NEO-18010、NEO-18032)

* 修正允許執行 **外部信號** 工作流活動，即使它被禁用。 (NEO-17524)

* 修正建立新結構時的問題。

* 修正傳送SMS訊息時的追蹤問題。 (NEO-19595)

* 修正傳遞指標中顯示錯誤目標對象數的問題。

* 修正透過工作流程活動產生描述性報表時，顯示錯誤百分比的問題。 (NEO-14314)

* 修正當時間檢視參數時，傳送輸送量報表顯示不同數字的問題。 (NEO-11783)

* 修正「追蹤」工作流程無法更新交易式訊息追蹤指標的問題。 (NEO-17770)

* 修正透過SOAP要求選件時，造成Web程式當機並重新啟動的回歸問題。 (NEO-19482)

* 修正了如果上傳目錄為遠端共用位置，則無法將資料上傳至公用資源的問題。 (NEO-19361)

* 修正 **從Adobe Experience Cloud匯入對象** 技術工作流程持續失敗。 (NEO-18463)

* 修正使用從Experience Manager匯入的範本時，無法傳送傳遞的問題。 (NEO-17540)

* 修正了升級至9032組建版本並防止執行個體透過SSL通訊協定連線至FTP伺服器的問題。 (NEO-20498)

* 修正刪除、插入或更新大量資料時，使用 **更新資料** 以FDA結構為目標維度的工作流程中的活動。 (NEO-13280)

* 修正當HTML內容標籤外部有Javascript程式碼時，無法傳送電子郵件的問題。 (NEO-18628)

* 修正嘗試從已傳送訊息的傳送記錄顯示鏡像頁面時發生的問題。 (NEO-17976)

* 修正無法 **鏡像頁面的連結** 個人化區塊，不會顯示在 **文字內容** 按一下 **匯入HTML** 傳遞。 (NEO-17568)

* 按一下已釐清過期之鏡像頁面的連結時，會顯示錯誤訊息。 (NEO-17340)

* 修正無法在 **資料分送** 建立畫面。

* 修正以亞洲/加爾各答為時區的例項中排程傳送活動時發生的問題。 (NEO-20001)

* 傳送發生相關性設定問題時，現在會顯示錯誤。

* 修正 **關於** 功能表。

* 修正嘗試從工作流程中循環傳送的屬性更新路由帳戶時發生的問題。 (NEO-18684)

* 修正透過重新導向模組連線至執行個體時，一旦關閉連線就無法正確清理的問題。
