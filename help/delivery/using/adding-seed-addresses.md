---
title: 添加種子地址
seo-title: 添加種子地址
description: 添加種子地址
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 添加種子地址{#adding-seed-addresses}

## 遞送中的種子地址 {#seed-addresses-in-a-delivery}

要為傳送添加特定種子地址，請按一下鏈 **[!UICONTROL To]** 接，然後選擇選 **[!UICONTROL Seed addresses]** 項卡。

![](assets/s_ncs_user_edit_del_addresses_tab.png)

有三種可能的插入模式：

1. 輸入單個種子地址。

   若要這麼做，請按一 **[!UICONTROL Add]** 下按鈕並定義位址欄位的內容。 對每個地址重複。 如需詳細資訊，請參閱[本小節](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address)。

1. 匯入地址範本並加以調整，以符合您的需求。

   要執行此操作，請按一下鏈 **[!UICONTROL Import seed templates...]** 接並選擇包含地址模板的資料夾。 有關詳細資訊，請參閱創 [建種子地址模板](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)。

   如有必要，在新增這些內容後，您可以按兩下，或按一 **[!UICONTROL Detail...]** 下按鈕以調整每個位址的內容。

1. 建立條件以動態選擇要插入的控制地址。

   要執行此操作，請按一下鏈 **[!UICONTROL Edit the dynamic condition...]** 接，然後輸入種子地址選擇參數。 例如，您可以包含特定資料夾中包含的所有種子位址，或您組織中屬於特定部門的種子位址。

   本節將介紹此示例：使 [用案例：選擇條件上的種子地址](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)。

>[!NOTE]
>
>當使用的收件者表不是預設的 **nms:recipient** 表，而您使用Adobe Campaign模組隨附的「收件匣轉譯」功能時，就會使用此 **[!UICONTROL Deliverability]** 選項。
>
>有關詳細資訊，請參 [閱「使用外部收件者表](../../delivery/using/using-an-external-recipient-table.md) 」和「收件箱」 [渲染的文檔](../../delivery/using/inbox-rendering.md)。

對於傳送，您也可以自訂地址插入提取檔案的方式。 預設情況下，它們會按輸出檔案的排序順序插入，但您可以選擇將它們插入到檔案的末尾或開頭，或在主目標的收件人之間隨機插入。

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 促銷活動中的種子位址 {#seed-addresses-in-a-campaign}

若要將種子位址新增至促銷活動的目標，請選取該作業，然後按一下標 **[!UICONTROL Edit]** 簽。

按一下 **[!UICONTROL Advanced campaign settings...]** 連結，然後按一 **[!UICONTROL Seed addresses]** 下標籤，如下所示：

![](assets/s_ncs_user_edit_op_addresses_tab.png)

從促銷活動插入的種子位址將新增至促銷活動中每個傳送的目標。
