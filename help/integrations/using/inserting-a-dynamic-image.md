---
title: 插入動態影像
seo-title: 插入動態影像
description: 插入動態影像
seo-description: null
page-status-flag: never-activated
uuid: 4acc905e-625c-45aa-bb70-7dde22911aa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: f6e4d22b-4ad3-4a1e-8a6f-3bdfc1da0535
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f4d5d8474099776f770e88fcaf3bf15256da1be2

---


# 插入Target動態內容 {#inserting-a-dynamic-image}

在本指南中，我們將說明如何將Target的動態選件整合至Adobe Campaign的電子郵件中。

我們想要建立包含影像區塊的傳送，這些影像區塊會根據收件者的國家／地區動態變更。 資料會隨每個mbox請求傳送，並視訪客的IP位址而定。

在這封電子郵件中，我們希望其中一張影像會根據下列使用者體驗動態變更：

* 電子郵件在法國開啟。
* 電子郵件在美國開啟。
* 如果這些條件都不適用，則會顯示預設影像。

![](assets/target_4.png)

為了達到此目的，我們需要在Adobe Campaign和Target中執行下列步驟：

1. [在電子郵件中插入動態選件](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [建立重新導向選件](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [建立閱聽眾](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [建立體驗定位活動](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [預覽和傳送電子郵件](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## 在電子郵件中插入動態選件 {#inserting-dynamic-offer}

在Adobe Campaign中，定義完電子郵件的目標和內容後，您就可以從Target插入動態影像。

若要這麼做，請指定預設影像的URL、位置名稱，以及您要傳輸至Target的欄位。

在Adobe Campaign中，有兩種方法可將動態影像從Target插入電子郵件：

* 如果您使用數位內容編輯器，請選擇現有影像，然後從工具 **[!UICONTROL Insert]** 列選 **[!UICONTROL Dynamic image served by Adobe Target]** 取>。

   ![](assets/target_5.png)

* 如果您使用標準編輯器，請將游標置於要插入影像的位置，然後從個人化下拉式選單 **[!UICONTROL Include]** 中 **[!UICONTROL Dynamic image served by Adobe Target...]** 選取>。

   ![](assets/target_12.png)

### 定義影像參數 {#defining-image-parameters}

* URL **[!UICONTROL Default image]**:當未滿足任何條件時將顯示的影像。 您也可以從資產庫中選取影像。
* The **[!UICONTROL Target location]**:輸入動態選件的位置名稱。 您必須在Target活動中選取此位置。
* The **[!UICONTROL Landing Page]**:如果您想要將預設影像重新導向至預設登陸頁面。 此URL僅適用於在最終電子郵件中顯示預設影像且為選用的情況。
* The **[!UICONTROL Additional decision parameters]**:指定在Adobe Target區段中定義的欄位與Adobe Campaign欄位之間的對應。 使用的Adobe Campaign欄位必須已在rawbox中指定。 在我們的範例中，我們新增了「國家」欄位。

如果您在Adobe Target的設定中使用「企業版」權限，請在此欄位中新增對應的屬性。 在此頁面中進一步瞭解Target Enterprise [權限](https://marketing.adobe.com/resources/help/en_US/target/target/properties-overview.html)。

![](assets/target_13.png)

## 建立重新導向選件 {#create-redirect-offers}

在Target中，您可以建立不同版本的選件。 視每個使用者體驗而定，您可以建立重新導向選件，並指定要顯示的影像。

在我們的案例中，我們需要兩個重新導向選件，第三個（預設值）將在Adobe Campaign中定義。

1. 若要在Target Standard中建立新的重新導向選件，請從標籤中 **[!UICONTROL Content]** 按一下 **[!UICONTROL Code offers]**。

1. 按一 **[!UICONTROL Create]** 下 **[!UICONTROL Redirect Offer]**。

   ![](assets/target_9.png)

1. 輸入選件的名稱和影像的URL。

   ![](assets/target_6.png)

1. 請依照相同的程式，處理剩餘的重新導向選件。 For more on this, refer to this [page](https://docs.adobe.com/help/en/target/using/experiences/offers/offer-redirect.html).

## 建立閱聽眾 {#audiences-target}

在Target中，您需要建立兩個對象，造訪您選件的訪客將會針對要傳送的不同內容分類。 針對每個對象，新增規則以定義誰將能夠看見選件。

1. 若要在Target中建立新對象，請從標籤 **[!UICONTROL Audiences]** 按一下 **[!UICONTROL Create Audience]**。

   ![](assets/audiences_1.png)

1. 新增名稱至您的觀眾。

   ![](assets/audiences_2.png)

1. 按一 **[!UICONTROL Add a rule]** 下並選取類別。 規則使用特定條件來定位訪客。 您可以新增條件或在其他類別中建立新規則，以調整規則。

1. 請依照相同的程式處理其餘的觀眾。

## 建立體驗定位活動 {#creating-targeting-activity}

在Target中，我們需要建立「體驗定位」活動、定義不同的體驗，並將它們與對應的選件建立關聯。

### 定義觀眾 {#defining-the-audience}

1. 若要建立「體驗定位」活動，請從標籤中 **[!UICONTROL Activities]** 按一下，然 **[!UICONTROL Create Activity]** 後 **[!UICONTROL Experience Targeting]**。

   ![](assets/target_10.png)

1. 選擇 **[!UICONTROL Form]** 為 **[!UICONTROL Experience Composer]**。

1. 按一下按鈕以選擇對 **[!UICONTROL Change audience]** 像。

   ![](assets/target_10_2.png)

1. 選取在先前步驟中建立的對象。

   ![](assets/target_10_3.png)

1. 按一下以建立其他體驗 **[!UICONTROL Add Experience Targeting]**。

### 定義位置和內容 {#defining-location-content}

為每個觀眾新增內容：

1. 在Adobe Campaign中插入動態選件時，選取您選擇的位置名稱。

   ![](assets/target_15.png)

1. 按一下下拉式按鈕並選取 **[!UICONTROL Change Redirect Offer]**。

   ![](assets/target_content.png)

1. 選取您先前建立的重新導向選件。

   ![](assets/target_content_2.png)

1. 請依照相同的步驟進行第二個體驗。

### 定義活動 {#defining-activity}

此窗 **[!UICONTROL Target]** 口會匯總您的活動。 如有需要，您可以新增其他體驗。

![](assets/target_experience.png)

該 **[!UICONTROL Goal & Settings]** 窗口允許您通過設定優先順序、目標或持續時間來個性化活動。

該 **[!UICONTROL Reporting Settings]** 部分可讓您選取動作並編輯將決定何時達到目標的參數。

![](assets/target_experience_2.png)

## 在Campaign Classic中預覽和傳送電子郵件 {#preview-send-email}

在Adobe Campaign中，您現在可以預覽電子郵件，並對不同的收件者測試其轉換效果。 您會注意到，影像會根據建立的不同體驗而改變。 若要進一步瞭解建立電子郵件的資訊，請參 [閱本頁](../../delivery/using/defining-the-email-content.md)。

您現在已準備好傳送電子郵件，包括Target提供的動態選件。

![](assets/target_20.png)
