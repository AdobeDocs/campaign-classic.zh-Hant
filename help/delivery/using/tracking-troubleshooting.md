---
product: campaign
title: 追蹤疑難排解
description: 本節提供與在Adobe Campaign Classic中追蹤設定和實作相關的常見問題。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 62e67a39-1e5c-4716-a3f3-b0ca69693cd0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 1%

---

# 追蹤疑難排解 {#tracking-troubleshooting}

![](../../assets/common.svg)

在本節中，您會在Adobe Campaign Classic中找到與追蹤設定和實作相關的常見問題。

## 追蹤工作流程失敗 {#tracking-workflow-failing}

我的追蹤工作流程失敗，如何偵測追蹤檔案中損毀的行？

>[!NOTE]
>
>僅適用於Windows

已損壞的跟蹤日誌檔案……/nl6/var/&lt;instance_name>/redir/log/0x0000記錄檔可停止追蹤工作流程。 若要輕鬆偵測損毀的線條並移除這些線條以繼續追蹤工作流程，您可以使用下列命令。

### 我知道哪個檔案里的損壞行

在這種情況下，在0x00000000000A0000.log檔案中可以找到損壞的行，但同一進程可以應用於一組檔案 — 逐個。

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

然後，您可以停止追蹤工作流程、刪除損毀的行並重新啟動工作流程。

### 我現在不知道檔案中的損壞行是

1. 使用下列命令列來簽入所有追蹤檔案。

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. 該命令列出所有損壞的行。 例如：

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在使用者代理之前新增回車功能，以便能更妥善讀取，且無法反映有效的轉譯。

1. 運行grep命令以查找相應的檔案。

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. 找到檔案名和行號有問題的日誌。 例如：

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在使用者代理之前新增回車符，以便更好地讀取，且無法反映有效的轉譯。

然後，您可以停止追蹤工作流程、刪除損毀的行並重新啟動工作流程。

## 追蹤連結間歇性失敗 {#tracking-links-fail-intermittently}

嘗試存取追蹤連結時，會顯示下列訊息：

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. 訪問&lt;redirection_server>/r/test URL，並檢查請求是否返回了生成號和localhost。

1. 檢查serverConf.xml檔案中的spareServer配置以查找跟蹤伺服器。 此配置應處於重定向模式。

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

1. 手動檢查&lt;deliveryID>.xml檔案是否存在於……中的電腦上/nl6/var/&lt;instance_name>/redir/url/&lt;YYYY>目錄（YYYY代表傳送年）。

1. 手動檢查在&lt;deliveryID>.xml檔案中是否可找到&lt;trackingUrlId>。

1. 在相關的deliveryID傳送中手動檢查broadlogID是否存在。

1. 檢查&lt;deliveryID>.xml檔案中的權限……/nl6/var/&lt;instance_name>/redir/url/year目錄。

   他們應至少擁有644個權限，讓Apache可以讀取追蹤url，以重新導向要求的連結。

## 是否更新NmsTracking_Pointer選項？ {#updating-option}

更新NmsTracking_Pointer選項時，請遵循下列步驟：

1. 停止追蹤工作流程。

1. 停止trackinglogd服務。

1. 將NmsTracking_Pointer選項更新為所需值。

1. 重新啟動trackinglogd服務。

1. 重新啟動追蹤工作流程。

## 某些WebMail似乎無法使用追蹤功能 {#webmail}

您可以自訂點擊追蹤公式，並指定自訂Adobe Analytics追蹤公式。

這種自訂需要謹慎進行，以避免增加額外的換行字元。 javascript運算式外部出現的所有換行字元都會出現在最終公式中。

追蹤URL中這類額外的換行字元會導致某些WebMail（AOL、GMail等）發生問題。

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

若要了解額外換行的位置，您可以以固定字串STRING取代javascript運算式。

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

若要了解額外換行的位置，您可以以固定字串STRING取代javascript運算式。

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## 追蹤記錄擷取速度太慢 {#slow-retrieval}

當例項不會直接擷取追蹤記錄，但從遠距Adobe Campaign Classic伺服器擷取記錄時，會透過GetTrackingLogs SOAP呼叫（在remoteTracking結構中定義）擷取記錄。

serverConf.xml檔案中的選項可讓您設定透過此方法一次擷取的記錄數：logCountPerRequest。

logCountPerRequest的預設值為1000，在某些情況下，它可能證明為太小。 接受的值必須介於0和10.000之間。

## 無法將跟蹤日誌連結到收件人 {#link-recipients}

在Adobe Campaign Classic中，就收件者結構描述與broadlog/trackinglog結構描述而言，目標對應應是唯一的。

![](assets/tracking-troubleshooting.png)

無法使用具有相同追蹤記錄結構的多個目標結構，因為追蹤工作流程將無法與目標ID調解資料。

如果您不想搭配nms:recipient使用現成可用的目標對應，我們建議使用下列方法：

* 如果您想使用自訂定位維度，則需要使用nms:broadlog作為範本來建立自訂broadLog/trackingLog架構（例如nms:broadLogRcp、nms:broadLogSvc等）。

* 如果您想使用OOB trackingLogRcp/broadLogRcp，目標維度必須是nms:recipient，篩選維度可以是自訂結構。
