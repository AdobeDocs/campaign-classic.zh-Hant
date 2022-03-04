---
product: campaign
title: 建立種子地址
description: 瞭解如何建立和使用種子地址
feature: Seed Address
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 建立種子地址{#creating-seed-addresses}

![](../../assets/common.svg)

種子地址不是通過標準配置檔案和目標管理的，而是在Adobe Campaign層次結構的專用節點中 **[!UICONTROL Resources > Campaign management > Seed addresses]**。

您可以建立子資料夾以組織種子地址。 為此，請按一下右鍵 **[!UICONTROL Seed addresses]** 節點和選擇 **[!UICONTROL Create a new 'Seed addresses' folder]**。 命名子資料夾，然後按 **[!UICONTROL Enter]** 驗證。 現在，您可以建立種子地址或將種子地址複製到此子資料夾。 有關此內容的詳細資訊，請參閱 [定義地址](#defining-addresses)。

Adobe Campaign還允許您建立種子地址模板，這些模板將導入交貨或市場活動中，並根據相關交貨和市場活動的特定需求進行調整。 請參閱 [建立種子地址模板](#creating-seed-address-templates)。

## 定義地址 {#defining-addresses}

要建立種子地址，請執行以下步驟：

1. 按一下 **[!UICONTROL New]** 按鈕。
1. 在匹配欄位中輸入連結到地址的資料 **[!UICONTROL Recipient]** 頁籤。 可用欄位與遞送收件人配置檔案（nms:recipient表）中的標準欄位對應：姓名、名字、電子郵件等。

   >[!NOTE]
   >
   >地址的標籤將自動填入您定義的姓氏和名字。
   >
   >建立種子地址時，不必輸入每個頁籤的所有欄位。 任何缺失的個性化元素在交付期間隨機輸入。

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 在 **[!UICONTROL Seed fields]** 頁籤，在分析階段輸入將在交貨日誌中插入的值(在 **[!UICONTROL nms:broadLog]** )的正平方根。

1. 在 **[!UICONTROL Additional data]** 頁籤，輸入用於在資料管理工作流中建立的交貨的個性化資料，以及要為其分配特定值的資料。

   >[!NOTE]
   >
   >確保已使用以「@」開頭的別名在中定義了其他目標資料 **[!UICONTROL Enrichment]** 的子菜單。 否則，您將無法在交付活動中將它們與種子地址正確一起使用。

## 建立種子地址模板 {#creating-seed-address-templates}

要建立要導入的地址模板，並且可以為每個傳遞修改地址模板，該流程與定義新種子地址時的流程相同。 唯一的區別是種子地址模板地址必須儲存在「Template」類型資料夾中。

要定義模板資料夾，請應用以下流程：

1. 新建 **[!UICONTROL Seed addresses]** 鍵入資料夾，按一下右鍵資料夾，然後選擇 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 按一下 **[!UICONTROL Restriction]** 頁籤，然後添加以下篩選條件： **@isModel =true**。

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   現在，儲存在此資料夾中的地址可以用作地址模板。 您可以將它們導入交貨或市場活動中，並根據相關交貨和市場活動的特定需求調整它們(請參閱： [添加種子地址](adding-seed-addresses.md))。
