---
product: campaign
title: 傳訊伺服器
description: 傳訊伺服器
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 3%

---

# 傳訊伺服器{#messaging-server}



Adobe Campaign會以原生方式處理傳出電子郵件，但需要傳統電子郵件伺服器來接收連結至傳回電子郵件的傳入訊息（來自郵件程式常駐程式）。 應用程式會自動處理此伺服器上設定的信箱。

如果設定為POP3存取權的所有伺服器擷取郵件時都保留了SMTP「郵件ID」標頭，則這些伺服器都可用於接收回信。 例如，使用Qmail、SendMail和Microsoft Exchange的實施目前正在生產中。 然而，部分Lotus Notes/domino的安裝顯示「Message-Id」標題的維護有問題。

>[!CAUTION]
>
>此郵件伺服器可能必須處理大量負載：在初始階段，一般清單最多可產生10%的跳出率（如果您傳送100,000封郵件，預期會收到10,000封跳出）。
>
>這就是為什麼我們建議不要將您的公司傳訊伺服器用於此工作，因為它可能會受到強烈的影響。
>
>建議您設定DNS的特定子網域以及退回郵件的專用伺服器。
