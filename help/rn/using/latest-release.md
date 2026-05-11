---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 2296c1a7f6b818991d1620281077547d9250f16d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 76%

---

# 最新版本 {#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。 每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本 7.4.3 - 版本編號 9394 {#release-7-4-3}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

>[!CAUTION]
>
> 用戶端主控台升級為強制。

_2026年3月31日_

### 安全性改善 {#security-7-4-3}

* 為了維持最佳的安全性、穩定性和合規性，Debian 已升級至版本 13，而 PostgreSQL 已升級至版本 17。 請參閱[相容性矩陣](compatibility-matrix.md)。

### 修正 {#fixes-7-4-3}

>[!NOTE]
>
> 下列修正專案已逐步在後續的7.4.3版本編號中推出。 導覽至&#x200B;**[!UICONTROL Help > About...]** [功能表](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)，檢查您是否擁有最新的9394@28aaec9組建。 如需詳細資訊，請聯絡您的Adobe代表。

* 修正了條碼元件允許不受限制的高度參數的問題，因為這可能會造成安全性弱點。 (NEO-89984)
* 修正了透過工作流程建立的清單中，列舉欄位缺少臨時名稱屬性的問題，因為這會導致介面中顯示不正確或空白列舉標籤。 (NEO-91158)
* 修正了在具有重複資料刪除活動的工作流程中使用 targetData 欄位時，傳送準備失敗並出現個人化錯誤的問題。 (NEO-87693)
* 修正了在 PostgreSQL 15 中，由於類型轉換需求，導致單一字元字串欄位與其他字串串連失敗的問題。 (NEO-88028)
* 修正了由於上層與下層傳遞 ID 不符，分散式行銷中的協作行銷活動追蹤記錄未寫入資料庫的問題。 (NEO-86836)
* 修正了即使訊息成功傳送，傳送記錄仍顯示訊息已取消的問題，尤其會影響波次排程的傳送。 (NEO-78933)
* 修正了資料庫清理工作流程無法有效清除資料的問題，因為這可能會影響效能。 (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* 修正了某些傳送的傳送統計資料未完全重新計算的問題，尤其是會影響成功指標。 (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* 修正開啟某些參考缺少上游目標定位結構描述的工作流程時，使用者端主控台可能當機的問題。 (NEO-28727)
* 修正了在啟動失敗後無法識別使用者端主控台版本的問題，因為安裝套件中缺少版本檔案。 (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

