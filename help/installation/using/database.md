---
product: campaign
title: Campaign Classic資料庫建議
description: 資料庫建議
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---

# 資料庫{#database}



資料庫伺服器可以在任何給定作業系統上運行，而不管應用程式伺服器或伺服器使用的作業系統是什麼，只要它們之間有網路連接。

只要能夠與Adobe Campaign的不同元件建立連接，資料庫伺服器的作業系統就不重要。

同時檢查 [資料庫訪問層](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 的子菜單。

## Microsoft SQL Server {#microsoft-sql-server}

本機客戶端必須安裝在Adobe Campaign應用程式伺服器上。

可以通過ODBC驅動程式配置面板，在 **SQL Server本機客戶端11.0**。

必須存在以下訪問DLL: **sqlncli11.dll**。

訪問DLL在Microsoft網站上找到。

>[!NOTE]
>
>不支援從在Linux中運行的應用程式伺服器訪問MicrosoftSQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支援包含多位元組字元的列名。

的 **NLS_NCHAR_CHARACTERSET** 和 **NLS_CHARECT** 需要正確配置參數，才能使資料庫以Unicode或ANSI工作。

Adobe Campaign使用預設Oracle編碼。 使用其他編碼可能會觸發相容性問題：在這種情況下，請與技術支援聯繫。

要瞭解編碼，請使用以下 **sqlplus** 命令：

```
SELECT * FROM nls_database_parameters ;
```

* 對於Unicode安裝，支援的編碼為：

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* 對於ANSI安裝（非unicode），僅支援以下編碼：

```
  NLS_CHARACTERSET WE8MSWIN1252
```

登錄到 **sqlplus**，使用Oracle用戶配置檔案：

```
su - oracle 
sqlplus 
[login] [password]
```

您還可以參考 [OracleLinux客戶端](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)。

## PostgresSQL {#postgressql}

我們建議您在安裝資料庫引擎時安裝UTF-8支援。 這樣，您將能夠建立Unicode資料庫。

**相關主題**

* [Adobe Campaign Classic表中的未登錄選項](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
