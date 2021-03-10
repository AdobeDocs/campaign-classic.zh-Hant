---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: a21f970b6b81105517a11bcbd7f334173acc76e4
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Apple推播通知服務伺服器憑證更新{#apns-certificate-update}

在2021年3月29日，Apple推播通知服務(APNs)基礎架構更新將影響Adobe Campaign ClassiciOS頻道。 作業系統組態變更為&#x200B;**mandatory**&#x200B;以避免iOS推播頻道中斷。

在本頁](https://developer.apple.com/news/?id=7gx0a2lp)中進一步瞭解APN更改[。

身為代管客戶，您不需採取任何動作：Adobe已將新的根證書整合到您的環境中。

身為內部部署／混合型客戶，您需要更新您的設定，以確保在2021年3月29日前順暢地進行&#x200B;**轉換。**

若要合併新憑證，請遵循下列步驟：

1. 從本頁](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL)下載&#x200B;**AAACertificateServices 5/12/2020**&#x200B;根證書[。

1. 將它新增至作業系統信任商店。

1. 重新啟動Adobe CampaignWeb服務：

   ```
   nlserver restart web
   ```
