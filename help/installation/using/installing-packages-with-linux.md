---
product: campaign
title: 使用 Linux 安裝軟體套件
description: 使用 Linux 安裝軟體套件
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: fbab510788abe0fccbbd791233c906e7f9d8d703
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 1%

---

# 使用 Linux 安裝軟體套件{#installing-packages-with-linux}

![](../../assets/v7-only.svg)

若為Linux 32位元平台，請安裝Adobe Campaign 32位元。 對於Linux 64位元平台，請安裝Adobe Campaign 64位元。

Adobe Campaign針對每個版本都隨附一個套件： **nlserver**. 此套件包含指定版本的二進位檔和組態檔。

安裝命令允許您：

* 將檔案複製到 **/usr/local/neolane**
* 建立Adobe Campaign Linux帳戶（和關聯群組），此帳戶是以 **/usr/local/neolane** 作為主目錄
* 建立自動指令碼 **/etc/init.d/nlserver6** 供啟動時使用，或建立系統單元（從20.1開始）。

>[!NOTE]
>
>此 **奈羅蘭** 在運行命令之前，不能建立系統用戶。 此 **奈羅蘭** 安裝期間會自動建立使用者。
>
>此 **home** 連結到的目錄 **奈羅蘭** 使用者也會在 **[!UICONTROL /usr/local/neolane]**. 請確定上有足夠的空間 **[!UICONTROL /usr/local]** 磁碟（數GB）。

您可以執行 **ping`hostname`** 命令，確保伺服器可以到達自己。

## 基於RPM包的分發 {#distribution-based-on-rpm--packages}

要將Adobe Campaign安裝到RPM（RHEL、CentOS和SUSE）作業系統上，請應用以下步驟：

1. 您必須先取得Adobe Campaign套件。

   檔案的名稱如下，其中 **XXXX** 是Adobe Campaign編號：

   * **nlserver6-v7-XXXX-0.x86_64.rpm** 適用於v7。
   * **nlserver6-XXXX-0.x86_64.rpm** 適用於v6.1。

   >[!CAUTION]
   >
   >請務必在本區段的命令範例中，為您版本的Adobe Campaign使用正確的檔案名稱。

1. 若要安裝，請以 **根** 並執行以下命令(其中 **XXXX** 是Adobe Campaign組建編號):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm檔案對包具有依賴性，您可以在CentOS/Red Hat分發上找到這些包。 如果您不想使用其中的某些相依性(例如，如果您想使用OracleJDK而非OpenJDK)，則可能需要使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

執行netreport所需的&#39;bc&#39;命令(請參閱 [本節](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) )，預設不適用於所有Linux發行版本。 要檢查該命令是否可用，請運行「which bc」命令。 如果沒有，則必須安裝它。

使用CentOS時，必須安裝bc.x86_64包：連接為 **根** 並運行以下命令：

```
yum install bc.x86_64
```

## 根據APT(Debian)進行分發 {#distribution-based-on-apt--debian-}

### Debian 64位元 {#in-debian-64-bits}

若要在Debian 64位元作業系統上安裝Adobe Campaign 64位元，請套用下列步驟：

1. 您必須先取得Adobe Campaign套件。

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** 適用於v7。
   * **nlserver6-XXXX-linux-2.6-amd64.deb** 適用於v6.1。

   **XXXX** 是Adobe Campaign組建編號。

   >[!CAUTION]
   >
   >請務必在本區段的命令範例中，為您版本的Adobe Campaign使用正確的檔案名稱。

1. 若要安裝，請以 **根** 並執行以下命令(其中 **XXXX** 是Adobe Campaign組建編號):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果缺少依賴項，請運行以下命令：

   ```
   apt-get install -f
   ```

**Debian 8/9細節**

在Debian 8/9作業系統上安裝Adobe Campaign時，請考慮下列事項：

* 必須預先安裝OpenSSL。
* 使用下列命令安裝libicu52(Debian 8)或libicu57(Debian 9)、libprotobuf9(Debian8)和libc-ares2 :

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* 使用以下命令安裝JDK7:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## 個人化參數 {#personalizing-parameters}

有些參數可透過 **customer.sh** 檔案

如果您是第一次執行安裝，則 **customer.sh** 伺服器上可能尚未存在檔案。 建立它，並確定它具有執行權限。 如果不是，請輸入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 伺服器編碼 {#server-encoding}

預設情況下，伺服器在iso8859-15環境中啟動。 不過，伺服器可以在UTF-8環境中啟動。

>[!CAUTION]
>
>此變更會影響與檔案系統（透過工作流程或JavaScript指令碼載入的檔案）的互動以及檔案編碼。 因此，建議使用預設環境。

然而，為了建立 **日文例項**，您必須使用UTF-8環境。

若要啟用UTF-8環境，請使用下列命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 伺服器的預設語言 {#default-language-for-the-server}

安裝支援英文和法文。 預設會使用英文。

要切換為法文，請輸入以下命令：

```
su - neolane
vi nl6/customer.sh
```

並新增下列行：

```
export neolane_LANG=fra
```

為確保系統消息被正確讀取，控制台必須位於與語言對應的代碼頁中（法文為ISO-8859-1或–15）。

### 環境變數 {#environment-variables}

必須正確定義下列環境變數。

某些組合需要變更執行Adobe Campaign所用的環境。 特定檔案(`/usr/local/neolane/nl6/customer.sh`)即可建立及編輯，以新增Adobe Campaign環境專屬的修改。

如有必要，請編輯 **customer.sh** 檔案，使用 **vi customer.sh** 命令和調整配置或添加遺漏行：

* 對於Oracle客戶端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   oracle_HOME環境變數的內容與Oracle安裝目錄匹配。

   TNS_ADMIN變數的內容必須符合 **tnsnames.ora** 檔案。

* 對於LibreOffice:

   若要在現有版本的LibreOffice上執行Adobe Campaign，需要其他配置：您需要指定安裝目錄的訪問路徑。 例如：

   * Debian

      提供了OOO_INSTALL_DIR和OOO_BASIS_INSTALL_DIR的預設值。 您可以在 **customer.sh** 如果LibreOffice安裝的佈局不同：

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

* 針對Java開發套件(JDK):

   依預設，Adobe Campaign環境的設定指令碼(`~/nl6/env.sh`)搜索JDK安裝目錄。 由於此行為並非100%可靠，因此您需要指定需要使用哪些JDK。 若要這麼做，您可以強制 **JDK_HOME** 環境變數，使用下列命令：

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >這是一個例子。 請確定使用的JDK版本與目錄名稱相符。

   要測試JDK配置，請使用以下命令以Adobe Campaign系統用戶身份登錄：

   ```
   su - neolane
   ```

您必須重新啟動Adobe Campaign服務，才能將變更納入考量。

命令如下：

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

從20.1開始，我們建議改用下列命令：

```
systemctl stop nlserver
systemctl start nlserver
```

### OracleLinux中的客戶端 {#oracle-client-in-linux}

將Oracle與Adobe Campaign搭配使用時，您需要在Linux中設定Oracle用戶端層。

* 使用完整客戶端
* TNS定義

   在安裝階段，必須添加TNS定義。 要執行此操作，請使用下列命令：

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* 環境變數

   請參閱 [環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Adobe Campaign組態

   若要完成Adobe Campaign的Oracle用戶端安裝，您必須為 **.so** 檔案供Adobe Campaign使用。

   要執行此操作，請使用下列命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果您遇到問題，請確定 [Oracle安裝檔案](https://docs.oracle.com/) 已正確安裝。

## 安裝檢查 {#installation-checks}

您現在可以使用以下命令執行初始安裝測試：

```
su - neolane
nlserver pdump
```

當Adobe Campaign未啟動時，回應為：

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

這些命令可讓您建立 **config-default.xml** 和 **serverConf.xml** 組態檔。 中所有可用的參數 **serverConf.xml** 列於此 [節](../../installation/using/the-server-configuration-file.md).

Press **Ctrl+C** 要停止進程，請輸入以下命令：

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

若要停止，請輸入：

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

## 內部標識符的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器會定義技術登入，稱為 **內部** 在所有情況下均具有所有權利。 安裝後登錄名沒有密碼。 必須定義一個。

深入了解 [本節](../../installation/using/configuring-campaign-server.md#internal-identifier).
