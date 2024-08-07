---
product: campaign
title: 關於範本
description: 開始使用傳遞範本
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Delivery Templates
role: User
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---

# 關於範本{#about-templates}

傳遞設定可以儲存在傳遞範本中以便重複使用。 範本可能包含傳遞的完整或部分設定。

傳遞範本可以手動執行（如本章所述），或根據事件（在設定時間啟動、檔案到達伺服器等）執行。 傳遞範本可透過樹狀結構中的&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;節點進行設定。

![](assets/s_user_template_list.png)

範本有兩種型別：

1. Adobe Campaign原生傳遞範本

   不得從系統中刪除原生範本。 其中包含每個傳送通道的最低設定。 但是，管理員可以限制某些功能，或為使用者提供預設值（追蹤啟動、寄件者電子郵件地址等）。 原生案例會以粗體顯示在範本清單中。 必須複製它們才能修改它們。

1. 預先定義的傳遞範本

   Adobe Campaign管理員可以建立新的傳遞範本。 操作者（擁有適當存取許可權者）或伺服器程式可自動重複使用這些存取許可權。 例如，您可以設定電子郵件傳遞範本，當使用者使用此範本建立傳遞時，他們只需輸入文字或HTML內容然後傳遞即可；管理員已定義其他選項。

>[!NOTE]
>
>可用的範本取決於存取權、執行個體設定和上下文。 例如，當您建立資訊服務時，可以連結確認訊息的傳遞範本：然後您只能存取其目標對應為訂閱對應的範本。 如需詳細資訊，請參閱[選取目標對應](selecting-a-target-mapping.md)和[服務與訂閱](about-services-and-subscriptions.md)。
