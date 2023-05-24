---
product: campaign
title: 傳訊伺服器
description: 傳訊伺服器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# 傳訊伺服器{#messaging-server}



Adobe Campaign會以原生方式處理傳出電子郵件，但需要傳統電子郵件伺服器來接收連結到傳回電子郵件的傳入訊息（來自郵件程式守護程式）。 應用程式會自動處理此伺服器上設定的信箱。

如果設定為POP3存取權的所有伺服器在擷取郵件時保留SMTP「Message-ID」標頭，則可以用來接收回信。 例如，使用Qmail、SendMail和Microsoft Exchange的實施目前正在生產中。 不過，Lotus Notes/domino的某些安裝顯示「Message-Id」標頭的維護有問題。

>[!CAUTION]
>
>此郵件伺服器可能必須處理大量負載：在初始階段，一般清單最多可產生10%的跳出率（如果您傳送100,000則郵件，預期會收到10,000則跳出）。
>
>因此我們建議不要使用此工作的公司傳訊伺服器，因為它可能會受到強烈的影響。
>
>建議您設定DNS的特定子網域和專用伺服器來退回郵件。
