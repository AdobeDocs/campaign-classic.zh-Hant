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



Adobe Campaign以本機方式處理出站電子郵件，但是，傳統電子郵件伺服器需要接收連結到返回的電子郵件（從郵件程式守護程式）的傳入郵件。 此伺服器上配置的郵箱將由應用程式自動處理。

如果為POP3訪問配置的所有伺服器在收集郵件時保留SMTP「Message-ID」標頭，則它們可用於接收返回郵件。 例如，使用Qmail、SendMail和MicrosoftExchange的實施目前正在生產中。 但是，Lotus Notes/domino的某些安裝顯示了維護「Message-Id」標頭的問題。

>[!CAUTION]
>
>此郵件伺服器可能必須處理繁重的負載：在初始階段，典型清單的彈跳率最高可達10%（如果您發送10萬條消息，則預期會收到10,000條回報）。
>
>因此，我們建議不要將您公司的消息伺服器用於此任務，因為它可能會受到強烈影響。
>
>建議為DNS的特定子域和用於彈回郵件的專用伺服器進行配置。
