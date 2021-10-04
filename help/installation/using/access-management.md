---
product: campaign
title: 存取管理
description: 進一步了解存取管理最佳實務。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 8%

---

# 存取管理 {#access-management}

![](../../assets/v7-only.svg)

## 網頁應用程式運算子

WebApp運算子是立即可用的管理員。 要提高安全性，請遵循以下准則：

* 以新運算子取代此運算子中直接命名為的管理員（可命名為「webapp」）。 如需詳細資訊，請參閱[本頁面](../../platform/using/access-management.md)。

* 在資料夾（主要是收件者資料夾）中新增webApp運算子，以授與收件者的讀/寫存取權。 如需詳細資訊，請參閱[此頁面](../../platform/using/access-management.md)。

* 如果使用多品牌（或多地理）例項，您可能會想要將Web應用程式存取權分割為不同的收件者資料夾。 若要這麼做：

   1. 複製webApp運算子

   1. 輸入每個重複項的名稱。 例如：webapp_brand、webapp_brand2等。

   1. 複製Web應用程式模板以使每個品牌具有一個模板，並通過選擇「使用特定帳戶」來編輯屬性以更改運算子。  在[本頁](../../web/using/defining-web-forms-properties.md)中瞭解更多。

## 安全群組和管理員運算子

建立足夠的安全性群組，為您的運算子提供足夠的權限，讓他們能夠執行所需的操作，而不是執行更多操作。

請勿使用管理員運算子（或請勿共用）。 為每個實際用戶建立一個運算子（以具有準確的審計/記錄）。 將新命名的管理員新增至管理群組。 如果您未使用管理員運算子，請勿將其刪除，也不要加以停用：此運算子用於內部執行處理。 但您可以禁止其[對客戶端控制台的訪問](../../platform/using/access-management.md)並限制其安全區域（本地主機）。

請避免在管理員群組中新增太多運算子（或具有已命名管理員權限）。 它們是功能強大的運算子（它們可以執行所有SQL陳述式、在伺服器上執行命令等）。

Adobe Campaign透過[命名權限](../../platform/using/access-management.md#named-rights)提供三個高階權限：

* **管理** （管理）:提供對所有內容的訪問，並允許執行所有操作，繞過所有已命名的權限檢查，因此它包括PROGRAM EXECUTION(createProcess)和SQL已命名的權限

* **程式執行** (createProcess):允許執行外部程式（在伺服器上）

* **SQL**:允許在資料庫上運行SQL指令碼（以便繞過安全模型）。注意：如果需要執行複雜的計算（例如篩選），可以請資料庫管理員建立SQL函式並將其添加到允許清單中。 在[本頁](../../installation/using/scripting-coding-guidelines.md)中瞭解更多。

* **將它們授予極少（且受信任的）運算子**
