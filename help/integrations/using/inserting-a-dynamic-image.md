---
product: campaign
title: 插入動態影像
description: 插入動態影像
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 3%

---

# 插入Target動態內容 {#inserting-a-dynamic-image}



在本頁面中，瞭解如何將Adobe Target的動態優惠方案整合到Adobe Campaign的電子郵件中。

目標是使用影像區塊來建立傳遞，該區塊會根據收件者的國家/地區動態變更：資料會隨每個mbox請求傳送，且取決於收件者的IP位址。

在此訊息中，影像可根據下列使用者體驗動態變化：

* 電子郵件會在法國開啟。
* 此電子郵件於美國開啟。
* 如果這些條件都不適用，則會顯示預設影像。

![](assets/target_4.png)

若要執行此動作，請套用下列步驟：

1. [在電子郵件中插入動態優惠方案](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [建立重新導向選件](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [建立對象](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [建立體驗鎖定目標活動](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [預覽和傳送電子郵件](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## 在電子郵件中插入動態優惠方案 {#inserting-dynamic-offer}

在Adobe Campaign中，定義完電子郵件的目標和內容後，您就可以從Target插入動態影像。

若要這麼做，請指定預設影像的URL、位置名稱，以及您要傳輸至Target的欄位。

在Adobe Campaign中，有兩種方式可將Target的動態影像插入電子郵件中：

* 如果您使用數位內容編輯器，請選擇現有影像並選取 **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** （從工具列）。

   ![](assets/target_5.png)

* 如果您使用標準編輯器，請將游標置於要插入影像的位置，然後選取 **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** 從「個人化」下拉式功能表。

   ![](assets/target_12.png)

### 定義影像引數 {#defining-image-parameters}

* 此 **[!UICONTROL Default image]**&#x200B;的URL：不符合任何條件時顯示的影像。 您也可以從「資產」資料庫中選取影像。
* 此 **[!UICONTROL Target location]**：輸入動態選件位置的名稱。 您必須在Target活動中選取此位置。
* 此 **[!UICONTROL Landing Page]**：如果您要將預設影像重新導向至預設登陸頁面。 此URL僅適用於預設影像顯示在最終電子郵件中的情況，且為選用。
* 此 **[!UICONTROL Additional decision parameters]**：指定Adobe Target區段中所定義欄位與Adobe Campaign欄位之間的對應。 使用的Adobe Campaign欄位必須在rawbox中指定。 在我們的範例中，我們新增了「國家/地區」欄位。

如果您在Adobe Target的設定中使用企業許可權，請在此欄位中新增對應的屬性。 若要深入瞭解Target企業許可權，請參閱 [此頁面](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html).

![](assets/target_13.png)

## 建立重新導向選件 {#create-redirect-offers}

在Target中，您可以建立不同版本的選件。 根據每個使用者體驗，可以建立重新導向選件，而且您可以指定要顯示的影像。

在我們的案例中，我們需要兩個重新導向選件，第三個選件（預設一個）將在Adobe Campaign中定義。

1. 若要在Target Standard中建立新的重新導向選件，請從 **[!UICONTROL Content]** 標籤，按一下 **[!UICONTROL Code offers]**.

1. 按一下 **[!UICONTROL Create]**，之後 **[!UICONTROL Redirect Offer]**。

   ![](assets/target_9.png)

1. 輸入選件的名稱和影像的URL。

   ![](assets/target_6.png)

1. 對其餘的重新導向選件執行相同的程式。 如需關於此項目的詳細資訊，請參閱此[頁面](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html)。

## 建立對象 {#audiences-target}

在Target中，您需要建立兩個受眾，造訪您選件的人員將針對要傳送的不同內容分類到這兩個受眾中。 針對每個對象，新增規則以定義能夠檢視選件的對象。

1. 若要在Target中建立新對象，請從 **[!UICONTROL Audiences]** 標籤，按一下 **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. 新增名稱至您的對象。

   ![](assets/audiences_2.png)

1. 按一下 **[!UICONTROL Add a rule]** 並選取類別。 規則會使用特定條件來鎖定訪客。 您可以藉由新增條件或在其他類別中建立新規則來調整規則。

1. 對其餘對象執行相同的程式。

## 建立體驗鎖定目標活動 {#creating-targeting-activity}

在Target中，我們需要建立體驗鎖定目標活動、定義不同的體驗，並將其與對應的選件建立關聯。

### 定義對象 {#defining-the-audience}

1. 若要建立體驗鎖定目標活動，請從 **[!UICONTROL Activities]** 標籤，按一下 **[!UICONTROL Create Activity]** 則 **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. 選取 **[!UICONTROL Form]** 作為 **[!UICONTROL Experience Composer]**.

1. 按一下「 」以選擇對象 **[!UICONTROL Change audience]** 按鈕。

   ![](assets/target_10_2.png)

1. 選取在先前步驟中建立的對象。

   ![](assets/target_10_3.png)

1. 按一下以建立其他體驗 **[!UICONTROL Add Experience Targeting]**.

### 定義位置和內容 {#defining-location-content}

為每個對象新增內容：

1. 選取您在Adobe Campaign中插入動態選件時選擇的位置名稱。

   ![](assets/target_15.png)

1. 按一下下拉式按鈕並選取 **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. 選取您先前建立的重新導向選件。

   ![](assets/target_content_2.png)

1. 對第二個體驗執行相同的步驟。

### 定義活動 {#defining-activity}

此 **[!UICONTROL Target]** 視窗會摘要列出您的活動。 如有需要，您可以新增其他體驗。

![](assets/target_experience.png)

此 **[!UICONTROL Goal & Settings]** 視窗可讓您透過設定優先順序、目標或持續時間來個人化您的活動。

此 **[!UICONTROL Reporting Settings]** 區段可讓您選取動作並編輯將決定何時實現目標的引數。

![](assets/target_experience_2.png)

## 預覽和傳送電子郵件 {#preview-send-email}

在Adobe Campaign中，您現在可以預覽電子郵件，並測試其對不同收件者的轉譯。 您會注意到影像會根據建立的不同體驗而變更。 若要瞭解有關建立電子郵件的詳細資訊，請參閱此 [頁面](../../delivery/using/defining-the-email-content.md).

您現在已準備好傳送包含Target動態優惠方案的電子郵件。

![](assets/target_20.png)
