---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 66387e2e008051901fe3385f571d7fe798829100
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 28%

---

# 最新版本 {#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本 7.4.3 - 版本編號 9392 {#release-7-4-3}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

_2026年3月16日_

>[!CAUTION]
>
> 使用者端主控台升級為強制性。

### 安全性改善 {#security-7-4-3}

* 為了維持最佳的安全性、穩定性和法規遵循性，Debian已升級至版本13，而PostgreSQL已升級至版本17。 請參閱[相容性矩陣](compatibility-matrix.md)。

### 修正 {#fixes-7-4-3}

* 修正條碼元件允許不受限制的高度引數，而這可能造成安全性弱點的問題。 (NEO-89984)
* 修正透過工作流程建立的清單中，列舉欄位缺少暫時名稱屬性，導致介面中顯示不正確或空白列舉標籤的問題。 (NEO-91158)
* 修正某些傳送的傳送統計資料未完全重新計算的問題，尤其是會影響成功指標。 (NEO-88106)
* 修正在具有重複資料刪除活動的工作流程中使用targetData欄位時，傳送準備失敗並出現個人化錯誤的問題。 (NEO-87693)
* 修正在PostgreSQL 15中，由於型別轉型需求，導致單一字元字串欄位與其他字串串串連失敗的問題。 (NEO-88028)
* 修正由於上層與下層傳遞ID不符，分散式行銷中的合作行銷活動追蹤記錄未寫入資料庫的問題。 (NEO-86836)
* 修正即使訊息成功傳送，傳送記錄仍顯示訊息已取消的問題，尤其是波次排程的傳送。 (NEO-78933)
* 修正資料庫清理工作流程無法有效清除資料（這可能會影響效能）的問題。 (NEO-76439)

