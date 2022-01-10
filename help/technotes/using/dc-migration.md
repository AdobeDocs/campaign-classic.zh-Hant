---
product: campaign
title: 移轉至公用雲端
description: 深入了解Campaign Classic移轉至Public Cloud
feature: Overview
role: User
level: Beginner
exl-id: 2b282221-d048-4f6e-b52e-f8e584af2c0e
source-git-commit: 1d32161d60f6b382188012b104c642f504e28645
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 2%

---

# 概覽{#dc-ovv}

![](../../assets/v7-only.svg)

## 內容

作為尊貴的Adobe Campaign Classic客戶，我們致力提供您最佳體驗和價值。 多年來，我們已認識到在雲中托管客戶的價值和可靠性。  作為 [年度升級計畫](../../rn/using/rn-overview.md#yearly-upgrade)，我們將所有客戶移至Adobe Managed Services(AWS上的Public Cloud)，以提供更好、更可靠的服務。

該計畫有三個主要目標：

* 通過將基礎設施移至安全而現代的環境來解決已查明的安全漏洞(AWS)。
* 消除可能繁瑣的擴展過程，提供對 [增強的MTA](../../delivery/using//sending-with-enhanced-mta.md) 提高所有維護服務水準。
* 為未來的Adobe Campaign Classic做好準備，包括更自動化、定期的升級，不需要那麼多的資源，也不需要太多的時間。

### 字彙

* **版本編號升級**  — 當Adobe Campaign Classic軟體更新為最新的安全版本編號，但仍維持相同的主要/次要版本編號。 例如：Campaign v7 20.2.3版本編號9182至Campaign v7 21.2.5版本編號9188。 [了解更多](../../platform/using/faq-build-upgrade.md)。
* **MID/RT**  — 托管於Analytics Cloud的訊息執行伺服器（批次促銷活動為MID，即時單一訊息為RT）
* **每年升級計畫**  — 該方案提供改進的安全、改進的支援、增強的維護和穩定性。 它也可讓日後的升級更輕鬆，並可存取Campaign中的新功能。  [了解更多](../../rn/using/rn-overview.md#yearly-upgrade)。
* **AWS** - Amazon Web Services(Amazon Public Cloud)
* **SFTP**  — 安全檔案傳輸協定。 [了解更多](../../platform/using/sftp-server-usage.md)。


>[!NOTE]
>Campaign Classicv7移轉至Public Cloud可影響客戶使用 **Adobe Managed Services** 只有。


## 好處

**安全性**

* 最新安全性修正
* 閒置資料加密
* 改善驗證(IMS)

**基礎設施**

* 靈活的硬體可擴充性
* 更快速的恢復
* 提高可靠性和穩定性
* 協調的作業程式

**效能**

* 改善電子郵件容量
* 更大的資料庫
* 校驗競選版本

**為Adobe Campaign Classic客戶帶來強大、可靠的解決方案**

1. 更好的生產流程，導致更高的可靠性、更快的問題反應、更快的重大事故恢復。
1. 更高的電子郵件傳送容量。 在新資料中心托管的執行個體將能夠受益於電子郵件傳送的專用基礎架構。 這可能會導致電子郵件傳送速度提高，或允許使用較少的傳送IP。
1. 更好的硬體可擴充性。 增加硬體資源的速度可以快得多。 從技術上講，這次的震級是1小時，而不是數天。

**每年升級使未來升級更輕鬆**

1. 您的組織等待升級的時間越長，升級變得越複雜，且面臨漏洞的可能性也會增加（尤其是從舊版移轉時）。
1. 透過Campaign年度升級（原為Gold Standard計畫），您的執行個體將會更新，並準備好以更少的手動干預和資源接收更多自動化和定期更新。

![](assets/GSMigrations.png)

## 關於移轉

受影響帳戶的移轉至Adobe Managed Services(Public Cloud)將於2020/2021年完成。 Adobe將引導您的組織完成此歷程。

為了開始此工作，需要進行此移轉的帳戶會收到Adobe寄來的電子郵件通訊，提供時間表和檔案存取權。 這會是您排程移轉帳戶的通知。

移轉可由 [開啟新的客戶服務支援票證](https://experienceleague.adobe.com/?support-solution=Campaign#support). 使用主旨行「移轉至AWS」。

### 此移轉是否為強制性？

此移轉至雲端的步驟為 **前往 [年度升級方案](../../rn/using/rn-overview.md#yearly-upgrade)** Adobe Campaign實例。 如果您托管於非公用雲端(AWS)的資料中心，則此移轉為必要。

Amazon Web Services(AWS)是一個現代化、安全且最佳化的環境，是Adobe Managed Services雲端的托管場所。 [深入了解AWS](https://aws.amazon.com/application-hosting/benefits/).

Adobe計畫解除舊版資料中心的運行，必須將運行在舊版資料中心的Adobe Campaign實例傳輸到新的參考資料中心AWS。

這是前進的關鍵路徑，因為您的當前位置可能會暴露在 **安全性和效能漏洞**.

此外，此移轉現在是 **未來任何版本編號升級的先決條件** 你的Adobe Campaign。 舊版資料中心不再提供組建升級功能。

Adobe致力於保護您的資料，並協助您邁向Adobe Campaign未來的正軌。 我們需要你們的合作，使它成為共同的成功！


**我們組織了一個小組** 專門的客戶服務代表、客戶成功經理、產品經理、工程師、 TechOps專家和產品顧問，協助並確保體驗順暢無礙。 我們致力確保您具有相關專案和聯絡資訊。

我們投入巨大精力開發技術，使此遷移快速、無縫且安全。

### 限制

* 遷移過程將伴隨不可避免的平台停機。 此計畫的目的是引導最大限度地減少此停機時間。
* 資料整合的IP變更。
* 新傳送IP的傳遞能力提升。 不過，該計畫是讓這項業務對企業而言透明，而不像在上線期間所做的最初升級。

進一步了解Campaign移轉至 [Public Cloud常見問題集](dc-migration-faq.md).


## 遷移至Public Cloud的路徑

Adobe會處理大部分動作。 我們需要您進行驗證和簽核。

![](assets/MigrationPath.png)

## 移轉准則

### 全球方法

**資料庫**

資料庫將從舊版資料中心傾棄，並在Public Cloud(AWS)還原。 在新資料中心重新啟動後，應用程式將從關閉前的確切狀態恢復。 除了某些已排程的工作會延遲外，使用者不會看到任何差異。

**電子郵件傳送IP**

移轉完成後，Campaign執行個體的傳送IP將會完全不同。 為了確保順利轉換，Adobe將通過從舊IP向新IP進行預先切換流量，來實現新發送IP的升級。

**資料整合IP**

用戶端的資料整合可能會因資料整合的IP變更而受到影響。 視Campaign作為伺服器或用戶端而定，變更可能會影響兩個方向。
典型案例：

* SFTP，可能是雙向
* HTTP，可能是雙向
* SMPP（與SMS提供者的連線）、以用戶端形式使用Campaign、變更來源IP

一般而言，這表示用戶端應檢查其防火牆上可能設定的IP限制，並據此進行調整。*

**Campaign伺服器**

現有的Campaign伺服器（實際上是容器）將以「提升並轉移」方法移至Public Cloud(AWS)。 也就是說，不需要安裝新伺服器，但整個伺服器將傳輸到新資料中心。 操作只需要低級技術重新配置即可完成。

**伺服器名稱**

在用於行銷通訊的子網域下方：會保持不變。 不過，視實施而定，用戶端可能需要執行下列動作：

* 若是子網域委派（一般情況）,Adobe會處理所有變更，並確保順暢轉換
* 若是CNAME設定（例外），將會要求用戶端實作變更。 需要與Adobe協調。

若為使用者存取和資料整合，neolane.net下的名稱將維持不變。

這表示如果伺服器名稱未由硬式編碼IP取代，變更對使用者和資料整合實作而言將是透明的。

### 準備

**電子郵件傳送IP**

首先，Adobe傳遞能力將評估平台的傳遞能力狀態，並建議交換機至新IP的計畫。

Adobe將在新資料中心上配置相同數量的IP。

一旦布建新IP，新IP的數量就會開始增加。

**應用程式清理**
資料中心之間的資料傳輸處於停機的關鍵路徑。

資料的儲存方式有兩種：

1. 最重要的是，資料庫
1. 應用程式伺服器上的檔案（資料匯入和匯出）

縮小資料庫的大小對於加快資料傳輸至關重要。

建議：

* 縮短歷史資料（傳送記錄、追蹤記錄等）的保留期
* 刪除其他表格（傳送、收件者、自訂表格）上無用的記錄

### 執行

**暫停執行**

建議您放慢速度，最好在舊式資料中心關閉應用程式之前暫停所有執行：傳遞和工作流程。 這樣便於在Public Cloud(AWS)上重新啟動，因為程式將有時間「優雅」暫停並儲存任何進行中的執行狀態。

**移轉期間**

移轉期間，只有一項服務可繼續運作：電子郵件連結重新導向。 換言之，收件者在電子郵件中按一下後，將可以到達登錄頁面。 但系統不會記錄這些點按，因此移轉前不久開始的傳送點按率將低於正常。

**重新啟動**

遷移到新環境後，應用程式將逐步重新啟動：

* 首次存取主控台，讓使用者無需主動執行任何動作即可檢查狀態
* 然後，工作流程和傳送

### 移轉後

**刪除舊式資料中心上的實例**

應用程式遷移完成後，將無計畫在舊式資料中心再次運行任何進程。 我們希望，除了臨時備份之外，舊式資料中心上的所有資料都可以擦除，直到定時備份過程在Public Cloud(AWS)上運行。

**DNS委派**

通常，從Campaign傳送電子郵件（錯誤地址中@符號右側的部分）的網域已委派給Adobe。 可將委派變更並實作至AWS DNS伺服器。


## 支援和其他有效連結{#support}

* [移轉至Adobe Managed Services(Public Cloud)常見問題集](dc-migration-faq.md)
* [促銷活動年度升級](../../rn/using/rn-overview.md)
* [建置升級常見問題集](../../platform/using/faq-build-upgrade.md)
