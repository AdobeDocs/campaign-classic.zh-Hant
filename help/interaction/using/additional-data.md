---
product: campaign
title: 其他資料
description: 其他資料
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# 其他資料{#additional-data}

![](../../assets/v7-only.svg)

在呼叫互動引擎期間，您可以傳輸內容相關的其他資訊。 此資料可來自儲存在工作流程（傳出通道）工作表中的目標資料，或網站在呼叫（傳入通道）期間傳送的呼叫資料。 您可以在適用性規則、優惠方案個人化中使用此額外資料，也可以將其儲存在主張表格中。

對於入站通道，例如恢復咨詢優惠方案的人員的瀏覽器語言或呼叫中心代理的名稱等資訊可能很有用。 然後，您可以在適用性規則中使用此呼叫資料，只向以法文或英文檢視網頁的使用者提供優惠方案。

在目標工作流程（傳出通道）中，您可以在呼叫引擎期間使用目標資料。 例如，您可以透過FDA，以收件者連結交易或外部資料庫的資料來擴充目標。

## 其他資料配置 {#additional-data-configuration}

您必須擴充 **nms:interaction** 連結至環境的架構，並宣告呼叫互動引擎期間將使用的其他欄位清單。 建立適用性規則或個人化優惠方案時，您可從 **互動** 節點(請參閱 [使用其他資料](#using-additional-data))。

對於傳入頻道，您必須將呼叫資料欄位新增至 **互動** 節點。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>傳入頻道支援Xml集合，但其他結構的連結則不支援。

對於傳出通道，您必須新增 **targetData** 包含其他欄位至 **互動** 節點。

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>對出頻道不支援集合。 不過，您可以建立其他結構的連結。

如果要將此資料儲存在主張表格中，您也必須將 **nms:positionRcp** 架構並宣告這些欄位。

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## 其他資料實作 {#additional-data-implementation}

### 輸入通道（網頁） {#input-channel--web-page-}

若要在呼叫引擎時傳輸其他資料，您必須新增 **interactionGlobalCtx** 變數填入網頁的JavaScript程式碼中。 插入 **互動** 包含此變數中呼叫資料的節點。 您必須遵循與 **nms:interaction** 綱要。 請參閱： [其他資料配置](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### 輸出通道 {#output-channel}

您必須建立目標工作流，通過遵循與 **nms:interaction** 綱要。 請參閱： [其他資料配置](#additional-data-configuration).

## 使用其他資料 {#using-additional-data}

### 適用性規則 {#eligibility-rules}

您可以在優惠方案、類別和權重的適用性規則中使用其他資料。

例如，您可以選擇將選件只顯示給檢視頁面的使用者，使用英文。

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>您必須限制定義資料的管道上的規則。 在我們的範例中，我們將限制傳入Web頻道(**[!UICONTROL Taken into account if]** 欄位)。

### 個人化 {#personalization}

個人化優惠方案時，您也可以使用此額外資料。 例如，您可以新增導覽語言的條件

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>您必須在定義資料的管道上限制個人化。 在我們的範例中，我們會限制傳入Web頻道上的規則。

如果您使用其他資料個人化優惠方案，此資料預設不會顯示在預覽中，因為資料庫中沒有此資料。 環境 **[!UICONTROL Example of call data]** 索引標籤中，您必須新增值範例才能在預覽中使用。 請遵循與 **nms:interaction** 綱要擴充功能。 有關詳細資訊，請參閱 [其他資料配置](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

預覽時，按一下 **[!UICONTROL Content personalization options for the preview]** 並選取 **[!UICONTROL Call data]** 欄位。

![](assets/ita_calldata_preview2.png)

### 儲存 {#storage}

在對引擎的調用期間，您可以在主張表中儲存其他資料，以豐富資料庫。 這些資料可用於報表、ROI計算或後續程式。

>[!NOTE]
>
>您必須將 **nms:positionRcp** 方案並聲明將包含要儲存的資料的欄位。 如需詳細資訊： [其他資料配置](#additional-data-configuration).

在優惠方案空間中，前往 **[!UICONTROL Storage]** ，然後按一下 **[!UICONTROL Add]** 按鈕。

在 **[!UICONTROL Storage path]** 欄中，選擇主題表中的儲存欄位。 在 **[!UICONTROL Expression]** 欄中，選取 **[!UICONTROL Interaction]** 節點。

您可以在產生主張或接受主張時（當使用者點按優惠方案時）擷取呼叫資料。

![](assets/ita_calldata_storage.png)
