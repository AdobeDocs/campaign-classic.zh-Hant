---
product: campaign
title: 影像顯示問題
description: 影像顯示問題
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# 影像顯示問題{#image-display-issues}



如果您在傳送的訊息中遇到面部影像顯示問題，原因可能連結到錯誤位置：

* 位置可能不相符，或影像可能未正確推送至重複的追蹤伺服器：請檢查您的設定。
* 影像可能不在行銷執行個體的公用資源資料夾中：請將影像上傳至您的資源資料夾以解決問題。
* 如果您在中間來源架構中工作：傳送校樣時，檢查影像上傳且未發生錯誤（資訊會顯示在分析記錄中）。

如何疑難排解：

1. 傳送會顯示影像的校樣。
1. 驗證執行個體設定中的資源設定是否正確。
1. 檢查公用資源資料夾，如果沒有在公用資源資料夾中，則檢查傳送中參考的資料夾。
