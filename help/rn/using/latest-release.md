---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b9a716f327b8fdd68c3bf36dbe864535308def30
workflow-type: ht
source-wordcount: '294'
ht-degree: 100%

---

# 最新版本 {#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。 每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本 7.4.3 - 版本編號 9394 {#release-7-4-3}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

_2026 年 3 月 16 日_

>[!CAUTION]
>
> 用戶端主控台升級為強制。

### 安全性改善 {#security-7-4-3}

* 為了維持最佳的安全性、穩定性和合規性，Debian 已升級至版本 13，而 PostgreSQL 已升級至版本 17。請參閱[相容性矩陣](compatibility-matrix.md)。

### 修正 {#fixes-7-4-3}

* 修正了條碼元件允許不受限制的高度參數的問題，因為這可能會造成安全性弱點。(NEO-89984)
* 修正了透過工作流程建立的清單中，列舉欄位缺少臨時名稱屬性的問題，因為這會導致介面中顯示不正確或空白列舉標籤。(NEO-91158)
* 修正了某些傳送的傳送統計資料未完全重新計算的問題，尤其是會影響成功指標。(NEO-88106)
* 修正了在具有重複資料刪除活動的工作流程中使用 targetData 欄位時，傳送準備失敗並出現個人化錯誤的問題。(NEO-87693)
* 修正了在 PostgreSQL 15 中，由於類型轉換需求，導致單一字元字串欄位與其他字串串連失敗的問題。(NEO-88028)
* 修正了由於上層與下層傳遞 ID 不符，分散式行銷中的協作行銷活動追蹤記錄未寫入資料庫的問題。(NEO-86836)
* 修正了即使訊息成功傳送，傳送記錄仍顯示訊息已取消的問題，尤其會影響波次排程的傳送。(NEO-78933)
* 修正了資料庫清理工作流程無法有效清除資料的問題，因為這可能會影響效能。(NEO-76439)

