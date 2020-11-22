---
solution: Campaign Classic
product: campaign
title: 連線閾值
description: 連線閾值
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---


# 連線閾值{#connection-thresholds}

對於負載較重的伺服器，可能會超出連接閾值。 無論如何，找出原因都很有用。

有三種不同的臨界值：

1. Web連接閾值，在Web伺服器中配置。 要修改它，請與系統管理員聯繫。
1. 資料庫連接閾值。 要修改它，請與資料庫管理員聯繫。
1. Adobe Campaign連線臨界值可在兩處使用：

   * Tomcat側：實際到達Adobe Campaign Tomcat用戶端的所有查詢。

      此閾值在nl6/tomcat-8/conf/server.xml檔案中 **配置** 。 maxThreads **** 屬性可讓您增加一次處理之查詢數的臨界值。 例如，可變更為250。

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

   * 資料庫：進程在資料庫上同時開啟的所有連接集。

      此閾值在檔案nl6/conf/serverConf.xml中 **配置**。 位於 **資料來源** pool中的maxCnx **屬性** ，可讓您增加同時處理的查詢臨界值。

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

