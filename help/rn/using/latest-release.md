---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2: id: e5e477db-ebc7-4368-ab0f-4d8fc2aed405id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: a9e48513ed4ceb2650d0eeff18563a010a148c80
workflow-type: tm+mt
source-wordcount: 498
ht-degree: 81%

---

# 最新版本 {#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。 每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本7.4.3 {#release-7-4-3}

### 建置9397 {#build-9397}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

_2026年6月30日_

#### 安全性改善 {#security-7-4-3-9397}

此版本編號包含安全性修正。 此為建議的一般可用性版本，並取代先前的Campaign Classic v7版本。

#### 其他變更 {#changes-7-4-3-9397}

依預設，webForm.jsp現在會忽略使用者端提供的`ctx`引數。 這是由`disableCtxInWebForm`引數所控制，其預設設定為「true」。

如果您的WebForm要求目前傳入了`ctx`引數，您可以將下列專案新增至 <web> 個元素（屬於config） — <instance>.xml檔案。 計畫逐步淘汰此使用方式。

```
<web>
  ...
  <jsp disableCtxInWebForm="false" />
  ...
</web>
```

### 建置9396 {#build-9396}

[!BADGE 已棄用]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="已棄用"}

_2026年6月9日_

此版本編號包含安全性修正。

### 建置9394 {#build-9394}

[!BADGE 已棄用]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="已棄用"}

>[!CAUTION]
>
> 用戶端主控台升級為強制。

_2026 年 3 月 31 日_

#### 安全性改善 {#security-7-4-3}

* 為了維持最佳的安全性、穩定性和合規性，Debian 已升級至版本 13，而 PostgreSQL 已升級至版本 17。 請參閱[相容性矩陣](compatibility-matrix.md)。

#### 修正 {#fixes-7-4-3}

>[!NOTE]
>
> 下列修正程式已逐步在後續的 7.4.3 版本中推出。 瀏覽至&#x200B;**[!UICONTROL Help > About...]** [功能表](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)，檢查您是否擁有最新的 9394@28aaec9 版本。 如需詳細資訊，請聯絡您的 Adobe 代表。

* 修正了條碼元件允許不受限制的高度參數的問題，因為這可能會造成安全性弱點。 (NEO-89984)
* 修正了透過工作流程建立的清單中，列舉欄位缺少臨時名稱屬性的問題，因為這會導致介面中顯示不正確或空白列舉標籤。 (NEO-91158)
* 修正了在具有重複資料刪除活動的工作流程中使用 targetData 欄位時，傳送準備失敗並出現個人化錯誤的問題。 (NEO-87693)
* 修正了在 PostgreSQL 15 中，由於類型轉換需求，導致單一字元字串欄位與其他字串串連失敗的問題。 (NEO-88028)
* 修正了由於上層與下層傳遞 ID 不符，分散式行銷中的協作行銷活動追蹤記錄未寫入資料庫的問題。 (NEO-86836)
* 修正了即使訊息成功傳送，傳送記錄仍顯示訊息已取消的問題，尤其會影響波次排程的傳送。 (NEO-78933)
* 修正了資料庫清理工作流程無法有效清除資料的問題，因為這可能會影響效能。 (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* 修正了某些傳送的傳送統計資料未完全重新計算的問題，尤其是會影響成功指標。 (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* 修正了開啟某些參考缺失上游目標定位結構描述的工作流程時，用戶端主控台可能當機的問題。 (NEO-28727)
* 修正了在啟動失敗後無法識別用戶端主控台版本的問題，因為安裝套件中缺少版本檔案。 (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

