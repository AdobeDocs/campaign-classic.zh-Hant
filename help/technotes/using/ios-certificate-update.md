---
product: campaign
title: 技術檔案
description: 技術檔案
hide: false
hidefromtoc: true
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Apple推播通知服務伺服器憑證更新 {#apns-certificate-update}

![](../../assets/v7-only.svg)

2021年3月29日起，Apple推播通知服務(APN)基礎架構更新將影響Adobe Campaign Classic iOS通道。 作業系統組態變更為&#x200B;**強制**，以避免iOS推播通道中斷。

了解更多有關APN更改[的資訊，請參閱本頁](https://developer.apple.com/news/?id=7gx0a2lp)。

身為托管客戶，不需要採取任何動作：Adobe已將新的根憑證整合至您的環境。

身為內部部署/混合客戶，您必須更新設定，以確保在2021年3月29日前&#x200B;**順暢轉換**。

若要合併新憑證，請遵循下列步驟：

1. 從此頁面](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL)下載&#x200B;**AAACertificateServices 5/12/2020**&#x200B;根憑證[。

1. 檢查您的OS和JAVAtrustore中都有AAA憑證。 如果沒有，請新增。

1. 重新啟動Adobe Campaign Web服務：

   ```
   nlserver restart web
   ```
