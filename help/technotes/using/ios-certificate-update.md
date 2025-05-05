---
product: campaign
title: Technote - Apple推播通知服務伺服器憑證更新
description: Apple推播通知服務伺服器憑證更新
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Apple推播通知服務伺服器憑證更新 {#apns-certificate-update}



2024年10月17日，Apple推播通知服務(APN)基礎架構更新影響Adobe Campaign Classic iOS頻道。 作業系統設定變更為&#x200B;**必要**，以避免iOS推播頻道中斷。

在此頁面[&#128279;](https://developer.apple.com/news/?id=09za8wzy)中進一步瞭解APN變更。

作為託管客戶，無需採取任何動作：Adobe已將新的根憑證整合至您的環境。

作為內部部署/混合部署客戶，您需要更新設定，以確保在2025年2月24日之前順暢轉換&#x200B;**&#x200B;**。

若要合併新憑證，請遵循下列步驟：

1. 從此頁面[&#128279;](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO)下載&#x200B;**SHA-2根： USERTrust RSA Certification Authority憑證**&#x200B;根憑證。

1. 檢查您的OS和JAVA Trustores中是否都有AAA憑證。 如果沒有，請新增它。

1. 重新啟動Adobe Campaign Web服務：

   ```
   nlserver restart web
   ```
