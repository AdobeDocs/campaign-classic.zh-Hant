---
product: campaign
title: 使用 Linux 安裝軟體套件
description: 使用 Linux 安裝軟體套件
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 1%

---

# 使用 Linux 安裝軟體套件{#installing-packages-with-linux}

![](../../assets/v7-only.svg)

若為Linux 32位元平台，請安裝Adobe Campaign 32位元。 對於Linux 64位元平台，請安裝Adobe Campaign 64位元。

Adobe Campaign針對每個版本都隨附一個套件：**nlserver**。 此套件包含指定版本的二進位檔和組態檔。

安裝命令允許您：

* 將檔案複製到&#x200B;**/usr/local/neolane**
* 建立Adobe Campaign Linux帳戶（和相關組），該帳戶以&#x200B;**/usr/local/neolane**&#x200B;作為其主目錄
* 建立自動指令碼&#x200B;**/etc/init.d/nlserver6**&#x200B;以在啟動時使用，或建立系統單元（從20.1開始）。

>[!NOTE]
>
>**neolane**&#x200B;系統用戶必須在命令運行之前尚未建立。 在安裝期間會自動建立&#x200B;**neolane**&#x200B;使用者。
>
>連結到&#x200B;**neolane**&#x200B;用戶的&#x200B;**home**&#x200B;目錄也在&#x200B;**[!UICONTROL /usr/local/neolane]**&#x200B;中自動建立。 請確保&#x200B;**[!UICONTROL /usr/local]**&#x200B;磁碟上有足夠的空間（數GB）。

您可以執行&#x200B;**ping`hostname`**&#x200B;命令，確保伺服器可以到達自己。

## 基於RPM包的分發 {#distribution-based-on-rpm--packages}

要將Adobe Campaign安裝到RPM（RHEL、CentOS和SUSE）作業系統上，請應用以下步驟：

1. 您必須先取得Adobe Campaign套件。

   檔案的名稱如下，其中&#x200B;**XXXX**&#x200B;是Adobe Campaign組建編號：

   * **nlserver6-v7-XXXX-0.x86_64.** rpmfor v7。
   * **nlserver6-XXXX-0.x86_64.** rpmfor v6.1。

   >[!CAUTION]
   >
   >請務必在本區段的命令範例中，為您版本的Adobe Campaign使用正確的檔案名稱。

1. 若要安裝，請以&#x200B;**root**&#x200B;連線並執行下列命令(其中&#x200B;**XXXX**&#x200B;是Adobe Campaign組建編號):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   rpm檔案對包具有依賴性，您可以在CentOS/Red Hat分發上找到這些包。 如果您不想使用其中的某些相依性(例如，如果您想使用OracleJDK而非OpenJDK)，則可能需要使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

執行netreport所需的&#39;bc&#39;命令（有關詳細資訊，請參閱[此部分](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)）預設不適用於所有Linux分發。 要檢查該命令是否可用，請運行「which bc」命令。 如果沒有，則必須安裝它。

使用CentOS時，必須安裝bc.x86_64包：以&#x200B;**root**&#x200B;連接並運行以下命令：

```
yum install bc.x86_64
```

## 根據APT(Debian)進行分發 {#distribution-based-on-apt--debian-}

### Debian 64位元 {#in-debian-64-bits}

若要在Debian 64位元作業系統上安裝Adobe Campaign 64位元，請套用下列步驟：

1. 您必須先取得Adobe Campaign套件。

   * **nlserver6-v7-XXXX-linux-2.6-amd64.** debfor v7。
   * **nlserver6-XXXX-linux-2.6-amd64.** debfor v6.1。

   **** XXXX是Adobe Campaign版本編號。

   >[!CAUTION]
   >
   >請務必在本區段的命令範例中，為您版本的Adobe Campaign使用正確的檔案名稱。

1. 若要安裝，請以&#x200B;**root**&#x200B;連線並執行下列命令(其中&#x200B;**XXXX**&#x200B;是Adobe Campaign組建編號):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   如果缺少相關性，請運行以下命令：

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

有些參數可透過&#x200B;**customer.sh**&#x200B;檔案個人化

如果您是第一次執行安裝，伺服器上可能尚未存在&#x200B;**customer.sh**&#x200B;檔案。 建立它，並確定它具有執行權限。 如果不是，請輸入以下命令：

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### 伺服器編碼 {#server-encoding}

預設情況下，伺服器在iso8859-15環境中啟動。 不過，伺服器可以在UTF-8環境中啟動。

>[!CAUTION]
>
>此變更會影響與檔案系統（透過工作流程或JavaScript指令碼載入的檔案）的互動以及檔案編碼。 因此，建議使用預設環境。

不過，若要建立&#x200B;**日文例項**，您必須使用UTF-8環境。

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

某些組合需要變更執行Adobe Campaign所用的環境。 可以建立並編輯特定檔案(`/usr/local/neolane/nl6/customer.sh`)，以新增Adobe Campaign環境特有的修改。

如有必要，請使用&#x200B;**vi customer.sh**&#x200B;命令編輯&#x200B;**customer.sh**&#x200B;檔案，並調整配置或添加遺漏的行：

* 對於Oracle客戶端：

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   oracle_HOME環境變數的內容與Oracle安裝目錄匹配。

   TNS_ADMIN變數的內容必須與&#x200B;**tnsnames.ora**&#x200B;檔案的位置匹配。

* 對於LibreOffice:

   若要在現有版本的LibreOffice上執行Adobe Campaign，需要其他配置：您需要指定安裝目錄的訪問路徑。 例如：

   * Debian

      提供了OOO_INSTALL_DIR、OOO_BASIS_INSTALL_DIR、OOO_URE_INSTALL_DIR的預設值。 如果您的LibreOffice安裝佈局不同，則可以在&#x200B;**customer.sh**&#x200B;中覆蓋它們：

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

   預設情況下，Adobe Campaign環境的配置指令碼(`~/nl6/env.sh`)會搜索JDK安裝目錄。 由於此行為並非100%可靠，因此您需要指定需要使用哪些JDK。 要執行此操作，可以使用以下命令強制&#x200B;**JDK_HOME**&#x200B;環境變數：

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

   請參閱[環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables)。

* Adobe Campaign組態

   若要完成Adobe Campaign的Oracle用戶端安裝，您需要為Adobe Campaign使用的&#x200B;**.so**&#x200B;檔案建立符號連結。

   要執行此操作，請使用下列命令：

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

如果您遇到問題，請確保[Oracle安裝文檔](https://docs.oracle.com/)中列出的包已正確安裝。

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

這些命令可讓您建立&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;組態檔。 **serverConf.xml**&#x200B;中所有可用的參數都列在此[節](../../installation/using/the-server-configuration-file.md)中。

按&#x200B;**Ctrl+C**&#x200B;停止進程，然後輸入以下命令：

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

Adobe Campaign伺服器定義名為&#x200B;**internal**&#x200B;的技術登入，該登入在所有執行個體上都具有所有權限。 安裝後登錄名沒有密碼。 必須定義一個。

進一步了解[本節](../../installation/using/configuring-campaign-server.md#internal-identifier)。
