---
product: campaign
title: 使用Linux安裝套件
description: 使用Linux安裝套件
feature: Installation, Application Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 0%

---

# 使用Linux安裝套件{#installing-packages-with-linux}

Adobe Campaign隨附 **nlserver** 包含指定版本的二進位檔和組態檔的套件。

安裝指令可讓您：

* 將檔案複製到 **/usr/local/neolane**
* 建立Adobe Campaign Linux帳戶（及相關群組），此帳戶建立方式 **/usr/local/neolane** 作為主目錄
* 建立自動指令碼 **/etc/init.d/nlserver6** 啟動時使用，或建立系統單元

>[!NOTE]
>
>此 **neolane** 執行命令之前不能建立系統使用者。 此 **neolane** 使用者會在安裝期間自動建立。
>
>此 **home** 連結至 **neolane** 使用者也會在中自動建立 **[!UICONTROL /usr/local/neolane]**. 請確定上有足夠的空間 **[!UICONTROL /usr/local]** 磁碟。

您可以執行 **ping`hostname`** 命令來確保伺服器可以連線到自己。

## 根據RPM套件的分佈 {#distribution-based-on-rpm--packages}

若要將Adobe Campaign安裝在RPM (RHEL、CentOS)作業系統上，請執行下列步驟：

1. 取得Adobe Campaign套件。 檔案的名稱為 **nlserver6-v7-XXXX-0.x86_64.rpm**，其中 **XXXX** 是Adobe Campaign版本編號。

   >[!CAUTION]
   >
   >在本節的命令範例中，請確定您的Adobe Campaign版本使用了正確的檔案名稱。

1. 若要安裝，請連線為 **根** 並執行下列指令，其中 **XXXX** 是Adobe Campaign版本編號：

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm檔案與您可以在CentOS/Red Hat分配上找到的套裝程式相依性。 如果您不想使用其中的部分相依性(例如，如果要使用OracleJDK而非OpenJDK)，則可能需要使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

此 `bc` 命令，執行 [網路報表](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)預設情況下，並非所有Linux發行版本都可使用。 若要檢查指令是否可用，請執行 `which bc` 命令。 如果沒有，您必須安裝。

使用CentOS時，您必須安裝bc.x86_64套件：連線為 **根** 並執行下列命令：

```
yum install bc.x86_64
```

## 根據APT (Debian)的分發 {#distribution-based-on-apt--debian-}

若要在Debian 64位元作業系統上安裝Adobe Campaign，請套用下列步驟：

1. 取得Adobe Campaign套件。 檔案的名稱為 **nlserver6-v7-XXXX-linux-2.6-amd64.deb**，其中 **XXXX** 是Adobe Campaign版本編號。

   >[!CAUTION]
   >
   >在本節的命令範例中，請確定您的Adobe Campaign版本使用了正確的檔案名稱。

1. 若要安裝，請連線為 **根** 並執行下列指令，其中 **XXXX** 是Adobe Campaign版本編號：

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果遺失相依性，請執行以下命令：

   ```
   apt-get install -f
   ```


1. 在Debian作業系統上安裝Adobe Campaign時，請考量下列事項：

* 必須先安裝OpenSSL。
* 使用下列指令安裝libicu和libc-aresYY （其中XX是版本）：

  ```
  apt install libicuXX
  ```

  ```
  apt install libc-aresXX
  ```

  ```
  apt install openjdk-XX-jdk
  ```

## 個人化引數 {#personalizing-parameters}

部分引數可透過以下方式個人化： **customer.sh** 檔案

如果您是第一次執行安裝， **customer.sh** 檔案可能尚未存在於伺服器上。

建立它，並確定它有執行許可權。 如果不是這種情況，請輸入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 伺服器編碼 {#server-encoding}

依預設，伺服器會在iso8859-15環境中啟動。 不過，伺服器可以在UTF-8環境中啟動。

>[!CAUTION]
>
>此變更會影響與檔案系統（透過工作流程或JavaScript指令碼載入的檔案）的互動以及檔案編碼。 因此，我們建議使用預設環境。

若要建立 **日文例項**，您必須使用UTF-8環境。

若要啟用UTF-8環境，請使用以下命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 環境變數 {#environment-variables}

必須正確定義下列環境變數。

某些組合需要變更用於執行Adobe Campaign的環境。 特定檔案(`/usr/local/neolane/nl6/customer.sh`)可建立並編輯以新增Adobe Campaign環境的特定修改。

如有需要，請編輯 **customer.sh** 檔案使用 **vi customer.sh** 命令並調整設定或新增缺少的行：

* 對於Oracle使用者端：

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  oracle_HOME環境變數的內容與Oracle安裝目錄相符。

  TNS_ADMIN變數的內容必須與 **tnsnames.ora** 檔案。

* 若為LibreOffice：

  若要在現有LibreOffice版本上執行Adobe Campaign，需要進行其他設定：您必須指定安裝目錄的存取路徑。 例如：

   * Debian

     提供了OOO_INSTALL_DIR和OOO_BASIS_INSTALL_DIR的預設值。 您可以在中覆寫它們 **customer.sh** 如果您的LibreOffice安裝版面配置不同：

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     使用下列預設值：

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* 適用於Java開發套件(JDK)：

  依預設，Adobe Campaign環境的設定指令碼(`~/nl6/env.sh`)會搜尋JDK安裝目錄。 不過，建議您指定需要使用的JDK。 若要這麼做，您可以強制 **JDK_HOME** 環境變數（使用以下命令）：

  ```
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >請確定使用的JDK版本符合目錄名稱。

  若要測試JDK設定，請使用以下命令以Adobe Campaign系統使用者身分登入：

  ```
  su - neolane
  ```

您必須重新啟動Adobe Campaign服務，才能將變更納入考量。

命令如下：

```
systemctl stop nlserver
systemctl start nlserver
```

### Linux中的Oracle使用者端 {#oracle-client-in-linux}

搭配Adobe Campaign使用Oracle時，您需要在Linux中設定Oracle使用者端層。

* 使用完整使用者端
* TNS定義

  TNS定義必須在安裝階段新增。 要執行此操作，請使用下列命令：

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* 環境變數

  請參閱 [環境變數](#environment-variables).

* Adobe Campaign的設定

  若要完成Adobe CampaignOracle使用者端的安裝，您需要為 **.so** Adobe Campaign使用的檔案。

  要執行此操作，請使用下列命令：

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

如果發生問題，請確定Oracle安裝檔案中列出的套件已正確安裝。

## 安裝檢查 {#installation-checks}

您現在可以使用下列指令執行初始安裝測試：

```
su - neolane
nlserver pdump
```

Adobe Campaign未啟動時，回應為：

```
no task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝測試完成後，輸入下列命令：

```
nlserver web
```

接著會顯示下列資訊：

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

這些指令可讓您建立 **config-default.xml** 和 **serverConf.xml** 組態檔。 所有引數都可在 **serverConf.xml** 列於此 [區段](../../installation/using/the-server-configuration-file.md).

按下 **Ctrl+C** 若要停止程式，請輸入下列命令：

```
nlserver start web
```

接著會顯示下列資訊：

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

若要停止，請輸入：

```
nlserver stop web
```

接著會顯示下列資訊：

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 內部識別碼的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器會定義名為的技術登入 **內部** 擁有所有執行個體的所有權利。 安裝之後，登入沒有密碼。 必須定義一個。

若要了解詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。
