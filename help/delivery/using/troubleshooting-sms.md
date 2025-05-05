---
product: campaign
title: 簡訊疑難排解
description: 進一步瞭解如何疑難排解簡訊頻道
feature: SMS, Troubleshooting
role: User
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: f660dcbb111e73f12737d96ebf9be2aeccbca8ee
workflow-type: tm+mt
source-wordcount: '3044'
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
1. 如果初始問題並非總是出現，請在結束前進行合理的嘗試次數。
1. 如果該單一帳戶未出現問題，請停用該帳戶，然後重新啟動至下一個帳戶的步驟2。

當您分別檢查每個帳戶後，可能會出現以下兩種情況：

* **問題出現在一或多個帳戶上**

  在這種情況下，您可以對每個帳戶個別套用其他疑難排解程式。 最好在診斷帳戶時停用其他帳戶，以減少網路流量和記錄數量。

* **在任何時候只有一個帳戶作用中時，問題未出現**

  帳戶之間發生衝突。 如前所述，Adobe Campaign會個別處理帳戶，但提供者可能會將其視為單一帳戶。

   * 您在所有帳戶之間使用不同的登入/密碼組合。
您必須連絡提供者，才能診斷其身邊的潛在衝突。

   * 某些外部帳戶共用相同的 登入/密碼 組合。供應商無法分辨外部帳戶 `BIND PDU` 來自哪個，因此他們將來自多個帳戶的所有連接視為單個連接。 他們可能通過這兩個帳戶隨機路由MO和SR，從而導致問題。如果提供程序支持同一 登入/密碼 組合的多個短代碼，則必須詢問他們將該短代碼放在 .`BIND PDU`請注意，這條信息必須放在 中 `BIND PDU`，而不是 `SUBMIT_SM`放在 中，因為 是唯一 `BIND PDU` 允許正確路由MO的地方。請參閱上面各種PDU[&#128279;](sms-protocol.md#information-pdu)區段中的資訊，以瞭解`BIND PDU`中可用的欄位，通常是您在`address_range`中新增短程式碼，但需要提供者的特殊支援。 請聯絡他們，以瞭解他們如何獨立路由多個短程式碼。
Adobe Campaign支援在相同的外部帳戶上處理多個短程式碼。

## 一般外部帳戶問題 {#external-account-issues}

* 調查連接器最近是否已更改以及由誰更改（檢查外部帳戶作為群組）。

  ```
  select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
  
  (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
  
  (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
  
  N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
  
  from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
  ```

* 調查（在 /postupgrade 目錄中）系統是否已升級以及何時升級
* 調查最近是否升級了影響SMS的任何包 （/var/log/dpkg.log）。

## 中間來源的問題 （託管）{#issue-mid-sourcing}

* 如果問題發生在中間來源環境上，請確保在中間來源伺服器上正確創建和更新傳遞和廣泛的日誌。 如果不是這種情況，則這不是簡訊問題。

* 如果一切在中間伺服器上運作正常，且簡訊已正確傳送，但行銷執行個體未正確更新，則您可能會發生中間同步問題。

## 連線到提供者時的問題 {#issue-provider}

* 如果`BIND PDU`傳回非零`command_status`代碼，請詢問提供者以取得詳細資訊。

* 檢查網路是否已正確設定，以便與提供者建立TCP連線。

* 要求提供者確認其是否已正確將IP新增至Adobe Campaign執行個體的允許清單。

* 檢查&#x200B;**外部帳戶**&#x200B;設定。 詢問提供者欄位的值。

* 如果連線成功但不穩定，請檢查[問題與不穩定的連線](troubleshooting-sms.md#issues-unstable-connection)區段。

* 如果連線問題難以診斷，網路擷取可提供資訊。 請確定網路擷取在問題出現時同時執行，以便有效地分析問題。 您也應該記下問題出現的確切時間。

## 連線不穩定的問題 {#issues-unstable-connection}

如果發生下列任一情況，則會將連線視為不穩定：

* 連線持續少於1小時。 由於Adobe Campaign Classic MTA的運作方式，Adobe Campaign Classic傳送器連線屬於例外情況。

* 提供者傳送`UNBIND PDU`。

* `enquire_link`逾時，在Adobe Campaign端或提供者端皆然。 在這種情況下，您可能會看到帶有非零錯誤代碼的`ENQUIRE_LINK_RESP`。

* 有許多`BIND PDU`。視連線數目而定，一天內不應超過幾次。 每小時應發出超過1個BIND PDU的警報。

如何修正連線穩定性問題：

* 不穩定的連線很少是根本原因，這通常是另一個問題觸發中斷連線所造成。 優先尋找根本原因。

* 啟用詳細的SMPP追蹤。 您需要他們檢視連線重新啟動時發生的情況。

* 如果提供者傳送`BIND PDU`，則可能有錯誤。 詢問您的提供者為何傳送`UNBING`。

* 進行網路擷取有時是檢視連線如何關閉的唯一方法。

* 如果提供者透過傳送`TCP FIN`或`TCP RST packet`來關閉連線，請詢問您的提供者更多資訊。

* 如果提供者在傳送包含錯誤碼的全新錯誤（例如`DELIVER_SM_RESP`）後關閉連線，則他們必須修正其聯結器，否則將阻止傳輸其他型別的訊息，並觸發MTA節流。 在收發器模式中，這尤其重要，因為關閉連線會同時影響MT和SR。

## 傳送MT （傳送給一般使用者的一般SMS）時的問題{#issue-MT}

* 檢查連線是否穩定。 除了Adobe Campaign Classic上的傳送器外，SMPP連線應持續保持至少1小時。 請參閱[不穩定連線的問題](sms-protocol.md#issues-unstable-connection)一節。

* 如果重新啟動MTA讓傳送MT在短時間內再次運作，則可能是因為連線不穩定而發生節流。 請參閱[不穩定連線的問題](troubleshooting-sms.md#issues-unstable-connection)一節。

* 檢查廣泛記錄檔是否存在且狀態正確，且日期正確。 如果不是，可能是傳送或傳送準備問題。

* 檢查MTA是否實際處理訊息。 如果不是這種情況，這可能不是SMS問題。

* 檢查SMS聯結器是否實際與提供者的裝置繫結。 請向提供者要求回饋意見，以確保所有系統皆能正常通訊。 請參閱`BIND_TRANSMITTER`和`BIND_TRANSCEIVER PDU`以取得繫結程式的資訊。 您可能需要啟用SMPP追蹤才能正確進行疑難排解。

* 啟用SMPP追蹤後，請檢查`SUBMIT_SM PDU`是否包含正確的資訊。

* 檢查提供者是否以「確定」值（代碼0）回應`SUBMIT_SM_RESP PDU`。 請確定PDU在到達時會有合理的延遲：超過1秒的任何時間都必須與提供者討論，通常在100毫秒內到達。

* 如果所有這些步驟都有效，您可以確信問題出在提供者方面。 他們必須在平台上執行疑難排解。

* 如果它可以運作，但輸送量不一致，請嘗試調整傳送視窗並降低MT輸送量。 您需要與提供者合作以調整此專案。 Adobe Campaign可以快速傳送訊息，因此提供者的裝置可能會出現效能問題。

## MT重複（同一個SMS會連續多次傳送）{#duplicated-MT}

重複專案通常是由重試所造成。 重試訊息時一般會有重複專案，您應該嘗試移除重試的根本原因。

* 如果您發現傳送的重複專案剛好相隔60秒，可能是提供者端的問題，他們傳送`SUBMIT_SM_RESP`的速度不夠快。

* 如果您看到許多`BIND/UNBIND`，表示您的連線不穩定。 在嘗試解決重複訊息問題之前，請先參閱[不穩定的連線問題](troubleshooting-sms.md#issues-unstable-connection)一節以取得解決方案。

降低重試時的重複專案數量：

* 降低傳送視窗。 傳送視窗應該足夠大，以涵蓋`SUBMIT_SM_RESP`延遲。 其值表示在視窗已滿時發生錯誤時可以複製的最大消息數。

## 處理SR（傳遞收據）時出現問題 {#issue-process-SR}

* 您需要啟用 SMPP 追蹤才能執行任何類型的 SR 故障排除。

* 檢查`DELIVER_SM PDU`是否來自提供者，其格式是否正確。

* 檢查Adobe Campaign是否及時回覆成功的`DELIVER_SM_RESP PDU`。 在Adobe Campaign Classic上，這可保證SR已插入`providerMsgId`資料表，以供SMS程式延遲處理。

`DELIVER_SM PDU`如果未成功確認，則應檢查以下內容：

* 檢查與外部帳戶&#x200B;**中的** id 摘取和錯誤處理相關的正則表示式。您可能需要根據 的 `DELIVER_SM PDU`內容對其進行驗證。

* 檢查表中是否正確預配 `broadLogMsg` 了錯誤。

如果 已被 `DELIVER_SM PDU` Adobe Campaign Classic 擴展 SMPP 連接器確認，但 broadLog 未正確更新，請檢查匹配 MT、SR 和 broadlog 條目[&#128279;](sms-protocol.md#matching-mt)部分中描述的 ID 協調過程。

如果修復了除某些 無效 SR 仍在提供程式緩衝區中的所有內容，則可以使用“無效 ID 確認計數”選項跳過它們。 應謹慎使用，並在緩衝區清理后儘快重置為 0。

## 處理MO （以及黑名單/自動回覆）時的問題{#issue-process-MO}

* 在測試期間啟用SMPP追蹤。 如果您沒有啟用TLS，您應該在疑難排解MO時進行網路擷取，以檢查PDU是否包含正確資訊及格式是否正確。

* 擷取網路流量或分析SMPP追蹤時，如果設定了回覆，請務必擷取與MO及其回覆MT的整個交談。

* 如果MO (`DELIVER_SM PDU`)未出現在追蹤中，則問題是在提供者端。 他們必須在平台上執行疑難排解。

* 如果`DELIVER_SM PDU`出現，請檢查Adobe Campaign是否確認它並成功`DELIVER_SM_RESP PDU` （代碼0）。 此RESP可保證所有處理邏輯已由Adobe Campaign套用（自動回覆和允許/封鎖清單）。 如果不是這種情況，請在SMS流程日誌中搜尋錯誤訊息。

* 如果已啟用自動回覆，請檢查`SUBMIT_SM`是否已傳送給提供者。 如果沒有，在SMS程式記錄中一定會找到錯誤訊息。

* 如果在追蹤中找到包含回覆的`SUBMIT_SM MT PDU`，但簡訊未送達行動電話，您必須連絡提供者以取得疑難排解方面的協助。

## 未排除被隔離的收件者（被自動回覆功能隔離）的傳送準備期間的問題 {#issue-delivery-preparation}

* 檢查隔離表格和傳送記錄中的電話號碼格式是否完全相同。 如果不是，請參閱此[區段](sms-protocol.md#automatic-reply) （如果您遇到國際電話號碼格式的加號首碼問題）。

* 檢查短程式碼。 如果收件者的短程式碼與外部帳戶中定義的相同，或是空白（空白=任何短程式碼），則可能會發生排除。 如果整個Adobe Campaign執行個體只使用一個短程式碼，則比較容易讓所有&#x200B;**短程式碼**&#x200B;欄位都留空。

## 編碼問題 {#encoding-issues}

**步驟1：與提供者連絡**

請聯絡他們，看看他們有什麼問題。 他們應該可以告訴您問題是在他們這邊還是Adobe Campaign這邊。 如果問題出在Adobe Campaign，他們應該能夠告訴您確切的欄位不正確。

**步驟2：瞭解您訊息的內容**

Unicode允許許多類似字元的變體，而Adobe Campaign無法處理所有變體。

最常見的問題來自文書處理器的複製貼上，這會將常見的字元變更為印刷正確的版本：空格變更為不可破斷的空格，雙引號變更為開頭和結尾引號，減號變更為各種連字型大小等。

測試時請勿複製並貼上訊息，請一律直接在介面中輸入。

使用十六進位，您可以分辨類似字元之間的差異。 小寫L、大寫I、O、0、所有不同型別的引號、非拉丁編碼或甚至不同型別的空格可能看起來都相同，甚至完全不顯示。

若要將unicode轉換為十六進位，您可以使用線上工具，例如[Unicode代碼轉換器](https://r12a.github.io/app-conversion/)網站。 輸入您的文字，確定沒有PII （例如電話號碼），然後按一下&#x200B;**轉換**。 您會在底部（UTF-32區域）看到十六進位值。

開啟有關編碼問題的票證時，無論是否透過提供者或[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)，請一律包含您所輸入內容的十六進位版本，以及您所看到的內容。

**步驟3：瞭解您應該傳送哪些內容**

決定您要使用的編碼，並線上上搜尋其字元表。 檢查您要傳送的字元是否確實可在目的碼頁面中使用。 檢查`data_coding`欄位是否正確，並符合您和提供者預期的欄位。

**步驟4：瞭解您實際傳送的內容**

您將需要聯結器的偵錯輸出，才能檢視您傳送給提供者的確切位元組。 編碼問題出現在`SUBMIT_SM PDU`中，因此請務必擷取它們。 傳送在記錄中容易找到的非常不同的訊息。

測試時傳送不同種類的特殊字元。 例如，GSM7編碼具有十六進位形式非常不同的延伸字元，這些字元很容易辨識，因為它們沒有出現在任何其他編碼中。

## 通訊SMS問題時要包含的元素 {#element-include}

每當您尋求SMS問題的協助時(無論是開啟Adobe Campaign的支援票證、SMS提供者，或有關問題的任何通訊型別)，都需要包含下列資訊以確保其正確符合資格。 適當合格的問題是加快解決問題的關鍵。

* **出現問題時啟用詳細的SMPP訊息**。 沒有這個，大部分的SMS問題都無法解決。

* 如果問題與SMS流量有關，請先聯絡提供者。 他們的平台最適合即時有效診斷SMS流量問題。

* 包括問題的簡短但實事求是的描述。

* 包括預期結果的說明。

* 包含提供者的意見回饋。

* 包含相關記錄檔和/或網路擷取。 進行擷取時，請務必在擷取期間重現問題。

* 如果您包含記錄、追蹤或擷取，請在問題出現時精確定位檔案中的確切位置。

* 如果您參考訊息、PDU或記錄，請清楚說明其時間戳記，以便更容易找到。

* 嘗試在測試環境中重現問題。 如果您不確定設定，請在測試環境中嘗試，並使用SMPP追蹤檢查結果。 報告測試環境中復寫的問題通常比直接報告生產環境中問題要好。

* 包括在平台上所做的任何變更或調整。 此外，也請包含提供者可能已在其一側完成的任何變更。

### 網路捕獲 {#network-capture}

並不總是需要網路捕獲，通常冗長的SMPP消息就足夠了。 下面是一些準則，可説明您確定是否需要網路捕獲：

* 連線問題，但詳細訊息未顯示任何`BIND_RESP PDU`。

* 無法解釋的連線沒有錯誤訊息，這是聯結器偵測到低層通訊協定錯誤時的正常行為。

* 提供者抱怨解除繫結/中斷連線程式。

* 可選 TLV 欄位中的編碼問題。

* 在不同的連線之間懷疑是混合的流量。

在所有其他情況下，請嘗試先分析詳細的SMPP訊息，並僅在詳細記錄中缺少資訊時請求網路擷取。

在某些情況下，不需要擷取網路流量。 最常見的情況如下：

* TLS已啟用：根據定義，TLS流量會加密，因此無法擷取。

* 效能問題：記錄檔包含追蹤效能問題所需的所有資訊。

* 計時問題（`retry timing`、`enquire_link`週期、輸送量上限等）

* SR剖析和處理：詳細記錄檔可提供更多內容和更好的簡報。

* mo處理（自動回覆、隔離）。

* 未涉及實際SMPP流量的錯誤：傳遞準備、訊息中心API問題、工作流程問題等。

## 啟用SMPP追蹤 {#enabling-smpp-traces}

新聯結器支援透過追蹤的延伸記錄： SMPP。 追蹤輸出於MTA記錄檔中，而非標準輸出中。

**為每個外部帳戶啟用（偏好方法）**

1. 在&#x200B;**外部帳戶**&#x200B;中，勾選&#x200B;**在記錄檔**&#x200B;中啟用詳細的SMPP追蹤。
1. 等待10分鐘，讓伺服器重新載入外部帳戶。

現在應該會啟用。

**正在設定中啟用**

在`config-instance.xml`檔案中，設定下列引數：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 檢查容器上開啟的連線數目 {#open-connections}

若要檢查容器上開啟的連線數目，您可以使用此命令：

```
(for pid in $(ss -neopts  | sed -n 's/^.*:3600[ \t].*users:(([0-9A-Za-z"]*,pid=\([0-9]*\),.*$/\1/p' | sort ); do  cat /proc/$pid/cmdline; echo  " $pid" ;done;) | uniq --count
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

為sms流程開啟4個連線，每個具有5個子系的mta子系開啟2個連線。

## 簡訊傳遞狀態之間的差異

若要釐清&#x200B;**已傳送**、**已傳送給提供者**&#x200B;與&#x200B;**已接收行動裝置**&#x200B;狀態之間的差異，請參閱下列詳細定義：

* **已在行動裝置上接收**：
訊息已成功傳遞至使用者的裝置，並透過行動已終止(MT)傳遞和狀態報告(SR)兩者提供的確認。

* **已傳送**：
已透過行動裝置已終止(MT)步驟成功處理訊息，但尚未收到確認傳遞到行動裝置的狀態報告(SR)。

* **傳送給提供者**：
訊息已使用`SUBMIT_SM command`傳送給提供者，但未收到提供者的`SUBMIT_SM_RESP`確認。

訊息可能維持在&#x200B;**已傳送**&#x200B;狀態，因為轉換至&#x200B;**已接收**&#x200B;取決於使用者裝置的狀態報告(SR)。 如果使用者的儲存格接收不良或其他連線問題，他們可能不會立即收到訊息。 在這種情況下，提供者應負責重試傳送，或說明未產生SR的原因。 如果提供者發現任何不一致，就必須確保Campaign的行為符合預期。

以下是標準SMS傳送狀態：

* **擱置中**：郵件尚未傳送給彙總。

* **提供者已考慮**：郵件已傳送至彙總，且彙總已確認回條。

* **已傳送**：彙總器已確認訊息已成功推送至使用者的行動網路，且沒有立即發生任何錯誤。

* **在行動裝置上接收**：使用者的行動裝置已確認接收，且彙總器已驗證此訊息。

* **失敗**：郵件已傳送至彙總程式，彙總程式嘗試在定義的時間段（例如，幾個小時）內傳送至使用者的行動裝置。 由於網路問題、使用者裝置無法使用或其他原因，傳送最終失敗。
