---
product: campaign
title: 推播疑難排解
description: 推播疑難排解
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
TQID: https://experienceleague.adobe.com/3T6eC52Edyai-8Bn-ioDxvB5C04iDqBNmlZzuxVturE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 109
ht-degree: 0%

---

# 疑難排解{#troubleshooting}

如果您的行動裝置已連線至Wi-Fi，但您未收到通知，請檢查防火牆是否未封鎖FCM/APNs連線埠。

**Android**：行動裝置已連線到連線埠5228到5230上的FCM伺服器。 因此，您必須設定防火牆，使其可授權與FCM的連線。 要開啟的連線埠為：5228 （最常使用）、5229和5230。

**iOS**：

HTTP/2聯結器：您必須允許與下列伺服器之間的通訊：

* api.push.apple.com：連線埠443
* api.development.push.apple.com：連線埠443

>[!NOTE]
>
>如需這兩個聯結器的詳細資訊，請參閱[在Adobe Campaign中設定行動應用程式](configuring-the-mobile-application.md)。
