---
solution: Campaign Classic
product: campaign
title: 與 Linux 網頁伺服器整合
description: 瞭解如何將Campaign整合至網頁伺服器(Linux)
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---

# 與 Linux 網頁伺服器整合{#integration-into-a-web-server-for-linux}

Adobe Campaign包含Apache Tomcat，它可透過HTTP（和SOAP）在應用程式伺服器中當做入口點。

您可以使用此整合的Tomcat伺服器來服務HTTP請求。

在本例中：

* 預設監聽埠為8080。 要更改它，請參閱[本節](configure-tomcat.md)。
* 然後，用戶端主控台會使用URL進行連線，例如：

   ```
   http://<computer>:8080
   ```

但是，出於安全和管理原因，我們建議使用專用的Web伺服器作為HTTP通信的主要入口點，因為運行Adobe Campaign的電腦在Internet上被公開，並且您希望開啟對網路外部控制台的訪問。

Web伺服器也可讓您使用HTTP通訊協定來保證資料的機密性。

同樣地，當您想要使用追蹤功能時，必須使用Web伺服器，此功能僅能做為Web伺服器的擴充模組。

>[!NOTE]
>
>如果您不使用追蹤功能，則可執行Apache或IIS的標準安裝，並重新導向至促銷活動。 不需要追蹤Web伺服器擴充模組。

## 使用Debian {#configuring-the-apache-web-server-with-debian}配置Apache Web伺服器

如果您已在基於APT的分發中安裝Apache，則此程式適用。

應用以下步驟：

1. 使用以下命令禁用預設載入的模組：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   確保&#x200B;**alias**、**authz_host**&#x200B;和&#x200B;**mime**&#x200B;模組仍處於啟用狀態。 為此，請使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 在&#x200B;**/etc/apache2/mods-available**&#x200B;中建立檔案&#x200B;**nlsrv.load**，並插入下列內容：

   在德比安8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 使用以下命令在&#x200B;**/etc/apache2/mods-available**&#x200B;中建立檔案&#x200B;**nlsrv.conf**:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用以下命令激活此模組：

   ```
    a2enmod nlsrv
   ```

   如果您使用&#x200B;**mod_rewrite**&#x200B;模組用於Adobe Campaign頁，則需要將&#x200B;**nlsrv.load**&#x200B;和&#x200B;**nlsrv.conf**&#x200B;檔案更名為&#x200B;**zz-nlsrv.load**&#x200B;和&#x200B;**zz-nlsrv.a9/>。**&#x200B;要激活模組，請運行以下命令：

   ```
   a2enmod zz-nlsrv
   ```

1. 編輯&#x200B;**/etc/apache2/envvars**&#x200B;檔案，新增下列行：

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   儲存變更。

1. 然後，使用以下類型的命令將Adobe Campaign用戶添加到Apache用戶組，反之亦然：

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. 重新啟動Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## 在RHEL {#configuring-apache-web-server-in-rhel}中配置Apache Web伺服器

如果您已在基於RPM（RHEL、CentOS和Suse）的軟體包下安裝並保護Apache，則此過程適用。

應用以下步驟：

1. 在`httpd.conf`檔案中，激活以下Apache模組：

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

1. 在`/etc/httpd/conf.d/`資料夾中建立Adobe Campaign特定的配置檔案。 例如`CampaignApache.conf`

1. 對於&#x200B;**RHEL7**，在檔案中添加以下說明：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 對於&#x200B;**RHEL7**:

   添加包含以下內容的`/etc/systemd/system/httpd.service`檔案：

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   更新系統使用的模組：

   ```
   systemctl daemon-reload
   ```

1. 然後，通過運行以下命令將Adobe Campaign運算子添加到Apache運算子組中，反之亦然：

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   要使用的組名取決於Apache的配置方式。

1. 運行Apache和Adobe Campaign伺服器。

   針對RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 啟動Web伺服器並測試配置{#launching-the-web-server-and-testing-the-configuration}

您現在可以啟動Apache來測試設定。 Adobe Campaign模組現在應在控制台上顯示其橫幅（某些作業系統上顯示兩個橫幅）:

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
```

然後輸入：

```
GET /r/test
```

將顯示以下資訊：

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

您也可以從網頁瀏覽器要求URL [`https://<computer>`](https://myserver.adobe.com/r/test)。
