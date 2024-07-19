---
product: campaign
title: 命令列
description: 命令列
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%

---

# 命令列{#command-lines}



下列命令列需要存取應用程式伺服器的能力。 對於由Adobe託管的部署，這些命令只能由Adobe執行。

## 建立執行個體 {#creating-an-instance}

您可以使用命令列來建立執行個體，語法如下：

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

（**eng**&#x200B;和&#x200B;**fra**&#x200B;可能是`[lang]`引數的值）

命令&#x200B;**nlserver config -addinstance：instance1/demo&#42;/eng**&#x200B;可讓您使用DNS遮罩示範&#42;以英文建立名為&#x200B;**instance1**&#x200B;的執行個體。

## 宣告資料庫 {#declaring-a-database}

您可以使用下列語法，從命令列將現有資料庫與執行處理相關聯：

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

**`[rdbms]`**&#x200B;引數可能有下列值：

* **postgresql**：對於PostgreSQL，
* **oracle**：針對Oracle，
* **mssql**：對於Microsoft SQL Server，

下列命令使用稱為&#x200B;**base6**&#x200B;的SQL型別伺服器設定&#x200B;**demo**&#x200B;執行個體，連結至&#x200B;**dbsrv**&#x200B;伺服器上的&#x200B;**campaign**&#x200B;帳戶及其&#x200B;**密碼**：

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
