---
product: campaign
title: 「使用案例：依條件選取種子地址」
description: 「使用案例：依條件選取種子地址」
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# 使用實例：依條件選取種子地址{#use-case-selecting-seed-addresses-on-criteria}


在傳遞或行銷活動的框架中，**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結可讓您根據特定的選取條件選擇種子地址。

在此使用案例中，網站&#x200B;**我的線上圖書館**&#x200B;想要根據客戶的文學品味來個人化電子報。

負責遞送的使用者與購買部門合作，為購買警察小說的訂閱者建立電子報。

為了分享他們與同事共同作業的最終結果，交貨經理決定將其採購部門的同事新增至交貨作為種子地址。 使用動態條件可讓您節省設定和更新位址的時間。

若要使用動態條件，您必須具備：

* 已準備好傳送的傳遞，
* 有共同值的種子地址。 此值可以是Adobe Campaign中已存在的欄位。 在此範例中，種子地址會分享「部門」欄位中的「購買」值，預設情況下不會出現在應用程式中。

## 步驟1 — 建立傳遞 {#step-1---creating-a-delivery}

建立傳遞的步驟在[建立電子郵件傳遞](creating-an-email-delivery.md)區段中詳細說明。

在此範例中，傳遞管理員已建立電子報並選取收件者。

![](assets/dlv_seeds_usecase_01.png)

## 步驟2 — 建立通用值 {#step-2---creating-a-common-value}

若要建立類似範例（採購部門）中的通用值，您必須先擴充種子地址的&#x200B;**資料結構描述**，並編輯相關的輸入表單。

### 擴充資料架構 {#extending-the-data-schema}

如需結構描述擴充功能的詳細資訊，請參閱[本節](../../configuration/using/data-schemas.md)。

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;節點中，按一下&#x200B;**[!UICONTROL New]**&#x200B;圖示。
1. 在&#x200B;**[!UICONTROL Creation of a data schema]**&#x200B;視窗中，選取&#x200B;**[!UICONTROL Extension of a schema]**&#x200B;選項並按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/dlv_seeds_usecase_09.png)

1. 選取&#x200B;**[!UICONTROL Seed addresses]**&#x200B;來源結構描述，輸入&#x200B;**doc**&#x200B;作為&#x200B;**[!UICONTROL Namespace]**，然後按一下&#x200B;**[!UICONTROL Ok]**。

   ![](assets/dlv_seeds_usecase_10.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 在結構描述編輯視窗中，複製下方的行並將它們貼到熒幕擷取畫面中指示的區域中。

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

   在此案例中，您指定已在種子位址表格中建立名為&#x200B;**[!UICONTROL Department]**&#x200B;的新列舉，且是以標準&#x200B;**[!UICONTROL @company]**&#x200B;列舉範本（在種子位址表單中標示在名稱&#x200B;**公司**&#x200B;下）為基礎。

1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 在&#x200B;**[!UICONTROL Tools > Advanced]**&#x200B;功能表中，選取&#x200B;**[!UICONTROL Update database structure]**&#x200B;選項。

   ![](assets/dlv_seeds_usecase_12.png)

1. 顯示更新精靈時，按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕以存取「編輯表格」視窗：在種子位址資料結構描述中執行的變更需要結構更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 請依照精靈的指示進行，直到您進入頁面執行更新為止。 按一下 **[!UICONTROL Start]** 按鈕。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成後，您可以關閉精靈。

1. 中斷連線，然後重新連線至Adobe Campaign。 在種子位址資料結構中所做的變更現在生效。 為了從種子位址畫面顯示它們，您必須更新相關聯的&#x200B;**[!UICONTROL Input form]**。 請參閱[更新輸入表單](#updating-the-input-form)區段。

#### 從連結的表格擴充資料結構 {#extending-the-data-schema-from-a-linked-table}

種子地址資料結構描述可以使用連結到收件者資料結構描述 — 收件者(nms)的表格中的值。

例如，使用者想要整合連結至收件者結構描述的&#x200B;**[!UICONTROL Country]**&#x200B;資料表中找到的&#x200B;**[!UICONTROL Internet Extension]**。

![](assets/dlv_seeds_usecase_06.png)

因此，他們必須擴充種子地址資料架構，如區段所述。 不過，要在&#x200B;**步驟4**&#x200B;整合的程式碼行如下：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它們表示：

* 使用者想要建立名為&#x200B;**[!UICONTROL Internet Extension]**&#x200B;的新元素，
* 此元素來自&#x200B;**[!UICONTROL Country]**&#x200B;資料表。

>[!CAUTION]
>
>在連結資料表名稱中，您必須指定此連結資料表的&#x200B;**xpath-dst**。
>
>您可以在收件者表格的&#x200B;**[!UICONTROL Country]**&#x200B;元素中找到此專案。

![](assets/dlv_seeds_usecase_07.png)

然後，使用者可以從區段的&#x200B;**步驟5**&#x200B;追蹤並更新種子地址的&#x200B;**[!UICONTROL Input form]**。

請參閱[更新輸入表單](#updating-the-input-form)區段。

#### 更新輸入表單 {#updating-the-input-form}

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Input forms]**&#x200B;節點中，尋找種子地址輸入表單。

   ![](assets/dlv_seeds_usecase_19.png)

1. 編輯表單並在&#x200B;**[!UICONTROL Recipient]**&#x200B;容器中插入下列行。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 儲存您的變更。
1. 開啟種子地址。 **[!UICONTROL Department]**&#x200B;欄位出現在&#x200B;**[!UICONTROL Recipient]**&#x200B;資料表中。

   ![](assets/dlv_seeds_usecase_22.png)

1. 編輯您要用於傳遞的種子地址，並在&#x200B;**[!UICONTROL Department]**&#x200B;欄位中輸入&#x200B;**Purchasing**&#x200B;作為值。

## 步驟3 — 定義條件 {#step-3---defining-the-condition}

您現在可以為傳遞指定種子地址的動態條件。 操作步驟：

1. 開啟傳遞。

   ![](assets/dlv_seeds_usecase_01.png)

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，然後按&#x200B;**[!UICONTROL Seed addresses]**&#x200B;索引標籤以存取&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結。

   ![](assets/dlv_seeds_usecase_02.png)

1. 選取運算式，讓您選擇想要的種子地址。 使用者可在此選取&#x200B;**[!UICONTROL Department (@workField)]**&#x200B;運算式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 選取您想要的值。 在此範例中，使用者從下拉式值清單中選取&#x200B;**採購**&#x200B;部門。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >先前建立的結構描述擴充功能來自&#x200B;**收件者**&#x200B;結構描述。 上方熒幕顯示的值來自&#x200B;**收件者**&#x200B;綱要的列舉。

1. 按一下&#x200B;**[!UICONTROL Ok]**。

   查詢會顯示在&#x200B;**[!UICONTROL Select target]**&#x200B;視窗中。

   ![](assets/dlv_seeds_usecase_04.png)

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以核准查詢。
1. 分析您的傳遞，然後按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤以存取傳遞記錄。

   採購部門的種子地址會顯示為待定傳遞，就像收件者或其他種子地址一樣。

   ![](assets/dlv_seeds_usecase_05.png)

1. 按一下&#x200B;**[!UICONTROL Send]**&#x200B;按鈕以開始傳遞。

   採購部門的成員會組成您的種子地址，這些地址將會在其電子郵件收件匣中接收傳遞。

   ![](assets/dlv_seeds_usecase_18.png)
