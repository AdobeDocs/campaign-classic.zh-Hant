---
title: 在電子郵件中插入條形碼
seo-title: 在電子郵件中插入條形碼
description: 在電子郵件中插入條形碼
seo-description: null
page-status-flag: never-activated
uuid: 61f9d8ea-38b0-46a5-8085-b6f34f8559f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 679b9ae2-362c-483d-acb8-47bc01928541
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 在電子郵件中插入條形碼{#inserting-a-barcode-in-an-email}

條碼產生模組可讓您建立數種符合許多常見標準的條碼，包括2D條碼。

可以使用使用客戶標準定義的值動態生成條形碼作為點陣圖。 個人化條碼可以包含在電子郵件宣傳中。 收件者可列印訊息並將它顯示給發行公司以進行掃描（例如，當結帳時）。

若要將條形碼插入電子郵件中，請將游標置於要顯示該條形碼的內容中，然後按一下個人化按鈕。 Select **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

然後設定下列元素以符合您的需求：

1. 選擇條形碼類型。

   * 對於1D格式，Adobe Campaign提供下列類型：Codabar, Code 128, GS1-128（之前稱為EAN-128）, UPC-A, UPC-E, ISBN, EAN-8, Code39, Interable 2 of 5, POSTNET和Royal Mail(RM4SCC)。

      1D條形碼示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417類型與2D格式有關。

      2D條碼範例：

      ![](assets/barcode_insert_09.png)

   * 若要插入QR Code，請選取此類型並輸入要套用的糾錯率。 此比率定義了重複的資訊量和惡化容限。

      ![](assets/barcode_insert_06.png)

      QR code範例：

      ![](assets/barcode_insert_12.png)

1. 輸入要插入到電子郵件中的條形碼的大小：配置比例可讓您將條形碼的大小從x1增加或減小到x10。
1. 該 **[!UICONTROL Value]** 欄位允許您定義條形碼的值。 值可以與特殊選件相符，也可以是標準的函式，也可以是連結至客戶的資料庫欄位的值。

   此示例顯示了EAN-8類型條形碼，該條形碼已添加到收件者的帳戶號。 若要新增此帳戶號碼，請按一下欄位右側的個人化按 **[!UICONTROL Value]** 鈕並選取 **[!UICONTROL Recipient > Account number]**。

   ![](assets/barcode_insert_15.png)

1. 此 **[!UICONTROL Height]** 欄位可讓您設定條碼的高度，而不需變更其寬度，方法是變更每個條條之間的間距。

   根據條形碼類型，沒有限制條目控制。 如果條形碼值不正確，則只會在「預覽」模式中顯示該值，在 **「預覽** 」模式中，條形碼將以紅色划出。

   >[!NOTE]
   >
   >分配給條形碼的值取決於其類型。 例如，EAN-8類型的數字恰好為8。
   >
   >欄位右側的個人化按鈕 **[!UICONTROL Value]** 可讓您除了新增值本身以外，還新增資料。 這豐富了條形碼，前提是條形碼標準接受它。
   >
   >例如，如果您使用GS1-128類型的條形碼，並且除了要輸入值之外還要輸入收件人的帳戶號，請按一下個性化按鈕並選擇 **[!UICONTROL Recipient > Account number]**。 如果正確輸入了選定收件人的帳戶號碼，條形碼會將其納入考慮範圍。

在設定好這些元素後，您就可以完成電子郵件並傳送。 若要避免錯誤，請務必在按一下標籤執行傳送前，先確定您的內容已正確 **[!UICONTROL Preview]** 顯示。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果條形碼的值不正確，其點陣圖將以紅色交叉顯示。

![](assets/barcode_insert_11.png)
