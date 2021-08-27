---
product: campaign
title: 在 Linux 中移轉 Adobe Campaign v7
description: 在 Linux 中移轉 Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---

# 在 Linux 中移轉 Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

## 一般程式 {#general-procedure}

在Linux中的移轉步驟如下：

1. 停止服務：請參閱[服務停止](#service-stop)。
1. 保存資料庫：請參閱[備份資料庫和現有安裝](#back-up-the-database-and-the-existing-installation)。
1. 解除安裝先前的Adobe Campaign版本套件：請參閱[解除安裝Adobe Campaign舊版套件](#uninstalling-adobe-campaign-previous-version-packages)。
1. 移轉平台：請參閱[部署Adobe Campaign v7](#deploying-adobe-campaign-v7)。
1. 重新啟動服務：請參閱[重新啟動服務](#re-starting-services)。

## 服務停止 {#service-stop}

首先，停止所有相關電腦上具有資料庫訪問權限的所有進程。

1. 以&#x200B;**root**&#x200B;登入。
1. 需要停止使用重定向模組（**webmdl**&#x200B;服務）的所有伺服器。 對於Apache，請運行以下命令：

   ```
   /etc/init.d/apache2 stop
   ```

1. 以&#x200B;**root**&#x200B;重新登入。
1. 在所有伺服器上停止Adobe Campaign舊版服務。

   ```
   /etc/init.d/nlserver6 stop
   ```

   如果要從v5.11遷移，請運行以下命令：

   ```
   /etc/init.d/nlserver5 stop
   ```

1. 請確定每個伺服器上都已停止Adobe Campaign服務。

   ```
   ps waux | grep nlserver
   ```

   活動進程的清單及其ID(PID)將一併顯示。

1. 如果一或多個Adobe Campaign程式在幾分鐘後仍處於作用中或封鎖狀態，請終止。

   ```
   killall nlserver
   ```

1. 如果某些進程在幾分鐘後仍處於活動狀態，則可以使用命令強制它們關閉：

   ```
   killall -9 nlserver
   ```

## 備份資料庫和現有安裝 {#back-up-the-database-and-the-existing-installation}

程式取決於您的Adobe Campaign舊版。

### 從Adobe Campaign v5.11移轉 {#migrating-from-adobe-campaign-v5-11}

1. 備份Adobe Campaign資料庫。
1. 以&#x200B;**neolane**&#x200B;登錄，並使用以下命令備份&#x200B;**nl5**&#x200B;目錄：

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >為了防患於未然，建議您將&#x200B;**nl5.back**&#x200B;資料夾壓縮並儲存至伺服器以外的安全位置。

1. 編輯&#x200B;**config-`<instance name>`.xml**（在&#x200B;**nl5.back**&#x200B;資料夾中），以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服務自動啟動。 例如，將&#x200B;**autoStart**&#x200B;替換為&#x200B;**_autoStart**（仍為&#x200B;**neolane**）。

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### 從Adobe Campaign v6.02移轉 {#migrating-from-adobe-campaign-v6-02}

1. 備份Adobe Campaign資料庫。
1. 以&#x200B;**neolane**&#x200B;登錄，並使用以下命令備份&#x200B;**nl6**&#x200B;目錄：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >為了防患於未然，建議您壓縮&#x200B;**nl6.back**&#x200B;資料夾，並將其儲存至伺服器以外的安全位置。

1. 編輯&#x200B;**config-`<instance name>`.xml**（在&#x200B;**nl6.back**&#x200B;資料夾中）以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服務自動啟動。 例如，將&#x200B;**autoStart**&#x200B;替換為&#x200B;**_autoStart**(仍為&#x200B;**Adobe Campaign**)。

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### 從Adobe Campaign v6.1移轉 {#migrating-from-adobe-campaign-v6-1}

1. 備份Adobe Campaign資料庫。
1. 以&#x200B;**neolane**&#x200B;登錄，並使用以下命令備份&#x200B;**nl6**&#x200B;目錄：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >為了防患於未然，建議您壓縮&#x200B;**nl6.back**&#x200B;資料夾，並將其儲存至伺服器以外的安全位置。

## 解除安裝Adobe Campaign舊版套件 {#uninstalling-adobe-campaign-previous-version-packages}

程式取決於您的Adobe Campaign舊版。

### 解除安裝Adobe Campaign v5套件 {#uninstalling-adobe-campaign-v5-packages}

1. 以&#x200B;**root**&#x200B;登入。
1. 使用下列命令識別安裝的Adobe Campaign套件。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -l | grep nl
      ```

      隨即顯示已安裝的程式包清單：

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -qa | grep nl
      ```

1. 解除安裝Adobe Campaign v5套件。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### 解除安裝Adobe Campaign v6套件 {#uninstalling-adobe-campaign-v6-packages}

本節說明如何解除安裝Adobe Campaign v6.02或v6.1套件。

1. 以&#x200B;**root**&#x200B;登入。
1. 使用下列命令識別安裝的Adobe Campaign套件。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -l | grep nl
      ```

      隨即顯示已安裝的程式包清單：

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -qa | grep nl
      ```

1. 解除安裝Adobe Campaign v6套件。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

程式取決於您的Adobe Campaign舊版。

### 從Adobe Campaign v5.11移轉 {#migrating-from-adobe-campaign-v5_11-1}

部署Adobe Campaign需要兩個階段：

* 安裝Adobe Campaign v7套件：必須在每個伺服器上執行此操作。
* 升級後：必須在每個實例上啟動此命令。

若要部署Adobe Campaign，請套用下列步驟：

1. 使用下列命令安裝最新的Adobe Campaign v7套件：

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >您必須成功安裝軟體包，然後才能繼續下一步。

   >[!NOTE]
   >
   >從v5.11移轉時，預設情況下，Adobe Campaign會安裝在&#x200B;**/usr/local/neolane/nl6/**&#x200B;目錄中。
   >
   >安裝套件後，會顯示下列訊息：**&#39;WdbcTimeZone&#39;選項缺少**。 這是正常的。

1. 若要讓用戶端主控台安裝程式可供使用，請將其複製至Adobe Campaign安裝目錄：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有關如何在Linux中安裝Adobe Campaign的詳細資訊，請參閱[本區段](../../installation/using/installing-campaign-standard-packages.md)。

1. 修改與&#x200B;**neolane**&#x200B;使用者相符的&#x200B;**.bashrd**&#x200B;檔案。 以&#x200B;**neolane**&#x200B;登錄，並運行以下命令：

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >當您以&#x200B;**neolane**&#x200B;登入時，會顯示下列訊息：**nl5/env.sh :沒有此類檔案或目錄**。 這是正常的。

   在檔案結尾處，將&#x200B;**nl5/env.sh**&#x200B;替換為&#x200B;**nl6/env.sh**。

1. 以&#x200B;**root**&#x200B;登入，並使用下列命令準備執行個體：

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >以下命令可讓您建立Adobe Campaign v6內部檔案系統：**conf**&#x200B;目錄（含&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;檔案）、**var**&#x200B;目錄。

1. 轉到&#x200B;**nl5.back**&#x200B;備份資料夾，並複製（覆寫）每個實例的配置檔案和子資料夾。 以&#x200B;**neolane**&#x200B;登錄，然後運行以下命令：

   >[!IMPORTANT]
   >
   >對於下面的第一個命令，請勿複製&#x200B;**config-default.xml**&#x200B;檔案。

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. 在Adobe Campaign v7 **serverConf.xml**&#x200B;和&#x200B;**config-default.xml**&#x200B;檔案中，套用您針對Adobe Campaign v5的特定設定。 對於&#x200B;**serverConf.xml**&#x200B;檔案，請使用&#x200B;**nl5/conf/serverConf.xml.diff**&#x200B;檔案。

   >[!NOTE]
   >
   >報告從Adobe Campaign v5到Adobe Campaign v7的設定時，請確定通往物理目錄的路徑會導向Adobe Campaign v7，而非Adobe Campaign v5。

1. 由於遷移不是一般安裝，因此您需要強制重新啟動&#x200B;**trackinglogd**&#x200B;服務。 要執行此操作，請開啟&#x200B;**nl6/conf/config-default.xml**&#x200B;檔案，並確認&#x200B;**trackinglogd**&#x200B;服務已啟動（僅在追蹤/重新導向伺服器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果未在追蹤伺服器上啟動&#x200B;**trackinglogd**&#x200B;服務，則不會轉送追蹤資訊。

1. 使用下列命令重新載入Adobe Campaign v7設定：

   ```
   nlserver config -reload
   ```

1. 使用以下命令（仍為&#x200B;**neolane**）啟動升級後進程：

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >您必須指定在升級後期間要用作參考的時區（使用&#x200B;**-timezone**&#x200B;選項）。 在此案例中，我們使用歐洲/巴黎時區&#x200B;**— 時區：&quot;Europe/Paris&quot;**。

   >[!NOTE]
   >
   >強烈建議您將基礎升級為「多時區」。 有關時區選項的詳細資訊，請參閱[時區](../../migration/using/general-configurations.md#time-zones)區段。

>[!IMPORTANT]
>
>尚未啟動Adobe Campaign服務：仍需在Apache中進行變更。

### 從Adobe Campaign v6.02移轉 {#migrating-from-adobe-campaign-v6_02-1}

部署Adobe Campaign需要兩個階段：

* 安裝Adobe Campaign v7套件：必須在每個伺服器上執行此操作。
* 升級後：必須在每個實例上啟動此命令。

若要部署Adobe Campaign，請套用下列步驟：

1. 使用下列命令安裝最新的Adobe Campaign v7套件：

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >您必須成功安裝軟體包，然後才能繼續下一步。

   >[!NOTE]
   >
   >Adobe Campaign v7預設會安裝在與Adobe Campaign v6.02相同的目錄中：**/usr/local/neolane/nl6/**。

1. 若要讓用戶端主控台安裝程式可供使用，請將其複製至Adobe Campaign安裝目錄：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有關如何在Linux中安裝Adobe Campaign的詳細資訊，請參閱[本區段](../../installation/using/installing-campaign-standard-packages.md)。

1. 由於遷移不是一般安裝，因此您需要強制重新啟動&#x200B;**trackinglogd**&#x200B;服務。 要執行此操作，請開啟&#x200B;**nl6/conf/config-default.xml**&#x200B;檔案，並確認&#x200B;**trackinglogd**&#x200B;服務已啟動（僅在追蹤/重新導向伺服器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果未在追蹤伺服器上啟動&#x200B;**trackinglogd**&#x200B;服務，則不會轉送追蹤資訊。

1. 轉到&#x200B;**nl6.back**&#x200B;備份資料夾，並複製（覆寫）每個實例的配置檔案和子資料夾。 以&#x200B;**neolane**&#x200B;登錄，然後運行以下命令：

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. 使用下列命令重新載入Adobe Campaign v7設定：

   ```
   nlserver config -reload
   ```

1. 使用以下命令（仍為&#x200B;**neolane**）啟動升級後進程：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >「多時區」模式僅在v6.02中可用於PostgreSQL資料庫引擎。 現在，無論使用哪個版本的資料庫引擎，都可使用它。 強烈建議您將基礎升級為「多時區」。 有關時區選項的詳細資訊，請參閱[時區](../../migration/using/general-configurations.md#time-zones)區段。

### 從Adobe Campaign v6.1移轉 {#migrating-from-adobe-campaign-v6_1-1}

部署Adobe Campaign需要兩個階段：

* 安裝Adobe Campaign v7套件：必須在每個伺服器上執行此操作。
* 升級後：必須在每個實例上啟動此命令。

若要部署Adobe Campaign，請套用下列步驟：

1. 使用下列命令安裝最新的Adobe Campaign v7套件：

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >您必須成功安裝軟體包，然後才能繼續下一步。

   >[!NOTE]
   >
   >Adobe Campaign v7預設安裝在&#x200B;**/usr/local/neolane/nl6/**&#x200B;目錄中。

1. 若要讓用戶端主控台安裝程式可供使用，請將其複製至Adobe Campaign安裝目錄：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >有關如何在Linux中安裝Adobe Campaign的詳細資訊，請參閱[本區段](../../installation/using/installing-campaign-standard-packages.md)。

1. 轉到&#x200B;**nl6.back**&#x200B;備份資料夾，並複製（覆寫）每個實例的配置檔案和子資料夾。 以&#x200B;**neolane**&#x200B;登錄，然後運行以下命令：

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. 使用下列命令重新載入Adobe Campaign v7設定：

   ```
   nlserver config -reload
   ```

1. 使用以下命令（仍為&#x200B;**neolane**）啟動升級後進程：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## 遷移重定向伺服器(Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>本節內容僅適用於從Adobe Campaign v5.11移轉時。

此階段需要停止Apache。 請參閱：[服務停止](#service-stop)。

1. 以&#x200B;**root**&#x200B;登入。
1. 更改Apache環境變數，使其連結到&#x200B;**nl6**&#x200B;目錄。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      vi /etc/apache2/envvars
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 然後運行以下命令：

   * 在&#x200B;**Debian**&#x200B;中：

      在&#x200B;**nlsrv.load**&#x200B;檔案中，將&#x200B;**nl5**&#x200B;替換為&#x200B;**nl6**。

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      刪除&#x200B;**nlsrv.conf**&#x200B;檔案的連結並建立新的連結。

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      前往&#x200B;**/usr/local/apache2/conf**&#x200B;目錄，編輯&#x200B;**http.conf**&#x200B;檔案，並在下列各行中將&#x200B;**nl5**&#x200B;取代為&#x200B;**nl6**。

      在&#x200B;**RHEL 7/Debian 8**&#x200B;中：

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. 前往&#x200B;**alias.conf**&#x200B;檔案，並將所有&#x200B;**nl5**&#x200B;取代為&#x200B;**nl6**。 若要在Debian中執行此動作，請執行下列命令：

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 安全區域 {#security-zones}

如果您要從v6.02或更舊版本移轉，則必須先配置安全區域，才能啟動服務。 有關詳細資訊，請參閱[安全](../../migration/using/general-configurations.md#security)。

## 重新啟動服務 {#re-starting-services}

程式取決於您的Adobe Campaign舊版。

### 從Adobe Campaign v5.11移轉 {#migrating-from-adobe-campaign-v5_11-2}

在&#x200B;**config-`<instance name>`.xml**&#x200B;檔案中，重新激活&#x200B;**mta**、**wfserver**、**stat**&#x200B;等的自動啟動。 服務。

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

在下列各伺服器上啟動Apache和Adobe Campaign服務：

1. 跟蹤和重定向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

在繼續下一步之前，請對新安裝運行完整測試，確保沒有回歸，並且所有操作都可以按照[常規配置](../../migration/using/general-configurations.md)部分中的所有建議運行。

### 從Adobe Campaign v6.02移轉 {#migrating-from-adobe-campaign-v6_02-2}

在&#x200B;**config-`<instance name>`.xml**&#x200B;檔案中，重新激活&#x200B;**mta**、**wfserver**、**stat**&#x200B;等的自動啟動。 服務。

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

在下列各伺服器上啟動Apache和Adobe Campaign服務：

1. 跟蹤和重定向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

請依照[一般設定](../../migration/using/general-configurations.md)區段中的所有建議，完全測試新安裝，檢查其是否未回復，並確認一切皆正常運作。

### 從Adobe Campaign v6.1移轉 {#migrating-from-adobe-campaign-v6_1-2}

在下列各伺服器上啟動Apache和Adobe Campaign服務：

1. 跟蹤和重定向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

請依照[一般設定](../../migration/using/general-configurations.md)區段中的所有建議，完全測試新安裝，檢查其是否未回復，並確認一切皆正常運作。

## 刪除和清除Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>本節內容僅適用於從Adobe Campaign v5.11移轉時。

在刪除及清除Adobe Campaign v5安裝之前，您必須套用下列建議：

* 請功能團隊對新安裝執行完整檢查。
* 只有在您確定不需要回滾時，才解除安裝Adobe Campaign v5。

刪除&#x200B;**nl5.back**&#x200B;目錄。 以&#x200B;**neolane**&#x200B;登錄，然後運行以下命令：

```
su - neolane
rm -rf nl5.back
```

重新啟動伺服器。
