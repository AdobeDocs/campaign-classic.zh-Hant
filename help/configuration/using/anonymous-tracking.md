---
solution: Campaign Classic
product: campaign
title: 匿名追蹤
description: 匿名追蹤
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---


# 匿名追蹤{#anonymous-tracking}

Adobe Campaign可讓您在收件者匿名瀏覽您的網站時，將收集的網路追蹤資訊連結至收件者。 當使用者瀏覽您網站的標籤頁面時，會收集此瀏覽資訊，如此一來，當使用者點按Adobe Campaign所傳送的電子郵件時，就會識別這些資訊，並自動將資訊連結至這些網頁。

>[!IMPORTANT]
>
>在網站上設定匿名追蹤可觸發大量追蹤記錄的收集，進而影響資料庫的運作。 小心配置。\
>追蹤記錄檔會儲存在資料庫中，直到追蹤資料被清除為止。 使用部署嚮導配置清除頻率。 如需詳細資訊，請參閱[本章節](../../installation/using/deploying-an-instance.md#purging-data)。

若要在您的例項上啟用匿名Web追蹤，必須設定下列元素：

* 追蹤伺服器的&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**trackWebVisitors**&#x200B;重新導向&#x200B;**元素參數必須設為&#39;** true **&#39;，以在uuid中放置永久Cookie(** 230 **)未知網際網路使用者瀏覽網站的瀏覽器。**
* 必須在部署精靈的追蹤設定畫面中選取&#x200B;**匿名網頁追蹤**&#x200B;模式。

   ![](assets/webtracking_anonymous_set.png)

* 必須在追蹤伺服器上發佈並執行Web表格和調查。 必須在部署嚮導中選擇匹配選項。

   ![](assets/webtracking_publication_set_for_webapps.png)

