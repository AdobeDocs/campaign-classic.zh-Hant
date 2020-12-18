---
solution: Campaign Classic
product: campaign
title: '"使用案例：配置欄位替代"'
description: '"使用案例：配置欄位替代"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---


# 使用案例：配置欄位替代{#use-case-configuring-the-field-substitution}

隨機欄位替代可讓您將收件者清單中的值歸因於使用者在傳送中使用此值時的種子地址空白(例如：名稱、城市等)。

此替代可讓您在建立傳送時節省時間：替代不會手動將所需值新增至種子位址，而是會在遞送鎖定的收件者清單中隨機恢復此值，並將其套用至種子位址。

## 內容 {#context}

在此使用案例中，網站&#x200B;**My online library**&#x200B;會根據客戶喜愛的文學類型，向客戶寄送折扣。

遞送經理將個人化領域與他的電子郵件中最喜愛的類型整合。 他想用一些種子地址。 這些種子地址在其表中具有個人化欄位，但不保存任何值。

要使用隨機欄位替代，您必須具有：

* 一個或多個個人化欄位，
* 根據傳送中使用的個人化欄位修改&#x200B;**資料模式**&#x200B;的種子地址。

## 建立傳送{#step-1---creating-a-delivery}

建立傳送的步驟詳見[建立電子郵件傳送](../../delivery/using/creating-an-email-delivery.md)一節。

在此範例中，傳送管理員已建立電子報。

![](assets/dlv_seeds_usecase_24.png)

## 編輯種子地址資料方案{#editing-the-seed-addresses-data-schema}

有關如何修改資料模式的說明，請參見一節。

在此示例中，種子地址資料模式採用從收件人資料模式建立的值：

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

此列舉可讓使用者指定其客戶最喜愛的文學類型。

要在種子地址&#x200B;**輸入表單**&#x200B;中查看此資料模式修改，您必須更新它。 請參閱[更新輸入表單](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form)一節。

## 配置個人化{#configuring-personalization}

1. 開啟傳送。

   在此範例中，傳送包含兩個個人化欄位：收件者的&#x200B;**名字**&#x200B;和收件者的&#x200B;**最愛的文學類型**。

   ![](assets/dlv_seeds_usecase_25.png)

1. 設定傳送清單和種子位址。 請參閱[識別目標人口](../../delivery/using/steps-defining-the-target-population.md)。

   在此範例中，使用者選擇&#x200B;**最喜愛的文學類型**&#x200B;為Sci-Fi的使用者作為主要目標群體。

   ![](assets/dlv_seeds_usecase_26.png)

   用戶將種子地址添加到傳送中。

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >有關&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結的詳細資訊，請參閱[使用案例：選擇條件](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)上的種子地址。

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤，然後選取種子地址以測試個人化。

   ![](assets/dlv_seeds_usecase_28.png)

   您可以看到其中一個個人化欄位是空的。 由於種子地址沒有此欄位的資料，因此HTML內容預覽無法顯示值。

   在傳送時執行域的隨機替換&#x200B;**。**

1. 按一下 **[!UICONTROL Send]** 按鈕。
1. 先分析您的傳送，然後&#x200B;**確認傳送**。

   種子地址將接收其收件箱中的發送。

   現場個人化非常有效。

   ![](assets/dlv_seeds_usecase_08.png)
