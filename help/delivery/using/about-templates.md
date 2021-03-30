---
solution: Campaign Classic
product: campaign
title: 關於範本
description: 關於範本
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---


# 關於範本{#about-templates}

傳送設定可儲存在傳送範本中，以便重新使用。 範本可能包含傳送的完整或部分設定。

可如本章所述手動執行傳送模板，或根據事件（在指定時間啟動，檔案到達伺服器等）執行。 可通過樹中的&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;節點配置傳送模板。

![](assets/s_user_template_list.png)

範本有兩種類型：

1. Adobe Campaign本地交付模板

   不得從系統中刪除原生模板。 它們包含每個傳送管道的最低組態。 不過，管理員可以限制某些功能或提供預設值給使用者（追蹤啟動、寄件者電子郵件地址等）。 範本清單中的原生藍本會以粗體顯示。 必須複製它們才能修改它們。

1. 預先定義的傳送範本

   Adobe Campaign管理員可以建立新的傳送範本。 營運商（具有適當存取權限的營運商）或伺服器程式可自動重複使用。 例如，您可以設定電子郵件傳送範本，當使用者使用此範本建立傳送時，他只需要輸入文字或HTML內容，然後傳送；管理員已經定義了其他選項。

>[!NOTE]
>
>可用的範本取決於您的存取權限、您的例項設定，以及內容。 例如，當您建立資訊服務時，可以連結傳送範本以確認訊息：然後您只能存取其目標對應為訂閱對應的範本。 有關詳細資訊，請參閱[選擇目標映射](../../delivery/using/selecting-a-target-mapping.md)和[關於服務和訂閱](../../delivery/using/about-services-and-subscriptions.md)。
