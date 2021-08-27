---
product: campaign
title: '"使用案例：配置欄位替代"'
description: '"使用案例：配置欄位替代"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---

# 使用案例：配置欄位替代{#use-case-configuring-the-field-substitution}

![](../../assets/common.svg)

隨機欄位替代可讓您將收件者清單中的值歸因於使用者在傳送中使用此值時的種子地址空白(範例：名稱、城市等)。

此替代可讓您在建立傳送時節省時間：替代不會手動將所需值新增至種子地址，而是會在傳遞所定位的收件者清單中隨機恢復此值，並將其套用至種子地址。

## 內容 {#context}

在此使用案例中，網站&#x200B;**我的線上資料庫**&#x200B;會根據客戶最喜愛的文學類型，向客戶傳送折扣。

傳送管理員已將與最喜愛類型連結的個人化欄位整合至其電子郵件。 他想用一些種子地址。 這些種子地址的表格中有個人化欄位，但沒有儲存任何值。

若要使用隨機欄位替代，您必須具備：

* 包含一或多個個人化欄位的傳送，
* 根據傳送中使用的個人化欄位修改&#x200B;**資料結構**&#x200B;的種子地址。

## 建立傳遞 {#step-1---creating-a-delivery}

在[建立電子郵件傳送](creating-an-email-delivery.md)區段中會詳細說明建立傳送的步驟。

在此範例中，傳送管理員已建立電子報。

![](assets/dlv_seeds_usecase_24.png)

## 編輯種子地址資料架構 {#editing-the-seed-addresses-data-schema}

有關如何修改資料架構的說明，請參閱一節。

在此範例中，種子地址資料架構採用從收件者資料架構建立的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此列舉可讓使用者指定其客戶的最喜愛文學類型。

要在種子地址&#x200B;**輸入表單**&#x200B;中查看此資料架構修改，必須更新它。 請參閱[更新輸入表單](use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form)區段。

## 設定個人化 {#configuring-personalization}

1. 開啟傳遞。

   在此範例中，傳送有兩個個人化欄位：收件者的&#x200B;**名字**&#x200B;和收件者的&#x200B;**最喜愛的文學類型**。

   ![](assets/dlv_seeds_usecase_25.png)

1. 設定您的傳送清單和種子地址。 請參閱[識別目標母體](steps-defining-the-target-population.md)。

   在此範例中，使用者選取其&#x200B;**最喜愛的文學類型**&#x200B;為Sci-Fi的使用者作為主要目標母體。

   ![](assets/dlv_seeds_usecase_26.png)

   使用者將種子地址新增至傳送。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >有關&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結的詳細資訊，請參閱[使用案例：依條件](use-case--selecting-seed-addresses-on-criteria.md)選取種子地址。

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤，然後選取種子地址以測試個人化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一個個人化欄位空白。 由於種子地址沒有此欄位的資料，因此HTML內容預覽無法顯示值。

   在傳送&#x200B;**時執行**&#x200B;欄位的隨機替代。

1. 按一下 **[!UICONTROL Send]** 按鈕。
1. 分析您的傳送，然後&#x200B;**確認傳送**。

   種子地址會在其收件匣中接收傳遞。

   欄位個人化有效。

   ![](assets/dlv_seeds_usecase_08.png)
