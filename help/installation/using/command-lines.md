---
product: campaign
title: 命令列
description: 命令列
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# 命令列{#command-lines}

以下命令行需要訪問應用程式伺服器的能力。 對於由Adobe托管的部署，這些命令只能由Adobe執行。

## 建立實例{#creating-an-instance}

可使用命令列使用語法執行例項建立：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

（其中&#x200B;**eng**&#x200B;和&#x200B;**fra**&#x200B;是`[lang]`參數的可能值）

命令&#x200B;**nlserver config -addinstance:instance1/demo*/eng**&#x200B;允許您使用DNS掩碼演示*建立一個名為&#x200B;**instance1**&#x200B;的實例，該實例的英文版為。

## 聲明資料庫{#declaring-a-database}

您可以使用以下語法，將現有資料庫與命令行中的實例關聯：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

**`[rdbms]`**&#x200B;參數可能有下列值：

* **postgresql**:對於PostgreSQL,
* **oracle**:oracle,
* **mssql**:對於Microsoft SQL Server,
* **DB2**:DB2引擎。

以下命令使用名為&#x200B;**base6**&#x200B;的SQL類型伺服器配置&#x200B;**demo**&#x200B;實例，該伺服器連結到&#x200B;**campaign**&#x200B;帳戶及其&#x200B;**password**&#x200B;在&#x200B;**dbsrv**&#x200B;伺服器上：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
