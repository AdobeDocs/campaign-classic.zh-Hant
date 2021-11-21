---
product: campaign
title: SQL 資料管理
description: 了解有關SQL資料管理工作流活動的更多資訊
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# SQL 資料管理{#sql-data-management}

![](../../assets/common.svg)

此 **SQL資料管理** 活動可讓您編寫自己的SQL指令碼，以建立和填入工作表。

## 先決條件 {#prerequisites}

設定活動之前，請確定已符合下列必要條件：

* 活動僅適用於遠端資料來源。 此 **[!UICONTROL FDA]** 因此，您的執行個體必須安裝（同盟資料存取）套件。 [深入瞭解](../../installation/using/about-fda.md)。

   如需詳細資訊，請視您的Campaign版本而定，參閱下列區段：

   ![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文件](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[  Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html)

* 輸出結構必須存在於資料庫中且連結至FDA資料庫。
* 執行工作流程的運算子必須具有 **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** 名字正確。 [深入瞭解](../../platform/using/access-management-named-rights.md)。

## 配置SQL資料管理活動 {#configuring-the-sql-data-management-activity}

1. 指定活動 **[!UICONTROL Label]**.
1. 選取 **[!UICONTROL External account]** 若要使用，請選取 **[!UICONTROL Outbound schema]** 連結至此外部帳戶。

   >[!CAUTION]
   >
   >已修正「傳出」結構，無法編輯。

1. 添加SQL指令碼。

   >[!CAUTION]
   >
   >SQL指令碼編寫器有責任確保SQL指令碼正常工作，並確保其引用（欄位名稱等） 符合「傳出」結構。

   如果要載入現有的SQL代碼，請選擇 **[!UICONTROL The SQL script is contained in an entity stored in the database]** 選項。 SQL指令碼必須建立並儲存在 **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** 功能表。

   否則，在專用區域中鍵入或複製貼上SQL指令碼。

   ![](assets/sql_datamanagement.png)

   活動可讓您在指令碼中使用下列變數：

   * **activity.tableName**:出站工作表的SQL名稱。
   * **task.incomingTransitionByName(&#39;name&#39;)。tableName**:要使用的傳入轉變所攜帶的工作表的SQL名稱（轉變由其名稱標識）。

      >[!NOTE]
      >
      >(&#39;name&#39;)值對應至 **[!UICONTROL Name]** 欄位。

1. 如果SQL指令碼已包含建立出站工作表的命令，請取消選擇 **[!UICONTROL Automatically create work table]** 選項。 否則，一旦工作流執行，就會自動建立工作表。
1. 按一下 **[!UICONTROL Ok]** 確認活動設定。

活動現在已設定。 它已準備好在工作流程中執行。

>[!CAUTION]
>
>一旦活動執行後，出站轉變記錄計數僅表示性。 它可能因SQL指令碼的複雜程度而有所不同。
>  
>如果活動重新啟動，則會從其開頭執行整個指令碼，而不論其執行狀態為何。

## SQL指令碼示例 {#sql-script-samples}

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
