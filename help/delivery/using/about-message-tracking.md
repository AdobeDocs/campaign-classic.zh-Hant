---
product: campaign
title: 開始使用追蹤
description: 深入瞭解Adobe Campaign追蹤的一般准則
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 2%

---

# 開始使用訊息追蹤 {#get-started-tracking}

>[!IMPORTANT]
>
>如需同時適用於Campaign Classic v7和Campaign v8的&#x200B;**一般追蹤指引**，請參閱[Campaign v8訊息追蹤檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}：
>
>* [設定追蹤的連結](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [設定 URL 追蹤選項](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [追蹤個人化連結](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [存取追蹤記錄](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [測試追蹤](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [追蹤報告](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**此頁面僅記錄Campaign Classic v7的特定追蹤功能**，主要用於混合部署和內部部署。

## 追蹤功能

### 追蹤設定 {#configure-tracking}

對於Campaign Classic v7 **混合/內部部署**，您必須在使用前於執行個體層級設定追蹤。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services，追蹤設定是由Adobe執行。

**操作原則**

在使用追蹤之前，您必須先為例項設定追蹤。 需要在Adobe Campaign應用程式伺服器和網頁伺服器上執行設定。

在Campaign中，有兩種型別的追蹤：

* **網頁追蹤**：此模式可讓您追蹤網站頁面的造訪
* **訊息追蹤**：此模式可讓您追蹤訊息傳遞和收件者行為

在安裝期間選擇追蹤模式。 對於內部部署安裝，必須在執行個體層級定義追蹤設定。 [了解更多](../../installation/using/deploying-an-instance.md#operating-principle)

**追蹤伺服器**

若要設定追蹤，您必須向追蹤伺服器宣告並註冊執行個體。 追蹤伺服器可用來記錄和擷取收件者所點按URL的相關資訊。

對於內部部署安裝，追蹤伺服器通常是執行Adobe Campaign Web應用程式的網頁伺服器。 追蹤伺服器URL必須在您的執行個體設定中定義。 [了解更多](../../installation/using/deploying-an-instance.md#tracking-server)

**正在儲存追蹤**

設定追蹤並填入您的URL後，必須註冊追蹤伺服器。 註冊可讓Adobe Campaign儲存追蹤資訊，並提供追蹤活動的報表和統計資料。

對於內部部署，追蹤資訊會儲存在資料庫中，並透過技術工作流程擷取。 **追蹤**&#x200B;技術工作流程會處理並儲存從重新導向伺服器收集的追蹤資料。 [了解更多](../../installation/using/deploying-an-instance.md#saving-tracking)

### 網站應用程式追蹤 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**Web應用程式追蹤是Campaign Classic v7**&#x200B;專屬的並在Campaign v8中無法使用。

**追蹤 Web 應用程式**

您也可以追蹤和測量具有追蹤標籤的網頁應用程式頁面上的造訪次數。 此功能可用於所有Web應用程式型別，例如表單和登入頁面。 [了解更多](../../web/using/tracking-a-web-application.md)

**網站應用程式追蹤選擇退出**

網站應用程式追蹤選擇退出可讓您停止追蹤選擇退出行為追蹤之一般使用者的網站行為。 您可以在網頁應用程式或登入頁面中加入顯示橫幅的功能，讓使用者選擇退出。 [了解更多](../../web/using/web-application-tracking-opt-out.md)

## 追蹤疑難排解 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

下列疑難排解提示適用於&#x200B;**Campaign Classic v7混合/內部部署**。 部分資訊可能也會套用至Campaign v8內部部署。 如需Campaign v8受管理的Cloud Services，請聯絡您的Adobe代表以尋求協助。

如需Campaign v8的基本追蹤疑難排解步驟，請參閱Campaign v8檔案[中的](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}疑難排解追蹤。

### 基本檢查 {#basic-checks}

**檢查trackinglogd處理序是否正在執行**

此程式會從IIS/Web伺服器共用記憶體讀取並寫入重新導向記錄。

您可以選取執行個體中的「監視」標籤，從首頁存取它。 您也可以在執行個體上執行下列命令： `<user>@<instance>:~$ nlserver pdump`

如果trackinglogd處理序未出現在清單中，請在執行個體上使用下列命令啟動它： `<user>@<instance>:~$ nlserver start trackinglogd`

**檢查追蹤技術工作流程最近是否執行中**

您可以在資料夾管理>生產>技術工作流程中找到追蹤技術工作流程。

### 進階疑難排解 {#advanced-troubleshooting}

+++追蹤工作流程失敗

>[!NOTE]
>
>僅適用於Windows

損毀的追蹤記錄檔……/nl6/var/&lt;instance_name>/redir/log/0x0000記錄檔可以停止追蹤工作流程。 若要輕鬆偵測損壞的行並移除它們以繼續執行追蹤工作流程，您可以使用以下命令。

**我知道損壞的行**&#x200B;在哪個檔案中

在這種情況下，可以在0x00000000000A0000.log檔案中找到損毀的行，但相同的程式可以逐一套用至一組檔案。

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

然後，您可以停止追蹤工作流程、刪除損壞的行並重新啟動工作流程。

**我不知道損毀的資料行是哪個檔案**

1. 使用以下命令列來入庫所有追蹤檔案。

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. 指令會列出所有損壞的行。 例如：

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在使用者代理程式之前新增歸位字元，以便讓閱讀效果更好，而且不會反映有效的演算。

1. 執行grep指令以尋找對應的檔案。

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. 使用檔案名稱和行號尋找錯誤的記錄。 例如：

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >已在使用者代理程式之前新增歸位字元，以允許更佳的讀取且不會反映有效的演算。

然後，您可以停止追蹤工作流程、刪除損壞的行並重新啟動工作流程。

+++

+++追蹤連結間歇性失敗

嘗試存取追蹤連結時，會顯示下列訊息：

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. 存取&lt;redirection_server>/r/test URL並檢查要求是否傳回組建號碼和localhost。

1. 檢查serverConf.xml檔案中追蹤伺服器的spareServer組態。 此設定應該在重新導向模式。

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

1. 手動檢查電腦上的……/nl6/var/&lt;instance_name>/redir/url/&lt;YYYY>目錄中是否存在&lt;deliveryID>.xml檔案（YYYY代表傳遞年份）。

1. 手動檢查是否可以在&lt;deliveryID>.xml檔案中找到&lt;trackingUrlId>。

1. 手動檢查相關deliveryID傳遞中是否存在broadlogID。

1. 檢查……/nl6/var/&lt;instance_name>/redir/url/year目錄中的&lt;deliveryID>.xml檔案許可權。

   他們應該至少有644個許可權，這樣Apache才能讀取追蹤URL，以重新導向請求的連結。

+++

+++更新NmsTracking_Pointer選項

更新NmsTracking_Pointer選項時，請遵循下列步驟：

1. 停止追蹤工作流程。

1. 停止trackinglogd服務。

1. 將NmsTracking_Pointer選項更新為所要的值。

1. 重新啟動trackinglogd服務。

1. 重新啟動追蹤工作流程。

+++

+++某些WebMail無法進行追蹤

您可以自訂點選追蹤公式，並指定自訂Adobe Analytics追蹤公式。

這類自訂需要謹慎進行，以免新增額外的換行字元。 JavaScript運算式外部出現的所有換行字元都會出現在最終公式中。

追蹤URL中這類額外的換行字元，在某些webMail （AOL、GMail等）中會導致問題。

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

+++

+++追蹤記錄擷取太慢

當執行個體未直接擷取追蹤記錄，而是從遠距的Adobe Campaign Classic伺服器擷取記錄時，會透過GetTrackingLogs SOAP呼叫（在remoteTracking結構描述中定義）來擷取記錄。

serverConf.xml檔案中的選項可讓您設定透過以下方法一次擷取的記錄數： logCountPerRequest。

logCountPerRequest的預設值為1000，在某些情況下可能會證明太小。 接受的值必須介於0到10.000之間。

+++

+++追蹤記錄檔無法連結至收件者

在Adobe Campaign Classic中，就收件者綱要與broadlog / trackinglog綱要而言，目標對應應該是唯一的。

![](assets/tracking-troubleshooting.png)

無法將多個目標定位結構描述與相同的trackinglog結構描述搭配使用，因為追蹤工作流程將無法協調資料與目標ID。

如果您不想要搭配nms:recipient使用現成的目標對應，我們建議採取下列方法：

* 如果您想要使用自訂目標維度，則需要使用nms:broadlog作為範本（例如nms:broadLogRcp、nms:broadLogSvc等）建立自訂broadLog/trackingLog結構描述。

* 若要使用OOB trackingLogRcp/broadLogRcp，目標維度必須是nms:recipient，而篩選維度可以是自訂結構描述。

+++
