---
product: campaign
title: "使用實例：依條件選取種子地址"
description: "使用實例：依條件選取種子地址"
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 3%

---

# 使用實例：依條件選取種子地址{#use-case-selecting-seed-addresses-on-criteria}



在傳遞或行銷活動的架構中， **[!UICONTROL Edit the dynamic condition...]** 連結可讓您根據特定選擇條件選擇種子地址。

在此使用案例中，網站 **我的線上圖書館** 想根據客戶的文學品味，個人化電子報。

與採購部門一起，負責交付的用戶為購買了警察小說的訂閱者建立了電子報。

為了分享與他們協作的最終結果，交付經理決定將他們的同事從採購部門添加到交付中，作為種子地址。 使用動態條件可讓您節省配置和更新地址的時間。

若要使用動態條件，您必須具備：

* 已準備好傳送，
* 具有共同值的種子地址。 此值可以是Adobe Campaign中已存在的欄位。 在此示例中，種子地址共用「部門」欄位中的「採購」值，預設情況下，該值不存在於應用程式中。

## 步驟1 — 建立傳送 {#step-1---creating-a-delivery}

建立傳送的步驟在 [建立電子郵件傳送](creating-an-email-delivery.md) 區段。

在此範例中，傳送管理員已建立電子報並選取收件者。

![](assets/dlv_seeds_usecase_01.png)

## 步驟2 — 建立公用值 {#step-2---creating-a-common-value}

若要建立與範例（Oracle Purchasing部門）中相同的通用值，您必須先將 **資料結構** ，並編輯相關的輸入表單。

### 擴充資料結構 {#extending-the-data-schema}

如需結構擴充功能的詳細資訊，請參閱 [本節](../../configuration/using/data-schemas.md).

1. 在 **[!UICONTROL Administration > Configuration > Data schemas]** 節點，按一下 **[!UICONTROL New]** 表徵圖。
1. 在 **[!UICONTROL Creation of a data schema]** ，選擇 **[!UICONTROL Extension of a schema]** 選項，然後按一下 **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. 選取 **[!UICONTROL Seed addresses]** 源架構，請輸入 **doc** 作為 **[!UICONTROL Namespace]** 按一下 **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 在架構編輯視窗中，複製下方的線條，並貼到螢幕擷取畫面所示的區域中。

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   然後複製下列行並貼到 **[!UICONTROL Seed to insert in the export files]** 元素。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在此情況下，您會指定名為 **[!UICONTROL Department]** 已在種子地址表中建立，且是以標準為基礎 **[!UICONTROL @company]** 枚舉模板（在名稱下標籤） **公司** )。

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 在 **[!UICONTROL Tools > Advanced]** ，選擇 **[!UICONTROL Update database structure]** 選項。

   ![](assets/dlv_seeds_usecase_12.png)

1. 顯示更新嚮導時，按一下 **[!UICONTROL Next]** 按鈕訪問「編輯表」窗口：在種子地址資料模式中執行的更改需要結構更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 請依照精靈操作，直到到達頁面執行更新。 按一下 **[!UICONTROL Start]** 按鈕。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成後，您可以關閉精靈。

1. 斷開連接，然後重新連接到Adobe Campaign。 在種子地址資料架構中所做的變更現在已生效。 為了從種子地址螢幕中顯示它們，您必須更新關聯的 **[!UICONTROL Input form]**. 請參閱 [更新輸入表單](#updating-the-input-form) 區段。

#### 從連結的表擴展資料架構 {#extending-the-data-schema-from-a-linked-table}

種子地址資料方案可以使用來自連結到接收者資料方案 — 接收者(nms)的表的值。

例如，使用者想要整合 **[!UICONTROL Internet Extension]** 在 **[!UICONTROL Country]** 連結至收件者架構的表格。

![](assets/dlv_seeds_usecase_06.png)

因此，種子地址資料結構必須擴展，如一節所述。 不過，要在 **步驟4** 如下所示：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它們表示：

* 使用者想要建立新元素的 **[!UICONTROL Internet Extension]**,
* 這個元素來自 **[!UICONTROL Country]** 表格。

>[!CAUTION]
>
>在連結的表格名稱中，您必須指定 **xpath-dst** 連結的桌子。
>
>這可在 **[!UICONTROL Country]** 元素。

![](assets/dlv_seeds_usecase_07.png)

然後，使用者可從 **步驟5** ，並更新 **[!UICONTROL Input form]** 種子地址。

請參閱 [更新輸入表單](#updating-the-input-form) 區段。

#### 更新輸入表單 {#updating-the-input-form}

1. 在 **[!UICONTROL Administration > Configuration > Input forms]** 節點，查找種子地址輸入表單。

   ![](assets/dlv_seeds_usecase_19.png)

1. 編輯表單並在 **[!UICONTROL Recipient]** 容器。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 儲存您的變更。
1. 開啟種子地址。 此 **[!UICONTROL Department]** 欄位中 **[!UICONTROL Recipient]** 表格。

   ![](assets/dlv_seeds_usecase_22.png)

1. 編輯要用於傳送的種子地址，然後輸入 **購買** 作為 **[!UICONTROL Department]** 欄位。

## 步驟3 — 定義條件 {#step-3---defining-the-condition}

您現在可以指定傳送種子地址的動態條件。 操作步驟：

1. 開啟傳遞。

   ![](assets/dlv_seeds_usecase_01.png)

1. 按一下 **[!UICONTROL To]** 連結，然後 **[!UICONTROL Seed addresses]** 標籤來存取 **[!UICONTROL Edit the dynamic condition...]** 連結。

   ![](assets/dlv_seeds_usecase_02.png)

1. 選取可讓您選擇所需種子地址的運算式。 在此，使用者會選取 **[!UICONTROL Department (@workField)]** 運算式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 選取您想要的值。 在此範例中，使用者會選取 **購買** 值下拉式清單中的部門。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >先前建立的結構擴充功能來自 **收件者** 綱要。 上方螢幕上顯示的值來自 **收件者** 綱要。

1. 按一下&#x200B;**[!UICONTROL Ok]**。

   查詢會顯示在 **[!UICONTROL Select target]** 窗口。

   ![](assets/dlv_seeds_usecase_04.png)

1. 按一下 **[!UICONTROL Ok]** 以批准查詢。
1. 分析您的傳送，然後按一下 **[!UICONTROL Delivery]** 標籤來存取傳送記錄檔。

   採購部門的種子地址顯示為待交付，與接收方的種子地址或其他種子地址一樣。

   ![](assets/dlv_seeds_usecase_05.png)

1. 按一下 **[!UICONTROL Send]** 按鈕以開始傳送。

   購買部門的成員構成種子地址的一部分，這些種子地址將在其電子郵件收件箱中接收傳遞內容。

   ![](assets/dlv_seeds_usecase_18.png)
