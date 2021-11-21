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

只能由 **技術管理員** 存取「選件空間」子資料夾。 優惠方案空間只能在設計環境中建立，並會在優惠方案核准期間自動複製至即時環境。

目錄選件的內容是在選件空間中設定。 依預設，內容可包含下列欄位： **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** 和 **[!UICONTROL Text content]**. 欄位序列是在選件空間中設定。

進階參數可讓您指定聯絡人識別金鑰（例如，該金鑰可由各種元素、名稱和電子郵件欄位組成）。 有關詳細資訊，請參閱 [呈現已識別的優惠方案](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) 區段。

HTML或XML呈現是透過呈現函式建立。 呈現函式中定義的欄位順序必須與內容中設定的序列相同。

![](assets/offer_space_create_009.png)

若要建立新優惠方案空間，請套用下列程式：

1. 前往優惠方案空間清單，然後按一下 **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. 選取您要使用的管道，並變更優惠方案空間的標籤。

   ![](assets/offer_space_create_002.png)

1. 檢查 **[!UICONTROL Enable unitary mode]** 框（如果以下情形適用）:

   * 您正在使用與訊息中心的互動
   * 您使用互動的單一模式（入站互動）

1. 前往 **[!UICONTROL Content field]** 按一下 **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. 前往 **[!UICONTROL Content]** 節點，然後依下列順序選取欄位： **[!UICONTROL Title]**，然後 **[!UICONTROL Image URL]**，然後 **[!UICONTROL HTML content]**，然後 **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. 檢查 **[!UICONTROL Required]** 框，使每個欄位成為必填欄位。

   >[!NOTE]
   >
   >此設定會用於預覽，如果相關選件中缺少其中一個必要元素，則發佈時會使選件空間無效。 不過，如果優惠方案已在優惠方案空間上線，則不會考慮這些條件。

   ![](assets/offer_space_create_005.png)

1. 按一下 **[!UICONTROL Edit functions]** 來建立呈現函式。

   這些函式可用來在優惠方案空間中產生優惠方案表示法。 有幾種可能的格式：傳出互動的HTML或文字，傳入互動的XML。

   ![](assets/offer_space_create_006.png)

1. 前往 **[!UICONTROL HTML rendering]** 索引標籤和選取 **[!UICONTROL Overload the HTML rendering function]**.
1. 插入您的呈現函式。

   ![](assets/offer_space_create_007.png)

如有必要，您可以為入站互動過載XML呈現函式。 您也可以針對對外互動來過載HTML和文字轉譯功能。 有關詳細資訊，請參閱 [關於傳入頻道](../../interaction/using/about-inbound-channels.md).

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

當互動引擎建立優惠方案主張時，其狀態會變更，無論是入站或出站互動。 這兩個值之間的選擇取決於 **[!UICONTROL Design]** 環境

您可以針對每個空間，根據您要顯示在優惠方案報表中的資訊，設定建立主張時要套用的狀態。

若要這麼做，請使用下列程式：

1. 前往 **[!UICONTROL Storage]** 頁簽。
1. 選擇建立主張時要應用到的狀態。

   ![](assets/offer_update_status_001.png)

### 在接受主張時設定狀態 {#configuring-the-status-when-the-proposition-is-accepted}

接受優惠方案主張後，您可以使用預設提供的其中一個值來設定該主張的新狀態。 當收件者點按選件中的連結，並呼叫互動引擎時，更新即有效。

若要這麼做，請使用下列程式：

1. 前往 **[!UICONTROL Storage]** 頁簽。
1. 選擇在接受主張時要應用於該主張的狀態。

   ![](assets/offer_update_status_002.png)

**入站互動**

此 **[!UICONTROL Storage]** 索引標籤可讓您定義 **提議** 和 **接受** 僅提供建議。 若是傳入互動，應直接在呼叫優惠方案引擎的URL中指定優惠方案狀態，而非透過介面。 如此一來，您就能指定在其他情況下（例如，如果優惠方案主張遭拒）要套用的狀態。

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

例如，主張（識別碼） **40004**) **家庭保險** 顯示在 **尼奧班克** 網站包含下列URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

當訪客點按選件，因此URL時， **[!UICONTROL Accepted]** 狀態（值） **3**)會套用至主張，而訪客會重新導向至的新頁面 **尼奧班克** 地點來簽保險合同。

>[!NOTE]
>
>如果您想在URL中指定其他狀態（例如，如果優惠方案主張遭拒），請使用與所需狀態對應的值。 範例： **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot;等。
>
>狀態及其值可在 **[!UICONTROL Offer propositions (nms)]** 資料結構。 如需詳細資訊，請參閱[此頁面](../../configuration/using/data-schemas.md)。

**傳出互動**

如果是對外互動，您可以自動套用 **[!UICONTROL Interested]** 當傳送包含連結時，狀態為優惠方案主張。 只需新增 **_urlType=&quot;11&quot;** 連結的值：

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 每個空間的選件預覽 {#offer-preview-per-space}

在此索引標籤中，您可以透過所選方法來檢視收件者符合資格的優惠方案。 在以下範例中，收件者可透過郵件取得三份優惠方案。

![](assets/offer_space_overview_002.png)

如果收件者不符合任何優惠方案的資格，則會顯示在預覽中。

![](assets/offer_space_overview_001.png)

當內容被限制為空格時，預覽可忽略這些內容。 這是互動架構已擴充為使用入站通道新增空間中參考的欄位的情況(如需詳細資訊，請參閱 [擴充功能範例](../../interaction/using/extension-example.md))。
