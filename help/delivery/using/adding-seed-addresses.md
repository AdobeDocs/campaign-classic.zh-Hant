---
product: campaign
title: 新增種子地址
description: 新增種子地址
feature: Seed Address
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 5%

---

# 新增種子地址{#adding-seed-addresses}

![](../../assets/common.svg)

## 遞送中的種子地址 {#seed-addresses-in-a-delivery}

要為交貨添加特定種子地址，請按一下 **[!UICONTROL To]** 連結，然後選擇 **[!UICONTROL Seed addresses]** 頁籤。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三種可能的插入模式：

1. 輸入單個種子地址。

   要執行此操作，請按一下 **[!UICONTROL Add]** 按鈕並定義地址欄位的內容。 對每個地址重複。

1. 導入地址模板並調整它們以滿足您的需要。

   要執行此操作，請按一下 **[!UICONTROL Import seed templates...]** 連結並選擇包含地址模板的資料夾。 如需詳細資訊，請參閱[本章節](creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，添加後，可按兩下它們或按一下 **[!UICONTROL Detail...]** 按鈕來調整每個地址的內容。

1. 建立條件以動態選擇要插入的控制地址。

   要執行此操作，請按一下 **[!UICONTROL Edit the dynamic condition...]** 連結，然後輸入種子地址選擇參數。 例如，您可以包括特定資料夾中包含的所有種子地址，或包括您組織中屬於特定部門的種子地址。

   本節將介紹一個示例： [用例：選擇標準中的種子地址](use-case--selecting-seed-addresses-on-criteria.md)。

>[!NOTE]
>
>當使用的收件人表不是預設值時，將使用此選項 **nms：收件人** 表，並且您正在使用隨Adobe Campaign **[!UICONTROL Deliverability]** 中。
>
>有關此內容的詳細資訊，請參閱 [使用外部收件人表](using-an-external-recipient-table.md) 以及 [收件箱呈現](inbox-rendering.md)。

對於交貨，您還可以自定義地址插入提取檔案的方式。 預設情況下，它們會按輸出檔案的排序順序插入，但您可以選擇在檔案的末尾或開頭插入，或在主目標的收件人之間隨機插入。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 市場活動中的種子地址 {#seed-addresses-in-a-campaign}

要將種子地址添加到市場活動的目標中，請選擇該操作，然後按一下 **[!UICONTROL Edit]** 頁籤。

按一下 **[!UICONTROL Advanced campaign settings...]** 連結，然後 **[!UICONTROL Seed addresses]** 頁籤，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

從市場活動插入的種子地址將添加到市場活動中每個交貨的目標。
