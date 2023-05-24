---
product: campaign
title: 追蹤疑難排解
description: 本節提供與Adobe Campaign中的追蹤設定和實作相關的常見問題
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: 62e67a39-1e5c-4716-a3f3-b0ca69693cd0
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 1%

---

# 追蹤疑難排解 {#tracking-troubleshooting}



在本節中，您將找到與Adobe Campaign Classic中的追蹤設定和實作相關的常見問題。

## 追蹤工作流程失敗 {#tracking-workflow-failing}

我的追蹤工作流程失敗，如何偵測追蹤檔案中的損毀行？

>[!NOTE]
>
>僅適用於Windows

損毀的追蹤記錄檔……/nl6/var/&lt;instance_name>/redir/log/0x0000記錄檔可以停止追蹤工作流程。 若要輕鬆偵測損壞的行並移除它們以繼續追蹤工作流程，您可以使用以下命令。

### 我知道損壞的行位於哪個檔案中

在這種情況下，可以在0x00000000000A0000.log檔案中找到損毀的行，但相同的程式可以逐一套用至一組檔案。

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

然後，您可以停止追蹤工作流程、刪除損壞的行並重新啟動工作流程。

### 我目前沒有損壞行的檔案

1. 使用以下命令列來入庫所有追蹤檔案。

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. 命令會列出所有損壞的行。 例如：

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在使用者代理程式之前新增歸位字元，以便閱讀效果更佳，且並未反映有效演算。

1. 執行grep指令以尋找對應的檔案。

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. 使用檔案名稱和行號尋找有問題的記錄。 例如：

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在使用者代理程式之前新增歸位字元，以便進行更佳的讀取，且不會反映有效的演算。

然後，您可以停止追蹤工作流程、刪除損壞的行並重新啟動工作流程。

## 追蹤連結間歇性失敗 {#tracking-links-fail-intermittently}

嘗試存取追蹤連結時，會顯示下列訊息：

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. 存取 &lt;redirection_server>/r/test URL並檢查要求是否傳回組建編號和localhost。

1. 檢查serverConf.xml檔案中用於追蹤伺服器的spareServer組態。 此設定應處於重新導向模式。

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. 手動檢查 &lt;deliveryid>.xml檔案存在於電腦中……/nl6/var/&lt;instance_name>/redir/url/&lt;yyyy> 目錄（YYYY代表傳遞年份）。

1. 手動檢查是否 &lt;trackingurlid> 您可在以下網址找到： &lt;deliveryid>.xml檔案。

1. 手動檢查相關deliveryID傳遞中是否存在broadlogID。

1. Check &lt;deliveryid>.xml檔案許可權，位於……/nl6/var/&lt;instance_name>/redir/url/year目錄。

   他們應具有至少644個許可權，這樣Apache就可以讀取追蹤URL以重新導向請求的連結。

## 是否要更新NmsTracking_Pointer選項？ {#updating-option}

更新NmsTracking_Pointer選項時，請遵循下列步驟：

1. 停止追蹤工作流程。

1. 停止trackinglogd服務。

1. 將NmsTracking_Pointer選項更新為所要的值。

1. 重新啟動trackinglogd服務。

1. 重新啟動追蹤工作流程。

## 追蹤似乎無法用於某些WebMail {#webmail}

您可以自訂點選追蹤公式，並指定自訂Adobe Analytics追蹤公式。

這類自訂需要謹慎進行，以避免新增額外的換行字元。 JavaScript運算式以外出現的所有換行字元都會出現在最終公式中。

追蹤URL中這類額外的換行字元會導致某些webMail （AOL、GMail等）發生問題。

**第一個範例：**

* 語法不正確

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* 正確語法

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

若要瞭解額外換行字元的位置，您可以使用固定字串STRING取代JavaScript運算式。

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**第二個範例**

* 語法不正確

   ```
   <%@ include option='NmsTracking_ClickFormula' %>
   <% // Parameters expected by Adobe Analytics
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* 正確語法

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

若要瞭解額外換行字元的位置，您可以使用固定字串STRING取代JavaScript運算式。

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## 追蹤記錄擷取速度太慢 {#slow-retrieval}

當執行個體未直接擷取追蹤記錄，而是從遠端Adobe Campaign Classic伺服器擷取記錄時，會透過remoteTracking結構描述中定義的GetTrackingLogs SOAP呼叫來擷取記錄。

serverConf.xml檔案中的選項可讓您設定透過以下方法一次擷取的記錄數： logCountPerRequest。

logCountPerRequest的預設值為1000，在某些情況下可能會證明太小。 接受的值必須介於0到10.000之間。

## 追蹤記錄檔無法連結至收件者 {#link-recipients}

在Adobe Campaign Classic中，就收件者結構描述與broadlog / trackinglog結構描述而言，目標對應應該是唯一的。

![](assets/tracking-troubleshooting.png)

無法將多個目標定位結構描述與相同的trackinglog結構描述搭配使用，因為追蹤工作流程將無法協調資料與目標ID。

如果您不想要搭配nms：recipient使用現成可用的目標對應，建議您採取下列方法：

* 如果您想要使用自訂目標維度，您需要使用nms：broadlog作為範本建立自訂broadLog/trackingLog結構描述（例如nms：broadLogRcp、nms：broadLogSvc等）。

* 如果您想要使用OOB trackingLogRcp/broadLogRcp，目標維度必須是nms：recipient，而篩選維度可以是自訂結構描述。
