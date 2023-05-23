---
product: campaign
title: 連線閾值
description: 連線閾值
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 連線閾值{#connection-thresholds}



對於負載較重的伺服器，可能會超出連接閾值。 無論如何，找出原因是有用的。

有三個不同的閾值：

* 的 **Web連接閾值**，在Web伺服器中配置。 要修改它，請與系統管理員聯繫。

* 的 **資料庫連接閾值**。 要修改它，請與資料庫管理員聯繫。

* 的 **Adobe Campaign連接閾值**，可在兩個位置提供：

   * **雄貓** 側：所有查詢實際上都到達了Adobe CampaignTomcat客戶端。

      此閾值是在 **nl6/tomcat-8/conf/server.xml** 的子菜單。 的 **最大線程數** 屬性用於增加一次處理的查詢數的閾值。 例如，可以改為250。

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

   * **資料庫**:進程在資料庫上同時開啟的所有連接集。

      此閾值在檔案中配置 **nl6/conf/serverConf.xml**。 的 **maxCnx** 位於 **資料源池** 允許您增加同時處理的查詢的閾值。

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
