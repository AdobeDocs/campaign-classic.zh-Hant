---
product: campaign
title: 使用傳遞範本
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# 使用範本 {#use-templates}

傳遞範本可為最常見的活動類型提供現成的案例，借此提高效率。 透過範本，行銷人員可以在較短的時間內以最少的自訂方式部署新的行銷活動。

在[此小節](../../delivery/using/creating-a-delivery-template.md)中深入了解傳遞範本。

## 開始使用傳遞範本{#gs-templates}

[傳遞範本](../../delivery/using/creating-a-delivery-template.md)可讓您一次定義一組符合您需求且可重複使用的技術和功能屬性。 然後，您就可以視需要節省時間並標準化傳送。

當您在Adobe Campaign中管理多個品牌時，Adobe建議每個品牌有一個子網域。 例如，銀行可以有與其每個地區機構對應的數個子網域。 如果銀行擁有bluebank.com域，其子域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每個子網域有一個傳送範本可讓您一律為每個品牌使用正確的預先設定參數，以避免錯誤並節省時間。

**提示**:為避免設定錯誤，建議您複製原生範本並變更其屬性，而非建立新範本。

## 配置地址

* 寄件者的地址是必填欄位，以允許傳送電子郵件。

* 某些ISP（網際網路服務提供者）在接受訊息之前，會檢查寄件者地址的有效性。

* 錯誤形成的地址可能導致接收伺服器拒絕該地址。 您必須確保提供正確的地址。

* 地址必須明確標識發件人。 域必須由發件人擁有並註冊。

* Adobe建議建立與為傳送和回覆指定的地址對應的電子郵件帳戶。 請咨詢您的消息系統管理員。

若要在Campaign介面中設定位址，請遵循下列步驟：

1. 在[傳遞範本](../../delivery/using/creating-a-delivery-template.md)中，按一下&#x200B;**[!UICONTROL From]**&#x200B;連結。 在&#x200B;**[!UICONTROL Email header parameters]**&#x200B;視窗中，填寫下列欄位：

   ![](assets/d_best_practices_email_header.png)

1. 在&#x200B;**[!UICONTROL Sender address]**&#x200B;欄位中，確認地址域與您委派給Adobe的子網域相同。 您可以更改「@」之前的部分，但不能更改域地址。

1. 在&#x200B;**[!UICONTROL From]**&#x200B;欄位中，使用可供收件者輕鬆識別的名稱（例如您的品牌名稱），以提高傳送的開始率。 若要進一步改善收件者的體驗，您可以新增人員名稱，例如「Emma from Megastore」。

1. 在&#x200B;**[!UICONTROL Reply address text]**&#x200B;欄位中，預設會使用寄件者的地址進行回覆。 不過，Adobe建議使用現有的實際位址，例如您的品牌客戶服務。 在此情況下，如果收件者傳送回覆，客戶服務將能處理。

### 設定控制組

傳送後，您可以比較已排除收件者的行為與已接收傳送的收件者。 然後，您可以測量行銷活動的效率。 進一步了解控制組[此部分](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

若要設定控制組，請按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。 在&#x200B;**[!UICONTROL Select target]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Control group]**&#x200B;頁簽。 您可以擷取目標的一部分，例如5%的隨機樣本。

![](assets/d_best_practices_control_group.png)

## 使用類型來套用篩選器或控制規則

類型包含在分析階段期間套用的檢查規則，然後再傳送任何訊息。

在範本屬性的&#x200B;**[!UICONTROL Typology]**&#x200B;標籤中，根據您的需求變更預設類型。

例如，為了更妥善地控制傳出流量，您可以定義可使用的IP位址，方法是為每個子網域定義一個相關性，並為每個相關性建立一個類型。 相關性會在執行個體的設定檔案中定義。 請連絡您的Adobe Campaign管理員。

有關類型的詳細資訊，請參閱[此區段](../../campaign/using/about-campaign-typologies.md)。
