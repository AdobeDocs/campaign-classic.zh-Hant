---
product: campaign
title: 與 Linux 網頁伺服器整合
description: 了解如何將Campaign整合至網頁伺服器(Linux)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---

# 與 Linux 網頁伺服器整合{#integration-into-a-web-server-for-linux}



Adobe Campaign包含Apache Tomcat，可透過HTTP（和SOAP）作為應用程式伺服器中的入口點。

您可以使用此整合的Tomcat伺服器來處理HTTP請求。

在此情況下：

* 預設監聽埠為8080。 若要變更，請參閱 [本節](configure-tomcat.md).
* 然後，用戶端主控台會使用URL進行連線，例如：

   ```
   http://<computer>:8080
   ```

但是，出於安全和管理原因，我們建議使用專用的Web伺服器作為HTTP通信的主要入口點，因為運行Adobe Campaign的電腦在Internet上被公開，並且您希望開啟對網路外部控制台的訪問。

Web伺服器也可讓您透過HTTPs通訊協定保證資料機密性。

同樣地，當您想使用追蹤功能時，必須使用Web伺服器，這只能作為Web伺服器的擴充模組使用。

>[!NOTE]
>
>如果您未使用追蹤功能，則可執行Apache或IIS的標準安裝，並重新導向至Campaign。 不需要追蹤Web伺服器擴充模組。

## 使用Debian設定Apache Web伺服器 {#configuring-the-apache-web-server-with-debian}

如果您已根據APT在發佈下安裝Apache，則此程式適用。

應用以下步驟：

1. 預設情況下，使用以下命令禁用載入的模組：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   確保 **別名**, **authz_host** 和 **mime** 模組仍會啟用。 為此，請使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 建立檔案 **nlsrv.load** in **/etc/apache2/mods available** 並插入下列內容：

   在Debian 8中：

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 建立檔案 **nlsrv.conf** in **/etc/apache2/mods available** 使用下列命令：

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用以下命令激活此模組：

   ```
    a2enmod nlsrv
   ```

   如果您使用 **mod_rewrite** 模組，您必須重新命名 **nlsrv.load** 和 **nlsrv.conf** 檔案 **zz-nlsrv.load** 和 **zz-nlsrv.conf**. 要激活模組，請運行以下命令：

   ```
   a2enmod zz-nlsrv
   ```

1. 編輯 **/etc/apache2/envvars** 檔案中，添加以下行：

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

## 在RHEL中配置Apache Web伺服器 {#configuring-apache-web-server-in-rhel}

如果您已在基於RPM（RHEL、CentOS和Suse）的包下安裝並保護Apache，則此過程適用。

應用以下步驟：

1. 在 `httpd.conf` 檔案中，激活以下Apache模組：

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

1. 在 `/etc/httpd/conf.d/` 檔案夾。 例如 `CampaignApache.conf`

1. 針對 **RHEL7**，請在檔案中新增下列指示：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 針對 **RHEL7**:

   新增 `/etc/systemd/system/httpd.service` 檔案，其內容如下：

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

   要使用的群組名稱取決於Apache的設定方式。

1. 執行Apache和Adobe Campaign伺服器。

   對於RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 啟動Web伺服器並測試配置{#launching-the-web-server-and-testing-the-configuration}

您現在可以啟動Apache來測試設定。 Adobe Campaign模組現在應該會在主控台上顯示其橫幅（某些作業系統上有兩個橫幅）:

```
 /etc/init.d/apache start
```

會顯示下列資訊：

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

接下來檢查它是否透過提交測試URL來回應。

您可以執行以下動作，從命令列測試：

```
 telnet localhost 80  
```

您應取得：

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

然後輸入：

```
GET /r/test
```

會顯示下列資訊：

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

您也可以要求URL [`https://<computer>`](https://myserver.adobe.com/r/test) 從網頁瀏覽器。
