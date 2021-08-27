---
product: campaign
title: 建立優惠方案空間
description: 建立優惠方案空間
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# 建立優惠方案空間{#creating-offer-spaces}

![](../../assets/v7-only.svg)

只能由&#x200B;**技術管理員**&#x200B;執行建立優惠方案空間的操作，該管理員具有對優惠方案空間子資料夾的訪問權限。 優惠方案空間只能在設計環境中建立，並會在優惠方案核准期間自動複製至即時環境。

目錄選件的內容是在選件空間中設定。 依預設，內容可包含下列欄位：**[!UICONTROL Title]**、**[!UICONTROL Destination URL]**、**[!UICONTROL Image URL]**、**[!UICONTROL HTML content]**&#x200B;和&#x200B;**[!UICONTROL Text content]**。 欄位序列是在選件空間中設定。

進階參數可讓您指定聯絡人識別金鑰（例如，該金鑰可由各種元素、名稱和電子郵件欄位組成）。 如需詳細資訊，請參閱[顯示已識別的選件](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer)區段。

HTML或XML呈現是透過呈現函式來建立。 呈現函式中定義的欄位順序必須與內容中設定的序列相同。

![](assets/offer_space_create_009.png)

若要建立新優惠方案空間，請套用下列程式：

1. 前往選件空格清單，然後按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/offer_space_create_001.png)

1. 選取您要使用的管道，並變更優惠方案空間的標籤。

   ![](assets/offer_space_create_002.png)

1. 如果以下其中一種情況適用於您，請核取&#x200B;**[!UICONTROL Enable unitary mode]**&#x200B;方塊：

   * 您正在使用與訊息中心的互動
   * 您使用互動的單一模式（入站互動）

1. 前往&#x200B;**[!UICONTROL Content field]**&#x200B;視窗，然後按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/offer_space_create_003.png)

1. 轉至&#x200B;**[!UICONTROL Content]**&#x200B;節點，然後按以下順序選擇欄位：**[!UICONTROL Title]**，然後是&#x200B;**[!UICONTROL Image URL]**，然後是&#x200B;**[!UICONTROL HTML content]**，然後是&#x200B;**[!UICONTROL Destination URL]**。

   ![](assets/offer_space_create_004.png)

1. 勾選&#x200B;**[!UICONTROL Required]**&#x200B;方塊，將每個欄位設為必填欄位。

   >[!NOTE]
   >
   >此設定會用於預覽，如果相關選件中缺少其中一個必要元素，則發佈時會使選件空間無效。 不過，如果優惠方案已在優惠方案空間上線，則不會考慮這些條件。

   ![](assets/offer_space_create_005.png)

1. 按一下&#x200B;**[!UICONTROL Edit functions]**&#x200B;以建立呈現函式。

   這些函式可用來在優惠方案空間中產生優惠方案表示法。 有幾種可能的格式：傳出互動的HTML或文字，傳入互動的XML。

   ![](assets/offer_space_create_006.png)

1. 前往&#x200B;**[!UICONTROL HTML rendering]**&#x200B;標籤，然後選取&#x200B;**[!UICONTROL Overload the HTML rendering function]**。
1. 插入您的呈現函式。

   ![](assets/offer_space_create_007.png)

如有必要，您可以為入站互動過載XML呈現函式。 您也可以為對外互動過載HTML和文字轉譯功能。 有關詳細資訊，請參閱[關於入站通道](../../interaction/using/about-inbound-channels.md)。

## 優惠方案主張狀態 {#offer-proposition-statuses}

優惠方案主張可能會根據與目標母體的互動而有各種狀態。 互動隨附一組值，可在優惠方案主張的整個生命週期中套用。 不過，您需要設定平台，以便在建立並接受優惠方案主張時變更狀態。

>[!NOTE]
>
>優惠方案主張的狀態不會立即更新。 這會由每小時觸發的追蹤工作流程執行。

### 狀態清單 {#status-list}

互動會提供下列值，可用來限定優惠方案主張的狀態：

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

預設不會套用這些值：必須進行設定。

>[!NOTE]
>
>如果優惠方案連結至狀態為「已傳送」的傳送，優惠方案主張的狀態會自動變更為「已呈現」。

### 在建立主張時配置狀態 {#configuring-the-status-when-the-proposition-is-created}

當互動引擎建立優惠方案主張時，其狀態會變更，無論是入站或出站互動。 這兩個值之間的選擇取決於&#x200B;**[!UICONTROL Design]**&#x200B;環境中選件空格的設定方式

您可以針對每個空間，根據您要顯示在優惠方案報表中的資訊，設定建立主張時要套用的狀態。

若要這麼做，請使用下列程式：

1. 前往所需空間的&#x200B;**[!UICONTROL Storage]**&#x200B;標籤。
1. 選擇建立主張時要應用到該主張的狀態。

   ![](assets/offer_update_status_001.png)

### 在接受主張時設定狀態 {#configuring-the-status-when-the-proposition-is-accepted}

接受優惠方案主張後，您可以使用預設提供的其中一個值來設定該主張的新狀態。 當收件者點按選件中的連結，並呼叫互動引擎時，更新即有效。

若要這麼做，請使用下列程式：

1. 前往所需空間的&#x200B;**[!UICONTROL Storage]**&#x200B;標籤。
1. 選擇在接受主張時要應用於該主張的狀態。

   ![](assets/offer_update_status_002.png)

**入站互動**

**[!UICONTROL Storage]**&#x200B;索引標籤可讓您定義&#x200B;**propsed**&#x200B;的狀態，以及&#x200B;**accepted**&#x200B;僅提供命題。 若是傳入互動，應直接在呼叫優惠方案引擎的URL中指定優惠方案狀態，而非透過介面。 如此一來，您就能指定在其他情況下（例如，如果優惠方案主張遭拒）要套用的狀態。

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

例如，符合&#x200B;**Neobank**&#x200B;網站上顯示的&#x200B;**家庭保險**&#x200B;優惠的主張(識別碼&#x200B;**40004**)包含下列URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

當訪客點按選件並因此按下URL時，**[!UICONTROL Accepted]**&#x200B;狀態（值&#x200B;**3**）就會套用至主張，並將訪客重新導向至&#x200B;**Neobank**&#x200B;網站的新頁面，以取消保險合約。

>[!NOTE]
>
>如果您想在URL中指定其他狀態（例如，如果優惠方案主張遭拒），請使用與所需狀態對應的值。 範例：**[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot;等。
>
>在&#x200B;**[!UICONTROL Offer propositions (nms)]**&#x200B;資料架構中可擷取狀態及其值。 如需詳細資訊，請參閱[此頁面](../../configuration/using/data-schemas.md)。

**傳出互動**

如果是對外互動，當傳送包含連結時，您可以自動將&#x200B;**[!UICONTROL Interested]**&#x200B;狀態套用至優惠方案主張。 只需將&#x200B;**_urlType=&quot;11&quot;**&#x200B;值新增至連結即可：

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 每個空間的選件預覽 {#offer-preview-per-space}

在此索引標籤中，您可以透過所選方法來檢視收件者符合資格的優惠方案。 在以下範例中，收件者可透過郵件取得三份優惠方案。

![](assets/offer_space_overview_002.png)

如果收件者不符合任何優惠方案的資格，則會顯示在預覽中。

![](assets/offer_space_overview_001.png)

當內容被限制為空格時，預覽可忽略這些內容。 當互動架構已擴充為使用入站通道新增空間中參考的欄位時，即為此情況（如需詳細資訊，請參閱[擴充功能範例](../../interaction/using/extension-example.md)）。
