---
solution: Campaign Classic
product: campaign
title: 命令列
description: 命令列
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# 命令列{#command-lines}

以下命令行要求能夠訪問應用程式伺服器。 對於由Adobe托管的部署，這些命令只能由Adobe執行。

## 建立實例{#creating-an-instance}

可使用命令行以下語法執行實例建立：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

（其中&#x200B;**eng**&#x200B;和&#x200B;**fra**&#x200B;是`[lang]`參數的可能值）

使用命令&#x200B;**nlserver config -addinstance:instance1/demo*/eng**，您可以使用DNS掩碼demo*建立一個名為&#x200B;**instance1**&#x200B;的英文實例。

## 聲明資料庫{#declaring-a-database}

可以使用以下語法將現有資料庫與命令行中的實例關聯：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

**`[rdbms]`**&#x200B;參數可能有下列值：

* **postgresql**:對於PostgreSQL,
* **oracle**:oracle,
* **mssql**:對於Microsoft SQL Server,
* **DB2**:用於DB2引擎。

以下命令將&#x200B;**demo**&#x200B;實例配置為SQL類型伺服器&#x200B;**base6**，該伺服器連結到&#x200B;**campaign**&#x200B;帳戶及其&#x200B;**password**&#x200B;在&#x200B;**dbsrv**&#x200B;伺服器上的口令：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

