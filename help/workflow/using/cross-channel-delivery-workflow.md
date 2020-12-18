---
solution: Campaign Classic
product: campaign
title: 跨通道傳遞工作流程
description: 進一步瞭解跨通道傳送工作流程
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---


# 跨通道傳遞工作流程{#cross-channel-delivery-workflow}

此使用案例提供跨通道傳送工作流程的範例。 本節[介紹跨通道傳送的一般概念。](../../workflow/using/cross-channel-deliveries.md)

目標是將資料庫收件者的讀者細分為不同群組，以便傳送電子郵件至群組，並傳送SMS訊息至其他群組。

此使用案例的主要實施步驟如下：

1. 建立&#x200B;**[!UICONTROL Query]**&#x200B;活動以鎖定您的對象。
1. 建立包含選件連結的&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動。
1. 使用&#x200B;**[!UICONTROL Split]**&#x200B;活動可：

   * 傳送另一封電子郵件給未開啟第一封電子郵件的收件者。
   * 傳送簡訊給開啟電子郵件但未按一下選件連結的收件者。
   * 將開啟電子郵件並按一下連結的收件者新增至資料庫。

![](assets/wkf_cross-channel_7.png)

## 步驟1:鎖定對象{#step-1--targeting-the-audience}

若要定義目標，請建立查詢以識別收件者。

1. 建立促銷活動. 如需詳細資訊，請參閱[本章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在促銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中，將&#x200B;**Query**&#x200B;活動新增至工作流程。 有關使用本練習的詳細資訊，請參閱[本節](../../workflow/using/query.md)。
1. 定義將接收您遞送的收件者。 例如，選擇「Gold」成員作為目標維。
1. 新增篩選條件至查詢。 在此範例中，選取具有電子郵件地址和行動號碼的收件者。

   ![](assets/wkf_cross-channel_3.png)

1. 儲存您的變更。

## 步驟2:建立包含選件{#step-2--creating-an-email-including-an-offer}的電子郵件

1. 建立&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動，並在工作流程中按兩下該活動以加以編輯。 如需建立電子郵件的詳細資訊，請參閱[本節](../../delivery/using/about-email-channel.md)。
1. 設計訊息並將包含選件的連結插入內容。

   ![](assets/wkf_cross-channel_1.png)

   如需將選件整合至訊息內文的詳細資訊，請參閱[本節](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine)。

1. 儲存您的變更。
1. 按一下右鍵&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動以將其開啟。
1. 選擇&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項以恢復人口和跟蹤日誌。

   ![](assets/wkf_cross-channel_2.png)

   這可讓您使用這項資訊，根據收件者在收到第一封電子郵件時的行為，傳送其他傳送內容。

1. 新增&#x200B;**[!UICONTROL Wait]**&#x200B;活動，讓收件者在幾天內開啟電子郵件。

   ![](assets/wkf_cross-channel_4.png)

## 步驟3:將產生的觀眾{#step-3--segmenting-the-resulting-audience}分段

在識別目標並建立第一次傳送後，您必須使用篩選條件將目標細分為不同的人口族群。

1. 將&#x200B;**Split**&#x200B;活動新增至工作流程並開啟它。 有關使用本練習的詳細資訊，請參閱[本節](../../workflow/using/split.md)。
1. 從查詢上游計算的人口族群建立三個區段。

   ![](assets/wkf_cross-channel_6.png)

1. 對於第一個子集，選擇&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Edit]**。

   ![](assets/wkf_cross-channel_8.png)

1. 選擇&#x200B;**[!UICONTROL Recipients of a delivery]**&#x200B;作為限制過濾器，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/wkf_cross-channel_9.png)

1. 在篩選設定中，從&#x200B;**[!UICONTROL Behavior]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Recipients who have not opened or clicked (email)]**，然後選取電子郵件，包括您要從傳送清單傳送的選件。 按一下 **[!UICONTROL Finish]**。

   ![](assets/wkf_cross-channel_10.png)

1. 對第二個子集進行類似操作，並從&#x200B;**[!UICONTROL Behavior]**&#x200B;下拉清單中選擇&#x200B;**[!UICONTROL Recipients who have not clicked (email)]**。

   ![](assets/wkf_cross-channel_11.png)

1. 對於第三個子集，在選擇&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**&#x200B;並按一下&#x200B;**[!UICONTROL Edit]**&#x200B;後，選擇&#x200B;**[!UICONTROL Use a specific filtering dimension]**&#x200B;選項。
1. 從&#x200B;**[!UICONTROL Filtering dimension]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Recipient tracking log]**，從&#x200B;**[!UICONTROL List of restriction filters]**&#x200B;中反白標示&#x200B;**[!UICONTROL Filtering conditions]**，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/wkf_cross-channel_12.png)

1. 選擇篩選條件，如下所示：

   ![](assets/wkf_cross-channel_13.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以儲存變更。

## 步驟4:定版工作流{#step-4--finalizing-the-workflow}

1. 在由&#x200B;**[!UICONTROL Split]**&#x200B;活動產生的三個子集之後，將相關活動添加到工作流中：

   * 新增&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動，傳送提醒電子郵件至第一個子集。
   * 新增&#x200B;**[!UICONTROL Mobile delivery]**&#x200B;活動，以傳送SMS訊息至第二子集。
   * 添加&#x200B;**[!UICONTROL List update]**&#x200B;活動，將相應的收件者添加到資料庫。

1. 連按兩下工作流程中的傳送活動以進行編輯。 有關建立電子郵件和SMS的詳細資訊，請參閱[電子郵件通道](../../delivery/using/about-email-channel.md)和[SMS通道](../../delivery/using/sms-channel.md)。
1. 連按兩下&#x200B;**[!UICONTROL List update]**&#x200B;活動，然後選取&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項。

   然後，您可以將產生的收件者從Adobe Campaign匯出至Adobe Experience Cloud。 例如，您可以在Adobe Target中新增&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活動來使用對象。 如需詳細資訊，請參閱[匯出觀眾](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience)。

1. 按一下操作欄中的&#x200B;**開始**&#x200B;按鈕以執行工作流。

將分段由&#x200B;**Query**&#x200B;活動定位的人口，以根據收件人的行為接收電子郵件或SMS傳送。 剩餘人口將使用&#x200B;**[!UICONTROL List update]**&#x200B;活動添加到資料庫。
