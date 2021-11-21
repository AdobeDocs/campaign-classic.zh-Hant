---
product: campaign
title: 新增種子地址
description: 新增種子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 5%

---

# 新增種子地址{#adding-seed-addresses}

![](../../assets/common.svg)

## 傳送中的種子地址 {#seed-addresses-in-a-delivery}

若要新增傳送的特定種子地址，請按一下 **[!UICONTROL To]** 連結，然後選取 **[!UICONTROL Seed addresses]** 標籤。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三種可能的插入模式：

1. 輸入單個種子地址。

   若要這麼做，請按一下 **[!UICONTROL Add]** 按鈕並定義地址欄位的內容。 對每個地址重複。

1. 匯入地址範本並加以調整以符合您的需求。

   若要這麼做，請按一下 **[!UICONTROL Import seed templates...]** 連結，並選取包含地址範本的資料夾。 如需詳細資訊，請參閱[本章節](creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，新增這些參數後，您可以連按兩下，或按一下 **[!UICONTROL Detail...]** 按鈕來調整每個地址的內容。

1. 建立條件以動態選取要插入的控制地址。

   若要這麼做，請按一下 **[!UICONTROL Edit the dynamic condition...]** 連結，然後輸入種子地址選擇參數。 例如，您可以包含特定資料夾中包含的所有種子地址，或包含貴組織特定部門的種子地址。

   本節將提供此範例： [使用案例：選擇條件上的種子地址](use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>當使用的收件者表格不是預設值時，就會使用此選項 **nms:recipient** 表格，且您使用Adobe Campaign隨附的收件匣轉譯功能 **[!UICONTROL Deliverability]** 模組。
>
>有關詳細資訊，請參閱 [使用外部收件者表格](using-an-external-recipient-table.md) 和 [收件匣轉譯](inbox-rendering.md).

對於傳送，您也可以自訂將位址插入解壓縮檔案的方式。 依預設，它們會以輸出檔案的排序順序插入，但您可以選取在檔案的結尾或開頭插入，或在主要目標的收件者之間隨機插入。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 行銷活動中的種子地址 {#seed-addresses-in-a-campaign}

若要將種子地址新增至促銷活動的目標，請選取操作，然後按一下 **[!UICONTROL Edit]** 標籤。

按一下 **[!UICONTROL Advanced campaign settings...]** 連結，然後 **[!UICONTROL Seed addresses]** 標籤，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

從促銷活動插入的種子地址將新增至促銷活動中每個傳送的目標。
