---
solution: Campaign Classic
product: campaign
title: 檔案與資源管理
description: 瞭解如何在Campaign中設定檔案和資源管理
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---

# 檔案和資源管理{#file-and-resmanagement}

## 限制上載檔案格式{#limiting-uploadable-files}

使用&#x200B;**uploadWhiteList**&#x200B;屬性來限制可在Adobe Campaign伺服器上上載的檔案類型。

此屬性可在&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**dataStore**&#x200B;元素中使用。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

此屬性的預設值為&#x200B;**。+**，可讓您上傳任何檔案類型。

要限制可能的格式，請用有效的java規則運算式替換屬性值。 您可以用逗號分隔數個值，以輸入數個值。

例如：**uploadWhiteList=&quot;&quot;。*.png、。*.jpg&quot;**&#x200B;可讓您在伺服器上上傳PNG和JPG格式。 不接受其他格式。

>[!NOTE]
>
>在Internet Explorer中，完整的檔案路徑必須由規則運算式驗證。

您也可以設定Web伺服器，以防止上傳重要檔案。 [了解更多](web-server-configuration.md)

## 代理連接配置{#proxy-connection-configuration}

例如，您可以使用&#x200B;**檔案傳輸**&#x200B;工作流程活動，將Campaign伺服器連接至外部系統。 要實現此目的，您需要通過特定命令配置&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**proxyConfig**&#x200B;部分。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

可能有下列代理連接：HTTP、HTTPS、FTP、SFTP。 請注意，從20.2促銷活動發行開始，HTTP和HTTPS通訊協定參數已不再提供&#x200B;****。 這些參數仍在下面提及，因為它們在以前的版本中仍然可用——包括9032。

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

如果您要在與HTTP/HTTPS流量相同的埠上設定FTP，則可使用下列功能：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

只有當通訊協定參數為「ftp」時，才會使用「http」和「https」選項，並指出指定埠上的通道是透過HTTPS或HTTP執行。

如果您使用不同的埠來透過代理伺服器傳送FTP/SFTP和HTTP/HTTPS流量，則應設定「ftp」通訊協定參數。


例如：

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

然後輸入密碼。

HTTP連線在proxyHTTP參數中定義：

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS連線在proxyHTTPS參數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS連線是在proxyFTP參數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果您對數種連線類型使用相同的proxy，則只會定義proxyHTTP，並將useSingleProxy設為&quot;1&quot;或&quot;true&quot;。

如果您有內部連線，而且該連線應經由proxy，請在override參數中新增。

如果您想暫時停用Proxy連線，請將啟用的參數設為&quot;false&quot;或&quot;0&quot;。

## 管理公共資源{#managing-public-resources}

若要公開提供，連結至促銷活動的電子郵件和公共資源中使用的影像必須存在於可外部存取的伺服器上。 然後，外部收件者或運算子就可使用這些檔案。 [進一步瞭解](../../installation/using/deploying-an-instance.md#managing-public-resources)。

公共資源儲存在Adobe Campaign安裝目錄的&#x200B;**/var/res/instance**&#x200B;目錄中。

相符的URL為：**http://server/res/instance**，其中&#x200B;**instance**&#x200B;是追蹤例項的名稱。

通過向&#x200B;**conf-`<instance>`.xml**&#x200B;檔案添加節點，可以指定另一個目錄，以配置伺服器上的儲存。 這表示新增下列行：

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

在這種情況下，在部署精靈視窗的上半部中指定之公用資源的新URL應指向此資料夾。
