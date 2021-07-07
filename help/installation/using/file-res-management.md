---
product: campaign
title: 檔案和資源管理
description: 了解如何在Campaign中設定檔案和資源管理
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 939552f127207f258448b2a82bb8c4c000371694
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# 檔案和資源管理{#file-and-resmanagement}

## 限制上傳檔案格式 {#limiting-uploadable-files}

使用&#x200B;**uploadWhiteList**&#x200B;屬性來限制可在Adobe Campaign伺服器上上載的檔案類型。

此屬性可在&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**dataStore**&#x200B;元素內使用。 **serverConf.xml**&#x200B;中所有可用的參數都列在此[節](../../installation/using/the-server-configuration-file.md)中。

此屬性的預設值為&#x200B;**。+** ，並可讓您上傳任何檔案類型。

若要限制可能的格式，請以有效的java規則運算式取代屬性值。 您可以以逗號分隔數個值，以輸入數個值。

例如：**uploadWhiteList=&quot;。*.png,。*.jpg&quot;**&#x200B;可讓您在伺服器上傳PNG和JPG格式。 不接受其他格式。

>[!NOTE]
>
>在Internet Explorer中，完整的檔案路徑必須由規則運算式驗證。

您也可以設定Web伺服器，以防止上傳重要檔案。 [深入瞭解](web-server-configuration.md)

## 代理連接配置 {#proxy-connection-configuration}

例如，您可以使用&#x200B;**檔案傳輸**&#x200B;工作流程活動，將Campaign伺服器透過代理連線至外部系統。 為此，您需要通過特定命令配置&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**proxyConfig**&#x200B;部分。 **serverConf.xml**&#x200B;中可用的所有參數都列在此[節](../../installation/using/the-server-configuration-file.md)中。

可能有下列代理連接：HTTP、HTTPS、FTP、SFTP。 請注意，自20.2 Campaign版本開始，HTTP和HTTPS通訊協定參數已&#x200B;**不再提供**。 由於這些參數在舊版組建（包括9032）中仍然可用，因此下文仍提及。

>[!CAUTION]
>
>僅支援基本驗證模式。 不支援NTLM身份驗證。
>
>不支援SOCKS代理。


您可以使用下列命令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

通訊協定參數可以是「http」、「https」或「ftp」。

如果您在與HTTP/HTTPS流量相同的埠上設定FTP，則可使用下列項目：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

只有當通訊協定參數為「ftp」時，才會使用「http」和「https」選項，並指出指定埠上的隧道傳輸是透過HTTPS還是透過HTTP執行。

如果您透過代理伺服器對FTP/SFTP和HTTP/HTTPS流量使用不同的埠，則應設定「ftp」通訊協定參數。


例如：

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

然後輸入密碼。

HTTP連線會定義在proxyHTTP參數中：

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS連線會定義於proxyHTTPS參數中：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS連線會定義於proxyFTP參數中：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果您對數種連線類型使用相同的代理，則只會以useSingleProxy設為&quot;1&quot;或&quot;true&quot;來定義proxyHTTP。

如果您有內部連線應通過Proxy，請在覆寫參數中新增這些連線。

如果要暫時禁用代理連接，請將enabled參數設定為&quot;false&quot;或&quot;0&quot;。

如果您需要透過代理使用iOS HTTP/2連接器，則支援下列HTTP代理模式：

* 不驗證的HTTP
* HTTP基本驗證

要激活代理模式，必須在`serverconf.xml`檔案中進行以下更改：

```
<nmac useHTTPProxy="true">
```

有關此iOS HTTP/2連接器的詳細資訊，請參閱此[page](../../delivery/using/about-mobile-app-channel.md)。

## 管理公用資源 {#managing-public-resources}

若要公開使用，連結至促銷活動的電子郵件和公共資源中使用的影像必須存在於可外部存取的伺服器上。 然後，外部收件者或運算子就能使用這些ID。 [深入瞭解](../../installation/using/deploying-an-instance.md#managing-public-resources)。

公用資源儲存在Adobe Campaign安裝目錄的&#x200B;**/var/res/instance**&#x200B;目錄中。

相符的URL為：**http://server/res/instance**&#x200B;其中&#x200B;**instance**&#x200B;為追蹤例項的名稱。

您可以將節點添加到&#x200B;**conf-`<instance>`.xml**&#x200B;檔案中以配置伺服器上的儲存，從而指定另一個目錄。 這表示會新增下列行：

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

在這種情況下，部署精靈視窗上方所提供之公用資源的新URL應指向此資料夾。
