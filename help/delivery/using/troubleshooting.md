---
solution: Campaign Classic
product: campaign
title: 疑難排解
description: 疑難排解
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 22f44f5723ab35e95caa438583fe06314c763ba1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---


# 疑難排解{#troubleshooting}

如果您的移動設備已連接到Wi-Fi，而您未收到通知，請檢查防火牆是否未阻止FCM/APN埠。

**Android**:移動設備連接到埠5228到5230上的FCM伺服器。因此，必須配置防火牆，以便它授權與FCM的連接。 要開啟的埠包括：5228（最常使用）、5229和5230。

**iOS**:

HTTP/2連接器：您必須允許與下列伺服器通訊：

* api.push.apple.com:埠443
* api.development.push.apple.com:埠443

>[!NOTE]
>
>如需兩個連接器的詳細資訊，請參閱[在Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md)。
