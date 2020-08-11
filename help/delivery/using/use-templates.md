---
title: 使用傳送範本
seo-title: 使用傳送範本
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# 使用範本 {#use-templates}

提供範本可針對大多數常見活動類型提供現成的藍本，以提高效率。 使用範本，行銷人員可以在較短的時間內，以最少的自訂方式部署新的促銷活動。

在本節中進一步瞭解傳送 [範本](../../delivery/using/creating-a-delivery-template.md)。

## 開始使用傳送範本 {#gs-templates}

交 [貨範本](../../delivery/using/creating-a-delivery-template.md) ，可讓您定義一組符合您需求且可重複使用於未來交貨的技術和功能屬性。 然後，您就可以節省時間，並視需要標準化傳送。

當您在Adobe Campaign中管理多個品牌時，Adobe建議每個品牌擁有一個子網域。 例如，銀行可以有多個子域，對應其每個區域機構。 如果銀行擁有bluebank.com網域，其子網域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每個子網域有一個傳送範本，讓您隨時針對每個品牌使用正確的預先設定參數，以避免錯誤並節省您的時間。

**提示**: 為避免Campaign Standard中的設定錯誤，建議您複製原生範本並變更其屬性，而非建立新範本。

## 配置地址

* 傳送者的地址是強制性的，以允許傳送電子郵件。

* 某些ISP（Internet服務提供商）在接受消息之前檢查發件人地址的有效性。

* 錯誤形成的地址可能導致接收伺服器拒絕。 您必須確定地址正確無誤。

* 地址必須明確標識發件人。 域必須由發送者擁有並註冊。

* Adobe建議建立與傳送和回覆所指定之位址對應的電子郵件帳戶。 請洽詢您的訊息系統管理員。

若要在促銷活動介面中設定位址，請遵循下列步驟：

1. 在傳送 [範本中](../../delivery/using/creating-a-delivery-template.md)，按一下 **[!UICONTROL From]** 連結。 在視窗 **[!UICONTROL Email header parameters]** 中，填寫下列欄位：

   ![](assets/d_best_practices_email_header.png)

1. 在欄位 **[!UICONTROL Sender address]** 中，請確定位址網域與您委派給Adobe的子網域相同。 您可以變更&#39;@&#39;前的部分，但不能變更網域位址。

1. 在欄位 **[!UICONTROL From]** 中，使用收件者可輕易辨識的名稱（例如您的品牌名稱），以提高您的交貨的開業率。 若要進一步改善收件者的體驗，您可以新增人名，例如「Emma from Megastore」。

1. 在欄位 **[!UICONTROL Reply address text]** 中，預設會使用傳送者的位址來回覆。 不過，Adobe建議使用現有的實際地址，例如您品牌的客戶服務。 在這種情況下，如果收件者傳送回覆，客戶服務將能夠處理。

### 設定控制群組

傳送傳送後，您可以比較已排除的收件者與已接收傳送的收件者的行為。 然後，您可以衡量促銷活動的效率。 請進一步瞭解本節中 [的控制群組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

若要設定控制群組，請按一下連 **[!UICONTROL To]** 結。 在窗口 **[!UICONTROL Select target]** 中，選擇該選 **[!UICONTROL Control group]** 項卡。 您可以擷取目標的一部分，例如5%的隨機樣本。

![](assets/d_best_practices_control_group.png)

## 使用類型套用篩選或控制規則

類型學包含分析階段期間在傳送任何訊息之前套用的檢查規則。

在範本 **[!UICONTROL Typology]** 屬性的索引標籤中，根據您的需求變更預設類型。

例如，為了更好地控制對外流量，您可以定義每個子網域可使用一個相似性，並為每個相似性建立一個類型，以定義哪些IP位址。 相關性在實例的配置檔案中定義。 請洽詢您的Adobe Campaign管理員。

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).
