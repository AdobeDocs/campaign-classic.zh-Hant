---
product: campaign
title: 建立種子地址
description: 瞭解如何建立和使用種子地址
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Seed Address
role: User, Developer
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
TQID: https://experienceleague.adobe.com/ya4m8nG7m3DUj-buOZMnd2Nzfx1J6lmIiOuo1VcHjwU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a658c786-869b-4194-a780-2594d663adda
subfeature_v2: id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 426
ht-degree: 1%

---

# 建立種子地址{#creating-seed-addresses}

種子位址不是透過標準設定檔和目標來管理，而是在Adobe Campaign階層&#x200B;**[!UICONTROL Resources > Campaign management > Seed addresses]**&#x200B;的專用節點中管理。

您可以建立子資料夾以組織種子地址。 若要這麼做，請用滑鼠右鍵按一下&#x200B;**[!UICONTROL Seed addresses]**&#x200B;節點並選取&#x200B;**[!UICONTROL Create a new 'Seed addresses' folder]**。 為子資料夾命名，然後按&#x200B;**[!UICONTROL Enter]**&#x200B;進行驗證。 您現在可以建立種子地址或將其複製到此子資料夾。 如需詳細資訊，請參閱[定義地址](#defining-addresses)。

Adobe Campaign也可讓您建立種子地址範本，這些範本會匯入至傳遞或行銷活動中，並根據相關傳遞和行銷活動的特定需求進行調整。 請參閱[建立種子地址範本](#creating-seed-address-templates)。

## 定義地址 {#defining-addresses}

若要建立種子地址，請遵循下列步驟：

1. 按一下種子地址清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。
1. 從&#x200B;**[!UICONTROL Recipient]**&#x200B;索引標籤的相符欄位中，輸入連結到位址的資料。 可用欄位對應到傳遞收件者（nms:recipient表格）之設定檔中的標準欄位：名稱、名字、電子郵件等。

   >[!NOTE]
   >
   >地址的標籤會自動填入您定義的姓氏和名字。
   >
   >建立種子地址時，不需要輸入每個標籤的所有欄位。 在傳遞分析期間隨機輸入缺少的個人化元素。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在&#x200B;**[!UICONTROL Address fields]**&#x200B;索引標籤中，輸入將在分析階段（在&#x200B;**[!UICONTROL nms:broadLog]**&#x200B;表格中）插入傳遞記錄中的值。

1. 在&#x200B;**[!UICONTROL Additional data]**&#x200B;索引標籤中，輸入用於資料管理工作流程中所建立傳遞的個人化資料，以及您想要指派特定值的對象。

   >[!NOTE]
   >
   >請確定已在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動中定義其他目標資料，且別名開頭為&#39;@&#39;。 否則，您將無法在傳送活動中正確搭配種子地址使用。

## 建立種子地址範本 {#creating-seed-address-templates}

若要建立將匯入且可能針對每次傳遞修改的位址範本，程式與定義新種子位址時相同。 唯一的區別是種子地址範本地址必須儲存在「範本」型別資料夾中。

若要定義範本資料夾，請套用下列程式：

1. 建立新的&#x200B;**[!UICONTROL Seed addresses]**&#x200B;型別資料夾，在資料夾上按一下滑鼠右鍵，然後選取&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 按一下&#x200B;**[!UICONTROL Restriction]**&#x200B;索引標籤並新增下列篩選條件： **@isModel = true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   儲存在此資料夾中的地址現在可以用作地址範本。 您可以將它們匯入傳遞或行銷活動，並根據相關傳遞和行銷活動的特定需求進行調整（請參閱[新增種子地址](adding-seed-addresses.md)）。
