---
title: 設定促銷活動伺服器
seo-title: 設定促銷活動伺服器
description: 設定促銷活動伺服器
seo-description: null
page-status-flag: never-activated
uuid: be21ae4b-ca2a-4952-b256-cd8dc51309cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1a94c94e-ab6b-45c2-a0f3-6adeec7e2d2d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1e8492d8e91d679ac13da875974e27d0f7791dc3

---


# 設定促銷活動伺服器{#configuring-campaign-server}

下節詳細說明可根據您的需求和環境特性執行的伺服器端組態。

這些組態必須由管理員執行，且僅 **適用於內部部署** 代管模型。 對於 **代管** (Hosted)部署，伺服器端設定只能由Adobe設定。 不過，您可以在「控制面板」中設定某些設定（例如，IP白名單或URL權限）。

如需詳細資訊，請參閱下列章節：

* [控制面板檔案](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)
* [代管模型](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署與代管功能矩陣](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)
* [混合型和代管型配置步驟](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_About_hybrid_and_hosted_models.html)

Campaign Classic組態檔會儲存在Adobe Campaign安 **裝資料夾的** conf資料夾中。 配置分佈在兩個檔案上：

* **serverConf.xml**:所有實例的常規配置。 此檔案結合了Adobe Campaign伺服器的技術參數：這些會由所有例項共用。 以下詳細說明了其中一些參數。 本節列出的不同節點和 [參數](../../installation/using/the-server-configuration-file.md)。
* **config-`<instance>`.xml** (其中 **instance** 是實例的名稱):實例的特定配置。 如果您在多個實例之間共用伺服器，請在其相關檔案中輸入每個實例的特定參數。

## 定義安全區 {#defining-security-zones}

### 關於安全區 {#about-security-zones}

每個運算子都必須連結至區域才能登入例項，且運算子IP必須包含在安全區域中定義的位址或位址集中。 安全區設定是在Adobe Campaign伺服器的設定檔案中執行。

操作員從控制台（節點）中的配置檔案連結到安 **[!UICONTROL Administration > Access management > Operators]** 全區。 在本節中瞭解如何將區域連結至Campaign [運算子](#linking-a-security-zone-to-an-operator)。

### 建立安全區 {#creating-security-zones}

區域由以下項定義：

* 一或多個IP位址範圍（IPv4和IPv6）
* 與每個IP位址範圍連結的技術名稱

安全區域互鎖，這表示在另一個區域中定義新區域可以減少可登錄該區域的運算子數量，同時增加分配給每個運算子的權限。

必須在伺服器配置期間在serverConf.xml文 **件中定義區域** 。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

每個區域都定義權限，例如：

* HTTP連線，而非HTTPS
* 錯誤顯示（Java錯誤、JavaScript、C++等）
* 報告和webApp預覽
* 透過登入／密碼進行驗證
* 非安全連接模式

>[!NOTE]
>
>**每個運算子都必須連結至區域**。 如果運算子的IP位址屬於區域所定義的範圍，運算子可登入執行個體。\
>操作員的IP地址可以定義在多個區域中。 在這種情況下，運算子會收到 **每個區** 域的可用權限集。

現成可用的serverConf.xml **檔案包含** 3個區域：公 **共、VPN和LAN**。

>[!NOTE]
>
>**現成可用的配置是安全的**。 不過，在從舊版Adobe Campaign移轉之前，可能需要暫時降低安全性，才能移轉並核准新規則。

如何在serverConf.xml檔案中定 **義區域的示例** :

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

定義區域的所有權利如下：

* **allowDebug**:可讓webApp在「debug」模式中執行
* **allowEmptyPassword**:授權不使用密碼的實例的連接
* **allowHTTP**:不需使用HTTPS通訊協定即可建立工作階段
* **allowUserPassword**:作業Token可以有下列格式「`<login>/<password>`」
* **sessionTokenOnly**:連線URL中不需要安全性Token
* **showErrors**:會轉送並顯示伺服器端的錯誤

>[!CAUTION]
>
>在區域定義中，每個具有true值的屬 **性** ，都會降低安全性。

使用消息中心時，如果有數個執行例項，您需要建立額外的安全區，其中 **sessionTokenOnly** attribute defined as **true**，其中只需新增必要的IP位址。 如需設定例項的詳細資訊，請參 [閱本檔案](../../message-center/using/creating-a-shared-connection.md)。

### 安全區的最佳做法 {#best-practices-for-security-zones}

在LAN安全區的定 **義中** ，可以添加定義技術訪問的IP地址掩碼。 此新增功能將允許存取伺服器上裝載的所有執行個體。

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

我們建議在僅存取特定例項的運算子專用的設定檔案中，直接定義IP位址範圍。

在檔 **`config-<instance>.xml`** 案中：

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

### 安全區中的子網和代理 {#sub-networks-and-proxies-in-a-security-zone}

proxy參 **數可用於子網元** 素中，以指定安全區 **** 域中的proxy使用。

當參考代理並且連接通過此代理進入時（通過HTTP X-Forwarded-For標頭可見），驗證區域是代理的客戶端區域，而不是代理的客戶端區域。

>[!CAUTION]
>
>如果已設定代理，並且可以覆寫它（或者如果不存在），則測試的IP位址將會被偽造。
>
>此外，中繼現在也像Proxy一樣產生。 因此，您可以將IP地址127.0.0.1添加到安全區配置中的Proxy清單中。
>
>例如：「 `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`」。

可能會發生各種情況：

* 安全區中直接引用子網路，且未配置代理：子網路的使用者可以直接連線至Adobe Campaign伺服器。

   ![](assets/8101_proxy1.png)

* 為安全區域中的子網路指定代理：來自此子網路的使用者可透過此代理存取Adobe Campaign伺服器。

   ![](assets/8101_proxy2.png)

* 代理包含在安全區子網路中：透過此Proxy存取的使用者（不論其來源為何）都可存取Adobe Campaign伺服器。

   ![](assets/8101_proxy3.png)

可能存取Adobe Campaign伺服器的Proxy IP位址必須同時輸入相關網路和 **`<subnetwork>`** 第一層子網路 **`<subnetwork name="all"/>`**。 例如，以下是IP位址為10.131.146.102的Proxy:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

### 將安全區連結到操作員 {#linking-a-security-zone-to-an-operator}

定義區域後，必須將每個運算子連結到其中一個運算子，才能登錄到實例，並且該運算子的IP地址必須包含在區域中引用的地址或地址範圍中。

區域的技術組態會在促銷活動伺服器的組態檔案中執行： **serverConf.xml**。

在此之前，您必須首先配置現成枚舉，以將標籤連結到 **[!UICONTROL Security zone]** serverConf.xml檔案中定義的區 **域的內部名稱** 。

此設定是在促銷活動檔案總管中完成：

1. 按一下節 **[!UICONTROL Administration > Platform > Enumerations]** 點。
1. 選擇系 **[!UICONTROL Security zone (securityZone)]** 統枚舉。

   ![](assets/enum_securityzone.png)

1. 對於伺服器配置檔案中定義的每個安全區，按一下按 **[!UICONTROL Add]** 鈕。
1. 在字 **[!UICONTROL Internal name]** 段中，輸入serverConf.xml檔案中定 **義的區域名稱** 。 它對應於元 **素的@name**`<securityzone>` 屬性。 在標籤欄位中輸入連結至內部名稱的 ****&#x200B;標籤。

   ![](assets/enum_addsecurityvalue.png)

1. 按一下「確定」並儲存修改。

定義區域並配置枚舉後， **[!UICONTROL Security zone]** 您需要將每個操作符連結到安全區域：

1. 按一下節 **[!UICONTROL Administration > Access management > Operators]** 點。
1. 選擇要將安全區域連結到的操作員，然後按一下該選 **[!UICONTROL Edit]** 項卡。
1. 前往標籤 **[!UICONTROL Access rights]** 並按一下連 **[!UICONTROL Edit access parameters...]** 結。

   ![](assets/zone_operator.png)

1. 從下拉式清單 **[!UICONTROL Authorized connection zone]** 中選取區域

   ![](assets/zone_operator_selection.png)

1. 按一 **[!UICONTROL OK]** 下並儲存修改，以套用這些變更。

## 配置Tomcat {#configuring-tomcat}

### Tomcat的預設埠 {#default-port-for-tomcat}

當Tomcat伺服器的8080偵聽埠已忙於配置所需的其他應用程式時，您需要將8080埠替換為免費埠（例如8090）。 若要變更，請編 **輯儲存在** Adobe Campaign安裝資料夾之 **** /tomcat-7/conf目錄中的server.xml檔案。

然後修改JSP中繼頁的埠。 若要這麼做，請變 **更儲存在Adobe Campaign安裝目錄** /conf **** 目錄中的serverConf.xml檔案。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### 映射Tomcat中的資料夾 {#mapping-a-folder-in-tomcat}

要定義客戶特定設定，可以在 **/tomcat-7/conf** （包含上下文。xml檔案）資料夾中建立 **user_contexts.xml****** 檔案。

此檔案將包含下列類型的資訊：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可在伺服器端重制此作業。

## 個人化傳送參數 {#personalizing-delivery-parameters}

傳送參數在serverConf.xml **配置檔案中定義** 。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

一般伺服器組態和指令在 [Campaign伺服器組態中有詳細說明](../../installation/using/campaign-server-configuration.md)。

您也可以根據您的需求和設定執行下列設定。

### SMTP中繼 {#smtp-relay}

MTA模組用作SMTP廣播（埠25）的本地郵件傳輸代理。

但是，如果安全策略要求，則可以將其替換為中繼伺服器。 在這種情況下，全局吞吐量將是中繼吞吐量（前提是中繼伺服器吞吐量低於Adobe Campaign 1）。

在這種情況下，這些參數是通過在部分中配置SMTP伺服器來設 **`<relay>`** 置的。 必須指定用於傳輸郵件及其關聯埠的SMTP伺服器的IP地址（或主機）（預設為25）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!CAUTION]
>
>此操作模式對傳送帶來嚴重限制，因為由於中繼伺服器的固有效能（延遲、頻寬……），它可大大降低吞吐量。 此外，限定同步傳送錯誤（通過分析SMTP通信量檢測到）的能力將受到限制，如果中繼伺服器不可用，則無法發送。

### MTA子進程 {#mta-child-processes}

可以根據伺服器的CPU功率和可用網路資源來控制子進程（預設情況下為maxSpareServers 2）的數量，以優化廣播效能。 此配置將在每台電腦的MTA **`<master>`** 配置部分中進行。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱「電子郵 [件傳送最佳化」](../../installation/using/email-deliverability.md#email-sending-optimization)。

### 管理具有相關性的出站SMTP通信 {#managing-outbound-smtp-traffic-with-affinities}

>[!CAUTION]
>
>相關性配置需要從一個伺服器到另一個伺服器之間保持一致。 我們建議您連絡Adobe以取得相似性設定，因為所有執行MTA的應用程式伺服器上都應複製設定變更。

您可以通過具有IP地址的相關性來改進出站SMTP通信。

若要這麼做，請套用下列步驟：

1. 在serverConf.xml檔案 **`<ipaffinity>`** 的區段 **中輸入相關性** 。

   **一個相似性可以有數個不同的名稱：分離，使用**;字元。

   例如：

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   要查看相關參數，請參 **閱serverConf.xml檔案** 。

1. 若要在下拉式清單中啟用相似性選擇，您需要在 **IPAffinity枚舉中新增相似性名稱** 。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >本文檔詳細介紹了 [枚舉](../../platform/using/managing-enumerations.md)。

   然後，您可以選取要使用的相似性，如下所示：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您也可以參考 [Delivery伺服器組態](../../installation/using/email-deliverability.md#delivery-server-configuration)。

## URL權限 {#url-permissions}

可由JavaScript代碼（工作流程等）呼叫的預設URL清單的Campaign Classic例項有限。 這些URL可讓您的例項正常運作。

依預設，例項不允許連線至外部URL。 不過，您可以將一些外部URL新增至授權URL的清單，讓您的例項可以連線至這些URL。 這可讓您將促銷活動例項連接至外部系統，例如SFTP伺服器或網站，以啟用檔案和／或資料傳輸。

新增URL後，該URL會在例項的設定檔案(serverConf.xml)中參考。

它們可讓您管理URL權限的方式視您的代管模型而定：

* **混合** 或 **內部部署**:將允許的URL新增至 **serverConf.xml檔案**。 詳細資訊請參閱以下章節。
* **代管**:新增URL以允許透過「控 **制面板」**。 如需詳細資訊，請參閱專 [用檔案](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html)。

使用 **Hybrid****和** On-premise **代管模型時，管理員需要參考** Server **** Conf.xml檔案中的新urlPermission。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

存在三種連接保護模式：

* **阻止**:不屬於白名單的所有URL都會被封鎖，並顯示錯誤訊息。 這是postupgrade之後的預設模式。
* **權限**:允許所有不屬於白名單的URL。
* **警告**:所有非白色的URL皆允許使用，但JS解譯器會發出警告，讓管理員可以收集這些URL。 此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!CAUTION]
>
>根據預設，新客戶的客戶端使用阻 **塞模式**。 如果他們需要允許新的URL，則應聯絡其管理員以將它列入白名單。
>
>來自移轉的現有客戶可使用警 **告模式** 一段時間。 同時，他們需要在授權URL之前分析出站流量。 定義授權URL清單後，應連絡其管理員，將URL加入白名單並啟 **用封鎖模式**。

## 動態頁面安全性與中繼 {#dynamic-page-security-and-relays}

預設情況下，所有動態頁都自動與啟動Web模 **塊的電腦的本地** Tomcat伺服器相關。 此配置在 **`<url>`** ServerConf.xml檔案的查 **詢中繼配置部分中輸** 入。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

在遠程伺服器上中繼動態頁 **面** ;如果未在電腦上激活Web模組。 為此，必須將 **localhost** 替換為JSP和JSSP、Web應用程式、報告和字串的遠程電腦的名稱。

有關各種可用參數的詳細資訊，請參 **閱serverConf.xml配置檔案** 。

對於JSP頁，預設配置為：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用下列JSP頁面：

* /nl/jsp/**soapruter.jsp**:用戶端主控台與網站服務連線(SOAP API)、
* /nl/jsp/**m.jsp**:鏡像頁面，
* /nl/jsp/**logon.jsp**:基於Web訪問報告和客戶端控制台的部署，
* /nl/jsp/**s.jsp** :使用病毒式行銷（贊助和社交網路）。

「行動應用程式頻道」使用的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**例如：**

可以防止客戶機從外部連接。 為此，只需限制 **soaprouter.jsp的執行** ，並僅授權執行鏡像頁、病毒式連結、Web表單和公共資源。

參數如下：

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

在此示例中，該 **`<IP_addresses>`** 值與授權使用此掩碼中繼模組的IP地址清單（由comas分隔）一致。

>[!NOTE]
>
>值應根據您的配置和網路限制進行調整，尤其是如果已為您的安裝開發了特定配置。

## 限制授權的外部命令 {#restricting-authorized-external-commands}

>[!NOTE]
>
>只有內部部署安裝才需要以下配置。

從組建8780起，技術管理員可限制Adobe Campaign中可使用的授權外部指令清單。

為此，您需要建立一個文本檔案，其中包含您要防止使用的命令清單，例如：

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!CAUTION]
>
>這份清單並非完整無遺。

在服務 **器配置檔案** 的執行節點中，需要引用blackstFile屬性中以前建立 **的檔案** 。

**僅適用於Linux**:在伺服器配置檔案中，我們重新命令您指定專用於執行外部命令的用戶，以增強您的安全配置。 此用戶在配置檔案的 **exec** 節點中設定。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

>[!NOTE]
>
>如果未指定任何使用者，則會在Adobe Campaign例項的使用者內容中執行所有命令。 使用者必須與執行Adobe Campaign的使用者不同。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

此使用者必須新增至「Adobe Campaign」運算子的使用者清單。

>[!CAUTION]
>
>您不應使用自訂sudo。 系統上需要安裝標準Sudo。

## 管理HTTP標題 {#managing-http-headers}

依預設，不會中繼所有HTTP標題。 您可以在中繼傳送的回覆中新增特定標題。 操作步驟：

1. 轉至 **serverConf.xml檔案** 。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。
1. 在節 **`<relay>`** 點中，轉至中繼的HTTP標頭清單。
1. 新增具 **`<responseheader>`** 有下列屬性的元素：

   * **名稱**:標題名稱
   * **值**:值名稱。
   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 冗餘追蹤 {#redundant-tracking}

當使用多部伺服器進行重新導向時，它們必須能夠透過SOAP呼叫彼此通訊，才能共用要重新導向之URL的資訊。 在發送啟動時，可能並非所有重定向伺服器都可用；因此，他們可能沒有相同程度的資訊。

>[!NOTE]
>
>使用標準或企業架構時，主應用程式伺服器必須獲得授權，才能在每部電腦上傳追蹤資訊。

冗餘伺服器的URL必須通過serverConf.xml檔案在重定向配置 **中指定** 。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

**例如：**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

enableIf **** 屬性是可選的（預設為空），並允許您僅在結果為true時啟用連接；這可讓您在所有重新導向伺服器上取得相同的組態。

要獲取電腦的主機名，請運行以下命令： **hostname -s**。

## 管理公共資源 {#managing-public-resources}

公共資源在管理公共 [資源中顯示](../../installation/using/deploying-an-instance.md#managing-public-resources)。

它們會儲存在 **Adobe Campaign安裝目錄的** /var/res/instance目錄中。

相符的URL為： **http://server/res/instance** ，其 **中instance** 是追蹤例項的名稱。

通過向 **conf-`<instance>`** .xml檔案添加節點以配置伺服器上的儲存，可以指定另一個目錄。 這表示新增下列行：

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

在這種情況下，在部署精靈視窗的上半部中指定之公用資源的新URL應指向此資料夾。

## 高可用性工作流程與相關性 {#high-availability-workflows-and-affinities}

您可以設定數個工作流程伺服器(wfserver)，並在兩部或多部電腦上散發。 如果您選擇此類型的架構，請根據Adobe Campaign存取權設定負載平衡器的連線模式。

要從Web訪問，請選擇負載平衡 **器模式** ，以限制連接時間。

如果透過Adobe Campaign主控台存取，請選 **擇雜湊****或嚴格ip** 模式。 例如，這可讓您維持rich client和伺服器之間的連線，並防止使用者作業在匯入或匯出作業期間中斷。

您可以選擇在特定電腦上強制執行工作流或工作流活動。 若要這麼做，您必須為相關工作流程或活動定義一或多個相關性。

1. 在欄位中輸入工作流程或活動的相關性，以建立工作流程或活動的 **[!UICONTROL Affinity]** 相關性。

   您可以自由選擇相似性名稱。 不過，請務必不要使用空格或標點符號。 如果您使用不同的伺服器，請指定不同的名稱。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉式清單包含先前使用的相關性。 它會隨著時間而以不同的輸入值完成。

1. 開啟 **nl6/conf/config-`<instance>.xml`**file。
1. 按如下方式修改與模組 **[!UICONTROL wfserver]** 匹配的行：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果您定義數個相似性，則必須以逗號分隔，不含空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   執行未定義相關性的工作流程時，必須使用名稱后面的逗號。

   如果您只想執行已定義相似性的工作流程，請勿在相關性清單的結尾加上逗號。 例如，按如下方式修改行：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自動重新啟動程式 {#automatic-process-restart}

依預設，不同的Adobe Campaign程式會每天早上6點（伺服器時間）自動重新啟動。

不過，您可以變更此設定。

要執行此操作，請轉到安 **裝的conf儲存庫中的serverConf.xml****** 檔案。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

在此檔案中配置的每個進程都具有 **processRestartTime** 屬性。 您可以修改此屬性的值，以根據需要調整每個進程的重新啟動時間。

>[!CAUTION]
>
>請勿刪除此屬性。 必須每天重新啟動所有進程。

## 限制可上載檔案 {#limiting-uploadable-files}

新的屬性 **uploadWhiteList** ，可讓您限制可在Adobe Campaign伺服器上上傳的檔案類型。

此屬性可在serverConf.xml文 **件的dataStore****元素中使用** 。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

此屬性的預設值為 **。+** ，並可讓您上傳任何檔案類型。

要限制可能的格式，必須用有效的java規則運算式替換屬性值。 您可以用逗號分隔數個值，以輸入數個值。

例如： **uploadWhiteList=&quot;&quot;。*.png、。*.jpg」** ，可讓您在伺服器上上傳PNG和JPG格式。 不接受其他格式。

>[!CAUTION]
>
>在Internet explorer中，完整的檔案路徑必須由規則運算式驗證。

## 代理連接配置 {#proxy-connection-configuration}

如果您需要透過Proxy將Campaign伺服器連線至外部（例如使用檔案傳輸工作流程活動），則需要透過命令來設定serverConf的proxyConfig區段。 可能有下列代理連接：HTTP、HTTPS、FTP、SFTP。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

>[!NOTE]
>
>不支援SOCKS代理。

使用下列命令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

通訊協定參數可以是「http」、「https」或「ftp」。

如果您要在與HTTP/HTTPS流量相同的埠上設定FTP，則可使用下列功能：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

只有當通訊協定參數為「ftp」時，才會使用「http」和「https」選項，並指出指定埠上的通道是透過HTTPS或HTTP執行。

如果您使用不同的埠來透過代理伺服器傳送FTP/SFTP和HTTP/HTTPS流量，則應設定「ftp」通訊協定參數。


例如：

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

然後輸入密碼。

HTTP連線在proxyHTTP參數中定義：

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS連線在proxyHTTPS參數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS連線是在proxyFTP參數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果您對數種連線類型使用相同的proxy，則只會定義proxyHTTP，並將useSingleProxy設為&quot;1&quot;或&quot;true&quot;。

如果您有內部連線，而且該連線應經由proxy，請在override參數中新增。

如果您想暫時停用Proxy連線，請將啟用的參數設為&quot;false&quot;或&quot;0&quot;。
