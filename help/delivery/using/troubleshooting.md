---
title: 疑難排解
seo-title: 疑難排解
description: 疑難排解
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa2b6890d3c9eaf7b4b6521b2edfb494faa4798c

---


# 疑難排解{#troubleshooting}

如果您的移動設備已連接到Wi-Fi，而您未收到通知，請檢查防火牆是否未阻止FCM/APNS埠。

**Android**:移動設備連接到埠5228到5230上的FCM伺服器。 因此，必須配置防火牆，以便它授權與FCM的連接。 要開啟的埠包括：5228（最常使用）、5229和5230。

**iOS**:

二進位連接器：要發送通知，您必須授權埠2195上的入站和出站TCP通信。 連接到推送服務的設備必須授權埠5223上的入站和出站TCP通信。

HTTP/2連接器：您必須允許與下列伺服器通訊：

* api.push.apple.com:埠443
* api.development.push.apple.com:埠443

>[!NOTE]
>
>如需兩個連接器的詳細資訊，請參 [閱在Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md)。
