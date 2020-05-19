---
title: 豐富資料
seo-title: 豐富資料
description: 豐富資料
seo-description: null
page-status-flag: never-activated
uuid: 3f65a8a2-b3e1-4c4c-9653-b8a7c4d7557a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: f87da08f-68b9-4e2b-821f-b3ff20e390f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1aca6758bc787f91ae28d7d5add875edf04541e8
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---


# 豐富資料{#enriching-data}

## 關於豐富資料 {#about-enriching-data}

此使用案例詳細資訊可能會在定位 **[!UICONTROL Enrichment]** 工作流程中使用活動。 有關使用活動的詳 **[!UICONTROL Enrichment]** 細資訊，請參閱： [濃縮](../../workflow/using/enrichment.md)。

本節也提供如何以自訂日期豐富電子郵件傳送的使 [用案例](../../workflow/using/email-enrichment-with-custom-date-fields.md)。

行銷資料庫中的連絡人會收到邀請，以透過網路應用程式參與競賽。 比賽結果見表 **[!UICONTROL Competition results]** 格。 此表連結到聯繫人表(**[!UICONTROL Recipients]**)。 表格 **[!UICONTROL Competition results]** 包含下列欄位：

* 競爭名稱(@game)
* 試用版號碼(@trial)
* 分數(@score)

![](assets/uc1_enrich_1.png)

在表格中找到的 **[!UICONTROL Recipients]** 聯繫人可以連結到表格中的幾 **[!UICONTROL Competition results]** 行。 這兩個表之間的關係為1-n類型。 以下是收件者結果記錄的範例：

![](assets/uc1_enrich_2.png)

此使用案例的目的是根據參加最新競賽的人的最高分，將個人化的遞送寄送給他們。 得分最高的得獎者得第一名，得分第二名的得獎者得到安慰獎，其他所有人都得到一個資訊，希望他們下次能更好運。

若要設定此使用案例，我們建立了下列定位工作流程：

![](assets/uc1_enrich_3.png)

要建立工作流，請應用以下步驟：

1. 新增 **[!UICONTROL Query]** 兩個活動和 **[!UICONTROL Intersection]** 一個活動，以鎖定上次參加競賽的新訂閱者。
1. 此活 **[!UICONTROL Enrichment]** 動可讓我們新增儲存在表格中的 **[!UICONTROL Competition results]** 資料。 我 **[!UICONTROL Score]** 們的傳送個人化將會進行的欄位，會新增至工作流程的工作表。
1. 類型 **[!UICONTROL Split]** 活動可讓我們根據分數建立收件者子集。
1. 對於每個子集，都 **[!UICONTROL Delivery]** 會添加類型活動。

## 步驟1: 定位 {#step-1--targeting}

第一個查詢可讓我們定位在過去六個月內新增至資料庫的收件者。

![](assets/uc1_enrich_4.png)

第二個查詢可讓我們定位參加上次競賽的收件者。

![](assets/uc1_enrich_5.png)

然後 **[!UICONTROL Intersection]** 會新增一個類型活動，以鎖定在過去六個月內新增至資料庫的收件者，以及參加上次競爭的收件者。

## 步驟2: 濃縮 {#step-2--enrichment}

在此範例中，我們要根據表格中儲存的欄位， **[!UICONTROL Score]** 個人化傳送 **[!UICONTROL Competition results]** 內容。 此表與收件者表具有1-n類型關係。 此活 **[!UICONTROL Enrichment]** 動可讓我們將連結至篩選維度的表格資料新增至工作流程的工作表。

1. 在擴充活動的編輯畫面中，選取， **[!UICONTROL Add data]**&#x200B;然後按一 **[!UICONTROL Data linked to the filtering dimension]** 下滑鼠 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_6.png)

1. 然後選取 **[!UICONTROL Data linked to the filtering dimension]** 選項，選取表格 **[!UICONTROL Competition results]** 並按一下 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_7.png)

1. 輸入ID和標籤，然後在欄位 **[!UICONTROL Limit the line count]** 中選取選 **[!UICONTROL Data collected]** 項。 在字 **[!UICONTROL Lines to retrieve]** 段中，選擇&#39;1&#39;作為值。 對於每個收件者，擴充活動會將表格中的單 **[!UICONTROL Competition results]** 一行新增至工作流程的工作表。 按一下 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. 在此範例中，我們想要復原收件者的最高分數，但僅針對上一個競賽。 若要這麼做，請在欄位中新增篩選 **[!UICONTROL Competition name]** 器，以排除所有與先前比賽相關的行。 按一下 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. 移至畫面 **[!UICONTROL Sort]** 並按一下按 **[!UICONTROL Add]** 鈕，選取欄 **[!UICONTROL Score]** 位並核取欄中的方塊， **[!UICONTROL descending]** 以遞減順序排序 **[!UICONTROL Score]** 欄位項目。 對於每個收件者，擴充活動會新增一行，以符合上次遊戲的最高分數。 按一下 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. 在視窗 **[!UICONTROL Data to add]** 中，按兩下欄 **[!UICONTROL Score]** 位。 對於每個收件者，擴充活動只會新增欄 **[!UICONTROL Score]** 位。 按一下 **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

按一下右鍵富集活動的入站轉換並選擇 **[!UICONTROL Display the target]**。 工作表包含以下資料：

![](assets/uc1_enrich_13.png)

連結的架構是：

![](assets/uc1_enrich_15.png)

在富集活動的出站轉移時續訂此操作。 我們可以看到連結至收件者分數的資料已新增。 每個收件者的最高分已復原。

![](assets/uc1_enrich_12.png)

匹配模式也已豐富。

![](assets/uc1_enrich_14.png)

## 步驟3: 分割和傳送 {#step-3--split-and-delivery}

若要根據收件者的分數來排序，會在 **[!UICONTROL Split]** 富集後新增活動。

![](assets/uc1_enrich_18.png)

1. 已定義第&#x200B;**一個(Winner**)子集，以包含最高分數的收件者。 若要這麼做，請定義記錄數的限制、套用遞減排序至分數，並將記錄數限制為1。

   ![](assets/uc1_enrich_16.png)

1. 第二(**第二**)子集包括具有第二最高分數的接收者。 配置與第一個子集的配置相同。

   ![](assets/uc1_enrich_17.png)

1. 第三個(輸&#x200B;**家**)子集包含所有其他收件者。 前往標籤 **[!UICONTROL General]** 並核取方塊，以 **[!UICONTROL Generate complement]** 鎖定未達到最高分的所有收件者。

   ![](assets/uc1_enrich_19.png)

1. 為每個 **[!UICONTROL Delivery]** 子集新增類型活動，使用不同的傳送範本。

   ![](assets/uc1_enrich_20.png)

