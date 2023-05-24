---
product: campaign
title: 擴充功能範例
description: 擴充功能範例
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# 擴充功能範例{#extension-example}



如果是傳入連絡人（客服中心或網站），系統會使用一組適用性規則，向指定連絡人建議最相關的優惠方案。 若要豐富優惠方案的資格標準，請將 **nms：interaction** 結構描述。

* 若要新增互動內容，請擴充 **nms：interaction** 結構描述和建立儘可能多的 **屬性** 結構描述中必要的元素。

   在以下範例中，新增的標準為國家/地區代碼和上次造訪的頁面。

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 然後，您可以在定義適用性條件定義時，使用先前建立的屬性。

   在以下範例中，我們可以建立適用性條件，以根據使用者所在的國家/地區或他們檢視的最後一個網頁來顯示優惠方案。

   ![](assets/s_ncs_configuration_offer_context.png)

* 設定SOAP呼叫時，插入 **內容** 用於參照在互動結構描述中新增的內容資訊的XML元素。 如需詳細資訊，請參閱 [透過SOAP整合（伺服器端）](../../interaction/using/integration-via-soap--server-side-.md).
