---
product: campaign
title: 疑難排解
description: 疑難排解
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---

# 疑難排解{#troubleshooting}

![](../../assets/common.svg)

如果您的移動設備已連接到Wi-Fi，並且您未收到通知，請檢查防火牆是否未阻止FCM/APNs埠。

**安卓**:移動設備連接到埠5228到5230上的FCM伺服器。 因此，必須配置防火牆，以便它授權與FCM的連接。 要開啟的埠包括：5228（使用頻率最高）、5229和5230。

**iOS**:

HTTP/2連接器：您必須允許與以下伺服器通信：

* api.push.apple.com:埠443
* api.development.push.apple.com:埠443

>[!NOTE]
>
>有關兩個連接器的詳細資訊，請參閱 [在Adobe Campaign配置移動應用程式](configuring-the-mobile-application.md)。
