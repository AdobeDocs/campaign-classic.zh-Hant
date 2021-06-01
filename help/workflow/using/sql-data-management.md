---
product: campaign
title: SQL 資料管理
description: 了解有關SQL資料管理工作流活動的更多資訊
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 3%

---

# SQL 資料管理{#sql-data-management}

**SQL資料管理**&#x200B;活動允許您編寫自己的SQL指令碼以建立和填充工作表。

## 先決條件 {#prerequisites}

設定活動之前，請確定已符合下列必要條件：

* 活動僅適用於遠端資料來源。 因此，您的執行個體上必須安裝&#x200B;**[!UICONTROL FDA]**（同盟資料存取）套件。 [瞭解更多](../../installation/using/about-fda.md)。
* 輸出結構必須存在於資料庫中且連結至FDA資料庫。 [瞭解更多](../../configuration/using/about-schema-reference.md)。
* 執行工作流程的運算子必須具有名為&#x200B;**[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]**&#x200B;的權限。 [瞭解更多](../../platform/using/access-management-named-rights.md)。

## 配置SQL資料管理活動{#configuring-the-sql-data-management-activity}

1. 指定活動&#x200B;**[!UICONTROL Label]**。
1. 選取要使用的&#x200B;**[!UICONTROL External account]**，然後選取連結至此外部帳戶的&#x200B;**[!UICONTROL Outbound schema]**。

   >[!CAUTION]
   >
   >已修正「傳出」結構，無法編輯。

1. 添加SQL指令碼。

   >[!CAUTION]
   >
   >SQL指令碼編寫器有責任確保SQL指令碼正常工作，並確保其引用（欄位名稱等） 符合「傳出」結構。

   如果要載入現有SQL代碼，請選擇&#x200B;**[!UICONTROL The SQL script is contained in an entity stored in the database]**&#x200B;選項。 必須在&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]**&#x200B;菜單中建立並儲存SQL指令碼。

   否則，在專用區域中鍵入或複製貼上SQL指令碼。

   ![](assets/sql_datamanagement.png)

   活動可讓您在指令碼中使用下列變數：

   * **activity.tableName**:出站工作表的SQL名稱。
   * **task.incomingTransitionByName(&#39;name&#39;)。tableName**:要使用的傳入轉變所攜帶的工作表的SQL名稱（轉變由其名稱標識）。

      >[!NOTE]
      >
      >(&#39;name&#39;)值對應於轉變屬性的&#x200B;**[!UICONTROL Name]**&#x200B;欄位。

1. 如果SQL指令碼已包含建立出站工作表的命令，請取消選擇&#x200B;**[!UICONTROL Automatically create work table]**&#x200B;選項。 否則，一旦工作流執行，就會自動建立工作表。
1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以確認活動配置。

活動現在已設定。 它已準備好在工作流程中執行。

>[!CAUTION]
>
>一旦活動執行後，出站轉變記錄計數僅表示性。 它可能因SQL指令碼的複雜程度而有所不同。
>  
>如果活動重新啟動，則會從其開頭執行整個指令碼，而不論其執行狀態為何。

## SQL指令碼示例{#sql-script-samples}

>[!NOTE]
>
>本節中的指令碼示例應在PostgreSQL下執行。

下面的指令碼允許您建立工作表並將資料插入到該工作表中：

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

以下指令碼允許您執行CTAS操作(CREATE TABLE AS SELECT)和建立工作表索引：

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
