---
product: campaign
title: 如何使用工作流程資料
description: 瞭解如何使用工作流程資料
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 如何使用工作流程資料{#how-to-use-workflow-data}



## 更新資料庫 {#updating-the-database}

所有收集的資料都可用於更新資料庫或用於傳送。 例如，您可以豐富訊息內容個人化的可能性（包括訊息中的合約數、指定去年的平均購物車等）或詳細人口目標定位（傳送訊息給合約共同持有者、目標定位線上服務的1,000個最佳訂閱者等）。 此資料也可以匯出或封存於清單中。

### 清單和直接更新 {#lists-and-direct-updates}

Adobe Campaign資料庫和現有清單的資料可以使用兩個專用活動進行更新：

* **[!UICONTROL List update]**&#x200B;活動可讓您將工作表儲存在資料清單中。

  您可以選取或建立現有清單。 在這種情況下，將計算名稱，並可能計算記錄資料夾。

  ![](assets/s_user_create_list.png)

  請參閱[清單更新](list-update.md)。

* **[!UICONTROL Update data]**&#x200B;活動會大量更新資料庫中的欄位。

  如需詳細資訊，請參閱[更新資料](update-data.md)。

### 訂閱/取消訂閱管理 {#subscription-unsubscription-management}

若要瞭解透過工作流程訂閱及取消訂閱收件者資訊服務的相關資訊，請參閱[訂閱服務](subscription-services.md)。

## 透過工作流程傳送 {#sending-via-a-workflow}

### 傳遞活動 {#delivery-activity}

傳遞活動在[傳遞](delivery.md)中有詳細說明。

### 豐富化及目標定位傳遞 {#enriching-and-targeting-deliveries}

傳遞可處理來自工作流程的資料，以自訂內容或目標母體選擇框架內的內容。

例如，在直接郵件傳送的架構中，您可以在擷取檔案中加入從工作流程中執行的資料操作擷取的其他資料：

![](assets/s_advuser_add_data_postal_mail.png)

除了常用的個人化欄位之外，您還可以將工作流程階段中的個人化欄位新增到傳送內容。 工作流程活動中定義的其他資料可保留並在傳送助理員中供存取，如下列範例所示，以用於定義直接郵件傳送框架內的輸出檔案名稱：

![](assets/s_advuser_using_additional_data.png)

工作流程表格中所包含的資料是以其名稱識別：它一律由&#x200B;**targetData**&#x200B;連結組成。 如需詳細資訊，請參閱[目標資料](data-life-cycle.md#target-data)。

在電子郵件傳送的框架中，個人化欄位也可以使用目標工作流程階段中執行之目標擴充功能的資料，如下列範例所示：

![](assets/s_advuser_add_data_email.png)

如果在目標定位活動中指定了區段代碼，則會將其新增到工作流程表格的特定欄，並會與個人化欄位一起提供。 若要顯示所有個人化欄位，請按一下可透過個人化按鈕存取的&#x200B;**[!UICONTROL Target extension > Other...]**&#x200B;連結。

![](assets/s_advuser_segment_code_select.png)
