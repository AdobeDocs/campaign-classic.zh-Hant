---
solution: Campaign Classic
product: campaign
title: 追蹤疑難排解
description: 本節提供與Adobe Campaign Classic中追蹤設定和實作相關的常見問題。
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: efa36dc08ce4dd59805bb9eba63a4249e14609d7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# 追蹤疑難排解{#tracking-troubleshooting}

在本節中，您會在Adobe Campaign Classic中找到與追蹤設定和實施相關的常見問題。

## 追蹤工作流程失敗{#tracking-workflow-failing}

我的追蹤工作流程失敗，我要如何偵測追蹤檔案中的損毀行？

>[!NOTE]
>
>僅適用於Windows

已損毀的追蹤記錄檔……/nl6/var/&lt;instance_name>/redir/log/0x0000記錄檔可以停止追蹤工作流程。 若要輕鬆偵測損毀的線條並移除它們以繼續追蹤工作流程，您可使用下列命令。

### 我知道哪個檔案中的損壞行

在這種情況下，在0x00000000000A0000.log檔案中可以找到損壞的行，但同一過程可以應用於一組檔案——逐個。

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

然後，您可以停止追蹤工作流程、刪除損毀的行並重新啟動工作流程。

### 我現在不知道檔案中的損壞行是

1. 使用以下命令行簽入所有跟蹤檔案。

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
   >已在使用者代理之前新增歸位功能，以提供更佳的閱讀效果，且無法反映有效的轉譯效果。

1. 運行grep命令以查找相應的檔案。

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. 使用檔案名和行號查找錯誤日誌。 例如：

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在使用者代理之前新增回車符，以便提供更佳的閱讀效果，且無法反映有效的轉換效果。

然後，您可以停止追蹤工作流程、刪除損毀的行並重新啟動工作流程。

## 追蹤連結間歇性{#tracking-links-fail-intermittently}失敗

嘗試存取追蹤連結時，會顯示下列訊息：

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. 存取&lt;redirection_server>/r/test URL，並檢查請求是否傳回了組建編號和localhost。

1. 在serverConf.xml檔案中檢查spareServer配置以查找跟蹤伺服器。 此配置應處於重定向模式。

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

1. 手動檢查&lt;deliveryID>.xml檔案是否存在於……中的機器上/nl6/var/&lt;instance_name>/redir/url/&lt;YYYY>目錄（YYYY代表傳送年份）。

1. 手動檢查&lt;trackingUrlId>是否可在&lt;deliveryID>.xml檔案中找到。

1. 在相關的deliveryID傳送中手動檢查broadlogID是否存在。

1. 檢查……中的&lt;deliveryID>.xml檔案權限/nl6/var/&lt;instance_name>/redir/url/year目錄。

   他們應至少擁有644個權限，如此Apache才能讀取追蹤URL以重新導向請求的連結。

## 是否更新NmsTracking_Pointer選項？{#updating-option}

更新NmsTracking_Pointer選項時，請遵循下列步驟：

1. 停止追蹤工作流程。

1. 停止trackinglogd服務。

1. 將NmsTracking_Pointer選項更新為所需值。

1. 重新啟動trackinglogd服務。

1. 重新啟動追蹤工作流程。

## 某些WebMail {#webmail}似乎無法使用追蹤

您可以自訂點按追蹤公式，並指定自訂Adobe Analytics追蹤公式。

這種自訂作業必須謹慎進行，以避免新增額外的換行字元。 Javascript運算式以外的所有換行字元都會出現在最終公式中。

追蹤URL中的這種額外換行字元會導致某些webMail（AOL、GMail等）的問題。

**第一個範例：**

* 語法不正確

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* 正確語法

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

若要瞭解額外換行的位置，您可以使用固定字串STRING來取代javascript運算式。

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
   <% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* 正確語法

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

若要瞭解額外換行的位置，您可以使用固定字串STRING來取代javascript運算式。

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## 追蹤記錄擷取速度太慢{#slow-retrieval}

當例項未直接擷取追蹤記錄，但是從遠端的Adobe Campaign Classic伺服器擷取記錄時，會透過GetTrackingLogs SOAP呼叫來擷取記錄，此呼叫在remoteTracking架構中定義。

serverConf.xml檔案中的一個選項允許您設定通過以下方法一次檢索的日誌數：logCountPerRequest。

logCountPerRequest的預設值為1000，在某些情況下可能證明為過小。 接受的值必須介於0和10.000之間。

## 追蹤記錄無法連結至收件者{#link-recipients}

在Adobe Campaign Classic中，目標對應在收件者結構描述與broadlog /trackinglog結構描述方面應是唯一的。

![](assets/tracking-troubleshooting.png)

無法使用具有相同追蹤記錄結構的多個定位結構，因為追蹤工作流程無法使用定位ID來協調資料。

如果您不想與nms:recipient一起使用現成可用的目標映射，我們建議使用下列方法：

* 如果要使用自訂定位維，您需要使用nms:broadlog作為模板（例如nms:broadLogRcp、nms:broadLogSvc等）建立自訂broadLog/trackingLog模式。

* 如果您想要使用OOB trackingLogRcp/broadLogRcp，定位維度必須是nms:recipient，篩選維度可以是自訂架構。
