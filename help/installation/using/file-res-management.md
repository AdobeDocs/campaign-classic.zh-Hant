---
product: campaign
title: 檔案和資源管理
description: 瞭解如何在市場活動中配置檔案和資源管理
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 4ff86349d6b8966273585bf2a1ea0d785a7e87cb
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 1%

---

# 檔案和資源管理{#file-and-resmanagement}

![](../../assets/v7-only.svg)

## 限制上載檔案格式 {#limiting-uploadable-files}

使用 **上載白名單** 屬性，以限制可在Adobe Campaign伺服器上上載的檔案類型。

此屬性在 **資料儲存** 元素 **serverConf.xml** 的子菜單。 中的所有可用參數 **serverConf.xml** 列在 [節](../../installation/using/the-server-configuration-file.md)。

此屬性的預設值是 **。+** 並允許您上載任何檔案類型。

要限制可能的格式，請用有效的java規則運算式替換屬性值。 可以通過用逗號分隔多個值來輸入它們。

例如： **uploadWhiteList=&quot;。&#42;.png,&#42;.jpg** 將允許您在伺服器上上載PNG和JPG格式。 不接受其他格式。

您還可以通過配置Web伺服器來阻止上載重要檔案。 [了解更多](web-server-configuration.md)

## 代理連接配置 {#proxy-connection-configuration}

您可以使用 **檔案傳輸** 例如，工作流活動。 要實現此目標，您需要配置 **代理配置** 的下界 **serverConf.xml** 檔案。 中的所有可用參數 **serverConf.xml** 列在 [節](../../installation/using/the-server-configuration-file.md)。

可以使用以下代理連接：HTTP、HTTPS、FTP、SFTP。 請注意，從20.2市場活動版開始，HTTP和HTTPS協定參數是 **不再可用**。 這些參數在以前的版本（包括9032）中仍然可用，因此在下文中仍提及。

>[!CAUTION]
>
>僅支援基本身份驗證模式。 不支援NTLM身份驗證。
>
>不支援SOCKS代理。

可以使用以下命令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

協定參數可以是「http」、「https」或「ftp」。

如果將FTP設定在與HTTP/HTTPS通信相同的埠上，則可以使用以下命令：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

僅當協定參數為「ftp」時才使用「http」和「https」選項，並指示指定埠上的隧道是通過HTTPS還是通過HTTP執行。

如果在代理伺服器上對FTP/SFTP和HTTP/HTTPS通信使用其他埠，則應設定「ftp」協定參數。


例如：

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

然後輸入密碼。

HTTP連接在proxyHTTP參數中定義：

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS連接在proxyHTTPS參數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS連接在proxyFTP參數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果對多個連接類型使用相同的代理，則將只使用useSingleProxy設定為&quot;1&quot;或&quot;true&quot;來定義proxyHTTP。

如果內部連接應通過代理，請在覆蓋參數中添加這些連接。

如果要臨時禁用代理連接，請將啟用的參數設定為「false」或「0」。

如果需要通過代理使用iOSHTTP/2連接器，則支援以下HTTP代理模式：

* HTTP無驗證
* HTTP基本身份驗證

要激活代理模式，必須在 `serverconf.xml` 檔案：

```
<nmac useHTTPProxy="true">
```

有關此iOSHTTP/2連接器的詳細資訊，請參閱 [頁](../../delivery/using/about-mobile-app-channel.md)。

## 管理公共資源 {#managing-public-resources}

要公開獲得，電子郵件中使用的影像和與市場活動連結的公共資源必須位於外部可訪問的伺服器上。 然後，它們可供外部收件人或操作員使用。 [了解更多資訊](../../installation/using/deploying-an-instance.md#managing-public-resources)。

公共資源儲存在 **/var/res/instance** 的子目錄。

匹配的URL為： **http://server/res/instance** 何處 **實例** 是跟蹤實例的名稱。

可以通過將節點添加到 **會議`<instance>`.xml** 檔案，以配置伺服器上的儲存。 這意味著添加以下行：

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

在這種情況下，在部署嚮導窗口的上半部分中為公共資源指定的新URL應指向此資料夾。
