---
product: campaign
title: 在電子郵件中插入條碼
description: 在電子郵件中插入條碼
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Email Design
role: User
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# 在電子郵件中插入條碼{#insert-a-barcode-in-an-email}

條碼產生模組可讓您建立符合許多常見標準的幾種條碼，包括2D條碼。

您可以使用使用客戶條件定義的值，動態產生條碼做為點陣圖。 電子郵件行銷活動中可包含個人化條碼。 收件者可以列印訊息，並展示給發行公司以供掃描（例如結帳時）。

若要將條碼插入電子郵件中，請將游標置於您要顯示它的內容中，然後按一下個人化按鈕。 選取 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然後設定以下元素以符合您的需求：

1. 選取條碼型別。

   * 對於1D格式，Adobe Campaign提供下列型別：Codabar、代碼128、GS1-128 （先前稱為EAN-128）、UPC-A、UPC-E、ISBN、EAN-8、代碼39、交錯式2 （共5個）、POSTNET和皇家郵件(RM4SCC)。

     1D條碼範例：

     ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417型別涉及2D格式。

     2D條碼範例：

     ![](assets/barcode_insert_09.png)

   * 若要插入QR碼，請選取此型態並輸入要套用的錯誤更正率。 此比率定義重複資訊的數量以及劣化的容許度。

     ![](assets/barcode_insert_06.png)

     QR碼範例：

     ![](assets/barcode_insert_12.png)

1. 輸入您要插入電子郵件中的條碼大小：設定比例可讓您增加或減少條碼大小，從x1到x10。
1. 此 **[!UICONTROL Value]** 欄位可讓您定義條碼的值。 值可以比對特殊優惠方案，也可以是條件的函式，也可以是連結至客戶的資料庫欄位的值。

   此範例顯示EAN-8型別條碼，收件者的帳號已加入條碼。 若要新增此帳號，請按一下 **[!UICONTROL Value]** 欄位並選取 **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. 此 **[!UICONTROL Height]** 欄位可讓您設定條碼的高度，而不變更其寬度，方法是變更每個條之間的間距量。

   根據條碼型別，沒有限制性的進入控制。 如果條碼值不正確，它將只會顯示在 **預覽** 將條碼以紅色交叉的模式。

   >[!NOTE]
   >
   >指定給條碼的值取決於其型別。 例如，EAN-8型別應該有8個數字。
   >
   >右側的個人化按鈕 **[!UICONTROL Value]** 欄位可讓您在值本身之外新增資料。 只要條碼標準接受，這就能豐富條碼。
   >
   >例如，如果您使用GS1-128型別條碼，且除了輸入值外，還想輸入收件者的帳號，請按一下個人化按鈕，然後選取 **[!UICONTROL Recipient > Account number]**. 如果所選取收件者的帳號輸入正確，條碼會將其列入考量。

設定這些元素後，您就可以完成電子郵件並加以傳送。 為避免錯誤，請一律確保內容顯示正確，然後再按一下 **[!UICONTROL Preview]** 標籤。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果條碼的值不正確，其點陣圖會以紅色劃掉。

![](assets/barcode_insert_11.png)
