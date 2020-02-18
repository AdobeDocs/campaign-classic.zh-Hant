---
title: 使用Linux安裝軟體包
seo-title: 使用Linux安裝軟體包
description: 使用Linux安裝軟體包
seo-description: null
page-status-flag: never-activated
uuid: d83f00b5-500b-406a-a3d6-ea5639f244f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 04faa9f3-d160-4060-b26e-44333f2faf71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# 使用Linux安裝軟體包{#installing-packages-with-linux}

若是Linux 32位元平台，請安裝Adobe Campaign 32位元。 若是Linux 64位元平台，請安裝Adobe Campaign 64位元。

Adobe Campaign針對上述各個版本都提供一個套件： **nlserver**。 此套件包含特定版本的二進位檔和設定檔。

使用安裝命令，您可以：

* 將檔案複製到 **/usr/local/neolane**
* 建立Adobe Campaign linux帳戶（及相關群組），以 **/usr/local/neolane** 為首頁目錄建立
* 建立自動指令 **碼/etc/init.d/nlserver6** ，以便在啟動時使用，或建立系統單元（從20.1開始）。

>[!NOTE]
>
>在 **運行命令之前** ，不能建立Neolane系統用戶。 在安 **裝期間** ，會自動建立Neolane使用者。
>
>連結 **到Neolane用戶** 的Home目錄 **，也會在中自動建立****[!UICONTROL /usr/local/neolane]**。 請確定磁碟上有足夠的空 **[!UICONTROL /usr/local]** 間（數GB）。

您可以運行 **ping`hostname`**命令，確保伺服器可以自行訪問。

## 基於RPM包的分發 {#distribution-based-on-rpm--packages}

若要將Adobe Campaign安裝至RPM（RHEL、CentOS和SUSE）作業系統，請套用下列步驟：

1. 您必須先取得Adobe Campaign套件。

   檔案命名如下，其中 **XXXX** 是Adobe Campaign組建編號：

   * **v7的nlserver6-v7-XXXX-0.x86_64.rpm** 。
   * **v6.1的nlserver6-XXXX-0.x86_64.rpm** 。
   >[!CAUTION]
   >
   >請務必在本節的命令範例中，針對您的Adobe Campaign版本使用正確的檔案名稱。

1. 若要安裝它，請以 **root用戶身** 份連接並執行下列命令(其中 **XXXX** 是Adobe Campaign組建編號):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm檔案對包具有依賴性，您可以在CentOS/Red hat分發上找到這些包。 如果您不想使用其中某些相關性（例如，如果想使用Oracle JDK而不是OpenJDK），則可能必須使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

執行netreport所需的&#39;bc&#39;命令(如需詳細資 [訊](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) ，請參閱本節)，在所有Linux散發版本上都不提供。 要檢查命令是否可用，請運行「which bc」命令。 否則，您必須安裝它。

使用CentOS時，您必須安裝bc.x86_64套件：以root身 **份連接** ，然後執行下列命令：

```
yum install bc.x86_64
```

## 基於APT(Debian)的分發 {#distribution-based-on-apt--debian-}

### 在德比安64位 {#in-debian-64-bits}

若要在Debian 64位元作業系統上安裝Adobe Campaign 64位元，請套用下列步驟：

1. 您必須先取得Adobe Campaign套件。

   * **v7適用的nlserver6-v7-XXXX-linux-2.6-amd64.deb** 。
   * **v6.1適用的nlserver6-XXXX-linux-2.6-amd64.deb** 。
   **XXXX** 是Adobe Campaign組建編號。

   >[!CAUTION]
   >
   >請務必在本節的命令範例中，針對您的Adobe Campaign版本使用正確的檔案名稱。

1. 若要安裝它，請以 **root用戶身** 份連接並執行下列命令(其中 **XXXX** 是Adobe Campaign組建編號):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果缺少相關性，請運行以下命令：

   ```
   apt-get install -f
   ```

**德比安8/9細節**

在Debian 8/9作業系統上安裝Adobe Campaign時，請考慮下列事項：

* 必須事先安裝OpenSSL。
* 使用下列命令安裝libicu52(Debian 8)或libicu57(Debian 9)、libprotobuf9(Debian 8)和libc-ares2:

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* 使用下列命令安裝JDK7:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## 個人化參數 {#personalizing-parameters}

部分參數可透過 **customer.sh檔案個人化** 。

如果您是第一次執行安裝， **customer.sh** 檔案可能尚未在伺服器上存在。 建立它並確定它具有執行權限。 如果不是這樣，請輸入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 伺服器編碼 {#server-encoding}

依預設，伺服器會在iso8859-15環境中啟動。 不過，伺服器可以在UTF-8環境中啟動。

>[!CAUTION]
>
>這項變更會影響與檔案系統（透過工作流程或JavaScript指令碼載入的檔案）的互動以及檔案編碼。 因此，我們建議使用預設環境。

不過，若要建立 **日文例項**，您必須使用UTF-8環境。

若要啟用UTF-8環境，請使用下列命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 伺服器的預設語言 {#default-language-for-the-server}

安裝支援英文和法文。 英文預設為使用。

要切換到法語，請輸入以下命令：

```
su - neolane
vi nl6/customer.sh
```

並新增下列行：

```
export neolane_LANG=fra
```

為確保系統消息正確讀取，控制台必須位於與語言對應的代碼頁面中（法語為ISO-8859-1或-15）。

### 環境變數 {#environment-variables}

必須正確定義以下環境變數。

某些組合需要變更用於執行Adobe Campaign的環境。 您可以建立和編`/usr/local/neolane/nl6/customer.sh`輯特定檔案()，以新增Adobe Campaign環境的特定修改。

如有必要，請 **使用vi customer.sh命令編輯****** customer.sh檔案，並調整配置或添加缺少的行：

* 對於Oracle客戶端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   ORACLE_HOME環境變數的內容與Oracle安裝目錄匹配。

   TNS_ADMIN變數的內容必須與 **tnsnames.ora檔案的位置匹配** 。

* 對於LibreOffice:

   若要在現有版本的LibreOffice上執行Adobe Campaign，需要其他設定：您需要指定到安裝目錄的訪問路徑。 例如：

   * 德比安

      提供了OOO_INSTALL_DIR、OOO_BASIS_INSTALL_DIR、OOO_URE_INSTALL_DIR的預設值。 如果您的LibreOffice安裝 **版面不同** ，您可以在customer.sh中覆寫它們：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      使用下列預設值：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* 針對Java開發套件(JDK):

   依預設，Adobe Campaign環境(`~/nl6/env.sh`)的組態指令碼會搜尋JDK安裝目錄。 由於此行為不是100%可靠，因此您需要指定需要使用的JDK。 要執行此操作，可以使用以 **下命令強制JDK_HOME** 環境變數：

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >這就是一個例子。 請確定使用的JDK版本與目錄名稱相符。

   若要測試JDK設定，請使用下列命令以Adobe Campaign系統使用者身分登入：

   ```
   su - neolane
   ```

您必須重新啟動Adobe Campaign服務，才能將變更納入考量。

這些命令如下：

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

從20.1開始，建議改用下列命令：

```
systemctl stop nlserver
systemctl start nlserver
```

### Linux中的Oracle客戶端 {#oracle-client-in-linux}

將Oracle與Adobe Campaign一起使用時，您需要在Linux中配置Oracle客戶端層。

* 使用完整用戶端
* TNS定義

   TNS定義必須在安裝階段添加。 若要這麼做，請使用下列命令：

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* 環境變數

   請參閱環 [境變數](../../installation/using/installing-packages-with-linux.md#environment-variables)。

* Adobe Campaign的設定

   若要完成Adobe Campaign的Oracle用戶端安裝，您必須為Adobe Campaign使用的 **.so** 檔案建立符號連結。

   若要這麼做，請使用下列命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果遇到問題，請確保 [Oracle安裝文檔中列出的軟體包](https://www.oracle.com/pls/db112/portal.portal_db?selected=11) 已正確安裝。

## 安裝檢查 {#installation-checks}

您現在可以使用下列命令執行初始安裝測試：

```
su - neolane
nlserver pdump
```

當Adobe Campaign未啟動時，回應是：

```
no task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝測試完成後，輸入以下命令：

```
nlserver web
```

接著會顯示下列資訊：

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

這些命令可讓您 **建立config-default.xml****和serverConf.xml** 組態檔。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

按 **Ctrl+C** 停止進程，然後輸入以下命令：

```
nlserver start web
```

接著會顯示下列資訊：

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

要停止，請輸入：

```
nlserver stop web
```

接著會顯示下列資訊：

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 內部識別碼的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器會定義名為內部的技術登 **入** ，此登入具有所有例項的所有權限。 在安裝後，登入就沒有密碼。 必須定義一個。

請參閱「內 [部識別碼](../../installation/using/campaign-server-configuration.md#internal-identifier)」一節。
