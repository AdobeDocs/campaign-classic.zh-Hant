---
product: campaign
title: SQL 資料管理
description: 瞭解有關SQL資料管理工作流活動的詳細資訊
feature: Workflows
exl-id: cada78cb-658f-4b9e-8136-31c17cb1d82f
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# SQL 資料管理{#sql-data-management}

![](../../assets/common.svg)

的 **SQL資料管理** 活動，您可以編寫自己的SQL指令碼來建立和填充工作表。

## 必要條件 {#prerequisites}

在配置活動之前，請確保滿足以下先決條件：

* 該活動僅適用於遠程資料源。 的 **[!UICONTROL FDA]** 因此，必須在實例上安裝（聯合資料存取）軟體包。 [了解更多資訊](../../installation/using/about-fda.md)。

   有關此內容的詳細資訊，請參閱以下各節：

   ![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文件](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[  Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html)

* 出站模式必須存在於資料庫中，並且必須連結到FDA資料庫。
* 執行工作流的運算子必須具有 **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** 名字正確。 [了解更多資訊](../../platform/using/access-management-named-rights.md)。

## 配置SQL資料管理活動 {#configuring-the-sql-data-management-activity}

1. 指定活動 **[!UICONTROL Label]**。
1. 選擇 **[!UICONTROL External account]** ，然後選擇 **[!UICONTROL Outbound schema]** 連結到此外部帳戶。

   >[!CAUTION]
   >
   >出站架構已修復，無法編輯。

1. 添加SQL指令碼。

   >[!CAUTION]
   >
   >SQL指令碼編寫器有責任確保SQL指令碼正常工作，並確保其引用（欄位名稱等） 符合出站架構。

   如果要載入現有SQL代碼，請選擇 **[!UICONTROL The SQL script is contained in an entity stored in the database]** 的雙曲餘切值。 必須建立SQL指令碼並將其儲存在 **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** 的子菜單。

   否則，在專用區域中鍵入或複製貼上SQL指令碼。

   ![](assets/sql_datamanagement.png)

   該活動允許您在指令碼中使用以下變數：

   * **activity.tableName**:出站工作表的SQL名稱。
   * **task.incomingTransitionByName(&#39;name&#39;)。tableName**:傳入轉換要使用的工作表的SQL名稱（轉換由其名稱標識）。

      >[!NOTE]
      >
      >(&#39;name&#39;)值與 **[!UICONTROL Name]** 的子菜單。

1. 如果SQL指令碼已包含建立出站工作表的命令，請取消選擇 **[!UICONTROL Automatically create work table]** 的雙曲餘切值。 否則，一旦工作流執行，將自動建立工作表。
1. 按一下 **[!UICONTROL Ok]** 確認活動配置。

現在已配置活動。 它已準備好在工作流中執行。

>[!CAUTION]
>
>一旦執行了活動，出站轉移記錄計數僅指示性。 它可能因SQL指令碼的複雜性級別而異。
>  
>如果重新啟動活動，則無論整個指令碼的執行狀態如何，都會從它的開頭執行。

## SQL指令碼示例 {#sql-script-samples}

>[!NOTE]
>
>本節中的指令碼示例應在PostgreSQL下執行。

下面的指令碼允許您建立工作表並將資料插入到同一工作表中：

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

下面的指令碼允許您執行CTAS操作(CREATE TABLE AS SELECT)並建立工作表索引：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

下面的指令碼允許您合併兩個工作表：

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```
