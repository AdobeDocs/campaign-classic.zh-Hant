---
product: campaign
title: Campaign Tomcat設定
description: Campaign Tomcat設定
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# 設定Apache Tomcat {#configuring-tomcat}



Adobe Campaign使用 **稱為Apache Tomcat的內嵌Web servlet** 在應用程式和任何外部介面（包括使用者端主控台、追蹤的URL連結、SOAP呼叫等）之間處理HTTP/HTTPS請求。 在任何面對外部的Adobe Campaign執行個體中，通常有一個外部Web伺服器（通常是IIS或Apache）在這之前。

進一步瞭解Campaign中的Tomcat以及如何在中找到您的Tomcat版本 [此頁面](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。

## Apache Tomcat的預設連線埠 {#default-port-for-tomcat}

當Tomcat伺服器的8080接聽連線埠已經忙碌於設定所需的其他應用程式時，您需要使用可用連線埠來取代8080連線埠（例如8090）。 若要變更，請編輯 **server.xml** 檔案已儲存在 **/tomcat-8/conf** Adobe Campaign安裝資料夾的目錄。

然後修改JSP轉送頁面的連線埠。 若要這麼做，請變更 **serverConf.xml** 檔案已儲存在 **/conf** Adobe Campaign安裝目錄的目錄。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 在Apache Tomcat中對應資料夾 {#mapping-a-folder-in-tomcat}

若要定義客戶特定設定，您可以建立 **user_contexts.xml** 中的檔案 **/tomcat-8/conf** 資料夾，其中也包含 **contexts.xml** 檔案。

此檔案將包含下列型別的資訊：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有需要，可在伺服器端重新產生此操作。

## 隱藏Tomcat錯誤報告 {#hide-tomcat-error-report}

基於安全考量，強烈建議您隱藏Tomcat錯誤報告。 步驟如下。

1. 開啟 **server.xml** 檔案位於 **/tomcat-8/conf** Adobe Campaign安裝資料夾的目錄：  `/usr/local/neolane/nl6/tomcat-8/conf`
1. 在所有現有的前後關聯元素後面新增下列元素：

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. 重新啟動nlserver和Apache Web Server。
