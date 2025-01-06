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
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# 設定Apache Tomcat {#configuring-tomcat}

Adobe Campaign使用名為Apache Tomcat **的**&#x200B;內嵌Web servlet來處理應用程式與任何外部介面(包括使用者端主控台、追蹤的URL連結、SOAP呼叫等)之間的HTTP/HTTPS要求。 在任何面對外部的Adobe Campaign執行個體中，通常有一個外部網頁伺服器（通常是IIS或Apache）位於此伺服器之前。

進一步瞭解Campaign中的Tomcat以及如何在[此頁面](../../production/using/locate-tomcat-version.md)中找到您的Tomcat版本。

>[!AVAILABILITY]
>
>
>* 從Campaign v7.4.1開始，Tomcat 10.1是預設版本。
>
>* Adobe Campaign Classic不使用WebSocket和HTTP2通訊協定。
>



## Apache Tomcat的預設連線埠 {#default-port-for-tomcat}


>[!NOTE]
>
>此程式僅限於&#x200B;**內部部署**&#x200B;部署。
>

當Tomcat伺服器的8080接聽連線埠已經忙碌於組態所需的其他應用程式時，您需要將8080連線埠取代為可用連線埠（例如8090）。 若要變更，請編輯儲存在Adobe Campaign安裝資料夾的&#x200B;**/tomcat-X/conf**&#x200B;目錄中的&#x200B;**server.xml**&#x200B;檔案。

然後修改JSP轉送頁面的連線埠。 若要這麼做，請變更儲存在Adobe Campaign安裝目錄&#x200B;**/conf**&#x200B;目錄中的&#x200B;**serverConf.xml**&#x200B;檔案。

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 在Apache Tomcat中對應資料夾 {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>此程式僅限於&#x200B;**內部部署**&#x200B;部署。
>

若要定義客戶特定的設定，您可以在&#x200B;**/tomcat-X/conf**&#x200B;資料夾中建立&#x200B;**user_contexts.xml**&#x200B;檔案，其中也包含&#x200B;**contexts.xml**&#x200B;檔案。

此檔案將包含下列型別的資訊：

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可在伺服器端重新產生此操作。

## 隱藏Tomcat錯誤報告 {#hide-tomcat-error-report}


>[!NOTE]
>
>此程式僅限於&#x200B;**內部部署**&#x200B;部署。
>
>自Campaign v7.4.1起，不再需要此變更。
>

基於安全考量，我們強烈建議您隱藏Tomcat錯誤報告。 請依照下列步驟操作：

1. 開啟位於Adobe Campaign安裝資料夾`/usr/local/neolane/nl6/tomcat-X/conf`之&#x200B;**/tomcat-X/conf**&#x200B;目錄中的&#x200B;**server.xml**&#x200B;檔案
1. 在所有現有的前後關聯元素後面新增下列元素：

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. 重新啟動nlserver和Apache Web Server。
