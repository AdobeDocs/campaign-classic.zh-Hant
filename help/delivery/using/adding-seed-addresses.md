---
solution: Campaign Classic
product: campaign
title: 新增種子地址
description: 新增種子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 6%

---


# 添加種子地址{#adding-seed-addresses}

## 傳送{#seed-addresses-in-a-delivery}中的種子地址

要為傳送添加特定種子地址，請按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，然後選擇&#x200B;**[!UICONTROL Seed addresses]**&#x200B;頁籤。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三種可能的插入模式：

1. 輸入單個種子地址。

   要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並定義地址欄位的內容。 對每個地址重複。 如需詳細資訊，請參閱[本章節](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address)。

1. 匯入地址範本並加以調整，以符合您的需求。

   要執行此操作，請按一下&#x200B;**[!UICONTROL Import seed templates...]**&#x200B;連結，然後選擇包含地址模板的資料夾。 如需詳細資訊，請參閱[本章節](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，在新增這些項目後，您可以按兩下，或按一下&#x200B;**[!UICONTROL Detail...]**&#x200B;按鈕以調整每個位址的內容。

1. 建立條件以動態選擇要插入的控制地址。

   要執行此操作，請按一下&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結，然後輸入種子地址選擇參數。 例如，您可以包含特定資料夾中包含的所有種子位址，或您組織中屬於特定部門的種子位址。

   本節將介紹此示例：[使用案例：選擇條件](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)上的種子地址。

>[!NOTE]
>
>當使用的收件者表不是預設的&#x200B;**nms:recipient**&#x200B;表，並且您正在使用Adobe Campaign **[!UICONTROL Deliverability]**&#x200B;模組提供的「收件箱呈現」功能時，將使用此選項。
>
>有關詳細資訊，請參閱[使用外部收件人表](../../delivery/using/using-an-external-recipient-table.md)和[收件箱呈現](../../delivery/using/inbox-rendering.md)上的文檔。

對於傳送，您也可以自訂地址插入提取檔案的方式。 預設情況下，它們會按輸出檔案的排序順序插入，但您可以選擇將它們插入到檔案的末尾或開頭，或在主目標的收件人之間隨機插入。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 促銷活動中的種子位址{#seed-addresses-in-a-campaign}

若要將種子位址新增至促銷活動的目標，請選取該操作，然後按一下&#x200B;**[!UICONTROL Edit]**&#x200B;標籤。

按一下&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Seed addresses]**&#x200B;頁籤，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

從促銷活動插入的種子位址將新增至促銷活動中每個傳送的目標。
