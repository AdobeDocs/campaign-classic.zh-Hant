---
product: campaign
title: 匿名追蹤
description: 瞭解如何設定匿名追蹤
feature: Configuration, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 5%

---

# 匿名追蹤{#anonymous-tracking}

當收件者匿名瀏覽您的網站時，Adobe Campaign可讓您將收集的網頁追蹤資訊連結至該收件者。 當使用者瀏覽您網站的已標籤頁面時，系統會收集此瀏覽資訊，這樣當使用者按一下Adobe Campaign傳送的電子郵件後，系統就會識別這些頁面，且資訊會自動連結至這些頁面。

>[!IMPORTANT]
>
>在網站上設定匿名追蹤可能會觸發大量追蹤記錄的收集，進而影響資料庫作業。 請謹慎設定。\
>追蹤記錄會儲存在資料庫中，直到清除追蹤資料為止。 使用部署精靈來設定清除頻率。 如需詳細資訊，請參閱[本章節](../../installation/using/deploying-an-instance.md#purging-data)。

若要在您的執行個體上啟用匿名Web追蹤，必須設定下列元素：

* 此 **trackWebVisitors** 的引數 **重新導向** 的元素 **serverConf.xml** 追蹤伺服器的檔案必須設定為&#39;**true**&#39;，放置永久Cookie (**uuid230**)，這些瀏覽器屬於造訪網站的未知網際網路使用者。
* 此 **匿名網路追蹤** 必須在部署精靈的追蹤設定畫面中選取模式。

  ![](assets/webtracking_anonymous_set.png)

* 網路表單必須在追蹤伺服器上發佈及執行。 必須在部署精靈中選取相符選項。

  ![](assets/webtracking_publication_set_for_webapps.png)
