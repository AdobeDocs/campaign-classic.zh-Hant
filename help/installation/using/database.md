---
product: campaign
title: Campaign Classic資料庫建議
description: 資料庫建議
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---

# 資料庫{#database}



資料庫伺服器可以在任何給定的作業系統上運行，而不管應用伺服器或伺服器使用的作業系統為何，只要它們之間有網路連接。

只要與Adobe Campaign的不同元件有連線，資料庫伺服器的作業系統就不重要。

同時檢查 [資料庫訪問層](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 區段。

## Microsoft SQL Server {#microsoft-sql-server}

本機用戶端必須安裝在Adobe Campaign應用程式伺服器上。

您可以通過ODBC驅動程式配置面板(位於 **SQL Server本機客戶端11.0**.

必須存在以下訪問DLL: **sqlncli11.dll**.

在Microsoft網站上找到存取DLL。

>[!NOTE]
>
>不支援從在Linux中運行的應用程式伺服器訪問Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支援含有多位元組字元的欄名稱。

此 **NLS_NCHAR_CHARACTERSET** 和 **NLS_CHARACTERSET** 必須正確配置參數，才能使資料庫在Unicode或ANSI中工作。

Adobe Campaign使用預設Oracle編碼。 使用其他編碼可能會觸發相容性問題：在此情況下，請聯絡技術支援。

若要了解您的編碼，請使用下列項目 **sqlplus** 命令：

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

登入 **sqlplus**，請使用Oracle使用者設定檔：

```
su - oracle 
sqlplus 
[login] [password]
```

您也可以參閱 [OracleLinux中的客戶端](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

建議您在安裝資料庫引擎時安裝UTF-8支援。 這樣，您將能夠建立Unicode資料庫。

**相關主題**

* [Adobe Campaign Classic表格中的取消登入選項](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
