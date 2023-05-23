---
product: campaign
title: 設定 Campaign 伺服器
description: 設定 Campaign 伺服器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 2%

---

# 市場活動伺服器配置入門{#gs-campaign-server-config}



本章詳細介紹可執行的伺服器端配置，以滿足您的需求和環境特性。

## 限制

這些過程僅限於 **現場**/**混合** 部署並需要「管理」權限。

對於 **托管** 部署，伺服器端設定只能通過Adobe配置。 但是，可以在 [市場活動控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)，如IP允許清單管理或URL權限。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)。

有關詳細資訊，請參閱以下各節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](../../installation/using/hosting-models.md)
* [Campaign Classic內部部署和托管能力矩陣](../../installation/using/capability-matrix.md)

## 配置檔案

Campaign Classic配置檔案儲存在 **會議** 資料夾。 該配置分佈在兩個檔案上：

* **serverConf.xml**:所有實例的常規配置。 此檔案將Adobe Campaign伺服器的技術參陣列合在一起：所有實例共用這些實例。 以下對這些參數的說明進行了詳細說明。 此處列出的不同節點和參數 [節](../../installation/using/the-server-configuration-file.md)。
* **配置`<instance>`.xml** ( **實例** 是實例的名稱):實例的特定配置。 如果您在多個實例之間共用伺服器，請在其相關檔案中輸入特定於每個實例的參數。

## 配置範圍

根據您的需求和配置配置配置或調整市場活動伺服器。 您可以：

* 保護 [內部標識符](#internal-identifier)
* 啟用 [市場活動流程](#enabling-processes)
* 配置 [URL權限](url-permissions.md)
* 定義 [安全區](security-zones.md)
* 配置 [Tomcat設定](configure-tomcat.md)
* 自定義 [交貨參數](configure-delivery-settings.md)
* 定義 [動態頁安全和中繼](#dynamic-page-security-and-relays)
* 限制清單 [允許的外部命令](#restricting-authorized-external-commands)
* 設定 [冗餘跟蹤](#redundant-tracking)
* 管理 [高可用性和工作流關聯性](#high-availability-workflows-and-affinities)
* 配置檔案管理 —  [瞭解更多資訊](file-res-management.md)
   * 限制上載檔案格式
   * 啟用對公共資源的訪問
   * 配置代理連接
* [自動進程重新啟動](#automatic-process-restart)


## 內部標識符 {#internal-identifier}

的 **內部** identifier是用於安裝、管理和維護的技術登錄。 此登錄名未與實例關聯。

使用此登錄名連接的操作員將擁有所有實例的所有權限。 如果安裝新，此登錄名將沒有密碼。 必須手動定義此密碼。

使用以下命令：

```
nlserver config -internalpassword
```

然後顯示以下資訊。 輸入並確認密碼：

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## 啟用進程 {#enabling-processes}

Adobe Campaign伺服器上的進程通過 **config-default.xml** 和 **`config-<instance>.xml`** 的子菜單。

要將更改應用於這些檔案，如果Adobe Campaign服務已啟動，則必須運行 **nlserver config -reload** 的子菜單。

有兩種進程：多實例和單實例。

* **多實例**:對所有實例啟動一個單個進程。 這就是 **網**。 **syslog** 和 **跟蹤日誌** 進程。

   可以從 **config-default.xml** 的子菜單。

   聲明Adobe Campaign伺服器訪問客戶端控制台和重定向（跟蹤）:

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在本示例中，使用 **六** 命令。 可以使用任何 **.txt** 或 **.xml** 編輯器。

* **單實例**:每個實例啟動一個進程(模組： **門**。 **wf伺服器**。 **郵件**。 **簡訊** 和 **統計**)。

   可以使用實例的配置檔案配置啟用：

   ```
   config-<instance>.xml
   ```

   聲明伺服器以進行傳遞、執行工作流實例和恢復彈回郵件：

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**市場活動資料儲存**

可以配置儲存目錄(**var** 目錄)中的所有資料（日誌、下載、重定向等）。 要執行此操作，請使用 **XTK_VAR_DIR** 系統變數：

* 在Windows中，在 **XTK_VAR_DIR** 系統變數

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，轉到 **customer.sh** 檔案並指示： **導出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   有關此內容的詳細資訊，請參閱 [個性化參數](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。


## 動態頁安全和中繼 {#dynamic-page-security-and-relays}

預設情況下，所有動態頁都與 **本地** 其Web模組已啟動的電腦的Tomcat伺服器。 此配置在 **`<url>`** 的查詢中繼配置部分 **ServerConf.xml** 的子菜單。

您可以在 **遠程** 伺服器；的子菜單。 為此，必須替換 **本地主機** JSP和JSSP的遠程電腦名、Web應用程式、報告和字串。

有關各種可用參數的詳細資訊，請參閱 **serverConf.xml** 配置檔案。

對於JSP頁，預設配置為：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用以下JSP頁：

* /nl/jsp/**soprouter.jsp**:客戶端控制台和Web服務連接(SOAP API),
* /nl/jsp/**m.jsp**:鏡像頁，
* /nl/jsp/**logon.jsp**:基於Web訪問報告和部署客戶端控制台，
* /nl/jsp/**s.jsp** :使用病毒式營銷（贊助和社交網路）。

用於Mobile App Channel的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**範例:**

可以防止客戶機從外部連接。 為此，只需限制 **soprouter.jsp** 僅授權執行鏡像頁、病毒連結、網路表格和公共資源。

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

在此示例中， **`<IP_addresses>`** 值與授權為此掩碼使用中繼模組的IP地址清單（由comas分隔）一致。

>[!NOTE]
>
>值應根據您的配置和網路約束進行調整，特別是在為您的安裝開發了特定配置時。

### 管理HTTP標頭 {#managing-http-headers}

預設情況下，不中繼所有HTTP標頭。 您可以在中繼發送的回復中添加特定標頭。 操作步驟：

1. 轉到 **serverConf.xml** 的子菜單。
1. 在 **`<relay>`** 節點，轉到中繼HTTP標頭清單。
1. 添加 **`<responseheader>`** 元素，具有以下屬性：

   * **名稱**:標題名稱
   * **值**:值名稱。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制授權的外部命令 {#restricting-authorized-external-commands}

從build 8780 ，技術管理員可以限制可在Adobe Campaign使用的授權外部命令清單。

為此，您需要建立一個文本檔案，其中包含要阻止使用的命令清單，例如：

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

在 **執行** 的子目錄中，需要引用 **黑名單檔案** 屬性。

**僅適用於Linux**:在伺服器配置檔案中，我們建議您指定一個專用於執行外部命令的用戶來增強您的安全配置。 此用戶在 **執行** 的子菜單。 中的所有可用參數 **serverConf.xml** 列在 [節](../../installation/using/the-server-configuration-file.md)。

>[!NOTE]
>
>如果未指定用戶，則在Adobe Campaign實例的用戶上下文中執行所有命令。 用戶必須與運行Adobe Campaign的用戶不同。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

需要將此用戶添加到「neolane」Adobe Campaign運算子的用戶清單。

>[!IMPORTANT]
>
>您不應使用自定義sudo。 系統上需要安裝標準sudo。


## 冗餘跟蹤 {#redundant-tracking}

當多個伺服器用於重定向時，它們必須能夠通過SOAP調用彼此通信，以便共用要重定向的URL中的資訊。 在交付啟動時，可能並非所有重定向伺服器都可用；所以他們可能沒有同等程度的資訊。

>[!NOTE]
>
>使用標準或企業體系結構時，必須授權主應用程式伺服器在每台電腦上上載跟蹤資訊。

必須在重定向配置中通過 **serverConf.xml** 的子菜單。

**範例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

的 **enableIf** 屬性是可選的（預設為空），並允許您僅在結果為true時啟用連接。 這允許您在所有重定向伺服器上獲得相同的配置。

要獲取電腦的主機名，請運行以下命令： **主機名 — s**。



## 高可用性工作流和關聯 {#high-availability-workflows-and-affinities}

您可以配置多個工作流伺服器(wfserver)，並將它們分發到兩台或多台電腦上。 如果選擇此類型的體系結構，請根據Adobe Campaign訪問權限配置負載平衡器的連接模式。

要從Web訪問，請選擇 **負載平衡器** 模式以限制連接時間。

如果通過Adobe Campaign控制台訪問，請選擇 **散列** 或 **粘滯ip** 的子菜單。 這樣，您就可以維護富客戶端與伺服器之間的連接，並防止在導入或導出操作期間中斷用戶會話。

您可以選擇在特定電腦上強制執行工作流或工作流活動。 為此，必須為相關工作流或活動定義一個或多個關聯。

1. 通過在中輸入工作流或活動的關聯 **[!UICONTROL Affinity]** 的子菜單。

   可以選擇任何關聯名稱，但請確保不使用空格或標點符號。 如果使用不同的伺服器，請指定不同的名稱。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉清單包含以前使用的關聯。 它會隨著時間而用不同的輸入值完成。

1. 開啟 **nl6/conf/config-`<instance>.xml`** 的子菜單。
1. 修改與 **[!UICONTROL wfserver]** 模組如下：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果定義了多個關聯，則它們必須用逗號分隔，且不帶任何空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   執行沒有定義關聯的工作流時，必須使用緊鄰名稱后的逗號。

   如果您只想執行已定義關聯的工作流，請不要在關聯清單的末尾添加逗號。 例如，按如下方式修改行：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自動重新啟動 {#automatic-process-restart}

預設情況下，不同的Adobe Campaign進程每天在上午6點（伺服器時間）自動重新啟動。

但是，您可以更改此配置。

要執行此操作，請轉到 **serverConf.xml** 檔案，位於 **會議** 安裝的儲存庫。

此檔案中配置的每個進程都有 **processRestartTime** 屬性。 您可以修改此屬性的值，以根據需要調整每個進程的重新啟動時間。

>[!IMPORTANT]
>
>不要刪除此屬性。 必須每天重新啟動所有進程。
