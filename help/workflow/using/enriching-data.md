---
product: campaign
title: 豐富資料
description: 深入了解擴充工作流程活動
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 豐富資料{#enriching-data}

![](../../assets/common.svg)

## 關於擴充資料 {#about-enriching-data}

此使用案例詳細說明的可能用途 **[!UICONTROL Enrichment]** 目標工作流程中的活動。 有關使用的詳細資訊 **[!UICONTROL Enrichment]** 活動，請參閱： [擴充](enrichment.md).

有關如何使用自訂日期豐富電子郵件傳送的使用案例，請參閱 [本節](email-enrichment-with-custom-date-fields.md).

通過Web應用程式向行銷資料庫中的聯繫人發送參加競爭的邀請。 競爭結果於 **[!UICONTROL Competition results]** 表格。 此表已連結到聯繫表(**[!UICONTROL Recipients]**)。 此 **[!UICONTROL Competition results]** 表格包含下列欄位：

* 競爭名稱(@game)
* 試用號(@trial)
* 分數(@score)

![](assets/uc1_enrich_1.png)

在 **[!UICONTROL Recipients]** 表格可連結至 **[!UICONTROL Competition results]** 表格。 這兩個表之間的關係為1-n類型。 以下是收件者的結果記錄範例：

![](assets/uc1_enrich_2.png)

此使用案例的用途是根據參與最新競爭的人員的最高分數，將個人化傳遞傳送給他們。 得分最高的受獎者得第一名，得分第二名的受獎者得到安慰獎，其他所有人都會收到一條資訊，希望他們下次能更好運。

為了設定此使用案例，我們建立了下列目標工作流程：

![](assets/uc1_enrich_3.png)

要建立工作流，請應用以下步驟：

1. 二 **[!UICONTROL Query]** 活動與一個 **[!UICONTROL Intersection]** 活動會新增至上次競爭的target新訂閱者。
1. 此 **[!UICONTROL Enrichment]** 活動可讓我們新增儲存在 **[!UICONTROL Competition results]** 表格。 此 **[!UICONTROL Score]** 我們的傳送個人化將進行的欄位會新增至工作流程的工作表。
1. 此 **[!UICONTROL Split]** 類型活動可讓我們根據分數建立收件者子集。
1. 對於每個子集， **[!UICONTROL Delivery]** 已新增類型活動。

## 步驟1:定位 {#step-1--targeting}

第一個查詢可讓我們鎖定過去6個月內新增至資料庫的收件者。

![](assets/uc1_enrich_4.png)

第二個查詢可讓我們鎖定參加上次競爭的收件者。

![](assets/uc1_enrich_5.png)

安 **[!UICONTROL Intersection]** 然後會新增「類型活動」，以定位在過去6個月內新增至資料庫的收件者，以及加入上次競爭的收件者。

## 步驟2:擴充 {#step-2--enrichment}

在此範例中，我們想要根據 **[!UICONTROL Score]** 儲存在 **[!UICONTROL Competition results]** 表格。 此表與收件者表具有1-n類型關係。 此 **[!UICONTROL Enrichment]** 活動可讓我們將資料從連結至篩選維度的表格新增至工作流程的工作表格。

1. 在擴充活動的編輯畫面中，選取 **[!UICONTROL Add data]**，然後 **[!UICONTROL Data linked to the filtering dimension]** 按一下 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. 然後選取 **[!UICONTROL Data linked to the filtering dimension]** 選項，選擇 **[!UICONTROL Competition results]** 表格，按一下 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. 輸入ID和標籤，然後選取 **[!UICONTROL Limit the line count]** 選項 **[!UICONTROL Data collected]** 欄位。 在 **[!UICONTROL Lines to retrieve]** 欄位中，選擇「1」作為值。 對於每個收件者，擴充活動會從 **[!UICONTROL Competition results]** 表格顯示在工作流的工作表中。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_8.png)

1. 在此範例中，我們想要復原收件者的最高分數，但僅針對上次競爭。 若要這麼做，請新增篩選器至 **[!UICONTROL Competition name]** 欄位來排除與先前比賽相關的所有行。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_9.png)

1. 前往 **[!UICONTROL Sort]** 畫面，然後按一下 **[!UICONTROL Add]** 按鈕，選擇 **[!UICONTROL Score]** 欄位中，並核取 **[!UICONTROL descending]** 欄來排序項目 **[!UICONTROL Score]** 欄位。 對於每個收件者，擴充活動會新增一行，以符合上次遊戲的最高分數。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_10.png)

1. 在 **[!UICONTROL Data to add]** 按兩下 **[!UICONTROL Score]** 欄位。 對於每個收件者，擴充活動只會新增 **[!UICONTROL Score]** 欄位。 按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/uc1_enrich_11.png)

以滑鼠右鍵按一下擴充活動的入站轉變，然後選取 **[!UICONTROL Display the target]**. 工作表包含以下資料：

![](assets/uc1_enrich_13.png)

連結的架構為：

![](assets/uc1_enrich_15.png)

在擴充活動的出站轉變上更新此操作。 我們可以看到已新增連結至收件者分數的資料。 已恢復每個收件者的最高分數。

![](assets/uc1_enrich_12.png)

也已擴充相符的結構。

![](assets/uc1_enrich_14.png)

## 步驟3:分割和傳送 {#step-3--split-and-delivery}

若要根據收件者的分數來排序，請 **[!UICONTROL Split]** 擴充後會新增活動。

![](assets/uc1_enrich_18.png)

1. 第一個(**獲勝者**)子集合，以包含分數最高的收件者。 要執行此操作，請定義記錄數限制、對分數套用降序排序，並將記錄數限制為1。

   ![](assets/uc1_enrich_16.png)

1. 第二個(**第二名**)子集包含分數第二高的收件者。 設定與第一個子集的相同。

   ![](assets/uc1_enrich_17.png)

1. 第三個(**輸家**)子集包含所有其他收件者。 前往 **[!UICONTROL General]** 頁簽，並檢查 **[!UICONTROL Generate complement]** 方塊來定位未達到兩個最高分數的所有收件者。

   ![](assets/uc1_enrich_19.png)

1. 新增 **[!UICONTROL Delivery]** 為每個子集鍵入活動，使用每個子集的不同傳送模板。

   ![](assets/uc1_enrich_20.png)
