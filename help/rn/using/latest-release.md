---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# 最新版本{#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本 7.3.5 - 版本編號 9368 {#release-7-3-5}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}


_2023 年 12 月 5 日_


### 安全性增強功能 {#release-7-3-5-security}


* 透過 Campaign Classic v7.3.5，驗證流程已獲得改善並提高安全性。技術操作者現在應使用 Adobe Identity Management System (IMS) 來連線至 Campaign。透過[此技術說明](../../technotes/using/ims-migration.md)了解如何移轉您現有的技術帳戶。

* 此外，為了強化安全性和驗證流程，Adobe Campaign 強烈建議將一般使用者驗證模式從登入/密碼原生驗證移轉至 Adobe Identity Management System (IMS)。閱讀此[技術說明](../../technotes/using/migrate-users-to-ims.md)，了解如何移轉操作者。

* 現在，當網頁表單具有&#x200B;**待發佈**&#x200B;狀態，其不會自動上線。為了防止安全性問題，務必在&#x200B;**上線**&#x200B;之前予以發佈，並透過網頁瀏覽器中的網頁表單 URL 存取。[深入了解](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### 修補程式 {#release-7-3-5-patches}

* 修正使用來自 Google Big Query 資料庫的資料並更新 Oracle 資料庫中的資料時的問題： 工作流程暫存表格中所有金鑰皆設為 `0`。 (NEO-65091)
* 修正將 Google Big Query 資料庫上的兩個查詢合併到&#x200B;**聯合**&#x200B;工作流程活動時，導致工作流程執行失敗的問題。(NEO-63705)
* 修正了在按一下 Campaign 報告中的 `Back` 按鈕時要求使用者重新驗證的問題。(NEO-65087)
* 修正資料庫清理工作流程中，在傳遞校樣之前刪除傳遞時所發生的錯誤。 (NEO-48114)
* 修正連線至用戶端主控台時的問題：最近 TLS 驗證更新導致連線錯誤。(NEO-50488)
* 修正 Campaign 升級至 7.3.1 後 HTTP Proxy 驗證的問題。行銷活動工作流程中的 HTTP 請求失敗，因為 `error 407 – proxy auth required is returned`。 (NEO-49624)
* 修正&#x200B;**指令碼**&#x200B;工作流程活動中 GPG 解密的間歇性失敗。相關的錯誤訊息為：`gpg: decryption failed: No secret key`。(NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

