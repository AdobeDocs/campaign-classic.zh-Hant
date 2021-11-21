---
product: campaign
title: Campaign Tomcat設定
description: Campaign Tomcat設定
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: ed9e76495efb0cb49e248a7d38417642c5094a11
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 配置Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign使用 **名為Apache Tomcat的嵌入式Web servlet** 處理應用程式與任何外部介面（包括用戶端主控台、追蹤的URL連結、SOAP呼叫等）之間的HTTP/HTTPS要求。 對於任何面向外部的Adobe Campaign例項，此前通常會有外部Web伺服器（通常是IIS或Apache）。

進一步了解Campaign中的Tomcat，以及如何在中找到您的Tomcat版本 [本頁](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。

## Apache Tomcat的預設埠 {#default-port-for-tomcat}

當Tomcat伺服器的8080偵聽埠已忙於配置所需的另一個應用程式時，您需要用一個空閒埠（例如8090）替換8080埠。 若要變更，請編輯 **server.xml** 檔案儲存於 **/tomcat-8/conf** Adobe Campaign安裝資料夾的目錄。

然後修改JSP中繼頁的埠。 若要這麼做，請變更 **serverConf.xml** 檔案儲存於 **/conf** Adobe Campaign安裝目錄的目錄。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 映射Apache Tomcat中的資料夾 {#mapping-a-folder-in-tomcat}

若要定義客戶特定設定，您可以建立 **user_contexts.xml** 檔案 **/tomcat-8/conf** 資料夾，其中也包含 **contexts.xml** 檔案。

此檔案將包含下列類型的資訊：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可在伺服器端重新產生此操作。
