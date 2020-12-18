---
solution: Campaign Classic
product: campaign
title: 豐富資料
description: 進一步瞭解Enrichment工作流程活動
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---


# 擴充資料{#enriching-data}

## 關於豐富資料{#about-enriching-data}

此使用案例詳細資訊可能用於定位工作流程中的&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動。 有關使用&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動的詳細資訊，請參閱：[Enrichment](../../workflow/using/enrichment.md)。

[本節](../../workflow/using/email-enrichment-with-custom-date-fields.md)也提供如何以自訂日期豐富電子郵件傳送的使用案例。

行銷資料庫中的連絡人會收到邀請，以透過網路應用程式參與競賽。 比賽結果在&#x200B;**[!UICONTROL Competition results]**&#x200B;表中恢復。 此表連結至聯繫人表(**[!UICONTROL Recipients]**)。 **[!UICONTROL Competition results]**&#x200B;表格包含下列欄位：

* 競爭名稱(@game)
* 試用版號碼(@trial)
* 分數(@score)

![](assets/uc1_enrich_1.png)

在&#x200B;**[!UICONTROL Recipients]**&#x200B;表中找到的聯繫人可以連結到&#x200B;**[!UICONTROL Competition results]**&#x200B;表中的幾行。 這兩個表之間的關係為1-n類型。 以下是收件者結果記錄的範例：

![](assets/uc1_enrich_2.png)

此使用案例的目的是根據參加最新競賽的人的最高分，將個人化的遞送寄送給他們。 得分最高的得獎者得第一名，得分第二名的得獎者得到安慰獎，其他所有人都得到一個資訊，希望他們下次能更好運。

若要設定此使用案例，我們建立了下列定位工作流程：

![](assets/uc1_enrich_3.png)

要建立工作流，請應用以下步驟：

1. 將兩個&#x200B;**[!UICONTROL Query]**&#x200B;活動和一個&#x200B;**[!UICONTROL Intersection]**&#x200B;活動添加到上次參加競賽的目標新訂閱者。
1. **[!UICONTROL Enrichment]**&#x200B;活動使我們能夠添加儲存在&#x200B;**[!UICONTROL Competition results]**&#x200B;表中的資料。 我們的傳送個人化將進行的&#x200B;**[!UICONTROL Score]**&#x200B;欄位會新增至工作流程的工作表。
1. **[!UICONTROL Split]**&#x200B;類型活動使我們能夠根據分數建立收件人子集。
1. 對於每個子集，都添加&#x200B;**[!UICONTROL Delivery]**&#x200B;類型活動。

## 步驟1:定位{#step-1--targeting}

第一個查詢可讓我們定位在過去六個月內新增至資料庫的收件者。

![](assets/uc1_enrich_4.png)

第二個查詢可讓我們定位參加上次競賽的收件者。

![](assets/uc1_enrich_5.png)

然後會新增&#x200B;**[!UICONTROL Intersection]**&#x200B;類型活動，以鎖定在過去六個月內新增至資料庫的收件者，以及參加最後一次比賽的收件者。

## 步驟2:擴充{#step-2--enrichment}

在此範例中，我們想根據儲存在&#x200B;**[!UICONTROL Competition results]**&#x200B;表格中的&#x200B;**[!UICONTROL Score]**&#x200B;欄位來個人化傳送。 此表與收件者表具有1-n類型關係。 **[!UICONTROL Enrichment]**&#x200B;活動使我們能夠將連結到篩選維的表的資料添加到工作流的工作表中。

1. 在富集活動的編輯螢幕中，選擇&#x200B;**[!UICONTROL Add data]** ，然後選擇&#x200B;**[!UICONTROL Data linked to the filtering dimension]** ，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_6.png)

1. 然後選擇&#x200B;**[!UICONTROL Data linked to the filtering dimension]**&#x200B;選項，選擇&#x200B;**[!UICONTROL Competition results]**&#x200B;表，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_7.png)

1. 輸入ID和標籤，然後在&#x200B;**[!UICONTROL Data collected]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Limit the line count]**&#x200B;選項。 在&#x200B;**[!UICONTROL Lines to retrieve]**&#x200B;欄位中，選取&#39;1&#39;作為值。 對於每個收件者，擴充活動會將&#x200B;**[!UICONTROL Competition results]**&#x200B;表格中的單一行新增至工作流程的工作表。 按一下 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_8.png)

1. 在此範例中，我們想要復原收件者的最高分數，但僅針對上一個競賽。 若要這麼做，請在&#x200B;**[!UICONTROL Competition name]**&#x200B;欄位中新增篩選，排除所有與先前比賽相關的行。 按一下 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_9.png)

1. 轉到&#x200B;**[!UICONTROL Sort]**&#x200B;螢幕並按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，選擇&#x200B;**[!UICONTROL Score]**&#x200B;欄位並選中&#x200B;**[!UICONTROL descending]**&#x200B;列中的框，以降序對&#x200B;**[!UICONTROL Score]**&#x200B;欄位的項進行排序。 對於每個收件者，擴充活動會新增一行，以符合上次遊戲的最高分數。 按一下 **[!UICONTROL Next]**。

   ![](assets/uc1_enrich_10.png)

1. 在&#x200B;**[!UICONTROL Data to add]**&#x200B;窗口中，按兩下&#x200B;**[!UICONTROL Score]**&#x200B;欄位。 對於每個收件者，擴充活動將只新增&#x200B;**[!UICONTROL Score]**&#x200B;欄位。 按一下 **[!UICONTROL Finish]**。

   ![](assets/uc1_enrich_11.png)

按一下右鍵富集活動的入站轉換並選擇&#x200B;**[!UICONTROL Display the target]**。 工作表包含以下資料：

![](assets/uc1_enrich_13.png)

連結的架構是：

![](assets/uc1_enrich_15.png)

在富集活動的出站轉移時續訂此操作。 我們可以看到連結至收件者分數的資料已新增。 每個收件者的最高分已復原。

![](assets/uc1_enrich_12.png)

匹配模式也已豐富。

![](assets/uc1_enrich_14.png)

## 步驟3:分割和傳送{#step-3--split-and-delivery}

若要根據收件者的分數來排序，在擴充後會新增&#x200B;**[!UICONTROL Split]**&#x200B;活動。

![](assets/uc1_enrich_18.png)

1. 已定義第一(**Winner**)子集以包括具有最高分數的接收者。 若要這麼做，請定義記錄數的限制、套用遞減排序至分數，並將記錄數限制為1。

   ![](assets/uc1_enrich_16.png)

1. 第二（**第二位置**）子集包括具有第二最高分的接收者。 配置與第一個子集的配置相同。

   ![](assets/uc1_enrich_17.png)

1. 第三個(**losers**)子集包含所有其他收件者。 前往&#x200B;**[!UICONTROL General]**&#x200B;標籤並核取&#x200B;**[!UICONTROL Generate complement]**&#x200B;方塊，以鎖定未達到最高分的所有收件者。

   ![](assets/uc1_enrich_19.png)

1. 為每個子集添加&#x200B;**[!UICONTROL Delivery]**&#x200B;類型活動，使用不同的傳送模板。

   ![](assets/uc1_enrich_20.png)

