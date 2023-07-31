---
product: campaign
title: Technote - Apple推播通知服務伺服器憑證更新
description: Apple推播通知服務伺服器憑證更新
feature: Technote, Push
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Apple推播通知服務伺服器憑證更新 {#apns-certificate-update}



2021年3月29日，Apple推播通知服務(APN)基礎架構更新影響Adobe Campaign Classic iOS頻道。 作業系統組態變更為 **強制** 以避免iOS推播頻道中斷。

深入瞭解APN變更 [在此頁面中](https://developer.apple.com/news/?id=7gx0a2lp).

作為託管客戶，無需採取任何動作：Adobe已將新的根憑證整合至您的環境。

身為內部部署/混合部署客戶，您需要更新設定以確保順暢轉換 **2021年3月29日前**.

若要合併新憑證，請遵循下列步驟：

1. 下載 **AAACertificateServices 5/12/2020** 根憑證 [從此頁面](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. 檢查您的OS和JAVA Trustores中是否都有AAA憑證。 如果沒有，請新增它。

1. 重新啟動Adobe Campaign Web服務：

   ```
   nlserver restart web
   ```
