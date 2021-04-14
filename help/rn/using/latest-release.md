---
solution: Campaign Classic
product: campaign
title: 最新版本
description: 最新的 Campaign Classic 發行說明
feature: 概覽
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
translation-type: tm+mt
source-git-commit: 2c2dff554c716468c0984f3d893bd29aa9fd4453
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 97%

---

# 最新發行版本{#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic 發行候選版本**&#x200B;的新功能、改善和修正。

>[!NOTE]
>
>促銷活動&#x200B;**一般可用性(GA)組建**&#x200B;包括：[[!DNL Gold Standard] 11版](../../rn/using/gold-standard.md#gs-11)和[Campaign 20.2.5版](../../rn/using/release--20-2.md)。


## ![](assets/do-not-localize/blue_2.png) 發行版本 21.1.2 - Build 9282 {#release-21-1-2-build-9282}

_2021年4月14日_

* 密碼管理已改善，以最佳化安全性。
* 修正可能導致MTA當機的問題。

## ![](assets/do-not-localize/red_2.png) 發行版本 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_2021 年 2 月 22 日_

**安全性增強功能**

* 控制台驗證機制已經改善，以最佳化安全性。 (NEO-26944)
* 修正了安全性問題，針對伺服器端請求偽造 (SSRF) 問題加強保護。(NEO-28532)

**相容性更新**

下列系統現在已支援 Campaign：

* 使用 Salesforce CRM 外部帳戶時，現在已支援 Salesforce API 的 49 版本。

**已棄用功能**

 **技術傳遞能力監控**&#x200B;報告現在已被取代。

瞭解更多[與已棄用和已移除的功能頁面相關的資訊](../../rn/using/deprecated-features.md)。

**功能改善**

**電子郵件回饋服務 (EFS)**&#x200B;是一種可擴展的服務，它直接從增強型 MTA 中擷取回饋，從而提高報告的準確性。這項功能會以私人測試版發佈，未來發佈的版本將逐步提供給所有客戶。

* 現在，您可擷取所有類別的回饋，以進行完整精確的報告。
* 已傳遞指標的計算現在以增強型 MTA 的即時回饋為依據，以改進精確度和反應度。
* EFS 可解決同步軟退回的延遲問題。

如需詳細資訊，請參閱[詳細文件](../../delivery/using/sending-with-enhanced-mta.md#efs)。
如果您有興趣參與此私人測試版，請填妥此[表單](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我們將會與您聯絡。

**其他變更**

* 透過使用壓縮功能，已改善大型追蹤記錄的傳輸速度。
* Workflow Heatmap 已經過改善，可避免在執行包含多個活動的工作流程時逾時。 (NEO-27423)。
* 即使優惠方案結束日期已過，卻仍可能顯示的問題已修正。 Campaign Classic 現在會考慮結束日期的整個時間標記，而非僅考慮日期。 (NEO-27590)
* Google+ 連結已從&#x200B;**社交網路共用連結**&#x200B;個人化區塊中移除。
* 修正上一版本中實施錯誤修正後的問題。 使用 SSL/TLS 連線時，在主機名稱上新增檢查，導致 SMS 傳遞失敗。 已針對大多數通訊協定停用主機名稱驗證，例如使用 proxy 的 POP3、SMS 和 HTTP，而 SMS 外部帳戶的憑證檢查已改進為使用三個值 (NEO-29581)。 [進一步了解](../../delivery/using/sms-protocol.md#skip-tls)

**修補程式**

* 修正 Tab、Enter 和 Escape 鍵盤快速鍵無法在新登入畫面上運作的問題。
* 已修正重新整理問題，此問題會導致儲存後，新建立的工作流程名稱被預設值取代 (NEO-26106)。
* 修正在執行工作流程時，使用&#x200B;**外部檔案**&#x200B;目標對應在&#x200B;**傳遞**&#x200B;活動之前作為&#x200B;**擴充**&#x200B;活動的一部分新增新欄位的問題：不需要的欄位已新增到&#x200B;**外部檔案**&#x200B;目標對應。 (NEO-27687)
* 修正在重新開啟先前建立和儲存的 Web 應用程式時，造成原始程式碼中某些字元變更的問題。 (NEO-27597)
* 修正升級至包含追蹤連結 (來自 Build 19.1.4 和 Campaign 20.2) 之新簽名機制的建置時可能發生的問題：當多個範本與事件相關聯時，升級可能會導致在傳送異動訊息時選擇錯誤的範本。 (NEO-28326)
* 修正 MTA 在未重新啟動時無法回應且無法處理傳遞的問題。 (NEO-27455)
* 修正 MSSQL 資料庫在日期時間輸入欄位的大量載入作業期間，與時間標記管理相關的問題。
* 修正使用 Redshift xtk 函式時的工作流程查詢問題。 SubDays、SubSeconds、SubMinutes 和 SubHours 現在接受兩種 Redshift 時間標記類型 (NEO-24962)。
* 修正嘗試預覽具有匿名存取權的報表時，顯示指令碼錯誤訊息的問題。 (NEO-27081)
* 修正執行傳遞分析時，可能會減少伺服器上記憶體使用量的問題。
* 修正嘗試執行特定複雜查詢時，會導致執行個體無法作業的問題。
* 修正可能無法執行&#x200B;**「同步 Twitter 頁面」**&#x200B;的技術工作流程問題。 (NEO-28634)
* 修正嘗試使用&#x200B;**推文 (twitter)**&#x200B;傳遞範本在 Twitter 上發佈時，可能會顯示與 decryptPassword 函式相關的錯誤訊息的問題。 (NEO-28216)
* 修正使用 **Javascript** 活動在工作流程中提出 HTTP 請求時發生的問題。 在主機名稱中定義連接埠號碼後，呼叫將失敗，並出現下列錯誤 (NEO-29146)：

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 針對具有目標資料個人化的新傳遞修正無法傳送的問題 (NEO-30323)。
* 修正行銷執行個體中，發生數次當機所導致的核心檔案問題。
* 修正導致&#x200B;**追蹤**&#x200B;工作流程因下列錯誤而失敗的問題 (NEO-25206)：

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 修正活動的&#x200B;**目標定位與工作流程**&#x200B;標籤中建立和儲存傳遞項時發生的問題：預覽會失敗，並出現下列錯誤 (NEO-29440)：

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 修正在行銷執行個體與 Adobe Campaign Standard 執行個體或 Campaign Classic 中間來源執行個體之間設定外部帳戶，以及使用「DisableFOH2=1」選項時發生的錯誤。 在外部帳戶中使用「DisableFOH2=1」選項時，連線未正確關閉，並會累積導致以下錯誤 (NEO-26258)：

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 修正伺服器與提供者之間發生連線問題時的 SMS 錯誤。 然後，MTA 子項會自動停用連線。 只要尚未啟動新子項，Adobe Campaign Classic 就不會嘗試連線至這個失敗連線。
