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



若為過載伺服器，可能會超過連線臨界值。 無論如何，找出原因都相當實用。

有三個不同的臨界值：

* 此 **Web連線閾值**，已在網頁伺服器中設定。 若要修改它，請連絡您的系統管理員。

* 此 **資料庫連線閾值**. 若要修改它，請連絡您的資料庫管理員。

* 此 **Adobe Campaign連線臨界值**，有兩個地方可用：

   * **Tomcat** side：所有實際送達Adobe Campaign Tomcat使用者端的查詢。

      此臨界值設定於 **nl6/tomcat-8/conf/server.xml** 檔案。 此 **maxThreads** attribute可讓您增加一次處理的查詢數臨界值。 例如，可變更為250。

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

   * **資料庫**：由處理程式同時在資料庫上開啟的所有連線集。

      此臨界值是在檔案中設定的 **nl6/conf/serverConf.xml**. 此 **maxCnx** 屬性位於 **資料來源集區** 可讓您增加同時處理的查詢臨界值。

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
