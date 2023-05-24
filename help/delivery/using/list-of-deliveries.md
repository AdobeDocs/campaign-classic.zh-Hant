---
product: campaign
title: 存取傳遞清單
description: 瞭解如何存取已建立的傳遞清單
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: 6c0fd76f-3d79-4b69-b911-f8d99dd18c4b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 10%

---

# 存取傳遞清單 {#list-of-deliveries}



您可以從傳遞清單存取傳遞，方法是透過 **[!UICONTROL Campaign Management > Deliveries]** 樹狀結構的節點。

![](assets/deliveries-list.png)

依預設，傳遞清單包含在所選節點中建立的傳遞的名稱和狀態。 它也會顯示要成功傳送、處理和傳送的訊息數。

* 「 」的數量 **[!UICONTROL Messages to send]** 對應於分析後和傳遞前鎖定的收件者人數。
* 中的訊息數 **[!UICONTROL Success]** 欄對應於伺服器傳送的訊息數，以及收件者接收的訊息數。
* 「 」的數量 **[!UICONTROL Processed]** messages對應到已接收的訊息數加上有錯誤的訊息數。

>[!NOTE]
>
>對於大型傳遞，您可能希望更新這些值。 若要這麼做，請選取有問題的傳送，然後在其上按一下滑鼠右鍵。 選取 **[!UICONTROL Action > Recompute delivery and tracking indicators...]** 然後使用精靈來更新此資訊。

**相關主題：**

* [傳遞儀表板](delivery-dashboard.md)
* [傳遞狀態](delivery-statuses.md)
