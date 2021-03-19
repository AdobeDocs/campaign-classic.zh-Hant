---
solution: Campaign Classic
product: campaign
title: Campaign 伺服器設定
description: Campaign 伺服器設定
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# Campaign 伺服器設定{#campaign-server-configuration}

以下各節詳細介紹了強制性伺服器配置，這些配置將保證Adobe Campaign對大多數設定的高效運行。

[設定促銷活動伺服器](../../installation/using/configuring-campaign-server.md)中提供其他設定。

>[!NOTE]
>
>伺服器端組態只能透過AdobeAdobe代管的部署來執行。 要進一步瞭解不同的部署，請參閱[代管模型](../../installation/using/hosting-models.md)部分或[功能矩陣](../../installation/using/capability-matrix.md)。

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

## 配置檔案{#configuration-files}

配置檔案儲存在Adobe Campaign安裝資料夾的&#x200B;**conf**&#x200B;資料夾中。 配置分佈在兩個檔案上：

* **`config-<instance>.xml`** (其 **** 中instance是實例的名稱):實例的特定配置。如果您在多個實例之間共用伺服器，請在其相關檔案中輸入每個實例的特定參數。
* **serverConf.xml**:所有實例的常規配置。此檔案結合了Adobe Campaign伺服器的技術參數：這些會由所有例項共用。 以下詳細說明了其中一些參數。 請參閱檔案本身以查看所有可用參數。 此[部分](../../installation/using/the-server-configuration-file.md)中列出的不同節點和參數。

您可以配置Adobe Campaign資料（日誌、下載、重定向等）的儲存目錄（**var**&#x200B;目錄）。 若要這麼做，請使用&#x200B;**XTK_VAR_DIR**&#x200B;系統變數：

* 在Windows中，在&#x200B;**XTK_VAR_DIR**&#x200B;系統變數中指定以下值

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，轉到&#x200B;**customer.sh**&#x200B;檔案並指明：**匯出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   有關詳細資訊，請參閱[個性化參數](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。

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

## 傳送設定{#delivery-settings}

必須在&#x200B;**serverConf.xml**&#x200B;資料夾中設定傳送參數。

* **DNS配置**:指定傳送網域和DNS伺服器的IP位址（或主機），這些DNS伺服器用來回應MTA模組從此以後所做的MX類型DNS查 **`<dnsconfig>`** 詢。

   >[!NOTE]
   >
   >**nameServers**&#x200B;參數對於在Windows中安裝是必備的。 對於Linux中的安裝，它必須留空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

此檔案中可用的其他傳送參數顯示在[個性化傳送參數](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)中。

另請參閱[電子郵件傳遞能力](../../installation/using/email-deliverability.md)。
