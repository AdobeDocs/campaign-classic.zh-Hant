---
product: campaign
title: 使用實例：設定欄位替代
description: 使用實例：設定欄位替代
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 5%

---

# 使用實例：設定欄位替代{#use-case-configuring-the-field-substitution}



隨機欄位替代可讓您將收件者清單中的值歸因於使用者在傳送中使用此值時為空的種子地址（例如：名稱、城市等）。

此替代可讓您在建立傳送時節省時間：替代不會手動將所需值新增至種子地址，而是在傳送鎖定的收件者清單中隨機復原此值，並將其套用至種子地址。

## 內容 {#context}

在此使用案例中，網站&#x200B;**我的線上資料庫**&#x200B;想要根據客戶最喜愛的文學型別，向客戶傳送折扣。

傳遞管理員已將連結至最喜愛型別的個人化欄位整合至其電子郵件。 目的是使用一些種子地址：這些種子地址在表格中有個人化欄位，但沒有儲存任何值。

若要使用隨機欄位替代，您必須具備：

* 包含一或多個個人化欄位的傳遞，
* 根據傳遞中使用的個人化欄位，修改其&#x200B;**資料結構描述**&#x200B;的種子位址。

## 建立傳遞 {#step-1---creating-a-delivery}

建立傳遞的步驟已詳載於[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=zh-Hant){target="_blank"}。

在此範例中，傳遞管理員已建立電子報。

![](assets/dlv_seeds_usecase_24.png)

## 編輯種子地址資料結構 {#editing-the-seed-addresses-data-schema}

有關如何修改資料結構的指示會在一節中詳細說明。

在此範例中，種子地址資料方案會採用從收件者資料方案建立的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此分項清單可讓使用者指定其客戶最喜愛的文學型別。

若要讓此資料結構描述修改可在種子地址&#x200B;**輸入表單**&#x200B;中檢視，您必須更新它。 請參閱[更新輸入表單](use-case-selecting-seed-addresses-on-criteria.md#updating-the-input-form)區段。

## 設定個人化 {#configuring-personalization}

1. 開啟傳遞。

   在此範例中，傳遞有兩個個人化欄位：收件者的&#x200B;**名字**&#x200B;和收件者的&#x200B;**最喜愛的文學型別**。

   ![](assets/dlv_seeds_usecase_25.png)

1. 設定您的傳遞清單和種子地址。 請參閱[識別目標母體](steps-defining-the-target-population.md)。

   在此範例中，使用者會選取&#x200B;**最喜愛的文學型別**&#x200B;為Sci-Fi的使用者作為主要目標母體。

   ![](assets/dlv_seeds_usecase_26.png)

   使用者將種子地址新增到傳遞。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >如需&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結的詳細資訊，請參閱[使用案例：選取條件上的種子地址](use-case-selecting-seed-addresses-on-criteria.md)。

1. 按一下「**[!UICONTROL Preview]**」標籤，然後選取種子地址以測試個人化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一個個人化欄位是空的。 由於種子地址沒有此欄位的資料，因此HTML內容預覽無法顯示值。

   在傳遞&#x200B;**時**&#x200B;執行隨機替代欄位。

1. 按一下 **[!UICONTROL Send]** 按鈕。
1. 分析您的傳遞，然後&#x200B;**確認傳遞**。

   種子地址會在收件匣中接收傳遞。

   欄位個人化有效。

   ![](assets/dlv_seeds_usecase_08.png)
