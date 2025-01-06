---
product: campaign
title: 設定Campaign伺服器
description: 設定Campaign伺服器
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 1%

---

# 開始使用Campaign伺服器設定{#gs-campaign-server-config}



本章詳細說明可以根據您的需求和環境特性執行的伺服器端設定。

## 限制

這些程式僅限於&#x200B;**內部部署**/**混合**&#x200B;部署，且需要管理許可權。

對於&#x200B;**託管**&#x200B;部署，伺服器端設定只能由Adobe設定。 不過，某些設定可以在[Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)中設定，例如IP允許清單管理或URL許可權。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署和託管功能矩陣](../../installation/using/capability-matrix.md)

## 組態檔

Campaign Classic組態檔儲存在Adobe Campaign安裝資料夾的&#x200B;**conf**&#x200B;資料夾中。 此設定分為兩個檔案：

* **serverConf.xml**：所有執行個體的一般組態。 此檔案結合Adobe Campaign伺服器的技術引數：這些引數由所有執行個體共用。 其中一些引數的說明詳述如下。 此[區段](../../installation/using/the-server-configuration-file.md)中列出的不同節點和引數。
* **config-`<instance>`.xml** （其中&#x200B;**instance**&#x200B;是執行個體的名稱）：執行個體的特定設定。 如果您在多個執行個體之間共用伺服器，請在相關檔案中輸入每個執行個體專屬的引數。

## 設定範圍

根據您的需求和設定，設定或調整Campaign伺服器。 您可以：

* 保護[內部識別碼](#internal-identifier)
* 啟用[行銷活動程式](#enabling-processes)
* 設定[URL許可權](url-permissions.md)
* 定義[安全性區域](security-zones.md)
* 設定[Tomcat設定](configure-tomcat.md)
* 自訂[傳遞引數](configure-delivery-settings.md)
* 定義[動態頁面安全性與轉送](#dynamic-page-security-and-relays)
* 限制[允許的外部命令清單](#restricting-authorized-external-commands)
* 設定[備援追蹤](#redundant-tracking)
* 管理[高可用性與工作流程相關性](#high-availability-workflows-and-affinities)
* 設定檔案管理 — [深入瞭解](file-res-management.md)
   * 限制上傳檔案格式
   * 啟用對公用資源的存取權
   * 設定代理伺服器連線
* [自動程式重新啟動](#automatic-process-restart)


## 內部識別碼 {#internal-identifier}

**內部**&#x200B;識別碼是技術登入，用於安裝、管理和維護目的。 此登入未關聯到執行個體。

使用此登入連線的操作者將擁有所有執行個體的所有權利。 若是新的安裝，此登入將不會有密碼。 您必須手動定義此密碼。

使用以下命令：

```sql
nlserver config -internalpassword
```

接著會顯示下列資訊。 輸入並確認密碼：

```sql
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## 啟用程式 {#enabling-processes}

伺服器上的Adobe Campaign處理程式已透過&#x200B;**config-default.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**&#x200B;檔案啟用（和停用）。

若要套用變更至這些檔案，如果Adobe Campaign服務已啟動，您必須執行&#x200B;**nlserver config -reload**&#x200B;命令。

有兩種型別的程式：多執行個體和單一執行個體。

* **多重執行個體**：已針對所有執行個體啟動單一處理序。 這是&#x200B;**web**、**syslogd**&#x200B;和&#x200B;**trackinglogd**&#x200B;處理序的情況。

  可從&#x200B;**config-default.xml**&#x200B;檔案設定啟用。

  宣告Adobe Campaign伺服器以存取使用者端主控台及進行重新導向（追蹤）：

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  在此範例中，檔案是在Linux中使用&#x200B;**vi**&#x200B;命令編輯的。 可使用任何&#x200B;**.txt**&#x200B;或&#x200B;**.xml**&#x200B;編輯器編輯它。

* **單一執行個體**：每個執行個體已啟動一個處理序（模組： **mta**、**wfserver**、**inMail**、**sms**&#x200B;和&#x200B;**stat**）。

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

**行銷活動資料儲存**

您可以設定Adobe Campaign資料（記錄、下載、重新導向等）的儲存目錄（**var**&#x200B;目錄）。 若要這麼做，請使用&#x200B;**XTK_VAR_DIR**&#x200B;系統變數：

* 在Windows中，在&#x200B;**XTK_VAR_DIR**&#x200B;系統變數中表示下列值

  ```
  D:\log\AdobeCampaign
  ```

* 在Linux中，移至&#x200B;**customer.sh**&#x200B;檔案並指示： **export XTK_VAR_DIR=/app/log/AdobeCampaign**。

  如需詳細資訊，請參閱[個人化引數](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。


## 動態頁面安全性和轉送 {#dynamic-page-security-and-relays}

依預設，所有動態頁面都會自動關聯到Web模組已啟動之電腦的&#x200B;**本機** Tomcat伺服器。 已在&#x200B;**ServerConf.xml**&#x200B;檔案的查詢轉送組態的&#x200B;**`<url>`**&#x200B;區段中輸入此組態。

您可以在&#x200B;**遠端**&#x200B;伺服器上轉送執行動態頁面；如果電腦上未啟動Web模組。 若要這麼做，您必須將&#x200B;**localhost**&#x200B;取代為JSP和JSSP、Web應用程式、報表和字串的遠端電腦名稱。

如需各種可用引數的詳細資訊，請參閱&#x200B;**serverConf.xml**&#x200B;組態檔。

對於JSP頁面，預設組態為：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用下列JSP頁面：

* /nl/jsp/**soaprouter.jsp**：使用者端主控台和Web服務連線(SOAP API)，
* /nl/jsp/**m.jsp**：映象頁面，
* /nl/jsp/**logon.jsp**：使用者端主控台的Web式報表存取與部署，
* /nl/jsp/**s.jsp** ：使用病毒式行銷（贊助和社交網路）。

用於行動應用程式通道的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**範例：**

可以防止使用者端電腦從外部連線。 若要這麼做，只要限制執行&#x200B;**soaprouter.jsp**，並僅授權執行映象頁面、病毒連結、網路表單及公用資源。

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

在此範例中，**`<IP_addresses>`**&#x200B;值與授權使用此遮罩之轉送模組的IP位址清單（以逗號分隔）一致。

>[!NOTE]
>
>值應根據您的設定和網路限制進行調整，尤其是在已針對您的安裝開發特定設定時。

### 管理HTTP標頭 {#managing-http-headers}

依預設，不會轉送所有HTTP標頭。 您可以在轉送所傳送的回覆中新增特定標頭。 操作步驟：

1. 移至&#x200B;**serverConf.xml**&#x200B;檔案。
1. 在&#x200B;**`<relay>`**&#x200B;節點中，移至轉送HTTP標頭的清單。
1. 新增具有以下屬性的&#x200B;**`<responseheader>`**&#x200B;元素：

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

在伺服器設定檔的&#x200B;**exec**&#x200B;節點中，您必須參考&#x200B;**blacklistFile**&#x200B;屬性中先前建立的檔案。

**僅適用於Linux**：在伺服器設定檔中，建議您指定專為執行外部命令的使用者，以加強您的安全性設定。 此使用者設定於組態檔的&#x200B;**exec**&#x200B;節點中。 **serverConf.xml**&#x200B;中可用的所有引數都列在此[區段](../../installation/using/the-server-configuration-file.md)中。

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

必須在重新導向組態中透過&#x200B;**serverConf.xml**&#x200B;檔案指定多餘伺服器的URL。

**範例：**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf**&#x200B;屬性是選擇性的（預設為空白），只有在結果為true時才允許您啟用連線。 這可讓您在所有重新導向伺服器上取得相同的設定。

若要取得電腦的主機名稱，請執行以下命令： **主機名稱 — s**。



## 高可用性工作流程與相關性 {#high-availability-workflows-and-affinities}

您可以設定數個工作流程伺服器(wfserver)，並在兩部或多部電腦上分配這些伺服器。 如果您選擇這種架構，請根據Adobe Campaign存取權設定負載平衡器的連線模式。

若要從網頁存取，請選取&#x200B;**負載平衡器**&#x200B;模式以限制連線時間。

如果透過Adobe Campaign主控台存取，請選擇&#x200B;**雜湊**&#x200B;或&#x200B;**粘性ip**&#x200B;模式。 這可讓您維護RTF使用者端與伺服器之間的連線，並防止使用者工作階段在匯入或匯出作業期間中斷。

您可以選擇在特定電腦上強制執行工作流程或工作流程活動。 若要這麼做，您必須為相關工作流程或活動定義一或多個相關性。

1. 在&#x200B;**[!UICONTROL Affinity]**&#x200B;欄位中輸入工作流程或活動，以建立它們的相關性。

   您可以選擇任何相似性名稱，但請勿使用空格或標點符號。 如果您使用不同的伺服器，請指定不同的名稱。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉式清單包含先前使用的相關性。 它會隨著時間使用不同的輸入值完成。

1. 開啟&#x200B;**nl6/conf/config-`<instance>.xml`**&#x200B;檔案。
1. 修改符合&#x200B;**[!UICONTROL wfserver]**&#x200B;模組的行，如下所示：

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

若要這麼做，請移至您安裝之&#x200B;**conf**&#x200B;存放庫中的&#x200B;**serverConf.xml**&#x200B;檔案。

此檔案中設定的每個處理序都有&#x200B;**processRestartTime**&#x200B;屬性。 您可以修改此屬性的值，以根據您的需求調整每個流程的重新啟動時間。

>[!IMPORTANT]
>
>請勿刪除此屬性。 所有處理程式必須每天重新啟動。
