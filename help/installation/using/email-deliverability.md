---
solution: Campaign Classic
product: campaign
title: 電子郵件傳遞能力
description: 電子郵件傳遞能力
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2973'
ht-degree: 0%

---


# 技術電子郵件設定{#email-deliverability}

## 概觀 {#overview}

下節概述傳送電子郵件時控制Adobe Campaign例項輸出所需的設定。

>[!NOTE]
>
>有些組態只能由Adobe針對Adobe代管的部署執行，例如存取伺服器和執行個體組態檔。 若要進一步瞭解不同的部署，請參閱「代 [管模型](../../installation/using/hosting-models.md) 」一節或 [本頁](../../installation/using/capability-matrix.md)。

有關交付能力相關概念和最佳做法的詳細資訊，請參閱本 [節](../../delivery/using/about-deliverability.md)。

本節提供所有有關Adobe Campaign平台有效傳送及接收電子郵件的技術建 [議](../../delivery/using/technical-recommendations.md)。

## 操作原則 {#operating-principle}

您可以控制一或多個Adobe Campaign例項的輸出，以限制依網域而傳送的電子郵件數。 例如，您可將 **** yahoo.com位址的輸出限制為每小時20,000條，同時為所有其他網域設定每小時100,000條訊息。

必須針對傳送伺服器(**mta**)使用的每個IP位址控制訊息輸出。 數 **部分** （依數部電腦劃分，屬於各種Adobe Campaign例項）可共用相同的IP位址以傳送電子郵件：需要設定一個進程來協調這些IP地址的使用。

這是stat模 **塊的功** 能：它將所有要發送到郵件伺服器的連接請求和消息轉發到一組IP地址。 統計伺服器會追蹤傳送，並可根據設定的配額啟用或停用傳送。

![](assets/s_ncs_install_mta.png)

* 統計伺服器(**stat**)會連結至Adobe Campaign基礎，以載入其設定。
* 傳送伺服器(**mta**)使用UDP來連絡不一定屬於其本身實例的統計伺服器。

### 傳送伺服器 {#delivery-servers}

mta **模組** 將消息分發到其 **匹配子模** 塊。 每個 **模板** 在向統計伺服器請求授權併發送消息之前準備消息。

步驟如下：

1. mta會 **選擇符合條件的訊息** ，並為其指派可用的 **對應欄位**。
1. 此模 **塊會載入** 建立訊息（內容、個人化元素、附件、影像等）所需的所有資訊 並將訊息轉送至「電子郵 **件流量Shaper」**。
1. 當電子郵件流量整形器收到統計伺服器的授權(**smtp stat**)時，就會將消息發送給收件人。

![](assets/s_ncs_install_email_traffic_shaper.png)

### 電子郵件伺服器統計資料和限制 {#email-server-statistics-and-limitations}

統計伺服器會為接收消息的每個電子郵件伺服器維護以下統計資訊：

* 開啟的時間點連接數，
* 在最後一小時內發送的消息數，
* 成功／拒絕連接的速率，
* 到無法訪問伺服器的連接速率。

同時，模組會載入特定電子郵件伺服器的限制清單：

* 同時連接的最大數量，
* 每小時的最大消息數，
* 每個連接的最大消息數。

### 管理IP位址 {#managing-ip-addresses}

統計伺服器可以將多個實例或多個電腦與相同的公共IP地址組合在一起。 因此，它不會連結至特定的例項，但是它必須連絡例項才能復原每個網域的限制。

會針對每個目標MX和每個來源IP保留傳送統計資料。 例如，如果目標網域有5個MX，而平台可使用3個不同的IP位址，則伺服器可管理此網域多達15個系列的指示器。

源IP地址與公共IP地址匹配，即遠程電子郵件伺服器所看到的地址。 如果提供NAT路由器，則此IP地址可能與托管 **mta**&#x200B;的電腦的地址不同。 這就是為什麼統計伺服器使用與公共IP(**publicId**)匹配的標識符。 本地地址與此標識符之間的關聯在 **serverConf.xml配置檔案中聲明** 。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

## 傳送輸出控制 {#delivery-output-controlling}

若要傳送訊息給電子郵件伺服器， **** Email Traffic Shaper元件會要求從統計伺服器連線。 接受請求後，連線即會開啟。

在傳送訊息之前，模組會從伺服器要求「Token」。 這些代號通常至少是10個代號集，可減少伺服器的查詢數。

伺服器會儲存與連線和傳送相關的所有統計資料。 如果重新啟動，資訊會暫時丟失：每個客戶端保存其發送統計資訊的本地副本，並定期（每2分鐘）將其返回到伺服器。 然後，伺服器可以重新聚合資料。

以下各節將說明「電子郵件流量Shaper」元件 **對訊息的處理** 。

### 訊息傳送 {#message-delivery}

傳送訊息時，可能會有3個結果：

1. **成功**:訊息已成功傳送。 訊息會更新。
1. **消息失敗**:已聯繫的伺服器拒絕所選收件人的消息。 此結果與返回代碼550到599匹配，但可以定義例外。
1. **會話失敗** （向上5.11）:如果 **mta** 收到此訊息的回覆，訊息會被放棄(請參閱 [訊息放棄](#message-abandonment))。 訊息會傳送至其他路徑，或設為待定（如果沒有其他路徑可用）(請參 [閱「待定訊息](#message-pending)」)。

   >[!NOTE]
   >
   >路 **徑** 是Adobe Campaign mta和目標mta之間的連 **接******。 Adobe Campaign **mta** 可以從數個開始IP和數個目標網域IP中選擇。

### 訊息放棄 {#message-abandonment}

放棄的訊息會傳回 **至mta** ，而不再由mtachild **管理**。

mta **決定** 此訊息的程式（復原、放棄、隔離等） 視回應程式碼和規則而定。

### 留言擱置中 {#message-pending}

當訊息進入作用中佇列且沒有可用路徑時，就會暫停該訊息。

在連線錯誤後，路徑通常會標示為不可用的變數時間量。 不可用期取決於錯誤的頻率和年齡。

## 統計伺服器配置 {#statistics-server-configuration}

統計伺服器可由多個實例使用：它必須獨立於使用它的實例進行配置。

首先，定義將代管設定的Adobe Campaign資料庫。

### 啟動配置 {#start-configuration}

預設情況下， **每個實例** 都會啟動stat模組。 當實例在同一台電腦上共用時，或當實例共用相同的IP地址時，將使用單個統計伺服器：其他人必須被禁用。

### 伺服器埠的定義 {#definition-of-the-server-port}

預設情況下，統計伺服器監聽埠7777。 此埠可在serverConf.xml **檔案中修改** 。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

```
<stat port="1234"/>
```

## MX設定 {#mx-configuration}

### 關於MX規則 {#about-mx-rules}

MX規則(Mail eXchanger)是管理傳送伺服器與接收伺服器間通訊的規則。

>[!IMPORTANT]
>
>對於代管或混合安裝，如果您已升級至「增強MTA」，則不 **[!UICONTROL MX management]** 再使用傳送總處理能力規則。 增強型MTA使用其專屬的MX規則，可讓您根據您過去的電子郵件信譽，以及您傳送電子郵件的網域所提供的即時回應，依網域自訂您的吞吐量。
>
>如需Adobe Campaign增強型MTA的詳細資訊，請參閱本文 [件](https://helpx.adobe.com/tw/campaign/kb/acc-campaign-enhanced-mta.html)。

這些規則會在每天早上6點（伺服器時間）自動重新載入，以定期提供用戶端例項。

ISP將接受每小時預先定義的連接和消息數，具體取決於物料容量和內部策略。 ISP系統可以根據IP和發送域的信譽自動修改這些變數。 Adobe Campaign透過其傳遞能力平台，管理ISP超過150項特定規則，此外還管理其他網域的一項一般規則。

連接的最大數量不完全取決於MTA使用的公有IP地址數。

例如，如果您在MX規則中允許5個連線，而您已設定2個公用IP，則您可能認為無法同時開啟超過10個連線至此網域。 這不是事實，事實上，最大連線數指的是路徑和路徑，其中一個是我們的MTA公用IP，另一個是客戶MTA的公用IP。

在下列範例中，使用者已設定兩個公用IP位址，網域為yahoo.com。

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

yahoo.com的MX記錄告訴我們yahoo.com有3個Mail Sencer。 要連接對等郵件交換器，MTA將向DNS請求其IP地址。

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

對於此記錄，用戶可以聯繫8個對等IP地址。 由於他有2個公用IP位址，因此他有8 * 2 = 16個組合，可連至yahoo.com郵件伺服器。 這些組合中的每個都稱為路徑。

第二個MX記錄顯示為：

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

其中8個IP位址已用於mta5（98.136.216.26、98.138.112.38、63.250.192.46和98.136.217.203）。 此記錄可讓使用者使用4個新IP位址。 第三個MX記錄也會做同樣的事。

總共有16個遠端IP位址。 與我們的2個本機公共IP搭配使用，我們有32個路徑可連至yahoo.com郵件伺服器。

>[!NOTE]
>
>如果2個MX記錄參照相同的IP位址，則此記錄會計為一條路徑，而非兩條路徑。

以下是使用MX規則的一些範例：

![](assets/s_ncs_examples_mx_rules.png)

在以下範例中，使用者在特定網域的每小時限制為10,000則訊息，但MTA總處理能力高於此限制。

在此情況下，流量會分為12個時段，每小時5分鐘，而實際限制是每個時段833則訊息。

這些訊息會盡快傳遞。

![](assets/s_ncs_traffic_shaping.png)

### 設定MX管理 {#configuring-mx-management}

MX要遵循的規則在樹節點的 **[!UICONTROL MX management]** 文檔中 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 定義。

如果 **[!UICONTROL MX management]** 文檔中節點中不存在，則可以手動建立文檔。 操作步驟：

1. 建立新的郵件規則集。
1. Choose the **[!UICONTROL MX management]** mode.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. 在字 **段中輸入defaultMXRules****[!UICONTROL Internal name]** 。

為了考慮更改，您需要重新啟動統計伺服器。

要重新載入配置而不重新啟動統計伺服器，請在托管伺服器的電腦上使用以下命令： `nlserver stat -reload`

>[!NOTE]
>
>此命令行優先於 **nlserver restart**。 它可防止在重新啟動丟失之前收集到的統計資訊，並避免使用中的峰值，這些峰值可能會與MX規則中定義的配額相違背。

### 設定MX規則 {#configuring-mx-rules}

文 **[!UICONTROL MX management]** 件會列出連結至MX規則的所有網域。

這些規則依序套用：套用其MX遮色片與目標MX相容的第一個規則。

每個規則可用的參數如下：

* **[!UICONTROL MX mask]**:套用規則的網域。 每個規則都會定義MX的位址遮色片。 因此，任何名稱符合此遮色片名稱的MX都符合資格。 遮色片可包含&quot;*&quot;和&quot;?&quot; 一般字元。

   例如，以下地址：

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   與下列遮色片相容：

   * *.yahoo.com
   * ?.mx.yahoo.com

   例如，若是電子郵件位址foobar@gmail.com，網域為gmail.com,MX記錄為：

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   在這種情況下，將 `*.google.com` 使用MX規則。 如您所見，MX規則遮色片不一定符合郵件中的網域。 適用於gmail.com電子郵件位址的MX規則將是具有遮色片的規則 `*.google.com`。

* **[!UICONTROL Range of identifiers]**:此選項可讓您指出套用規則的識別碼範圍(publicID)。 您可以指定：

   * 數字：該規則只適用於此publicId,
   * 數字範圍(**number1-number2**):該規則將適用於這兩個數字之間的所有publicId。

   >[!NOTE]
   >
   >如果欄位為空白，規則會套用至所有識別碼。

   公用ID是一或多個MTA所使用之公用IP的內部識別碼。 這些ID是在 **config-instance.xml檔案的MTA伺服器中定義** 。

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**:定義此MX規則的屬性範圍。 勾選後，所有參數都會共用至實例上所有可用的IP。 若未勾選，則會針對每個IP定義MX規則。 最大消息數乘以可用IP數。
* **[!UICONTROL Maximum number of connections]**:與發送者網域同時連線的最大數目。
* **[!UICONTROL Maximum number of messages]**:可在連接上發送的最大消息數。 當訊息超過此數目時，連線即關閉，並開啟新連線。
* **[!UICONTROL Messages per hour]**:在一小時內可以發送到發件人域的消息數上限。
* **[!UICONTROL Connection time out]**:連接到域的時間閾值。

   >[!NOTE]
   >
   >Windows可在此臨 **界值** （視您的Windows版本而定）之前發出逾時。

* **[!UICONTROL Timeout Data]**:發送消息內容（SMTP協定的DATA部分）後的最大等待時間。
* **[!UICONTROL Timeout]**:與SMTP伺服器進行其他交換的最長等待時間。
* **[!UICONTROL TLS]**:TLS通訊協定可讓您加密電子郵件傳送，可選擇性啟用。 對於每個MX遮色片，都提供下列選項：

   * **[!UICONTROL Default configuration]**:這是在應用的serverConf.xml配置檔案中指定的常規配置。

      >[!IMPORTANT]
      >
      >不建議修改預設配置。

   * **[!UICONTROL Disabled]** :系統地發送這些消息而不加密。
   * **[!UICONTROL Opportunistic]** :如果接收伺服器(SMTP)可以生成TLS協定，則消息傳送將被加密。

配置示例：

![](assets/s_ncs_install_mx_mgt_rule_details.png)

### 管理電子郵件格式 {#managing-email-formats}

您可以定義已傳送訊息的格式，讓顯示的內容會根據每個收件者位址的網域自動調整。

若要這麼做，請前往位 **[!UICONTROL Management of email formats]** 於「 > > > >」中的 **[!UICONTROL Administration]****[!UICONTROL Campaign management]** 檔案 **[!UICONTROL Non deliverables management]** 中 **[!UICONTROL Mail rule sets]**。

本檔案包含所有預先定義網域的清單，這些網域對應Adobe Campaign管理的日文格式。 For more information, refer to [this document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

MIME結 **構** （多用途Internet郵件擴展）參數允許您定義要發送到不同郵件客戶端的郵件結構。 有三種可用選項：

* **多部分**:訊息會以文字或HTML格式傳送。 如果不接受HTML格式，訊息仍可以以文字格式顯示。

   依預設，多部分結構是多 **部分／替代**，但當將影像新增至訊息時，它會自 **動變成多部分／相關** 。 某些提供者預 **期會採用多部分／相關** ，即使未附加影像， **[!UICONTROL Force multipart/related]** 選項也會採用此格式。

* **HTML**:僅傳送HTML訊息。 如果不接受HTML格式，則不會顯示訊息。
* **文字**:系統會傳送僅文字格式的訊息。 文本格式消息的優點是其大小非常小。

如果啟 **[!UICONTROL Image inclusion]** 用此選項，這些選項會直接顯示在電子郵件的正文中。 然後，影像就會上傳，而URL連結會被其內容取代。

此選項在日本市場中尤其 **用於Deco-mail**、 **Decore Mail** 或 **Decoring Mail**。 如需詳細資訊，請參 [閱本檔案](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)。

>[!IMPORTANT]
>
>在電子郵件中插入影像會大幅增加其大小。

## 傳送伺服器組態 {#delivery-server-configuration}

### 時鐘同步 {#clock-synchronization}

組成Adobe Campaign平台（包括資料庫）的所有伺服器的時鐘必須同步，且其系統必須設定為相同時區。

### 統計伺服器的坐標 {#coordinates-of-the-statistics-server}

必須在mta中提供統計伺服器的地 **址**。

配 **置的****** mta元素的statServerAddress屬性可讓您指定要使用的埠的地址和編號。

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

要在同一台電腦上使用統計伺服器，您至少必須輸入具有localhost值的 **電腦名** :

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>如果未填入此欄位， **mta** 將不會啟動。

### 要使用的IP位址清單 {#list-of-ip-addresses-to-use}

有關流量管理的配置位於配 **置檔案的mta/child/smtp** 元素中。

對於每 **個IPAffinity** 元素，您需要聲明可用於該電腦的IP地址。

範例:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

參數如下：

* **地址**:這是要使用的MTA主機的IP地址。
* **helo主機**:此標識符表示SMTP伺服器將看到的IP地址。

* **publicId**:當NAT路由器後的數個Adobe Campaign mtas共用IP位址時，這項資 **訊很有** 用。 統計伺服器使用此標識符來儲存此起始點和目標伺服器之間的連接和發送統計資訊。
* **重量**:可讓您定義地址的使用相對頻率。 預設情況下，所有地址的權重均為1。

>[!NOTE]
>
>在serverConf.xml檔案中，您需要驗證一個IP是否對應於具有唯一識別碼(public_id)的單一主機。 它無法映射到多個主機，這可能導致傳送調節問題。

在上例中，在正常情況下，地址將按如下方式分配：

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

例如，如果第一個位址無法用於指定的MX，則會傳送如下訊息：

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**:可讓您為屬於特定網域的電子郵件保留此IP位址。 這是遮色片的清單，可包含一或多個萬用字元(&#39;*&#39;)。 如果未指定屬性，所有網域都可以使用此IP位址。

   範例： **includeDomains=&quot;wanadoo.com,orange.com,yahoo.*&quot;**

* **excludeDomains**:排除此IP位址的網域清單。 此篩選會套用在includeDomains篩 **選器之後** 。

   ![](assets/s_ncs_install_mta_ips.png)

## 電子郵件傳送最佳化 {#email-sending-optimization}

Adobe Campaign行銷活動的內部架 **構** ，會對最佳化電子郵件傳送的設定產生影響。 以下是改善遞送的一些秘訣。

### 調整maxWaitingMessages參數 {#adjust-the-maxwaitingmessages-parameter}

maxWaitingMessages **參數** ，表示matchild預先準備的最大 **訊息數**。 消息只有在發送或放棄後才會從此清單中刪除。

如果消息未按域排序，則此參數非常重要，尤其重要。

達到 **maxWorkingSetMb** (256)臨界值後，傳送伺服器就會停止傳送訊息。 效能會大幅降低，直到 **再次啟動** 匹配欄位。 要避免此問題，您可以增加 **maxWorkingSetMb** 參數的臨界值，或降低 **maxWaitingMessages參數的臨界值** 。

maxWorkingSetMb **** 參數是以經驗方式計算的，方法是將最大消息數乘以平均消息大小，再乘以2.5。例如，如果訊息的平均大小為50 kB，而 **maxWaitingMessages** 參數等於1,000，則使用的記憶體平均大小為125 MB。

### 調整像片數 {#adjust-the-number-of-mtachild}

子代數不應超過電腦中的處理器數(約 1000次課程)。 我們建議您不要超過8個 **欄位**。 然後，您可以增加每個子代的 **訊息數** (**maxMsgPerChild**)，以達到足夠的生命週期。
