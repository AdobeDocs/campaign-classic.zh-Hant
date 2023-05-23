---
product: campaign
title: 使用 Linux 安裝軟體套件
description: 使用 Linux 安裝軟體套件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 1%

---

# 使用 Linux 安裝軟體套件{#installing-packages-with-linux}



對於Linux 32位平台，請安裝Adobe Campaign32位。 對於Linux 64位平台，請安裝Adobe Campaign64位。

對於每個版本，Adobe Campaign都提供一個軟體包： **nlserver**。 此程式包包含給定版本的二進位檔案和配置檔案。

通過安裝命令，您可以：

* 將檔案複製到 **/usr/local/neolane**
* 建立Adobe CampaignLinux帳戶（和關聯組），該帳戶是 **/usr/local/neolane** 作為其主目錄
* 建立自動指令碼 **/etc/init.d/nlserver6** 或建立系統設備（從20.1開始）。

>[!NOTE]
>
>的 **奈羅烷** 在運行命令之前不能建立系統用戶。 的 **奈羅烷** 用戶在安裝期間自動建立。
>
>的 **家** 連結到的目錄 **奈羅烷** 用戶也在中自動建立 **[!UICONTROL /usr/local/neolane]**。 請確保上面有足夠的空間 **[!UICONTROL /usr/local]** 磁碟（幾GB）。

您可以運行 **平`hostname`** 命令，確保伺服器可以訪問自己。

## 基於RPM包的分發 {#distribution-based-on-rpm--packages}

要將Adobe Campaign安裝到RPM（RHEL、CentOS和SUSE）作業系統上，請應用以下步驟：

1. 你必須先拿到Adobe Campaign的包裹。

   該檔案命名如下，其中 **XXXX** 是Adobe Campaign版本號：

   * **nlserver6-v7-XXXX-0.x86_64.rpm** v7。
   * **nlserver6-XXXX-0.x86_64.rpm** 6.1版。

   >[!CAUTION]
   >
   >確保在本節的命令示例中使用正確的Adobe Campaign版本檔案名。

1. 要安裝它，請連接為 **根** 並執行以下命令(其中 **XXXX** 是Adobe Campaign內部版本號):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm檔案與CentOS/Red Hat分發上可找到的軟體包有依賴關係。 如果不想使用其中的一些依賴項(例如，如果想使用OracleJDK而不是OpenJDK)，則可能必須使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

執行netreport所必需的「bc」命令(請參閱 [此部分](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) )，在所有Linux發行版上都不可用。 要檢查該命令是否可用，請運行「which bc」命令。 否則，必須安裝它。

使用CentOS，必須安裝bc.x86_64軟體包：連接 **根** 並運行以下命令：

```
yum install bc.x86_64
```

## 基於APT(Debian)的分佈 {#distribution-based-on-apt--debian-}

### 在德比64位 {#in-debian-64-bits}

要在Debian 64位作業系統上安裝Adobe Campaign64位，請應用以下步驟：

1. 你必須先拿到Adobe Campaign的包裹。

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** v7。
   * **nlserver6-XXXX-linux-2.6-amd64.deb** 6.1版。

   **XXXX** 是Adobe Campaign的編號。

   >[!CAUTION]
   >
   >確保在本節的命令示例中使用正確的Adobe Campaign版本檔案名。

1. 要安裝它，請連接為 **根** 並執行以下命令(其中 **XXXX** 是Adobe Campaign內部版本號):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果缺少依賴項，請運行以下命令：

   ```
   apt-get install -f
   ```

**德比安8/9細節**

在Debian 8/9作業系統上安裝Adobe Campaign時，請考慮以下事項：

* 必須事先安裝OpenSSL。
* 使用以下命令安裝libicu52(Debian 8)或libicu57(Debian 9)、libprotobuf9(Debian8)和libc-ares2:

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

## 個性化參數 {#personalizing-parameters}

某些參數可通過 **customer.sh** 檔案

如果是首次執行安裝， **customer.sh** 伺服器上可能尚不存在檔案。 建立它並確保它具有執行權限。 如果不是這樣，請輸入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 伺服器編碼 {#server-encoding}

預設情況下，伺服器在iso8859-15環境中啟動。 但是，伺服器可以在UTF-8環境中啟動。

>[!CAUTION]
>
>此更改影響與檔案系統（通過工作流或JavaScript指令碼載入的檔案）的交互和檔案編碼。 因此，我們建議使用預設環境。

然而，為了創造 **日語實例**，必須使用UTF-8環境。

要啟用UTF-8環境，請使用以下命令：

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### 伺服器的預設語言 {#default-language-for-the-server}

安裝支援英語和法語。 預設情況下使用英語。

要切換到法語，請輸入以下命令：

```
su - neolane
vi nl6/customer.sh
```

並添加以下行：

```
export neolane_LANG=fra
```

為確保正確讀取系統消息，控制台必須位於與語言（法語為ISO-8859-1或–15）對應的代碼頁中。

### 環境變數 {#environment-variables}

必須正確定義以下環境變數。

某些組合要求對用於執行Adobe Campaign的環境進行更改。 特定檔案(`/usr/local/neolane/nl6/customer.sh`)，以添加特定於Adobe Campaign環境的修改。

如有必要，請編輯 **customer.sh** 檔案 **vi customer.sh** 命令並調整配置或添加缺少的行：

* 對於Oracle客戶端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   oracle_HOME環境變數的內容與Oracle安裝目錄匹配。

   TNS_ADMIN變數的內容必須與 **tnsnames.ora** 的子菜單。

* 對於LibreOffice:

   要在現有版本的LibreOffice上運行Adobe Campaign，需要其他配置：您需要指定到安裝目錄的訪問路徑。 例如：

   * Debian

      提供了OOO_INSTALL_DIR和OOO_BASIS_INSTALL_DIR的預設值。 可以在 **customer.sh** 如果LibreOffice安裝的佈局不同：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      ```

   * CentOs

      使用以下預設值：

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      ```

* 對於Java開發工具包(JDK):

   預設情況下，Adobe Campaign環境的配置指令碼(`~/nl6/env.sh`)搜索JDK安裝目錄。 由於此行為不是100%可靠，因此需要指定需要使用哪些JDK。 為此，您可以強制 **JDK_HOME** 環境變數使用以下命令：

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >這是一個例子。 確保使用的JDK版本與目錄名稱匹配。

   要testJDK配置，請使用以下命令以Adobe Campaign系統用戶身份登錄：

   ```
   su - neolane
   ```

必須重新啟動Adobe Campaign服務，才能將更改考慮在內。

命令如下：

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

從20.1開始，我們建議改用以下命令：

```
systemctl stop nlserver
systemctl start nlserver
```

### OracleLinux客戶端 {#oracle-client-in-linux}

在與Adobe CampaignOracle時，需要在Linux中配置Oracle客戶端層。

* 使用完整客戶端
* TNS定義

   在安裝階段必須添加TNS定義。 為此，請使用以下命令：

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* 環境變數

   請參閱 [環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables)。

* Adobe Campaign配置

   要完成Adobe CampaignOracle客戶端的安裝，您需要為 **.so** 檔案由Adobe Campaign使用。

   為此，請使用以下命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果遇到問題，請確保在 [Oracle安裝文檔](https://docs.oracle.com/) 已正確安裝。

## 安裝檢查 {#installation-checks}

現在，您可以使用以下命令執行初始安裝test:

```
su - neolane
nlserver pdump
```

當Adobe Campaign未啟動時，響應是：

```
no task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝test完成後，輸入以下命令：

```
nlserver web
```

然後顯示以下資訊：

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

這些命令允許您建立 **config-default.xml** 和 **serverConf.xml** 配置檔案。 中的所有可用參數 **serverConf.xml** 列在 [節](../../installation/using/the-server-configuration-file.md)。

按 **Ctrl+C** 要停止進程，請輸入以下命令：

```
nlserver start web
```

然後顯示以下資訊：

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

然後顯示以下資訊：

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 內部標識符的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器定義名為 **內部** 對所有情況都擁有所有權。 安裝後登錄名沒有密碼。 必須定義一個。

在[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)了解更多資訊。
