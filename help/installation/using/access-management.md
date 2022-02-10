---
product: campaign
title: 存取管理
description: 瞭解有關訪問管理最佳做法的更多資訊
feature: Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 8%

---

# 存取管理 {#access-management}

![](../../assets/v7-only.svg)

## Webapp操作員

現成， WebApp操作員是管理員。 要提高安全性，請遵循以下准則：

* 將此操作員中名為right的管理員替換為新管理員（可以命名為「webapp」）。 如需詳細資訊，請參閱[本頁面](../../platform/using/access-management.md)。

* 在資料夾（主要是收件人資料夾）中添加WebApp運算子，以授予收件人讀/寫權限。 如需詳細資訊，請參閱[此頁面](../../platform/using/access-management.md)。

* 如果使用多品牌（或多地域）實例，您可能希望將Web應用程式訪問權限拆分為不同的收件人資料夾。 若要這麼做：

   1. 複製WebApp運算子

   1. 輸入每個副本的名稱。 例如：webapp_brand 、 webapp_brand2等。

   1. 複製一個Web應用程式模板，使每個品牌有一個模板，並通過選擇使用特定帳戶編輯屬性以更改運算子。  在[本頁](../../web/using/defining-web-forms-properties.md)中瞭解更多。

## 安全組和管理員操作員

建立足夠的安全組，為操作員提供足夠的權限，讓他們做他們需要的事情，而不是更多。

請勿使用管理員操作員（或不共用它）。 為每個物理用戶建立一個操作員（以進行準確的審核/記錄）。 將新命名的管理員添加到管理組。 如果不使用管理員操作員，請不要刪除它，也不要禁用它：此運算子用於內部執行處理。 但你可以禁止 [訪問客戶端控制台](../../platform/using/access-management.md) 並限制其安全區域（到本地主機）。

避免在管理員組（或具有管理員命名權限）中添加過多的操作員。 它們是功能非常強大的運算子（它們可以執行所有SQL陳述式，在伺服器上執行命令等）。

Adobe Campaign通過 [命名權限](../../platform/using/access-management.md#named-rights):

* **管理** （管理員）:允許訪問所有內容並允許執行所有操作，繞過所有已命名的權限檢查，因此它包括PROGRAM EXECUTION(createProcess)和SQL已命名權限

* **程式執行** （建立進程）:允許執行外部程式（在伺服器上）

* **SQL**:允許在資料庫上運行SQL指令碼（以便它可以繞過安全模型）。 注：如果需要執行複雜的計算（例如篩選），可以要求資料庫管理員建立SQL函式並將其添加到allowlist中。 在[本頁](../../installation/using/scripting-coding-guidelines.md)中瞭解更多。

* **將它們授予極少（和受信任）的運算子**
