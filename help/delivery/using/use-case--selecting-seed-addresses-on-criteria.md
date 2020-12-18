---
solution: Campaign Classic
product: campaign
title: '"使用案例：依條件選取種子地址"'
description: '"使用案例：依條件選取種子地址"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---


# 使用案例：依條件選取種子地址{#use-case-selecting-seed-addresses-on-criteria}

在傳送或促銷活動的架構中，**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結可讓您根據特定選擇標準選擇種子位址。

在此使用案例中，網站&#x200B;**My online library**&#x200B;會根據客戶的文學品味，將電子報個人化。

負責遞送的使用者會與採購部門合作，為購買警察小說的訂閱者建立電子報。

為分享與採購部門合作的最終結果，交貨經理決定將採購部門的同事新增至交貨，作為種子地址。 使用動態條件可節省配置和更新地址的時間。

若要使用動態條件，您必須具備：

* 準備寄送的貨物，
* 具有公用值的種子地址。 此值可以是Adobe Campaign中已存在的欄位。 在此範例中，種子位址會在「部門」欄位中共用「購買」值，此值預設不會出現在應用程式中。

## 步驟1 —— 建立傳送{#step-1---creating-a-delivery}

建立傳送的步驟詳見[建立電子郵件傳送](../../delivery/using/creating-an-email-delivery.md)一節。

在此範例中，傳送管理員已建立電子報並選取收件者。

![](assets/dlv_seeds_usecase_01.png)

## 步驟2 —— 建立公用值{#step-2---creating-a-common-value}

要建立與示例（採購部門）中的公用值類似的值，您必須先擴展種子地址的&#x200B;**資料架構**&#x200B;並編輯相關的輸入表單。

### 擴展資料模式{#extending-the-data-schema}

有關架構擴展的詳細資訊，請參閱[配置指南](../../configuration/using/data-schemas.md)。

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;節點中，按一下&#x200B;**[!UICONTROL New]**&#x200B;表徵圖。
1. 在&#x200B;**[!UICONTROL Creation of a data schema]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Extension of a schema]**&#x200B;選項並按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/dlv_seeds_usecase_09.png)

1. 選擇&#x200B;**[!UICONTROL Seed addresses]**&#x200B;源方案，輸入&#x200B;**doc**&#x200B;作為&#x200B;**[!UICONTROL Namespace]**，然後按一下&#x200B;**[!UICONTROL Ok]**。

   ![](assets/dlv_seeds_usecase_10.png)

1. 按一下 **[!UICONTROL Save]**。
1. 在架構編輯視窗中，複製下面的行，並貼到螢幕擷取中指示的區域。

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   然後複製下列行，並貼到&#x200B;**[!UICONTROL Seed to insert in the export files]**&#x200B;元素下。

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   在這種情況下，您指定在種子地址表中建立了名為&#x200B;**[!UICONTROL Department]**&#x200B;的新枚舉，該枚舉基於標準&#x200B;**[!UICONTROL @company]**&#x200B;枚舉模板（在種子地址表中的名稱&#x200B;**Company**&#x200B;下標籤）。

1. 按一下 **[!UICONTROL Save]**。
1. 在&#x200B;**[!UICONTROL Tools > Advanced]**&#x200B;菜單中，選擇&#x200B;**[!UICONTROL Update database structure]**&#x200B;選項。

   ![](assets/dlv_seeds_usecase_12.png)

1. 顯示更新嚮導時，按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕以訪問「編輯表」窗口：在種子地址資料模式中執行的更改需要結構更新。

   ![](assets/dlv_seeds_usecase_13.png)

1. 請依照精靈進行，直到您進入頁面執行更新。 按一下 **[!UICONTROL Start]** 按鈕。

   ![](assets/dlv_seeds_usecase_14.png)

   更新完成後，您可以關閉精靈。

1. 中斷連線，然後重新連線至Adobe Campaign。 種子地址資料模式中所做的更改現在是有效的。 為了從種子地址螢幕中看到它們，您必須更新關聯的&#x200B;**[!UICONTROL Input form]**。 請參閱[更新輸入表單](#updating-the-input-form)一節。

#### 從連結表{#extending-the-data-schema-from-a-linked-table}擴展資料模式

種子地址資料模式可以使用來自連結到接收者資料模式的表的值——接收者(nms)。

例如，用戶希望將&#x200B;**[!UICONTROL Country]**&#x200B;表中找到的&#x200B;**[!UICONTROL Internet Extension]**&#x200B;與收件人方案連結。

![](assets/dlv_seeds_usecase_06.png)

因此，它們必須擴展種子地址資料模式，如一節中所述。 但是，要在&#x200B;**步驟4**&#x200B;整合的代碼行如下：

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

它們指出：

* 使用者想要建立名為&#x200B;**[!UICONTROL Internet Extension]**&#x200B;的新元素，
* 此元素來自&#x200B;**[!UICONTROL Country]**&#x200B;表格。

>[!CAUTION]
>
>在連結表名中，必須指定該連結表的&#x200B;**xpath-dst**。
>
>這可在收件者表格的&#x200B;**[!UICONTROL Country]**&#x200B;元素中找到。

![](assets/dlv_seeds_usecase_07.png)

然後，用戶可以從該節的&#x200B;**步驟5**&#x200B;進行操作，並更新種子地址的&#x200B;**[!UICONTROL Input form]**。

請參閱[更新輸入表單](#updating-the-input-form)一節。

#### 更新輸入表單{#updating-the-input-form}

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Input forms]**&#x200B;節點中，查找種子地址輸入表單。

   ![](assets/dlv_seeds_usecase_19.png)

1. 編輯表單，並在&#x200B;**[!UICONTROL Recipient]**&#x200B;容器中插入下列行。

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 儲存您的變更。
1. 開啟種子地址。 **[!UICONTROL Department]**&#x200B;欄位會出現在&#x200B;**[!UICONTROL Recipient]**&#x200B;表格中。

   ![](assets/dlv_seeds_usecase_22.png)

1. 編輯要用於傳送的種子地址，並在&#x200B;**[!UICONTROL Department]**&#x200B;欄位中輸入&#x200B;**Purchasing**&#x200B;作為值。

## 步驟3 —— 定義條件{#step-3---defining-the-condition}

您現在可以指定傳送種子地址的動態條件。 操作步驟：

1. 開啟傳送。

   ![](assets/dlv_seeds_usecase_01.png)

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Seed addresses]**&#x200B;頁籤以訪問&#x200B;**[!UICONTROL Edit the dynamic condition...]**&#x200B;連結。

   ![](assets/dlv_seeds_usecase_02.png)

1. 選擇可讓您選擇所需種子地址的表達式。 在此，用戶選擇&#x200B;**[!UICONTROL Department (@workField)]**&#x200B;表達式。

   ![](assets/dlv_seeds_usecase_03.png)

1. 選取您要的值。 在此範例中，使用者從值下拉式清單中選擇&#x200B;**Purchasing**&#x200B;部門。

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >先前建立的架構擴展來自&#x200B;**recipient**&#x200B;架構。 上述螢幕上顯示的值來自&#x200B;**接收方**&#x200B;模式的枚舉。

1. 按一下 **[!UICONTROL Ok]**。

   查詢顯示在&#x200B;**[!UICONTROL Select target]**&#x200B;窗口中。

   ![](assets/dlv_seeds_usecase_04.png)

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;批准查詢。
1. 分析您的傳送，然後按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤以存取傳送記錄檔。

   採購部門的種子地址顯示為待交貨，與接收者或其他種子地址相同。

   ![](assets/dlv_seeds_usecase_05.png)

1. 按一下&#x200B;**[!UICONTROL Send]**&#x200B;按鈕以開始傳送。

   採購部門的成員構成了種子地址的一部分，這些種子地址將接收其電子郵件收件箱中的發送。

   ![](assets/dlv_seeds_usecase_18.png)
