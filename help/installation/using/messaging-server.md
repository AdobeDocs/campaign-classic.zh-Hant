---
title: 消息伺服器
seo-title: 消息伺服器
description: 消息伺服器
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 消息伺服器{#messaging-server}

Adobe Campaign會以原生方式處理傳出電子郵件，但傳統電子郵件伺服器必須接收連結至傳回電子郵件（來自郵件守護程式）的傳入訊息。 應用程式將自動處理在此伺服器上配置的郵箱。

如果為POP3訪問配置的所有伺服器在拾取郵件時保留了SMTP &quot;Message-ID&quot;標頭，則可以使用這些伺服器接收返回郵件。 例如，使用Qmail、SendMail和Microsoft exchange的實作目前正在生產中。 但是，Lotus Notes/domino的某些安裝顯示了維護&quot;Message-Id&quot;標頭的問題。

>[!CAUTION]
>
>此郵件伺服器可能必須處理大量負載：在初始階段，一般清單可產生高達10%的反彈率（如果您傳送100,000則訊息，預期會收到10,000則反彈）。
>
>因此，我們建議您不要針對此工作使用您的公司訊息伺服器，因為它可能會受到強烈影響。
>
>建議您配置DNS的特定子域和彈回郵件專用伺服器。
