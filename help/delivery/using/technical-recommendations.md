---
solution: Campaign Classic
product: campaign
title: 使用Adobe Campaign Classic改善傳遞能力的技術建議
description: 探索使用Adobe Campaign Classic提高傳遞率的技巧、設定和工具。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: tm+mt
source-wordcount: '2427'
ht-degree: 0%

---


# 技術建議{#technical-recommendations}

以下列出幾種可用來改善傳遞率的技術、組態和工具。

## 設定 {#configuration}

### 反向DNS {#reverse-dns}

Adobe Campaign會檢查是否提供反向DNS來識別IP位址，且這會正確指向IP。

網路配置中的一個重要點是確保為每個傳出消息的IP地址定義了正確的反向DNS。 這表示對於給定的IP地址，存在具有匹配DNS（A記錄）的反向DNS記錄（PTR記錄），該DNS（記錄）返回初始IP地址。

反向DNS的網域選擇在處理某些ISP時會產生影響。 特別是，AOL只接受與反向DNS位於相同域的地址的反饋環（請參見[反饋環](#feedback-loop)）。

有工具可用於驗證域的配置：[https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx)。

### MX規則{#mx-rules}

MX規則(Mail eXchanger)是管理傳送伺服器與接收伺服器間通訊的規則。

更精確地說，它們可用來控制Campaign MTA（訊息傳輸代理）傳送電子郵件至每個個別電子郵件網域或ISP（例如hotmail.com、comcast.net）的速度。 這些規則通常基於ISP發佈的限制（例如每個SMTP連接不包含超過20條消息）。

有關MX管理的更多資訊，請參閱[本節](../../installation/using/email-deliverability.md#mx-configuration)。

### TLS {#tls}

TLS（傳輸層安全性）是一種加密協定，可用於保護兩個電子郵件伺服器之間的連接，並保護電子郵件內容不受預定收件人以外的任何人讀取。

## 驗證{#authentication}

### SPF {#spf}

SPF（發件人策略框架）是一種電子郵件驗證標準，允許域的所有者指定允許代表該域發送電子郵件的電子郵件伺服器。 此標準使用電子郵件「回傳路徑」標題（也稱為「封套寄件者」位址）中的網域。

有工具可用於驗證SPF記錄：[https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

SPF是一種技術，在某種程度上，它使您能夠確保電子郵件中使用的域名不偽造。 當從域收到消息時，查詢域的DNS伺服器。 回應是簡短記錄（SPF記錄），詳細列出哪些伺服器有權從此網域傳送電子郵件。 如果我們假定只有域的所有者有更改此記錄的方法，我們可以認為此技術不允許偽造發送者地址，至少不允許偽造&quot;@&quot;右側的部分。

在最終的[RFC 4408規範](https://www.rfc-editor.org/info/rfc4408)中，消息的兩個元素用於確定被視為發送方的域：由SMTP &quot;HELO&quot;（或&quot;EHLO&quot;）命令指定的域和由&quot;Return-Path&quot;（或&quot;MAIL FROM&quot;）標題地址指定的域，也是彈回地址。 不同的考慮使得只考慮其中一個值成為可能；我們建議確保兩個來源都指定相同的網域。

檢查SPF可評估發件人域的有效性：

* **無**:無法評估，
* **中立**:查詢的域不啟用評估，
* **通過**:域被認為是真的，
* **失敗**:域是偽造的，消息應該被拒絕，
* **SoftFail**:域可能是偽造的，但消息不應僅基於此結果而拒絕，
* **TempError**:暫時錯誤會停止評估。消息可以被拒絕，
* **PermError**:域的SPF記錄無效。

值得注意的是，在DNS伺服器級別記錄可能需要48小時才能考慮在內。 此延遲取決於接收伺服器的DNS快取刷新頻率。

### DKIM {#dkim}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級至[增強型MTA](../../delivery/using/sending-with-enhanced-mta.md)，則DKIM電子郵件驗證簽署由增強型MTA針對所有網域的所有訊息完成。

DKIM(DomainKeys Indified Mail)驗證是SPF的繼承者，使用公開金鑰加密技術，允許接收電子郵件伺服器驗證消息實際上是由其聲稱發送的個人或實體發送的，以及消息內容是否在最初發送（和DKIM「簽名」）和接收時間之間發生了更改。 此標準通常使用「寄件者」或「寄件者」標題中的網域。 為確保DKIM的安全級別，建議使用1024b的最佳做法加密大小。 大部分的存取提供者不會將低DKIM金鑰視為有效。

DKIM來自DomainKeys、Yahoo! 和Cisco Identified Internet Mail身份驗證原則，用於檢查發件人域的真實性並保證消息的完整性。

DKIM已更換&#x200B;**DomainKeys**&#x200B;驗證。

使用DKIM需要一些必要條件：

* **安全性**:加密是DKIM的關鍵元素，並確保自2013年春季起1024b的DKIM安全級別是建議的最佳做法加密大小。大部分的存取提供者不會將低DKIM金鑰視為有效。
* **聲譽**:信譽是以IP和／或網域為基礎，但較不透明的DKIM選擇器也是需要考慮的關鍵元素。選擇選擇器很重要：避免保留任何人都能使用的「違約」，因此名聲非常微弱。 您必須為&#x200B;**保留與贏取通訊**&#x200B;實施不同的選擇器，以進行驗證。
* **Adobe Campaign選項聲明**:在Adobe促銷活動中，DKIM私密金鑰是以DKIM選擇器和網域為基礎。目前無法使用不同的選擇器為相同的網域／子網域建立多個私密金鑰。 無法定義平台或電子郵件中驗證必須使用哪個選擇器網域／子網域。 平台可選擇選擇其中一個私鑰，這表示驗證有很高的失敗機率。

>[!NOTE]
>
>* 如果您已為Adobe Campaign實例配置DomainKeys，則只需在[網域管理規則](../../delivery/using/understanding-delivery-failures.md#domain-management)中選擇&#x200B;**dkim**。 否則，請遵循與DomainKeys相同的配置步驟（私用／公用金鑰）。
>* DKIM是DomainKeys的改進版本，因此無需為相同的域同時啟用DomainKeys和DKIM。
>* 下列網域目前驗證DKIM:AOL,Gmail。


### DMARC {#dmarc}

DMARC（基於域的消息驗證、報告和符合性）是最新的電子郵件驗證形式，它依賴SPF和DKIM驗證來確定電子郵件是否通過或失敗。 DMARC在兩個非常重要的方面是獨特而強大的：

* 符合性——允許發送方指示ISP如何處理任何未通過驗證的消息（例如不接受）。
* 報告——它為發送者提供詳細報告，顯示所有未通過DMARC驗證的消息，以及每個消息所使用的「發件人」域和IP地址。 這可讓公司識別驗證失敗且需要某些類型「修正」（例如，在其SPF記錄中新增IP位址）的合法電子郵件，以及其電子郵件網域上網路釣魚企圖的來源和普遍性。

DMARC可運用由[250ok](https://250ok.com/)產生的報表。

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## 反饋環{#feedback-loop}

回饋迴路可在ISP層級為用於傳送訊息的IP位址範圍宣告指定電子郵件地址。 ISP會以類似方式將郵件發送到此郵箱，即接收者報告為垃圾郵件的郵件。 應將平台設定為封鎖將來傳送給已投訴的使用者。 即使他們未使用適當的退出連結，也必須不再與他們聯絡。 根據這些抱怨， ISP將在其密鑰中添加一個IP地址。 根據ISP的不同，投訴率約為1%將導致IP地址被阻塞。

目前正在制定一個標準，以定義反饋迴路消息的格式：[濫用反饋報告格式(ARF)](https://tools.ietf.org/html/rfc6650)。

實作例項的回饋回圈需要：

* 專用於實例的郵箱，可能是彈回郵箱
* 專用於實例的IP發送地址

在Adobe Campaign中實作簡單的回饋迴路會使用反彈訊息功能。 反饋循環郵箱用作彈回郵箱，並定義規則來檢測這些消息。 將郵件作為垃圾郵件報告的收件人的電子郵件地址添加到隔離清單中。

* 在&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;中建立或修改彈回郵件規則&#x200B;**Feedback_loop**，其原因為&#x200B;**Recommed**&#x200B;和類型&#x200B;**Hard**。
* 如果郵箱已專門為反饋循環定義，請通過在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中建立新的外部「彈回郵件」帳戶來定義要訪問該郵箱的參數。

該機制立即開始運作，以處理投訴通知。 為確保此規則正常運作，您可以暫時停用帳戶，以免帳戶收集這些訊息，然後手動檢查回饋回圈信箱的內容。 在伺服器上，執行以下命令：

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

如果您被迫針對多個例項使用單一回饋迴路位址，您必須：

* 複製在任意數量的郵箱上收到的消息，
* 讓每個郵箱都通過一個實例進行選擇，
* 設定例項，使其只處理與其相關的訊息：例項資訊會包含在Adobe Campaign所傳送訊息的訊息ID標題中，因此也位於回饋回圈訊息中。 只需在實例配置檔案中指定&#x200B;**checkInstanceName**&#x200B;參數即可（預設情況下，實例未驗證，這可能導致某些地址被錯誤隔離）:

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Adobe Campaign的Deliverability服務可管理您對下列ISP的回饋迴路服務訂閱：AOL、BlueTie、Comcast、Cox、EarthLink、FastMail、Gmail、Hotmail、HostedEmail、Libero、Mail.ru、MailTrust、OpenSRS、QQ、RoadRunner、Synacor、Telenor、Terra、UniteOnline、USEine、USA4、USA、USINE、USA、X、XALL, Yahoo, Yandex, Zoho。

## List-Unsubscribe {#list-unsubscribe}

### 關於List-Unsubscribe {#about-list-unsubscribe}

必須添加名為&#x200B;**List-Unsubscribe**&#x200B;的SMTP標頭，以確保最佳的傳遞能力管理。

此標題可用作「以垃圾訊息形式報告」圖示的替代項目。 它會在電子郵件介面中顯示為取消訂閱連結。

使用此功能有助於保護您的聲譽，而且會以取消訂閱的方式執行意見回應。

>[!NOTE]
>
>此功能可從Build 6831取得。

要使用「清單取消訂閱」，必須輸入如下所示的命令行：

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>上述範例以收件者表格為基礎。 如果從另一個表執行資料庫實施，請確保用正確的資訊重述命令行。

以下命令行可用於建立動態&#x200B;**List-Unsubscribe**:

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail、Outlook.com和Microsoft Outlook都支援此方法，而且其介面中會直接提供取消訂閱按鈕。 這種技巧降低投訴率。

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

您可以通過以下方式實施&#x200B;**List-Unsubscribe**:

* 直接在傳送範本中新增命令行——請參閱[本節](#adding-a-command-line-in-a-delivery-template),
* 或者，建立排版規則——請參閱[本節](#creating-a-typology-rule)。

### 在傳送範本{#adding-a-command-line-in-a-delivery-template}中新增命令列

命令行必須添加到電子郵件SMTP標題的附加部分中。

您可以在每封電子郵件或現有的傳送範本中新增。 您也可以建立包含此功能的新傳送範本。

### 建立類型規則 {#creating-a-typology-rule}

規則必須包含產生命令行的指令碼，而且必須包含在電子郵件標題中。

>[!NOTE]
>
>我們建議建立類型規則：清單取消訂閱功能會自動新增至每封電子郵件。

1. 清單取消訂閱：&lt;mailto:unsubscribe@domain.com>

   按一下&#x200B;**取消訂閱**&#x200B;連結，會開啟使用者的預設電子郵件用戶端。 此類型學規則必須新增至用於建立電子郵件的類型學中。

1. 清單取消訂閱：`<https://domain.com/unsubscribe.jsp>`

   按一下&#x200B;**unsubscribe**&#x200B;連結會將使用者重新導向至您的取消訂閱表單。

   範例:

   ![](assets/s_tn_del_unsubscribe_param.png)

## 電子郵件最佳化{#email-optimization}

### SMTP {#smtp}

SMTP（簡單郵件傳輸協定）是電子郵件傳輸的Internet標準。

規則未檢查的SMTP錯誤列在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]**&#x200B;資料夾中。 預設情況下，這些錯誤消息被解釋為無法訪問的軟錯誤。 如果要正確限定來自SMTP伺服器的反饋，必須識別最常見的錯誤，並在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]**&#x200B;中添加相應規則。 若未執行此項作業，平台將執行不必要的重試（未知使用者的情況），或在指定數量的測試後，將某些收件者錯誤地置於隔離中。

### 專用IP {#dedicated-ips}

Adobe為每位客戶提供專屬的IP策略，以提升IP，以建立聲譽並最佳化傳送效能。

## IP 認證 {#ip-certification}

IP認證是傳送最佳實務方案，可協助確保收到電子郵件時不會遭到反垃圾郵件篩選器或其他電子郵件封鎖系統的封鎖。

目前有兩家供應商提供IP認證：Return Path和認證寄件者聯盟。

認證寄件者會新增至全球郵箱供應商和電子郵件安全公司使用的電子郵件允許清單。 這些商業許可清單基於一個系統，該系統使發送者能夠完全繞過反垃圾郵件過濾器，或者在他們進入系統時被分配增量點。

[Return Path Certification](https://www.validity.com/products/returnpath/certification/)計畫提供多項優點，包括：

* 在頂級郵箱提供商（如Microsoft、AOL、Yahoo、Gmail、Comcast、Orange、Mail.ru等）的收件箱位置有顯著的增加
* 在Cloudmark、SpamAssassin和Cisco Ironport等關鍵過濾器上享有良好的聲譽和待遇
* 專門負責全天候監控的法規遵循團隊，提供安全警報，並與您合作解決任何折中問題
* 郵箱提供商資料提供有關KPI、位置和認證效能的詳細資訊
* 簡化和更快速的IP變暖，包括在移轉或取得新IP位址時更具信譽和辨識度

[認證寄件者聯盟](https://certified-senders.org/certification-process/)認證提供其他優點：

* 符合高品質標準的商業電子郵件寄件者認證
* 改善商業電子郵件的傳送和傳遞能力，以提高收件匣放置率並減少垃圾訊息篩選
* 全面遵守法律標準以防範法律及財務風險
* 通過來自CSA投訴辦公室的早期警告和每日垃圾郵件陷阱報告保護聲譽

ISP可免費使用這些服務，而ISP的數量可能因允許清單而異。

但是，由於越來越多的ISP會根據每個收件匣擁有者的行為建立反垃圾郵件過濾器，而不是分析郵件內容本身，因此使用IP認證無法保證收件匣的放置甚至傳送。
