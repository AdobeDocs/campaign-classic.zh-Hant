---
product: campaign
title: 與 Linux 網頁伺服器整合
description: 瞭解如何將市場活動整合到Web伺服器(Linux)中
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---

# 與 Linux 網頁伺服器整合{#integration-into-a-web-server-for-linux}



Adobe Campaign包括Apache Tomcat，它通過HTTP（和SOAP）作為應用伺服器的入口點。

可以使用此整合的Tomcat伺服器來服務HTTP請求。

在本例中：

* 預設監聽埠為8080。 要更改它，請參閱 [此部分](configure-tomcat.md)。
* 然後，客戶端控制台使用URL進行連接，如：

   ```
   http://<computer>:8080
   ```

但是，出於安全和管理原因，我們建議使用專用的Web伺服器作為HTTP通信的主要入口點，因為運行Adobe Campaign的電腦在Internet上被暴露，並且您希望開啟對網路外部控制台的訪問。

Web伺服器還允許您使用HTTP協定保證資料機密性。

同樣，當您希望使用跟蹤功能時，必須使用Web伺服器，該功能僅作為Web伺服器的擴展模組可用。

>[!NOTE]
>
>如果不使用跟蹤功能，則可以執行Apache或IIS的標準安裝，並重定向到市場活動。 不需要跟蹤Web伺服器擴展模組。

## 使用Debian配置Apache Web伺服器 {#configuring-the-apache-web-server-with-debian}

如果您已在基於APT的分發下安裝Apache，則此過程適用。

應用以下步驟：

1. 使用以下命令禁用預設載入的模組：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   確保 **別名**。 **authz主機** 和 **mime** 模組仍處於啟用狀態。 為此，請使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 建立檔案 **nlsrv.load** 在 **/etc/apache2/mods可用** 插入以下內容：

   在德邊市8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 建立檔案 **nlsrv.conf** 在 **/etc/apache2/mods可用** 使用以下命令：

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用以下命令激活此模組：

   ```
    a2enmod nlsrv
   ```

   如果使用 **mod_rewrite** 用於Adobe Campaign頁面的模組，需要更名 **nlsrv.load** 和 **nlsrv.conf** 檔案 **zz-nlsrv.load** 和 **zz-nlsrv.conf**。 要激活模組，請運行以下命令：

   ```
   a2enmod zz-nlsrv
   ```

1. 編輯 **/etc/apache2/envvars** 檔案，添加以下行：

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   保存更改。

1. 然後使用以下命令類型將Adobe Campaign用戶添加到Apache用戶組，反之亦然：

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. 重新啟動Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## 在RHEL中配置Apache Web伺服器 {#configuring-apache-web-server-in-rhel}

如果已在基於RPM（RHEL、CentOS和Suse）的軟體包下安裝並保護了Apache，則此過程適用。

應用以下步驟：

1. 在 `httpd.conf` 檔案，激活以下Apache模組：

   ```
   alias
   authz_host
   mime
   ```

1. 停用以下模組：

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

   注釋連結到已停用模組的函式：

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

1. 在中建立Adobe Campaign特定的配置檔案 `/etc/httpd/conf.d/` 的子菜單。 例如 `CampaignApache.conf`

1. 對於 **RHEL7**，在檔案中添加以下說明：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 對於 **RHEL7**:

   添加 `/etc/systemd/system/httpd.service` 檔案，其內容如下：

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

   對於RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## 啟動Web伺服器並測試配置{#launching-the-web-server-and-testing-the-configuration}

現在，您可以通過啟動Apache來test配置。 Adobe Campaign模組現在應在控制台上顯示其橫幅（某些作業系統上有兩個橫幅）:

```
 /etc/init.d/apache start
```

顯示以下資訊：

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

接下來檢查它是否通過提交testURL來響應。

通過執行以下操作，可以從命令行test此項：

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

顯示以下資訊：

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

您也可以請求URL [`https://<computer>`](https://myserver.adobe.com/r/test) 從Web瀏覽器。
