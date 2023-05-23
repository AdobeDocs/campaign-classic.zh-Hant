---
product: campaign
title: 技術電子郵件配置
description: 瞭解如何配置市場活動以在發送電子郵件時控制實例的輸出
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '3023'
ht-degree: 0%

---

# 技術電子郵件設定{#email-deliverability}



## 概覽 {#overview}

以下部分概述了在發送電子郵件時控制Adobe Campaign實例輸出所需的配置。

>[!NOTE]
>
>某些配置只能通過Adobe執行由Adobe承載的部署，例如，訪問伺服器和實例配置檔案。 要瞭解有關不同部署的詳細資訊，請參閱 [托管模型](../../installation/using/hosting-models.md) 或 [此頁](../../installation/using/capability-matrix.md)。

有關與Adobe Campaign提供服務相關的概念和最佳做法的詳細資訊，請參閱此 [節](../../delivery/using/about-deliverability.md)。

有關可交付性的更深入瞭解，包括有關Adobe平台高效發送和接收電子郵件的所有技術建議，請參閱 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。

## 操作原則 {#operating-principle}

可以控制一個或多個Adobe Campaign實例的輸出以限制根據域發送的電子郵件數。 例如，您可以將輸出限制為每小時20,000 **雅虎.com** 地址，同時為所有其他域配置每小時100,000條消息。

需要針對傳遞伺服器使用的每個IP地址控制消息輸出(**門**)。 幾個 **門** 在多台電腦上分解並屬於各種Adobe Campaign實例可以共用相同的IP地址以用於電子郵件傳遞：需要設定一個進程來協調這些IP地址的使用。

這就是 **統計** 模組執行：它轉發所有要發送到郵件伺服器的連接請求和郵件，以獲得一組IP地址。 統計伺服器跟蹤交貨情況，並可以根據設定的配額啟用或禁用發送。

![](assets/s_ncs_install_mta.png)

* 統計伺服器(**統計**)連結到Adobe Campaign基地以載入其配置。
* 傳遞伺服器(**門**)使用UDP聯繫並非始終屬於其自己實例的統計伺服器。

### 交付伺服器 {#delivery-servers}

的 **門** 模組將消息分發到 **母體** 子模組。 每個 **母體** 在從統計伺服器請求授權併發送消息之前準備消息。

步驟如下：

1. 的 **門** 選擇合格郵件並為其分配可用郵件 **母體**。
1. 的 **母體** 載入生成郵件所需的所有資訊（內容、個性化元素、附件、影像等） 將消息轉發到 **電子郵件流量整形器**。
1. 一旦電子郵件流量整形器收到統計伺服器的授權(**smtsop stat**)，消息將發送到收件人。

![](assets/s_ncs_install_email_traffic_shaper.png)

### 電子郵件伺服器統計資訊和限制 {#email-server-statistics-and-limitations}

統計伺服器為接收消息的每個電子郵件伺服器維護以下統計資訊：

* 開啟的時間點連接數，
* 最近一小時內發送的郵件數，
* 成功/拒絕連接的速率，
* 到無法訪問的伺服器的連接速率。

同時，該模組載入了某些電子郵件伺服器的限制清單：

* 最大同時連接數，
* 每小時最大消息數，
* 每個連接的最大消息數。

### 管理IP地址 {#managing-ip-addresses}

統計伺服器可以將多個實例或多個具有相同公共IP地址的電腦組合在一起。 因此，它未連結到特定實例，但它必須聯繫實例以恢復每個域的限制。

每個目標MX和每個源IP的傳遞統計資訊都會保留。 例如，如果目標域有5個MX，而平台可以使用3個不同的IP地址，則伺服器可以管理此域多達15個系列的指示符。

源IP地址與公用IP地址匹配，即遠程電子郵件伺服器所看到的地址。 此IP地址可以與承載IP地址的電腦的地址不同 **門**，如果提供了NAT路由器。 這就是為什麼統計伺服器使用與公共IP匹配的標識符(**公共ID**)。 本地地址與此標識符之間的關聯在 **serverConf.xml** 配置檔案。 中的所有可用參數 **serverConf.xml** 列在 [節](../../installation/using/the-server-configuration-file.md)。

## 傳送輸出控制 {#delivery-output-controlling}

要向電子郵件伺服器傳遞郵件， **電子郵件流量整形器** 元件從統計伺服器請求連接。 接受請求後，連接即被開啟。

在發送消息之前，模組會從伺服器請求「令牌」。 這些通常至少是10個令牌的集合，這減少了對伺服器的查詢數。

伺服器保存所有與連接和交付相關的統計資訊。 在重新啟動時，資訊會暫時丟失：每個客戶端都保留其發送統計資訊的本地副本，並定期（每2分鐘）將其返回到伺服器。 然後，伺服器可以重新聚合資料。

以下各節介紹了 **電子郵件流量整形器** 元件。

### 消息傳遞 {#message-delivery}

發送消息時，可能會有3個結果：

1. **成功**:消息已成功發送。 消息已更新。
1. **消息失敗**:已聯繫的伺服器拒絕了所選收件人的郵件。 此結果與返回代碼550到599匹配，但可以定義異常。
1. **會話失敗** （5.11向上）:的 **門** 收到此消息的應答，消息將被放棄(請參閱 [消息放棄](#message-abandonment))。 消息將發送到其他路徑，如果沒有其他路徑可用，則設定為掛起(請參閱 [消息掛起](#message-pending))。

   >[!NOTE]
   >
   >A **路徑** 是Adobe Campaign **門** 目標 **門**。 Adobe Campaign **門** 可以從多個起始IP和多個目標域IP中選擇。

### 消息放棄 {#message-abandonment}

已放棄的消息將返回到 **門** 不再由管理 **母體**。

的 **門** 決定此郵件的程式（恢復、放棄、隔離等） 取決於響應代碼和規則。

### 消息掛起 {#message-pending}

當消息到達活動隊列且沒有可用路徑時，將掛起消息。

在連接錯誤後，路徑通常被標籤為不可用於可變時間量。 不可用時間取決於錯誤的頻率和時間。

## 統計伺服器配置 {#statistics-server-configuration}

統計伺服器可供多個實例使用：它必須獨立於將使用它的實例進行配置。

首先定義將承載配置的Adobe Campaign資料庫。

### 啟動配置 {#start-configuration}

預設情況下， **統計** 每個實例都啟動了模組。 當實例在同一台電腦上池化，或實例共用同一IP地址時，將使用單個統計伺服器：其他人必須被禁用。

### 伺服器埠的定義 {#definition-of-the-server-port}

預設情況下，統計伺服器偵聽埠7777。 可以在 **serverConf.xml** 的子菜單。 中的所有可用參數 **serverConf.xml** 列在 [節](../../installation/using/the-server-configuration-file.md)。

```
<stat port="1234"/>
```

## MX配置 {#mx-configuration}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，也請參見Wiki頁。 **[!UICONTROL MX management]** 交貨吞吐量規則不再使用。 增強型MTA使用其自己的MX規則，允許它根據您自己的歷史電子郵件信譽以及您發送電子郵件的域的即時反饋，按域定制您的吞吐量。

### 關於MX規則 {#about-mx-rules}

>[!NOTE]
>
>本節和以下各節僅適用於使用舊版市場活動MTA的現場安裝和托管/混合安裝。

MX規則（郵件eXchanger）是管理發送伺服器與接收伺服器之間通信的規則。

每天早晨6點（伺服器時間）自動重新載入這些規則，以便定期提供客戶端實例。

ISP將接受每小時預定義的連接和消息數，具體取決於物料容量和內部策略。 ISP系統可以根據IP和發送域的信譽自動修改這些變數。 通過其可交付性平台，Adobe Campaign通過ISP管理150多個特定規則，此外，還為其他域管理一個通用規則。

最大連接數不完全取決於MTA使用的公共IP地址數。

例如，如果在MX規則中允許5個連接，並且配置了2個公共IP，則您可能認為不能同時開啟10個以上的此域連接。 這不是真的，事實上，最大連接數是指一個路徑和一個路徑，該路徑是我們的MTA公共IP和客戶端MTA的公共IP的組合。

在以下示例中，用戶配置了兩個公共IP地址，域為yahoo.com。

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

雅虎網站的MX記錄告訴我們，雅虎網站有3個郵件交換器。 要連接對等郵件交換器，MTA將從DNS請求其IP地址。

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

對於此記錄，用戶可以聯繫8個對等IP地址。 由於用戶有2個公共IP地址，因此這給了他們8 * 2 = 16個組合以訪問yahoo.com郵件伺服器。 這些組合中的每一個都稱為路徑。

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

mta5(98.136.216.26、98.138.112.38、63.250.192.46和98.136.217.203)中已使用了這8個IP地址中的4個。 此記錄允許用戶使用4個新IP地址。 第三份MX記錄也是一樣。

總共有16個遠程IP地址。 與我們的2個本地公共IP相結合，我們有32條路徑可以到達yahoo.com郵件伺服器。

>[!NOTE]
>
>如果2條MX記錄引用的是相同的IP地址，則此記錄將計為一條路徑，而不是兩條。

以下是使用MX規則的一些示例：

![](assets/s_ncs_examples_mx_rules.png)

在以下示例中，用戶對於特定域每小時有10,000條消息的限制，但MTA吞吐量容量高於此限制。

在這種情況下，流量將分為12個時段，每小時5分鐘，而實際限制是每時段833條消息。

這些消息將盡快傳遞。

![](assets/s_ncs_traffic_shaping.png)

### 配置MX管理 {#configuring-mx-management}

MX要遵守的規則在 **[!UICONTROL MX management]** 的 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 的子目標。

如果 **[!UICONTROL MX management]** 節點中不存在文檔，您可以手動建立它。 操作步驟：

1. 建立新的郵件規則集。
1. 選擇 **[!UICONTROL MX management]** 的子菜單。

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. 輸入 **defaultMXRules** 的 **[!UICONTROL Internal name]** 的子菜單。

要考慮更改，需要重新啟動統計伺服器。

要重新載入配置而不重新啟動統計伺服器，請在承載伺服器的電腦上使用以下命令： `nlserver stat -reload`

>[!NOTE]
>
>此命令行是 **nlserver重新啟動**。 它防止在重新啟動丟失之前收集的統計資訊，並避免使用中可能違反MX規則中定義的配額的峰值。

### 配置MX規則 {#configuring-mx-rules}

的 **[!UICONTROL MX management]** 文檔列出連結到MX規則的所有域。

這些規則按順序應用：應用其MX掩碼與目標MX相容的第一條規則。

每個規則的以下參數是：

* **[!UICONTROL MX mask]**:應用規則的域。 每個規則都定義MX的地址掩碼。 因此，任何名稱與此掩碼匹配的MX都符合條件。 掩碼可以包含「&#42;&quot;和&quot;? 一般字元。

   例如，以下地址：

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   與以下掩碼相容：

   * &#42;.yahoo.com
   * ?.mx.yahoo.com

   例如，對於電子郵件地址foobar@gmail.com，域為gmail.com,MX記錄為：

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   在這種情況下，MX規則 `*.google.com` 的下界。 如您所見，MX規則掩碼不一定與郵件中的域匹配。 適用於gmail.com電子郵件地址的MX規則將是帶有掩碼的規則 `*.google.com`。

* **[!UICONTROL Range of identifiers]**:此選項用於指示規則所適用的標識符(publicID)的範圍。 可以指定：

   * 數字：規則將僅適用於此publicId,
   * 數字範圍(**數字1 — 數字2**):該規則將適用於這兩個數字之間的所有publicId。

   >[!NOTE]
   >
   >如果欄位為空，則規則將應用於所有標識符。

   公共ID是一個或多個MTA使用的公共IP的內部標識符。 這些ID在MTA伺服器中定義， **config-instance.xml** 的子菜單。

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**:定義此MX規則的屬性範圍。 選中後，所有參數都將在實例上所有可用的IP上共用。 如果未選中，將為每個IP定義MX規則。 最大消息數乘以可用IP數。
* **[!UICONTROL Maximum number of connections]**:到發件人域的同時連接的最大數目。
* **[!UICONTROL Maximum number of messages]**:在連接上可以發送的最大消息數。 當消息超過此數時，連接將關閉，並且會開啟新的連接。
* **[!UICONTROL Messages per hour]**:一小時內可發送到發件人域的最大郵件數。
* **[!UICONTROL Connection time out]**:用於連接到域的時間閾值。

   >[!NOTE]
   >
   >Windows可以發出 **超時** 在此閾值之前，這取決於您的Windows版本。

* **[!UICONTROL Timeout Data]**:發送消息內容（SMTP協定的DATA部分）後的最長等待時間。
* **[!UICONTROL Timeout]**:與SMTP伺服器進行其他交換的最長等待時間。
* **[!UICONTROL TLS]**:TLS協定允許您對電子郵件傳送進行加密，可以有選擇地啟用。 對於每個MX掩碼，可以使用以下選項：

   * **[!UICONTROL Default configuration]**:這是在應用的serverConf.xml配置檔案中指定的常規配置。

      >[!IMPORTANT]
      >
      >不建議修改預設配置。

   * **[!UICONTROL Disabled]** :系統地發送消息而不進行加密。
   * **[!UICONTROL Opportunistic]** :如果接收伺服器(SMTP)可以生成TLS協定，則消息傳遞將被加密。

配置示例：

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>有關將MX伺服器與Adobe Campaign配合使用的詳細資訊，請參閱 [此部分](../../installation/using/using-mx-servers.md)。

### 管理電子郵件格式 {#managing-email-formats}

您可以定義已發送消息的格式，以便顯示的內容根據每個收件人地址的域自動進行調整。

要執行此操作，請轉到 **[!UICONTROL Management of email formats]** 文檔，位於 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**。

此文檔包含與Adobe Campaign管理的日文格式對應的所有預定義域的清單。 有關詳細資訊，請參閱 [此文檔](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)。

![](assets/mail_rule_sets.png)

的 **MIME結構** （多用途Internet郵件擴展）參數允許您定義將發送到不同郵件客戶端的郵件結構。 有三種可用選項：

* **多部分**:消息以文本或HTML格式發送。 如果HTML格式未被接受，則消息仍能以文本格式顯示。

   預設情況下，多部件結構為 **多部件/替代**，但是 **多部件/相關** 將影像添加到消息中時。 某些供應商預計 **多部件/相關** 預設格式， **[!UICONTROL Force multipart/related]** 選項，即使未附加影像，也可以使用此格式。

* **HTML**:只發送HTML消息。 如果HTML格式未被接受，則不顯示消息。
* **文本**:將發送僅文本格式的消息。 文本格式消息的優點是其大小很小。

如果 **[!UICONTROL Image inclusion]** 選項，這些選項將直接顯示在電子郵件正文中。 然後將上載影像，URL連結將被其內容替換。

此選項在日本市場特別使用， **Deco郵件**。 **迪克雷郵件** 或 **裝飾郵件**。 有關詳細資訊，請咨詢 [此文檔](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)。

>[!IMPORTANT]
>
>在電子郵件中插入影像會大大增加其大小。

## 傳遞伺服器配置 {#delivery-server-configuration}

### 時鐘同步 {#clock-synchronization}

必須同步構成Adobe Campaign平台（包括資料庫）的所有伺服器的時鐘，並且其系統設定為同一時區。

### 統計伺服器的坐標 {#coordinates-of-the-statistics-server}

必須在中提供統計伺服器的地址 **門**。

的 **statServer地址** 屬性 **門** 配置的元素允許您指定要使用的埠的地址和編號。

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

要在同一台電腦上使用統計伺服器，必須至少輸入該電腦的名稱 **本地主機** 值：

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>如果未填充此欄位， **門** 不會啟動。

### 要使用的IP地址清單 {#list-of-ip-addresses-to-use}

有關流量管理的配置位於 **mta/child/smtp** 配置檔案的元素。

每個 **IPAfinity** 元素，需要聲明可用於電腦的IP地址。

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
* **黑羅主機**:此標識符表示SMTP伺服器將看到的IP地址。

* **公共ID**:當多個Adobe Campaign共用IP地址時，此資訊非常有用 **母** NAT路由器後面。 統計伺服器使用此標識符來儲存該起始點和目標伺服器之間的連接和發送統計資訊。
* **重量**:允許您定義地址的相對使用頻率。 預設情況下，所有地址的權重均為1。

>[!NOTE]
>
>在serverConf.xml檔案中，需要驗證一個IP是否對應於具有唯一標識符(public_id)的單個主機。 它無法映射到多個主機，這可能導致傳遞限制問題。

在上例中，在正常情況下，地址將按如下方式分發：

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

例如，如果不能將第一個地址用於給定MX，則消息將按如下方式發送：

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **包括域**:允許您為屬於特定域的電子郵件保留此IP地址。 這是一個蒙版清單，它可包含一個或多個通配符(「&#42;&#39;)。 如果未指定該屬性，則所有域都可以使用此IP地址。

   示例： **includeDomains=&quot;wanadoo.com,orange.com,yahoo。&#42;&quot;**

* **排除域**:排除此IP地址的域清單。 此篩選器在 **包括域** 的子菜單。

   ![](assets/s_ncs_install_mta_ips.png)

## 電子郵件發送優化 {#email-sending-optimization}

Adobe Campaign內部建築 **門** 對優化電子郵件傳遞的配置有影響。 以下是改進送貨情況的一些提示。

### 調整maxWaitingMessages參數 {#adjust-the-maxwaitingmessages-parameter}

的 **maxWaitingMessages** 參數指示由 **母體**。 只有消息被發送或放棄後，才會從此清單中刪除。

如果消息未按域排序，則此參數非常重要，尤其重要。

一旦 **maxWorkingSetMb** 達到(256)閾值，傳遞伺服器停止發送消息。 效能將顯著下降，直至 **母體** 重新啟動。 要避免此問題，您可以增加 **maxWorkingSetMb** 參數，或降低 **maxWaitingMessages** 的下界。

的 **maxWorkingSetMb** 通過將最大消息數乘以平均消息大小，再乘以2.5，以經驗方式計算參數。例如，如果消息的平均大小為50 kB, **maxWaitingMessages** 參數等於1,000，所用記憶體將平均為125 MB。

### 調整匹配欄位的數量 {#adjust-the-number-of-mtachild}

子代數不應超過電腦中的處理器數(大約 1000屆)。 我們建議您不要超過8 **母體**。 然後，您可以增加每個 **孩子** (**maxMsgPerChild**)以達到足夠的壽命。
