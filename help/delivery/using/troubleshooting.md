---
product: campaign
title: 推送疑難排解
description: 推送疑難排解
feature: Push
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 8d635722b8961b3edac9cc98f00f17b86f4ee523
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

---

# 疑難排解{#troubleshooting}

![](../../assets/v7-only.svg)

如果您的行動裝置已連線至Wi-Fi，而您未收到通知，請檢查防火牆是否未封鎖FCM/APN埠。

**Android**:行動裝置連接至連接埠5228至5230的FCM伺服器。 因此，您必須設定防火牆，以授權其與FCM連線。 要開啟的埠包括：5228（最常使用）、5229和5230。

**iOS**:

HTTP/2連接器：您必須允許與以下伺服器進行通信：

* api.push.apple.com:埠443
* api.development.push.apple.com:埠443

>[!NOTE]
>
>有關兩個連接器的詳細資訊，請參閱 [在Adobe Campaign中設定行動應用程式](configuring-the-mobile-application.md).
