---
product: campaign
title: 豐富資料
description: 瞭解有關「富集」工作流活動的詳細資訊
feature: Workflows, Enrichment Activity
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 豐富資料{#enriching-data}

![](../../assets/v7-only.svg)

## 關於豐富資料 {#about-enriching-data}

此使用案例詳細資訊 **[!UICONTROL Enrichment]** 目標工作流中的活動。 有關使用的詳細資訊 **[!UICONTROL Enrichment]** 活動，請參閱： [濃縮](enrichment.md)。

有關如何使用自定義日期豐富電子郵件傳遞的使用案例，請參見 [此部分](email-enrichment-with-custom-date-fields.md)。

通過網路應用向市場資料庫中的聯繫人發送參加比賽的邀請。 競爭結果將於2014年 **[!UICONTROL Competition results]** 的子菜單。 此表連結到聯繫人表(**[!UICONTROL Recipients]**)。 的 **[!UICONTROL Competition results]** 表包含以下欄位：

* 競爭名稱(@game)
* 試用號(@trial)
* 得分(@score)

![](assets/uc1_enrich_1.png)

在 **[!UICONTROL Recipients]** 表可以連結到中的幾行 **[!UICONTROL Competition results]** 的子菜單。 這兩個表之間的關係為1-n類型。 以下是收件人的結果日誌示例：

![](assets/uc1_enrich_2.png)

此使用案例的目的是，根據參加最新比賽的人的最高得分，將個性化的送貨發送給參加最新比賽的人。 得分最高的受獎者獲得第一獎，得分第二高的受獎者獲得安慰獎，其他人則收到祝他們下次好運的資訊。

要設定此用例，我們建立了以下目標工作流：

![](assets/uc1_enrich_3.png)

要建立工作流，請應用以下步驟：

1. 二 **[!UICONTROL Query]** 活動和 **[!UICONTROL Intersection]** 活動將添加到上次參加競爭的目標新訂戶。
1. 的 **[!UICONTROL Enrichment]** 活動使我們能夠添加儲存在 **[!UICONTROL Competition results]** 的子菜單。 的 **[!UICONTROL Score]** 「交付個性化」(Delivery Personalization)欄位將添加到工作流的工作表中。
1. 的 **[!UICONTROL Split]** 類型活動使我們能夠根據分數建立收件人子集。
1. 對於每個子集， **[!UICONTROL Delivery]** 類型活動即被添加。

## 步驟1:目標 {#step-1--targeting}

第一個查詢使我們能夠將過去六個月內添加到資料庫的收件人作為目標。

![](assets/uc1_enrich_4.png)

第二個查詢使我們能夠針對參加上次競爭的收件人。

![](assets/uc1_enrich_5.png)

安 **[!UICONTROL Intersection]** 然後，將類型活動添加到目標中，目標是在過去六個月內添加到資料庫的收件人以及參加上次競爭的人員。

## 步驟2:濃縮 {#step-2--enrichment}

在此示例中，我們要根據 **[!UICONTROL Score]** 儲存在 **[!UICONTROL Competition results]** 的子菜單。 此表與收件人表具有1-n類型關係。 的 **[!UICONTROL Enrichment]** 活動使我們能夠將連結到篩選維的表中的資料添加到工作流的工作表。

1. 在富集活動的編輯螢幕中，選擇 **[!UICONTROL Add data]**，則 **[!UICONTROL Data linked to the filtering dimension]** 按一下 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_6.png)

1. 然後選擇 **[!UICONTROL Data linked to the filtering dimension]** 選項 **[!UICONTROL Competition results]** 表格 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_7.png)

1. 輸入ID和標籤，然後選擇 **[!UICONTROL Limit the line count]** 的上界 **[!UICONTROL Data collected]** 的子菜單。 在 **[!UICONTROL Lines to retrieve]** 欄位中選擇「1」作為值。 對於每個收件人，富集活動將從 **[!UICONTROL Competition results]** 的下界。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_8.png)

1. 在此示例中，我們希望恢復受獎者的最高分，但僅是為上次比賽。 為此，請向 **[!UICONTROL Competition name]** 欄位，以排除與以前競爭相關的所有行。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_9.png)

1. 轉到 **[!UICONTROL Sort]** 並按一下 **[!UICONTROL Add]** 按鈕 **[!UICONTROL Score]** 的子菜單。 **[!UICONTROL descending]** 列，以對 **[!UICONTROL Score]** 按降序排列。 對於每個收件人，富集活動會添加一行，該行與上一場比賽的最高得分相匹配。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_10.png)

1. 在 **[!UICONTROL Data to add]** ，按兩下 **[!UICONTROL Score]** 的子菜單。 對於每個收件人，富集活動將僅添加 **[!UICONTROL Score]** 的子菜單。 按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/uc1_enrich_11.png)

按一下右鍵富集活動的入站轉換並選擇 **[!UICONTROL Display the target]**。 工作表包含以下資料：

![](assets/uc1_enrich_13.png)

連結的架構為：

![](assets/uc1_enrich_15.png)

在濃縮活動的出站轉移中續訂此操作。 我們可以看到，連結到收件人分數的資料已經添加。 已恢復每個收件人的最高分。

![](assets/uc1_enrich_12.png)

還豐富了匹配架構。

![](assets/uc1_enrich_14.png)

## 第3步：拆分和交付 {#step-3--split-and-delivery}

要根據收件人的分數對其進行排序， **[!UICONTROL Split]** 富集後會增加活動。

![](assets/uc1_enrich_18.png)

1. 第一個(**贏家**)子集已定義為包括得分最高的收件人。 為此，請定義記錄數的限制，對分數應用降序排序，並將記錄數限制為1。

   ![](assets/uc1_enrich_16.png)

1. 第二個(**第二名**)子集包括得分第二高的收件人。 配置與第一個子集的配置相同。

   ![](assets/uc1_enrich_17.png)

1. 第三個(**輸**)子集包含所有其他收件人。 轉到 **[!UICONTROL General]** 的子菜單。 **[!UICONTROL Generate complement]** 框，以未達到兩個最高分的所有收件者為目標。

   ![](assets/uc1_enrich_19.png)

1. 添加 **[!UICONTROL Delivery]** 為每個子集鍵入活動，為每個子集使用不同的傳遞模板。

   ![](assets/uc1_enrich_20.png)
