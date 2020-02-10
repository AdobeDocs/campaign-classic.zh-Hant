---
title: 建立種子地址
seo-title: 建立種子地址
description: 建立種子地址
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 建立種子地址{#creating-seed-addresses}

種子位址不是透過標準描述檔和目標來管理，而是在Adobe Campaign階層的專用節點中 **[!UICONTROL Resources > Campaign management > Seed addresses]**。

您可以建立子資料夾以組織種子地址。 要執行此操作，請按一下右鍵該節 **[!UICONTROL Seed addresses]** 點並選擇 **[!UICONTROL Create a new 'Seed addresses' folder]**。 命名子資料夾，然後按 **[!UICONTROL Enter]** 以驗證。 您現在可以建立或複製種子位址至此子資料夾。 For more on this, refer to [Defining addresses](#defining-addresses).

Adobe Campaign也可讓您建立種子位址範本，這些範本會匯入傳送或促銷活動，並根據相關傳送和促銷活動的特定需求加以調整。 請參閱「創 [建種子地址模板」](#creating-seed-address-templates)。

## 定義地址 {#defining-addresses}

要建立種子地址，請執行以下步驟：

1. 按一下 **[!UICONTROL New]** 種子地址清單上方的按鈕。
1. 在標籤的匹配欄位中輸入連結至地址的 **[!UICONTROL Recipient]** 資料。 可用欄位與傳送接收者配置檔案中的標準欄位相對應（nms:recipient表）:姓名、名字、電子郵件等。

   >[!NOTE]
   >
   >地址的標籤會自動填入您定義的姓氏和名字。
   >
   >建立種子地址時，不需要輸入每個頁籤的所有欄位。 任何遺失的個人化元素會在傳送期間隨機輸入。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在標 **[!UICONTROL Seed fields]** 簽中，輸入在分析階段（在表中）期間將插入傳送日誌中 **[!UICONTROL nms:broadLog]** 的值。
1. 在標籤中， **[!UICONTROL Additional data]** 輸入用於在「資料管理」工作流程中建立且您要指派特定值給之傳送的個人化資料。

## 建立種子地址模板 {#creating-seed-address-templates}

要建立要導入的地址模板，並且可針對每個傳送進行修改，該過程與定義新種子地址時的過程相同。 唯一的區別是種子地址模板地址必須儲存在「模板」類型資料夾中。

要定義模板資料夾，請應用以下流程：

1. 建立新類型 **[!UICONTROL Seed addresses]** 資料夾，以滑鼠右鍵按一下資料夾，然後選取 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 按一下標 **[!UICONTROL Restriction]** 簽並新增下列篩選條件： **@isModel = true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   儲存在此資料夾中的地址現在可用作地址範本。 您可以將它們匯入傳送或促銷活動，並根據相關傳送和促銷活動的特定需求加以調整(請參 [閱新增種子地址](../../delivery/using/adding-seed-addresses.md))。
