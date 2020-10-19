---
title: Campaign Classic資料庫建議
description: 資料庫建議
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# 資料庫{#database}

資料庫伺服器可以在任何給定作業系統上運行，而不管應用程式伺服器或伺服器使用的作業系統是什麼，只要它們之間有網路連接。

只要Adobe Campaign的不同元件都可連線，資料庫伺服器的作業系統就不重要。

同時檢查「數 [據庫訪問層](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 」部分。

## Microsoft SQL Server {#microsoft-sql-server}

原生用戶端必須安裝在Adobe Campaign應用程式伺服器上。

可以通過ODBC驅動程式配置面板(在 **SQL Server Native Client 11.0下)檢查伺服器上的本機客戶端**。

必須存在以下訪問DLL: **sqlncli11.dll**。

訪問DLL可在Microsoft網站上找到。

>[!NOTE]
>
>不支援從運行在Linux中的應用程式伺服器訪問Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支援含多位元組字元的欄名稱。

需要 **正確配置NLS_NCHAR_CHARACTERSET** 和 **** NLS_CHARACTERSET參數，以使資料庫能夠在Unicode或ANSI中工作。

Adobe Campaign使用預設的Oracle編碼。 使用其他編碼可能會觸發相容性問題：在此情況下，請聯絡技術支援。

要瞭解您的編碼，請使用以下 **sqlplus命令** :

```
SELECT * FROM nls_database_parameters ;
```

* 對於Unicode安裝，支援的編碼為：

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* 對於ANSI安裝（非Unicode），僅支援以下編碼：

```
  NLS_CHARACTERSET WE8MSWIN1252
```

要登錄 **sqlplus**，請使用Oracle用戶配置檔案：

```
su - oracle 
sqlplus 
[login] [password]
```

您也可以參考Linux [中的Oracle Client](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)。

## PostgresSQL {#postgressql}

我們建議您在安裝資料庫引擎時安裝UTF-8支援。 這樣，您將能夠建立Unicode資料庫。

**相關主題**

* [Adobe Campaign Classic表格中的取消登入選項](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
