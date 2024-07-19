---
product: campaign
title: 建立優惠方案空間
description: 建立優惠方案空間
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# 建立優惠方案空間{#creating-offer-spaces}



優惠方案空間的建立只能由有權存取優惠方案空間子資料夾的&#x200B;**技術管理員**&#x200B;執行。 優惠方案空間只能在設計環境中建立，並在優惠方案核准期間自動複製到即時環境中。

目錄優惠方案的內容是在優惠方案空間中設定。 依預設，內容可以包含以下欄位： **[!UICONTROL Title]**、**[!UICONTROL Destination URL]**、**[!UICONTROL Image URL]**、**[!UICONTROL HTML content]**&#x200B;和&#x200B;**[!UICONTROL Text content]**。 欄位序列是在選件空間中設定。

進階引數可讓您指定聯絡人識別金鑰（例如，可同時由各種元素、名稱和電子郵件欄位組成）。 如需詳細資訊，請參閱[簡報已識別的優惠](../../interaction/using/integration-via-javascript-client-side.md#presenting-an-identified-offer)區段。

HTML或XML演算會透過演算函式建立。 轉譯函式中定義的欄位順序必須與內容中設定的順序相同。

![](assets/offer_space_create_009.png)

若要建立新的優惠方案空間，請套用下列程式：

1. 前往優惠方案空間清單，然後按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/offer_space_create_001.png)

1. 選取您要使用的管道，並變更優惠方案空間的標籤。

   ![](assets/offer_space_create_002.png)

1. 如果下列其中一種情況適用於您，請核取&#x200B;**[!UICONTROL Enable unitary mode]**&#x200B;方塊：

   * 您正在使用與訊息中心的互動
   * 您使用互動的單一模式（傳入互動）

1. 前往&#x200B;**[!UICONTROL Content field]**&#x200B;視窗並按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/offer_space_create_003.png)

1. 移至&#x200B;**[!UICONTROL Content]**&#x200B;節點，並依下列順序選取欄位： **[!UICONTROL Title]**、**[!UICONTROL Image URL]**、**[!UICONTROL HTML content]**、**[!UICONTROL Destination URL]**。

   ![](assets/offer_space_create_004.png)

1. 核取&#x200B;**[!UICONTROL Required]**&#x200B;方塊，讓每個欄位成為必要欄位。

   >[!NOTE]
   >
   >此設定會用於預覽，並在相關選件中缺少其中一個必要元素時，讓選件空格在發佈時失效。 但是，如果優惠方案空間中已上線，則不會考慮這些條件。

   ![](assets/offer_space_create_005.png)

1. 按一下&#x200B;**[!UICONTROL Edit functions]**&#x200B;以建立演算函式。

   這些函式用於在優惠方案空間上產生優惠方案宣告。 有幾種可能的格式：傳出互動的HTML或文字，以及傳入互動的XML。

   ![](assets/offer_space_create_006.png)

1. 移至&#x200B;**[!UICONTROL HTML rendering]**&#x200B;標籤並選取&#x200B;**[!UICONTROL Overload the HTML rendering function]**。
1. 插入您的演算函式。

   ![](assets/offer_space_create_007.png)

如有必要，您可以針對傳入互動多載XML演算函式。 您也可以為傳出互動多載HTML和文字演算函式。 如需詳細資訊，請參閱[關於傳入頻道](../../interaction/using/about-inbound-channels.md)。

## 優惠方案主張狀態 {#offer-proposition-statuses}

視與目標母體的互動而定，優惠方案主張可能有各種狀態。 互動會隨附一組值，這些值可在優惠方案主張的整個生命週期中套用。 不過，您將需要設定平台，以便在建立及接受優惠方案主張時變更狀態。

>[!NOTE]
>
>優惠方案主張的狀態不會立即更新。 追蹤工作流程會每小時觸發一次。

### 狀態清單 {#status-list}

互動會提供下列值，這些值可用來限定優惠方案主張的狀態：

* **[!UICONTROL Accepted]**。
* **[!UICONTROL Scheduled]**。
* **[!UICONTROL Generated]**。
* **[!UICONTROL Interested]**。
* **[!UICONTROL Presented]**。
* **[!UICONTROL Rejected]**。

預設不會套用這些值：必須加以設定。

>[!NOTE]
>
>如果優惠連結到狀態為「已傳送」的傳遞，優惠方案主張的狀態會自動變更為「已呈現」。

### 建立主張時設定狀態 {#configuring-the-status-when-the-proposition-is-created}

當互動引擎建立優惠方案主張時，其狀態會變更，無論是傳入或傳出互動。 這兩個值之間的選擇取決於在&#x200B;**[!UICONTROL Design]**&#x200B;環境中設定選件空間的方式

對於每個空間，您可以根據要在優惠方案報表中顯示的資訊，設定建立主張時要套用的狀態。

要執行此操作，請使用下列程式：

1. 前往所需空間的&#x200B;**[!UICONTROL Storage]**&#x200B;標籤。
1. 選取您要在建立時套用至主張的狀態。

   ![](assets/offer_update_status_001.png)

### 在接受主張時設定狀態 {#configuring-the-status-when-the-proposition-is-accepted}

一旦接受優惠方案主張，您就可以使用預設提供的其中一個值來設定主張的新狀態。 當收件者按一下優惠中的連結時（會呼叫互動引擎），更新會生效。

要執行此操作，請使用下列程式：

1. 前往所需空間的&#x200B;**[!UICONTROL Storage]**&#x200B;標籤。
1. 選取您要在主張被接受時套用的狀態。

   ![](assets/offer_update_status_002.png)

**傳入互動**

**[!UICONTROL Storage]**&#x200B;索引標籤可讓您只定義&#x200B;**建議**&#x200B;和&#x200B;**接受**&#x200B;優惠方案主張的狀態。 針對傳入互動，應直接在呼叫優惠方案引擎的URL中指定優惠方案主張的狀態，而非透過介面。 如此一來，您將能夠指定在其他情況下要套用的狀態，例如在優惠方案主張被拒絕時。

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

例如，符合&#x200B;**Neobank**&#x200B;網站上顯示之&#x200B;**家庭保險**&#x200B;優惠方案的主張(識別碼&#x200B;**40004**)包含下列URL：

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

只要訪客按一下選件（因此是URL），就會將&#x200B;**[!UICONTROL Accepted]**&#x200B;狀態（值&#x200B;**3**）套用至主張，且訪客會重新導向至&#x200B;**Neobank**&#x200B;網站的新頁面，以取得保險合約。

>[!NOTE]
>
>如果您想在URL中指定其他狀態（例如，如果優惠方案主張被拒絕），請使用與所需狀態對應的值。 範例： **[!UICONTROL Rejected]** = &quot;5&quot;、**[!UICONTROL Presented]** = &quot;1&quot;等。
>
>可以在&#x200B;**[!UICONTROL Offer propositions (nms)]**&#x200B;資料結構描述中擷取狀態及其值。 如需詳細資訊，請參閱[此頁面](../../configuration/using/data-schemas.md)。

**傳出互動**

若是傳出互動，當傳遞包含連結時，您可以自動將&#x200B;**[!UICONTROL Interested]**&#x200B;狀態套用至優惠方案主張。 只需將&#x200B;**_urlType=&quot;11&quot;**&#x200B;值新增至連結即可：

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 每個空間的優惠預覽 {#offer-preview-per-space}

在此索引標籤中，您可以透過所選方法檢視收件者符合資格的優惠方案。 在下列範例中，收件者有資格透過郵件取得三個優惠方案書。

![](assets/offer_space_overview_002.png)

如果收件者不符合任何優惠方案的資格，便會在預覽中顯示。

![](assets/offer_space_overview_001.png)

當上下文限製為空格時，預覽可以忽略上下文。 當互動結構描述已擴充為使用傳入頻道新增空間中所參考的欄位時，就是這種情況（如需詳細資訊，請參閱[擴充功能範例](../../interaction/using/extension-example.md)）。
