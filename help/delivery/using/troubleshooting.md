---
product: campaign
title: 疑難排解
description: 疑難排解
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---

# 疑難排解{#troubleshooting}

如果您的行動裝置已連線至Wi-Fi，而您未收到通知，請檢查防火牆是否未封鎖FCM/APN埠。

**Android**:行動裝置連接至連接埠5228至5230的FCM伺服器。因此，您必須設定防火牆，以授權其與FCM連線。 要開啟的埠包括：5228（最常使用）、5229和5230。

**iOS**:

HTTP/2連接器：您必須允許與以下伺服器進行通信：

* api.push.apple.com:埠443
* api.development.push.apple.com:埠443

>[!NOTE]
>
>有關這兩個連接器的詳細資訊，請參閱[在Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md)。
