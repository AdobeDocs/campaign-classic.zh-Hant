---
product: campaign
title: 檔案和資源管理
description: 瞭解如何在Campaign中設定檔案和資源管理
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# 檔案和資源管理{#file-and-resmanagement}



## 限制上傳檔案格式 {#limiting-uploadable-files}

使用 **uploadWhiteList** 屬性來限制可在Adobe Campaign伺服器上傳的檔案型別。

此屬性可在 **dataStore** 的元素 **serverConf.xml** 檔案。 所有引數都可在 **serverConf.xml** 列於此 [區段](../../installation/using/the-server-configuration-file.md).

此屬性的預設值為 **.+** 並可讓您上傳任何檔案型別。

若要限制可能的格式，請以有效的Java規則運算式取代屬性值。 您可以用逗號分隔多個值，以輸入它們。

例如： **uploadWhiteList=&quot;。&#42;.png，.&#42;.jpg」** 可讓您將PNG和JPG格式上傳至伺服器。 不接受任何其他格式。

您也可以藉由設定Web伺服器來防止重要檔案上傳。 [了解更多](web-server-configuration.md)

>[!NOTE]
>
>此 **uploadWhiteList** 屬性會限制Adobe Campaign伺服器上可供上傳的檔案型別。 但是，當發佈模式為 **追蹤伺服器** 或 **其他Adobe Campaign伺服器**，則 **uploadWhitelist** 屬性也必須在這些伺服器上更新。

## Proxy連線設定 {#proxy-connection-configuration}

您可以透過Proxy，使用 **檔案傳輸** 例如工作流程活動。 若要完成此操作，您需要設定 **proxyConfig** 部分 **serverConf.xml** 檔案的特定命令。 所有引數都可在 **serverConf.xml** 列於此 [區段](../../installation/using/the-server-configuration-file.md).

可以使用下列Proxy連線：HTTP、HTTPS、FTP、SFTP。 請注意，從20.2 Campaign版本開始，HTTP和HTTPS通訊協定引數為 **不再提供**. 由於這些引數仍可在先前的組建中使用（包括9032），因此下文仍會提及這些引數。

>[!CAUTION]
>
>僅支援基本驗證模式。 不支援NTLM驗證。
>
>不支援SOCKS代理。

您可以使用下列指令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

通訊協定引數可以是&#39;http&#39;、&#39;https&#39;或&#39;ftp&#39;。

如果您在與HTTP/HTTPS流量相同的連線埠上設定FTP，您可以使用以下專案：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

「http」和「https」選項僅在通訊協定引數為「ftp」時使用，並指示指定連線埠上的通道是透過HTTPS還是透過HTTP執行。

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

FTP/FTPS連線在proxyFTP引數中定義：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果您對多個連線型別使用相同的Proxy，只有proxyHTTP會定義useSingleProxy設為&quot;1&quot;或&quot;true&quot;。

如果您有應通過Proxy的內部連線，請將其新增到覆寫引數中。

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

您可以將節點新增至以指定其他目錄 **conf-`<instance>`.xml** 檔案來設定伺服器上的儲存空間。 這表示新增下列行：

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
