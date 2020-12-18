---
solution: Campaign Classic
product: campaign
title: 建立種子地址
description: 瞭解如何建立和使用種子位址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---


# 建立種子地址{#creating-seed-addresses}

種子位址不是透過標準描述檔和目標來管理，而是在Adobe Campaign階層&#x200B;**[!UICONTROL Resources > Campaign management > Seed addresses]**&#x200B;的專用節點中。

您可以建立子資料夾以組織種子地址。 要執行此操作，請按一下右鍵&#x200B;**[!UICONTROL Seed addresses]**&#x200B;節點，然後選擇&#x200B;**[!UICONTROL Create a new 'Seed addresses' folder]**。 為子資料夾命名，然後按&#x200B;**[!UICONTROL Enter]**&#x200B;進行驗證。 您現在可以建立或複製種子位址至此子資料夾。 有關詳細資訊，請參閱[定義地址](#defining-addresses)。

Adobe Campaign也可讓您建立種子位址範本，這些範本會匯入傳送或促銷活動，並根據相關傳送和促銷活動的特定需求加以調整。 請參閱[建立種子地址模板](#creating-seed-address-templates)。

## 定義地址{#defining-addresses}

要建立種子地址，請執行以下步驟：

1. 按一下種子地址清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。
1. 在&#x200B;**[!UICONTROL Recipient]**&#x200B;標籤的匹配欄位中輸入連結到地址的資料。 可用欄位對應於傳送接收者配置檔案中的標準欄位（nms:recipient表）:姓名、名字、電子郵件等。

   >[!NOTE]
   >
   >地址的標籤會自動填入您定義的姓氏和名字。
   >
   >建立種子地址時，不需要輸入每個頁籤的所有欄位。 任何遺失的個人化元素會在傳送期間隨機輸入。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在&#x200B;**[!UICONTROL Seed fields]**&#x200B;標籤中，輸入在分析階段（在&#x200B;**[!UICONTROL nms:broadLog]**&#x200B;表格中）期間將插入傳送日誌的值。

1. 在&#x200B;**[!UICONTROL Additional data]**&#x200B;標籤中，輸入在「資料管理」工作流程中建立且您要指派特定值給之傳送的個人化資料。

   >[!NOTE]
   >
   >請確定已定義其他目標資料，其別名以&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動中的&#39;@&#39;開頭。 否則，您將無法在傳送活動中正確使用種子地址。

## 建立種子地址模板{#creating-seed-address-templates}

要建立要導入的地址模板，並且可針對每個傳送進行修改，該過程與定義新種子地址時的過程相同。 唯一的區別是種子地址模板地址必須儲存在「模板」類型資料夾中。

要定義模板資料夾，請應用以下流程：

1. 建立新的&#x200B;**[!UICONTROL Seed addresses]**&#x200B;類型資料夾，以滑鼠右鍵按一下資料夾，然後選取&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 按一下&#x200B;**[!UICONTROL Restriction]**&#x200B;頁籤並添加以下過濾條件：**@isModel = true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   儲存在此資料夾中的地址現在可用作地址範本。 您可以將它們匯入傳送或促銷活動，並根據相關傳送和促銷活動的特定需求加以調整（請參閱[新增種子位址](../../delivery/using/adding-seed-addresses.md)）。
