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
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 2%

---

# 開始使用Campaign伺服器組態{#gs-campaign-server-config}

本章詳細說明可根據您的需求和環境特定性執行的伺服器端配置。

## 限制

這些程式僅限於&#x200B;**內部部署**/**混合**&#x200B;部署，並需要管理權限。

對於&#x200B;**托管的**&#x200B;部署，伺服器端設定只能由Adobe設定。 不過，您可以在[促銷活動控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html)中設定某些設定，例如IP允許清單管理或URL權限。 [進一步瞭解](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/control-panel-home.html)
* [託管模式](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署和托管能力矩陣](../../installation/using/capability-matrix.md)

## 配置檔案

Campaign Classic配置檔案儲存在Adobe Campaign安裝資料夾的&#x200B;**conf**&#x200B;資料夾中。 配置分佈在兩個檔案上：

* **serverConf.xml**:所有實例的常規配置。此檔案結合了Adobe Campaign伺服器的技術參數：這些會由所有例項共用。 以下詳細說明了其中一些參數。 此[部分](../../installation/using/the-server-configuration-file.md)中列出的不同節點和參數。
* **config-`<instance>`.xml** (其中 **** instance是實例的名稱):實例的特定配置。如果您在多個實例之間共用伺服器，請在其相關檔案中輸入每個實例的特定參數。

## 配置範圍

根據您的需求和設定來設定或調整促銷活動伺服器。 您可以：

* 保全[內部識別碼](#internal-identifier)
* 啟用[促銷活動進程](#enabling-processes)
* 設定[URL權限](url-permissions.md)
* 定義[安全區](security-zones.md)
* 配置[Tomcat設定](configure-tomcat.md)
* 自訂[傳送參數](configure-delivery-settings.md)
* 定義[動態頁面安全性和中繼](#dynamic-page-security-and-relays)
* 限制[允許的外部命令清單](#restricting-authorized-external-commands)
* 設定[冗餘追蹤](#redundant-tracking)
* 管理[高可用性和工作流相關性](#high-availability-workflows-and-affinities)
* 配置檔案管理- [瞭解詳情](file-res-management.md)
   * 限制上傳檔案格式
   * 啟用對公共資源的訪問
   * 配置代理連接
* [自動重新啟動程式](#automatic-process-restart)


## 內部識別碼{#internal-identifier}

**internal**&#x200B;識別碼是用於安裝、管理和維護的技術登入。 此登入不與例項關聯。

使用此登錄連接的操作員將擁有所有實例的所有權限。 如果是新安裝，此登錄將沒有密碼。 您必須手動定義此密碼。

使用下列命令：

```
nlserver config -internalpassword
```

接著會顯示下列資訊。 輸入並確認密碼：

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## 啟用進程{#enabling-processes}

通過&#x200B;**config-default.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**&#x200B;檔案啟用（和禁用）伺服器上的Adobe Campaign進程。

要對這些檔案應用更改，如果啟動了Adobe Campaign服務，則必須運行&#x200B;**nlserver config -reload**&#x200B;命令。

有兩種流程：多執行個體和單一執行個體。

* **多實例**:所有例項都會啟動單一程式。**web**、**syslogd**&#x200B;和&#x200B;**trackinglogd**&#x200B;進程就是這樣。

   可從&#x200B;**config-default.xml**&#x200B;檔案設定啟用。

   聲明Adobe Campaign伺服器以訪問客戶端控制台和重定向（跟蹤）:

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在此示例中，在Linux中使用&#x200B;**vi**&#x200B;命令編輯檔案。 它可使用任何&#x200B;**.txt**&#x200B;或&#x200B;**.xml**&#x200B;編輯器進行編輯。

* **單實例**:每個實例(模組： **mta** wfserver **、** inMail **、** sm **** 和 **stat** Stat)。

   可使用實例的配置檔案配置啟用：

   ```
   config-<instance>.xml
   ```

   聲明要發送的伺服器、執行工作流實例和恢復彈回郵件：

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**促銷活動資料儲存**

您可以配置Adobe Campaign資料（日誌、下載、重定向等）的儲存目錄（**var**&#x200B;目錄）。 若要這麼做，請使用&#x200B;**XTK_VAR_DIR**&#x200B;系統變數：

* 在Windows中，在&#x200B;**XTK_VAR_DIR**&#x200B;系統變數中指定以下值

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，轉到&#x200B;**customer.sh**&#x200B;檔案並指明：**匯出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   有關詳細資訊，請參閱[個性化參數](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。


## 動態頁面安全性和中繼{#dynamic-page-security-and-relays}

預設情況下，所有動態頁都自動與啟動Web模組的電腦的&#x200B;**local** Tomcat伺服器相關。 此配置在&#x200B;**ServerConf.xml**&#x200B;檔案的查詢中繼配置的&#x200B;**`<url>`**&#x200B;部分中輸入。

您可以在&#x200B;**remote**&#x200B;伺服器上中繼動態頁的執行；如果未在電腦上激活Web模組。 要執行此操作，必須將&#x200B;**localhost**&#x200B;替換為遠程電腦的名稱，以用於JSP和JSSP、Web應用程式、報告和字串。

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

### 管理HTTP標題{#managing-http-headers}

依預設，不會中繼所有HTTP標題。 您可以在中繼傳送的回覆中新增特定標題。 操作步驟：

1. 轉至&#x200B;**serverConf.xml**&#x200B;檔案。
1. 在&#x200B;**`<relay>`**&#x200B;節點中，轉至中繼HTTP標頭清單。
1. 新增&#x200B;**`<responseheader>`**&#x200B;元素，其中包含下列屬性：

   * **名稱**:標題名稱
   * **值**:值名稱。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制授權的外部命令{#restricting-authorized-external-commands}

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


## 冗餘跟蹤{#redundant-tracking}

當使用多部伺服器進行重新導向時，它們必須能夠透過SOAP呼叫彼此通訊，才能共用要重新導向之URL的資訊。 在發送啟動時，可能並非所有重定向伺服器都可用；因此，他們可能沒有相同程度的資訊。

>[!NOTE]
>
>使用標準或企業架構時，主應用程式伺服器必須獲得授權，才能在每部電腦上傳追蹤資訊。

冗餘伺服器的URL必須通過&#x200B;**serverConf.xml**&#x200B;檔案在重定向配置中指定。

**範例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf**&#x200B;屬性是可選的（預設為空），並允許您僅在結果為true時啟用連接。 這可讓您在所有重新導向伺服器上取得相同的組態。

要獲取電腦的主機名，請運行以下命令：**hostname -s**。



## 高可用性工作流程和相關性{#high-availability-workflows-and-affinities}

您可以設定數個工作流程伺服器(wfserver)，並在兩部或多部電腦上散發。 如果您選擇此類型的體系結構，請根據Adobe Campaign訪問配置負載平衡器的連接模式。

要從Web訪問，請選擇&#x200B;**負載平衡器**&#x200B;模式以限制連接時間。

如果通過Adobe Campaign控制台訪問，請選擇&#x200B;**hash**&#x200B;或&#x200B;**嚴格ip**&#x200B;模式。 例如，這可讓您維持rich client和伺服器之間的連線，並防止使用者作業在匯入或匯出作業期間中斷。

您可以選擇在特定電腦上強制執行工作流或工作流活動。 若要這麼做，您必須為相關工作流程或活動定義一或多個相關性。

1. 在&#x200B;**[!UICONTROL Affinity]**&#x200B;欄位中輸入工作流程或活動的相關性，以建立工作流程或活動的相關性。

   您可以選擇任何相似性名稱，但請確定您不使用空格或標點符號。 如果您使用不同的伺服器，請指定不同的名稱。

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

## 自動重新啟動{#automatic-process-restart}

預設情況下，不同的Adobe Campaign進程每天早上6點（伺服器時間）自動重新啟動。

不過，您可以變更此設定。

要執行此操作，請轉至安裝&#x200B;**conf**&#x200B;儲存庫中的&#x200B;**serverConf.xml**&#x200B;檔案。

在此檔案中配置的每個進程都具有&#x200B;**processRestartTime**&#x200B;屬性。 您可以修改此屬性的值，以根據需要調整每個進程的重新啟動時間。

>[!IMPORTANT]
>
>請勿刪除此屬性。 必須每天重新啟動所有進程。
