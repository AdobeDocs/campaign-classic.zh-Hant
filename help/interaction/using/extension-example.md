---
solution: Campaign Classic
product: campaign
title: 擴充功能範例
description: 擴充功能範例
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

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

