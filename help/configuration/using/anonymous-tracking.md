---
product: campaign
title: 匿名追蹤
description: 匿名追蹤
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---

# 匿名追蹤{#anonymous-tracking}

Adobe Campaign可讓您在收集到的網頁追蹤資訊以匿名方式瀏覽您的網站時，將其連結至收件者。 當使用者瀏覽您網站的已標籤頁面時，會收集此瀏覽資訊，以便在使用者點按Adobe Campaign所傳送的電子郵件後，即可識別他們，並自動將資訊連結至他們。

>[!IMPORTANT]
>
>在網站上設定匿名追蹤可觸發大量追蹤記錄的收集，進而影響資料庫操作。 謹慎配置。\
>追蹤記錄檔會儲存在資料庫中，直到追蹤資料清除為止。 使用部署嚮導配置清除頻率。 如需詳細資訊，請參閱[本章節](../../installation/using/deploying-an-instance.md#purging-data)。

若要在您的執行個體上啟用匿名Web追蹤，必須設定下列元素：

* 追蹤伺服器的&#x200B;**serverConf.xml**&#x200B;檔案的&#x200B;**trackWebVisitors**&#x200B;元素的&#x200B;**重新導向**&#x200B;參數必須設為「**true**」，以在造訪網站之未知網際網路使用者的瀏覽器中放置永久Cookie(**230**)。
* 必須在部署嚮導的跟蹤配置螢幕中選擇&#x200B;**匿名Web跟蹤**&#x200B;模式。

   ![](assets/webtracking_anonymous_set.png)

* 網路表單和調查必須在追蹤伺服器上發佈及執行。 必須在部署嚮導中選擇匹配選項。

   ![](assets/webtracking_publication_set_for_webapps.png)
