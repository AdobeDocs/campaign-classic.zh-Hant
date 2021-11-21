---
product: campaign
title: 簡訊疑難排解
description: 進一步了解如何疑難排解SMS通道
audience: delivery
content-type: reference
topic-tags: configuring-channels
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---

# SMS疑難排解 {#troubleshooting-sms}

![](../../assets/common.svg)

## 不同外部帳戶之間的衝突 {#external-account-conflict}

如果執行個體有多個SMS外部帳戶，您必須檢查問題是否並非由外部帳戶之間的衝突所造成。

Adobe Campaign將外部帳戶視為不相關的實體。

如果您有多個帳戶，請依照此程式隔離造成問題的外部帳戶：

1. 禁用所有外部帳戶。
1. 啟用一個外部帳戶。
1. 嘗試重現問題。
1. 如果最初的問題不總是出現，在結束之前做出合理的嘗試。
1. 如果該單一帳戶未出現問題，請停用該問題，然後重新開始至下一個帳戶的步驟2。

在您個別檢查每個帳戶後，可能會有2種情況：

* **問題出現在一個或多個帳戶上**

   在此情況下，您可以對每個帳戶個別套用其他疑難排解程式。 最好在診斷帳戶時停用其他帳戶，以減少網路流量和記錄數。

* **任何時候只有一個帳戶處於活動狀態時，問題沒有出現**

   帳戶之間有衝突。 如前所述，Adobe Campaign會個別處理帳戶，但提供者可能會將其視為單一帳戶。

   * 所有帳戶之間使用不同的登入/密碼組合。
您必須聯繫提供者以診斷其方面的潛在衝突。

   * 某些外部帳戶共用相同的登入/密碼組合。
提供者無法分辨來自哪個外部帳戶 `BIND PDU` 來自，因此會將多個帳戶的所有連線視為單一連線。 他們可能隨機地在兩個帳戶上路由MO和SR，導致問題。
如果提供者針對相同的登入/密碼組合支援多個簡短代碼，您必須要求他們將該簡短代碼放在 `BIND PDU`. 請注意，此資訊必須放入 `BIND PDU`，而不在 `SUBMIT_SM`，自 `BIND PDU` 是唯一允許正確傳送MO的位置。
請參閱 [每種PDU中的資訊](sms-protocol.md#information-pdu) 一節，以了解 `BIND PDU`，通常您會在 `address_range`，但這需要提供者的特殊支援。 請聯繫他們，了解他們希望如何單獨路由多個短代碼。
Adobe Campaign支援在相同外部帳戶上處理多個短代碼。

## 一般外部帳戶的問題 {#external-account-issues}

* 調查連接器最近是否已更改以及由誰更改（按組檢查外部帳戶）。

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* 調查（在/postupgrade目錄中）系統是否升級以及何時升級
* 調查最近是否可能升級了任何影響SMS的套件(/var/log/dpkg.log)。

## 中間來源（托管）問題{#issue-mid-sourcing}

* 如果問題發生在中間來源環境，請確定已在中間來源伺服器上正確建立及更新傳送和廣泛記錄檔。 如果不是這樣，則不是SMS問題。

* 如果mid伺服器上的所有項目都運作正常，且SMS已正確傳送，但行銷執行個體未正確更新，則您可能會遇到中間同步問題。

## 連接到提供程式時出現問題 {#issue-provider}

* 若 `BIND PDU` 傳回非零 `command_status` 代碼，請向提供者索取詳細資訊。

* 檢查網路是否已正確配置，以便能夠對提供程式進行TCP連接。

* 要求提供者檢查他們是否已將IP正確新增至Adobe Campaign例項的允許清單。

* 檢查 **外部帳戶** 設定。 向提供者詢問欄位的值。

* 如果連接成功但不穩定，請檢查 [連接不穩定的問題](troubleshooting-sms.md#issues-unstable-connection) 區段。

* 如果難以診斷連接問題，則網路捕獲可以提供資訊。 確保在出現問題時網路捕獲同時運行，並且可以高效地分析問題。 您也應注意問題出現的確切時間。

## 連接不穩定的問題 {#issues-unstable-connection}

如果發生下列任一情況，則會將連線視為不穩定：

* 連線持續時間不到1小時。 Adobe Campaign Classic傳輸器連線是Adobe Campaign Classic MTA運作方式的例外。

* 提供程式發送 `UNBIND PDU`s.

* `enquire_link` 逾時(在Adobe Campaign端或提供者端)。 你可能會看到 `ENQUIRE_LINK_RESP` 在這種情況下會有非零的錯誤代碼。

* 有很多 `BIND PDU`s.視連線數量而定，一天內不應多於幾個。 每小時應有1個以上的BIND PDU發出警報。

如何修復連接穩定性問題：

* 不穩定的連接很少是根本原因，這往往是另一個問題導致中斷連接的結果。 優先順序是找出根本原因。

* 啟用詳細SMPP跟蹤。 您需要他們查看連線重新啟動時的狀況。

* 如果提供程式發送 `BIND PDU`s，可能有問題。 詢問您的提供者為何 `UNBING` 已傳送。

* 進行網路捕獲有時是查看連接關閉情況的唯一方法。

* 如果提供程式通過發送 `TCP FIN` 或 `TCP RST packet`，請向提供者詢問詳細資訊。

* 如果提供者在傳送清除錯誤(例如 `DELIVER_SM_RESP` 使用錯誤碼時，他們必須修復其連接器，否則將阻止其他類型的消息傳輸，並觸發MTA節流。 這在收發信機模式中尤其重要，關閉連接會影響MT和SR。

## 傳送MT時發生問題（傳送給一般使用者的一般SMS）{#issue-MT}

* 檢查連接是否穩定。 除Adobe Campaign Classic上的發射器外，SMPP連接應持續保持至少1小時。 請參閱 [連接不穩定的問題](sms-protocol.md#issues-unstable-connection).

* 如果重新啟動MTA讓傳送MT在一小段時間內再次運作，您可能會因為連線不穩定而受到限制。 請參閱 [連接不穩定的問題](troubleshooting-sms.md#issues-unstable-connection).

* 檢查廣泛記錄是否存在，且狀態正確且日期正確。 若非如此，可能是傳送或傳送準備問題。

* 檢查MTA是否實際處理訊息。 如果不是，這可能不是SMS問題。

* 檢查SMS連接器是否實際與提供者的設備綁定。 請向提供者提供反饋，以確保所有系統都正常通信。 請參閱 `BIND_TRANSMITTER` 和 `BIND_TRANSCEIVER PDU`s ，以了解綁定過程的資訊。 您可能需要啟用SMPP跟蹤才能正確進行故障排除。

* 啟用SMPP追蹤後，請檢查 `SUBMIT_SM PDU` 包含正確的資訊。

* 檢查提供者是否使用 `SUBMIT_SM_RESP PDU` 值（代碼0）。 確保PDU到達時有合理的延遲：超過1秒的內容必須與提供者討論，通常不到100毫秒。

* 如果所有這些步驟都起作用，您可以確信問題出在提供方。 他們必須在其平台上執行疑難排解作業。

* 如果它有效但吞吐量不一致，請嘗試調整發送窗口並降低MT吞吐量。 您需要與提供者合作，才能調整。 Adobe Campaign可以很快傳送訊息，因此提供者的裝置上可能會出現效能問題。

## MT會重複（一列會傳送多次相同的SMS）{#duplicated-MT}

重複項目通常是由重試造成。 重試訊息時有重複項目是正常情況，您應嘗試移除重試的根本原因。

* 如果您發現重複項目相隔60秒，可能是提供者端的問題，他們不會傳送 `SUBMIT_SM_RESP` 快點。

* 如果您看到許多 `BIND/UNBIND`，則連接不穩定。 請參閱[連接不穩定的問題](troubleshooting-sms.md#issues-unstable-connection) 區段，以解決重複訊息問題。

正在減少重試次數：

* 降低傳送視窗。 發送窗口應足夠大，可以覆蓋 `SUBMIT_SM_RESP` 延遲。 其值代表當視窗已滿時發生錯誤時，可複製的訊息數上限。

## 處理SR時發出（交貨收據） {#issue-process-SR}

* 您需要啟用SMPP跟蹤才能執行任何類型的SR故障排除。

* 檢查 `DELIVER_SM PDU` 來自提供者，且格式良好。

* 檢查Adobe Campaign回覆是否成功 `DELIVER_SM_RESP PDU` 及時。 在Adobe Campaign Classic上，這保證SR已插入 `providerMsgId` 表格，供SMS程式延期處理。

若 `DELIVER_SM PDU` 未成功確認，則您應檢查下列項目：

* 檢查與ID擷取和中的錯誤處理相關的規則運算式 **外部帳戶**. 您可能需要根據 `DELIVER_SM PDU`.

* 檢查錯誤是否已正確布建於 `broadLogMsg` 表格。

若 `DELIVER_SM PDU` 已由Adobe Campaign Classic延伸SMPP連接器確認，但broadLog未正確更新，請檢查區段中所述的ID調解程式 [匹配MT、SR和broadlog條目](sms-protocol.md#matching-mt).

如果您修正了所有問題，但某些無效SR仍在提供程式的緩衝區中，則可以使用「無效ID確認計數」選項來跳過它們。 這應謹慎使用，並在緩衝區清除後盡快重設為0。

## 處理MO時發生的問題（和黑名單/自動回覆）{#issue-process-MO}

* 在測試期間啟用SMPP跟蹤。 如果不啟用TLS，則在診斷MO時應執行網路捕獲，以檢查PDU是否包含正確的資訊且格式正確。

* 捕獲網路流量或分析SMPP跟蹤時，如果配置了回復，請確保捕獲與MO及其回復MT的整個對話。

* 若MO(`DELIVER_SM PDU`)未出現在追蹤中，問題出在提供者端。 他們必須在其平台上執行疑難排解作業。

* 若 `DELIVER_SM PDU` 顯示，檢查是否已獲得Adobe Campaign的認可，並成功 `DELIVER_SM_RESP PDU` （代碼0）。 此RESP可保證所有處理邏輯皆已由Adobe Campaign套用（自動回覆和允許/封鎖清單）。 若非如此，請在SMS處理記錄檔中搜尋錯誤訊息。

* 如果已啟用自動回覆，請檢查 `SUBMIT_SM` 已傳送給提供者。 若未包含，則保證會在SMS處理記錄中找到錯誤訊息。

* 若 `SUBMIT_SM MT PDU` 包含回覆的訊息會顯示在追蹤中，但簡訊未送達行動電話，您必須聯絡提供者，以取得疑難排解的協助。

## 傳送準備期間發生的問題，不會排除隔離的收件者（由自動回覆功能隔離） {#issue-delivery-preparation}

* 檢查隔離表和傳送日誌中的電話號碼格式是否完全相同。 否則，請參閱此 [節](sms-protocol.md#automatic-reply) 如果您對國際電話號碼格式的加號前置詞有問題。

* 檢查短代碼。 如果收件者的簡短代碼與外部帳戶中定義的相同，或空白(empty = any shortcode)，則會排除。 如果整個Adobe Campaign例項只使用一個簡短程式碼，就可輕鬆保留所有 **短碼** 欄位空白。

## 編碼問題 {#encoding-issues}

**步驟1:與提供者取得聯絡**

聯繫他們，看看他們有什麼問題。 他們應該能夠告訴你問題是在他們這邊還是在Adobe Campaign那邊。 如果問題出在Adobe Campaign中，他們應該能夠告訴您確切的欄位不正確。

**步驟2:了解您的訊息中的內容**

Unicode允許許多相似字元的變體，而Adobe Campaign無法處理所有變體。

最常見的問題是文字處理程式的複製貼上，它會將通常的字元變更為排版正確的版本：空格變為不斷行空格，雙引號變為開/閉引號，減號變為各種連字型大小等。

測試時請勿複製並貼上訊息，請一律直接在介面中輸入訊息。

使用十六進位，您可以區分類似字元之間的差異。 小寫L、大寫I、O、0、所有不同類型的引號、非拉丁編碼或甚至不同類型的空格都看起來相同或完全不顯示。

要將unicode轉換為十六進位，可以使用聯機工具，如 [Unicode代碼轉換器](https://r12a.github.io/app-conversion/) 網站。 輸入文字，確定沒有PII（例如電話號碼），然後按一下 **轉換**. 您會在底部看到十六進位值（UTF-32區域）。

開啟有關編碼問題的票證時，無論是與提供者或 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，一律包含十六進位版本，包含您所輸入的內容和所看到的內容。

**步驟3:了解您應傳送的內容**

確定您希望使用的編碼，並聯機搜索其字元表。 檢查您要傳送的字元是否實際可在目標程式碼頁面中使用。 檢查 `data_coding` 欄位正確，且符合您和提供者的期望。

**步驟4:了解您實際發送的**

您需要連接器的除錯輸出，才能查看您傳送給提供者的確切位元組。 中出現編碼問題 `SUBMIT_SM PDU`s，所以一定要抓住他們。 傳送在記錄檔中很容易找到的非常不同訊息。

測試時傳送不同種類的特殊字元。 例如，GSM7編碼具有十六進位形式非常不同的擴展字元，這些字元很容易被發現，因為它們不出現在任何其他編碼中。

## 傳送SMS問題時要包含的元素 {#element-include}

每當您在SMS問題上尋求協助時(無論是開啟支援票證給Adobe Campaign、給SMS提供者，或是針對此問題進行任何類型的通訊)，您都必須包含下列資訊，以確保其符合資格。 合格的問題是更快解決問題的關鍵。

* **啟用詳細SMPP消息** 當問題出現時。 沒有這個，大多數簡訊問題都是無法解決的。

* 如果問題與SMS流量有關，請先與提供者連絡。 其平台最適合即時有效診斷簡訊流量問題。

* 包括對問題的簡短但事實的描述。

* 包括預期結果的說明。

* 納入提供者的意見。

* 包括相關日誌和/或網路捕獲。 執行捕獲時，請確保在捕獲期間重現問題。

* 如果您包含日誌、跟蹤或捕獲，則在出現問題時找出檔案中的確切位置。

* 如果您參考消息、PDU或日誌，請清楚說明其時間戳記，以便更容易找到。

* 嘗試在測試環境中重現問題。 如果您不確定某個設定，請在測試環境中試用該設定，並使用SMPP追蹤檢查結果。 通常，報告在測試環境中複製的問題比直接報告生產環境的問題要好。

* 納入平台上所做的任何變更或調整。 此外，還包括提供者可能已在其一側所做的任何變更。

### 網路捕獲 {#network-capture}

不一定需要網路捕獲，通常冗餘的SMPP消息就足夠了。 以下是一些可幫助您確定是否需要網路捕獲的准則：

* 連線問題，但詳細訊息未顯示任何 `BIND_RESP PDU`.

* 無法解釋的斷開連接，沒有錯誤消息，這是連接器檢測到低級協定錯誤時的常見行為。

* 提供程式抱怨解除綁定/斷開進程。

* 選用TLV欄位中的編碼問題。

* 流量可疑混合在不同連線之間。

在所有其他情況下，請嘗試先分析詳細SMPP消息，並僅在詳細日誌中缺少資訊時才請求網路捕獲。

在某些情況下，不需要擷取網路流量。 以下是最常見的情況：

* 啟用TLS:根據定義，TLS流量會經過加密，因此無法擷取。

* 效能問題：記錄檔包含追蹤效能問題所需的所有資訊。

* 計時問題(`retry timing`, `enquire_link` 期間、輸送量上限等)

* SR解析和處理：詳細記錄可提供更多內容，並提供更佳的呈現方式。

* MO處理（自動回覆、隔離）。

* 與實際SMPP流量無關的錯誤：傳遞準備、訊息中心API問題、工作流程問題等。

## 啟用SMPP跟蹤 {#enabling-smpp-traces}

新連接器支援透過追蹤進行延伸記錄：SMPP。 跟蹤是在MTA日誌中輸出，而不是在標準輸出中。

**根據外部帳戶啟用（首選方法）**

1. 在 **外部帳戶**，檢查 **在日誌檔案中啟用詳細SMPP跟蹤**.
1. 等待10分鐘，讓伺服器重新載入外部帳戶。

現在應該是活動狀態。

**在配置中啟用**

在 `config-instance.xml` ，請設定下列參數：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 檢查容器上開啟的連線數 {#open-connections}

若要檢查容器上開啟的連線數，可使用以下命令：

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

這將列出為給定埠開啟的連接數。 這是3600埠。

結果應為：

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4個開啟sms程式的連線，每個mta子項2個，有5個子項。
