---
solution: Campaign Classic
product: campaign
title: SMS 疑難排解
description: 進一步瞭解如何疑難排解SMS頻道
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---


# SMS疑難排解{#troubleshooting-sms}

## 不同外部帳戶之間的衝突{#external-account-conflict}

如果實例有多個SMS外部帳戶，您必須檢查問題是否不是由外部帳戶之間的衝突造成的。

Adobe Campaign將外部帳戶視為不相關的實體。

如果您有多個帳戶，請依照下列步驟隔離導致問題的外部帳戶：

1. 禁用所有外部帳戶。
1. 啟用一個外部帳戶。
1. 嘗試重現問題。
1. 如果初始問題不總是出現，在結束之前先進行合理的嘗試。
1. 如果該單一帳戶未出現問題，請停用該問題，然後重新啟動至下一個帳戶的步驟2。

當您個別檢查每個帳戶後，可能會出現2種情況：

* **問題出現在一或多個帳戶上**

   在這種情況下，您可以針對每個帳戶分別套用其他疑難排解程式。 最好在診斷帳戶時停用其他帳戶，以減少網路流量和記錄檔數。

* **在任何時候只有一個帳戶處於活動狀態時，問題未出現**

   帳戶之間有衝突。 如前所述，Adobe Campaign單獨處理帳戶，但提供商可以將其視為單個帳戶。

   * 您在所有帳戶之間使用不同的登入／密碼組合。
您必須聯絡提供者，以診斷他們可能的衝突。

   * 部分外部帳戶共用相同的登入／密碼組合。
提供者無法得知`BIND PDU`來自哪個外部帳戶，因此他們會將來自多個帳戶的所有連線視為單一帳戶。 他們可能已隨機將MO和SR路由到兩個帳戶，導致問題。
如果提供者支援相同登入／密碼組合的多個簡短代碼，您必須詢問他們在`BIND PDU`中放置該簡短代碼的位置。 請注意，此項資訊必須放在`BIND PDU`中，而不是放在`SUBMIT_SM`中，因為`BIND PDU`是唯一可正確傳送MO的地方。
請參閱上述每種PDU](../../delivery/using/sms-protocol.md#information-pdu)中的[資訊部分，瞭解`BIND PDU`中有哪個欄位可用，通常在`address_range`中添加短代碼，但需要提供商的特殊支援。 請與他們聯絡，瞭解他們希望如何個別傳送多個簡短代碼。
Adobe Campaign支援處理相同外部帳戶的多個簡短代碼。

## 一般{#external-account-issues}的外部帳戶問題

* 調查連接器最近是否更改過，以及更改者（選中「外部帳戶」作為組）。

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* 調查（在/postupgrade目錄中）系統是否已升級，以及何時
* 調查影響SMS的任何套件最近是否已升級(/var/log/dpkg.log)。

## 中端來源（托管）問題{#issue-mid-sourcing}

* 如果問題發生在中間採購環境中，請確保在中間採購伺服器上正確建立和更新交貨和廣泛日誌。 如果不是這樣，這不是SMS問題。

* 如果中端伺服器上的所有功能都正常運作，而SMS已正確傳送，但行銷例項未正確更新，則可能會發生中端同步問題。

## 連接到提供程式{#issue-provider}時出現問題

* 如果`BIND PDU`傳回非零`command_status`代碼，請向提供者查詢詳細資訊。

* 檢查網路是否已正確配置，以便能夠與提供者建立TCP連接。

* 請要求提供者檢查他們是否將IP正確添加到Adobe Campaign實例的允許清單。

* 檢查&#x200B;**External account**&#x200B;設定。 向提供者詢問欄位的值。

* 如果連接成功但不穩定，請檢查[連接不穩定問題](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection)部分。

* 如果連接問題難以診斷，網路捕獲可以提供資訊。 確保網路捕獲在出現問題時同時運行，以便高效地分析。 您也應注意問題出現的確切時間。

## 連接不穩定的問題{#issues-unstable-connection}

如果發生以下任一情況，則將連接視為不穩定：

* 連線持續不到1小時。 Adobe Campaign Classic的發射器連接因Adobe Campaign ClassicMTA的工作方式而成為例外。

* 提供程式發送`UNBIND PDU`s。

* `enquire_link` 逾時，不論是在Adobe Campaign方面，還是在供應商方面。在此情況下，您可能會看到`ENQUIRE_LINK_RESP`包含非零錯誤代碼。

* 有很多`BIND PDU`s。一天中不應超過幾個，具體取決於連接數。 每小時多於1個BIND PDU應該是警報。

如何修復連接穩定性問題：

* 不穩定的連接很少是根本原因，這通常是另一個導致中斷連接的問題的結果。 優先順序是找出根本原因。

* 啟用詳細SMPP跟蹤。 您需要他們在連線重新啟動時查看發生的情況。

* 如果提供程式發送`BIND PDU`s，則可能出了問題。 詢問您的供應商傳送`UNBING`的原因。

* 獲取網路捕獲有時是查看連接關閉方式的唯一方法。

* 如果提供程式通過發送`TCP FIN`或`TCP RST packet`關閉連接，請向您的提供程式詢問詳細資訊。

* 如果提供者在發送清除錯誤（例如`DELIVER_SM_RESP`含錯誤代碼）後關閉連接，則必須修復其連接器，否則將阻止其它類型的消息傳輸，並觸發MTA調節。 在收發器模式中，關閉連接會影響MT和SR，這一點尤其重要。

## 傳送MT（一般SMS傳送給使用者）時的問題{#issue-MT}

* 檢查連接是否穩定。 除Adobe Campaign Classic的發射器外，SMPP連接應持續保持至少1小時。 請參閱[不穩定連接問題](../../delivery/using/sms-protocol.md#issues-unstable-connection)一節。

* 如果重新啟動MTA使發送MT在一小段時間內再次工作，則可能由於連接不穩定而出現頻寬限制。 請參閱[不穩定連接問題](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection)一節。

* 檢查廣泛日誌是否存在，且狀態正確且日期正確。 如果不是，這可能是遞送或遞送準備問題。

* 檢查MTA是否實際處理訊息。 如果不是這樣，這可能不是SMS問題。

* 檢查SMS連接器是否實際與供應商的設備綁定。 請要求提供者提供意見回應，以確保所有系統都正常通訊。 有關綁定進程的資訊，請參見`BIND_TRANSMITTER`和`BIND_TRANSCEIVER PDU`s。 您可能需要啟用SMPP跟蹤以進行正確的故障排除。

* 啟用SMPP跟蹤後，檢查`SUBMIT_SM PDU`是否包含正確的資訊。

* 檢查提供者是否以`SUBMIT_SM_RESP PDU`回應，並輸入&quot;OK&quot;值（代碼0）。 確保PDU到達時有合理的延遲：超過1秒的內容必須與供應商討論，通常會在100毫秒內到達。

* 如果所有這些步驟都能運作，您可以確信問題出在提供方。 他們必須在其平台上進行疑難排解。

* 如果它有效但吞吐量不一致，請嘗試調整發送窗口並降低MT吞吐量。 您需要與提供者合作來調整。 Adobe Campaign可以很快地發送消息，因此供應商的設備上可能出現效能問題。

## 複製MT（同一條SMS會一行多次發送）{#duplicated-MT}

重複項目通常由重試造成。 重試消息時出現重複是正常的，您應嘗試移除重試的根本原因。

* 如果您看到重複項目相隔60秒，這可能是提供者端的問題，他們傳送`SUBMIT_SM_RESP`的速度不夠快。

* 如果您看到許多`BIND/UNBIND`，表示連接不穩定。 在嘗試解決重複消息問題之前，請參見[不穩定連接問題](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection)一節以瞭解解決方案。

在重試時降低重複數量：

* 降低傳送視窗。 傳送視窗應足夠大，以涵蓋`SUBMIT_SM_RESP`延遲。 其值代表當視窗已滿時發生錯誤時，可複製的訊息數目上限。

## 處理SR（交貨收據）{#issue-process-SR}時發出問題

* 您需要啟用SMPP跟蹤才能執行任何類型的SR故障排除。

* 檢查`DELIVER_SM PDU`是否來自提供者，且其格式正確。

* 及時檢查Adobe Campaign以成功`DELIVER_SM_RESP PDU`回覆。 在Adobe Campaign Classic，這保證SR已插入`providerMsgId`表中，以便由SMS進程延遲處理。

如果`DELIVER_SM PDU`未成功確認，則應檢查以下內容：

* 在&#x200B;**External account**&#x200B;中檢查與ID提取和錯誤處理相關的regex。 您可能需要根據`DELIVER_SM PDU`的內容來驗證它們。

* 檢查`broadLogMsg`表中是否正確設定了錯誤。

如果`DELIVER_SM PDU`已由Adobe Campaign Classic擴展SMPP連接器確認，但broadLog未正確更新，請檢查[匹配MT、SR和broadlog條目](../../delivery/using/sms-protocol.md#matching-mt)一節中介紹的ID協調過程。

如果您修正了所有問題，但某些無效的SR仍在提供方的緩衝區中，則可以使用「無效的ID確認計數」選項跳過這些問題。 這應謹慎使用，並在緩衝區清除後盡快重設為0。

## 處理MO（和黑名單／自動回覆）時的問題{#issue-process-MO}

* 在測試期間啟用SMPP跟蹤。 如果未啟用TLS，在對MO進行故障排除時，應執行網路捕獲，以檢查PDU是否包含正確的資訊並且格式正確。

* 在捕獲網路流量或分析SMPP跟蹤時，如果配置了回覆，請確保捕獲與MO及其回覆MT的整個會話。

* 如果MO(`DELIVER_SM PDU`)未出現在跟蹤中，則問題出在提供方。 他們必須在其平台上進行疑難排解。

* 如果出現`DELIVER_SM PDU`，請檢查是否由Adobe Campaign確認`DELIVER_SM_RESP PDU`（代碼0）成功。 此RESP保證所有處理邏輯都由Adobe Campaign（自動回覆和允許／拒絕清單）所套用。 如果不是，請在SMS流程記錄檔中搜尋錯誤訊息。

* 如果已啟用自動回覆，請檢查`SUBMIT_SM`是否已傳送給提供者。 如果沒有，保證會在SMS程式記錄檔中找到錯誤訊息。

* 如果在追蹤中找到包含回覆的`SUBMIT_SM MT PDU`，但SMS未送達行動電話，您必須聯絡提供者以取得疑難排解的協助。

## 傳送準備期間未排除隔離收件者（由自動回覆功能隔離）的問題{#issue-delivery-preparation}

* 檢查隔離表和傳送日誌中的電話號碼格式是否完全相同。 如果沒有，請參閱此[部分](../../delivery/using/sms-protocol.md#automatic-reply)，如果您對國際電話號碼格式的加號前置詞有問題。

* 查看簡碼。 如果收件者的簡短代碼與外部帳戶中定義的代碼相同，或者是空白代碼（空白=任何簡短代碼），則可能會發生排除。 如果整個Adobe Campaign實例只使用一個短代碼，則更容易將所有&#x200B;**短代碼**&#x200B;欄位留空。

## 編碼問題{#encoding-issues}

**步驟1:與提供者聯絡**

聯絡他們，看看他們有什麼問題。 他們應該能夠告訴你，問題是站在他們這邊還是在Adobe Campaign那邊。 如果問題出在Adobe Campaign，他們應該能夠確切地告訴你哪個欄位不正確。

**步驟2:瞭解訊息中的內容**

Unicode允許許多類似字元的變體，而Adobe Campaign無法處理所有變體。

最常見的問題來源是從文字處理器複製貼上，將常見字元變更為印刷正確的版本：空格變為非破斷空格，雙引號變為開號和閉號，減號變為各種連字型大小等。

測試時不要複製並貼上訊息，請務必直接在介面中輸入訊息。

使用十六進位，您可以區分相似字元之間的差異。 小寫L、大寫I、O、0、所有不同類型的引號、非拉丁編碼或甚至不同類型的空格看起來都相同甚至完全不顯示。

若要將Unicode轉換為十六進位，您可以使用線上工具，例如[Unicode代碼轉換器](https://r12a.github.io/app-conversion/)網站。 輸入文字，確定沒有PII（例如電話號碼），然後按一下「轉換&#x200B;**」。**&#x200B;您會在底部看到十六進位值（UTF-32區域）。

在開啟有關編碼問題的票證時，無論是與提供者或[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)一起開啟，始終包含您鍵入的內容和所看到內容的十六進位版本。

**步驟3:瞭解您應傳送的內容**

判斷您預期使用的編碼，並線上搜尋其字元表格。 檢查您要傳送的字元是否實際可在目標程式碼頁面中使用。 檢查`data_coding`欄位是否正確，並符合您和提供者的期望。

**步驟4:瞭解您實際發送的**

您需要連接器的除錯輸出，才能確切看到您傳送給提供者的位元組。 編碼問題會出現在`SUBMIT_SM PDU`s中，請務必擷取。 傳送非常明確的訊息，在記錄檔中可輕鬆找到。

測試時傳送不同種類的特殊字元。 例如，GSM7編碼具有十六進位格式非常不同的擴展字元，它們很容易發現，因為它們不出現在任何其它編碼中。

## 在與SMS問題{#element-include}通訊時要包含的元素

每當您在SMS問題上尋求協助時，不論是開啟支援票證給Adobe Campaign、SMS提供者，或是與此問題進行任何通訊時，您都需要包含下列資訊，以確保其符合資格。 合格的問題是更快解決問題的關鍵。

* **當問題出現** 時啟用詳細SMPP消息。沒有這個，大部分的SMS問題都是無法解決的。

* 如果問題與SMS流量有關，請先聯絡提供者。 其平台最適合用於SMS流量問題的即時有效診斷。

* 包含問題的簡短但事實的描述。

* 包含預期結果的說明。

* 納入提供者的意見回應。

* 包括相關日誌和／或網路捕獲。 執行捕獲時，請確保在捕獲期間重現問題。

* 如果您包含記錄檔、追蹤或擷取，請在出現問題時找出檔案中的確切位置。

* 如果您引用消息、PDU或日誌，請清楚地聲明其時間戳記，以便更容易找到。

* 嘗試在測試環境中重現問題。 如果您不確定設定，請在測試環境中試用，並使用SMPP追蹤檢查結果。 通常，報告在測試環境中複製的問題比直接報告生產環境中的問題要好。

* 加入平台上所做的任何變更或調整。 此外，還應包含供應商可能在其一方所做的任何變更。

### 網路捕獲{#network-capture}

網路擷取並不總是需要，通常冗長的SMPP訊息就足夠了。 以下是一些幫助您確定是否需要網路捕獲的准則：

* 連線問題，但詳細訊息不會顯示任何`BIND_RESP PDU`。

* 無法解釋的斷開連接，沒有錯誤消息，這是連接器在檢測到低級協定錯誤時的常見行為。

* 提供者抱怨解除綁定／斷開連接過程。

* 可選TLV欄位中的編碼問題。

* 流量可能混在不同的連線之間。

在所有其他情況下，請嘗試先分析詳細的SMPP消息，並僅在詳細日誌中缺少資訊時才請求網路捕獲。

在某些情況下，不需要擷取網路流量。 以下是最常見的情況：

* 啟用TLS:根據定義，TLS流量會加密，因此無法擷取。

* 效能問題：記錄檔包含追蹤效能問題的所有必要資訊。

* 計時問題（`retry timing`、`enquire_link`期間、吞吐量上限等）

* SR解析和處理：詳細記錄可提供更多內容和更佳的簡報。

* MO處理（自動回覆、隔離）。

* 不涉及實際SMPP流量的錯誤：傳送準備、訊息中心API問題、工作流程問題等。

## 啟用SMPP跟蹤{#enabling-smpp-traces}

新連接器支援通過跟蹤擴展日誌：SMPP。 追蹤是在MTA記錄檔中輸出，而非在標準輸出中。

**依外部帳戶啟用（偏好的方法）**

1. 在&#x200B;**External account**&#x200B;中，選中&#x200B;**在日誌檔案**&#x200B;中啟用詳細SMPP跟蹤。
1. 等待10分鐘，讓伺服器重新載入外部帳戶。

它現在應該是活動的。

**在配置中啟用**

在`config-instance.xml`檔案中，設定下列參數：

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 檢查容器{#open-connections}上開啟的連接數

要檢查容器上開啟的連接數，可使用以下命令：

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

這將列出為給定埠開啟的連接數。 這裡我們使用埠3600。

結果應如下：

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4個已開啟的簡訊程式連線，2個每mta子系，5個子系。
