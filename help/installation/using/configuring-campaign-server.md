---
product: campaign
title: 設定 Campaign 伺服器
description: 設定 Campaign 伺服器
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 2%

---

# 開始使用Campaign伺服器設定{#gs-campaign-server-config}

本章詳細說明可執行以符合您的需求和環境特異性的伺服器端配置。

## 限制

這些程式限制為&#x200B;**內部部署**/**混合**&#x200B;部署，並需要管理權限。

對於&#x200B;**托管**&#x200B;部署，伺服器端設定僅能由Adobe設定。 不過，有些設定可在[促銷活動控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)內設定，例如IP允許清單管理或URL權限。 [瞭解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署與托管功能矩陣](../../installation/using/capability-matrix.md)

## 組態檔

Campaign Classic配置檔案儲存在Adobe Campaign安裝資料夾的&#x200B;**conf**&#x200B;資料夾中。 設定分佈在兩個檔案上：

* **serverConf.xml**:所有執行個體的一般設定。此檔案結合了Adobe Campaign伺服器的技術參數：這些會由所有執行個體共用。 以下詳細說明其中一些參數。 此[節](../../installation/using/the-server-configuration-file.md)中列出的不同節點和參數。
* **config-`<instance>`.xml** (其中 **** instance是執行個體的名稱):執行個體的特定設定。如果您在多個執行個體之間共用伺服器，請在其相關檔案中輸入每個執行個體專屬的參數。

## 配置範圍

根據您的需求和配置，設定或調整Campaign伺服器。 您可以：

* 保護[內部標識符](#internal-identifier)
* 啟用[促銷活動程式](#enabling-processes)
* 配置[URL權限](url-permissions.md)
* 定義[安全區域](security-zones.md)
* 配置[Tomcat設定](configure-tomcat.md)
* 自訂[傳送參數](configure-delivery-settings.md)
* 定義[動態頁面安全性並中繼](#dynamic-page-security-and-relays)
* 限制[允許的外部命令清單](#restricting-authorized-external-commands)
* 設定[冗餘跟蹤](#redundant-tracking)
* 管理[高可用性和工作流相關性](#high-availability-workflows-and-affinities)
* 配置檔案管理 — [了解更多](file-res-management.md)
   * 限制上傳檔案格式
   * 啟用對公共資源的訪問
   * 配置代理連接
* [自動處理重新啟動](#automatic-process-restart)


## 內部標識符{#internal-identifier}

**internal**&#x200B;標識符是用於安裝、管理和維護目的的技術登錄。 此登入不與執行個體相關聯。

使用此登入連結的運算子將擁有所有執行個體的所有權限。 若是新安裝，此登入將沒有密碼。 您必須手動定義此密碼。

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

伺服器上的Adobe Campaign程式會透過&#x200B;**config-default.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**&#x200B;檔案啟用（和停用）。

若要將變更套用至這些檔案，如果Adobe Campaign服務已啟動，您必須執行&#x200B;**nlserver config -reload**&#x200B;命令。

有兩種流程：多執行個體和單一執行個體。

* **多執行個體**:所有執行個體都會啟動單一程式。**web**、**syslogd**&#x200B;和&#x200B;**trackinglogd**&#x200B;進程的情況。

   可從&#x200B;**config-default.xml**&#x200B;檔案配置啟用。

   宣告Adobe Campaign伺服器以存取用戶端主控台和進行重新導向（追蹤）:

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在此示例中，在Linux中使用&#x200B;**vi**&#x200B;命令編輯檔案。 可以使用任何&#x200B;**.txt**&#x200B;或&#x200B;**.xml**&#x200B;編輯器來編輯它。

* **單實例**:每個實例（模組）啟動一個進程： **mta**、 **wfserver**、 **inMail**、 **** sms **和stat**)。

   可使用執行個體的設定檔案來設定啟用：

   ```
   config-<instance>.xml
   ```

   聲明伺服器以進行傳送、執行工作流實例和恢復退信：

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**行銷活動資料儲存**

您可以配置Adobe Campaign資料（日誌、下載、重定向等）的儲存目錄（**var**&#x200B;目錄）。 要執行此操作，請使用&#x200B;**XTK_VAR_DIR**&#x200B;系統變數：

* 在Windows中，在&#x200B;**XTK_VAR_DIR**&#x200B;系統變數中指出以下值

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，前往&#x200B;**customer.sh**&#x200B;檔案並指出：**匯出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   有關詳細資訊，請參閱[個人化參數](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。


## 動態頁面安全性和中繼{#dynamic-page-security-and-relays}

預設情況下，所有動態頁都自動與啟動Web模組的電腦的&#x200B;**local** Tomcat伺服器相關。 此配置在&#x200B;**ServerConf.xml**&#x200B;檔案的查詢中繼配置的&#x200B;**`<url>`**&#x200B;部分中輸入。

您可以在&#x200B;**remote**&#x200B;伺服器上中繼動態頁面的執行；如果電腦上未激活Web模組。 要執行此操作，必須將&#x200B;**localhost**&#x200B;替換為遠程電腦的名稱，以用於JSP和JSSP、Web應用程式、報告和字串。

有關各種可用參數的詳細資訊，請參閱&#x200B;**serverConf.xml**&#x200B;配置檔案。

對於JSP頁，預設配置為：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用下列JSP頁：

* /nl/jsp/**soaprouter.jsp**:用戶端主控台和網站服務連線(SOAP API),
* /nl/jsp/**m.jsp**:鏡像頁面，
* /nl/jsp/**logon**:基於Web的對報告和客戶端控制台的部署的訪問
* /nl/jsp/**s.jsp** :使用病毒式行銷（贊助和社交網路）。

「行動應用程式管道」使用的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**範例:**

可以防止客戶端電腦從外部連接。 要執行此操作，只需限制&#x200B;**soafprouter.jsp**&#x200B;的執行，並僅授權執行鏡像頁、病毒式連結、Web表單和公共資源。

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

在此示例中，**`<IP_addresses>`**&#x200B;值與授權為此掩碼使用中繼模組的IP地址清單（由comas分隔）一致。

>[!NOTE]
>
>值應根據您的配置和網路限制進行調整，尤其是如果已為您的安裝開發了特定配置。

### 管理HTTP標題{#managing-http-headers}

依預設，不會中繼所有HTTP標題。 您可以在中繼傳送的回覆中新增特定標題。 操作步驟：

1. 前往&#x200B;**serverConf.xml**&#x200B;檔案。
1. 在&#x200B;**`<relay>`**&#x200B;節點中，轉至中繼HTTP標頭清單。
1. 使用下列屬性新增&#x200B;**`<responseheader>`**&#x200B;元素：

   * **名稱**:標題名稱
   * **值**:值名稱。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制授權的外部命令{#restricting-authorized-external-commands}

從8780組建版本，技術管理員可限制可在Adobe Campaign中使用的授權外部命令清單。

要執行此操作，您需要建立一個文本檔案，其中包含您要阻止使用的命令清單，例如：

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
>這份清單並非詳盡無遺。

在伺服器配置檔案的&#x200B;**exec**&#x200B;節點中，您需要在&#x200B;**blacklistFile**&#x200B;屬性中引用以前建立的檔案。

**僅適用於Linux**:在伺服器配置檔案中，我們重新命令您指定專用於執行外部命令的用戶，以增強您的安全配置。此用戶設定在配置檔案的&#x200B;**exec**&#x200B;節點中。 **serverConf.xml**&#x200B;中所有可用的參數都列在此[節](../../installation/using/the-server-configuration-file.md)中。

>[!NOTE]
>
>如果未指定用戶，則所有命令都會在Adobe Campaign實例的用戶上下文中執行。 使用者必須與執行Adobe Campaign的使用者不同。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

需要將此使用者新增至&#39;neolane&#39; Adobe Campaign運算子的使用者清單。

>[!IMPORTANT]
>
>您不應使用自訂sudo。 需要在系統上安裝標準sudo。


## 冗餘跟蹤{#redundant-tracking}

當使用多個伺服器進行重新導向時，它們必須能夠通過SOAP呼叫彼此通信，以便共用要重新導向的URL中的資訊。 在發送啟動時，可能並非所有重定向伺服器都可用；因此，他們可能沒有相同層級的資訊。

>[!NOTE]
>
>使用標準或企業架構時，主應用程式伺服器必須獲得授權，才能上傳每台電腦的追蹤資訊。

必須在重定向配置中，通過&#x200B;**serverConf.xml**&#x200B;檔案指定冗餘伺服器的URL。

**範例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf**&#x200B;屬性為可選（預設為空），並且僅允許在結果為true時啟用連接。 這可讓您在所有重新導向伺服器上取得相同的設定。

要獲取電腦的主機名，請運行以下命令：**hostname -s**。



## 高可用性工作流程和相關性{#high-availability-workflows-and-affinities}

您可以配置多個工作流伺服器(wfserver)，並在兩台或多台電腦上分發它們。 如果您選擇此類型的架構，請根據Adobe Campaign存取權設定負載平衡器的連線模式。

要從Web訪問，請選擇&#x200B;**負載平衡器**&#x200B;模式以限制連接時間。

如果透過Adobe Campaign主控台存取，請選擇&#x200B;**雜湊**&#x200B;或&#x200B;**黏著ip**&#x200B;模式。 這可讓您維護rich用戶端與伺服器之間的連線，並防止在匯入或匯出作業期間中斷使用者工作階段。

您可以選擇在特定電腦上強制執行工作流程或工作流程活動。 要執行此操作，您必須為相關工作流程或活動定義一或多個相關性。

1. 在&#x200B;**[!UICONTROL Affinity]**&#x200B;欄位中輸入工作流程或活動的相關性，以建立這些相關性。

   您可以選擇任何相關性名稱，但請確定您不使用空格或標點符號。 如果您使用不同的伺服器，請指定不同的名稱。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉式清單包含先前使用的相關性。 會隨著時間而以不同的輸入值完成。

1. 開啟&#x200B;**nl6/conf/config-`<instance>.xml`**&#x200B;檔案。
1. 修改與&#x200B;**[!UICONTROL wfserver]**&#x200B;模組匹配的行，如下所示：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果您定義數個相似性，則必須以逗號區隔，不含任何空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   執行未定義相關性的工作流程時，必須使用名稱后面的逗號。

   如果您只想執行已定義相關性的工作流程，請勿在相關性清單的結尾加上逗號。 例如，修改行如下：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自動重新啟動{#automatic-process-restart}

依預設，不同的Adobe Campaign程式會每天早上6:00（伺服器時間）自動重新啟動。

不過，您可以變更此設定。

要執行此操作，請前往安裝之&#x200B;**conf**&#x200B;存放庫中的&#x200B;**serverConf.xml**&#x200B;檔案。

在此檔案中配置的每個進程都有&#x200B;**processRestartTime**&#x200B;屬性。 您可以修改此屬性的值，以根據您的需求調整每個程式的重新啟動時間。

>[!IMPORTANT]
>
>請勿刪除此屬性。 必須每天重新啟動所有進程。
