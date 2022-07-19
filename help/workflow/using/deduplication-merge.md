---
title: 使用重複資料消除活動的合併功能
description: 瞭解如何使用重複資料消除活動的合併功能
feature: Workflows, Data Management
exl-id: a6b10585-7bf9-4fef-b886-db081b6d3acc
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 7%

---

# 使用重複資料消除活動的合併功能 {#deduplication-merge}

![](../../assets/v7-only.svg)

## 關於此使用實例 {#about-this-use-case}

此用例說明如何使用 **[!UICONTROL Merge]** 功能 **[!UICONTROL Deduplication]** 的子菜單。

有關此功能的詳細資訊，請參閱 [此部分](deduplication.md#merging-fields-into-single-record)。

的 **[!UICONTROL Deduplication]** 活動用於從資料集中刪除重複行。 在此使用情形中，下面顯示的資料將基於「電子郵件」欄位進行複製。

| 上次修改日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 羅伯特 | 蒂斯納 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鮑比 | 蒂斯納 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | 鮑勃 |  | bob@mycompany.com |  | 888-888-8888 |

使用重複資料消除活動 **[!UICONTROL Merge]** 方案性，您可以為重複資料消除配置一組規則，以定義一組要合併到單個結果資料記錄中的欄位。 例如，對於一組重複的記錄，您可以選擇保留最舊的電話號碼或最近的名稱。

## 激活合併功能 {#activating-merge}


要啟用合併功能，您首先需要配置 **[!UICONTROL Deduplication]** 的子菜單。 要執行此操作，請依照下列步驟執行：

1. 開啟活動，然後按一下 **[編輯配置]** 的子菜單。

1. 選擇要用於重複資料消除的協調欄位，然後按一下 **[!UICONTROL Next]**。 在本示例中，我們要根據電子郵件欄位進行重複資料消除。

   ![](assets/uc_merge_edit.png)

1. 按一下 **[!UICONTROL Advanced parameters]** 連結，然後激活 **[!UICONTROL Merge records]** 和 **[!UICONTROL Use several record merging criteria]** 頁籤

   ![](assets/uc_merge_advanced_parameters.png)

1. 的 **[!UICONTROL Merge]** 頁籤 **[!UICONTROL Deduplication]** 配置螢幕。 我們將使用此頁籤指定執行重複資料消除時要合併的資料。

## 配置要合併的欄位 {#configuring-rules}

以下是我們希望將資料合併到單個記錄中的規則：

* 保留最新名稱（名字和姓氏欄位）,
* 留下最新的手機，
* 保留最舊的電話號碼，
* 組中的所有欄位必須為非NULL才能符合最終記錄的條件。

要配置這些規則，請執行以下步驟：

1. 開啟 **[!UICONTROL Merge]** ，然後按一下 **[!UICONTROL Add]** 按鈕

   ![](assets/uc_merge_add.png)

1. 指定要合併的欄位組的標識符和標籤。

   ![](assets/uc_merge_identifier.png)

1. 指明選擇要考慮的記錄的條件。

   ![](assets/uc_merge_filter.png)

1. 在上次修改日期排序以選擇最新名稱。

   ![](assets/uc_merge_sort.png)

1. 選擇要合併的欄位。 在此示例中，我們要保留名字和姓氏欄位。

   ![](assets/uc_merge_keep.png)

1. 這些欄位將添加到要合併的資料集中，並且新元素將添加到工作流架構中。

   重複這些步驟以配置行動電話和電話欄位。

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## 結果 {#results}

在配置這些規則後，將在 **[!UICONTROL Deduplication]** 的子菜單。

| 修改日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 羅伯特 | 蒂斯納 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鮑比 | 蒂斯納 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | 鮑勃 |  | bob@mycompany.com |  | 888-888-8888 |

根據先前配置的規則，將結果從三個記錄中合併。 通過比較，得出使用最近的姓名和手機以及原始電話號碼。

| 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
|------------|-----------|-------|--------------|------|
| 鮑比 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> 請注意，已合併的名稱是「Bobby」，因為我們配置了由名稱和最後一個欄位組成的「Name」規則。
>
>因此，「Bob」（最近的名）無法被考慮，因為其關聯的姓氏欄位為空。 最近的名字和姓氏組合在最後記錄中合併。
