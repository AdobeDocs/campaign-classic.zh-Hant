---
product: campaign
title: 使用傳遞範本
description: 使用傳遞範本
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Delivery Templates
hide: true
hidefromtoc: true
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---

# 使用範本 {#use-templates}



傳遞範本提供最常見活動型別的現成案例，有助於提高效率。 透過範本，行銷人員可以在較短的時間內以最小的自訂部署新行銷活動。

在[本節](creating-a-delivery-template.md)中進一步瞭解傳遞範本。

## 開始使用傳遞範本 {#gs-templates}

[傳遞範本](creating-a-delivery-template.md)可讓您定義一次符合您需求且可重複用於未來傳遞的一組技術和功能屬性。 然後您可以節省時間，並在需要時標準化傳遞。

當您在Adobe Campaign中管理多個品牌時，Adobe建議每個品牌使用一個子網域。 例如，銀行可以有數個子網域對應至其各個地區機構。 如果銀行擁有bluebank.com網域，其子網域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每個子網域擁有一個傳遞範本，可讓您針對每個品牌一律使用正確的預先設定引數，以避免錯誤並節省您的時間。

**提示**：若要避免設定錯誤，建議您複製原生範本並變更其屬性，而非建立新範本。

## 設定地址

* 寄件者的地址為必要項，才能傳送電子郵件。

* 有些ISP （網際網路服務提供者）在接受訊息之前，會先檢查寄件者地址的有效性。

* 格式錯誤的位址可能會導致接收伺服器拒絕該位址。 您必須確定已提供正確的地址。

* 地址必須明確識別寄件者。 網域必須屬於寄件者且已註冊給寄件者。

* Adobe建議建立對應至傳送和回覆所指定地址的電子郵件帳戶。 請洽詢您的傳訊系統管理員。

若要在Campaign介面中設定地址，請遵循下列步驟：

1. 在[傳遞範本](creating-a-delivery-template.md)中，按一下&#x200B;**[!UICONTROL From]**&#x200B;連結。 在&#x200B;**[!UICONTROL Email header parameters]**&#x200B;視窗中，填寫下列欄位：

   ![](assets/d_best_practices_email_header.png)

1. 在&#x200B;**[!UICONTROL Sender address]**&#x200B;欄位中，確定位址網域與您委派給Adobe的子網域相同。 您可以變更&#39;@&#39;之前的部分，但無法變更網域位址。

1. 在&#x200B;**[!UICONTROL From]**&#x200B;欄位中，使用收件者可輕鬆辨識的名稱（例如您的品牌名稱），以提高您傳送的開頭率。 若要進一步改善收件者的體驗，您可以新增個人名稱，例如「Emma from Megastore」。

1. 在&#x200B;**[!UICONTROL Reply address text]**&#x200B;欄位中，預設會使用寄件者的地址來回覆。 不過，Adobe建議使用現有的實際地址，例如您品牌的客戶服務。 在此情況下，如果收件者傳送回覆，客戶服務將能夠處理。

### 設定控制組

傳送傳遞後，您可以將排除的收件者與收到傳遞的收件者之行為進行比較。 接著，您就可以評估行銷活動的效率。 深入瞭解控制群組[本節](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

若要設定控制組，請按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。 在&#x200B;**[!UICONTROL Select target]**&#x200B;視窗中，選取&#x200B;**[!UICONTROL Control group]**&#x200B;標籤。 您可以擷取部分目標，例如5%隨機抽樣。

![](assets/d_best_practices_control_group.png)

## 使用型別來套用篩選器或控制規則

型別包含在傳送任何訊息之前，在分析階段套用的檢查規則。

在範本屬性的&#x200B;**[!UICONTROL Typology]**&#x200B;標籤中，根據您的需求變更預設型別。

例如，為了更能控制傳出流量，您可以定義要使用的IP位址，方法為為每個子網域定義一個相似性，並為每個相似性建立一種型別。 相似性是在執行個體的組態檔案中定義。 請連絡您的Adobe Campaign管理員。

如需型別的詳細資訊，請參閱[本節](../../campaign-opt/using/about-campaign-typologies.md)。
