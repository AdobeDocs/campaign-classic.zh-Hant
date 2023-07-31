---
product: campaign
title: Campaign Classic資料庫建議
description: 資料庫建議
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 4%

---

# 資料庫{#database}



資料庫伺服器可在任何指定的作業系統上執行，無論應用程式伺服器使用的作業系統為何，只要它們之間有網路連線即可。

只要與Adobe Campaign不同元件的連線可用，資料庫伺服器的作業系統就並不重要。

另請檢查 [資料庫存取層](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) 區段。

## Microsoft SQL Server {#microsoft-sql-server}

原生使用者端必須安裝在Adobe Campaign應用程式伺服器上。

您可以透過ODBC驅動程式組態面板，在底下檢查伺服器上的原生使用者端 **SQL Server Native Client 11.0**.

下列存取DLL必須存在： **sqlncli11.dll**.

存取DLL可在Microsoft網站上找到。

>[!NOTE]
>
>不支援從在Linux中執行的應用程式伺服器存取Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支援含有多位元組字元的欄名稱。

此 **NLS_NCHAR_CHARACTERSET** 和 **NLS_CHARACTERSET** 必須正確設定引數，資料庫才能在Unicode或ANSI中運作。

Adobe Campaign使用預設的Oracle編碼。 使用其他編碼可能會觸發相容性問題：在這種情況下，請聯絡技術支援人員。

若要瞭解您的編碼，請使用以下內容 **sqlplus** 命令：

```
SELECT * FROM nls_database_parameters ;
```

* 對於Unicode安裝，支援的編碼為：

  ```
  NLS_NCHAR_CHARACTERSET         AL16UTF16
  NLS_CHARACTERSET         AL32UTF8
  ```

* 對於ANSI安裝（非Unicode），僅支援下列編碼：

```
  NLS_CHARACTERSET WE8MSWIN1252
```

登入 **sqlplus**，使用Oracle使用者設定檔：

```
su - oracle 
sqlplus 
[login] [password]
```

您也可以參閱 [Linux中的Oracle使用者端](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

建議您在安裝資料庫引擎時安裝UTF-8支援。 這樣您就可以建立Unicode資料庫。

**相關主題**

* [Adobe Campaign Classic表格中的取消記錄選項](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
