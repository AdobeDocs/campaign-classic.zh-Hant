---
product: campaign
title: 跨頻道傳遞工作流程
description: 進一步瞭解跨頻道傳遞工作流程
feature: Workflows, Channels Activity
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 3%

---

# 跨頻道傳遞工作流程{#cross-channel-delivery-workflow}



此使用案例提供的範例涉及跨通道傳送工作流程。 跨通道傳遞的一般概念在[本節](cross-channel-deliveries.md)中呈現。

目標是將對象從資料庫的收件者細分為不同的群組，以便向群組傳送電子郵件並向其他群組傳送簡訊。

此使用案例的主要實作步驟如下：

1. 建立&#x200B;**[!UICONTROL Query]**&#x200B;活動以鎖定您的對象。
1. 正在建立包含優惠方案連結的&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動。
1. 使用&#x200B;**[!UICONTROL Split]**&#x200B;活動來：

   * 傳送另一封電子郵件給未開啟第一封電子郵件的收件者。
   * 傳送SMS給已開啟電子郵件但未按一下選件連結的收件者。
   * 將開啟電子郵件並按一下連結的收件者新增至資料庫。

![](assets/wkf_cross-channel_7.png)

## 步驟1：鎖定對象 {#step-1--targeting-the-audience}

若要定義您的目標，請建立查詢以識別收件者。

1. 建立行銷活動。 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在行銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;索引標籤中，新增&#x200B;**查詢**&#x200B;活動至您的工作流程。 有關使用此活動的詳細資訊，請參閱[本區段](query.md)。
1. 定義將接收您傳遞的收件者。 例如，選取「金級」成員作為目標維度。
1. 新增篩選條件至您的查詢。 在此範例中，選取擁有電子郵件地址和行動電話號碼的收件者。

   ![](assets/wkf_cross-channel_3.png)

1. 儲存您的變更。

## 步驟2：建立包含優惠方案的電子郵件 {#step-2--creating-an-email-including-an-offer}

1. 建立&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動，並在工作流程中連按兩下以進行編輯。 如需建立電子郵件的詳細資訊，請參閱[本節](../../delivery/using/about-email-channel.md)。
1. 設計訊息並將包含優惠方案的連結插入內容中。

   ![](assets/wkf_cross-channel_1.png)

   如需將優惠方案整合至訊息內文的詳細資訊，請參閱[本節](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine)。

1. 儲存您的變更。
1. 用滑鼠右鍵按一下&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動以開啟。
1. 選取&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項以復原母體及追蹤記錄。

   ![](assets/wkf_cross-channel_2.png)

   這可讓您使用此資訊，根據收件者在收到第一封電子郵件時的行為來傳送另一個傳遞。

1. 新增&#x200B;**[!UICONTROL Wait]**&#x200B;活動，讓收件者有幾天的時間開啟電子郵件。

   ![](assets/wkf_cross-channel_4.png)

## 步驟3：將產生的對象分段 {#step-3--segmenting-the-resulting-audience}

在識別目標並建立第一個傳遞後，您需要使用篩選條件將目標細分為不同的母體。

1. 將&#x200B;**分割**&#x200B;活動新增至工作流程並加以開啟。 有關使用此活動的詳細資訊，請參閱[本區段](split.md)。
1. 從查詢上游計算的母體建立三個區段。

   ![](assets/wkf_cross-channel_6.png)

1. 針對第一個子集，選取&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**&#x200B;選項並按一下&#x200B;**[!UICONTROL Edit]**。

   ![](assets/wkf_cross-channel_8.png)

1. 選取&#x200B;**[!UICONTROL Recipients of a delivery]**&#x200B;作為限制篩選器，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/wkf_cross-channel_9.png)

1. 在篩選設定中，從&#x200B;**[!UICONTROL Behavior]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Recipients who have not opened or clicked (email)]**，然後從傳遞清單中選取包含您要傳送之優惠方案的電子郵件。 按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/wkf_cross-channel_10.png)

1. 以類似方式繼續第二個子集，並從&#x200B;**[!UICONTROL Behavior]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Recipients who have not clicked (email)]**。

   ![](assets/wkf_cross-channel_11.png)

1. 對於第三個子集，在選取&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**&#x200B;並按一下&#x200B;**[!UICONTROL Edit]**&#x200B;後，選取&#x200B;**[!UICONTROL Use a specific filtering dimension]**&#x200B;選項。
1. 從&#x200B;**[!UICONTROL Filtering dimension]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Recipient tracking log]**，從&#x200B;**[!UICONTROL List of restriction filters]**&#x200B;反白顯示&#x200B;**[!UICONTROL Filtering conditions]**，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/wkf_cross-channel_12.png)

1. 依下列方式選取篩選條件：

   ![](assets/wkf_cross-channel_13.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以儲存變更。

## 步驟4：完成工作流程 {#step-4--finalizing-the-workflow}

1. 在從&#x200B;**[!UICONTROL Split]**&#x200B;活動產生的三個子集之後，將相關活動新增到您的工作流程中：

   * 新增&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動以傳送提醒電子郵件至第一個子集。
   * 新增&#x200B;**[!UICONTROL Mobile delivery]**&#x200B;活動以傳送SMS訊息至第二個子集。
   * 新增&#x200B;**[!UICONTROL List update]**&#x200B;活動以將對應的收件者新增至資料庫。

1. 在工作流程中按兩下傳送活動以進行編輯。 如需建立電子郵件和簡訊的詳細資訊，請參閱[電子郵件頻道](../../delivery/using/about-email-channel.md)和[簡訊頻道](../../delivery/using/sms-channel.md)。
1. 連按兩下&#x200B;**[!UICONTROL List update]**&#x200B;活動並選取&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項。

   然後，您可以將產生的收件者從Adobe Campaign匯出至Adobe Experience Cloud。 例如，您可以將&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活動新增至工作流程，以在Adobe Target中使用對象。 如需詳細資訊，請參閱[匯出對象](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience)。

1. 按一下動作列中的&#x200B;**開始**&#x200B;按鈕以執行工作流程。

**查詢**&#x200B;活動所定位的母體將會分段，以根據收件者的行為接收電子郵件或SMS傳遞。 剩餘母體將使用&#x200B;**[!UICONTROL List update]**&#x200B;活動新增至資料庫。
