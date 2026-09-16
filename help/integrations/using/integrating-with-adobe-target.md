---
product: campaign
title: 使用Adobe Campaign和Adobe Target
description: 瞭解如何將Adobe Campaign與Adobe Target整合
feature: Target Integration
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
TQID: https://experienceleague.adobe.com/f58vs0ePAH-7bcfJ8u1GKLzcz0-fHnrwFyOVUWOFW-o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Adobe Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Adobe Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Adobe Target integration
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# 合作使用Campaign與Target{#integrating-with-adobe-target}



使用Adobe Campaign搭配Adobe Target來最佳化電子郵件內容。

若要最佳化您的電子郵件內容，您可以在Adobe Target中建立重新導向選件，然後使用Adobe Campaign來管理電子郵件選件。 例如，您可以為男性收件者和女性收件者顯示不同的優惠方案。

整合會在電子郵件開啟時進行。 客戶開啟電子郵件時，會呼叫Target並顯示內容的動態版本。 內容包含所有瀏覽器都支援的靜態影像。 Target會追蹤對象或工作階段層級對選件的反應，且這些資料可在Target報表中使用。 [在Adobe Target檔案中進一步瞭解](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=zh-Hant)。


>[!NOTE]
>
>整合僅支援靜態影像。 其他內容無法個人化。

Adobe Target可運用數種型別的資料：

* 來自Adobe Campaign資料市場的資料
* 若所使用的資料不受法律限制，則連結至Adobe Target中的訪客ID的區段
* Adobe Target資料：使用者代理、IP位址、地理位置資料
