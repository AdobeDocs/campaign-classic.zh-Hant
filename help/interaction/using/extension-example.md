---
product: campaign
title: 擴充功能範例
description: 擴充功能範例
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 07a5742c6f142c786ad8ba2f8774e7e90e8cd191
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# 擴充功能範例{#extension-example}

![](../../assets/common.svg)

若是傳入連絡人（客服中心或網站），系統會使用一組適用性規則，向指定連絡人建議最相關的優惠方案。 若要豐富優惠方案的資格條件，請擴充 **nms:interaction** 綱要。

* 若要新增互動內容，請擴充 **nms:interaction** 架構和建立數量 **屬性** 元素。

   在下列範例中，新增的條件是國家/地區代碼和上次造訪的頁面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然後，您就可以使用先前在定義適用性條件定義時建立的屬性。

   在下列範例中，我們可以建立資格條件，根據使用者的國家/地區或他們檢視的最後一個網頁，來顯示優惠方案。

   ![](assets/s_ncs_configuration_offer_context.png)

* 設定SOAP呼叫時，插入 **內容** XML元素，以參考在互動架構中新增的內容資訊。 有關詳細資訊，請參閱 [透過SOAP整合（伺服器端）](../../interaction/using/integration-via-soap--server-side-.md).
