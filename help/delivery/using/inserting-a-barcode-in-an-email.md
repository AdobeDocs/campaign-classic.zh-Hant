---
product: campaign
title: 在電子郵件中插入條形碼
description: 在電子郵件中插入條形碼
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# 在電子郵件中插入條形碼{#insert-a-barcode-in-an-email}

![](../../assets/common.svg)

條形碼生成模組允許您建立符合許多常見標準的幾種條形碼，包括2D條形碼。

可以使用使用客戶標準定義的值動態地將條形碼生成為點陣圖。 個性化條形碼可以包含在電子郵件活動中。 收件人可以打印郵件並將其顯示給發卡公司進行掃描（例如，簽出時）。

要將條形碼插入電子郵件，請將游標置於要顯示它的內容中，然後按一下個性化按鈕。 選取 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然後配置以下元素以滿足您的需要：

1. 選擇條形碼類型。

   * 對於1D格式，以下類型在Adobe Campaign提供：代碼128、GS1-128（前稱EAN-128）、UPC-A、UPC-E、ISBN、EAN-8、Code39、5的交錯2、POSTNET和皇家郵件(RM4SCC)。

      1D條形碼示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417類型涉及2D格式。

      2D條形碼示例：

      ![](assets/barcode_insert_09.png)

   * 要插入QR碼，請選擇此類型並輸入要應用的糾錯率。 此速率定義重複資訊的數量和對劣化的容忍度。

      ![](assets/barcode_insert_06.png)

      QR代碼示例：

      ![](assets/barcode_insert_12.png)

1. 輸入要插入電子郵件的條形碼的大小：通過配置比例，可以將條形碼的大小從x1增加或減小到x10。
1. 的 **[!UICONTROL Value]** 欄位中，您可以定義條形碼的值。 值可以與特別優惠相匹配，也可以是標準的函式，也可以是連結到客戶的資料庫欄位的值。

   此示例顯示EAN-8類型條形碼，該條形碼已添加收件人的帳號。 要添加此帳號，請按一下「 **[!UICONTROL Value]** 選擇 **[!UICONTROL Recipient > Account number]**。

   ![](assets/barcode_insert_15.png)

1. 的 **[!UICONTROL Height]** 欄位中，您可以通過更改每個條形之間的間距來配置條形碼的高度，而不更改其寬度。

   根據條形碼的類型，沒有限制性輸入控制。 如果條形碼值不正確，則只能在 **預覽** 將條形碼以紅色划出的模式。

   >[!NOTE]
   >
   >分配給條形碼的值取決於其類型。 例如，EAN-8類型的數字應恰好為8。
   >
   >「Personalization（個性化）」按鈕 **[!UICONTROL Value]** 欄位中，除了值本身之外，還可添加資料。 這豐富了條形碼，前提是條形碼標準接受它。
   >
   >例如，如果您使用的是GS1-128類型條形碼，並且除了輸入值外，還要輸入收件人的帳號，請按一下個性化按鈕並選擇 **[!UICONTROL Recipient > Account number]**。 如果正確輸入了所選收件人的帳號，則條形碼將其考慮在內。

配置完這些元素後，您就可以完成電子郵件併發送。 要避免錯誤，請始終通過按一下 **[!UICONTROL Preview]** 頁籤。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果條形碼的值不正確，則其點陣圖將以紅色划出。

![](assets/barcode_insert_11.png)
