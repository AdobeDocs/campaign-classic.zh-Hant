---
product: campaign
title: Campaign Tomcat設定
description: Campaign Tomcat設定
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---

# 設定Apache Tomcat {#configuring-tomcat}

Adobe Campaign使用 **稱為Apache Tomcat的內嵌Web servlet** 在應用程式和任何外部介面（包括使用者端主控台、追蹤的URL連結、SOAP呼叫等）之間處理HTTP/HTTPS請求。 在任何面對外部的Adobe Campaign執行個體中，通常有一個外部網頁伺服器（通常是IIS或Apache）位於此伺服器之前。

進一步瞭解Campaign中的Tomcat以及如何在中找到您的Tomcat版本 [此頁面](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
> 從v7.4.1開始，Tomcat 10.1是預設版本。
>


## Apache Tomcat的預設連線埠 {#default-port-for-tomcat}


>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。
>

當Tomcat伺服器的8080接聽連線埠已經忙碌於組態所需的其他應用程式時，您需要將8080連線埠取代為可用連線埠（例如8090）。 若要變更，請編輯 **server.xml** 檔案已儲存在 **/tomcat-X/conf** Adobe Campaign安裝資料夾的目錄。

然後修改JSP轉送頁面的連線埠。 若要這麼做，請變更 **serverConf.xml** 檔案已儲存在 **/conf** Adobe Campaign安裝目錄的目錄。

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 在Apache Tomcat中對應資料夾 {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。
>

若要定義客戶特定設定，您可以建立 **user_contexts.xml** 中的檔案 **/tomcat-X/conf** 資料夾，其中也包含 **contexts.xml** 檔案。

此檔案將包含下列型別的資訊：

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可在伺服器端重新產生此操作。

## 隱藏Tomcat錯誤報告 {#hide-tomcat-error-report}


>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。
>
>自Campaign v7.4.1起，不再需要此變更。
>

基於安全考量，我們強烈建議您隱藏Tomcat錯誤報告。 請依照下列步驟操作：

1. 開啟 **server.xml** 檔案位於 **/tomcat-X/conf** Adobe Campaign安裝資料夾的目錄：  `/usr/local/neolane/nl6/tomcat-X/conf`
1. 在所有現有的前後關聯元素後面新增下列元素：

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. 重新啟動nlserver和Apache Web Server。
