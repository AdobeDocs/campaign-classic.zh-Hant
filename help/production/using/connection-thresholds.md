---
product: campaign
title: 連線閾值
description: 連線閾值
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# 連線閾值{#connection-thresholds}



若為大量載入的伺服器，可能會超過連線閾值。 無論如何，找出原因會很有用。

有三種不同的臨界值：

* 在網頁伺服器中設定的&#x200B;**網頁連線閾值**。 若要修改它，請連絡您的系統管理員。

* **資料庫連線閾值**。 若要修改它，請連絡您的資料庫管理員。

* **Adobe Campaign連線閾值**&#x200B;有兩個地方可供使用：

   * **Tomcat**&#x200B;端：所有查詢實際送達Adobe Campaign Tomcat使用者端。

     此臨界值設定在&#x200B;**nl6/tomcat-X/conf/server.xml**&#x200B;檔案中。 **maxThreads**&#x200B;屬性可讓您增加一次處理的查詢數臨界值。 例如，可變更為250。

     ```
     <Connector protocol="HTTP/1.1" port="8080"
                    maxThreads="75"
                    minSpareThreads="5"
                    enableLookups="true" redirectPort="8443"
                    acceptCount="100" connectionTimeout="20000"
                    disableUploadTimeout="true" />
         <Engine name="Tomcat-Standalone" defaultHost="localhost">
           <Host name="localhost" appBase="./"
                 unpackWARs="true" autoDeploy="true">
     ```

   * **資料庫**：由處理序同時開啟資料庫上所有連線的集合。

     此臨界值是在檔案&#x200B;**nl6/conf/serverConf.xml**&#x200B;中設定。 位於&#x200B;**資料來源集區**&#x200B;中的&#x200B;**maxCnx**&#x200B;屬性可讓您增加同時處理的查詢臨界值。

     ```
         <!-- Data source
              -->
           <dataSource name="default">
             <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
             <sqlParams funcPrefix="">
               <postConnectSQL/>
             </sqlParams>
             <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
           </dataSource>
     ```
