---
product: campaign
title: 連線閾值
description: 連線閾值
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 連線閾值{#connection-thresholds}



對於負載較重的伺服器，可能會超過連線臨界值。 無論如何，找出原因都很實用。

有三種不同的臨界值：

* 此 **Web連接閾值**，在您的Web伺服器中設定。 要修改它，請與系統管理員聯繫。

* 此 **資料庫連接閾值**. 要修改它，請與資料庫管理員聯繫。

* 此 **Adobe Campaign連線臨界值**，提供兩種位置：

   * **Tomcat** 側：所有查詢實際上都到達了Adobe Campaign Tomcat客戶端。

      此臨界值設定於 **nl6/tomcat-8/conf/server.xml** 檔案。 此 **maxThreads** 屬性可讓您增加一次處理的查詢數量的臨界值。 例如，可將其變更為250。

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

   * **資料庫**:由進程同時在資料庫上開啟的所有連接集。

      此臨界值已在檔案中設定 **nl6/conf/serverConf.xml**. 此 **maxCnx** 位於 **資料源池** 可讓您增加同時處理的查詢臨界值。

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
