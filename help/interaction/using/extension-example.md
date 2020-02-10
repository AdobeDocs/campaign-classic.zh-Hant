---
title: 擴充功能範例
seo-title: 擴充功能範例
description: 擴充功能範例
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 擴充功能範例{#extension-example}

若是來電連絡人（客服中心或網站），則會使用一組資格規則向特定連絡人建議最相關的優惠。 若要豐富選件的資格標準，請擴充 **nms:interaction** 架構。

* 要添加新的交互上下文，請擴展 **nms:interaction** 架構，並在架構中建立 **** 任意數量的屬性元素。

   在下列範例中，新增的准則是國家代碼和上次瀏覽的頁面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然後，您可以在定義資格標準定義時使用先前建立的屬性。

   在下列範例中，我們可建立資格標準，以根據使用者的國家／地區或他們上次檢視的網頁來顯示選件。

   ![](assets/s_ncs_configuration_offer_context.png)

* 設定SOAP呼叫時，請插入 **上下文** XML元素，以參考互動架構中新增的上下文資訊。 如需詳細資訊，請參 [閱「透過SOAP（伺服器端）進行整合」](../../interaction/using/integration-via-soap--server-side-.md)。

