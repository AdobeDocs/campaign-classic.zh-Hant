---
product: campaign
title: Technote - Apple推播通知服務伺服器憑證更新
description: Apple推播通知服務伺服器憑證更新
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Apple推播通知服務伺服器憑證更新 {#apns-certificate-update}

![](../../assets/v7-only.svg)

2021年3月29日，Apple推播通知服務(APN)基礎架構更新影響了Adobe Campaign Classic iOS頻道。 作業系統組態變更為 **強制** 以避免iOS推播通道中斷。

了解有關APN更改的更多資訊 [在本頁](https://developer.apple.com/news/?id=7gx0a2lp).

身為托管客戶，不需要採取任何動作：Adobe已將新的根憑證整合至您的環境。

身為內部部署/混合式客戶，您需要更新設定以確保順暢轉換 **2021年3月29日前**.

若要合併新憑證，請遵循下列步驟：

1. 下載 **AAACertificateServices 5/12/2020** 根證書 [從本頁面](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. 檢查您的OS和JAVAtrustore中都有AAA憑證。 如果沒有，請新增。

1. 重新啟動Adobe Campaign Web服務：

   ```
   nlserver restart web
   ```
