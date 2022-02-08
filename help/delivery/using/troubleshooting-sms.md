---
product: campaign
title: 簡訊疑難排解
description: 瞭解有關如何排除SMS通道故障的更多資訊
feature: SMS
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---

# SMS疑難解答 {#troubleshooting-sms}

![](../../assets/common.svg)

## 不同外部帳戶之間的衝突 {#external-account-conflict}

如果實例具有多個SMS外部帳戶，則必須檢查問題是否不是由外部帳戶之間的衝突引起的。

Adobe Campaign將外部帳戶視為不相關實體。

如果您有多個帳戶，請按照以下步驟隔離導致問題的外部帳戶：

1. 禁用所有外部帳戶。
1. 啟用一個外部帳戶。
1. 嘗試重現問題。
1. 如果初始問題並不總是出現，在結束之前先嘗試一下。
1. 如果該單個帳戶未出現問題，請禁用該問題，然後重新啟動到下一個帳戶的步驟2。

單獨檢查每個帳戶後，可能會出現兩種情況：

* **問題出現在一個或多個帳戶上**

   在這種情況下，您可以對每個帳戶分別應用其他故障排除過程。 最好在診斷帳戶時禁用其他帳戶，以減少網路流量和日誌數。

* **當任何時候只有一個帳戶處於活動狀態時，未出現問題**

   帳戶之間有衝突。 如前所述，Adobe Campaign單獨對待客戶，但提供商可將其視為單個客戶。

   * 您在所有帳戶之間使用不同的登錄/密碼組合。
您必須聯繫提供商，以診斷其一側的潛在衝突。

   * 某些外部帳戶共用相同的登錄/密碼組合。
提供程式無法確定從哪個外部帳戶 `BIND PDU` 是來自的，因此他們將多個帳戶的所有連接視為一個連接。 他們可能在兩個帳戶上隨機傳送MO和SR，導致問題。
如果提供程式支援同一登錄/密碼組合的多個短代碼，則您必須詢問它們將該短代碼放在 `BIND PDU`。 請注意，此資訊必須放在 `BIND PDU`，不在 `SUBMIT_SM`，也請參見Wiki頁。 `BIND PDU` 是唯一允許正確路由MO的位置。
查看 [每種PDU中的資訊](sms-protocol.md#information-pdu) 上部分，以瞭解 `BIND PDU`，通常在 `address_range`，但需要提供商的特殊支援。 聯繫他們瞭解他們希望如何獨立路由多個短代碼。
Adobe Campaign支援在同一外部帳戶上處理多個短代碼。

## 一般與外部帳戶有關 {#external-account-issues}

* 調查連接器最近是否被更改以及由誰更改（選中「外部帳戶」作為組）。

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* 調查（在/postupgrade目錄中）系統是否已升級以及何時升級
* 調查是否最近升級了影響SMS的任何包(/var/log/dpkg.log)。

## 中間採購（托管）問題{#issue-mid-sourcing}

* 如果問題在中間採購環境中發生，請確保在中間採購伺服器上正確建立和更新交貨和廣泛日誌。 如果不是這樣，這不是簡訊問題。

* 如果中端伺服器上的一切正常，並且SMS已正確發送，但營銷實例未正確更新，則可能會出現中端同步問題。

## 連接到提供程式時出現問題 {#issue-provider}

* 如果 `BIND PDU` 返回非零 `command_status` 代碼，請向提供程式瞭解詳細資訊。

* 檢查網路是否已正確配置，以便可以與提供程式建立TCP連接。

* 要求提供商檢查他們是否將IP正確添加到Adobe Campaign實例的允許清單中。

* 檢查 **外部帳戶** 的子菜單。 詢問提供程式欄位的值。

* 如果連接成功但不穩定，請檢查 [連接不穩定的問題](troubleshooting-sms.md#issues-unstable-connection) 的子菜單。

* 如果連接問題難以診斷，則網路捕獲可以提供資訊。 確保在出現問題時網路捕獲能夠同時運行，從而高效地分析問題。 您還應注意問題出現的確切時間。

## 連接不穩定的問題 {#issues-unstable-connection}

如果發生以下任何情況，則連接被視為不穩定：

* 連接持續時間不到1小時。 Adobe Campaign Classic的發射機連接由於Adobe Campaign ClassicMTA的工作方式而是例外。

* 提供程式發送 `UNBIND PDU`s

* `enquire_link` 不管是在Adobe Campaign方面，還是在供應商方面。 你可能會看到 `ENQUIRE_LINK_RESP` 有非零錯誤代碼。

* 有很多 `BIND PDU`s一天中的連接數不應超過幾個，具體取決於連接數。 每小時應有1個以上BIND PDU發出警報。

如何修復連接穩定性問題：

* 不穩定的連接很少是根本原因，它通常是另一個問題導致斷開連接的結果。 優先順序是查找根本原因。

* 啟用詳細SMPP跟蹤。 您需要他們查看連接重新啟動時發生的情況。

* 如果提供程式發送 `BIND PDU`s，可能有問題。 詢問您的提供商為什麼 `UNBING` 的子菜單。

* 獲取網路捕獲有時是查看連接如何關閉的唯一方法。

* 如果提供程式通過發送 `TCP FIN` 或 `TCP RST packet`，請咨詢您的提供商詳細資訊。

* 如果提供程式在發送清除錯誤後關閉連接，例如 `DELIVER_SM_RESP` 如果出現錯誤代碼，則他們必須修復其連接器，否則將阻止其他類型的消息傳輸，並觸發MTA限制。 在關閉連接影響MT和SR的收發器模式中，這一點尤其重要。

## 發送MT時出現問題（向最終用戶發送常規SMS）{#issue-MT}

* 檢查連接是否穩定。 除Adobe Campaign Classic的發射器外，SMPP連接應保持至少1小時不間斷。 請參閱一節 [連接不穩定的問題](sms-protocol.md#issues-unstable-connection)。

* 如果重新啟動MTA使發送MT在一小段時間內再次工作，則可能由於連接不穩定而有限制。 請參閱一節 [連接不穩定的問題](troubleshooting-sms.md#issues-unstable-connection)。

* 檢查廣日誌是否存在，且狀態正確且日期正確。 如果不是，這可能是遞送或遞送準備問題。

* 檢查MTA是否實際處理該消息。 如果不是這樣，這可能不是簡訊問題。

* 檢查SMS連接器是否與提供商的設備實際綁定。 請向提供方咨詢反饋，以確保所有系統都正常通信。 請參閱 `BIND_TRANSMITTER` 和 `BIND_TRANSCEIVER PDU`的子目錄。 您可能需要啟用SMPP跟蹤以進行正確的故障排除。

* 啟用SMPP跟蹤後，檢查 `SUBMIT_SM PDU` 包含正確的資訊。

* 檢查提供程式是否用 `SUBMIT_SM_RESP PDU` 值（代碼0）。 確保PDU到達時有合理的延遲：超過1秒的內容必須與提供商討論，通常在100毫秒內到達。

* 如果所有這些步驟都有效，您可以確信問題出在提供方。 他們必須在自己的平台上進行故障排除。

* 如果它有效但吞吐量不一致，請嘗試調整發送窗口並降低MT吞吐量。 您需要與提供商合作來調整它。 Adobe Campaign可以非常快地發送消息，因此供應商的設備可能出現效能問題。

## 複製MT（同一條SMS在一行中多次發送）{#duplicated-MT}

重複通常由重試引起。 重試消息時有重複項是很正常的，您應嘗試刪除重試的根本原因。

* 如果您看到重複項在60秒之外發送，則可能是提供方方面的問題，他們不會發送 `SUBMIT_SM_RESP` 足夠快。

* 如果你看到很多 `BIND/UNBIND`，連接不穩定。 查看[連接不穩定的問題](troubleshooting-sms.md#issues-unstable-connection) 部分，用於解決重複消息問題。

重試時減少重複項的數量：

* 降低發送窗口。 發送窗口應足夠大，以便 `SUBMIT_SM_RESP` 延遲。 其值表示窗口已滿時發生錯誤時可複製的消息的最大數量。

## 處理SR（交貨收據）時發出 {#issue-process-SR}

* 您需要啟用SMPP跟蹤才能執行任何類型的SR故障排除。

* 檢查 `DELIVER_SM PDU` 是來自供應商的，而且形態良好。

* 檢查Adobe Campaign是否成功回復 `DELIVER_SM_RESP PDU` 及時。 在Adobe Campaign Classic，這保證SR被插入 `providerMsgId` SMS進程延遲處理的表。

如果 `DELIVER_SM PDU` 未成功確認，則應檢查以下內容：

* 檢查與中的ID提取和錯誤處理相關的規則運算式 **外部帳戶**。 您可能需要根據 `DELIVER_SM PDU`。

* 檢查是否正確設定了 `broadLogMsg` 的子菜單。

如果 `DELIVER_SM PDU` 已被Adobe Campaign Classic擴展SMPP連接器確認，但broadLog未正確更新，請檢查一節中描述的ID協調過程 [匹配MT、SR和broadlog條目](sms-protocol.md#matching-mt)。

如果修復了所有內容，但某些無效SR仍在提供程式的緩衝區中，則可以使用「無效ID確認計數」選項跳過這些緩衝區。 應小心使用，並在緩衝區清除後盡快重置為0。

## 處理MO（和黑名單/自動答復）時出現問題{#issue-process-MO}

* 在test期間啟用SMPP跟蹤。 如果未啟用TLS，則在排除MO故障時應執行網路捕獲，以檢查PDU是否包含正確的資訊並且格式正確。

* 在捕獲網路通信量或分析SMPP跟蹤時，如果配置了回復，請確保捕獲與MO及其回復MT的整個對話。

* 如果MO(`DELIVER_SM PDU`)未出現在跟蹤中，問題出在提供程式端。 他們必須在自己的平台上進行故障排除。

* 如果 `DELIVER_SM PDU` 看來，檢查它是否被Adobe Campaign確認 `DELIVER_SM_RESP PDU` （代碼0）。 此RESP保證所有處理邏輯都已由Adobe Campaign應用（自動回復和允許/拒絕清單）。 如果不是，請在SMS進程日誌中搜索錯誤消息。

* 如果啟用了自動回復，請檢查 `SUBMIT_SM` 已發送到提供程式。 否則，保證在SMS進程日誌中找到錯誤消息。

* 如果 `SUBMIT_SM MT PDU` 包含回復的內容在跟蹤中找到，但SMS未到達手機，您必須與提供商聯繫，以獲得故障排除方面的幫助。

## 交付準備期間的問題不排除隔離的收件人（由自動回復功能隔離） {#issue-delivery-preparation}

* 檢查隔離表和交貨日誌中電話號碼格式是否完全相同。 如果不是，請參閱此 [節](sms-protocol.md#automatic-reply) 如果您對國際電話號碼格式的加號前置詞有問題。

* 檢查短碼。 如果收件人的短代碼與外部帳戶中定義的代碼相同或為空（空=任何短代碼），則可能會發生排除。 如果整個Adobe Campaign實例只使用一個短代碼，則更容易保留所有 **短碼** 欄位為空。

## 編碼問題 {#encoding-issues}

**步驟1:與提供商聯繫**

聯繫他們，看看他們有什麼問題。 他們應該能夠告訴你問題是在他們這邊還是在Adobe Campaign那邊。 如果問題出在Adobe Campaign，他們應該能夠告訴你哪個欄位不正確。

**步驟2:瞭解您的郵件中的內容**

Unicode允許許多類似字元的變體，而Adobe Campaign無法處理所有變體。

最常見的問題是從字處理器複製貼上，將通常的字元更改為排版正確的版本：空格改為非斷續空格，雙引號改為開引號和閉引號，減號改為各種連字元等。

測試時不要複製貼上您的郵件，請始終直接在介面中鍵入。

使用十六進位，可以區分相似字元之間的差異。 小寫L、大寫I、O、0、所有不同類型的引號、非拉丁編碼甚至不同類型的空格都可以看起來相同甚至根本不顯示。

要將unicode轉換為十六進位，可以使用聯機工具，如 [Unicode代碼轉換器](https://r12a.github.io/app-conversion/) 的子菜單。 鍵入文本，確保沒有PII，如電話號碼，然後按一下 **轉換**。 在底部（UTF-32區域）將看到十六進位值。

開啟有關編碼問題的票證時，無論是與提供程式還是 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，始終包含您鍵入的內容和您看到的內容的十六進位版本。

**第3步：知道你應該發送什麼**

確定要使用的編碼，並聯機搜索其字元表。 檢查目標代碼頁中是否確實有要發送的字元。 檢查 `data_coding` 欄位正確，並與您和提供程式期望的匹配。

**第4步：知道你到底派了什麼**

您需要連接器的調試輸出才能準確查看您發送給提供程式的位元組。 中出現編碼問題 `SUBMIT_SM PDU`所以一定要抓住他們。 發送在日誌中很容易找到的非常明顯的消息。

測試時發送不同種類的特殊字元。 例如，GSM7編碼具有擴展字元，這些字元的十六進位形式非常不同，因為它們不顯示在任何其他編碼中，所以易於識別。

## 通信SMS問題時要包括的元素 {#element-include}

無論您是在SMS問題上尋求幫助，還是在向Adobe Campaign開啟支援票證、向SMS提供商提供幫助，還是在此問題上進行任何通信，您都需要包括以下資訊，以確保它得到正確的鑑定。 合理的問題，是更快解決問題的關鍵。

* **啟用詳細SMPP消息** 的子菜單。 沒有這個，大多數簡訊問題是無法解決的。

* 如果問題與SMS通信有關，請首先與提供商聯繫。 其平台最適合即時高效地診斷簡訊流量問題。

* 包括對問題的簡短但實事求是的描述。

* 包括預期結果的說明。

* 包括來自提供程式的反饋。

* 包括相關日誌和/或網路捕獲。 執行捕獲時，確保在捕獲期間重現問題。

* 如果包括日誌、跟蹤或捕獲，則在出現問題時查明檔案中的確切位置。

* 如果引用消息、PDU或日誌，請清楚地聲明其時間戳，以便更容易查找。

* 嘗試在test環境中重現問題。 如果您不確定設定，請在test環境中嘗試，然後使用SMPP跟蹤檢查結果。 通常，報告在test環境中複製的問題比直接報告生產環境中的問題要好。

* 包括平台上所做的任何更改或微調。 此外，還包括提供方可能在其方面所做的任何更改。

### 網路捕獲 {#network-capture}

網路捕獲並不總是需要的，通常冗餘的SMPP消息已足夠。 以下是一些指導原則，可幫助您確定是否需要網路捕獲：

* 連接問題，但詳細消息不顯示任何 `BIND_RESP PDU`。

* 無錯誤消息的未解釋斷開連接，這是連接器在檢測到低級協定錯誤時的常見行為。

* 提供程式抱怨解除綁定/斷開連接進程。

* 在可選TLV欄位中編碼問題。

* 懷疑不同連接之間有混合通信。

在所有其他情況下，請嘗試首先分析詳細的SMPP消息，並僅在詳細日誌中缺少資訊時才請求網路捕獲。

在某些情況下，不需要捕獲網路通信量。 以下是最常見的情況：

* 啟用TLS:根據定義，TLS通信被加密，因此無法捕獲。

* 效能問題：日誌包含跟蹤效能問題所需的所有資訊。

* 計時問題(`retry timing`。 `enquire_link` 週期、吞吐量上限等)

* SR分析和處理：詳細日誌可提供更多上下文和更好的演示文稿。

* MO處理（自動答復、隔離）。

* 不涉及實際SMPP流量的錯誤：交付準備、消息中心API問題、工作流問題等

## 啟用SMPP跟蹤 {#enabling-smpp-traces}

新連接器支援通過跟蹤進行擴展日誌記錄：SMPP 跟蹤是在MTA日誌中輸出的，而不是在標準輸出中。

**啟用每個外部帳戶（首選方法）**

1. 在 **外部帳戶**&#x200B;選中 **在日誌檔案中啟用詳細SMPP跟蹤**。
1. 等待10分鐘，讓伺服器重新載入外部帳戶。

它現在應該是活動的。

**在配置中啟用**

在 `config-instance.xml` 檔案，設定以下參數：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 檢查容器上開啟的連接數 {#open-connections}

要檢查容器上開啟的連接數，可以使用以下命令：

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

這將列出為給定埠開啟的連接數。 我們使用埠3600。

結果應如下：

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

為sms進程開啟4個連接，每個mta子級有2個，有5個子級。
