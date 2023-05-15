---
product: campaign
title: 設定 Campaign 伺服器
description: 設定 Campaign 伺服器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 2%

---

# 開始使用Campaign伺服器設定{#gs-campaign-server-config}



本章詳細說明可執行以符合您的需求和環境特異性的伺服器端配置。

## 限制

這些程式僅限於 **內部部署**/**混合** 部署及需要管理權限。

針對 **托管** 部署，伺服器端設定僅能由Adobe設定。 不過，有些設定可在內設定 [Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)，例如IP允許清單管理或URL權限。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署與托管功能矩陣](../../installation/using/capability-matrix.md)

## 組態檔

Campaign Classic組態檔儲存在 **conf** Adobe Campaign安裝資料夾的資料夾。 設定分佈在兩個檔案上：

* **serverConf.xml**:所有執行個體的一般設定。 此檔案結合了Adobe Campaign伺服器的技術參數：這些會由所有執行個體共用。 以下詳細說明其中一些參數。 此處列出的不同節點和參數 [節](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (其中 **執行個體** 是例項的名稱):執行個體的特定設定。 如果您在多個執行個體之間共用伺服器，請在其相關檔案中輸入每個執行個體專屬的參數。

## 配置範圍

根據您的需求和配置，設定或調整Campaign伺服器。 您可以：

* 保護 [內部識別碼](#internal-identifier)
* 啟用 [行銷活動程式](#enabling-processes)
* 設定 [URL權限](url-permissions.md)
* 定義 [安全區域](security-zones.md)
* 設定 [Tomcat設定](configure-tomcat.md)
* 自訂 [傳遞參數](configure-delivery-settings.md)
* 定義 [動態頁面安全性和中繼](#dynamic-page-security-and-relays)
* 限制 [允許的外部命令](#restricting-authorized-external-commands)
* 設定 [冗餘跟蹤](#redundant-tracking)
* 管理 [高可用性和工作流程相關性](#high-availability-workflows-and-affinities)
* 配置檔案管理 —  [深入了解](file-res-management.md)
   * 限制上傳檔案格式
   * 啟用對公共資源的訪問
   * 配置代理連接
* [自動處理重新啟動](#automatic-process-restart)


## 內部識別碼 {#internal-identifier}

此 **內部** 識別碼是用於安裝、管理和維護目的的技術登入。 此登入不與執行個體相關聯。

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

## 啟用流程 {#enabling-processes}

伺服器上的Adobe Campaign程式會透過 **config-default.xml** 和 **`config-<instance>.xml`** 檔案。

若要將變更套用至這些檔案，如果已啟動Adobe Campaign服務，您必須執行 **nlserver配置 — reload** 命令。

有兩種流程：多執行個體和單一執行個體。

* **多執行個體**:所有執行個體都會啟動單一程式。 這是 **web**, **syslogd** 和 **trackinglogd** 程式。

   可透過 **config-default.xml** 檔案。

   宣告Adobe Campaign伺服器以存取用戶端主控台和進行重新導向（追蹤）:

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在此範例中，使用 **vi** 命令。 可使用 **.txt** 或 **.xml** 編輯器。

* **單實例**:每個實例（模組）啟動一個進程： **mta**, **wfserver**, **inMail**, **sms** 和 **stat**)。

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

您可以配置儲存目錄(**var** 目錄)（記錄、下載、重新導向等）。 若要這麼做，請使用 **XTK_VAR_DIR** 系統變數：

* 在Windows中，於 **XTK_VAR_DIR** 系統變數

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，前往 **customer.sh** 檔案並指出： **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

   有關詳細資訊，請參閱 [個人化參數](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## 動態頁面安全性和中繼 {#dynamic-page-security-and-relays}

依預設，所有動態頁面都會自動與 **本地** 啟動其Web模組的電腦的Tomcat伺服器。 此設定是在 **`<url>`** 查詢中繼配置的節 **ServerConf.xml** 檔案。

您可以在 **遠端** 伺服器；如果電腦上未激活Web模組。 若要這麼做，您必須取代 **localhost** 以JSP和JSSP、Web應用程式、報告和字串的遠程電腦的名稱。

有關各種可用參數的詳細資訊，請參閱 **serverConf.xml** 設定檔。

對於JSP頁，預設配置為：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用下列JSP頁：

* /nl/jsp/**soapruter.jsp**:用戶端主控台和網站服務連線(SOAP API),
* /nl/jsp/**m.jsp**:鏡像頁面，
* /nl/jsp/**logon.jsp**:基於Web的對報告和客戶端控制台的部署的訪問
* /nl/jsp/**s.jsp** :使用病毒式行銷（贊助和社交網路）。

「行動應用程式管道」使用的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**範例:**

可以防止客戶端電腦從外部連接。 若要這麼做，只需限制 **soapruter.jsp** 並僅授權執行鏡像頁面、病毒式連結、網路表單和公共資源。

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

在此範例中， **`<IP_addresses>`** 值與授權為此掩碼使用中繼模組的IP地址清單一致（由comas分隔）。

>[!NOTE]
>
>值應根據您的配置和網路限制進行調整，尤其是如果已為您的安裝開發了特定配置。

### 管理HTTP標題 {#managing-http-headers}

依預設，不會中繼所有HTTP標題。 您可以在中繼傳送的回覆中新增特定標題。 操作步驟：

1. 前往 **serverConf.xml** 檔案。
1. 在 **`<relay>`** 節點，轉至中繼HTTP標頭清單。
1. 新增 **`<responseheader>`** 元素（具有下列屬性）:

   * **名稱**:標題名稱
   * **value**:值名稱。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制授權的外部命令 {#restricting-authorized-external-commands}

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

在 **執行** 節點時，您需要參考 **blacklistFile** 屬性。

**僅適用於Linux**:在伺服器配置檔案中，建議您指定專用於執行外部命令的用戶以增強您的安全配置。 此使用者設定於 **執行** 配置檔案的節點。 中所有可用的參數 **serverConf.xml** 列於此 [節](../../installation/using/the-server-configuration-file.md).

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


## 冗餘跟蹤 {#redundant-tracking}

當使用多個伺服器進行重新導向時，它們必須能夠通過SOAP呼叫彼此通信，以便共用要重新導向的URL中的資訊。 在發送啟動時，可能並非所有重定向伺服器都可用；因此，他們可能沒有相同層級的資訊。

>[!NOTE]
>
>使用標準或企業架構時，主應用程式伺服器必須獲得授權，才能上傳每台電腦的追蹤資訊。

冗餘伺服器的URL必須在重定向配置中指定，通過 **serverConf.xml** 檔案。

**範例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

此 **enableIf** 屬性為選用（預設為空），且僅允許在結果為true時啟用連線。 這可讓您在所有重新導向伺服器上取得相同的設定。

要獲取電腦的主機名，請運行以下命令： **主機名 — s**.



## 高可用性工作流程和相關性 {#high-availability-workflows-and-affinities}

您可以配置多個工作流伺服器(wfserver)，並在兩台或多台電腦上分發它們。 如果您選擇此類型的架構，請根據Adobe Campaign存取權設定負載平衡器的連線模式。

若要從網路存取，請選取 **負載平衡器** 模式來限制連線時間。

如果透過Adobe Campaign主控台存取，請選擇 **雜湊** 或 **黏著ip** 模式。 這可讓您維護rich用戶端與伺服器之間的連線，並防止在匯入或匯出作業期間中斷使用者工作階段。

您可以選擇在特定電腦上強制執行工作流程或工作流程活動。 要執行此操作，您必須為相關工作流程或活動定義一或多個相關性。

1. 在 **[!UICONTROL Affinity]** 欄位。

   您可以選擇任何相關性名稱，但請確定您不使用空格或標點符號。 如果您使用不同的伺服器，請指定不同的名稱。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉式清單包含先前使用的相關性。 會隨著時間而以不同的輸入值完成。

1. 開啟 **nl6/conf/config-`<instance>.xml`** 檔案。
1. 修改符合 **[!UICONTROL wfserver]** 模組如下：

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

## 自動重新啟動 {#automatic-process-restart}

依預設，不同的Adobe Campaign程式會每天早上6:00（伺服器時間）自動重新啟動。

不過，您可以變更此設定。

若要這麼做，請前往 **serverConf.xml** 檔案，位於 **conf** 儲存庫。

此檔案中配置的每個進程都有 **processRestartTime** 屬性。 您可以修改此屬性的值，以根據您的需求調整每個程式的重新啟動時間。

>[!IMPORTANT]
>
>請勿刪除此屬性。 必須每天重新啟動所有進程。
