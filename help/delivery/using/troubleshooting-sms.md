---
product: campaign
title: 簡訊疑難排解
description: 進一步瞭解如何疑難排解SMS頻道
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: SMS
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---

# 簡訊疑難排解 {#troubleshooting-sms}



## 不同外部帳戶之間發生衝突 {#external-account-conflict}

如果執行個體有多個SMS外部帳戶，您必須檢查問題是否不是由外部帳戶之間的衝突所造成。

Adobe Campaign會將外部帳戶視為不相關的實體。

如果您有多個帳戶，請依照此程式來隔離造成問題的外部帳戶：

1. 停用所有外部帳戶。
1. 啟用一個外部帳戶。
1. 嘗試重現問題。
1. 如果初始問題並非總是出現，請在結論之前進行合理的嘗試次數。
1. 如果該單一帳戶未出現問題，請停用該帳戶，然後重新啟動至下一個帳戶的步驟2。

當您個別檢查每個帳戶後，可能會出現以下兩種情況：

* **問題出現在一個或多個帳戶上**

   在這種情況下，您可以對每個帳戶個別套用其他疑難排解程式。 在診斷帳戶時最好停用其他帳戶，以減少網路流量和記錄數量。

* **在任何時候只有一個帳戶作用中時，問題並未出現**

   帳戶之間發生衝突。 如前所述，Adobe Campaign會個別處理帳戶，但提供者可能會將其視為單一帳戶。

   * 您在所有帳戶之間使用不同的登入/密碼組合。
您必須連絡提供者，才能診斷其身邊的潛在衝突。

   * 某些外部帳戶共用相同的登入/密碼組合。
提供者無法辨別該使用哪個外部帳戶 `BIND PDU` 來自，因此他們將來自多個帳戶的所有連線視為單一。 他們可能在這兩個帳戶上隨機路由MO和SR，從而導致問題。
如果提供者支援相同登入/密碼組合的多個短程式碼，您必須詢問他們將短程式碼放在 `BIND PDU`. 請注意，此資訊必須放在 `BIND PDU`，且不在 `SUBMIT_SM`，由於 `BIND PDU` 是唯一允許正確路由MO的位置。
請參閱 [各種PDU中的資訊](sms-protocol.md#information-pdu) 區段中哪個欄位可用 `BIND PDU`，通常您會將短程式碼新增至 `address_range`，但這需要提供者的特殊支援。 請聯絡他們，以瞭解他們如何獨立路由多個短程式碼。
Adobe Campaign支援在相同的外部帳戶上處理多個短程式碼。

## 一般外部帳戶問題 {#external-account-issues}

* 調查最近是否變更過聯結器及變更者（檢查外部帳戶作為群組）。

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* 調查（在/postupgrade目錄中）系統是否已升級及何時升級
* 調查影響簡訊的任何套件最近是否可能升級(/var/log/dpkg.log)。

## 中間來源（託管）的問題{#issue-mid-sourcing}

* 如果問題發生在中間來源環境中，請確保在中間來源伺服器上正確建立和更新傳送和廣泛記錄。 如果不是這種情況，則不是SMS問題。

* 如果一切在中間伺服器上運作正常，且簡訊已正確傳送，但行銷執行個體未正確更新，則您可能會發生中間同步問題。

## 連線至提供者時的問題 {#issue-provider}

* 如果 `BIND PDU` 傳回非零 `command_status` 程式碼，請向提供者詢問更多資訊。

* 檢查網路是否已正確設定，以便與提供者建立TCP連線。

* 要求提供者確認其是否已正確將IP新增至Adobe Campaign執行個體的允許清單。

* Check **外部帳戶** 設定。 詢問提供者欄位的值。

* 如果連線成功但不穩定，請檢查 [不穩定的連線問題](troubleshooting-sms.md#issues-unstable-connection) 區段。

* 如果連線問題難以診斷，網路擷取可提供資訊。 請確定網路擷取在問題出現時同時執行，以便有效地進行分析。 您也應該記下問題出現的確切時間。

## 連線不穩定的問題 {#issues-unstable-connection}

如果發生下列任一情況，就會將連線視為不穩定：

* 連線持續少於1小時。 由於Adobe Campaign Classic MTA的運作方式，Adobe Campaign Classic傳送器連線屬於例外情況。

* 提供者傳送 `UNBIND PDU`s.

* `enquire_link` 逾時(在Adobe Campaign端或提供者端)。 您可能會看到 `ENQUIRE_LINK_RESP` 在該情況下具有非零的錯誤代碼。

* 有很多種 `BIND PDU`s.視連線數目而定，一天內不應超過幾個。 每小時應發出超過1個BIND PDU的警報。

如何修正連線穩定性問題：

* 不穩定的連線很少是根本原因，這通常是觸發中斷連線的另一個問題的結果。 優先尋找根本原因。

* 啟用詳細的SMPP追蹤。 您需要他們檢視連線重新啟動時發生的情況。

* 如果提供者傳送 `BIND PDU`s，可能有錯誤。 詢問您的提供者原因 `UNBING` 「 」已傳送。

* 進行網路擷取有時是檢視連線如何關閉的唯一方法。

* 如果提供者透過傳送 `TCP FIN` 或 `TCP RST packet`，請向您的提供者詢問更多資訊。

* 如果提供者在傳送乾淨錯誤後關閉連線，例如 `DELIVER_SM_RESP` 有了錯誤碼，他們必須修正其聯結器，否則將阻止傳輸其他型別的訊息並觸發MTA節流。 這在收發器模式中尤其重要，關閉連線會同時影響MT和SR。

## 傳送MT （傳送一般簡訊給一般使用者）時的問題{#issue-MT}

* 檢查連線是否穩定。 除了Adobe Campaign Classic上的傳送器外，SMPP連線應持續保持至少1小時。 請參閱區段 [不穩定的連線問題](sms-protocol.md#issues-unstable-connection).

* 如果重新啟動MTA讓傳送MT在一小段時間內再次正常運作，您可能會因為連線不穩定而遇到節流問題。 請參閱區段 [不穩定的連線問題](troubleshooting-sms.md#issues-unstable-connection).

* 檢查廣泛記錄檔是否存在且狀態正確，且日期正確。 如果不是，可能是傳遞或傳遞準備問題。

* 檢查MTA是否實際處理訊息。 如果不是這種情況，這可能不是SMS問題。

* 檢查SMS聯結器是否實際與提供者的裝置繫結。 請向提供者要求回饋意見，以確保所有系統皆正常通訊。 另請參閱 `BIND_TRANSMITTER` 和 `BIND_TRANSCEIVER PDU`s以取得繫結程式的相關資訊。 您可能需要啟用SMPP追蹤才能正確進行疑難排解。

* 啟用SMPP追蹤後，請檢查 `SUBMIT_SM PDU` 包含正確的資訊。

* 檢查提供者是否以回應 `SUBMIT_SM_RESP PDU` ，並以「確定」值（代碼0）表示。 請確定PDU以合理的延遲送達：超過1秒的任何時間都必須與提供者討論，通常在100毫秒內送達。

* 如果上述所有步驟都有效，您可以確信問題出在提供者方面。 他們必須在平台上執行疑難排解。

* 如果有效但傳輸量不一致，請嘗試調整傳送視窗並降低MT傳輸量。 您需要與提供者合作才能調整此專案。 Adobe Campaign可以非常快速地傳送訊息，因此提供者的裝置可能會出現效能問題。

## MT重複（同一個SMS會連續多次傳送）{#duplicated-MT}

重複專案通常是由重試所造成。 重試訊息時通常會有重複專案，您應該嘗試移除重試的根本原因。

* 如果您發現傳送的重複專案剛好相隔60秒，可能是提供者端的問題，因此他們不會傳送 `SUBMIT_SM_RESP` 夠快了。

* 如果您看到許多 `BIND/UNBIND`，表示您的連線不穩定。 請參閱[不穩定的連線問題](troubleshooting-sms.md#issues-unstable-connection) 區段，瞭解在嘗試解決重複訊息問題之前的解決方案。

減少重試時的重複專案數量：

* 降低傳送視窗。 傳送視窗應足夠大以涵蓋 `SUBMIT_SM_RESP` 延遲。 其值代表當視窗已滿時發生錯誤時可複製的最大訊息數。

## 處理SR （交貨收貨）時發貨 {#issue-process-SR}

* 您必須啟用SMPP追蹤才能執行任何型別的SR疑難排解。

* 檢查 `DELIVER_SM PDU` 來自提供者，且格式正確。

* 檢查Adobe Campaign是否回覆成功 `DELIVER_SM_RESP PDU` 以及時。 在Adobe Campaign Classic上，這可保證SR已插入 `providerMsgId` SMS程式延遲處理的表格。

如果 `DELIVER_SM PDU` 未成功確認，則您應檢查下列專案：

* 在中檢查與ID擷取和錯誤處理相關的Regex **外部帳戶**. 您可能需要根據的內容 `DELIVER_SM PDU`.

* 檢查錯誤是否已適當地布建在 `broadLogMsg` 表格。

如果 `DELIVER_SM PDU` 已由Adobe Campaign Classic延伸SMPP聯結器確認，但broadLog未正確更新，請檢查一節中說明的ID調解程式 [比對MT、SR和broadlog專案](sms-protocol.md#matching-mt).

如果您修正了所有問題，但某些無效SR仍在提供者的緩衝區中，則可以使用「無效ID認可計數」選項來略過它們。 這應謹慎使用，並在清除緩衝區後儘快重設為0。

## 處理MO （和黑名單/自動回覆）時的問題{#issue-process-MO}

* 在測試期間啟用SMPP追蹤。 如果您沒有啟用TLS，您應該在疑難排解MO時進行網路擷取，以檢查PDU是否包含正確的資訊以及格式是否正確。

* 擷取網路流量或分析SMPP追蹤時，請務必擷取與MO及其回覆MT （如果已設定回覆）的整個交談。

* 如果MO (`DELIVER_SM PDU`)未出現在追蹤中，問題出現在提供者端。 他們必須在平台上執行疑難排解。

* 如果 `DELIVER_SM PDU` 顯示，檢查Adobe Campaign是否確認成功 `DELIVER_SM_RESP PDU` （代碼0）。 此RESP可保證Adobe Campaign已套用所有處理邏輯（自動回覆和允許/封鎖清單）。 如果不是這種情況，請在SMS流程記錄中搜尋錯誤訊息。

* 如果已啟用自動回覆，請檢查 `SUBMIT_SM` 已傳送給提供者。 如果沒有，則保證會在SMS程式記錄中尋找錯誤訊息。

* 如果 `SUBMIT_SM MT PDU` 包含回覆的內容可在追蹤中找到，但SMS未送達行動電話，您必須聯絡提供者以尋求疑難排解方面的協助。

## 準備傳送期間的問題，未排除被隔離的收件者（被自動回覆功能隔離） {#issue-delivery-preparation}

* 檢查隔離表格和傳送記錄中的電話號碼格式是否完全相同。 如果不是，請參考此 [區段](sms-protocol.md#automatic-reply) 如果您遇到國際電話號碼格式的加號首碼問題。

* 檢查短碼。 如果收件者的短程式碼與外部帳戶中定義的相同，或是空白（空白=任何短程式碼），就可能發生排除。 如果整個Adobe Campaign例項只使用一個短程式碼，則更容易全部刪除 **簡短程式碼** 欄位空白。

## 編碼問題 {#encoding-issues}

**步驟1：與提供者聯絡**

請聯絡他們，看看他們有什麼問題。 他們應該能夠告訴您問題是屬於他們一方還是Adobe Campaign一方。 如果問題出在Adobe Campaign，他們應該能夠準確地告訴您哪個欄位不正確。

**步驟2：瞭解訊息內容**

Unicode允許許多類似字元的變體，而Adobe Campaign無法處理所有變體。

最常見的問題來自文書處理器的複製貼上，這會將一般字元變更為印刷體正確的版本：空格變更為不可破斷的空格，雙引號變更為開頭和結尾引號，減號變更為各種連字型大小等。

測試時請勿複製並貼上訊息，請一律直接在介面中輸入。

使用十六進位，您可以分辨類似字元之間的差異。 小寫L、大寫I、O、0、所有不同型別的引號、非拉丁編碼或甚至是不同型別的空格看起來可能都相同，甚至完全不顯示。

若要將unicode轉換為十六進位，您可以使用線上工具，例如 [Unicode程式碼轉換器](https://r12a.github.io/app-conversion/) 網站。 輸入您的文字，確定沒有PII （例如電話號碼），然後按一下 **轉換**. 您會在底部（UTF-32區域）看到十六進位值。

開啟有關編碼問題的票證時(無論與提供者還是 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，請一律加入您所輸入內容與所見內容的十六進位版本。

**步驟3：瞭解您應傳送哪些內容**

決定您預期使用的編碼，並線上上搜尋其字元表。 檢查您要傳送的字元是否確實可在目的碼頁面中使用。 檢查 `data_coding` 欄位正確無誤，且符合您和提供者的預期。

**步驟4：瞭解您實際傳送的內容**

您需要聯結器的偵錯輸出，才能檢視您傳送給提供者的確切位元組。 中出現編碼問題 `SUBMIT_SM PDU`s，請務必擷取它們。 傳送在記錄中容易找到的非常不同的訊息。

測試時傳送不同種類的特殊字元。 例如，GSM7編碼具有十六進位形式非常不同的延伸字元，這些字元很容易識別，因為它們未出現在任何其他編碼中。

## 通訊SMS問題時要包含的元素 {#element-include}

每當您尋求SMS問題的協助時，無論是開啟Adobe Campaign、SMS提供者的支援票證，還是任何有關問題的通訊，您都需要包含下列資訊以確保其符合適當資格。 適當合格的問題是加快解決問題的關鍵。

* **啟用詳細的SMPP訊息** 問題出現時。 沒有這個，大部分的SMS問題都無法解決。

* 如果問題與SMS流量有關，請先聯絡提供者。 他們的平台最適合即時有效診斷SMS流量問題。

* 包括問題的簡短但真實描述。

* 包含預期結果的說明。

* 包含提供者的意見回饋。

* 包含相關記錄檔和/或網路擷取。 進行擷取時，請務必在擷取期間重現問題。

* 如果您包含記錄、追蹤或擷取，請在問題出現時精確定位檔案中的確切位置。

* 如果您參考訊息、PDU或記錄，請清楚說明其時間戳記，以便更容易找到。

* 嘗試在測試環境中重現問題。 如果您不確定設定，請在測試環境中嘗試，然後使用SMPP追蹤檢查結果。 報告在測試環境中復寫的問題通常比直接報告生產環境的問題更好。

* 包含平台上的任何變更或調整。 此外，也請包含提供者可能在他們這邊完成的任何變更。

### 網路擷取 {#network-capture}

不一定需要網路擷取，通常只要詳細的SMPP訊息就足夠了。 以下是一些准則，可協助您判斷是否需要網路擷取：

* 連線問題，但詳細訊息未顯示任何 `BIND_RESP PDU`.

* 無法解釋的連線中斷沒有錯誤訊息，這是聯結器偵測到低層級通訊協定錯誤時的正常行為。

* 提供者抱怨解除繫結/中斷連線程式。

* 選擇性TLV欄位中出現編碼問題。

* 不同連線之間懷疑混合了流量。

在所有其他情況下，請先嘗試分析詳細的SMPP訊息，並只在詳細記錄中缺少資訊時要求網路擷取。

在某些情況下，不需要擷取網路流量。 最常見的情況如下：

* TLS已啟用：根據定義，TLS流量會加密，因此無法擷取。

* 效能問題：記錄檔包含追蹤效能問題所需的所有資訊。

* 計時問題(`retry timing`， `enquire_link` 期間、輸送量上限等)

* SR剖析和處理：詳細記錄檔可提供更多內容與更佳的簡報。

* MO處理（自動回覆、隔離）。

* 未涉及實際SMPP流量的錯誤：傳遞準備、訊息中心API問題、工作流程問題等。

## 啟用SMPP追蹤 {#enabling-smpp-traces}

新聯結器支援透過追蹤的延伸記錄： SMPP。 追蹤是MTA記錄檔中的輸出，而不是標準輸出中。

**為每個外部帳戶啟用（偏好方法）**

1. 在 **外部帳戶**，檢查 **在記錄檔中啟用詳細的SMPP追蹤**.
1. 等待10分鐘，讓伺服器重新載入外部帳戶。

現在應該會啟用。

**在設定中啟用**

在 `config-instance.xml` 檔案中，設定下列引數：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 檢查容器上開啟的連線數目 {#open-connections}

若要檢查容器上開啟的連線數目，您可以使用此命令：

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

這會列出為指定連線埠開啟的連線數目。 我們在這裡使用連線埠3600。

結果應如下所示：

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

為sms程式開啟4個連線，以及每個具有5個子系的mta子系2個。
