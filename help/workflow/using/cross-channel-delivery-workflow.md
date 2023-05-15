---
product: campaign
title: 跨頻道傳遞工作流程
description: 進一步了解跨通道傳遞工作流程
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---

# 跨頻道傳遞工作流程{#cross-channel-delivery-workflow}



此使用案例提供跨通道傳送工作流程的範例。 跨通道傳送的一般概念於 [本節](cross-channel-deliveries.md).

目標是將受眾從資料庫的收件者細分為不同的群組，以便傳送電子郵件至群組，並傳送簡訊至其他群組。

此使用案例的主要實施步驟如下：

1. 建立 **[!UICONTROL Query]** 鎖定對象的活動。
1. 建立 **[!UICONTROL Email delivery]** 包含選件連結的活動。
1. 使用 **[!UICONTROL Split]** 活動：

   * 傳送另一封電子郵件給未開啟第一封電子郵件的收件者。
   * 傳送簡訊給開啟電子郵件但未點按優惠方案連結的收件者。
   * 將開啟電子郵件並按一下連結的收件者新增至資料庫。

![](assets/wkf_cross-channel_7.png)

## 步驟1:鎖定對象 {#step-1--targeting-the-audience}

若要定義目標，請建立查詢以識別收件者。

1. 建立促銷活動. 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在 **[!UICONTROL Targeting and workflows]** 標籤，新增 **查詢** 活動。 有關使用此活動的詳細資訊，請參閱 [本節](query.md).
1. 定義將接收您傳遞內容的收件者。 例如，選擇「金」成員作為目標維。
1. 新增篩選條件至查詢。 在此範例中，選取具有電子郵件地址和行動電話號碼的收件者。

   ![](assets/wkf_cross-channel_3.png)

1. 儲存您的變更。

## 步驟2:建立包含優惠方案的電子郵件 {#step-2--creating-an-email-including-an-offer}

1. 建立 **[!UICONTROL Email delivery]** 活動，並在工作流程中連按兩下它以進行編輯。 如需建立電子郵件的詳細資訊，請參閱 [本節](../../delivery/using/about-email-channel.md).
1. 設計訊息並將包含選件的連結插入內容中。

   ![](assets/wkf_cross-channel_1.png)

   如需將優惠方案整合至訊息內文的詳細資訊，請參閱 [本節](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. 儲存您的變更。
1. 以滑鼠右鍵按一下 **[!UICONTROL Email delivery]** 活動以開啟。
1. 選取 **[!UICONTROL Generate an outbound transition]** 選項來復原母體和追蹤記錄。

   ![](assets/wkf_cross-channel_2.png)

   這可讓您根據收件者在收到第一封電子郵件時的行為，使用此資訊來傳送另一封傳送。

1. 新增 **[!UICONTROL Wait]** 讓收件者數天開啟電子郵件的活動。

   ![](assets/wkf_cross-channel_4.png)

## 步驟3:將產生的對象分段 {#step-3--segmenting-the-resulting-audience}

識別目標並建立第一次傳遞後，您需要使用篩選條件將目標細分為不同的母體。

1. 新增 **分割** 活動並開啟它。 有關使用此活動的詳細資訊，請參閱 [本節](split.md).
1. 從查詢上游的母體計算中建立三個區段。

   ![](assets/wkf_cross-channel_6.png)

1. 對於第一個子集，選取 **[!UICONTROL Add a filtering condition on the inbound population]** 選項，然後按一下 **[!UICONTROL Edit]**.

   ![](assets/wkf_cross-channel_8.png)

1. 選擇 **[!UICONTROL Recipients of a delivery]** 作為限制篩選，然後按一下 **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_9.png)

1. 在篩選設定中，選取 **[!UICONTROL Recipients who have not opened or clicked (email)]** 從 **[!UICONTROL Behavior]** 下拉式清單中，並從傳送清單中選取包含您要傳送之優惠方案的電子郵件。 按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/wkf_cross-channel_10.png)

1. 對第二個子集執行類似操作並選擇 **[!UICONTROL Recipients who have not clicked (email)]** 從 **[!UICONTROL Behavior]** 下拉式清單。

   ![](assets/wkf_cross-channel_11.png)

1. 對於第三個子集，在選取 **[!UICONTROL Add a filtering condition on the inbound population]** 按一下 **[!UICONTROL Edit]**，請選取 **[!UICONTROL Use a specific filtering dimension]** 選項。
1. 選擇 **[!UICONTROL Recipient tracking log]** 從 **[!UICONTROL Filtering dimension]** 下拉清單，突出顯示 **[!UICONTROL Filtering conditions]** 從 **[!UICONTROL List of restriction filters]** 按一下 **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_12.png)

1. 選取篩選條件，如下所示：

   ![](assets/wkf_cross-channel_13.png)

1. 按一下 **[!UICONTROL Finish]** 來儲存變更。

## 步驟4:完成工作流程 {#step-4--finalizing-the-workflow}

1. 在從 **[!UICONTROL Split]** 活動：

   * 新增 **[!UICONTROL Email delivery]** 活動，傳送提醒電子郵件至第一個子集。
   * 新增 **[!UICONTROL Mobile delivery]** 傳送SMS訊息至第二子集的活動。
   * 新增 **[!UICONTROL List update]** 活動，將對應的收件者新增至資料庫。

1. 連按兩下工作流程中的傳送活動以進行編輯。 如需建立電子郵件和簡訊的詳細資訊，請參閱 [電子郵件通道](../../delivery/using/about-email-channel.md) 和 [SMS通道](../../delivery/using/sms-channel.md).
1. 按兩下 **[!UICONTROL List update]** 活動並選取 **[!UICONTROL Generate an outbound transition]** 選項。

   然後，您可以將產生的收件者從Adobe Campaign匯出至Adobe Experience Cloud。 例如，您可以在Adobe Target中使用對象，方法是新增 **[!UICONTROL Update shared audience]** 活動。 有關詳細資訊，請參閱 [匯出對象](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. 按一下 **開始** 按鈕，執行工作流。

目標母體 **查詢** 活動將會分段，以根據收件者的行為接收電子郵件或簡訊傳送。 剩餘母體將使用 **[!UICONTROL List update]** 活動。
