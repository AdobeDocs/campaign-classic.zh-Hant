---
solution: Campaign Classic
product: campaign
title: Campaign Tomcat設定
description: Campaign Tomcat設定
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# 配置Apache Tomcat {#configuring-tomcat}

Adobe Campaign使用&#x200B;**內嵌的Web servlet，稱為Apache Tomcat**，處理應用程式與任何外部介面（包括用戶端主控台、追蹤的URL連結、SOAP呼叫等）之間的HTTP/HTTPS要求。 對於任何外部對應的Adobe Campaign實例，通常在此之前都有外部Web伺服器（通常為IIS或Apache）。

進一步瞭解Campaign中的Tomcat，以及如何在[本頁](../../production/using/locate-tomcat-version.md)中找到您的Tomcat版本。

## Apache Tomcat {#default-port-for-tomcat}的預設埠

當Tomcat伺服器的8080偵聽埠已忙於配置所需的其他應用程式時，您需要將8080埠替換為免費埠（例如8090）。 要更改它，請編輯保存在Adobe Campaign安裝資料夾&#x200B;**/tomcat-8/conf**&#x200B;目錄中的&#x200B;**server.xml**&#x200B;檔案。

然後修改JSP中繼頁的埠。 為此，請更改保存在Adobe Campaign安裝目錄&#x200B;**/conf**&#x200B;目錄中的&#x200B;**serverConf.xml**&#x200B;檔案。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 映射Apache Tomcat {#mapping-a-folder-in-tomcat}中的資料夾

要定義客戶特定設定，可以在&#x200B;**/tomcat-8/conf**&#x200B;資料夾中建立&#x200B;**user_contexts.xml**&#x200B;檔案，該檔案還包含&#x200B;**contexts.xml**&#x200B;檔案。

此檔案將包含下列類型的資訊：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可在伺服器端重制此作業。
