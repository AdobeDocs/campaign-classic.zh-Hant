---
product: campaign
title: '"使用案例：依條件選取種子地址"'
description: '"使用案例：依條件選取種子地址"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---

# 使用案例：依條件選取種子地址{#use-case-selecting-seed-addresses-on-criteria}

![](../../assets/common.svg)

在傳遞或促銷活動的架構中，**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結可讓您根據特定選擇標準選擇種子地址。

在此使用案例中，網站&#x200B;**我的線上資料庫**&#x200B;想要根據客戶的文學品味個人化其電子報。

與採購部門一起，負責交付的用戶為購買了警察小說的訂閱者建立了電子報。

為了分享與他們協作的最終結果，交貨經理決定將採購部門的同事添加到交貨中作為種子地址。 使用動態條件可讓您節省配置和更新地址的時間。

若要使用動態條件，您必須具備：

* 已準備好傳送，
* 具有共同值的種子地址。 此值可以是Adobe Campaign中已存在的欄位。 在此示例中，種子地址共用「部門」欄位中的「採購」值，預設情況下，該值不存在於應用程式中。

## 步驟1 — 建立傳遞 {#step-1---creating-a-delivery}

在[建立電子郵件傳送](creating-an-email-delivery.md)區段中會詳細說明建立傳送的步驟。

在此範例中，傳送管理員已建立電子報並選取收件者。

![](assets/dlv_seeds_usecase_01.png)

## 步驟2 — 建立通用值 {#step-2---creating-a-common-value}

若要建立與範例（採購部門）中相同的通用值，您必須先擴充種子地址的&#x200B;**資料結構**&#x200B;並編輯相關的輸入表單。

### 擴充資料結構 {#extending-the-data-schema}

有關架構擴展的詳細資訊，請參閱[配置指南](../../configuration/using/data-schemas.md)。

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;節點中，按一下&#x200B;**[!UICONTROL New]**&#x200B;圖示。
1. 在&#x200B;**[!UICONTROL Creation of a data schema]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Extension of a schema]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/dlv_seeds_usecase_09.png)

1. 選擇&#x200B;**[!UICONTROL Seed addresses]**&#x200B;源架構，輸入&#x200B;**doc**&#x200B;作為&#x200B;**[!UICONTROL Namespace]**，然後按一下&#x200B;**[!UICONTROL Ok]**。

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

   然後複製下列行並貼到&#x200B;**[!UICONTROL Seed to insert in the export files]**&#x200B;元素下。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在此情況下，您將指定已在種子地址表中建立名為&#x200B;**[!UICONTROL Department]**&#x200B;的新枚舉，該枚舉基於標準&#x200B;**[!UICONTROL @company]**&#x200B;枚舉模板（在種子地址表單中的名稱&#x200B;**公司**&#x200B;下標籤）。

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 在&#x200B;**[!UICONTROL Tools > Advanced]**&#x200B;菜單中，選擇&#x200B;**[!UICONTROL Update database structure]**&#x200B;選項。

   ![](assets/dlv_seeds_usecase_12.png)

1. 顯示更新嚮導時，按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕以訪問「編輯表」窗口：在種子地址資料模式中執行的更改需要結構更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 請依照精靈操作，直到到達頁面執行更新。 按一下 **[!UICONTROL Start]** 按鈕。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成後，您可以關閉精靈。

1. 斷開連接，然後重新連接到Adobe Campaign。 在種子地址資料架構中所做的變更現在已生效。 為了從種子地址螢幕中顯示它們，必須更新關聯的&#x200B;**[!UICONTROL Input form]**。 請參閱[更新輸入表單](#updating-the-input-form)區段。

#### 從連結的表擴展資料架構 {#extending-the-data-schema-from-a-linked-table}

種子地址資料方案可以使用來自連結到接收者資料方案 — 接收者(nms)的表的值。

例如，用戶希望整合連結到收件者架構的&#x200B;**[!UICONTROL Country]**&#x200B;表中的&#x200B;**[!UICONTROL Internet Extension]**。

![](assets/dlv_seeds_usecase_06.png)

因此，種子地址資料結構必須擴展，如一節所述。 不過，要在&#x200B;**step 4**&#x200B;整合的代碼行如下：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它們表示：

* 使用者想要建立名為&#x200B;**[!UICONTROL Internet Extension]**&#x200B;的新元素，
* 此元素來自&#x200B;**[!UICONTROL Country]**&#x200B;表格。

>[!CAUTION]
>
>在連結的表名中，必須指定該連結表的&#x200B;**xpath-dst**。
>
>這可在收件者表格的&#x200B;**[!UICONTROL Country]**&#x200B;元素中找到。

![](assets/dlv_seeds_usecase_07.png)

然後，用戶可以從節的&#x200B;**步驟5**&#x200B;執行操作，並更新種子地址的&#x200B;**[!UICONTROL Input form]**。

請參閱[更新輸入表單](#updating-the-input-form)區段。

#### 更新輸入表單 {#updating-the-input-form}

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Input forms]**&#x200B;節點中，查找種子地址輸入表單。

   ![](assets/dlv_seeds_usecase_19.png)

1. 編輯表單並在&#x200B;**[!UICONTROL Recipient]**&#x200B;容器中插入以下行。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 儲存您的變更。
1. 開啟種子地址。 **[!UICONTROL Department]**&#x200B;欄位顯示在&#x200B;**[!UICONTROL Recipient]**&#x200B;表中。

   ![](assets/dlv_seeds_usecase_22.png)

1. 編輯要用於傳送的種子地址，並在&#x200B;**[!UICONTROL Department]**&#x200B;欄位中輸入&#x200B;**Purchasing**&#x200B;作為值。

## 步驟3 — 定義條件 {#step-3---defining-the-condition}

您現在可以指定傳送種子地址的動態條件。 操作步驟：

1. 開啟傳遞。

   ![](assets/dlv_seeds_usecase_01.png)

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Seed addresses]**&#x200B;標籤以存取&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結。

   ![](assets/dlv_seeds_usecase_02.png)

1. 選取可讓您選擇所需種子地址的運算式。 在此，用戶選擇&#x200B;**[!UICONTROL Department (@workField)]**&#x200B;表達式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 選取您想要的值。 在此範例中，使用者從值下拉式清單中選取&#x200B;**Purchasing**&#x200B;部門。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >先前建立的架構擴充功能來自&#x200B;**recipient**&#x200B;架構。 上方畫面上顯示的值來自&#x200B;**recipient**&#x200B;架構的列舉。

1. 按一下&#x200B;**[!UICONTROL Ok]**。

   查詢將顯示在&#x200B;**[!UICONTROL Select target]**&#x200B;窗口中。

   ![](assets/dlv_seeds_usecase_04.png)

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以核准查詢。
1. 分析您的傳送，然後按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤以存取傳送記錄檔。

   採購部門的種子地址顯示為待交付，與接收方的種子地址或其他種子地址一樣。

   ![](assets/dlv_seeds_usecase_05.png)

1. 按一下&#x200B;**[!UICONTROL Send]**&#x200B;按鈕以開始傳送。

   購買部門的成員構成種子地址的一部分，這些種子地址將在其電子郵件收件箱中接收傳遞內容。

   ![](assets/dlv_seeds_usecase_18.png)
