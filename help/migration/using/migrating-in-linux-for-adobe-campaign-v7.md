---
solution: Campaign Classic
product: campaign
title: 在 Linux 中移轉 Adobe Campaign v7
description: 在 Linux 中移轉 Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---


# 在 Linux 中移轉 Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## 一般過程{#general-procedure}

Linux中的遷移步驟如下：

1. 停止服務：請參閱[服務停止](#service-stop)。
1. 保存資料庫：請參閱[備份資料庫和現有安裝](#back-up-the-database-and-the-existing-installation)。
1. 解除安裝舊版Adobe Campaign套件：請參閱[解除安裝Adobe Campaign舊版套件](#uninstalling-adobe-campaign-previous-version-packages)。
1. 移轉平台：請參閱[部署Adobe Campaign v7](#deploying-adobe-campaign-v7)。
1. 重新啟動服務：請參閱[重新啟動服務](#re-starting-services)。

## 服務停止{#service-stop}

首先，在所有相關電腦上停止所有訪問資料庫的進程。

1. 以&#x200B;**root**&#x200B;身份登錄。
1. 需要停止使用重定向模組（**webmdl**&#x200B;服務）的所有伺服器。 對於Apache，運行以下命令：

   ```
   /etc/init.d/apache2 stop
   ```

1. 以&#x200B;**root**&#x200B;的身分再次登入。
1. 在所有伺服器上停止Adobe Campaign舊版服務。

   ```
   /etc/init.d/nlserver6 stop
   ```

   如果您要從v5.11移轉，請執行下列命令：

   ```
   /etc/init.d/nlserver5 stop
   ```

1. 請確定每個伺服器上都已停止Adobe Campaign服務。

   ```
   ps waux | grep nlserver
   ```

   活動進程的清單及其ID(PID)將一併顯示。

1. 如果一或多個Adobe Campaign程式仍在作用中或幾分鐘後被封鎖，請停止它們。

   ```
   killall nlserver
   ```

1. 如果某些進程在幾分鐘後仍處於活動狀態，則可使用以下命令強制它們關閉：

   ```
   killall -9 nlserver
   ```

## 備份資料庫和現有安裝{#back-up-the-database-and-the-existing-installation}

此程式取決於您的Adobe Campaign舊版。

### 從Adobe Campaign 5.11 {#migrating-from-adobe-campaign-v5-11}版移轉

1. 備份Adobe Campaign資料庫。
1. 以&#x200B;**neolane**&#x200B;的身分登入，並使用下列命令備份&#x200B;**nl5**&#x200B;目錄：

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >為防患於未然，我們建議您將&#x200B;**nl5.back**&#x200B;資料夾壓縮，並儲存至伺服器以外的安全位置。

1. 編輯&#x200B;**config-`<instance name>`.xml**（在&#x200B;**nl5.back**&#x200B;資料夾中），以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服務自動啟動。 例如，將&#x200B;**autoStart**&#x200B;取代為&#x200B;**_autoStart**（仍為&#x200B;**neolane**）。

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

### 從Adobe Campaign 6.02 {#migrating-from-adobe-campaign-v6-02}版移轉

1. 備份Adobe Campaign資料庫。
1. 以&#x200B;**neolane**&#x200B;的身分登入，並使用下列命令備份&#x200B;**nl6**&#x200B;目錄：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >為防患於未然，我們建議您將&#x200B;**nl6.back**&#x200B;資料夾壓縮，並儲存至伺服器以外的安全位置。

1. 編輯&#x200B;**config-`<instance name>`.xml**（在&#x200B;**nl6.back**&#x200B;資料夾中），以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服務自動啟動。 例如，將&#x200B;**autoStart**&#x200B;取代為&#x200B;**_autoStart**（仍為&#x200B;**Adobe Campaign**）。

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

### 從Adobe Campaign 6.1 {#migrating-from-adobe-campaign-v6-1}版移轉

1. 備份Adobe Campaign資料庫。
1. 以&#x200B;**neolane**&#x200B;的身分登入，並使用下列命令備份&#x200B;**nl6**&#x200B;目錄：

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >為防患於未然，我們建議您將&#x200B;**nl6.back**&#x200B;資料夾壓縮，並儲存至伺服器以外的安全位置。

## 解除安裝Adobe Campaign舊版套件{#uninstalling-adobe-campaign-previous-version-packages}

此程式取決於您的Adobe Campaign舊版。

### 解除安裝Adobe Campaign v5套件{#uninstalling-adobe-campaign-v5-packages}

1. 以&#x200B;**root**&#x200B;身份登錄。
1. 使用下列命令識別安裝的Adobe Campaign套件。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -l | grep nl
      ```

      將顯示已安裝軟體包的清單：

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

### 解除安裝Adobe Campaign v6套件{#uninstalling-adobe-campaign-v6-packages}

本節說明如何解除安裝Adobe Campaign 6.02或v6.1套件。

1. 以&#x200B;**root**&#x200B;身份登錄。
1. 使用下列命令識別安裝的Adobe Campaign套件。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      dpkg -l | grep nl
      ```

      將顯示已安裝軟體包的清單：

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

此程式取決於您的Adobe Campaign舊版。

### 從Adobe Campaign 5.11 {#migrating-from-adobe-campaign-v5_11-1}版移轉

部署Adobe Campaign需要兩個階段：

* 安裝Adobe Campaign v7套件：必須在每台伺服器上執行此操作。
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
   >您必須成功安裝軟體包，才能繼續下一步。

   >[!NOTE]
   >
   >從v5.11移轉時，Adobe Campaign預設會安裝在&#x200B;**/usr/local/neolane/nl6/**&#x200B;目錄中。
   >
   >安裝軟體包後，將顯示以下消息：**&#39;WdbcTimeZone&#39;選項遺失**。 這是正常的。

1. 若要讓用戶端主控台安裝程式可供使用，請將它複製至Adobe Campaign安裝目錄：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >如需如何在Linux中安裝Adobe Campaign的詳細資訊，請參閱[本節](../../installation/using/installing-campaign-standard-packages.md)。

1. 修改與&#x200B;**neolane**&#x200B;使用者相符的&#x200B;**.bashrd**&#x200B;檔案。 以&#x200B;**neolane**&#x200B;的身分登入，然後執行下列命令：

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >當您以&#x200B;**neolane**&#x200B;的身分登入時，會顯示下列訊息：**nl5/env.sh:沒有此類檔案或目錄**。 這是正常的。

   在檔案末尾，將&#x200B;**nl5/env.sh**&#x200B;替換為&#x200B;**nl6/env.sh**。

1. 以&#x200B;**root**&#x200B;的身分登入，並使用下列命令準備實例：

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
   >這些命令可讓您建立Adobe Campaign v6內部檔案系統：**conf**&#x200B;目錄（含&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;檔案）、**var**&#x200B;目錄。

1. 轉至&#x200B;**nl5.back**&#x200B;備份資料夾並複製（覆蓋）每個實例的配置檔案和子資料夾。 以&#x200B;**neolane**&#x200B;的身分登入，然後執行下列命令：

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

1. 在Adobe Campaign v7 **serverConf.xml**&#x200B;和&#x200B;**config-default.xml**&#x200B;檔案中，套用您對Adobe Campaign v5的特定設定。 對於&#x200B;**serverConf.xml**&#x200B;檔案，請使用&#x200B;**nl5/conf/serverConf.xml.diff**&#x200B;檔案。

   >[!NOTE]
   >
   >在報告從Adobe Campaign v5到Adobe Campaign v7的設定時，請確定到實體目錄的路徑會導向Adobe Campaign v7，而非Adobe Campaign v5。

1. 由於遷移不是一般安裝，因此您需要強制重新啟動&#x200B;**trackinglogd**&#x200B;服務。 若要這麼做，請開啟&#x200B;**nl6/conf/config-default.xml**&#x200B;檔案，並確定&#x200B;**trackinglogd**&#x200B;服務已啟動（僅限在追蹤／重新導向伺服器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果追蹤伺服器上未啟動&#x200B;**trackinglogd**&#x200B;服務，則不會轉送追蹤資訊。

1. 使用下列命令重新載入Adobe Campaign v7設定：

   ```
   nlserver config -reload
   ```

1. 使用以下命令（仍然為&#x200B;**neolane**）啟動postupgrade進程：

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >您必須指定在配置期間要用作參考的時區（使用&#x200B;**-timezone**&#x200B;選項）。 在本例中，我們使用歐洲／巴黎時區&#x200B;**-timezone:&quot;歐洲／巴黎&quot;**。

   >[!NOTE]
   >
   >我們強烈建議將您的基地升級為「多時區」。 有關時區選項的詳細資訊，請參閱[時區](../../migration/using/general-configurations.md#time-zones)部分。

>[!IMPORTANT]
>
>請勿啟動Adobe Campaign服務：仍需在Apache中進行變更。

### 從Adobe Campaign 6.02 {#migrating-from-adobe-campaign-v6_02-1}版移轉

部署Adobe Campaign需要兩個階段：

* 安裝Adobe Campaign v7套件：必須在每台伺服器上執行此操作。
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
   >您必須成功安裝軟體包，才能繼續下一步。

   >[!NOTE]
   >
   >依預設，Adobe Campaign v7會安裝在與Adobe Campaign v6.02相同的目錄中：**/usr/local/neolane/nl6/**。

1. 若要讓用戶端主控台安裝程式可供使用，請將它複製至Adobe Campaign安裝目錄：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >如需如何在Linux中安裝Adobe Campaign的詳細資訊，請參閱[本節](../../installation/using/installing-campaign-standard-packages.md)。

1. 由於遷移不是一般安裝，因此您需要強制重新啟動&#x200B;**trackinglogd**&#x200B;服務。 若要這麼做，請開啟&#x200B;**nl6/conf/config-default.xml**&#x200B;檔案，並確定&#x200B;**trackinglogd**&#x200B;服務已啟動（僅限在追蹤／重新導向伺服器上）:

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >如果追蹤伺服器上未啟動&#x200B;**trackinglogd**&#x200B;服務，則不會轉送追蹤資訊。

1. 轉至&#x200B;**nl6.back**&#x200B;備份資料夾並複製（覆蓋）每個實例的配置檔案和子資料夾。 以&#x200B;**neolane**&#x200B;的身分登入，然後執行下列命令：

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

1. 使用以下命令（仍然為&#x200B;**neolane**）啟動postupgrade進程：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >「多時區」模式僅在v6.02中適用於PostgreSQL資料庫引擎。 現在，不論使用的資料庫引擎版本為何，都可使用它。 我們強烈建議將您的基地升級為「多時區」。 有關時區選項的詳細資訊，請參閱[時區](../../migration/using/general-configurations.md#time-zones)部分。

### 從Adobe Campaign 6.1 {#migrating-from-adobe-campaign-v6_1-1}版移轉

部署Adobe Campaign需要兩個階段：

* 安裝Adobe Campaign v7套件：必須在每台伺服器上執行此操作。
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
   >您必須成功安裝軟體包，才能繼續下一步。

   >[!NOTE]
   >
   >依預設，Adobe Campaign v7會安裝在&#x200B;**/usr/local/neolane/nl6/**&#x200B;目錄中。

1. 若要讓用戶端主控台安裝程式可供使用，請將它複製至Adobe Campaign安裝目錄：

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >如需如何在Linux中安裝Adobe Campaign的詳細資訊，請參閱[本節](../../installation/using/installing-campaign-standard-packages.md)。

1. 轉至&#x200B;**nl6.back**&#x200B;備份資料夾並複製（覆蓋）每個實例的配置檔案和子資料夾。 以&#x200B;**neolane**&#x200B;的身分登入，然後執行下列命令：

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

1. 使用以下命令（仍然為&#x200B;**neolane**）啟動postupgrade進程：

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## 遷移重定向伺服器(Apache){#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>本節僅適用於從Adobe Campaign 5.11版移轉時。

目前，Apache必須停止。 請參閱：[服務停止](#service-stop)。

1. 以&#x200B;**root**&#x200B;身份登錄。
1. 更改Apache環境變數，使其連結到&#x200B;**nl6**&#x200B;目錄。

   * 在&#x200B;**Debian**&#x200B;中：

      ```
      vi /etc/apache2/envvars
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. 然後執行下列命令：

   * 在&#x200B;**Debian**&#x200B;中：

      在&#x200B;**nlsrv.load**&#x200B;檔案中，將&#x200B;**nl5**&#x200B;取代為&#x200B;**nl6**。

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      刪除&#x200B;**nlsrv.conf**&#x200B;檔案的連結並建立新檔案。

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * 在&#x200B;**Red Hat**&#x200B;中：

      前往&#x200B;**/usr/local/apache2/conf**&#x200B;目錄，編輯&#x200B;**http.conf**&#x200B;檔案，並在下列行中以&#x200B;**nl6**&#x200B;取代&#x200B;**nl5**。

      在&#x200B;**RHEL 7/Debian 8**&#x200B;中：

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. 轉至&#x200B;**alias.conf**&#x200B;檔案，並將所有&#x200B;**nl5**&#x200B;取代為&#x200B;**nl6**。 要在Debian中執行此操作，請運行以下命令：

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## 安全區{#security-zones}

如果您要從v6.02或更舊版本移轉，則必須先設定安全區，才能啟動服務。 有關詳細資訊，請參閱[Security](../../migration/using/general-configurations.md#security)。

## 重新啟動服務{#re-starting-services}

此程式取決於您的Adobe Campaign舊版。

### 從Adobe Campaign 5.11 {#migrating-from-adobe-campaign-v5_11-2}版移轉

在&#x200B;**config-`<instance name>`.xml**&#x200B;檔案中，重新啟動&#x200B;**mta**、**wfserver**、**stat**&#x200B;等的自動啟動。 服務。

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

在下列每部伺服器上啟動Apache和Adobe Campaign服務：

1. 追蹤和重新導向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

在執行下一步之前，請對新安裝執行完整測試，確保沒有回歸，並遵循[一般設定](../../migration/using/general-configurations.md)一節中的所有建議，確保一切正常運作。

### 從Adobe Campaign 6.02 {#migrating-from-adobe-campaign-v6_02-2}版移轉

在&#x200B;**config-`<instance name>`.xml**&#x200B;檔案中，重新啟動&#x200B;**mta**、**wfserver**、**stat**&#x200B;等的自動啟動。 服務。

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

在下列每部伺服器上啟動Apache和Adobe Campaign服務：

1. 追蹤和重新導向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

完全測試新安裝，檢查它是否未重新恢復，並遵循[General configurations](../../migration/using/general-configurations.md)一節中的所有建議，確保所有項目都正常運作。

### 從Adobe Campaign 6.1 {#migrating-from-adobe-campaign-v6_1-2}版移轉

在下列每部伺服器上啟動Apache和Adobe Campaign服務：

1. 追蹤和重新導向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

完全測試新安裝，檢查它是否未重新恢復，並遵循[General configurations](../../migration/using/general-configurations.md)一節中的所有建議，確保所有項目都正常運作。

## 刪除和清除Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>本節僅適用於從Adobe Campaign 5.11版移轉時。

在刪除及清除Adobe Campaign v5安裝之前，您必須套用下列建議：

* 讓功能團隊對新安裝進行完整檢查。
* 只有在您確定不需要回溯時，才能解除安裝Adobe Campaign v5。

刪除&#x200B;**nl5.back**&#x200B;目錄。 以&#x200B;**neolane**&#x200B;的身分登入，然後執行下列命令：

```
su - neolane
rm -rf nl5.back
```

重新啟動伺服器。
