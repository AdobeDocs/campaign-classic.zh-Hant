---
product: campaign
title: 豐富資料
description: 進一步瞭解擴充工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Enrichment Activity
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 豐富資料{#enriching-data}



## 關於擴充資料 {#about-enriching-data}

此使用案例詳細說明可能使用的 **[!UICONTROL Enrichment]** 定位工作流程中的活動。 有關使用的詳細資訊 **[!UICONTROL Enrichment]** 活動，請參閱： [擴充](enrichment.md).

有關如何使用自訂日期擴充電子郵件傳送的使用案例，請參見 [本節](email-enrichment-with-custom-date-fields.md).

行銷資料庫中的連絡人會透過網頁應用程式收到加入競爭的邀請。 競爭的結果可在以下網址中恢復： **[!UICONTROL Competition results]** 表格。 此表格連結至聯絡人表格(**[!UICONTROL Recipients]**)。 此 **[!UICONTROL Competition results]** 表格包含下列欄位：

* 競爭名稱(@game)
* 試用編號(@trial)
* 分數(@score)

![](assets/uc1_enrich_1.png)

在下列位置找到聯絡人： **[!UICONTROL Recipients]** 表格可連結至 **[!UICONTROL Competition results]** 表格。 這兩個表格之間的關係是1-n型別。 以下是收件者的結果記錄檔範例：

![](assets/uc1_enrich_2.png)

此使用案例的目的是根據參加最新競爭的人的最高得分，將個人化傳遞傳送給他們。 得分最高的收件者會獲得第一名，得分第二高的收件者會獲得安慰獎，而所有其他收件者都會收到訊息，祝他們下次好運。

為了設定此使用案例，我們建立了以下目標定位工作流程：

![](assets/uc1_enrich_3.png)

若要建立工作流程，請套用下列步驟：

1. 二 **[!UICONTROL Query]** 活動與一 **[!UICONTROL Intersection]** 新增活動，以定位上次進入競爭的新訂閱者。
1. 此 **[!UICONTROL Enrichment]** 活動可讓我們新增儲存在 **[!UICONTROL Competition results]** 表格。 此 **[!UICONTROL Score]** 將在其中進行傳遞個人化的欄位會新增至工作流程的工作表。
1. 此 **[!UICONTROL Split]** 型別活動可讓我們根據分數建立收件者子集。
1. 對於每個子集， **[!UICONTROL Delivery]** 型別活動已新增。

## 步驟1：鎖定目標 {#step-1--targeting}

第一個查詢可讓我們定位過去六個月內新增至資料庫的收件者。

![](assets/uc1_enrich_4.png)

第二個查詢可讓我們鎖定參加上次競爭的收件者。

![](assets/uc1_enrich_5.png)

一個 **[!UICONTROL Intersection]** 然後，會新增型別活動，以定位在過去六個月內新增到資料庫的收件者，以及進入上次競爭的收件者。

## 步驟2：擴充 {#step-2--enrichment}

在此範例中，我們想要根據以下範例來個人化傳送： **[!UICONTROL Score]** 儲存在中的欄位 **[!UICONTROL Competition results]** 表格。 此表格與收件者表格有1-n型別的關係。 此 **[!UICONTROL Enrichment]** 活動可讓我們將連結至篩選維度的表格資料，新增至工作流程的工作表。

1. 在擴充活動的編輯畫面中，選取 **[!UICONTROL Add data]**，則 **[!UICONTROL Data linked to the filtering dimension]** 並按一下 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. 然後選取 **[!UICONTROL Data linked to the filtering dimension]** 選項，選取 **[!UICONTROL Competition results]** 表格並按一下 **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. 輸入ID和標籤，然後選取 **[!UICONTROL Limit the line count]** 中的選項 **[!UICONTROL Data collected]** 欄位。 在 **[!UICONTROL Lines to retrieve]** 欄位中，選取&#39;1&#39;作為值。 對於每個收件者，擴充活動會從以下專案新增單一明細行： **[!UICONTROL Competition results]** 工作流程工作表格的表格。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_8.png)

1. 在此範例中，我們要復原收件者的最高分數，但僅限於最後的競爭。 若要這麼做，請將篩選器新增至 **[!UICONTROL Competition name]** 此欄位可排除與先前競爭相關的所有明細行。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_9.png)

1. 前往 **[!UICONTROL Sort]** 畫面並按一下 **[!UICONTROL Add]** 按鈕，選取 **[!UICONTROL Score]** 欄位並勾選 **[!UICONTROL descending]** 欄以排序以下專案： **[!UICONTROL Score]** 欄位降序。 對於每個收件者，擴充活動會新增符合上一個遊戲最高分數的行。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc1_enrich_10.png)

1. 在 **[!UICONTROL Data to add]** 視窗，按兩下 **[!UICONTROL Score]** 欄位。 對於每個收件者，擴充活動只會新增 **[!UICONTROL Score]** 欄位。 按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/uc1_enrich_11.png)

以滑鼠右鍵按一下擴充活動的入站轉變，然後選取 **[!UICONTROL Display the target]**. 工作表包含下列資料：

![](assets/uc1_enrich_13.png)

連結的結構描述是：

![](assets/uc1_enrich_15.png)

在擴充活動的出站轉變上續約此作業。 我們可以看到連結至收件者分數的資料已新增。 已復原每個收件者的最高分數。

![](assets/uc1_enrich_12.png)

相符的結構描述也已更加豐富。

![](assets/uc1_enrich_14.png)

## 步驟3：分割與傳送 {#step-3--split-and-delivery}

若要根據收件者的分數來排序收件者，請 **[!UICONTROL Split]** 活動會在擴充後新增。

![](assets/uc1_enrich_18.png)

1. 第一個(**獲勝者**)子集已定義為包含具有最高分數的收件者。 若要這麼做，請定義記錄數量的限制、對分數套用降序排序，並將記錄數量限製為1。

   ![](assets/uc1_enrich_16.png)

1. 第二個(**第二名**)子集包含具有第二高分數的收件者。 設定與第一個子集的設定相同。

   ![](assets/uc1_enrich_17.png)

1. 第三個(**失敗者**)子集包含所有其他收件者。 前往 **[!UICONTROL General]** 標籤並核取 **[!UICONTROL Generate complement]** 方塊來鎖定未達到兩個最高分的所有收件者。

   ![](assets/uc1_enrich_19.png)

1. 新增 **[!UICONTROL Delivery]** 為每個子集輸入活動，並為每個子集使用不同的傳遞範本。

   ![](assets/uc1_enrich_20.png)
