---
solution: Campaign Classic
product: campaign
title: SQL 資料管理
description: 進一步瞭解SQL資料管理工作流活動
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 3%

---


# SQL 資料管理{#sql-data-management}

**SQL資料管理**&#x200B;活動可讓您編寫自己的SQL指令碼以建立和填充工作表。

## 必要條件 {#prerequisites}

在設定活動之前，請確定已符合下列先決條件：

* 活動僅適用於遠程資料源。 因此，您的實例上必須安裝&#x200B;**[!UICONTROL FDA]**(Federated Data Access)軟體包。 [進一步瞭解](../../installation/using/about-fda.md)。
* 出站模式必須存在於資料庫中，並連結到FDA資料庫。 [進一步瞭解](../../configuration/using/about-schema-reference.md)。
* 執行工作流的運算子必須具有名為right的&#x200B;**[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]**。 [進一步瞭解](../../platform/using/access-management-named-rights.md)。

## 配置SQL資料管理活動{#configuring-the-sql-data-management-activity}

1. 指定活動&#x200B;**[!UICONTROL Label]**。
1. 選擇要使用的&#x200B;**[!UICONTROL External account]**，然後選擇連結到此外部帳戶的&#x200B;**[!UICONTROL Outbound schema]**。

   >[!CAUTION]
   >
   >出站方案已修正，無法編輯。

1. 添加SQL指令碼。

   >[!CAUTION]
   >
   >SQL指令碼編寫者有責任確保SQL指令碼正常工作，並確保其引用（欄位名稱等） 符合「出站」模式。

   如果要載入現有的SQL代碼，請選擇&#x200B;**[!UICONTROL The SQL script is contained in an entity stored in the database]**&#x200B;選項。 SQL指令碼必須建立並儲存在&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]**&#x200B;菜單中。

   否則，在專用區域鍵入或複製貼上SQL指令碼。

   ![](assets/sql_datamanagement.png)

   此活動可讓您在指令碼中使用下列變數：

   * **activity.tableName**:出站工作表的SQL名稱。
   * **task.incomingTransitionByName(『name』)。tableName**:要使用的傳入轉換所攜帶的工作表的SQL名稱（轉換由其名稱標識）。

      >[!NOTE]
      >
      >(&#39;name&#39;)值與轉場屬性的&#x200B;**[!UICONTROL Name]**&#x200B;欄位相對應。

1. 如果SQL指令碼已包含建立出站工作表的命令，請取消選擇&#x200B;**[!UICONTROL Automatically create work table]**&#x200B;選項。 否則，工作表將在工作流執行後自動建立。
1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;確認活動配置。

活動現在已設定。 它已準備好在工作流中執行。

>[!CAUTION]
>
>執行活動後，出站轉移記錄計數僅表示。 它可能隨SQL指令碼的複雜程度而變化。
>  
>如果活動重新啟動，則無論其執行狀態如何，都會從開始執行整個指令碼。

## SQL指令碼示例{#sql-script-samples}

>[!NOTE]
>
>本節中的指令碼示例應在PostgreSQL下執行。

以下指令碼可讓您建立工作表，並將資料插入此相同的工作表：

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

以下指令碼可讓您執行CTAS操作(CREATE TABLE AS SELECT)並建立工作表索引：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

以下指令碼可讓您合併兩個工作表：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

