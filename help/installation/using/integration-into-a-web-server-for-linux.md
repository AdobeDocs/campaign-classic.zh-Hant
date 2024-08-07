---
product: campaign
title: 與Linux網頁伺服器整合
description: 瞭解如何將Campaign整合至網頁伺服器(Linux)
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 2%

---

# 與Linux網頁伺服器整合 {#integration-into-a-web-server-for-linux}


Adobe Campaign包含Apache Tomcat，可透過HTTP (和SOAP)作為應用程式伺服器的進入點。

您可以使用這個整合的Tomcat伺服器來處理HTTP要求。

在此案例中：

* 預設的接聽連線埠為8080。 若要變更，請參閱[本節](configure-tomcat.md)。
* 然後使用者端主控台會使用URL連線，例如：

  ```
  https://<computer>:8080
  ```

不過，基於安全性與管理考量，當執行Adobe Campaign的電腦公開在網際網路上，而您想要開啟網路外部主控台的存取權時，我們建議使用專用的Web伺服器作為HTTP流量的主要進入點。

網頁伺服器也可讓您透過HTTPs通訊協定來保證資料機密性。

同樣地，當您想要使用追蹤功能時，必須使用網頁伺服器，這項功能只能作為網頁伺服器的擴充模組使用。

>[!NOTE]
>
>如果您未使用追蹤功能，您可以執行Apache或IIS的標準安裝，並重新導向至Campaign。 不需要追蹤Web伺服器擴充功能模組。

## 使用Debian設定Apache Web Server {#configuring-the-apache-web-server-with-debian}

如果您在根據APT的分發下安裝Apache，則此程式適用。

應用以下步驟：

1. 使用下列命令停用預設載入的模組：

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   請確定&#x200B;**alias**、**authz_host**&#x200B;和&#x200B;**mime**&#x200B;模組仍然啟用。 為此，請使用以下命令：

   ```
   a2enmod  alias authz_host mime
   ```

1. 在&#x200B;**/etc/apache2/mods-available**&#x200B;中建立檔案&#x200B;**nlsrv.load**&#x200B;並插入下列內容：

   在Debian 8中：

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. 使用以下命令在&#x200B;**/etc/apache2/mods-available**&#x200B;中建立檔案&#x200B;**nlsrv.conf**：

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. 使用下列命令啟動此模組：

   ```
    a2enmod nlsrv
   ```

   如果您正在使用Adobe Campaign頁面的&#x200B;**mod_rewrite**&#x200B;模組，您必須將&#x200B;**nlsrv.load**&#x200B;和&#x200B;**nlsrv.conf**&#x200B;檔案重新命名為&#x200B;**zz-nlsrv.load**&#x200B;和&#x200B;**zz-nlsrv.conf**。 若要啟動模組，請執行以下命令：

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

如果您已在基於RPM （RHEL、CentOS和Suse）的套件下安裝並保護Apache，則此程式適用。

應用以下步驟：

1. 在`httpd.conf`檔案中，啟動下列Apache模組：

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

1. 在`/etc/httpd/conf.d/`資料夾中建立Adobe Campaign專屬的設定檔。 例如`CampaignApache.conf`

1. 針對&#x200B;**RHEL7**，請在檔案中新增下列指示：

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. 針對&#x200B;**RHEL7**：

   新增包含下列內容的`/etc/systemd/system/httpd.service`檔案：

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   更新系統使用的模組：

   ```
   systemctl daemon-reload
   ```

1. 接著執行命令，將Adobe Campaign運運算元新增至Apache運運算元群組（反之亦然）：

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

您現在可以啟動Apache以測試設定。 Adobe Campaign模組現在應在主控台上顯示其橫幅（某些作業系統上的兩個橫幅）：

```
 /etc/init.d/apache start
```

會顯示下列資訊：

```sql
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

接下來，請檢查它是否透過提交測試URL回應。

您可以從命令列透過執行以下動作來測試此專案：

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

您也可以從網頁瀏覽器要求URL `https://myserver.adobe.com/r/test`。
