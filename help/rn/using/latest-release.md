---
title: 最新版本
description: 最新版本
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1206b2dcee8a4b0e95a005e47b947b00388e7e43

---


# 最新版本{#latest-release}

[建立升級](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) |控 [制面板版本](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) |文 [件更新](../../rn/using/documentation-updates.md) |舊 [版](../../rn/using/release--19-2.md) |已過 [時的功能](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>一般可用性</strong></td>
   <td><img src="assets/blue3.png"/><strong>發行候選人</strong></td> 
   <td><img src="assets/orange3.png"/><strong>不再提供</strong></td> 
   <td><img src="assets/red3.png"/><strong>已過時</strong></td> 
  </tr> 
   <tr> 
   <td>提供最新的穩定版本。 <br>在生產環境中經過驗證。 </td>
   <td>經Adobe驗證的建置。 <br>等待生產校對。 </td>
   <td>更新的版本已修正錯誤。 <br>需要更新。 </td>
   <td>包含已知的回歸。 <br>更新是必備的。 </td>
  </tr> 
 </tbody> 
</table>

單 [擊此處](../../rn/using/release--19-1.md#release-19-1-4-build-9032) ，查看上 **一個穩定構建** (GA)。

## ![](assets/blue-2.png) 版本20.1 —— 組建版本9122 {#release-20-1-build-XXXX}

_2020年2月17日_

**新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>雪花FDA連接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake是完全托管的雲資料倉庫，可在儲存和計算級別進行擴展。 有了這個新的連接器，Adobe Campaign現在可以運用Snowflake的強大功能來執行大資料分段。 此連接器適用於所有客戶，包括Adobe代管。</p>
    <p>如需詳細資訊，請參閱詳細 <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">的檔案</a><a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html.">和教學影片</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop FDA連接器增強功能</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Hadoop FDA Connector已經過改良，可支援Hadoop 3.0和Cloudera。</p>
    <p>如需詳細資訊，請參閱詳 <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">細檔案</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 已改善報表設定的安全性，以防止點按劫持。 這會套用至新報表。 對於舊報表，您需要重新發佈以套用變更。 (NEO-13282)

* 修正cryptString中的小記憶體問題。 (NEO-20071)

* 已改良螢幕JSP以修正內部IP洩漏。 (NEO-16821)

* 修正堆疊追蹤資訊可顯示給非管理員使用者的問題。 (NEO-12388)

* 已改善對先前作業中快取資料的管理。 (NEO-17039)

* 修正登入。log檔案無法透過IMS記錄成功登入嘗試的問題。 (NEO-11004)

**改進**

* iOS 13現在支援HTTP2連接器。

* 改進了推播通知功能（nms:address和nms:appSubscriptionRcp）所使用的表的隔離管理和清除。 對於iOS（僅限HTTP2連接器），停用的Token現在的處理方式與Android相同。 現在，在NmsAppSubscriptionRcp表中設定了禁用標誌。 [閱讀更多資訊](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 在 **JavaScript程式碼和進階JavaScript程式碼工作流程活動中新增了一個選項****** ，以定義逾時期間。 這可防止javascript執行階段執行太長。 如果逾時期間過去，工作流程便會停止。 預設逾時為1小時。 [閱讀更多資訊](../../workflow/using/sql-code-and-javascript-code.md)

* 現在，當在中間採購伺服器上找不到相符的相似性時，傳送分析會停止，並顯示對應的錯誤訊息。

* 現在支援Postgres的資料庫容錯移轉：當資料庫伺服器當機並重新啟動時，Campaign現在會自動重新連線至它。

* 「開 **始擱置中** 」檢視已新增至「管理>稽核>工作流程狀態」節點。 這可讓您監控執行個體上等待營運管理程式啟動的所有 **工作流程** 。 此檢視隨附於行銷促銷活動套件。 [閱讀更多資訊](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**其他變更**

* 在Linux上，nlserver服務啟動現在使用系統單元，而不是/etc/init.d/nlserver6指令碼。 在安裝20.1軟體包時，會自動執行到新啟動方案的遷移。 /etc/init.d/nlserver6仍然提供，但是用於與nlserver服務（啟動、重新啟動、停止等）交互，建議您直接使用systemctl命令。

* 最耗用的自訂表格已從 **xtkNewId序列移至專用序列** 。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* 已改善查詢效能，這些效能可能會受到不必要的資料庫連線所影響。

* 已改善資料庫更新精靈的效能。

* 資料庫記錄管理得到了增強。

* 連接池的健壯性已經得到改善，這可能防止意外連接故障的發生太多。

* 增強了在發生軟性錯誤時傳送要隔離的電子郵件地址驗證規則。 [閱讀更多資訊](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 對於Debian,Campaign現在會在系統PCRE程式庫可用時使用。

* Campaign現在允許使用更新的系統ODBC庫。

* 在開啟連接以載入富映像時，已向LINE servlet添加超時。 如果影像載入時間太長，Servlet會停止連線，以避免瓶頸。

**修補程式**

* 修正使用Hadoop連接器時的帳戶金鑰加密問題。

* 修正因實施SSL認證而導致使用者連線在Windows伺服器上失敗的回歸問題。 (NEO-20629)

* 修正當工作流程ID為負數時，遞增查詢活動的問題。 (NEO-19779)

* 修正透過Netezza FDA連接器執行查詢時的編碼問題。 (NEO-19594)

* 修正在「Web下載」工作流程事件活動中使用POST方法時 **導致錯誤** 的問題。

* 已修正產生選件提案的問題。 (NEO-18176)

* 修正使用贏取網頁表單範本時的頁尾顯示問題。

* 修正在連續傳送內容中剖析URL時，可能導致其當機的問題。 (NEO-16910)

* 修正建立新促銷 **活動時** ，無 **** 法計算「開始」和「結束」欄位的問題。

* 修正使用URL時「檔 **案下載** 」工作流程活動的問題。

* 修正預覽報表查詢活動中匯入的清單時的問題。 (NEO-13119)

* 修正在電子郵件編輯器中選取「由促銷活動提供」個人化區塊時， **** 顯示過時影像的問題。

* 客戶端與伺服器之間的網路通信得到了改善。

* 修正在相同促銷活動中建立過多工作流程的問題。 現在，您無法建立超過28個工作流程。 將顯示警告。

* 修正在Union工作流程活 **動中使用** A selection of columns conniliation選項時 **** 的問題。

* 修正在工作流程中使用損毀的擴充清單時可能發生的主控台損毀問題。 (NEO-18096)

* 修正工作流程中可能發生的各種主控台損毀問題(NEO-18010、NEO-18032)

* 修正即使停用「外部訊號」工作流程 **活動** ，仍能執行該活動的問題。 (NEO-17524)

* 修正建立新架構時的問題。

* 修正傳送SMS訊息時的追蹤問題。 (NEO-19595)

* 修正傳送指標中顯示錯誤目標對象數的問題。

* 修正透過工作流程活動產生描述性報表時，顯示錯誤百分比的問題。 (NEO-14314)

* 修正當時間檢視參數時，傳送總處理量報表顯示不同數字的問題。 (NEO-11783)

* 修正「追蹤」工作流程無法更新交易訊息追蹤指標的問題。 (NEO-17770)

* 修正當透過SOAP要求選件時，造成Web程式當機並重新啟動的回歸問題。 (NEO-19482)

* 修正如果上傳目錄是遠端共用位置，則無法將資料上傳至公用資源的問題。 (NEO-19361)

* 修正從Adobe Experience cloud技術 **** 工作流程匯入觀眾時常失敗的問題。 (NEO-18463)

* 修正使用從Experience manager匯入的範本時，無法傳送傳送的問題。 (NEO-17540)

* 已修正在升級至建置9032並防止例項透過SSL通訊協定連線至FTP伺服器後發生的問題。 (NEO-20498)

* 修正使用FDA架構作為定位維度，在工作流程中刪除、插入或更新 **Update data** activity大量資料時發生的問題。 (NEO-13280)

* 修正在標籤外使用&#39;if&#39;陳述式時，無法傳送電子郵件的 `body` 問題。

* 修正嘗試從已傳送訊息的傳送記錄顯示鏡像頁面時所發生的問題。 (NEO-17976)

* 修正在傳送中按一下「匯 **入HTML** 」後，「將頁面鏡像為 ******** 」個人化區塊無法顯示在「文字內容」標籤中的問題。 (NEO-17568)

* 按一下到已澄清過期鏡像頁的連結時顯示的錯誤消息。 (NEO-17340)

* 修正「資料散發」建立畫面無法使用某些 **按鈕的問** 題。

* 修正以亞洲／加爾各答為時區的例項排程傳送活動時所發生的問題。 (NEO-20001)

* 傳送發生相似性設定問題時，現在會顯示錯誤。

* 修正「關於」功能表中顯示錯誤版本標 **簽** 。

* 修正嘗試從工作流程中循環傳送的屬性更新傳送帳戶時發生的問題。 (NEO-18684)

* 修正透過重新導向模組連線至執行個體時，導致連線在關閉後無法正確清理的問題。
