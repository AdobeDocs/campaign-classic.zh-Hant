---
product: campaign
title: 匿名互動
description: 匿名互動
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---

# 匿名互動{#anonymous-interactions}

![](../../assets/v7-only.svg)

![](assets/do-not-localize/how-to-video.png) 觀看此影 [](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) 片以取得如何將選件傳遞至已識別和匿名目標的概述。

## 針對匿名互動定位並儲存環境 {#targeting-and-storing-an-environment-for-anonymous-interactions}

依預設，互動會隨預先設定的環境提供，以鎖定收件者表格（已識別的選件）。 如果您想要鎖定另一個表格（匿名選件或特定收件者表格的訪客表格），則需要使用目標對應精靈來建立環境。 如需詳細資訊，請參閱[建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

當您通過映射建立嚮導建立匿名環境時，環境的&#x200B;**[!UICONTROL General]**&#x200B;頁簽中會自動選中&#x200B;**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;框。

**[!UICONTROL Targeting dimension]**&#x200B;自動完成。 依預設，它會連結至訪客表格。

將顯示&#x200B;**[!UICONTROL Visitor folder]**&#x200B;欄位。 自動完成以連結至&#x200B;**[!UICONTROL Visitors]**&#x200B;資料夾。 此欄位可讓您選擇要將訪客設定檔儲存於何處。

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>如果您想要篩選數種類型的訪客，例如針對一或多個品牌呈現的匿名選件，則需要為每個品牌建立環境，並為每個環境建立&#x200B;**[!UICONTROL Visitors]**&#x200B;類型資料夾。

## 匿名互動的選件目錄 {#offer-catalog-for-anonymous-interactions}

就像對外互動一樣，入站互動也會組織在由類別和選件組成的選件目錄中。

若要建立類別和空格，請套用與已識別訪客相同的程式（請參閱[建立優惠方案類別](../../interaction/using/creating-offer-categories.md)和[建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)）。

## 匿名訪客 {#anonymous-visitors}

當匿名訪客連線時，可將其提交至Cookie識別程式。 此隱含識別是根據訪客的瀏覽器記錄。

在此步驟中，會比較由Cookie復原的資料與資料庫中的資料。 在某些情況下，會識別訪客（接著以隱含方式識別），而在其他情況下，則無法識別訪客（因此保持匿名）。

若要執行此分析，請針對優惠方案空間核取&#x200B;**[!UICONTROL Implicitly identify the individual based on their browser history]**&#x200B;選項。

![](assets/identification_anonymous_visitors.png)

## 處理未識別的匿名訪客 {#processing-unidentified-anonymous-visitors}

分析後，如果未識別匿名訪客，您可以將其資料儲存在指定空間。 這可讓您建議專門針對這類訪客的選件，並符合指定的類型規則。

如果沒有任何元素可讓您識別連絡人，或如果您不想向可以隱含識別的連絡人建議已識別的優惠方案，您可以選擇對匿名環境進行備援。

若要這麼做，請檢查&#x200B;**[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**，然後在指定優惠方案空間時，於&#x200B;**[!UICONTROL Linked anonymous space]**&#x200B;中指定這些未識別訪客專屬的環境。

![](assets/anonymous_to_anonymous_environment.png)
