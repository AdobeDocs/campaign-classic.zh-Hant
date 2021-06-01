---
product: campaign
title: Campaign Tomcat設定
description: Campaign Tomcat設定
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf,b4a422b4-4b8b-4883-8d74-0dccda4a5ef3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 配置Apache Tomcat {#configuring-tomcat}

Adobe Campaign使用名為Apache Tomcat **的**&#x200B;內嵌web servlet，在應用程式和任何外部介面（包括客戶端控制台、追蹤的URL連結、SOAP呼叫等）之間處理HTTP/HTTPS要求。 對於任何面向外部的Adobe Campaign例項，此前通常會有外部Web伺服器（通常是IIS或Apache）。

進一步了解Campaign中的Tomcat，以及如何在[此頁面](../../production/using/locate-tomcat-version.md)中找到您的Tomcat版本。

>[!NOTE]
>
>此程式僅限於&#x200B;**內部部署**&#x200B;部署。


## Apache Tomcat {#default-port-for-tomcat}的預設埠

當Tomcat伺服器的8080偵聽埠已忙於配置所需的另一個應用程式時，您需要用一個空閒埠（例如8090）替換8080埠。 若要變更，請編輯儲存在Adobe Campaign安裝資料夾&#x200B;**/tomcat-8/conf**&#x200B;目錄中的&#x200B;**server.xml**&#x200B;檔案。

然後修改JSP中繼頁的埠。 要執行此操作，請變更儲存在Adobe Campaign安裝目錄&#x200B;**/conf**&#x200B;目錄中的&#x200B;**serverConf.xml**&#x200B;檔案。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 映射Apache Tomcat {#mapping-a-folder-in-tomcat}中的資料夾

若要定義客戶特定設定，您可以在&#x200B;**/tomcat-8/conf**&#x200B;資料夾中建立&#x200B;**user_contexts.xml**&#x200B;檔案，該資料夾中也包含&#x200B;**contexts.xml**&#x200B;檔案。

此檔案將包含下列類型的資訊：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可在伺服器端重新產生此操作。
