---
product: campaign
title: 建立種子地址
description: 了解如何建立和使用種子地址
feature: Seed Address
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 0065a25250d73c71e7569768a38b5836cccab992
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 建立種子地址{#creating-seed-addresses}

![](../../assets/common.svg)

種子地址不是透過標準設定檔和目標來管理，而是在Adobe Campaign階層的專用節點中 **[!UICONTROL Resources > Campaign management > Seed addresses]**.

您可以建立子資料夾以組織種子地址。 若要這麼做，請以滑鼠右鍵按一下 **[!UICONTROL Seed addresses]** 節點和選取 **[!UICONTROL Create a new 'Seed addresses' folder]**. 為子資料夾命名，然後按 **[!UICONTROL Enter]** 以驗證。 您現在可以建立種子地址或將種子地址複製到此子資料夾。 有關詳細資訊，請參閱 [定義地址](#defining-addresses).

Adobe Campaign也可讓您建立種子地址範本，這些範本會匯入至傳遞或促銷活動中，並根據相關傳遞和促銷活動的特定需求加以調整。 請參閱 [建立種子地址模板](#creating-seed-address-templates).

## 定義地址 {#defining-addresses}

要建立種子地址，請執行以下步驟：

1. 按一下 **[!UICONTROL New]** 按鈕（位於種子地址清單的上方）。
1. 在 **[!UICONTROL Recipient]** 標籤。 可用欄位對應於傳送收件者設定檔中的標準欄位（nms:recipient表格）:姓名、名字、電子郵件等

   >[!NOTE]
   >
   >地址的標籤會自動填入您定義的姓氏和名字。
   >
   >建立種子地址時，您不需要輸入每個頁簽的所有欄位。 傳遞分析期間會隨機輸入遺漏的個人化元素。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在 **[!UICONTROL Address fields]** 索引標籤，輸入要在分析階段插入傳送記錄中的值(在 **[!UICONTROL nms:broadLog]** 表格)。

1. 在 **[!UICONTROL Additional data]** 索引標籤，輸入在資料管理工作流程中建立，且您想要指派特定值給的傳送所使用的個人化資料。

   >[!NOTE]
   >
   >請確定已以別名（以「@」開頭）定義其他目標資料， **[!UICONTROL Enrichment]** 活動。 否則，您將無法在傳遞活動中將種子地址正確使用它們。

## 建立種子地址模板 {#creating-seed-address-templates}

要建立將導入的地址模板，並且可以針對每次傳送進行修改，該過程與定義新種子地址時的過程相同。 唯一的區別是種子地址模板地址必須儲存在「模板」類型資料夾中。

要定義模板資料夾，請應用以下過程：

1. 建立新 **[!UICONTROL Seed addresses]** 類型資料夾，按一下右鍵資料夾，然後選取 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 按一下 **[!UICONTROL Restriction]** 標籤，然後新增下列篩選條件： **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   儲存在此資料夾中的地址現在可以用作地址模板。 您可以將它們匯入傳送或行銷活動中，並根據相關傳送和行銷活動的特定需求加以調整(請參閱 [添加種子地址](adding-seed-addresses.md))。
