---
title: 無法連接
seo-title: 無法連接
description: 無法連接
seo-description: null
page-status-flag: never-activated
uuid: 5e4cf47d-9699-4b4c-9c45-064fdc17110a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 493067fb-68f1-48b9-afaa-3127a847db83
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 90813bc2913d56136067b9f64c0e934df3f17473

---


# 無法連接{#failure-to-connect}

其原因可能是多重的，並取決於各種情況。

檢查安全區的常規配置。

>[!NOTE]
>
>有關配置安全區的詳細資訊，請參 [閱本節](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

檢查以下資訊：

1. **網路檢查**

   * 您是否可從電腦存取網際網路？

      檢查您是否可以連線至網際網路上的網站（例如）。 如果您無法連線，問題就在您的電腦上。 請連絡您的系統管理員。

   * 您是否可透過其他服務連線至代管Adobe Campaign的伺服器？

      通過SSH或任何其他方式連接到伺服器。 如果不可能，則您的主機公司有問題。 聯繫其系統管理員。

1. **檢查Web伺服器端** (IIS/apache/etc.)

   * Web伺服器是否響應？

      使用網頁瀏覽器連線至Adobe Campaign伺服器存取URL: **http(s)://`<urlserver>`**. 如果未響應，則Web伺服器將停止在電腦上。 請洽詢您主機公司的系統管理員以重新啟動服務。

   * Adobe Campaign是否已正確整合？

      登入： **http(s):///`<urlserver>`/r/test** URL。 伺服器應返回以下類型的消息

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      如果未獲得此結果，請檢查Web伺服器配置中已考慮到整合。

1. **在Adobe Campaign端進行檢查**

   * Adobe Campaign web模組是否已啟動？

      連線至下列URL: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * 如果獲得Tomcat Java錯誤：

         JAVA整合是否正確執行？ Adobe Campaign需要SUN JDK。

         它已整合在檔案/nl6/customer.sh中 **`[path of application]`。**

      * 如果您取得空白頁面：

         Adobe Campaign web模組是否已啟動？ 您應獲得：

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * 如果不是，請使用以下命令重新啟動它：

         ```
         nlserver start web
         ```
>[!NOTE]
>
>如果您在列出Adobe Campaign模組時，取得下列類型的回應： **nlserver pdump**
>DD/MM/YYYY的Adobe Campaign Classic(7.X YY.R組建XXX@SHA1)的HH:MM:SS >應用程式伺服器無任務您必須重新啟動整個Adobe Campaign應用程式。 若要這麼做，請使用下列命令：**nlserver watchdog -svc -noconsole*
