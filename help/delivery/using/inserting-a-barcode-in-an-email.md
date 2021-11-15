---
product: campaign
title: 在電子郵件中插入條形碼
description: 在電子郵件中插入條形碼
audience: delivery
content-type: reference
topic-tags: sending-emails
source-git-commit: 3b8d685642fc74d918a0e312c66d5e4f7b424192
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# 在電子郵件中插入條形碼{#insert-a-barcode-in-an-email}

![](../../assets/common.svg)

條碼產生模組可讓您建立符合許多常見標準的數種條碼，包括2D條碼。

可以使用使用客戶條件定義的值以點陣圖形式動態生成條形碼。 電子郵件行銷活動中可包含個人化條碼。 收件者可以列印訊息，並將其顯示給發行公司以進行掃描（例如當結帳時）。

若要將條碼插入電子郵件中，請將游標置於您要顯示該條碼的內容中，然後按一下個人化按鈕。 選取 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然後設定下列元素以符合您的需求：

1. 選擇條形碼的類型。

   * 若為1D格式，可在Adobe Campaign中使用下列類型：Codabar，代碼128, GS1-128（前身為EAN-128）, UPC-A, UPC-E, ISBN, EAN-8，代碼39，交錯2 of 5, POSTNET和Royal Mail(RM4SCC)。

      1D條形碼的示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417類型與2D格式有關。

      2D條形碼的示例：

      ![](assets/barcode_insert_09.png)

   * 若要插入QR碼，請選取此類型並輸入要套用的糾錯率。 This rate defines the quantity of information repeated and the tolerance to deterioration.

      ![](assets/barcode_insert_06.png)

      QR碼範例：

      ![](assets/barcode_insert_12.png)

1. 輸入要插入電子郵件的條形碼的大小：配置刻度可以從x1增加或縮小條形碼的大小，從x1增加到x10。
1. 此 **[!UICONTROL Value]** 欄位可讓您定義條碼的值。 值可以符合特殊選件，也可以是條件的函式，也可以是連結至客戶之資料庫欄位的值。

   此示例顯示了EAN-8類型的條形碼，該條形碼已添加到收件者的帳號。 若要新增此帳號，請按一下 **[!UICONTROL Value]** 欄位和選取 **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. 此 **[!UICONTROL Height]** 欄位可讓您變更每個列之間的空間量，以設定條碼的高度，而不變更其寬度。

   根據條碼類型，沒有限制的輸入控制項。 如果條碼值不正確，則只會顯示在 **預覽** 以紅色將條形碼交叉的模式。

   >[!NOTE]
   >
   >分配給條形碼的值取決於其類型。 例如，EAN-8類型應正好有8個數字。
   >
   >The personalization button to the right of the **[!UICONTROL Value]** field lets you add data in addition to the value itself. 這豐富了條碼，前提是條碼標準接受它。
   >
   >例如，如果您使用GS1-128類型條形碼，並且除了要輸入值之外還要輸入收件人的帳戶號，請按一下個性化按鈕並選擇 **[!UICONTROL Recipient > Account number]**. 如果正確輸入了所選收件人的帳號，則條形碼會將其考慮在內。

設定這些元素後，您就可以完成電子郵件並傳送。 若要避免錯誤，請一律確定您的內容在執行傳送前，按一下 **[!UICONTROL Preview]** 標籤。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果條形碼的值不正確，則其點陣圖會以紅色交叉顯示。

![](assets/barcode_insert_11.png)
