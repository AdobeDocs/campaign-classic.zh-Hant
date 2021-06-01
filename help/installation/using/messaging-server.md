---
product: campaign
title: 傳訊伺服器
description: 傳訊伺服器
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# 傳訊伺服器{#messaging-server}

Adobe Campaign會以原生方式處理傳出電子郵件，但傳統電子郵件伺服器需要用來接收連結至傳回電子郵件（從郵件程式守護程式）的傳入訊息。 應用程式將自動處理在此伺服器上配置的郵箱。

如果為POP3訪問配置的所有伺服器在拾取郵件時保留SMTP「Message-ID」標頭，則它們可用於接收返回郵件。 例如，使用Qmail、SendMail和Microsoft Exchange的實施目前正在生產中。 但是，Lotus Notes/domino的某些安裝顯示了維護「Message-Id」標頭的問題。

>[!CAUTION]
>
>此郵件伺服器可能必須處理重負載：在初始階段，一般清單最多可產生10%的反彈率（如果您傳送100,000則訊息，預期會收到10,000則反彈）。
>
>這就是為什麼我們建議不要針對此任務使用您的公司訊息傳送伺服器，因為它可能會受到強烈影響。
>
>建議您配置DNS的特定子網域和退回郵件專用伺服器。
