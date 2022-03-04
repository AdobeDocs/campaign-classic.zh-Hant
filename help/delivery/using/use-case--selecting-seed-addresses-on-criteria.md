---
product: campaign
title: '"使用實例：依條件選取種子地址"'
description: '"使用實例：依條件選取種子地址"'
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 3%

---

# 使用實例：依條件選取種子地址{#use-case-selecting-seed-addresses-on-criteria}

![](../../assets/common.svg)

在交付或活動的框架內， **[!UICONTROL Edit the dynamic condition...]** 連結允許您根據特定選擇標準選擇種子地址。

在此使用情形中，站點 **我的聯機庫** 想根據客戶的文學品味，個性化通訊。

負責遞送的用戶與採購部門合作，為購買警察小說的訂戶建立了一份通訊。

為了與他們共用協作的最終結果，交付經理決定將採購部門的同事添加到交付中，作為種子地址。 使用動態條件可節省配置和更新地址的時間。

要使用動態條件，必須具備：

* 已準備好送貨，
* 具有公共值的種子地址。 此值可以是已存在於Adobe Campaign中的欄位。 在本示例中，種子地址在「部門」欄位中共用「採購」值，預設情況下，該值在應用程式中不存在。

## 步驟1 — 建立交貨 {#step-1---creating-a-delivery}

建立交貨的步驟在 [建立電子郵件傳遞](creating-an-email-delivery.md) 的子菜單。

在此示例中，交付經理建立了新聞稿並選擇了收件人。

![](assets/dlv_seeds_usecase_01.png)

## 步驟2 — 建立公用值 {#step-2---creating-a-common-value}

要建立與示例（Oracle Purchasing部門）中相同的公用值，必須首先擴展 **資料模式** 編輯相關的輸入表單。

### 擴展資料架構 {#extending-the-data-schema}

有關架構擴展的詳細資訊，請參閱 [此部分](../../configuration/using/data-schemas.md)。

1. 在 **[!UICONTROL Administration > Configuration > Data schemas]** 節點，按一下 **[!UICONTROL New]** 表徵圖
1. 在 **[!UICONTROL Creation of a data schema]** ，選擇 **[!UICONTROL Extension of a schema]** 選項 **[!UICONTROL Next]**。

   ![](assets/dlv_seeds_usecase_09.png)

1. 選擇 **[!UICONTROL Seed addresses]** 源架構，輸入 **文檔** 的 **[!UICONTROL Namespace]** 按一下 **[!UICONTROL Ok]**。

   ![](assets/dlv_seeds_usecase_10.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 在架構編輯窗口中，複製下面的行，並將它們貼上到螢幕快照中指示的區域中。

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   然後複製下列行，並將它們貼上到 **[!UICONTROL Seed to insert in the export files]** 的子菜單。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在本例中，您將指定名為 **[!UICONTROL Department]** 已在種子地址表中建立，並且基於標準 **[!UICONTROL @company]** 枚舉模板(標籤在名稱下 **公司** )的正平方根。

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 在 **[!UICONTROL Tools > Advanced]** 的 **[!UICONTROL Update database structure]** 的雙曲餘切值。

   ![](assets/dlv_seeds_usecase_12.png)

1. 顯示更新嚮導時，按一下 **[!UICONTROL Next]** 按鈕以訪問「編輯表」窗口：在種子地址資料模式中執行的更改需要結構更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 按照嚮導操作，直到您到頁面運行更新。 按一下 **[!UICONTROL Start]** 按鈕。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成後，可以關閉嚮導。

1. 斷開連接，然後重新連接到Adobe Campaign。 種子地址資料架構中所做的更改現在已生效。 要使它們在種子地址螢幕中可見，必須更新關聯的 **[!UICONTROL Input form]**。 請參閱 [更新輸入表單](#updating-the-input-form) 的子菜單。

#### 從連結表擴展資料模式 {#extending-the-data-schema-from-a-linked-table}

種子地址資料模式可以使用連結到接收者資料模式 — 接收者(nms)的表中的值。

例如，用戶希望將 **[!UICONTROL Internet Extension]** 在 **[!UICONTROL Country]** 連結到收件人架構的表。

![](assets/dlv_seeds_usecase_06.png)

因此，它們必須擴展該部分中詳述的種子地址資料模式。 但是，要整合的代碼行在 **步驟4** 如下：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它們表明：

* 用戶要建立名為 **[!UICONTROL Internet Extension]**。
* 這個元素來自 **[!UICONTROL Country]** 的子菜單。

>[!CAUTION]
>
>在連結的表名中，必須指定 **xpath-dst** 所連結的表。
>
>可以在 **[!UICONTROL Country]** 的下界。

![](assets/dlv_seeds_usecase_07.png)

用戶隨後可以從 **步驟5** 並更新 **[!UICONTROL Input form]** 種子地址。

請參閱 [更新輸入表單](#updating-the-input-form) 的子菜單。

#### 更新輸入表單 {#updating-the-input-form}

1. 在 **[!UICONTROL Administration > Configuration > Input forms]** 節點，查找種子地址輸入表單。

   ![](assets/dlv_seeds_usecase_19.png)

1. 編輯窗體，並在 **[!UICONTROL Recipient]** 容器。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 儲存您的變更。
1. 開啟種子地址。 的 **[!UICONTROL Department]** 的 **[!UICONTROL Recipient]** 的子菜單。

   ![](assets/dlv_seeds_usecase_22.png)

1. 編輯要用於交貨的種子地址並輸入 **採購** 值 **[!UICONTROL Department]** 的子菜單。

## 步驟3 — 定義條件 {#step-3---defining-the-condition}

現在，您可以指定傳送的種子地址的動態條件。 操作步驟：

1. 開啟交貨。

   ![](assets/dlv_seeds_usecase_01.png)

1. 按一下 **[!UICONTROL To]** 連結 **[!UICONTROL Seed addresses]** 頁籤 **[!UICONTROL Edit the dynamic condition...]** 的子菜單。

   ![](assets/dlv_seeds_usecase_02.png)

1. 選擇用於選擇所需種子地址的表達式。 此處用戶選擇 **[!UICONTROL Department (@workField)]** 表達式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 選擇所需的值。 在此示例中，用戶選擇 **採購** 的子菜單。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >先前建立的架構擴展來自 **收件人** 架構。 上面螢幕上顯示的值來自 **收件人** 架構。

1. 按一下&#x200B;**[!UICONTROL Ok]**。

   查詢顯示在 **[!UICONTROL Select target]** 的子菜單。

   ![](assets/dlv_seeds_usecase_04.png)

1. 按一下 **[!UICONTROL Ok]** 來批准該查詢。
1. 分析您的交貨，然後按一下 **[!UICONTROL Delivery]** 頁籤以訪問傳遞日誌。

   採購部門的種子地址顯示為待交貨，與接收方的種子地址或其他種子地址一樣。

   ![](assets/dlv_seeds_usecase_05.png)

1. 按一下 **[!UICONTROL Send]** 按鈕開始交貨。

   採購部門的成員構成了種子地址的一部分，這些種子地址將在其電子郵件收件箱中接收交貨。

   ![](assets/dlv_seeds_usecase_18.png)
