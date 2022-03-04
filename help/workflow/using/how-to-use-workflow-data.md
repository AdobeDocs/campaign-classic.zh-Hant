---
product: campaign
title: 如何使用工作流程資料
description: 瞭解如何使用工作流資料
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---

# 如何使用工作流程資料{#how-to-use-workflow-data}

![](../../assets/common.svg)

## 更新資料庫 {#updating-the-database}

所有收集的資料都可用於更新資料庫，或在交貨中。 例如，您可以豐富郵件內容個性化的可能性（包括郵件中的合同數、指定過去一年的平均購物車等） 或詳細的人口目標（向合同合同持有人發送消息，瞄準1000名線上服務最佳訂戶等）。 此資料也可以在清單中導出或存檔。

### 清單和直接更新 {#lists-and-direct-updates}

Adobe Campaign資料庫和現有清單的資料可通過以下兩項專門活動進行更新：

* 的 **[!UICONTROL List update]** 活動允許您將工作表儲存在資料庫中。

   您可以選擇現有清單或建立它。 在這種情況下，將計算名稱以及可能的記錄資料夾。

   ![](assets/s_user_create_list.png)

   請參閱 [清單更新](list-update.md)。

* 的 **[!UICONTROL Update data]** activity對資料庫中的欄位執行成批更新。

   有關此內容的詳細資訊，請參閱 [更新資料](update-data.md)。

### 訂閱/取消訂閱管理 {#subscription-unsubscription-management}

要瞭解有關通過工作流訂閱和取消訂閱資訊服務的收件人的資訊，請參閱 [訂閱服務](subscription-services.md)。

## 通過工作流發送 {#sending-via-a-workflow}

### 交貨活動 {#delivery-activity}

交貨活動詳見 [交貨](delivery.md)。

### 豐富和定向遞送 {#enriching-and-targeting-deliveries}

遞送可以處理來自工作流的資料以便自定義內容或在目標填充選擇框架內。

例如，在直郵遞送的框架內，您可以在抽取檔案中包括附加資料，這些資料來自工作流中執行的資料處理：

![](assets/s_advuser_add_data_postal_mail.png)

除了通常的個性化欄位外，您還可以將工作流階段中的個性化欄位添加到交付內容。 工作流活動中定義的其他資料可以在傳遞嚮導中保留並可訪問，如下例所示，用於定義直接郵件傳遞框架中的輸出檔案的名稱：

![](assets/s_advuser_using_additional_data.png)

工作流表中包含的資料由其名稱標識：它總是由 **目標資料** 的子菜單。 有關此內容的詳細資訊，請參閱 [目標資料](data-life-cycle.md#target-data)。

在電子郵件傳遞的框架中，個性化欄位還可以使用目標工作流階段中執行的目標擴展中的資料，如下例所示：

![](assets/s_advuser_add_data_email.png)

如果在目標活動中指定了段代碼，則會將其添加到工作流表的特定列，並將與個性化欄位一起提供。 要顯示所有個性化欄位，請按一下 **[!UICONTROL Target extension > Other...]** 可通過個性化按鈕訪問的連結。

![](assets/s_advuser_segment_code_select.png)
