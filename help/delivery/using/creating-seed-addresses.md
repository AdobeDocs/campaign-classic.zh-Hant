---
product: campaign
title: 建立種子地址
description: 瞭解如何建立和使用種子地址
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Seed Address
role: User, Data Engineer
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# 建立種子地址{#creating-seed-addresses}

種子地址不是透過標準設定檔和目標進行管理，而是在Adobe Campaign階層的專用節點中進行管理 **[!UICONTROL Resources > Campaign management > Seed addresses]**.

您可以建立子資料夾以組織種子地址。 若要這麼做，請用滑鼠右鍵按一下 **[!UICONTROL Seed addresses]** 節點並選取 **[!UICONTROL Create a new 'Seed addresses' folder]**. 為子資料夾命名，然後按下 **[!UICONTROL Enter]** 以進行驗證。 您現在可以建立種子地址或將其複製到此子資料夾。 有關詳細資訊，請參閱 [定義地址](#defining-addresses).

Adobe Campaign也可讓您建立種子地址範本，這些範本會匯入至傳遞或行銷活動中，並根據相關傳遞和行銷活動的特定需求進行調整。 請參閱 [建立種子地址範本](#creating-seed-address-templates).

## 定義地址 {#defining-addresses}

若要建立種子地址，請遵循下列步驟：

1. 按一下 **[!UICONTROL New]** 按鈕來標籤種子地址。
1. 在的相符欄位中，輸入連結至地址的資料 **[!UICONTROL Recipient]** 標籤。 可用欄位與傳送收件者（nms：recipient表格）之設定檔中的標準欄位相對應：名稱、名字、電子郵件等。

   >[!NOTE]
   >
   >地址的標籤會自動填入您定義的姓氏和名字。
   >
   >建立種子地址時，不需要輸入每個標籤的所有欄位。 在傳遞分析期間隨機輸入缺少的個人化元素。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在 **[!UICONTROL Address fields]** 索引標籤中，輸入將在分析階段期間插入傳送記錄中的值(在 **[!UICONTROL nms:broadLog]** 表格)。

1. 在 **[!UICONTROL Additional data]** 標籤，輸入在資料管理工作流程中建立且您想要指派特定值的傳遞所使用的個人化資料。

   >[!NOTE]
   >
   >請確定已在中定義其他目標資料，且別名開頭為&#39;@&#39;。 **[!UICONTROL Enrichment]** 活動。 否則，您將無法在傳送活動中正確搭配種子地址使用。

## 建立種子地址範本 {#creating-seed-address-templates}

若要建立將匯入且可能針對每次傳遞修改的位址範本，程式與定義新種子位址時相同。 唯一的區別是種子地址範本地址必須儲存在「範本」型別資料夾中。

若要定義範本資料夾，請套用下列程式：

1. 建立新的 **[!UICONTROL Seed addresses]** 輸入資料夾，在資料夾上按一下滑鼠右鍵，然後選取 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 按一下 **[!UICONTROL Restriction]** 並新增下列篩選條件： **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   儲存在此資料夾中的地址現在可以用作地址範本。 您可以將它們匯入傳遞或行銷活動，並根據相關傳遞和行銷活動的特定需求進行調整(請參閱 [新增種子地址](adding-seed-addresses.md))。
