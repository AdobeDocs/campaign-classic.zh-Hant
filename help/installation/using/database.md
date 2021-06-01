---
product: campaign
title: Campaign Classic資料庫建議
description: 資料庫建議
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 資料庫{#database}

資料庫伺服器可以在任何給定的作業系統上運行，而不管應用伺服器或伺服器使用的作業系統為何，只要它們之間有網路連接。

只要與Adobe Campaign的不同元件有連線，資料庫伺服器的作業系統就不重要。

另請檢查[資料庫訪問層](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers)部分。

## Microsoft SQL Server {#microsoft-sql-server}

本機用戶端必須安裝在Adobe Campaign應用程式伺服器上。

可以通過ODBC驅動程式配置面板在&#x200B;**SQL Server本機客戶端11.0**&#x200B;下檢查伺服器上的本機客戶端。

必須存在以下訪問DLL:**sqlncli11.dll**。

在Microsoft網站上找到訪問DLL。

>[!NOTE]
>
>不支援從在Linux中運行的應用程式伺服器訪問Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支援含有多位元組字元的欄名稱。

需要正確配置&#x200B;**NLS_NCHAR_CHARACTERSET**&#x200B;和&#x200B;**NLS_CHARACTERSET**&#x200B;參數，以使資料庫在Unicode或ANSI中工作。

Adobe Campaign使用預設Oracle編碼。 使用其他編碼可能會觸發相容性問題：在此情況下，請聯絡技術支援。

要了解您的編碼，請使用以下&#x200B;**sqlplus**&#x200B;命令：

```
SELECT * FROM nls_database_parameters ;
```

* 若為Unicode安裝，支援的編碼為：

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* 對於ANSI安裝（非Unicode），僅支援以下編碼：

```
  NLS_CHARACTERSET WE8MSWIN1252
```

要登錄&#x200B;**sqlplus**，請使用Oracle用戶配置檔案：

```
su - oracle 
sqlplus 
[login] [password]
```

您也可以在Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)中參考[Oracle客戶端。

## PostgresSQL {#postgressql}

建議您在安裝資料庫引擎時安裝UTF-8支援。 這樣，您將能夠建立Unicode資料庫。

**相關主題**

* [Adobe Campaign Classic表格中的取消登入選項](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
