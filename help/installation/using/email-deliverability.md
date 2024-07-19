---
product: campaign
title: 技術電子郵件設定
description: 瞭解如何設定Campaign，以在傳遞電子郵件時控制執行個體的輸出
feature: Installation, Deliverability
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '3094'
ht-degree: 0%

---

# 技術電子郵件設定{#email-deliverability}



## 概覽 {#overview}

下節提供在傳送電子郵件時控制Adobe Campaign執行個體輸出所需的設定概述。

>[!NOTE]
>
>某些設定只能由Adobe代管的部署Adobe執行，例如存取伺服器和執行個體設定檔案。 若要瞭解不同部署的詳細資訊，請參閱[託管模型](../../installation/using/hosting-models.md)區段或[此頁面](../../installation/using/capability-matrix.md)。

如需與Adobe Campaign傳遞能力相關的概念和最佳實務的詳細資訊，請參閱本[區段](../../delivery/using/about-deliverability.md)。

如需深入瞭解傳遞能力是什麼，包括有關Adobe平台有效率傳送和接收電子郵件的所有技術建議，請參閱[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。

## 操作原則 {#operating-principle}

您可以根據網域控制一或多個Adobe Campaign執行個體的輸出，以限制傳送的電子郵件數量。 例如，您可以將&#x200B;**yahoo.com**&#x200B;位址的輸出限製為每小時20,000，而所有其他網域則設定為每小時100,000則訊息。

必須控制傳遞伺服器(**mta**)使用的每個IP位址的訊息輸出。 在數台電腦上劃分的數個&#x200B;**mta**&#x200B;屬於各種Adobe Campaign執行個體，這些執行個體可以共用相同的IP位址來傳送電子郵件：需要設定程式來協調這些IP位址的使用。

這是&#x200B;**stat**&#x200B;模組所做的動作：它會轉送所有連線要求及要傳送至一組IP位址之郵件伺服器的郵件。 統計伺服器會追蹤傳遞內容，並可根據設定的配額啟用或停用傳送。

![](assets/s_ncs_install_mta.png)

* 統計伺服器(**stat**)已連結至Adobe Campaign基底以載入其設定。
* 傳遞伺服器(**mta**)使用UDP來連絡統計伺服器，該伺服器並不一定屬於自己的執行個體。

### 傳遞伺服器 {#delivery-servers}

**mta**&#x200B;模組會將訊息散發到其&#x200B;**mtachild**&#x200B;子模組。 每個&#x200B;**mtachild**&#x200B;會先準備郵件，再向統計伺服器要求授權，然後再進行傳送。

步驟如下：

1. **mta**&#x200B;會選取符合資格的郵件，並指派可用的&#x200B;**mtachild**&#x200B;給他們。
1. **mtachild**&#x200B;載入建立郵件所需的所有資訊（內容、個人化元素、附件、影像等） 並將訊息轉寄給&#x200B;**電子郵件流量整形器**。
1. 電子郵件流量整形器一收到統計伺服器的授權(**smtp stat**)，郵件就會傳送給收件者。

![](assets/s_ncs_install_email_traffic_shaper.png)

### 電子郵件伺服器統計資料和限制 {#email-server-statistics-and-limitations}

統計值伺服器會維護每個接收訊息之電子郵件伺服器的下列統計值：

* 開啟的時間點連線數目，
* 過去一小時內傳送的訊息數，
* 成功/拒絕連線的速率，
* 連線到無法連線之伺服器的速率。

同時，模組會載入特定電子郵件伺服器的限制清單：

* 同時連線數目上限，
* 每小時訊息數上限，
* 每個連線的最大訊息數量。

### 管理IP位址 {#managing-ip-addresses}

統計伺服器可以結合數個執行個體或具有相同公用IP位址的數台電腦。 因此，它不會連結到特定執行個體，但必須聯絡執行個體才能復原每個網域的限制。

會保留每個目標MX和每個來源IP的傳遞統計資料。 例如，如果目標網域有5個MX，而平台可以使用3個不同的IP位址，則伺服器可以為此網域管理最多15個系列的指標。

來源IP位址符合公用IP位址，即遠端電子郵件伺服器所看到的位址。 若提供NAT路由器，此IP位址可能與裝載&#x200B;**mta**&#x200B;的電腦位址不同。 這就是統計伺服器使用符合公用IP (**publicId**)的識別碼的原因。 本機位址與此識別碼之間的關聯已在&#x200B;**serverConf.xml**&#x200B;組態檔中宣告。 **serverConf.xml**&#x200B;中可用的所有引數都列在此[區段](../../installation/using/the-server-configuration-file.md)中。

## 傳遞輸出控制 {#delivery-output-controlling}

若要將郵件傳送至電子郵件伺服器，**電子郵件流量整形器**&#x200B;元件會要求統計伺服器連線。 一旦接受要求，就會開啟連線。

在傳送訊息之前，模組會從伺服器要求「Token」。 這些通常是至少包含10個權杖的集合，這會減少向伺服器查詢的次數。

伺服器會儲存與連線和傳遞相關的所有統計資料。 在重新開機時，資訊會暫時遺失：每個使用者端都會保留其傳送統計資料的本機副本，並定期（每2分鐘）將其傳回伺服器。 然後，伺服器可以重新彙總資料。

以下各節說明&#x200B;**電子郵件流量整形器**&#x200B;元件處理郵件的方式。

### 訊息傳送 {#message-delivery}

傳送訊息時，可能有3個結果：

1. **成功**：已成功傳送訊息。 訊息已更新。
1. **郵件失敗**：連絡的伺服器已拒絕所選收件者的郵件。 此結果符合傳回碼550到599，但可以定義例外。
1. **工作階段失敗** （5.11以上）：如果&#x200B;**mta**&#x200B;收到此訊息的回應，則會捨棄該訊息（請參閱[訊息放棄](#message-abandonment)）。 訊息會傳送至其他路徑，或如果沒有其他可用路徑，則設為擱置（請參閱[訊息擱置](#message-pending)）。

   >[!NOTE]
   >
   >**路徑**&#x200B;是Adobe Campaign **mta**&#x200B;與目標&#x200B;**mta**&#x200B;之間的連線。 Adobe Campaign **mta**&#x200B;可以從多個起始IP和多個目標網域IP中進行選擇。

### 放棄訊息 {#message-abandonment}

捨棄的訊息會傳回&#x200B;**mta**，不再由&#x200B;**mtachild**&#x200B;管理。

**mta**&#x200B;決定此郵件的程式（復原、放棄、隔離等） 視回應代碼和規則而定。

### 訊息待處理 {#message-pending}

當訊息到達使用中佇列且沒有可用路徑時，該訊息便會擱置。

發生連線錯誤後，路徑通常會在一段變數時間內標示為無法使用。 無法使用期間取決於錯誤的頻率和年齡。

## 統計資料伺服器設定 {#statistics-server-configuration}

統計伺服器可供數個執行個體使用：它必須獨立於使用它的執行個體進行設定。

首先，定義將主控設定的Adobe Campaign資料庫。

### 開始設定 {#start-configuration}

依預設，會為每個執行個體啟動&#x200B;**stat**&#x200B;模組。 當執行個體共用在相同電腦上時，或當執行個體共用相同的IP位址時，會使用單一統計伺服器：其他必須停用。

### 伺服器連線埠的定義 {#definition-of-the-server-port}

依預設，統計伺服器會在連線埠7777上接聽。 可以在&#x200B;**serverConf.xml**&#x200B;檔案中修改此連線埠。 **serverConf.xml**&#x200B;中可用的所有引數都列在此[區段](../../installation/using/the-server-configuration-file.md)中。

```
<stat port="1234"/>
```

## MX組態 {#mx-configuration}

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md)，將不再使用&#x200B;**[!UICONTROL MX management]**&#x200B;傳遞輸送量規則。 Enhanced MTA會使用其專屬的MX規則，如此可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件之網域所提供的即時回饋，而依網域來自訂您的輸送量。

### 關於MX規則 {#about-mx-rules}

>[!NOTE]
>
>本節及以下各節僅適用於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝。

MX規則（郵件交換器）是管理傳送伺服器與接收伺服器之間通訊的規則。

這些規則會在每天早上6點（伺服器時間）自動重新載入，以定期提供使用者端例項。

根據材料容量和內部政策，ISP將接受每小時預先定義的連線數和訊息數。 ISP系統可能會根據IP和傳送網域的信譽自動修改這些變數。 透過其傳遞平台，Adobe Campaign可管理ISP超過150項特定規則，此外還有適用於其他網域的一般規則。

連線數目上限並不完全取決於MTA使用的公用IP位址數目。

例如，如果您在MX規則中允許5個連線，並且已設定2個公用IP，您可能會認為您無法同時開啟超過10個連線至此網域。 這不是真的，實際上最大連線數是指路徑和路徑，這些路徑是我們的MTA公用IP之一和使用者端的MTA的公用IP的組合。

在以下範例中，使用者已設定兩個公用IP位址，而網域為yahoo.com。

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

yahoo.com的MX記錄告訴我們yahoo.com有3個郵件交換器。 若要連線對等郵件交換器，MTA將會向DNS要求其IP位址。

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

對於此記錄，使用者可以聯絡8個對等IP位址。 由於使用者有2個公用IP位址，因此可提供8 * 2 = 16個組合以連線yahoo.com郵件伺服器。 這些組合中的每一個都稱為路徑。

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

這8個IP位址中有4個已用於mta5 （98.136.216.26、98.138.112.38、63.250.192.46和98.136.217.203）。 此記錄可讓使用者使用4個新的IP位址。 第三個MX記錄也會有相同作用。

總共有16個遠端IP位址。 結合我們2個本機公用IP，我們有32個路徑可連線到yahoo.com郵件伺服器。

>[!NOTE]
>
>如果2條MX記錄參照的是相同的IP位址，則這條記錄會計為一條路徑，而不是兩條路徑。

以下是使用MX規則的一些範例：

![](assets/s_ncs_examples_mx_rules.png)

在以下範例中，使用者設有特定網域每小時10,000則訊息的限制，但MTA輸送量容量高於此限制。

在此情況下，流量會每小時被分為12個時段（5分鐘），實際限製為每時段833則訊息。

這些訊息將會儘快傳遞。

![](assets/s_ncs_traffic_shaping.png)

### 設定MX管理 {#configuring-mx-management}

要針對MX遵守的規則定義於樹狀結構&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;節點的&#x200B;**[!UICONTROL MX management]**&#x200B;檔案中。

如果&#x200B;**[!UICONTROL MX management]**&#x200B;檔案不存在於節點中，您可以手動建立。 操作步驟：

1. 建立一組新的郵件規則。
1. 選擇&#x200B;**[!UICONTROL MX management]**&#x200B;模式。

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. 在&#x200B;**[!UICONTROL Internal name]**&#x200B;欄位中輸入&#x200B;**defaultMXRules**。

若要將變更列入考量，您必須重新啟動統計伺服器。

若要重新載入設定而不重新啟動統計伺服器，請在裝載伺服器的電腦上使用下列命令： `nlserver stat -reload`

>[!NOTE]
>
>此命令列優先於&#x200B;**nlserver重新啟動**。 它可防止在重新啟動遺失之前收集的統計資料，並避免使用中的尖峰，這些尖峰可能會違反MX規則中定義的配額。

### 設定MX規則 {#configuring-mx-rules}

**[!UICONTROL MX management]**&#x200B;檔案列出連結至MX規則的所有網域。

這些規則會依序套用：會套用其MX遮罩與目標MX相容的第一個規則。

以下為可用於每個規則的引數：

* **[!UICONTROL MX mask]**：套用規則的網域。 每個規則都會定義MX的位址遮罩。 因此，任何名稱符合此遮罩的MX都是適用的。 遮罩可包含&quot;&#42;&quot;和&quot;？&quot; 一般字元。

  例如，下列位址：

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

  與下列遮罩相容：

   * &#42;.yahoo.com
   * ？.mx.yahoo.com

  例如，電子郵件地址foobar@gmail.com的網域為gmail.com，而MX記錄為：

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

  在此情況下，將會使用MX規則`*.google.com`。 如您所見，MX規則遮罩並不一定與郵件中的網域相符。 套用至gmail.com電子郵件地址的MX規則將是遮罩為`*.google.com`的規則。

* **[!UICONTROL Range of identifiers]**：此選項可讓您指定套用規則的識別碼(publicID)範圍。 您可以指定：

   * 數字：規則將僅適用於此publicId，
   * 數字範圍(**number1-number2**)：規則將套用至這兩個數字之間的所有publicId。

  >[!NOTE]
  >
  >如果欄位為空，規則會套用至所有識別碼。

  公用ID是一個或多個MTA使用的公用IP的內部識別碼。 這些ID是在&#x200B;**config-instance.xml**&#x200B;檔案的MTA伺服器中定義。

  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**：定義此MX規則的屬性範圍。 如果勾選，所有引數會在執行個體上可用的所有IP上共用。 取消勾選後，會為每個IP定義MX規則。 訊息數上限乘以可用的IP數。
* **[!UICONTROL Maximum number of connections]**：同時連線至寄件者網域的最大數目。
* **[!UICONTROL Maximum number of messages]**：連線時可傳送的訊息數上限。 當訊息超過此數目時，會關閉連線並開啟新連線。
* **[!UICONTROL Messages per hour]**：一小時內可傳送到寄件者網域的郵件數上限。
* **[!UICONTROL Connection time out]**：連線到網域的時間臨界值。

  >[!NOTE]
  >
  >視您的Windows版本而定，Windows可以在此臨界值之前發出&#x200B;**逾時**。

* **[!UICONTROL Timeout Data]**：傳送郵件內容後的最長等待時間（SMTP通訊協定的DATA區段）。
* **[!UICONTROL Timeout]**：與SMTP伺服器的其他交換等待時間上限。
* **[!UICONTROL TLS]**：可以選擇性啟用TLS通訊協定，讓您加密電子郵件傳遞。 對於每個MX遮色片，下列選項可供使用：

   * **[!UICONTROL Default configuration]**：這是套用的serverConf.xml組態檔中指定的一般組態。

     >[!IMPORTANT]
     >
     >不建議修改預設設定。

   * **[!UICONTROL Disabled]** ：郵件會系統化傳送，不會加密。
   * **[!UICONTROL Opportunistic]** ：如果接收伺服器(SMTP)可以產生TLS通訊協定，則會將郵件傳遞加密。

設定範例：

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>如需搭配Adobe Campaign使用MX伺服器的詳細資訊，請參閱[本節](../../installation/using/using-mx-servers.md)。

### 管理電子郵件格式 {#managing-email-formats}

您可以定義已傳送訊息的格式，以便顯示的內容能根據每位收件者地址的網域自動調整。

若要這麼做，請前往&#x200B;**[!UICONTROL Management of email formats]**&#x200B;檔案，它位於&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**。

本檔案包含對應至Adobe Campaign所管理日文格式的所有預先定義網域清單。 如需詳細資訊，請參閱[此檔案](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)。

![](assets/mail_rule_sets.png)

**MIME結構** （多用途網際網路郵件延伸）引數可讓您定義將傳送給不同郵件使用者端的郵件結構。 有三種可用選項：

* **Multipart**：郵件是以文字或HTML格式傳送。 如果不接受HTML格式，訊息仍能以文字格式顯示。

  依照預設，多重部分結構為&#x200B;**multipart/alternative**，但是當影像新增至訊息時，它會自動變成&#x200B;**multipart/related**。 某些提供者預設會使用&#x200B;**multipart/related**&#x200B;格式，即使未附加任何影像，**[!UICONTROL Force multipart/related]**&#x200B;選項也會採用此格式。

* **HTML**：只傳送HTML訊息。 如果不接受HTML格式，則不會顯示訊息。
* **文字**：已傳送純文字格式的訊息。 文字格式訊息的優點在於其非常小。

如果&#x200B;**[!UICONTROL Image inclusion]**&#x200B;選項已啟用，這些會直接顯示在電子郵件內文中。 然後會上傳影像，並以其內容取代URL連結。

日本市場特別使用這個選項來處理&#x200B;**裝飾郵件**、**裝飾郵件**&#x200B;或&#x200B;**裝飾郵件**。 如需詳細資訊，請參閱[此檔案](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles)。

>[!IMPORTANT]
>
>在電子郵件中插入影像會大幅增加其大小。

## 傳遞伺服器設定 {#delivery-server-configuration}

### 時鐘同步 {#clock-synchronization}

構成Adobe Campaign平台（包括資料庫）之所有伺服器的時鐘必須同步，且其系統設定為相同時區。

### 統計伺服器的座標 {#coordinates-of-the-statistics-server}

必須在&#x200B;**mta**&#x200B;中提供統計伺服器的位址。

組態的&#x200B;**mta**&#x200B;專案的&#x200B;**statServerAddress**&#x200B;屬性可讓您指定要使用的連線埠位址和號碼。

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

若要在同一部電腦上使用統計伺服器，您必須至少輸入具有&#x200B;**localhost**&#x200B;值的電腦名稱：

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>如果未填入此欄位，**mta**&#x200B;將不會啟動。

### 要使用的IP位址清單 {#list-of-ip-addresses-to-use}

有關流量管理的組態位於組態檔的&#x200B;**mta/child/smtp**&#x200B;專案。

對於每個&#x200B;**IPAffinity**&#x200B;專案，您必須宣告可用於電腦的IP位址。

例如：

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

引數如下：

* **位址**：這是要使用的MTA主機電腦的IP位址。
* **heloHost**：此識別碼代表SMTP伺服器所看到的IP位址。

* **publicId**：當IP位址由NAT路由器後面的數個Adobe Campaign **mta**&#x200B;共用時，此資訊很有用。 統計資料伺服器會使用此識別碼來記憶此起始點和目標伺服器之間的連線和傳送統計資料。
* **權重**：可讓您定義地址的相對使用頻率。 依預設，所有地址的權重等於1。

>[!NOTE]
>
>在serverConf.xml檔案中，您需要確認一個IP對應至具有唯一識別碼(public_id)的單一主機。 它無法對應至多個主機，這可能會造成傳送節流問題。

在上一個範例中，若使用一般條件，位址的分佈如下：

    * 「1」： 5 / (5+5+1) = 45%
    * 「2」： 5 / (5+5+1) = 45%
    * 「3」： 1 / (5+5+1) = 10%

舉例來說，如果第一個位址無法用於指定的MX，則會傳送如下訊息：

    * 「2」： 5 / (5+1) = 83%
    * 「3」： 1 / (5+1) = 17%

* **includeDomains**：可讓您保留此IP位址給屬於特定網域的電子郵件。 此遮罩清單可包含一或多個萬用字元(&#39;&#42;&#39;)。 如果未指定屬性，則所有網域都可以使用此IP位址。

  範例： **includeDomains=&quot;wanadoo.com，orange.com，yahoo.&#42;&quot;**

* **excludeDomains**：排除此IP位址的網域清單。 此篩選器套用在&#x200B;**includeDomains**&#x200B;篩選器之後。

  ![](assets/s_ncs_install_mta_ips.png)

## 電子郵件傳送最佳化 {#email-sending-optimization}

Adobe Campaign **mta**&#x200B;的內部架構對最佳化電子郵件傳遞的設定產生影響。 以下提供一些改善傳送的秘訣。

### 調整maxWaitingMessages引數 {#adjust-the-maxwaitingmessages-parameter}

**maxWaitingMessages**&#x200B;參數列示&#x200B;**mtachild**&#x200B;預先準備的訊息數目上限。 只有在傳送或捨棄訊息後，才會從此清單中刪除訊息。

如果訊息未依網域排序，此引數就非常重要，且特別重要。

一旦達到&#x200B;**maxWorkingSetMb** (256)臨界值，傳遞伺服器就會停止傳送訊息。 效能將大幅降低，直到&#x200B;**mtachild**&#x200B;再次啟動。 若要避免此問題，您可以增加&#x200B;**maxWorkingSetMb**&#x200B;引數的臨界值，或減少&#x200B;**maxWaitingMessages**&#x200B;引數的臨界值。

**maxWorkingSetMb**&#x200B;引數的計算方式是依據經驗將訊息數目上限乘以平均訊息大小，並將結果乘以2.5。例如，如果訊息的平均大小為50 kB，且&#x200B;**maxWaitingMessages**&#x200B;引數等於1,000，則使用的記憶體將平均125 MB。

### 調整配對數量 {#adjust-the-number-of-mtachild}

子系的數目不應超過機器中的處理器數目(約 1000個工作階段)。 建議您不要超過8 **mtachild**。 然後，您可以增加每個&#x200B;**子項** (**maxMsgPerChild**)的訊息數量，以獲得足夠的壽命。
