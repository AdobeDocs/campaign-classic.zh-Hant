---
product: campaign
title: 市場活動Tomcat配置
description: 市場活動Tomcat配置
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

# 配置Apache Tomcat {#configuring-tomcat}



Adobe Campaign使用 **嵌入式Web Servlet，稱為Apache Tomcat** 處理應用程式和任何外部介面（包括客戶端控制台、跟蹤的URL連結、SOAP調用等）之間的HTTP/HTTPS請求。 對於任何面向外部的Adobe Campaign實例，其前面通常有外部Web伺服器（通常為IIS或Apache）。

瞭解有關Campaing中Tomcat的詳細資訊以及如何在 [此頁](../../production/using/locate-tomcat-version.md)。

>[!NOTE]
>
>此過程僅限於 **現場** 部署。

## Apache Tomcat的預設埠 {#default-port-for-tomcat}

當Tomcat伺服器的8080偵聽埠已忙於配置所需的另一個應用程式時，您需要用一個空閒埠（例如8090）替換8080埠。 要更改它，請編輯 **伺服器.xml** 檔案保存在 **/tomcat-8/conf** 的子目錄。

然後修改JSP中繼頁的埠。 為此，請更改 **serverConf.xml** 檔案保存在 **/conf** 的子目錄。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 在Apache Tomcat中映射資料夾 {#mapping-a-folder-in-tomcat}

要定義客戶特定設定，您可以建立 **user_contexts.xml** 檔案 **/tomcat-8/conf** 資料夾，其中還包含 **上下文.xml** 的子菜單。

此檔案將包含以下類型的資訊：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可以在伺服器端複製此操作。

## 隱藏Tomcat錯誤報告 {#hide-tomcat-error-report}

出於安全原因，強烈建議您隱藏Tomcat錯誤報告。 這是步驟。

1. 開啟 **伺服器.xml** 檔案 **/tomcat-8/conf** Adobe Campaign安裝資料夾的目錄：  `/usr/local/neolane/nl6/tomcat-8/conf`
1. 在所有現有上下文元素後的底部添加以下元素：

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. 重新啟動nlserver和Apache Web伺服器。
