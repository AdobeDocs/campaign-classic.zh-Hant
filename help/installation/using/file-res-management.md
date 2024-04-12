---
product: campaign
title: 檔案與資源管理
feature: Installation, Application Settings
description: 瞭解如何在Campaign中設定檔案和資源管理
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 1%

---

# 檔案與資源管理{#file-and-resmanagement}



## 限制上傳檔案格式 {#limiting-uploadable-files}

使用 **uploadWhiteList** 屬性來限制可在Adobe Campaign伺服器上傳的檔案型別。

此屬性可在 **dataStore** 的元素 **serverConf.xml** 檔案。 所有引數都可在 **serverConf.xml** 列於此 [區段](../../installation/using/the-server-configuration-file.md).

此屬性的預設值為 **.+** 並可讓您上傳任何檔案型別。

若要限制可能的格式，請以有效的Java規則運算式取代屬性值。 您可以輸入數個值，方法是以逗號分隔。

例如： **uploadWhiteList=&quot;。&#42;.png，.&#42;.jpg」** 可讓您將PNG和JPG格式上傳至伺服器。 將不接受任何其他格式。

您也可以藉由設定Web伺服器來防止重要檔案上傳。 [了解更多](web-server-configuration.md)

>[!NOTE]
>
>此 **uploadWhiteList** 屬性會限制可在Adobe Campaign伺服器上傳的檔案型別。 但是，當發佈模式為 **追蹤伺服器** 或 **其他Adobe Campaign伺服器**，則 **uploadWhitelist** 屬性也必須在這些伺服器上更新。

## Proxy連線設定 {#proxy-connection-configuration}

您可以使用 **檔案傳輸** 例如工作流程活動。 若要完成此操作，您需要配置 **proxyConfig** 的區段 **serverConf.xml** 透過特定指令建立檔案。 所有引數都可在 **serverConf.xml** 列於此 [區段](../../installation/using/the-server-configuration-file.md).

可能有下列Proxy連線：HTTP、HTTPS、FTP、SFTP。 請注意，從20.2版Campaign開始，HTTP和HTTPS通訊協定引數為 **不再提供**. 由於這些引數仍可在先前的組建中使用（包括9032），因此下文仍會提及這些引數。

>[!CAUTION]
>
>僅支援基本驗證模式。 不支援NTLM驗證。
>
>不支援SOCKS代理。
>

您可以使用下列指令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

通訊協定引數可以是&#39;http&#39;、&#39;https&#39;或&#39;ftp&#39;。

如果您在與HTTP/HTTPS流量相同的連線埠上設定FTP，您可以使用以下專案：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

只有通訊協定引數是&#39;ftp&#39;並指示指定連線埠上的通道是透過HTTPS還是透過HTTP執行時，才會使用&#39;http&#39;和&#39;https&#39;選項。

如果您透過Proxy伺服器對FTP/SFTP和HTTP/HTTPS流量使用不同的連線埠，則應設定「ftp」通訊協定引數。


例如：

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

然後輸入密碼。

HTTP連線在proxyHTTP引數中定義：

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS連線在proxyHTTPS引數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS連線會在proxyFTP引數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果您對多個連線型別使用相同的Proxy，則只有ProxyHTTP會定義useSingleProxy設為&quot;1&quot;或&quot;true&quot;。

如果您有不應通過Proxy的內部連線，請將它們新增至覆寫引數。

如果要暫時停用Proxy連線，請將enabled引數設為&quot;false&quot;或&quot;0&quot;。

如果您需要透過Proxy使用iOS HTTP/2聯結器，則支援下列HTTP Proxy模式：

* 沒有驗證的HTTP
* HTTP基本驗證

若要啟動Proxy模式，必須在 `serverconf.xml` 檔案：

```
<nmac useHTTPProxy="true">
```

如需此iOS HTTP/2聯結器的詳細資訊，請參閱此 [頁面](../../delivery/using/about-mobile-app-channel.md).

## 管理公用資源 {#managing-public-resources}

若要公開發佈，連結至行銷活動的電子郵件和公共資源中使用的影像，必須存在於外部可存取的伺服器上。 然後，外部收件者或操作員便可使用這些值。 [了解更多](../../installation/using/deploying-an-instance.md#managing-public-resources)。

公用資源儲存在 **/var/res/instance** Adobe Campaign安裝目錄的目錄。

相符的URL是： **http://server/res/instance** 位置 **例項** 是追蹤例項的名稱。

您可以將節點新增至以指定另一個目錄 **會議 — `<instance>`.xml** 檔案來設定伺服器上的儲存空間。 這表示新增下列行：

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

在這種情況下，部署精靈視窗上方指定的公用資源新URL應指向此資料夾。
