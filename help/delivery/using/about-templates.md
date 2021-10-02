---
product: campaign
title: 關於範本
description: 關於範本
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---

# 關於範本{#about-templates}

![](../../assets/common.svg)

傳遞設定可儲存在傳遞範本中以供重複使用。 範本可能包含傳送的完整或部分設定。

傳遞範本可依照本章所述手動執行，或根據事件（在設定時間啟動、檔案到達伺服器時啟動等）執行。 傳遞範本可透過樹狀結構中的&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;節點進行設定。

![](assets/s_user_template_list.png)

範本有兩種類型：

1. Adobe Campaign原生傳送範本

   不得從系統中刪除本機範本。 這些量度包含每個傳送通道的最低設定。 不過，管理員可以限制特定功能或提供預設值給使用者（追蹤啟用、寄件者電子郵件地址等）。 範本清單中以粗體顯示原生案例。 必須複製它們，才能加以修改。

1. 預先定義的傳遞範本

   Adobe Campaign管理員可以建立新的傳遞範本。 操作員（具有適當訪問權限的操作員）或伺服器進程可自動重複使用它們。 例如，您可以設定電子郵件傳送範本，而當使用者使用此範本建立傳送時，他們只需輸入文字或HTML內容，然後傳送即可；管理員已定義了其他選項。

>[!NOTE]
>
>可用的範本取決於您的存取權限、執行個體設定和內容。 例如，當您建立資訊服務時，可以連結確認訊息的傳送範本：然後，您只能訪問其目標映射為訂閱映射的模板。 有關詳細資訊，請參閱[選擇目標映射](selecting-a-target-mapping.md)和[關於服務和訂閱](about-services-and-subscriptions.md)。
