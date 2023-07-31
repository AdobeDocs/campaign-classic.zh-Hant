---
product: campaign
title: 設定 Campaign 伺服器
description: 設定 Campaign 伺服器
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1603'
ht-degree: 3%

---

# 開始使用Campaign伺服器設定{#gs-campaign-server-config}



本章詳細說明可以根據您的需求和環境特性執行的伺服器端設定。

## 限制

這些程式僅限於 **內部部署**/**混合式** 部署，並需要管理許可權。

的 **託管** 部署，伺服器端設定只能由Adobe設定。 不過，某些設定可以在中設定 [Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)，例如IP允許清單管理或URL許可權。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署和託管功能矩陣](../../installation/using/capability-matrix.md)

## 組態檔

Campaign Classic組態檔儲存在 **conf** Adobe Campaign安裝資料夾的資料夾。 此設定分為兩個檔案：

* **serverConf.xml**：所有執行個體的一般設定。 此檔案結合Adobe Campaign伺服器的技術引數：這些引數由所有執行個體共用。 其中一些引數的說明詳述如下。 此清單中列出的不同節點和引數 [區段](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (其中 **例項** 執行個體的名稱)：執行個體的特定設定。 如果您在多個執行個體之間共用伺服器，請在相關檔案中輸入每個執行個體專屬的引數。

## 設定範圍

根據您的需求和設定，設定或調整Campaign伺服器。 您可以：

* 保護 [內部識別碼](#internal-identifier)
* 啟用 [行銷活動程式](#enabling-processes)
* 設定 [URL許可權](url-permissions.md)
* 定義 [安全性區域](security-zones.md)
* 設定 [Tomcat設定](configure-tomcat.md)
* 自訂 [傳遞引數](configure-delivery-settings.md)
* 定義 [動態頁面安全性和轉送](#dynamic-page-security-and-relays)
* 限制清單 [允許的外部命令](#restricting-authorized-external-commands)
* 設定 [備援追蹤](#redundant-tracking)
* 管理 [高可用性與工作流程相關性](#high-availability-workflows-and-affinities)
* 設定檔案管理 —  [瞭解更多](file-res-management.md)
   * 限制上傳檔案格式
   * 啟用對公用資源的存取權
   * 設定代理伺服器連線
* [自動程式重新啟動](#automatic-process-restart)


## 內部識別碼 {#internal-identifier}

此 **內部** 識別碼是技術登入，用於安裝、管理和維護目的。 此登入未關聯到執行個體。

使用此登入連線的操作者將擁有所有執行個體的所有權利。 若是新的安裝，此登入將不會有密碼。 您必須手動定義此密碼。

使用以下命令：

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

## 啟用程式 {#enabling-processes}

伺服器上的Adobe Campaign程式可透過以下方式啟用（和停用）： **config-default.xml** 和 **`config-<instance>.xml`** 檔案。

若要套用變更至這些檔案，如果Adobe Campaign服務已啟動，您必須執行 **nlserver設定 — reload** 命令。

有兩種型別的程式：多執行個體和單一執行個體。

* **多例項**：所有執行個體都會啟動單一程式。 以下專案即是如此 **網頁**， **syslogd** 和 **trackinglogd** 程式。

  您可以從以下位置設定啟用： **config-default.xml** 檔案。

  宣告Adobe Campaign伺服器以存取使用者端主控台及進行重新導向（追蹤）：

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  在此範例中，使用編輯檔案 **vi** Linux中的命令。 您可以使用任何 **.txt** 或 **.xml** 編輯者。

* **單執行個體**：每個執行個體都會啟動一個程式(模組： **mta**， **wfserver**， **inMail**， **簡訊** 和 **stat**)。

  可使用執行個體的設定檔案來設定啟用：

  ```
  config-<instance>.xml
  ```

  宣告伺服器以進行傳送、執行工作流程例項及復原退回郵件：

  ```
  <mta autoStart="true" statServerAddress="localhost"/>
  <wfserver autoStart="true"/>  
  <inMail autoStart="true"/>
  <stat autoStart="true"/>
  ```

**Campaign資料儲存**

您可以設定儲存目錄(**變數** 目錄)，或Adobe Campaign資料（記錄、下載、重新導向等）。 若要這麼做，請使用 **XTK_VAR_DIR** 系統變數：

* 在Windows中，在 **XTK_VAR_DIR** 系統變數

  ```
  D:\log\AdobeCampaign
  ```

* 在Linux中，前往 **customer.sh** 檔案並指出： **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  有關詳細資訊，請參閱 [個人化引數](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## 動態頁面安全性和轉送 {#dynamic-page-security-and-relays}

依預設，所有動態頁面都會自動與 **本機** 已啟動Web模組之電腦的Tomcat伺服器。 此設定輸入於 **`<url>`** 「 」的查詢轉送設定的區段 **ServerConf.xml** 檔案。

您可在上轉送動態頁面的執行 **遠端** 伺服器；如果電腦未啟動Web模組。 若要這麼做，您必須取代 **localhost** 遠端電腦的名稱，適用於JSP和JSSP、Web應用程式、報表和字串。

如需各種可用引數的詳細資訊，請參閱 **serverConf.xml** 組態檔。

對於JSP頁面，預設組態為：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用下列JSP頁面：

* /nl/jsp/**soaprouter.jsp**：使用者端主控台和Web服務連線(SOAP API)、
* /nl/jsp/**m.jsp**：映象頁面，
* /nl/jsp/**logon.jsp**：以Web方式存取報表和部署使用者端主控台，
* /nl/jsp/**s.jsp** ：使用病毒式行銷（贊助和社交網路）。

用於行動應用程式通道的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**範例:**

可以防止使用者端電腦從外部連線。 若要這麼做，只需限制執行 **soaprouter.jsp** 且僅授權執行映象頁面、病毒式連結、網路表單和公共資源。

引數如下：

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

在此範例中， **`<IP_addresses>`** 值與授權為此遮罩使用轉送模組的IP位址清單（以逗號分隔）一致。

>[!NOTE]
>
>值應根據您的設定和網路限制進行調整，尤其是在已針對您的安裝開發特定設定時。

### 管理HTTP標頭 {#managing-http-headers}

依預設，不會轉送所有HTTP標頭。 您可以在轉送所傳送的回覆中新增特定標頭。 操作步驟：

1. 前往 **serverConf.xml** 檔案。
1. 在 **`<relay>`** 節點，前往轉送HTTP標頭的清單。
1. 新增 **`<responseheader>`** 元素具有以下屬性：

   * **名稱**：標頭名稱
   * **值**：值名稱。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制授權的外部命令 {#restricting-authorized-external-commands}

從建置8780開始，技術管理員可以限制可以在Adobe Campaign中使用的授權外部命令清單。

為此，您需要建立一個文字檔案，其中包含您想防止使用的命令清單，例如：

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
>此清單並非詳盡無遺。

在 **執行** 節點所建立的URL中，您需要參照先前在 **blacklistFile** 屬性。

**僅適用於Linux**：在伺服器設定檔案中，建議您指定專門執行外部命令的使用者，以增強您的安全性設定。 此使用者設定於 **執行** 設定檔的節點。 所有引數都可在 **serverConf.xml** 列於此 [區段](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>如果未指定使用者，則所有命令都會在Adobe Campaign執行個體的使用者內容中執行。 使用者必須與執行Adobe Campaign的使用者不同。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

需要將此使用者新增到「neolane」Adobe Campaign運運算元的使用者清單中。

>[!IMPORTANT]
>
>您不應使用自訂sudo。 系統需安裝標準sudo。


## 備援追蹤 {#redundant-tracking}

使用多個伺服器重新導向時，它們必須能夠透過SOAP呼叫彼此通訊，以便從要重新導向的URL共用資訊。 在傳遞啟動時，可能無法使用所有的重新導向伺服器，因此它們可能沒有相同的資訊層級。

>[!NOTE]
>
>使用標準或企業架構時，主要應用程式伺服器必須獲得授權，才能上傳每部電腦的追蹤資訊。

多餘伺服器的URL必須在重新導向設定中指定，透過 **serverConf.xml** 檔案。

**範例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

此 **enableIf** 屬性是選用專案（預設為空白），只有在結果為true時才允許您啟用連線。 這可讓您在所有重新導向伺服器上取得相同的設定。

若要取得電腦的主機名稱，請執行以下命令： **主機名稱 — s**.



## 高可用性工作流程與相關性 {#high-availability-workflows-and-affinities}

您可以設定數個工作流程伺服器(wfserver)，並在兩部或多部電腦上分配這些伺服器。 如果您選擇這種架構，請根據Adobe Campaign存取權設定負載平衡器的連線模式。

若要從網頁存取，請選取 **負載平衡器** 模式以限制連線時間。

如果透過Adobe Campaign主控台存取，請選擇 **雜湊** 或 **粘性ip** 模式。 這可讓您維護RTF使用者端與伺服器之間的連線，並防止使用者工作階段在匯入或匯出作業期間中斷。

您可以選擇在特定電腦上強制執行工作流程或工作流程活動。 若要這麼做，您必須為相關工作流程或活動定義一或多個相關性。

1. 在工作流程或活動中輸入相關性，以建立這些相關性 **[!UICONTROL Affinity]** 欄位。

   您可以選擇任何相似性名稱，但請勿使用空格或標點符號。 如果您使用不同的伺服器，請指定不同的名稱。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉式清單包含先前使用的相關性。 它會隨著時間使用不同的輸入值完成。

1. 開啟 **nl6/conf/config-`<instance>.xml`** 檔案。
1. 修改符合以下條件的行： **[!UICONTROL wfserver]** 模組如下：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果您定義數個相關性，則必須以逗號分隔，且不含任何空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   執行未定義相似性的工作流程時，需要相似性名稱后的逗號。

   如果您只想執行已定義相似性的工作流程，請勿在相似性清單的末尾新增逗號。 例如，修改此行，如下所示：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自動重新啟動 {#automatic-process-restart}

根據預設，不同的Adobe Campaign程式會在每天早上6點（伺服器時間）自動重新啟動。

不過，您可以變更此設定。

若要這麼做，請前往 **serverConf.xml** 檔案，位於 **conf** 存放庫。

此檔案中設定的每個處理程式都有一個 **processRestartTime** 屬性。 您可以修改此屬性的值，以根據您的需求調整每個流程的重新啟動時間。

>[!IMPORTANT]
>
>請勿刪除此屬性。 所有處理程式必須每天重新啟動。
