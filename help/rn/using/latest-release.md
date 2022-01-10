---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 發行說明
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: e4dfdd32c07753ee9e202ab4e4bf815485e47d8b
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 17%

---

# 最新發行版本{#latest-release}

![](../../assets/v7-only.svg)

本頁列出隨附的新功能、改進和修正 **最新Campaign Classicv7版本**. 每個新組建都會提供狀態，並以顏色具體化。 進一步了解Campaign Classicv7的建置狀態，位於 [本頁](rn-overview.md).

## ![](assets/do-not-localize/green_2.png)發行版本 7.2.1 - 版本編號 9346 {#release-7-2-1}

_2022年1月10日_

**安全性增強功能**

已對FDA帳戶進行幾項安全性改善：

* 現在，ODBC驅動程式直接與Adobe Campaign第三方安裝。 安裝這些驅動程式不再需要手動步驟。
* 設定FDA外部帳戶時，您現在可以使用金鑰組驗證來登入Snowflake帳戶，以增強驗證安全性。 [閱讀全文](../../installation/using/configure-fda-snowflake.md)
* 設定FDA外部帳戶時，您現在可以使用系統指派的受管理身分識別，登入您的Azure synapse分析帳戶。 [閱讀全文](../../installation/using/configure-fda-synapse.md#azure-external)


**功能改善**

* Microsoft Dynamics CRM 365 Connector

   已套用有關Microsoft Dynamics Connector Web API的重要修正：

   * 修正在工作流程觸發的匯入期間，字串類型欄位的Null值儲存為Null而非空白值的問題。
   * 修正使用Web API呼叫匯入或匯出資料時，導致下列錯誤的問題：&quot;無效的URI:URI方案太長」。
   * 修正從Microsoft Dynamics 365匯入包含查閱欄位之資料時的各種問題。

* Google BigQuery FDA Connector

   * Google BigQuery FDA Connector現在可用於托管部署。 [閱讀全文](../../installation/using/configure-fda-google-big-query.md)
   * 新增支援，以啟用Google BigQuery FDA連接器之代理伺服器的連線。 可透過外部帳戶設定的「選項」欄位設定所需的代理選項。 [閱讀全文](../../installation/using/configure-fda-google-big-query.md#google-external)

**其他變更**

* 淘汰後，Microsoft CRM、Salesforce、OracleCRM隨需活動已從介面中移除。 若要設定Adobe Campaign與CRM系統之間的資料同步，您可以使用CRM連接器活動。 [閱讀全文](../../workflow/using/crm-connector.md)
* 此 **[!UICONTROL Encrypted identifier]** 欄位已新增至訪客結構(nms:visitor)。 此欄位已經過計算，將用於網路應用程式。當在中間來源執行個體上設定「行」管道時，即適用。
* CRM資料來源現在可與 **更改資料源** 活動。
* 已在 **錯誤管理** 工作流活動的屬性：此 **錯誤時中止** 選項會自動停止工作流程。 之後將無法重新啟動它(NEO-29661)。 [閱讀全文](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* 專用序列現在用於生成nmsGroup表的主鍵，該表用於建立收件者的統計組。 之前曾使用xtknewId序列。 (NEO-30832)
* 新增使用CRM連接器活動批次更新作業的支援。

**修補程式**

* 修正建立傳送時，造成 **影像** 的 **追蹤與影像** 窗口。 使用自動代理配置時會發生此問題。 (NEO-33260)
* 修正了無法以同步模式在Debian 10伺服器(HTTPS)上傳檔案的問題。
* 修正了無法記錄傳送統計資料表(`nmsDeliveryLogStats`)，在刪除相關傳送後，無法在資料庫清除期間從中間來源例項清除。 (NEO-31034)
* 修正使用Token式驗證時，無法在iOS上傳送行動應用程式通知的問題(NEO-38640)。
* 修正了嘗試建立和設定報表時，可能顯示指令碼錯誤訊息的問題(NEO-38393)。
* 修正了由於同時更新大量傳送指標，可能導致追蹤工作流程在Oracle上失敗的問題(NEO-39653)。
* 修正了在執行控制類型時發生錯誤，而無法傳送傳送的問題(NEO-39833)。
* 修正登錄頁面中，線上調查回應的HTML頁面中無法正確顯示特殊字元的問題(NEO-39438)。
* 修正了在Explorer標籤中以滑鼠右鍵按一下任何資料夾時，Campaign Classic主控台無法運作的問題(NEO-38884)。
* 修正使用先前建立的傳送範本時，在遺失Web Analytics設定的新傳送中連結至Web Analytics帳戶的錯誤。 (NEO-28666)
* 修正了無法預覽附加至工作流程的行動傳遞問題。
* 修正了在啟用追蹤連結的URL簽章機制時，個人化追蹤URL無法重新導向的錯誤。
* 修正了可能因索引管理問題而導致升級後失敗的問題。
* 修正將查閱欄位資料類型與Microsoft Dynamics CRM搭配使用時發生的錯誤，此類資料類型 **匯入** 或 **匯出** 工作流程活動。
* 修正了由於代理組態問題，無法登入主控台的問題。 (NEO-38388)
* 修正了妨礙&#x200B;**清除資料夾**&#x200B;功能正常運作的問題。 (NEO-37459)
* 修正當參考的xml包含雙引號時，搭配Microsoft Dynamics CRM帳戶使用xml資料欄位時，導致請求錯誤的問題。
* 修正了導致網路逾時問題錯誤記錄為指令碼中斷問題，而非網路錯誤的問題。 在 JavaScript 活動中包含的 HTTP 要求中，會發生此問題。(NEO-38079)
* 修正了在嘗試提取時間元件時，執行 Amazon Redshift HoursDiff 和 MinutesDiff 函式時傳回錯誤結果的問題。(NEO-31673)
* 修正無法 **熱點點按** 報告自9182建置以來的傳送載入。 (NEO-28900)
* 修正以字元實體參照(`&amp;`)會防止使用者存取連結至QR碼的URL。 (NEO-28621)
* 修正每當使用者建立新促銷活動工作流程和連結至Web Analytics帳戶的傳送活動時，就會建立新外部帳戶的問題。 這是因為webAnalyticsAccount傳送物件中缺少ID所致。 (NEO-39691)
* 修正了&#x200B;**讀取清單** 在資料庫中以負 ID 識別清單時，工作流程活動無法運作的問題。 (NEO-39607)
* 修正的問題：可能導致 **中間來源（傳送記錄檔）** 工作流程失敗。 (NEO-39662)
* 修正了無法預覽已附加至工作流程的電子郵件傳送的問題。 (NEO-37840)
* 修正了可能導致資料庫清理工作流程刪除包含清單值的有效表的問題。 (NEO-34911)
* 修正了行銷執行個體上，計費工作流程可能當機的問題。
