---
title: 匿名追蹤
seo-title: 匿名追蹤
description: 匿名追蹤
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 匿名追蹤{#anonymous-tracking}

Adobe Campaign可讓您在收件者匿名瀏覽您的網站時，將收集的網路追蹤資訊連結至收件者。 當使用者瀏覽您網站的標籤頁面時，會收集此瀏覽資訊，如此一來，當使用者點按Adobe Campaign所傳送的電子郵件時，就會識別這些資訊，並自動將資訊連結至這些網頁。

>[!IMPORTANT]
>
>在網站上設定匿名追蹤可觸發大量追蹤記錄的收集，進而影響資料庫的運作。 小心配置。\
>追蹤記錄檔會儲存在資料庫中，直到追蹤資料被清除為止。 使用部署嚮導配置清除頻率。 如需詳細資訊，請參閱[本小節](../../installation/using/deploying-an-instance.md#purging-data)。

若要在您的例項上啟用匿名Web追蹤，必須設定下列元素：

* 追蹤 **的server** Conf.xml檔案中，trackVisitors元素的 **trackWebVisitors參數必須設定為「TrueConf** 」，以在造訪網站之未知使用者的網際網路瀏覽器中放置 ************ Cookie(permonantUuid 230B)。
* 必須 **** 在部署精靈的追蹤設定畫面中選取「匿名Web追蹤」模式。

   ![](assets/webtracking_anonymous_set.png)

* 必須在追蹤伺服器上發佈並執行Web表格和調查。 必須在部署嚮導中選擇匹配選項。

   ![](assets/webtracking_publication_set_for_webapps.png)

