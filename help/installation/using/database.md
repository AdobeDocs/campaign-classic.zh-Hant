---
product: campaign
title: Campaign Classic資料庫建議
description: 資料庫建議
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 2%

---

# 資料庫{#database}



資料庫伺服器可在任何指定的作業系統上執行，無論應用程式伺服器使用的作業系統為何，只要它們之間有網路連線即可。

只要與Adobe Campaign不同元件的連線可用，資料庫伺服器的作業系統就並不重要。

同時檢查[資料庫存取層](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers)區段。

## Microsoft SQL Server {#microsoft-sql-server}

原生使用者端必須安裝在Adobe Campaign應用程式伺服器上。

您可以透過&#x200B;**SQL Server Native Client 11.0**&#x200B;底下的ODBC驅動程式組態面板，檢查伺服器上的原生使用者端。

必須存在下列存取DLL： **sqlncli11.dll**。

存取DLL可在Microsoft網站上找到。

>[!NOTE]
>
>不支援從在Linux中執行的應用程式伺服器存取Microsoft SQL Server。

## Oracle {#oracle}

>[!NOTE]
>
>不支援含有多位元組字元的欄名稱。

必須正確設定&#x200B;**NLS_NCHAR_CHARACTERSET**&#x200B;和&#x200B;**NLS_CHARACTERSET**&#x200B;引數，資料庫才能在Unicode或ANSI中運作。

Adobe Campaign使用預設的Oracle編碼。 使用其他編碼可能會觸發相容性問題：在這種情況下，請聯絡技術支援人員。

若要瞭解您的編碼方式，請使用下列&#x200B;**sqlplus**&#x200B;命令：

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

若要登入&#x200B;**sqlplus**，請使用Oracle的使用者設定檔：

```
su - oracle 
sqlplus 
[login] [password]
```

您也可以參考Linux中的[Oracle使用者端](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)。

## PostgresSQL {#postgressql}

建議您在安裝資料庫引擎時安裝UTF-8支援。 這樣您就可以建立Unicode資料庫。

**相關主題**

* [Adobe Campaign Classic資料表中未記錄的選項](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
