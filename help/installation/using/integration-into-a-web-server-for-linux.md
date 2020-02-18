---
title: 與Linux網頁伺服器整合
seo-title: 與Linux網頁伺服器整合
description: 與Linux網頁伺服器整合
seo-description: null
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a37daa8e31afd3d2ab7d5b70bd8ae02c59ce9ee0

---


# 與Linux網頁伺服器整合{#integration-into-a-web-server-for-linux}

Adobe Campaign包含Apache Tomcat，可透過HTTP（和SOAP）在應用程式伺服器中當做入口點。

您可以使用此整合的Tomcat伺服器來服務HTTP請求。

在本例中：

* 預設監聽埠為8080。 要更改它，請參 [閱Configuring Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat)。
* 然後，用戶端主控台會使用URL進行連線，例如：

   ```
   http://<computer>:8080
   ```

不過，出於安全性和管理原因，我們建議使用專用的Web伺服器作為HTTP流量的主要入口點，因為執行Adobe Campaign的電腦在網際網路上公開，而且您想要在網路外開啟主控台的存取權。

Web伺服器也可讓您使用HTTP通訊協定來保證資料的機密性。

同樣地，當您想要使用追蹤功能時，必須使用Web伺服器，此功能僅能做為Web伺服器的擴充模組。

>[!NOTE]
>
>如果您不使用追蹤功能，則可執行Apache或IIS的標準安裝，並重新導向至促銷活動。 不需要追蹤Web伺服器擴充模組。

## 使用Debian配置Apache web伺服器 {#configuring-the-apache-web-server-with-debian}

如果您已在基於APT的分發下安裝Apache，則此程式適用。

應用以下步驟：

1. 使用以下命令禁用預設載入的模組：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   請確定 **別名**、authz_host **和** mime **** 模組仍處於啟用狀態。 為此，請使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 在 **/etc/apache2/mods-available中建立檔案nlsrv.load****** ，並插入以下內容：

   在德比安8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 使用下 **列命令在** /etc/apache2/mods-available中建立檔案 **** nlsrv.conf:

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用以下命令激活此模組：

   ```
    a2enmod nlsrv
   ```

   如果您使用Adobe Campaign頁的 **mod_rewrite** module，則需要將 **nlsrv.rewrite** 和 **nlsrv.conf檔案更名為** lsrv. ******** nzz和Zz-Nsrv.conf載入重新命名為Jadobe Campaign頁面。 要激活模組，請運行以下命令：

   ```
   a2enmod zz-nlsrv
   ```

1. 編輯 **/etc/apache2/envvars** 檔案，新增下列行：

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   儲存變更。

1. 然後使用下列命令類型，將Adobe Campaign使用者新增至Apache使用者群組，反之亦然：

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. 重新啟動Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## 在RHEL中配置Apache web伺服器 {#configuring-apache-web-server-in-rhel}

如果您已在基於RPM（RHEL、CentOS和Suse）的軟體包下安裝並保護Apache，則此過程適用。

應用以下步驟：

1. 在檔案 `httpd.conf` 中，激活以下Apache模組：

   ```
   alias
   authz_host
   mime
   ```

1. 停用下列模組：

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   對連結至停用模組的函式加上註解：

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. 在資料夾中建立Adobe Campaign專用的設定 `/etc/httpd/conf.d/` 檔。 例如 `CampaignApache.conf`

1. 對 **於RHEL7**，請在檔案中新增下列指示：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf
   ```

1. 針對 **RHEL7**:

   新增包含 `/etc/systemd/system/httpd.service` 下列內容的檔案：

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   更新系統使用的模組：

   ```
   systemctl daemon-reload
   ```

1. 然後，執行命令，將Adobe Campaign運算子新增至Apache運算子群組，反之亦然：

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   要使用的組名取決於Apache的配置方式。

1. 執行Apache和Adobe Campaign伺服器。

   針對RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 啟動Web伺服器並測試配置{#launching-the-web-server-and-testing-the-configuration}

您現在可以啟動Apache來測試設定。 Adobe Campaign模組現在應該會在主控台上顯示其橫幅（某些作業系統上有兩個橫幅）:

```
 /etc/init.d/apache start
```

將顯示以下資訊：

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

接下來，請檢查它是否透過送出測試URL做出回應。

通過執行以下操作，可以從命令行測試：

```
 telnet localhost 80  
```

您應獲得：

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
````

然後輸入：

```
GET /r/test
````

將顯示以下資訊：

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
````

您也可以從網頁瀏 [`https://<computer>`](https://machine/r/test) 覽器要求URL。