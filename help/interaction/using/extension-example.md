---
product: campaign
title: 擴充功能範例
description: 擴充功能範例
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# 擴充功能範例{#extension-example}

若是傳入連絡人（客服中心或網站），系統會使用一組適用性規則，向指定連絡人建議最相關的優惠方案。 若要豐富優惠方案的資格標準，請擴充&#x200B;**nms:interaction**&#x200B;方案。

* 若要新增互動內容，請擴充&#x200B;**nms:interaction**&#x200B;架構，並視需要在架構中建立多個&#x200B;**attribute**&#x200B;元素。

   在下列範例中，新增的條件為國家/地區代碼和上次造訪的頁面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然後，您就可以使用先前在定義適用性條件定義時建立的屬性。

   在下列範例中，我們可以建立資格條件，根據使用者的國家/地區或他們檢視的最後一個網頁，來顯示優惠方案。

   ![](assets/s_ncs_configuration_offer_context.png)

* 配置SOAP調用時，插入&#x200B;**context** XML元素以參考在交互架構中添加的上下文資訊。 如需詳細資訊，請參閱[透過SOAP整合（伺服器端）](../../interaction/using/integration-via-soap--server-side-.md)。
