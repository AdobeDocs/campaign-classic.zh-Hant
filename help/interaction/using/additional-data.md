---
product: campaign
title: 其他資料
description: 其他資料
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 2%

---

# 其他資料{#additional-data}



在呼叫互動引擎期間，您可以傳輸內容相關的其他資訊。 此資料可能來自儲存在工作流程（傳出頻道）工作表中的目標資料，或網站在呼叫（傳入頻道）期間傳送的呼叫資料。 您可以在適用性規則、優惠個人化中使用這些額外資料，也可以將其儲存在主張表格中。

對於傳入頻道，復原諸如諮詢優惠方案的人員的瀏覽器語言或呼叫中心代理的名稱之類的資訊可能會很有用。 然後，您就可以在適用性規則中使用此呼叫資料，將優惠方案僅呈現給檢視網頁的法文或英文人員。

在目標工作流程（傳出頻道）中，您可以在呼叫引擎期間使用目標資料。 例如，您可以透過FDA，以收件者連結交易或外部資料庫的資料擴充目標。

## 其他資料設定 {#additional-data-configuration}

您必須擴充 **nms：互動** 連結至環境的結構描述，並宣告在呼叫互動引擎期間使用的其他欄位清單。 建立適用性規則或個人化優惠方案時，這些欄位將可從 **互動** 節點(請參閱 [使用其他資料](#using-additional-data))。

針對傳入頻道，您必須將通話資料欄位新增至 **互動** 節點。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>傳入頻道支援XML集合，但不支援其他結構描述的連結。

對於傳出頻道，您必須新增 **targetdata** 包含其他欄位的元素 **互動** 節點。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>傳出頻道不支援集合。 不過，您可以建立其他結構描述的連結。

如果您想要將此資料儲存在主張表格中，您也必須擴充 **nms：propositionRcp** 並宣告這些欄位。

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## 其他資料實作 {#additional-data-implementation}

### 輸入管道（網頁） {#input-channel--web-page-}

若要在呼叫引擎時傳輸其他資料，您必須新增 **interactionGlobalCtx** 變數插入網頁的JavaScript程式碼中。 插入 **互動** 包含呼叫資料至此變數的節點。 您必須遵循的xml結構與 **nms：互動** 綱要。 請參閱： [其他資料設定](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### 輸出頻道 {#output-channel}

您必須建立目標工作流程，載入工作表的其他資料，方法為遵循與相同的xml結構和相同的內部名稱 **nms：互動** 綱要。 請參閱： [其他資料設定](#additional-data-configuration).

## 使用其他資料 {#using-additional-data}

### 適用性規則 {#eligibility-rules}

您可以將適用性規則中的其他資料用於優惠方案、類別和權重。

例如，您可以選擇只向檢視頁面的人顯示英文選件。

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>您必須將規則限制在定義資料的管道上。 在我們的範例中，我們限制的是傳入網路頻道(**[!UICONTROL Taken into account if]** 欄位)。

### 個人化 {#personalization}

您也可以在個人化優惠時使用此其他資料。 例如，您可以為導覽語言新增條件

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>您必須限制定義資料的管道上的個人化。 在我們的範例中，我們限制的是傳入網路頻道的規則。

如果您使用其他資料將優惠個人化，則此資料預設不會出現在預覽中，因為資料庫中不提供此資料。 在環境的 **[!UICONTROL Example of call data]** 索引標籤中，您必須新增要在預覽中使用的值範例。 請遵循中的相同xml結構 **nms：互動** 綱要延伸。 有關詳細資訊，請參閱 [其他資料設定](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

預覽時，按一下 **[!UICONTROL Content personalization options for the preview]** 並選取 **[!UICONTROL Call data]** 欄位。

![](assets/ita_calldata_preview2.png)

### 儲存空間 {#storage}

在呼叫引擎期間，您可以在主張表格中儲存其他資料，以擴充資料庫。 例如，此資料可用於報告、ROI計算或之後的流程。

>[!NOTE]
>
>您必須已擴充 **nms：propositionRcp** 並宣告包含要儲存之資料的欄位。 有關詳細資訊： [其他資料設定](#additional-data-configuration).

在優惠方案空間，前往 **[!UICONTROL Storage]** 標籤並按一下 **[!UICONTROL Add]** 按鈕。

在 **[!UICONTROL Storage path]** 欄中，選取主張表格中的儲存欄位。 在 **[!UICONTROL Expression]** 欄中，選取其他欄位 **[!UICONTROL Interaction]** 節點。

您可以在產生主張或接受主張時（當人員按一下優惠時）擷取通話資料。

![](assets/ita_calldata_storage.png)
