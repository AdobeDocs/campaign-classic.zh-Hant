---
title: 促銷活動伺服器設定
seo-title: 促銷活動伺服器設定
description: 促銷活動伺服器設定
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# 促銷活動伺服器設定{#campaign-server-configuration}

以下各節詳細說明必備的伺服器組態，以確保Adobe Campaign在大部分設定中都能有效運作。

「設定促銷活動」伺服器 [提供其他設定](../../installation/using/configuring-campaign-server.md)。

>[!NOTE]
>
>伺服器端組態只能由Adobe針對Adobe代管的部署執行。 若要進一步瞭解不同的部署，請參閱「代 [管模型](../../installation/using/hosting-models.md) 」一節或 [本文](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。

## 內部識別碼 {#internal-identifier}

內部 **識別碼** ，是用於安裝、管理和維護目的的技術登入。 此登入不與例項關聯。

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

## 配置檔案 {#configuration-files}

設定檔案會儲存在Adobe Campaign安 **裝資料夾** (conf)資料夾中。 配置分佈在兩個檔案上：

* **`config-<instance>.xml`** (其 **中** instance是實例的名稱):實例的特定配置。 如果您在多個實例之間共用伺服器，請在其相關檔案中輸入每個實例的特定參數。
* **serverConf.xml**:所有實例的常規配置。 此檔案結合了Adobe Campaign伺服器的技術參數：這些會由所有例項共用。 以下詳細說明了其中一些參數。 請參閱檔案本身以查看所有可用參數。 本節列出的不同節點和 [參數](../../installation/using/the-server-configuration-file.md)。

您可以設定Adobe Campaign資料(**記錄檔** 、下載、重新導向等)的儲存目錄（var目錄）。 若要這麼做，請使 **用XTK_VAR_DIR系統變數** :

* 在Windows中，在 **XTK_VAR_DIR系統變數中指示以下值** 。

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，請至 **customer.sh檔案** ，並指出：匯 **出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## 啟用流程 {#enabling-processes}

伺服器上的Adobe Campaign程式會透過 **config-default.xml和檔案啟用（和停用）****`config-<instance>.xml`** 。

若要將變更套用至這些檔案，如果Adobe Campaign服務已啟動，您必須執行 **nlserver config -reload** 命令。

有兩種流程：多執行個體和單一執行個體。

* **多實例**:所有例項都會啟動單一程式。 Web、syslogd和 **trackinglogd**&#x200B;進程就是 ******** 這樣。

   可從config-default.xml檔案 **設定啟用** 。

   宣告Adobe Campaign伺服器以存取用戶端主控台並進行重新導向（追蹤）:

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在此示例中，使用Linux中的 **vi命令** 編輯檔案。 您可以使用任何 **.txt** 或 **.xml編輯器來編輯** 。

* **單實例**:每個實例(模組： **mta、wfserver****、** Mail **in** Mail **Sms** 和Stat ****)。

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

## 傳送設定 {#delivery-settings}

傳送參數必須在serverConf.xml資 **料夾中設定** 。

* **DNS配置**:指定傳送網域和DNS伺服器的IP位址（或主機），這些DNS伺服器用來回應MTA模組從此以後所做的MX類型DNS查 **`<dnsconfig>`** 詢。

   >[!NOTE]
   >
   >nameServers **參數** ，是在Windows中安裝的必備參數。 對於Linux中的安裝，它必須留空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

此檔案中其他可用的傳送參數會顯示在個人化 [傳送參數中](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)。

另請參閱電 [子郵件傳遞功能](../../installation/using/email-deliverability.md)。
