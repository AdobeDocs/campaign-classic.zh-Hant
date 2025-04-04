---
product: campaign
title: 存取管理
description: 進一步瞭解存取管理最佳實務
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 8%

---

# 存取管理 {#access-management}



## Webapp運運算元

WebApp運運算元是立即可用的管理員。 若要改善安全性，請遵循下列准則：

* 將此運運算元中名為許可權的管理員取代為新管理員（可命名為「webapp」）。 如需詳細資訊，請參閱[本頁面](../../platform/using/access-management.md)。

* 在資料夾（主要是收件者資料夾）中新增webApp運運算元，以授予收件者讀取/寫入許可權。 如需詳細資訊，請參閱[此頁面](../../platform/using/access-management.md)。

* 如果使用多品牌（或多地理）執行個體，您可能會想要將Web應用程式存取權分割至不同的收件者資料夾。 若要這麼做：

   1. 複製webApp運運算元

   1. 輸入每個重複專案的名稱。 例如：webapp_brand、webapp_brand2等。

   1. 複製Web應用程式範本讓每個品牌擁有一個範本，並選取「使用特定帳戶」來編輯屬性以變更運運算元。  在[本頁](../../web/using/defining-web-forms-properties.md)中瞭解更多。

## 安全性群組與管理員操作員

建立足夠的安全群組，讓您的操作員擁有足夠的權利，讓他們能執行他們需要的動作，而不是更多。

請勿使用管理員運運算元（或不共用該運運算元）。 為每個實體使用者建立一個運運算元（以便擁有準確的稽核/記錄）。 將您新命名的管理員新增至管理員群組。 如果您不使用管理員運運算元，請勿將其刪除，也請勿停用它：此運運算元在內部用於執行處理。 但您可以禁止其[存取使用者端主控台](../../platform/using/access-management.md)，並限制其安全區域（至localhost）。

避免在管理員群組中新增太多運運算元（或具有管理員命名許可權）。 它們是功能非常強大的運運算元（它們可以執行所有SQL陳述式、在伺服器上執行命令等等）。

Adobe Campaign透過[已命名的許可權](../../platform/using/access-management.md#named-rights)提供三個高階許可權：

* **管理** （管理員）：提供存取所有專案的許可權，並允許執行所有專案，略過所有命名的許可權檢查，因此包含程式執行(createProcess)和SQL命名的許可權

* **程式執行** (createProcess)：允許執行外部程式（在伺服器上）

* **SQL**：允許在資料庫上執行SQL指令碼（因此它可以略過安全性模式）。 注意：如果您需要執行複雜的計算（例如篩選），您可以要求資料庫管理員建立SQL函式，並將它們新增至允許清單。 在[本頁](../../installation/using/scripting-coding-guidelines.md)中瞭解更多。

* **將其授與極少（且受信任的）運運算元**
