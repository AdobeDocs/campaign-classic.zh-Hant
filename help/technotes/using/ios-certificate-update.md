---
product: campaign
title: Technote - Apple推播通知服務伺服器憑證更新
description: Apple推播通知服務伺服器憑證更新
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Apple推播通知服務伺服器憑證更新 {#apns-certificate-update}



2021年3月29日，Apple推播通知服務(APN)基礎架構更新影響Adobe Campaign Classic iOS頻道。 作業系統設定變更為&#x200B;**必要**，以避免iOS推播頻道中斷。

在此頁面](https://developer.apple.com/news/?id=7gx0a2lp)中進一步瞭解APN變更[。

作為託管客戶，無需採取任何動作：Adobe已將新的根憑證整合至您的環境。

作為內部部署/混合部署客戶，您需要更新設定，以確保在2021年3月29日之前&#x200B;**無縫轉換**。

若要合併新憑證，請遵循下列步驟：

1. 從此頁面](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL)下載&#x200B;**AAACertificateServices 5/12/2020**&#x200B;根憑證[。

1. 檢查您的OS和JAVA Trustores中是否都有AAA憑證。 如果沒有，請新增它。

1. 重新啟動Adobe Campaign Web服務：

   ```
   nlserver restart web
   ```
