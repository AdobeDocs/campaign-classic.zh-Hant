---
solution: Campaign Classic
product: campaign
title: 設定 Campaign 伺服器
description: 設定 Campaign 伺服器
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 6%

---

# 設定 Campaign 伺服器{#configuring-campaign-server}

下節詳細說明可根據您的需求和環境特性執行的伺服器端組態。

這些配置必須由管理員和&#x200B;**On-premise**&#x200B;代管模型執行。

對於&#x200B;**Hosted**&#x200B;部署，伺服器端設定只能由Adobe設定。 不過，您可以在「控制面板」中設定某些設定（例如，IPallowlist管理或URL權限）。

>[!NOTE]
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本章節](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
>
>請注意，您的實例必須裝載在AWS上，並使用最新的[Gold Standard](../../rn/using/gs-overview.md)組建版本或[最新的GA組建版本(21.1)](../../rn/using/latest-release.md)進行升級。 瞭解如何在[本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本。 要檢查您的實例是否托管在AWS上，請遵循本頁[中詳細介紹的步驟。](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/control-panel-home.html)
* [託管模式](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署和托管能力矩陣](../../installation/using/capability-matrix.md)
* [混合型和代管型配置步驟](../../installation/using/hosting-models.md)

Campaign Classic配置檔案儲存在Adobe Campaign安裝資料夾的&#x200B;**conf**&#x200B;資料夾中。 配置分佈在兩個檔案上：

* **serverConf.xml**:所有實例的常規配置。此檔案結合了Adobe Campaign伺服器的技術參數：這些會由所有例項共用。 以下詳細說明了其中一些參數。 此[部分](../../installation/using/the-server-configuration-file.md)中列出的不同節點和參數。
* **config-`<instance>`.xml** (其中 **** instance是實例的名稱):實例的特定配置。如果您在多個實例之間共用伺服器，請在其相關檔案中輸入每個實例的特定參數。

## 配置Tomcat {#configuring-tomcat}

### Tomcat {#default-port-for-tomcat}的預設埠

當Tomcat伺服器的8080偵聽埠已忙於配置所需的其他應用程式時，您需要將8080埠替換為免費埠（例如8090）。 要更改它，請編輯保存在Adobe Campaign安裝資料夾&#x200B;**/tomcat-8/conf**&#x200B;目錄中的&#x200B;**server.xml**&#x200B;檔案。

然後修改JSP中繼頁的埠。 為此，請更改保存在Adobe Campaign安裝目錄&#x200B;**/conf**&#x200B;目錄中的&#x200B;**serverConf.xml**&#x200B;檔案。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### 映射Tomcat {#mapping-a-folder-in-tomcat}中的資料夾

要定義客戶特定設定，可以在&#x200B;**/tomcat-8/conf**&#x200B;資料夾中建立&#x200B;**user_contexts.xml**&#x200B;檔案，該檔案還包含&#x200B;**contexts.xml**&#x200B;檔案。

此檔案將包含下列類型的資訊：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可在伺服器端重制此作業。

## 個人化傳送參數{#personalizing-delivery-parameters}

傳送參數在&#x200B;**serverConf.xml**&#x200B;配置檔案中定義。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

[Campaign伺服器組態](../../installation/using/campaign-server-configuration.md)中詳細說明一般伺服器組態和指令。

您也可以根據您的需求和設定執行下列設定。

### SMTP中繼{#smtp-relay}

MTA模組用作SMTP廣播（埠25）的本地郵件傳輸代理。

但是，如果安全策略要求，則可以將其替換為中繼伺服器。 在這種情況下，全局吞吐量將是中繼吞吐量(如果中繼伺服器吞吐量低於Adobe Campaign吞吐量)。

在這種情況下，通過在&#x200B;**`<relay>`**&#x200B;部分中配置SMTP伺服器來設定這些參數。 必須指定用於傳輸郵件及其關聯埠的SMTP伺服器的IP地址（或主機）（預設為25）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>此操作模式對傳送帶來嚴重限制，因為由於中繼伺服器的固有效能（延遲、頻寬……），它可大大降低吞吐量。 此外，限定同步傳送錯誤（通過分析SMTP通信量檢測到）的能力將受到限制，如果中繼伺服器不可用，則無法發送。

### MTA子進程{#mta-child-processes}

可以根據伺服器的CPU功率和可用網路資源來控制子進程（預設情況下為maxSpareServers 2）的數量，以優化廣播效能。 此配置將在每台電腦的MTA配置的&#x200B;**`<master>`**&#x200B;部分中進行。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另請參閱[電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization)。

### 使用相關性{#managing-outbound-smtp-traffic-with-affinities}管理出站SMTP通信

>[!IMPORTANT]
>
>相關性配置需要從一個伺服器到另一個伺服器之間保持一致。 我們建議您與Adobe聯絡以進行親和性配置，因為所有執行MTA的應用程式伺服器上應複製組態變更。

您可以通過具有IP地址的相關性來改進出站SMTP通信。

若要這麼做，請套用下列步驟：

1. 在&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**`<ipaffinity>`**&#x200B;區段中輸入相關性。

   一個相似性可以有數個不同的名稱：若要分隔，請使用&#x200B;**;**&#x200B;字元。

   範例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   要查看相關參數，請參閱&#x200B;**serverConf.xml**&#x200B;檔案。

1. 若要在下拉式清單中啟用相似性選擇，您需要在&#x200B;**IPAffinity**&#x200B;列舉中新增相似性名稱。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >[本檔案](../../platform/using/managing-enumerations.md)中詳述了枚舉。

   然後，您可以選取要使用的相似性，如下所示：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您也可以參考[傳送伺服器組態](../../installation/using/email-deliverability.md#delivery-server-configuration)。

## URL 權限{#url-permissions}

可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。這些是可讓您的執行個體正常運作的 URL。

依預設，執行個體不得連線到外部 URL。不過，您可以將一些外部URL新增至授權URL的清單，讓您的例項可以連線至這些URL。 這可讓您將 Campaign 執行個體連結到外部系統，例如 SFTP 伺服器或網站，以啟用檔案和/或資料傳輸。

新增 URL 後，執行個體的設定檔案 (serverConf.xml) 便會參照該 URL。

它們可讓您管理URL權限的方式視您的代管模型而定：

* **** Hybridor **內部部署**:將允許的URL新增至 **serverConf.xml檔案**。詳細資訊請參閱以下章節。
* **代管**:新增URL以允許透過「控 **制面板」**。如需詳細資訊，請參閱[專屬文件](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html)。

   >[!NOTE]
   >
   >所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本章節](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)中。
   >
   >請注意，您的實例必須裝載在AWS上，並使用最新的[Gold Standard](../../rn/using/gs-overview.md)構建版本進行升級。 瞭解如何在[本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本。 要檢查您的實例是否托管在AWS上，請遵循本頁[中詳細介紹的步驟。](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)

使用&#x200B;**Hybrid**&#x200B;和&#x200B;**On-premise**&#x200B;代管模型時，管理員需要在&#x200B;**serverConf.xml**&#x200B;檔案中參考新的&#x200B;**urlPermission**。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

存在三種連接保護模式：

* **阻止**:不屬於允許清單的所有URL都被阻止，並返回錯誤消息。這是postupgrade之後的預設模式。
* **權限**:允許所有不屬於允許清單的URL。
* **警告**:允許所有不屬於允許清單的URL，但JS解釋器會發出警告，以便管理員收集這些URL。此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>根據預設，新客戶的客戶端使用&#x200B;**封鎖模式**。 如果他們需要允許新的URL，則應聯繫其管理員以將其添加到allowlist。
>
>來自移轉的現有客戶可使用&#x200B;**警告模式**&#x200B;一段時間。 同時，他們需要在授權URL之前分析出站流量。 定義授權URL的清單後，應聯絡其管理員，將URL新增至allowlist並啟動&#x200B;**封鎖模式**。

## 動態頁面安全性和中繼{#dynamic-page-security-and-relays}

預設情況下，所有動態頁都自動與啟動Web模組的電腦的&#x200B;**local** Tomcat伺服器相關。 此配置在&#x200B;**ServerConf.xml**&#x200B;檔案的查詢中繼配置的&#x200B;**`<url>`**&#x200B;部分中輸入。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

在&#x200B;**remote**&#x200B;伺服器上中繼動態頁的執行；如果未在電腦上激活Web模組。 要執行此操作，必須將&#x200B;**localhost**&#x200B;替換為遠程電腦的名稱，以用於JSP和JSSP、Web應用程式、報告和字串。

有關各種可用參數的詳細資訊，請參閱&#x200B;**serverConf.xml**&#x200B;配置檔案。

對於JSP頁，預設配置為：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用以下JSP頁：

* /nl/jsp/**soaprouter.jsp**:用戶端主控台與網站服務連線(SOAP API)、
* /nl/jsp/**m.jsp**:鏡像頁面，
* /nl/jsp/**logon.jsp**:基於Web訪問報告和客戶端控制台的部署，
* /nl/jsp/**s.jsp**:使用病毒式行銷（贊助和社交網路）。

「行動應用程式頻道」使用的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**範例:**

可以防止客戶機從外部連接。 為此，只需限制&#x200B;**soaprouter.jsp**&#x200B;的執行，並僅授權執行鏡像頁、病毒式連結、Web表單和公共資源。

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

在此示例中，**`<IP_addresses>`**&#x200B;值與授權使用此掩碼的中繼模組的IP地址清單（由comas分隔）一致。

>[!NOTE]
>
>值應根據您的配置和網路限制進行調整，尤其是如果已為您的安裝開發了特定配置。

## 限制授權的外部命令{#restricting-authorized-external-commands}

>[!NOTE]
>
>只有內部部署安裝才需要以下配置。

從build 8780開始，技術管理員可以限制可在Adobe Campaign使用的授權外部命令清單。

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

>[!IMPORTANT]
>
>這份清單並非完整無遺。

在伺服器配置檔案的&#x200B;**exec**&#x200B;節點中，您需要引用&#x200B;**blickstFile**&#x200B;屬性中先前建立的檔案。

**僅適用於Linux**:在伺服器配置檔案中，我們重新命令您指定專用於執行外部命令的用戶，以增強您的安全配置。此用戶設定在配置檔案的&#x200B;**exec**&#x200B;節點中。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

>[!NOTE]
>
>如果未指定用戶，則在Adobe Campaign實例的用戶上下文中執行所有命令。 使用者必須與執行Adobe Campaign的使用者不同。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

該用戶需要添加到「Neolane」Adobe Campaign運算子的用戶清單中。

>[!IMPORTANT]
>
>您不應使用自訂sudo。 系統上需要安裝標準Sudo。

## 管理HTTP標頭{#managing-http-headers}

依預設，不會中繼所有HTTP標題。 您可以在中繼傳送的回覆中新增特定標題。 操作步驟：

1. 轉至&#x200B;**serverConf.xml**&#x200B;檔案。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。
1. 在&#x200B;**`<relay>`**&#x200B;節點中，轉至中繼HTTP標頭清單。
1. 新增&#x200B;**`<responseheader>`**&#x200B;元素，其中包含下列屬性：

   * **名稱**:標題名稱
   * **值**:值名稱。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 冗餘跟蹤{#redundant-tracking}

當使用多部伺服器進行重新導向時，它們必須能夠透過SOAP呼叫彼此通訊，才能共用要重新導向之URL的資訊。 在發送啟動時，可能並非所有重定向伺服器都可用；因此，他們可能沒有相同程度的資訊。

>[!NOTE]
>
>使用標準或企業架構時，主應用程式伺服器必須獲得授權，才能在每部電腦上傳追蹤資訊。

冗餘伺服器的URL必須通過&#x200B;**serverConf.xml**&#x200B;檔案在重定向配置中指定。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

**範例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf**&#x200B;屬性是可選的（預設為空），並允許您僅在結果為true時啟用連接；這可讓您在所有重新導向伺服器上取得相同的組態。

要獲取電腦的主機名，請運行以下命令：**hostname -s**。

## 管理公共資源{#managing-public-resources}

公共資源在[管理公共資源](../../installation/using/deploying-an-instance.md#managing-public-resources)中顯示。

它們儲存在Adobe Campaign安裝目錄的&#x200B;**/var/res/instance**&#x200B;目錄中。

相符的URL為：**http://server/res/instance**，其中&#x200B;**instance**&#x200B;是追蹤例項的名稱。

通過向&#x200B;**conf-`<instance>`.xml**&#x200B;檔案添加節點，可以指定另一個目錄，以配置伺服器上的儲存。 這表示新增下列行：

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

## 高可用性工作流程和相關性{#high-availability-workflows-and-affinities}

您可以設定數個工作流程伺服器(wfserver)，並在兩部或多部電腦上散發。 如果您選擇此類型的體系結構，請根據Adobe Campaign訪問配置負載平衡器的連接模式。

要從Web訪問，請選擇&#x200B;**負載平衡器**&#x200B;模式以限制連接時間。

如果通過Adobe Campaign控制台訪問，請選擇&#x200B;**hash**&#x200B;或&#x200B;**嚴格ip**&#x200B;模式。 例如，這可讓您維持rich client和伺服器之間的連線，並防止使用者作業在匯入或匯出作業期間中斷。

您可以選擇在特定電腦上強制執行工作流或工作流活動。 若要這麼做，您必須為相關工作流程或活動定義一或多個相關性。

1. 在&#x200B;**[!UICONTROL Affinity]**&#x200B;欄位中輸入工作流程或活動的相關性，以建立工作流程或活動的相關性。

   您可以自由選擇相似性名稱。 不過，請務必不要使用空格或標點符號。 如果您使用不同的伺服器，請指定不同的名稱。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉式清單包含先前使用的相關性。 它會隨著時間而以不同的輸入值完成。

1. 開啟&#x200B;**nl6/conf/config-`<instance>.xml`**&#x200B;檔案。
1. 按如下方式修改與&#x200B;**[!UICONTROL wfserver]**&#x200B;模組匹配的行：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果您定義數個相似性，則必須以逗號分隔，不含任何空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   執行未定義相關性的工作流程時，必須使用名稱后面的逗號。

   如果您只想執行已定義相似性的工作流程，請勿在相關性清單的結尾加上逗號。 例如，按如下方式修改行：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自動進程重新啟動{#automatic-process-restart}

預設情況下，不同的Adobe Campaign進程每天早上6點（伺服器時間）自動重新啟動。

不過，您可以變更此設定。

要執行此操作，請轉至安裝&#x200B;**conf**&#x200B;儲存庫中的&#x200B;**serverConf.xml**&#x200B;檔案。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

在此檔案中配置的每個進程都具有&#x200B;**processRestartTime**&#x200B;屬性。 您可以修改此屬性的值，以根據需要調整每個進程的重新啟動時間。

>[!IMPORTANT]
>
>請勿刪除此屬性。 必須每天重新啟動所有進程。

## 限制可上載檔案{#limiting-uploadable-files}

新屬性&#x200B;**uploadWhiteList**&#x200B;可讓您限制可在Adobe Campaign伺服器上上傳的檔案類型。

此屬性可在&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**dataStore**&#x200B;元素中使用。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

此屬性的預設值為&#x200B;**。+**，並可讓您上傳任何檔案類型。

要限制可能的格式，必須用有效的java規則運算式替換屬性值。 您可以用逗號分隔數個值，以輸入數個值。

例如：**uploadWhiteList=&quot;&quot;。*.png、。*.jpg&quot;**&#x200B;可讓您在伺服器上上傳PNG和JPG格式。 不接受其他格式。

>[!IMPORTANT]
>
>在Internet Explorer中，完整的檔案路徑必須由規則運算式驗證。

## 代理連接配置{#proxy-connection-configuration}

例如，您可以使用&#x200B;**檔案傳輸**&#x200B;工作流程活動，將Campaign伺服器連接至外部系統。 要實現此目的，您需要通過特定命令配置&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**proxyConfig**&#x200B;部分。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

可能有下列代理連接：HTTP、HTTPS、FTP、SFTP。 請注意，從20.2促銷活動發行開始，HTTP和HTTPS通訊協定參數已不再提供&#x200B;****。 這些參數仍在下面提及，因為它們在以前的版本中仍然可用——包括9032。

>[!CAUTION]
>
>僅支援基本驗證模式。 不支援NTLM身份驗證。
>
>不支援SOCKS代理。


您可以使用下列命令：

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
