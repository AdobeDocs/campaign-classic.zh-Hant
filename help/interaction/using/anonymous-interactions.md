---
title: 匿名互動
seo-title: 匿名互動
description: 匿名互動
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8e37be4f764feadb49c70a9d598f8f3b8f864380

---


# 匿名互動{#anonymous-interactions}

觀看此 [影片](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) ，以取得如何將選件傳送至已識別和匿名目標的概觀。

## 針對匿名互動鎖定和儲存環境 {#targeting-and-storing-an-environment-for-anonymous-interactions}

依預設，互動隨附預先設定的環境，以定位收件者表格（已識別的選件）。 如果您想要定位另一個表格（匿名選件的訪客表格或特定收件者表格），則需要使用定位對應精靈來建立環境。 如需詳細資訊，請參 [閱建立選件環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

當您通過映射建立嚮導建立匿名環境時， **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 該框將自動選中該環境的選項 **[!UICONTROL General]** 卡。

自動 **[!UICONTROL Targeting dimension]** 完成。 依預設，會連結至訪客表格。

此時將 **[!UICONTROL Visitor folder]** 顯示該欄位。 自動完成以連結至資料 **[!UICONTROL Visitors]** 夾。 此欄位可讓您選擇訪客描述檔的儲存位置。

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>如果您想要篩選數種訪客類型，例如針對一或多個品牌顯示匿名選件，則需要為每個品牌建立環境，並為每個環境建立 **[!UICONTROL Visitors]** 類型資料夾。

## 匿名互動的選件目錄 {#offer-catalog-for-anonymous-interactions}

如同對外互動，傳入互動會組織在由類別和選件組成的選件目錄中。

若要建立類別和空格，請套用與所識別訪客相同的程式(請參閱「建立選 [件類別](../../interaction/using/creating-offer-categories.md) 」 [和「建立選件環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)」)。

## 匿名訪客 {#anonymous-visitors}

匿名訪客在連線時可能會提交至Cookie識別程式。 此隱含識別是以訪客的瀏覽器歷史記錄為基礎。

在此步驟中，會比較由Cookie所復原的資料與資料庫中的資料。 在某些情況下，訪客會被識別（接著隱含地被識別），而在其他情況下，訪客不被識別（因此匿名）。

若要執行此分析，請針對選件空間勾選 **[!UICONTROL Implicitly identify the individual based on their browser history]** 選項。

![](assets/identification_anonymous_visitors.png)

## 處理未識別的匿名訪客 {#processing-unidentified-anonymous-visitors}

分析後，若未識別匿名訪客，您可將其資料儲存在指定的空間。 這可讓您針對此類型的訪客建議特別針對的選件，並符合指定的類型學規則。

如果沒有可讓您識別聯絡人的元素，或您不想向可隱含識別的聯絡人建議已識別的選件，您可以選擇對匿名環境進行備援。

若要這麼做，請勾選 **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**，然後指定指定選件空間時，這些未識別訪客 **[!UICONTROL Linked anonymous space]** 專屬的環境。

![](assets/anonymous_to_anonymous_environment.png)

