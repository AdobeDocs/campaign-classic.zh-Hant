---
product: campaign
title: 如何使用工作流程資料
description: 了解如何使用工作流程資料
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---

# 如何使用工作流程資料{#how-to-use-workflow-data}

![](../../assets/common.svg)

## 更新資料庫 {#updating-the-database}

所有收集的資料都可用來更新資料庫或傳送。 例如，您可以豐富訊息內容個人化的可能性（包括訊息中的合約數、指定去年的平均購物車等） 或詳細人口目標定位（傳送訊息給合約合同持有人、鎖定1,000位線上服務最佳訂閱者等）。 此資料也可匯出或封存於清單中。

### 清單和直接更新 {#lists-and-direct-updates}

Adobe Campaign資料庫的資料和現有清單可使用兩個專用活動來更新：

* 此 **[!UICONTROL List update]** 活動可讓您將工作表儲存在資料庫中。

   您可以選取現有清單或加以建立。 在此情況下，將計算名稱和可能的記錄資料夾。

   ![](assets/s_user_create_list.png)

   請參閱 [清單更新](list-update.md).

* 此 **[!UICONTROL Update data]** 活動會執行資料庫中欄位的大量更新。

   有關詳細資訊，請參閱 [更新資料](update-data.md).

### 訂閱/取消訂閱管理 {#subscription-unsubscription-management}

若要了解如何透過工作流程訂閱和取消訂閱收件者至資訊服務，請參閱 [訂閱服務](subscription-services.md).

## 透過工作流程傳送 {#sending-via-a-workflow}

### 傳送活動 {#delivery-activity}

傳送活動在 [傳送](delivery.md).

### 豐富化及鎖定傳送 {#enriching-and-targeting-deliveries}

傳遞可處理工作流程中的資料，以自訂內容或在目標母體選擇的框架內。

例如，在直接郵件傳送的架構內，您可以在擷取檔案中，包含從工作流程中執行的資料操作擷取的其他資料：

![](assets/s_advuser_add_data_postal_mail.png)

除了通常的個人化欄位，您還可以將工作流程階段的個人化欄位新增至傳送內容。 可以在傳送精靈中保留並存取工作流程活動中定義的其他資料，如下列範例所示，以在直接郵件傳送的架構中定義輸出檔案的名稱：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的資料由其名稱標識：它總是由 **targetData** 連結。 有關詳細資訊，請參閱 [目標資料](data-life-cycle.md#target-data).

在電子郵件傳送的架構中，個人化欄位也可以使用目標擴充功能在目標工作流程階段中執行的資料，如下列範例所示：

![](assets/s_advuser_add_data_email.png)

如果在鎖定目標活動中指定區段代碼，則會將其新增至工作流程表格的特定欄，並連同個人化欄位一併提供。 若要顯示所有個人化欄位，請按一下 **[!UICONTROL Target extension > Other...]** 可透過個人化按鈕存取的連結。

![](assets/s_advuser_segment_code_select.png)
