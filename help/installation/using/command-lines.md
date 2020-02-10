---
title: 命令行
seo-title: 命令行
description: 命令行
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 命令行{#command-lines}

以下命令行要求能夠訪問應用程式伺服器。 對於Adobe代管的部署，這些命令只能由Adobe執行。

## 建立例項 {#creating-an-instance}

可使用命令行以下語法執行實例建立：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(其中 **eng** 和 **fra** 是參數的可能 `[lang]` 值)

命令 **nlserver config -addinstance:instance1/demo*/eng** ，使用DNS掩碼示範*建立一個名為 **instance1** 的英文實例。

## 聲明資料庫 {#declaring-a-database}

可以使用以下語法將現有資料庫與命令行中的實例關聯：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

參數可能有下列 **`[rdbms]`** 值：

* **postgresql**:對於PostgreSQL,
* **oracle**:對於Oracle,
* **mssql**:對於Microsoft SQL Server,
* **DB2**:用於DB2引擎。

以下命令 **demo** with the SQL type server configures the **demo6**, linked to the campaign account and its password **on the********** dbsrv Server:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

