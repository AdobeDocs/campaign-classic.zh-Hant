---
product: campaign
title: 匿名互動
description: 匿名互動
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# 匿名互動{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png)觀看此[影片](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com)，以概略瞭解如何將優惠傳遞至已識別和匿名目標。

## 定位和儲存匿名互動的環境 {#targeting-and-storing-an-environment-for-anonymous-interactions}

依預設，互動會隨附預先設定的環境，以鎖定收件者表格（已識別的優惠方案）。 如果您想要鎖定其他表格（匿名選件的訪客表格或特定的收件者表格），則需要使用目標對應精靈來建立環境。 如需詳細資訊，請參閱[建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。

當您透過對應建立精靈建立匿名環境時，**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;方塊會在環境的&#x200B;**[!UICONTROL General]**&#x200B;標籤中自動勾選。

**[!UICONTROL Targeting dimension]**&#x200B;已自動完成。 依預設，它會連結至訪客表格。

**[!UICONTROL Visitor folder]**&#x200B;欄位隨即顯示。 連結至&#x200B;**[!UICONTROL Visitors]**&#x200B;資料夾會自動完成。 此欄位可讓您選擇存放訪客設定檔的位置。

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>如果您想要篩選數種型別的訪客，例如，當呈現給一個或多個品牌的匿名優惠方案時，您需要為每個品牌建立一個環境，並為每個環境建立一個&#x200B;**[!UICONTROL Visitors]**&#x200B;型別資料夾。

## 匿名互動的優惠方案目錄 {#offer-catalog-for-anonymous-interactions}

就像傳出互動一樣，傳入互動會整理在優惠方案目錄中，由類別和優惠方案組成。

若要建立類別和空間，請套用與已識別訪客相同的程式（請參閱[建立優惠方案類別](../../interaction/using/creating-offer-categories.md)和[建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)）。

## 匿名訪客 {#anonymous-visitors}

匿名訪客在連線時，可能會提交至Cookie識別程式。 此隱含辨識是以訪客的瀏覽器記錄為基礎。

在此步驟中，會比較Cookie復原的資料與資料庫中的資料。 在某些情況下，訪客會被識別（然後會以隱含方式識別），而在其他情況下，訪客不會被識別（因此會維持匿名）。

若要執行此分析，請核取優惠方案空間的&#x200B;**[!UICONTROL Implicitly identify the individual based on their browser history]**&#x200B;選項。

![](assets/identification_anonymous_visitors.png)

## 處理未識別的匿名訪客 {#processing-unidentified-anonymous-visitors}

分析之後，如果未識別匿名訪客，您可以將他們的資料儲存在指定的空間。 這可讓您根據指定的型別規則，建議專門針對這類訪客的優惠方案。

如果沒有可讓您識別連絡人的元素，或您不想向可隱含識別的連絡人建議已識別的優惠，您可以選擇對匿名環境執行遞補。

若要這麼做，請核取&#x200B;**[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**，然後在指定選件空間時，指定&#x200B;**[!UICONTROL Linked anonymous space]**&#x200B;中這些未識別訪客的專屬環境。

![](assets/anonymous_to_anonymous_environment.png)
