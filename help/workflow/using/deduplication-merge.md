---
title: 使用重複資料刪除活動的合併功能
description: 了解如何使用重複資料刪除活動的合併功能
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
exl-id: a6b10585-7bf9-4fef-b886-db081b6d3acc
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 5%

---

# 使用重複資料刪除活動的合併功能 {#deduplication-merge}

![](../../assets/common.svg)

## 關於此使用實例 {#about-this-use-case}

此使用案例說明如何在&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動中使用&#x200B;**[!UICONTROL Merge]**&#x200B;功能。

有關此功能的詳細資訊，請參閱[此部分](deduplication.md#merging-fields-into-single-record)。

**[!UICONTROL Deduplication]**&#x200B;活動用於從資料集中刪除重複行。 在此使用案例中，下方顯示的資料會根據「電子郵件」欄位重複。

| 上次修改日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 羅伯特 | 蒂斯納 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鮑比 | 蒂斯納 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

利用重複資料刪除活動的&#x200B;**[!UICONTROL Merge]**&#x200B;功能，您可以為重複資料刪除配置一組規則，以定義一組要合併到單個結果資料記錄中的欄位。 例如，使用一組重複記錄時，您可以選擇保留最舊的電話號碼或最新名稱。

## 啟用合併功能 {#activating-merge}


若要啟用合併功能，您必須先設定&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動。 要執行此操作，請依照下列步驟執行：

1. 開啟活動，然後按一下&#x200B;**[Edit configuration]**&#x200B;連結。

1. 選取要用於重複資料刪除的調解欄位，然後按一下&#x200B;**[!UICONTROL Next]**。 在此範例中，我們想根據電子郵件欄位去重複化。

   ![](assets/uc_merge_edit.png)

1. 按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結，然後啟動&#x200B;**[!UICONTROL Merge records]**&#x200B;和&#x200B;**[!UICONTROL Use several record merging criteria]**&#x200B;選項。

   ![](assets/uc_merge_advanced_parameters.png)

1. 將&#x200B;**[!UICONTROL Merge]**&#x200B;標籤添加到&#x200B;**[!UICONTROL Deduplication]**&#x200B;配置螢幕。 我們將使用此索引標籤來指定執行重複資料刪除時要合併的資料。

## 設定要合併的欄位 {#configuring-rules}

以下是我們要用來將資料合併至單一記錄的規則：

* 保留最近的名稱（名字和姓氏欄位）,
* 留著最新的手機，
* 保留最舊的電話號碼，
* 組中的所有欄位必須為非空值，才能符合最終記錄的資格。

若要設定這些規則，請遵循下列步驟：

1. 開啟&#x200B;**[!UICONTROL Merge]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕。

   ![](assets/uc_merge_add.png)

1. 指定要合併的欄位群組的識別碼和標籤。

   ![](assets/uc_merge_identifier.png)

1. 指明選擇要考慮的記錄的條件。

   ![](assets/uc_merge_filter.png)

1. 按上次修改日期排序，以選取最近的名稱。

   ![](assets/uc_merge_sort.png)

1. 選擇要合併的欄位。 在此範例中，我們想保留名字和姓氏欄位。

   ![](assets/uc_merge_keep.png)

1. 欄位會新增至要合併的資料集，而新元素會新增至工作流程架構。

   重複這些步驟以配置行動電話和電話欄位。

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## 結果 {#results}

設定這些規則後，會在&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動結束時收到下列資料。

| 修改日期 | 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 羅伯特 | 蒂斯納 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鮑比 | 蒂斯納 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

根據先前設定的規則，從三個記錄中合併結果。 通過對比，得出使用最新名稱和手機以及原電話號碼的結論。

| 名字 | 姓氏 | 電子郵件 | 行動電話 | 電話 |
|------------|-----------|-------|--------------|------|
| 鮑比 | 蒂斯納 | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> 請注意，已合併的名字是「Bobby」，因為我們已設定由名字和姓氏欄位組成的「Name」規則。
>
>因此，無法考慮&quot;Bob&quot;（最近的名字），因為其相關聯的姓氏欄位為空。 最近的名字和姓氏組合合併到最後記錄。
