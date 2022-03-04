---
product: campaign
title: 使用傳遞範本
description: 使用傳遞範本
feature: Delivery Templates
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# 使用範本 {#use-templates}

![](../../assets/common.svg)

交付模板通過為大多數常見活動類型提供現成的方案而提高了效率。 使用模板，營銷人員可以在較短的時間內部署具有最小定制量的新市場活動。

瞭解有關中的交付模板的詳細資訊 [此部分](creating-a-delivery-template.md)。

## 交貨模板入門 {#gs-templates}

A [交貨模板](creating-a-delivery-template.md) 使您能夠一次定義一組適合您需要且可重複使用以用於將來交貨的技術和功能屬性。 然後，您可以節省時間，並在需要時使交貨標準化。

當您在Adobe Campaign管理多個品牌時，Adobe建議每個品牌有一個子域。 例如，銀行可以具有與其每個區域機構對應的多個子域。 如果銀行擁有bluebank.com域，其子域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每個子域有一個交付模板使您始終能夠為每個品牌使用正確的預先配置的參數，這樣可避免錯誤並節省時間。

**提示**:為避免配置錯誤，建議您複製本機模板並更改其屬性，而不是建立新模板。

## 配置地址

* 發件人地址是允許發送電子郵件的必需地址。

* 某些ISP（Internet服務提供商）在接受消息之前檢查發送者地址的有效性。

* 格式錯誤的地址可能導致接收伺服器拒絕它。 您必須確保提供了正確的地址。

* 地址必須明確標識發件人。 域必須由發件人擁有並註冊。

* Adobe建議建立與為遞送和回復指定的地址對應的電子郵件帳戶。 請咨詢消息系統管理員。

要在市場活動介面中配置地址，請執行以下步驟：

1. 在 [交貨模板](creating-a-delivery-template.md)，按一下 **[!UICONTROL From]** 的子菜單。 在 **[!UICONTROL Email header parameters]** 的子菜單。

   ![](assets/d_best_practices_email_header.png)

1. 在 **[!UICONTROL Sender address]** 欄位，確保地址域與您委託給Adobe的子域相同。 您可以更改「@」之前的部件，但不能更改域地址。

1. 在 **[!UICONTROL From]** 欄位中，使用易於被收件人識別的名稱（如您的品牌名稱）來增加交貨的開始率。 為了進一步改善接收者的體驗，您可以添加一個人的姓名，例如「Emma from Megastore」。

1. 在 **[!UICONTROL Reply address text]** 欄位中，預設情況下使用發件人地址進行答復。 但是，Adobe建議使用現有的實際地址，如您品牌的客戶服務。 在這種情況下，如果收件人發送回復，客戶服務將能夠處理。

### 設定控制組

發送遞送後，您可以將排除的收件人的行為與收到遞送的收件人進行比較。 然後，您可以衡量您的活動的效率。 瞭解有關控制組的詳細資訊 [此部分](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

要設定控制組，請按一下 **[!UICONTROL To]** 的子菜單。 在 **[!UICONTROL Select target]** ，選擇 **[!UICONTROL Control group]** 頁籤。 可以提取目標的一部分，例如5%的隨機樣本。

![](assets/d_best_practices_control_group.png)

## 使用類型來應用篩選器或控制規則

類型包含在分析階段應用的檢查規則，然後才會發送任何消息。

在 **[!UICONTROL Typology]** 的子菜單。

例如，為了更好地控制出站通信量，可以通過為每個子域定義一個關聯和為每個關聯建立一個類型來定義可以使用哪些IP地址。 關聯在實例的配置檔案中定義。 聯繫您的Adobe Campaign管理員。

有關類型的詳細資訊，請參閱 [此部分](../../campaign-opt/using/about-campaign-typologies.md)。
