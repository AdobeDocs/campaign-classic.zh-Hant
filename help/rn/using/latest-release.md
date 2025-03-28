---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 631188b5974eaa4cd1bf667c5df9f2ff0f983cf0
workflow-type: ht
source-wordcount: '251'
ht-degree: 100%

---

# 最新版本 {#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本 7.4.2 - 版本編號 9390 {#release-7-4-2}

[!BADGE 有限可用性]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="有限可用性"}

_2025 年 3 月 21 日_

>[!AVAILABILITY]
>
>此版本為&#x200B;**有限可用性** (LA)。僅限 Hosted/Managed Services 使用者使用。 此版本不久將可供混合及內部部署客戶使用。

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### 安全性改善 {#security-7-4-2}

此版本附帶幾個安全修正。

透過 **[!UICONTROL Adobe Experience Cloud]** 外部帳戶與 Adobe 解決方案和應用程式的連線已更新，以加強安全性。

### 修正 {#release-7-4-2-fixes}

此版本包含下列主要修正：

* TLS / SMPP 連線 — 修正 SMPP 穩定性問題

* Google BigQuery 修正：

   * 修正 BOOLEAN 資料類型的回歸問題
   * 修正 Proxy 設定問題
   * 修正 DATETIME 資料類型的回歸問題
   * 固定大量負載穩定性
   * 改善 ODBC 版本的內部測試
   * 修正連接字串特殊字元的問題
   * 已移除 Google BigQuery 查詢的預設逾時 (5 分鐘)

* 郵件傳輸代理程式 (MTA) — 已修正孤立 MTA 子代理卡在 **[!UICONTROL Start pending]** 狀態的問題。

此版本還修正下列問題：

ΝΕΟ-47269、ΝΕΟ-59059、NEO-62455、ΝΕΟ-65774、ΝΕΟ-66462、NEO-66989、ΝΕΟ-77898、ΝΕΟ-78843、NEO-79373、ΝΕΟ-79598、ΝΕΟ-80145、NEO-80245、ΝΕΟ-80434、ΝΕΟ-80683、NEO-81222、ΝΕΟ-81433、ΝΕΟ-81864、NEO-82351、ΝΕΟ-82781、ΝΕΟ-82838、NEO-82923、ΝΕΟ-83252、ΝΕΟ-83809、NEO-83826、NEO-84024、ΝΕΟ-84553、NEO-85150

