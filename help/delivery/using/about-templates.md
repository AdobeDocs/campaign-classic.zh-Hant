---
product: campaign
title: 關於範本
description: 交貨模板入門
feature: Delivery Templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 1%

---

# 關於範本{#about-templates}

![](../../assets/common.svg)

交貨配置可以保存在交貨模板中以便被重新使用。 模板可包含傳遞的完整或部分配置。

可以手動執行遞送模板，如本章所述，或根據事件（在設定時間啟動，檔案到達伺服器等）。 可通過 **[!UICONTROL Resources > Templates > Delivery templates]** 的子菜單。

![](assets/s_user_template_list.png)

模板有兩種類型：

1. Adobe Campaign本地交貨模板

   不得從系統中刪除本機模板。 它們包括每個傳送渠道的最小配置。 但是，管理員可以限制某些功能或向用戶提供預設值（跟蹤激活、發件人電子郵件地址等）。 模板清單中以粗體顯示本機方案。 必須複製它們才能修改它們。

1. 預定義的交貨模板

   Adobe Campaign管理員可以建立新的交貨模板。 操作員（那些具有適當訪問權限的操作員）或伺服器進程可自動重用它們。 例如，您可以配置電子郵件傳遞模板，當用戶使用此模板建立傳遞時，他們只需輸入文本或HTML內容，然後傳遞；其他選項已由管理員定義。

>[!NOTE]
>
>可用模板取決於您的訪問權限、實例配置和上下文。 例如，在建立資訊服務時，您可以連結確認消息的傳遞模板：然後，您只能訪問其目標映射為訂閱映射的模板。 有關此內容的詳細資訊，請參閱 [選擇目標映射](selecting-a-target-mapping.md) 和 [服務和訂閱](about-services-and-subscriptions.md)。
