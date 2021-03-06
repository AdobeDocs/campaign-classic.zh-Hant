---
product: campaign
title: 命令列
description: 命令列
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# 命令列{#command-lines}

![](../../assets/v7-only.svg)

以下命令行需要訪問應用程式伺服器的能力。 對於由Adobe托管的部署，這些命令只能由Adobe執行。

## 建立例項 {#creating-an-instance}

可使用命令列使用語法執行例項建立：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(其中 **eng** 和 **fra** 是 `[lang]` 參數)

命令 **nlserver config -addinstance:instance1/demo*/eng** 可讓您建立名為 **instance1** 英文版，帶有DNS掩碼演示*。

## 聲明資料庫 {#declaring-a-database}

您可以使用以下語法，將現有資料庫與命令行中的實例關聯：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

下列值適用於 **`[rdbms]`** 參數：

* **postgresql**:對於PostgreSQL,
* **oracle**:oracle,
* **mss**:針對Microsoft SQL Server,
* **DB2**:DB2引擎。

以下命令將配置 **示範** SQL類型伺服器的實例稱為 **base6**，連結至 **行銷活動** 帳戶及其 **密碼** 在 **dbsrv** 伺服器：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
