---
solution: Campaign Classic
product: campaign
title: 存取管理
description: 進一步瞭解存取管理最佳實務。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 5%

---


# 存取管理 {#access-management}

## 網路應用程式營運商

現成可用的webApp運算子是管理員。 若要改善安全性，請遵循下列准則：

* 以新的運算子取代直接從此運算子命名的管理員（可命名為&#39;webapp&#39;）。 如需詳細資訊，請參閱[本頁面](../../platform/using/access-management.md)。

* 將webApp運算子新增至資料夾（主要是收件者資料夾），以授與收件者的讀／寫存取權。 有關詳細資訊，請參見[此頁面](../../platform/using/access-management.md)。

* 如果使用多品牌（或多地域）例項，您可能想要將Web應用程式存取權分割為不同的收件者資料夾。 若要這麼做：

   1. 複製webApp運算子

   1. 輸入每個復本的名稱。 例如：webapp_brand、webapp_brand2等。

   1. 複製Web應用程式範本，讓每個品牌都有一個範本，並編輯屬性以變更運算元，方法是選取「使用特定帳戶」。  進一步瞭解[本頁](../../web/using/defining-web-forms-properties.md)。

## 安全群組和管理員營運商

建立足夠的安全性群組，為您的營運商提供足夠的權利，讓營運商可以做所需的事，而不是更多。

請勿使用管理員運算元（或不共用）。 為每個實際用戶建立一個運算子（以獲得準確的審計／記錄）。 將新命名的管理員新增至管理群組。 如果您未使用管理員運算子，請勿刪除它，也不要停用它：此運算子用於內部執行處理。 但您可以禁止其對客戶端控制台的[訪問，並限制其安全區（對localhost）。](../../platform/using/access-management.md)

請避免在管理員群組中新增太多運算元（或具有管理員命名的權限）。 它們是功能強大的運算子（它們可以執行所有SQL陳述式、在伺服器上執行命令等）。

Adobe Campaign通過[命名rights](../../platform/using/access-management.md#named-rights)提供三種高級權限：

* **管理** （管理員）:提供對所有內容的訪問，並允許執行所有操作，略過所有命名權限檢查，因此它包括PROGRAM EXECUTION(createProcess)和SQL命名權限

* **程式執行** (createProcess):允許執行外部程式（在伺服器上）

* **SQL**:允許在資料庫上運行SQL指令碼（以便它可以繞過安全模型）。注意：如果您需要執行複雜的計算（例如過濾），可以要求資料庫管理員建立SQL函式並將其添加到允許清單中。 進一步瞭解[本頁](../../installation/using/scripting-coding-guidelines.md)。

* **授與極少數（且受信任）運算子**
