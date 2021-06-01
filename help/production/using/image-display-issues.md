---
product: campaign
title: 影像顯示問題
description: 影像顯示問題
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# 影像顯示問題{#image-display-issues}

如果您在傳送的訊息中遇到影像顯示問題，可能會將原因連結至不正確的位置：

* 位置可能不相符，或影像可能未正確推送至重複的追蹤伺服器：檢查您的設定。
* 影像不能位於行銷執行個體的公用資源資料夾中：將影像上傳至資源資料夾以解決問題。
* 如果您使用中間來源架構：傳送校樣時，會上傳檢查影像，且未發生錯誤（資訊會顯示在分析記錄中）。

疑難排解：

1. 傳送會顯示影像的校樣。
1. 驗證執行個體設定中的資源配置是否正確。
1. 檢查公用資源資料夾，如果不在公用資源資料夾中，則檢查傳送中參考的資料夾。
