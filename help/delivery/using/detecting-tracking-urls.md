---
product: campaign
title: 偵測追蹤URL
description: 深入瞭解追蹤URL的建議模式
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: 'https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%
---
# 偵測追蹤 URL

Adobe Campaign會在傳遞分析期間偵測要追蹤內容的URL。

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要瞭解如何偵測URL以及要使用哪些模式，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}

## 不安全的模式

將個人化連結新增至您的內容時，請一律避免URL的主機名稱部分有任何個人化專案，以避免潛在的安全性缺口。 在[本頁](../../installation/using/privacy.md#url-personalization)中瞭解更多。

例如，`<a href="http://<%=myURL%>">`語法是&#x200B;**不安全**，必須避免。

* 如果Adobe Campaign產生的連結包含一或多個引數，使用此語法可能會導致安全性問題。
* 整備可能會錯誤地修補某些連結，這可能隨機發生。 典型症狀是一段HTML，可在電子郵件校樣中看到，但預覽中看不到。
* URL的逸出有問題，URL中的某些字元可能會導致問題。
* 名稱為ID的引數不能與重新導向URL中的引數相衝突。
* 因此，追蹤的興趣會限製為傳送的統計資料，因為Adobe Campaign會以不同方式追蹤「myURL」的所有可能值。
