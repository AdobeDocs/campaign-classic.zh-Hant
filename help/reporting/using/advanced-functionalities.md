---
title: 進階功能
seo-title: 進階功能
description: 進階功能
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# 進階功能{#advanced-functionalities}

## 添加指令碼 {#adding-a-script}

### 指令碼活動 {#script-activity}

此活動使您能夠處理資料並輕鬆建立不啟用SQL語言的複雜查詢。

只需在指令碼視窗中輸入您的查詢即可。

此標 **[!UICONTROL Texts]** 簽可讓您定義文字字串。 然後可搭配下列語法使用： **$（識別碼）**。 有關使用文本的詳細資訊，請 [參閱添加頁眉和頁腳](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

>[!CAUTION]
>
>我們不建議使用JavaScript程式碼來建立匯整。

若要建立報表的歷史記錄，請新增下列行至JavaScript查詢，以儲存已封存的資料：

```
if( ctx.@_historyId.toString().length == 0 )
```

否則，將顯示當前資料。

### 外部指令碼 {#external-script}

可以使用將在伺服器和／或客戶端上執行的外部指令碼。 操作步驟：

1. 編輯報表屬性，然後按一下 **[!UICONTROL Scripts]**。
1. 按一下 **[!UICONTROL Add]** 並選擇要引用的指令碼。
1. 然後選擇執行模式。

   如果添加了多個指令碼，請使用工具欄的箭頭來定義其執行順序。

   ![](assets/reporting_custom_js.png)

## 呼叫另一份報告 {#calling-up-another-report}

### 跳轉活動 {#jump-activity}

跳轉就像沒有箭頭的轉場：它可讓您從一個活動移至另一個活動，或存取另一個報表。
