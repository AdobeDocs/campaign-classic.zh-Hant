---
product: campaign
title: 命令列
description: 命令列
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 4%

---

# 命令列{#command-lines}



下列命令列需要存取應用程式伺服器的能力。 對於由Adobe託管的部署，這些命令只能由Adobe執行。

## 建立執行個體 {#creating-an-instance}

您可以使用命令列來建立執行個體，語法如下：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(其中 **英文** 和 **週五** 下列各項的可能值： `[lang]` 引數)

指令 **nlserver config -addinstance：instance1/demo&#42;/eng** 可讓您建立名為的執行個體， **instance1** 英文版搭配DNS遮罩示範&#42;.

## 宣告資料庫 {#declaring-a-database}

您可以使用下列語法，從命令列將現有資料庫與執行處理相關聯：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

下列的值適用於 **`[rdbms]`** 引數：

* **postgresql**：對於PostgreSQL，
* **oracle**：針對Oracle，
* **mssql**：針對Microsoft SQL Server，
* **DB2**：適用於DB2引擎。

以下指令會設定 **示範** 具有SQL型別伺服器的執行個體稱為 **base6**，連結至 **行銷活動** 帳戶及其 **密碼** 於 **dbsrv** 伺服器：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
