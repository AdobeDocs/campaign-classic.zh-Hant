---
product: campaign
title: 命令列
description: 命令列
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# 命令列{#command-lines}



下列命令列需要存取應用程式伺服器的能力。 對於由Adobe託管的部署，這些命令只能由Adobe執行。

## 建立執行個體 {#creating-an-instance}

您可以使用命令列來建立執行個體，語法如下：

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(其中 **英文** 和 **週五** 為的可能值 `[lang]` parameter)

命令 **nlserver config -addinstance：instance1/demo&#42;/eng** 可讓您建立名為的執行個體 **instance1** DNS遮罩示範的英文&#42;.

## 宣告資料庫 {#declaring-a-database}

您可以使用下列語法，從命令列將現有資料庫與執行處理建立關聯：

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

下列值適用於 **`[rdbms]`** 引數：

* **postgresql**：對於PostgreSQL，
* **oracle**：若為Oracle，
* **mssql**：對於Microsoft SQL Server，
* **DB2**：適用於DB2引擎。

以下指令會設定 **示範** 具有SQL型別伺服器的執行個體，稱為 **base6**，連結至 **行銷活動** 帳戶及其 **密碼** 於 **dbsrv** 伺服器：

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
