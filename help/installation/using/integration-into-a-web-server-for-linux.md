---
product: campaign
title: 與 Linux 網頁伺服器整合
description: 瞭解如何將Campaign整合至網頁伺服器(Linux)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 403227736e2e8c606204e9324d0afb5b71be62a5
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 5%

---

# 與 Linux 網頁伺服器整合{#integration-into-a-web-server-for-linux}



Adobe Campaign包含Apache Tomcat，可透過HTTP （和SOAP）作為應用程式伺服器的進入點。

您可以使用此整合式Tomcat伺服器來處理HTTP請求。

在此案例中：

* 預設接聽連線埠為8080。 若要變更，請參閱 [本節](configure-tomcat.md).
* 然後，使用者端主控台會使用URL連線，例如：

   ```
   http://<computer>:8080
   ```

不過，基於安全性與管理考量，建議使用專用網頁伺服器作為HTTP流量的主要入口點，因為執行Adobe Campaign的電腦會公開在網際網路上，而您想要開啟網路外部主控台的存取許可權。

網頁伺服器也可讓您使用HTTPs通訊協定來保證資料機密性。

同樣地，當您想要使用追蹤功能時，也必須使用Web伺服器，追蹤功能只能當做擴充模組提供給Web伺服器。

>[!NOTE]
>
>如果您未使用追蹤功能，可以執行標準Apache或IIS安裝，並重導至Campaign。 不需要追蹤Web伺服器擴充功能模組。

## 使用Debian設定Apache Web Server {#configuring-the-apache-web-server-with-debian}

如果您在根據APT的分發下安裝Apache，則此程式適用。

應用以下步驟：

1. 使用下列命令停用預設載入的模組：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   確保 **別名**， **authz_host** 和 **mime** 模組仍為啟用。 為此，請使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 建立檔案 **nlsrv.load** 在 **/etc/apache2/mods-available** 並插入下列內容：

   在Debian 8中：

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 建立檔案 **nlsrv.conf** 在 **/etc/apache2/mods-available** 使用下列命令：

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用下列命令啟動此模組：

   ```
    a2enmod nlsrv
   ```

   如果您使用 **mod_rewrite** Adobe Campaign頁面的模組，您必須重新命名 **nlsrv.load** 和 **nlsrv.conf** 檔案至 **zz-nlsrv.load** 和 **zz-nlsrv.conf**. 若要啟動模組，請執行以下命令：

   ```
   a2enmod zz-nlsrv
   ```

1. 編輯 **/etc/apache2/envvars** 檔案中，新增下列行：

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   儲存變更。

1. 然後使用以下型別的命令，將Adobe Campaign使用者新增至Apache使用者群組，反之亦然：

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. 重新啟動Apache：

   ```
   invoke-rc.d apache2 restart
   ```

## 在RHEL中設定Apache Web Server {#configuring-apache-web-server-in-rhel}

若您已在RPM （RHEL、CentOS和Suse）封裝下安裝並保護Apache，則此程式適用。

應用以下步驟：

1. 在 `httpd.conf` 檔案中，啟用下列Apache模組：

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

   註解連結至已停用模組的函式：

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

1. 在中建立Adobe Campaign專屬設定檔 `/etc/httpd/conf.d/` 資料夾。 例如 `CampaignApache.conf`

1. 對象 **RHEL7**，請在檔案中新增下列指示：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 對象 **RHEL7**：

   新增 `/etc/systemd/system/httpd.service` 包含下列內容的檔案：

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   更新systemd使用的模組：

   ```
   systemctl daemon-reload
   ```

1. 然後執行命令，將Adobe Campaign運運算元新增至Apache運運算元群組（反之亦然）：

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   要使用的群組名稱取決於Apache的設定方式。

1. 執行Apache和Adobe Campaign伺服器。

   對於RHEL7：

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 啟動Web伺服器並測試設定{#launching-the-web-server-and-testing-the-configuration}

您現在可以啟動Apache以測試設定。 Adobe Campaign模組現在應在主控台上顯示其橫幅（某些作業系統上有兩個橫幅）：

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

接下來，請檢查它是否透過提交測試URL來回應。

您可以從命令列透過執行下列動作來測試此專案：

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

您也可以要求URL `https://myserver.adobe.com/r/test` 從網頁瀏覽器。
