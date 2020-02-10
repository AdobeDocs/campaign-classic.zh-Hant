---
title: 「使用案例：配置欄位替代"
seo-title: 「使用案例：配置欄位替代"
description: 「使用案例：配置欄位替代"
seo-description: null
page-status-flag: never-activated
uuid: 7f083dc6-e6d7-4eea-ac66-87674716515c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: a104fcab-75e6-4d73-bc3d-88570de6df7f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 003bac4c5d89290b9d3653d6ddfab7284b68642d

---


# 使用案例：配置欄位替代{#use-case-configuring-the-field-substitution}

隨機欄位替代可讓您將收件者清單中的值歸因於使用者在傳送中使用此值時的種子地址空白(例如：名稱、城市等)。

此替代可讓您在建立傳送時節省時間：替代不會手動將所需值新增至種子位址，而是會在遞送鎖定的收件者清單中隨機恢復此值，並將其套用至種子位址。

## 內容 {#context}

在此使用案例中，「我的 **線上圖書館** 」網站會根據客戶喜愛的文學類型，向其客戶提供折扣。

遞送經理將個人化領域與他的電子郵件中最喜愛的類型整合。 他想用一些種子地址。 這些種子地址在其表中具有個人化欄位，但不保存任何值。

要使用隨機欄位替代，您必須具有：

* 一個或多個個人化欄位，
* 其資料 **結構** ，會根據傳送中使用的個人化欄位修改種子位址。

## 建立傳送 {#step-1---creating-a-delivery}

建立傳送的步驟在「建立電子郵件傳送 [」區段中詳述](../../delivery/using/creating-an-email-delivery.md) 。

在此範例中，傳送管理員已建立電子報。

![](assets/dlv_seeds_usecase_24.png)

## 編輯種子地址資料模式 {#editing-the-seed-addresses-data-schema}

有關如何修改資料模式的說明，請參見一節。

在此示例中，種子地址資料模式採用從收件人資料模式建立的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此列舉可讓使用者指定其客戶最喜愛的文學類型。

要在種子地址輸入表單中查看此資料模式修 **改**，必須更新它。 請參閱「更 [新輸入表單](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) 」一節。

## 設定個人化 {#configuring-personalization}

1. 開啟傳送。

   在此範例中，傳送包含兩個個人化欄位：收件者的名 **字** ，以及收件者最喜 **歡的文學類型**。

   ![](assets/dlv_seeds_usecase_25.png)

1. 設定傳送清單和種子位址。 請參閱 [識別目標人口族群](../../delivery/using/steps-defining-the-target-population.md)。

   在此範例中，使用者選擇其最 **愛的文學類型** Sci-Fi的使用者為主要目標群體。

   ![](assets/dlv_seeds_usecase_26.png)

   用戶向傳送添加種子地址。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >如需連結的詳細資 **[!UICONTROL Edit the dynamic condition...]** 訊，請參閱使 [用案例：選擇條件上的種子地址](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)。

1. 按一下標 **[!UICONTROL Preview]** 簽，然後選取種子地址以測試個人化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一個個人化欄位是空的。 由於種子地址沒有此欄位的資料，因此HTML內容預覽無法顯示值。

   場的隨機替換是在發 **送時進行的**。

1. Click the **[!UICONTROL Send]** button.
1. 分析您的傳送，然後 **確認傳送**。

   種子地址將接收其收件箱中的發送。

   現場個人化非常有效。

   ![](assets/dlv_seeds_usecase_08.png)
