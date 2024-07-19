---
product: campaign
title: 推播疑難排解
description: 推播疑難排解
feature: Push, Troubleshooting
role: User
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '108'
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
