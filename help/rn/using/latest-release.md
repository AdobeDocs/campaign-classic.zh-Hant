---
solution: Campaign Classic
product: campaign
title: 最新版本
description: 最新的 Campaign Classic 發行說明
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 571821ce775a7c354d01404d14faee8d2a21c170
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# 最新版本{#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic 發行候選版本**&#x200B;的新功能、改善和修正。

如需 Campaign Classic Gold Standard 版本（最新的 GA 版本編號）資訊，[請參閱本頁面](../../rn/using/gold-standard.md)。

## ![](assets/do-not-localize/blue_2.png) 版本 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_2021年2月22日_

**安全性增強功能**

* 主控台驗證機制已經改進，以最佳化安全性。 (NEO-26944)
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-28532)

**相容性更新**

下列系統現在已支援 Campaign：

* 使用Salesforce CRM外部帳戶時，現在支援第49版的Salesforce API。

**棄用的功能**

**技術傳遞能力監控**&#x200B;報告現在已過時。

瞭解更多[與已棄用和已移除的功能頁面相關的資訊](../../rn/using/deprecated-features.md)。

**功能改善**

**電子郵件反饋服務(EFS)是** 一種可擴展的服務，它直接從增強的MTA中捕獲反饋，從而提高報告的準確性。這項功能會以私人測試版發佈，未來發佈的版本將逐步提供給所有客戶。

* 現在，您可擷取所有類別的回饋，以進行完整精確的報告。
* 傳遞的指標的計算現在基於來自增強型 MTA 的即時回饋，以改進精確度和反應性。
* EFS 可解決同步軟退信的延遲問題。

如需詳細資訊，請參閱[詳細文件](../../delivery/using/sending-with-enhanced-mta.md#efs)。如果您有興趣參與此私人測試版，請填妥此[表格](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我們會回覆給您。

**其他變更**

* 使用壓縮功能已改善大型追蹤記錄檔的傳輸速度。
* Workflow Heatmap已經過改良，可避免在執行包含多個活動的工作流程時逾時。 (NEO-27423).
* 修正即使選件的結束日期已過，仍可能顯示選件的問題。 Campaign Classic現在會考量結束日期的整個時間戳記，而非僅考慮日期。 (NEO-27590)
* Google+連結已從&#x200B;**社交網路共用連結**&#x200B;個人化區塊中移除。
* 修正上一版中實施錯誤修正後的問題。 使用SSL/TLS連線時，在主機名稱上新增檢查，導致SMS傳送失敗。 已針對大多數通訊協定停用主機名稱驗證，例如使用proxy的POP3、SMS和HTTP，而SMS外部帳戶的憑證檢查已改進為使用三個值(NEO-29581)。 [進一步了解](../../delivery/using/sms-protocol.md#skip-tls)

**修補程式**

* 修正Tab、Enter和Escape鍵盤快速鍵無法在新登入畫面上運作的問題。
* 已修正重新整理問題，此問題會在儲存後，將新建立的工作流程名稱取代為預設值(NEO-26106)。
* 修正在運行工作流時，使用&#x200B;**外部檔案**&#x200B;目標映射在&#x200B;**Delivery**&#x200B;活動之前作為&#x200B;**Excrenth**&#x200B;活動的一部分添加新欄位的問題：不需要的欄位已添加到&#x200B;**外部檔案**&#x200B;目標映射。 (NEO-27687)
* 修正在重新開啟先前建立和儲存的Web應用程式時，造成原始碼中某些字元變更的問題。 (NEO-27597)
* 修正升級至包含追蹤連結（來自Build 19.1.4和Campaign 20.2）之新簽名機制的建置時可能發生的問題：當多個範本與事件相關聯時，升級可能會導致在傳送事務性訊息時選擇錯誤的範本。 (NEO-28326)
* 修正MTA無法回應且無法處理傳送的問題，除非重新啟動。 (NEO-27455)
* 修正MSSQL資料庫在日期時間類型欄的大量載入作業期間與時間戳記管理相關的問題。
* 修正使用Redshift xtk函式時的工作流程查詢問題。 SubDays、SubSeconds、SubMinutes和SubHours現在接受兩種Redshift時間戳記類型(NEO-24962)。
* 修正嘗試預覽具有匿名存取權的報表時，顯示指令碼錯誤訊息的問題。 (NEO-27081)
* 修正執行傳送分析時，可能會減少伺服器上記憶體使用量的問題。
* 修正當嘗試執行特定複雜查詢時，會導致例項無法運作的問題。
* 修正可能無法執行「同步Twitter頁面&#x200B;**」技術工作流程的問題。**(NEO-28634)
* 修正當嘗試使用&#x200B;**推文(twitter)**&#x200B;傳送範本在Twitter上發佈時，可能會顯示與decryptPassword函式相關的錯誤訊息的問題。 (NEO-28216)
* 修正使用&#x200B;**Javascript**&#x200B;活動在工作流程中提出HTTP要求時發生的問題。 在主機名稱中定義埠號後，呼叫將失敗，並出現下列錯誤(NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 修正無法傳送具有目標資料個人化之新傳送的問題。
* 修正行銷實例中發生數次當機導致核心檔案的問題。
* 修正&#x200B;**Tracking**&#x200B;工作流程因下列錯誤而失敗的問題(NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 修正在促銷活動的&#x200B;**定位與工作流程**&#x200B;標籤中建立和儲存傳送時發生的問題：預覽會失敗，並出現下列錯誤(NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 修正在行銷實例與Adobe Campaign Standard實例或Campaign Classic中部採購實例之間設定外部帳戶，並使用「DisableFOH2=1」選項時發生的錯誤。 在外部帳戶中使用&quot;DisableFOH2=1&quot;選項時，連接未正確關閉，並會累積導致以下錯誤(NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 修正伺服器與提供者之間發生連線問題時的SMS錯誤。 然後，MTA子項會自動停用連線。 Adobe Campaign Classic不會嘗試連接到此失敗的連接，只要尚未啟動新子系。
