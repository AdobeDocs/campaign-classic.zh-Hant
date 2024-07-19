---
product: campaign
title: 訂閱服務
description: 進一步瞭解訂閱服務工作流程活動
feature: Workflows, Targeting Activity, Subscription Services Activity
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 3%

---

# 訂閱服務{#subscription-services}



**訂閱服務**&#x200B;型別活動可讓您為轉換中指定的母體建立或刪除資訊服務的訂閱。

若要進行設定，請編輯活動並輸入其標籤，然後選取要執行的動作（訂閱或取消訂閱）及相關服務，如下列範例所示：

![](assets/edit_service_inscription.png)

1. 輸入活動的標籤。
1. 若要在執行結束時建立轉換，請選取&#x200B;**[!UICONTROL Generate an outbound transition]**。

   一般而言，目標對資訊服務的訂閱會標籤目標定位工作流程的結尾，這也是預設未啟用選項的原因。

1. 如果您想要訂閱或取消訂閱所選資訊服務的指定母體，請按一下&#x200B;**[!UICONTROL Subscription]**&#x200B;或&#x200B;**[!UICONTROL Unsubscription]**。
1. 選取&#x200B;**[!UICONTROL Send a confirmation message]**&#x200B;以通知收件者他們已訂閱或取消訂閱服務。

   此訊息的內容是在與資訊服務相關的傳遞範本中指定的。 如需詳細資訊，請參閱本[區段](../../delivery/using/managing-subscriptions.md)。

## 範例：訂閱電子報的收件者清單 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

在單一操作中，以下工作流程旨在製作一份符合電子報資格的收件者清單（對象為居住在巴黎的工作人士），以便讓他們訂閱。

若要這麼做，您也必須排除已訂閱的收件者。

>[!CAUTION]
>
>在手動訂閱收件者服務之前，請確認這些收件者接受來自您的通訊。

![](assets/subscription_services_example.png)

1. 新增下列三個查詢：

   * 1個目標收件者，年齡在18至60歲。
   * 第二個目標定位位於巴黎的收件者。
   * 第三個目標定位目前未訂閱電子報的收件者。

1. 新增交集活動以交叉參照不同的結果。
1. 您也可以插入清單更新，使最新訂閱者的清單保持最新狀態。
1. 插入訂閱服務活動，然後按兩下此項以進行設定。
1. 輸入活動標籤並選取&#x200B;**[!UICONTROL Subscription]**。

   如有需要，您可以核取&#x200B;**[!UICONTROL Send a confirmation message]**&#x200B;方塊，通知收件者其電子報訂閱。

1. 選取電子報所在的資料夾，然後從顯示的清單中選取電子報。
1. 取消勾選&#x200B;**[!UICONTROL Generate outbound transition]**，讓此活動將標示工作流程結尾，然後按一下&#x200B;**[!UICONTROL Ok]**。

在工作流程執行期間，與所有三個查詢相對應的收件者會新增到清單中，並訂閱電子報。

您可以前往收件者的「**[!UICONTROL Subscription]**」標籤，檢查訂閱是否成功。

## 輸入引數 {#input-parameters}

* tableName
* 結構描述

每個傳入事件都必須指定由這些引數定義的目標。
