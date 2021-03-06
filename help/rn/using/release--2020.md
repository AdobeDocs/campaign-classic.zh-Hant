---
product: campaign
title: 2020 版本
description: 進一步瞭解 Campaign Classic 2020 版本
feature: Overview
role: User
level: Beginner
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '6601'
ht-degree: 73%

---

# 2020 版本{#release-2020}

![](../../assets/v7-only.svg)


## 第 20.3 發行版本{#release-20-3}

### ![](assets/do-not-localize/red_2.png)版本 20.3.3 - 版本編號 9234 {#release-20-3-3-build-9234}

_2021年1月11日_

* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)
* 修正了與 broadlog 產生程序相關的迴歸問題，而此問題可能導致 MTA 程序當機。

### ![](assets/do-not-localize/red_2.png)版本 20.3.1 - 版本編號 9228 {#release-20-3-1-build-9228}

_2020 年 10 月 27 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在 **2021 年 6 月 30 日**&#x200B;後與 Campaign 連線。[深入瞭解](../../technotes/using/ims-updates.md)
> * 此版本隨附[安全性修正](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。
> * 如果您透過 oAuth 驗證使用 Experience Cloud 觸發程式整合，您必須依照[本頁](../../integrations/using/configuring-adobe-io.md)所述移至 Adobe I/O。**2021 年 9 月**[已淘汰](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)具有 Campaign 的舊版 oAuth 驗證模式。 託管環境繼續使用延伸功能，直到 **2022 年 2 月 23 日**。作為本地或混合型客戶，請與Adobe客戶服務部門聯繫，將支援期限延長至2022年2月。 您必須向 Adobe 提供 [OAuth 應用程式的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。


**新增功能？**

<table> 
<thead>
<tr> 
<th> <strong>iOS 推播通知改善</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>將行動應用程式與 Campaign 整合時，您需要使用 Apple 推播通知服務 (APN) 來保護您的通訊安全。您可以使用憑證式或權杖式驗證。
</p>
<p>這兩種驗證模式現在都適用於 Campaign Classic 的 iOS 行動應用程式：
</p>
<ul> 
<li><p>權杖式驗證（建議）：此驗證模式是以 .p8 檔案為基礎。此驗證模式速度較快，因為每個 APN 請求都包含權杖。<a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">進一步瞭解</a></p></li>
<li><p>憑證式驗證：此驗證模式是以 .p12 檔案為基礎。對於每個應用程式，都需要個別憑證。此憑證由 Apple 透過您的開發人員帳戶所傳遞傳送。<a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">進一步瞭解</a></p></li> 
</ul>
<p>在<a href="../../delivery/using/configuring-the-mobile-application.md">詳細文件中</a>瞭解如何在 Campaign 中選取驗證模式。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Android 推播通知改善</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">已改善 Android 推播通知，以為 Android 推播頻道驗證支援 FCM HTTP v1 API。</a> </p>
<p>藉由新的 API 支援版本，您現在可以傳送提供提升豐富推播訊息功能的 FCM 通知訊息。<a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">進一步瞭解</a></p> 
<p>瞭解如何在 Adobe Campaign 中為 Android 配置 FCM HTTP v1 API，清參閱<a href="../../delivery/using/configuring-the-mobile-application-android.md">本節</a> 。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增強功能**

* 確保載入資料庫安全：為了防止 DLL 預先載入攻擊，Campaign 現在只能在載入 Campaign 用戶端 (nlclient) 的同時，從 Windows 預設系統 DLL 路徑中載入 Windows DLL。[瞭解更多](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 攻擊而加強保護。(NEO-25661)
* 修正了在處理 GDPR 隱私權要求的同時，無法從與收件者表格有第二層級關係的自訂表格中刪除記錄的問題。(NEO-25967)
* 修正了在非管理員使用者嘗試同步 Adobe Experience Manager 範本時，使用 API 調用的安全性問題。(NEO-23487)

**相容性更新**

下列系統現在已支援 Campaign：
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

瞭解更多與[ Campaign 相容性矩陣相關的資訊](../../rn/using/compatibility-matrix.md)。

**棄用的功能**

不建議在第 20.3 版本中使用下列功能：

* 已棄用使用於匯入和匯出受眾至 Adobe Experience Cloud 的 Demdex 網域。如果您使用 Demdex 網域作為匯入/匯出的外部帳戶，則需要依此調整實施。[進一步瞭解](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* 已變更原本以 oAUTH 驗證設定為基礎而用於存取管道的觸發器整合驗證，並將其移動至 Adobe I/O。[瞭解更多](../../integrations/using/configuring-adobe-io.md)

瞭解更多[與已棄用和已移除的功能頁面相關的資訊](../../rn/using/deprecated-features.md)。

**功能改善**

* 幾項改善進行於&#x200B;**客戶端控制台**：
   * 已更新連線通訊協定，以遵循新的 IMS 驗證機制。伺服器和客戶機控制台升級是2021年6月30日之後必須能夠連接的。
   * 為了避免與某些網際網路安全性 GPO 規則限制發生不相容的情況，已將 Campaign 用戶端主控台登入畫面由內建的標準 Windows 表單取代。
   * 修正了在使用 64 位元用戶端主控台的工作流程中進行複製/貼上活動所發生的問題。(NEO-27635)
   * 在&#x200B;**「關於」**&#x200B;功能表中，已新增資訊，以區分 64 位元和 32 位元控制台。
* 當恢復工作流程時，現在則會在記錄中顯示工作流程識別碼，其可讓您更清楚地識別已恢復的工作流程。
* 已引入新的永久 cookie：nllastdelid。此 cookie（UUID230 除外）將儲存 deliveryId。當續存期間 cookie 不存在時，會從存在於此 cookie 中的 deliveryId 擷取 broadlog 資訊。
此變更修正了在瀏覽器續存期間結束時，所發生的問題：已刪除包含 deliveryId 和 broadlogId 的續存期間 cookie。若無 deliveryId，則無法找到 broadlog 資訊，而且若為永久追蹤（上一次傳遞），追蹤表格資訊將會遺失。
瞭解更多 cookies 詳細資訊，請參閱[本節](../../platform/using/privacy-and-recommendations.md#cookies)。
* 透過在傳送傳遞前重新啟動 MTA 程序，改善了具有傳送性伺服器的高容量傳遞生產效能。

**其他變更**

* 當使用 SFTP 相對路徑時，`~/`不再自動新增字元。如有需要，您可以手動將`~/`字元新增至路徑，但 Adobe 建議您使用&#x200B;**絕對路徑**。
* 在使用 Microsoft SQL Server 配置新的資料庫時，已將 Windows NT 驗證從可用的驗證方法中移除。[顯示全文](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* 已針對 Teradata 進行資料庫清理工作流最佳化，以提高效能。(NEO-19959)
* 改善了從 Adobe Target 插入影像時顯示的錯誤訊息，且外部帳戶的租用戶名稱為空白的問題。
* 在傳遞屬性中，**[!UICONTROL Archive emails]**&#x200B;將選項重新命名&#x200B;**[!UICONTROL Email BCC]**。
* 為了提高穩健性，已拒絕選取所有具有無效節點的查詢。如果您需要停用檢查並返回上一個行為，可將 XtkSecurity_Disable_QueryCheck 設定為 0。
* 已為nmsBroadlogId序列添加負ID範圍支援。 此生成將調整nmsBroadlogId序列的min_value以包括負範圍。 如果您有不允許負ID的嚴格用例，請將序列的min_value還原為1。

**技術演變**

已將 Tomcat 從第 7 版 (7.0.103) 更新為第 8 版 (8.5.57)。

已將`tomcat-7`目錄取代為`tomcat-8`目錄。

在 windows 上，現在可將 _iis_neolane_setup.vbs_ 和 _apache_neolane.conf_ 安裝在目錄`conf`中（而非上一個`tomcat-7/conf`）。

在 linux 上，現在可將 _apache_neolane.conf_ 安裝在`conf`目錄中。

**修補程式**

* 修正了無法重新計算傳遞數據的問題。
* 修正了在上傳 CSV 檔案和使用舊的版本編號連線至伺服器的 Campaign Classic 9080 版本編號時，顯示錯誤訊息的問題。(NEO-23218)
* 修正了為外部帳戶配置 Microsoft Dynamics CRM 精靈時，可能顯示錯誤訊息的問題。這是因為最新 MS Dynamics CRM API 版本的相容性問題。(NEO-24528)
* 修正了無法使用 CRM 連接器，從 Campaign Classic 將查詢類型記錄（即與其他表格連接的外鍵記錄所組成的資料）匯出至 Microsoft Dynamics 的問題。(NEO-23864)
* 修正了無法擷取 Microsoft Dynamics 資料的問題，若是在 CRM 連接器中啟用，**「自動索引」**&#x200B;選項的時候。(NEO-25981)
* 修正了即使連線已結束，仍可能會開啟連線的 IMS 驗證問題。現在會在結束時自動關閉終止的連線，以避免累積連線且佔用系統資源。(NEO-25996)
* 修正了因為外部帳戶的錯誤配置（帳戶或密碼錯誤）而導致 Adobe Experience Manager 內容同步傳送失敗，未顯示錯誤訊息的問題。現在會顯示發生失敗的訊息，可讓您更輕鬆地識別問題。(NEO-25586)
* 修正了在選取&#x200B;**「更新」**&#x200B;作業類型於&#x200B;**「更新」資料**&#x200B;活動中所發生的問題。如果需要更新的資料不正確，工作流程將會發生錯誤並失敗。如果資料不正確，工作流程並不會失敗，且會將記錄儲存至&#x200B;**「拒絕」**&#x200B;離開轉換。(NEO-23794)
* 修正了包含子工作流程的工作流程無法運作的問題。(NEO-24036)
* 修正了當編輯行銷活動範本說明，在複製貼上像是日文字元等符號時，無法顯示&#x200B;**「儲存」**&#x200B;按鈕的問題。(NEO-27071)
* 修正了無法在執行個體配置精靈中變更追蹤伺服器的問題。
* 修正了無法儲存行銷活動說明或行銷活動範本的問題，其發生於在按一下&#x200B;**「儲存」**&#x200B;按鈕前按了視窗外部。(NEO-27449)
* 修正了無法運作&#x200B;**「主要帳單設定檔數」**(billingActiveContactCount) 技術工作流程的問題。如果在方案擴充的計算欄位上執行連結，便會發生此問題。建立了大量的資料，其可能導致資料庫的暫存空間被用盡。(NEO-24062)
* 修正了&#x200B;**「資料載入（檔案）」**&#x200B;活動的問題，如果日文字元位於檔案結尾，則無法從 txt 和 csv 檔案將其匯入。(NEO-24957)
* 修正了連續傳遞而無法正確填入&#x200B;**「已開始分析」****和「已完成分析」**&#x200B;欄位的問題。(NEO-20755)
* 修正了嘗試在查詢後預覽 SMS 訊息時，除&#x200B;**收件者** (nms:recipient) 以外的其他方案可能會顯示錯誤訊息的問題。(NEO-27517)
* 修正了使用 Snowflake FDA 連接器時所發生的問題。具有 Snowflake FDA 存取名稱權限的使用者無法對 Snowflake FDA 方案執行查詢。在記錄中顯示「找不到密碼」類型的錯誤。(NEO-23851)
* 修正了使用 FDA 連接器時，連結的 FDA 方案名稱為目前方案的元素名稱子字串時，所發生的問題。例如，這發生在若 FDA 方案是「cust」，且收件者方案中的其中一個元素是「customer」，就會發生這種問題。在擷取「customer」元素內的欄目並從「cust」FDA 方案中新增欄目時，本機的欄目值便會遺失。(NEO-20193)
* 修正了從外部資料庫擷取記錄並將記錄插入 Campaign 資料庫時，所發生的工作流程問題。(NEO-26359)
* 修正了&#x200B;**「更新事件狀態」**&#x200B;技術工作流程中的問題：為了符合&#x200B;**「傳送數據」**&#x200B;活動的傳入對應欄位大小、**「更新傳遞數據」**&#x200B;活動的三個目標欄位大小，已從 32 位元變更為 64 位元。(NEO-11557) 瞭解更多&#x200B;**「更新」事件狀態**&#x200B;工作流程[，請參閱本節](../../workflow/using/about-technical-workflows.md)。
* 修正了在&#x200B;**「訊息中心事件歷史記錄」**&#x200B;報到中，嘗試套用篩選器且導致指令碼錯誤，且無法根據日期範圍篩選的問題。(NEO-23365)
* 修正了干擾問題，其在 **Campaign 工作** (operationMgt) 和&#x200B;**預覽**（預測）技術工作流程之間。當排定的傳遞仍為「目標就緒」或「就緒即可傳送」狀態時，便會發生此問體。(NEO-20819)
* 修正了 xtkOperator mdata 欄位中未顯示 XML 識別碼時，所發生的 XML 解析問題。它導致了後升級失敗。(NEO-26113)
* 修正了在使用 **File Transfer** 活動，連結至在 SSL 加密的 Azure 外部帳戶，其為連線至 HTTP 而非 HTTPS 的問題。(NEO-26720)
* 修正了 MSSQL 資料庫在清除工作流程期間，可能在 up_updatestats 程序發生錯誤的問題。
* 修正了在關閉 Web 程序期間，如果仍在處理互動要求時所發生的當機問題。(NEO-26447)
* 修正了 Oracle DB **NoNull** 功能在升級 9032 後無法再運作的問題。(NEO-26488)
* 修正了在安裝未含有訊息中心安裝包的 LINEV2 安裝包之情況下，升級 9171 後而無法追蹤工作流程的問題。
* 修正了因屬性「APP」資料庫連線字串最終取得無效值，而導致無法將連線池新增至所需連線數的可擴充性問題。(NEO-25105)
* 修正了在代理配置層級，導致您無法在更新到最新 Windows 10 後登入 Adobe Campaign 的問題。(NEO-27813)
* 修正了在匯入含有追蹤連結的 HTML 範本後，使傳送的電子郵件顯示無用 URL 的問題。(NEO-25909)
* 修正了在工作流程&#x200B;**「分割」**&#x200B;活動中顯示目標資料餘數時，而造成伺服器當機的問題。
* 修正了在清除運算式剖析器時，防止記憶體損毀所造成的伺服器當機問題。(NEO-26856)
* 修正了在非管理員使用者定義的執行個體變數的擴充活動時所產生的問題。(NEO-25653)
* 已修復可阻止工作流資料導出到FDA資料庫的回歸(Teradata、Snowflake)。

## 第 20.2 發行版本{#release-20-2}

### ![](assets/do-not-localize/limited_2.png)版本 20.2.5 - 版本編號 9188 {#release-20-2-5-build-9188}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2021年 3 月 31 日_

**功能改進**

* 已對無效soap調用上的崩潰進行了改進。 這可能導致實例在嘗試運行特定複雜查詢時停止工作。 (NEO-28796、NEO-30553)
* 已修復一個回歸，該回歸由於主機名驗證而阻止使用TLS發送SMS。 (NEO-29581)
* 已修復導致簽名跟蹤連結無法處理某些電子郵件客戶端的問題。 (NEO-28414、NEO-29615)
* 使用WebApp跟蹤標籤時已修復跟蹤ID序列，這可能導致與重複ID衝突。 (NEO-27931)
* 已修復導致每日wfserver重新啟動停止運行工作流的問題。 (NEO-30047)
* 修正了在非管理員使用者嘗試同步 Adobe Experience Manager 範本時，使用 API 調用的安全性問題。(NEO-32389、NEO-23487)
* 修復了在通過模板建立的交貨上關閉交貨對話框時導致控制台崩潰的問題。 (NEO-31547)
* 已修復建立和保存在 **目標和工作流** 頁籤：預覽將失敗，出現以下錯誤。(NEO-29440)
* 已修復Tomcat 8.5發送無效答案的問題，這導致事務性消息傳遞日誌中出現錯誤。 (NEO-30858)
* 修復了導致外部線程管理中記憶體損壞並影響效能的回歸問題。
* 修復了在使用自定義目標映射時可能導致開單工作流失敗的問題。 自定義架構的主鍵儲存在僅允許整數值的「sourceId」列中。 它現在允許整數和字串值。 (NEO-25914、NEO-28146)
* 修正迴歸，防止在傳遞中使用主控台的某些元件，例如日期選擇器和影像管理。 (NEO-31453)

### ![](assets/do-not-localize/red_2.png)版本 20.2.4 - 版本編號 9187 {#release-20-2-4-build-9187}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)
* 修正迴歸，防止在傳遞中使用主控台的某些元件，例如日期選擇器和影像管理。 （NEO-31453、NEO-31454）

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2020 年 12 月 22 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在 **2021 年 6 月 30 日**&#x200B;後與 Campaign 連線。[深入瞭解](../../technotes/using/ims-updates.md)
> * 此版本隨附[安全性修正](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。
> * 如果您透過 oAuth 驗證使用 Experience Cloud 觸發程式整合，您必須依照[本頁](../../integrations/using/configuring-adobe-io.md)所述移至 Adobe I/O。**2021 年 9 月**[已淘汰](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)具有 Campaign 的舊版 oAuth 驗證模式。 託管環境繼續使用延伸功能，直到 **2022 年 2 月 23 日**。作為本地或混合型客戶，請與Adobe客戶服務部門聯繫，將支援期限延長至2022年2月。 您必須向 Adobe 提供 [OAuth 應用程式的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。


**功能改進**

* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 最初基於oAUTH身份驗證設定訪問管道的觸發器整合身份驗證已更改並移到Adobe I/O。 [瞭解更多資訊](../../integrations/using/configuring-adobe-io.md)
* [在 iOS APN 舊版二進位通訊協定支援結束之後，在升級後期間，](https://developer.apple.com/news/?id=c88acm2b)使用此通訊協定的所有執行個體都會更新為 HTTP/2 通訊協定。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)
* 已修復連接錯誤後導致SMPP連接器停用的問題，防止發送其他SMS傳送，並導致效能問題。 (NEO-28609)
* 修正了在清除運算式剖析器時，防止記憶體損毀所造成的伺服器當機問題。(NEO-26856)
* 修正了在工作流程&#x200B;**「分割」**&#x200B;活動中顯示目標資料餘數時，而造成伺服器當機的問題。
* 修正了嘗試在查詢後預覽 SMS 訊息時，除&#x200B;**收件者** (nms:recipient) 以外的其他方案可能會顯示錯誤訊息的問題。(NEO-27517)
* 在使用主機名中顯式定義的埠號發出HTTPS連接請求時，修復了問題，調用失敗，出現證書錯誤。 (NEO-29146)
* 解決了POSIX線程管理中在市場營銷實例上生成大型核心轉儲檔案的問題。 (NEO-28117、NEO-29281)
* 已修復問題，這些問題可能導致Web進程在準備交貨或具有重複交貨預覽時崩潰。 (NEO-27790、NEO-27517)
* 解決了由非管理員操作員觸發時導致交貨或證明發送失敗的問題。 (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **新控制面板 10 月發行版本**，其中包含使用 CNAME 的網域設定及新的資料庫監控功能。[進一步瞭解](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=zh-Hant)。

### ![](assets/do-not-localize/red_2.png)版本 20.2.3 - 版本編號 9182 {#release-20-2-3-build-9182}

_2020 年 9 月 11 日_

* 修正了由於傳送組件上單一錯誤功能導致記憶體過載，導致傳送準備遭到封鎖的迴歸。(NEO-27346)
* 修正了在重新發佈 Web 應用程式之前，關閉 Apache 和 Web 伺服器的升級後問題。(NEO-27155)
* 已修復HTML模板管理上的回歸，因為對頁籤的誤解導致跟蹤URL變得可見。 (NEO-25909)
* 修正了資料庫清除工作流程因非受管理資料來源而可能失敗的問題。(NEO-23160、NEO-23364)
* 清除工作流程現在會依 100 的批次清除過期清單，而非逐一清除。
* 修正了導致無法修改外部帳戶內部名稱的迴歸。(NEO-27323)
* 修正了升級後期間的迴歸，而導致 nlserver（錯誤記錄）錯誤啟動。
* 已改善共用記憶體的更新管理。20.2 中所需的其他步驟已不再需要。

### ![](assets/do-not-localize/red_2.png)版本 20.2.2 - 版本編號 9180 {#release-20-2-2-build-9180}

_2020 年 7 月 22 日_

* 修正了在停用簽名功能時，無法進行追蹤的問題。(NEO-26411)
* 修正了造成個人化網域中未簽署的連結在允許時遭到封鎖的問題。(NEO-25210)
* 修正了在使用某些特定 Outlook 舊版本時，無法開啟/按一下追蹤 URL 的問題。(NEO-25688)
* 修正了導致在電子郵件傳送中錯誤定義鏡像頁面 URL（因為 ASCII 字元控制不當）的問題。(NEO-26084)
* 修正了反網路釣魚服務中編碼 URL 管理的問題。(NEO-25283)
* 修正了在個人化參數（井字鍵符號的錨點標記）中無法使用片段追蹤 URL 的問題。(NEO-25774)
* 修正了在使用特定自訂追蹤公式時的追蹤問題。(NEO-25277)
* 修正了「通知單擊」無法進行追蹤的問題（iOS 和 Android 推播通知）。(NEO-25965)
* 修正了影響工作流程中計算欄位的迴歸，導致工作流程失敗。(NEO-25194)
* 修正無法即時建立網頁追蹤 URL 的迴歸。(NEO-20999)
* 已修正現成可用的傳送報表迴歸問題，在匯出為 PDF 時，這些報表會顯示為截斷。(NEO-25757)
* 修正了部署精靈中的當機問題。
* 修正了「優惠方案」通知工作流程在升級後後無法正常運作的問題。
* 改善了 iOS HTTP2 連接器（協力廠商更新和錯誤管理）。(NEO-25904、NEO-25903)
* catalina.properties 中的 jarToSkip 清單已更新，而可刪除對不再使用的 jar 檔案的參照（iOS 通知）。
* 修正了在升級後封鎖傳送準備的問題。
* 在切換至新序列 ID 機制後，所有更新收件者表格的 Web 應用程式都會在升級後期間重新發佈。
* 修正了傳送內容中的潛在 XSS 弱點。(NEO-17987、NEO-26073)

![](assets/do-not-localize/cp-icon.png) **新的控制面板 6 月版本**，包含作用中設定檔監控、子網域傳遞送能力稽核及 GPG 金鑰管理。[進一步瞭解](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html)。

### ![](assets/do-not-localize/red_2.png)版本 20.2.1 - 版本編號 9178 {#release-20-2-1-build-9178}

_2020 年 6 月 8 日_

**新增了哪些功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>支援表情符號</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>在 Campaign 設計訊息時，您現在可以使用專屬按鈕，輕鬆將表情符號插入訊息本文。您也可以在電子郵件主旨列新增表情符號。您可以在介面自訂可用的表情符號清單。</p>
    <p>如需新增表情符號的詳細資訊，請參閱<a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">相關的文件</a>，以瞭解詳情。前往<a href="../../delivery/using/customizing-emoticon-list.md">此章節</a>，瞭解如何自訂表情符號清單。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA 連接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您現在可以將 Campaign 執行個體連線至 Azure Synapse 外部資料庫。此連線透過新的外部帳戶進行管理。</p>
    <p>Azure Synapse 僅適用於混合式和內部部署環境。如需詳細資訊，請參閱<a href="../../installation/using/configure-fda-synapse.md">相關的文件</a>，以瞭解詳情。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>泰國及巴西隱私權法</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>泰國的個人資料保護法 (PDPA) 是新的隱私權法令，該法協調泰國的資料保護要求並以現代化方式加以規範。 </p>
   <p>巴西的 Lei Geral de Proteção de Dados (LGPD) 將於 2021 年初生效，所有於巴西收集或處理個人資料的公司皆適用。</p>
   <p>這些法令及規範適用於所持有資料的主體居住於這些國家的 Adobe Campaign 客戶。除了 Campaign 已提供的隱私權功能 (包括許可管理、資料保留設定及使用者角色) 外，我們還將利用此機會加入其他功能，以協助您做好迎接 PDPA 及 LGPD 的準備：</p>
   <ul> 
     <li><p>近用權與刪除全：我們利用了專為 GDPR 和 CCPA 所新增的功能。<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">顯示全文</a></p></li> 
     <li> <p>使用 Campaign 介面或API 建立隱私權要求時，您現在可以選取<strong>法規類型</strong>：PDPA、LGPD、GDPR、CCPA。<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">顯示全文</a>。</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 追蹤電子郵件中的連結已提高安全性，並對所有客戶已是預設功能。另外還提供增強的安全性功能，您可以透過連絡客戶服務來啟用此功能。有關非托管客戶啟用此功能的詳細資訊和步驟，請參閱 [「安全性與隱私權」檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。(NEO-24232)

* 為了最佳化安全性，用於產生檔案名稱的 MD5 雜湊演算法已增強 sha256，以利公開檔案上傳。(NEO-17044)

* 為了增強防範 XSS 攻擊的安全性，執行鏡像頁面時將禁用客戶端指令碼。(NEO-17987)

* 修正&#x200B;**隱私權要求清除**&#x200B;技術工作流程無法刪除調解資料的問題。(NEO-25168、NEO-21004)

* 修正&#x200B;**檔案傳輸**&#x200B;活動使 SFTP 金鑰驗證無法在 Debian 9 運作的問題。(NEO-23183)

**相容性增強功能**

下列系統現在已支援 Campaign：
* 作業系統： Debian 10
* RDBMS：Oracle 18c 及 Oracle 19c
* FDA：Azure Synapse Analytics

進一步瞭解[ Campaign 相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)。

**功能改善**

* 改善交易式傳訊功能，以提供更佳的使用者體驗。您現在可以取消發佈交易式傳訊範本，該範本將從執行實例刪除。[進一步瞭解](../../message-center/using/publishing-message-templates.md#template-unpublication)。

* 提供新的選項，用來設定傳送包含影像或附件之電子郵件時的限制。這些護欄措施可以避免效能問題，對於交易式傳訊特別有用。[顯示全文](../../installation/using/configuring-campaign-options.md#delivery)

* 新的&#x200B;**在資料庫準備傳遞組件**&#x200B;選項，允許直接在資料庫執行傳遞準備，大幅加快分析作業。此選項僅適用於特定配置。[進一步瞭解](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)。(NEO-23886)

* 已改善 Microsoft Dynamics 的 [CRM Connector 活動](../../workflow/using/crm-connector.md) 效能。(NEO-13303、NEO-12710)

* 已增加共用記憶體版本。

   >[!WARNING]
   >
   >此項功能改善需要於執行升級後，進行額外的步驟操作。請參閱下面的&#x200B;**技術演變**&#x200B;一節。

* 加強清理工作流程。現在清理工作流程，也將自動刪除所有已刪除工作流程的孤立工作台。[進一步瞭解](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)。

* 使用 iOS HTTP2連接器的 iOS 行動應用程式憑證，現在將於傳送推播通知前驗證，因此可以避免傳遞因憑證過期而失敗。

* 改善了 HTTP 代理連線的管理機制。[進一步瞭解](../../installation/using/file-res-management.md)。

* **[!UICONTROL Javascript Code]** 和 **[!UICONTROL Advanced Javascript Code]** 工作流程活動中的新選項，可在限制後停止執行。預設值為 1 小時。[進一步瞭解](../../workflow/using/sql-code-and-javascript-code.md#javascript-code)。

**其他變更**

* 舊版 SMS 連接器現已棄用。請參閱 [已棄用的功能頁面](../../rn/using/deprecated-features.md)。

* 您無法再使用自己的 Litmus 帳戶來佈建及使用 Adobe Campaign 的收件匣轉譯。[進一步瞭解](../../delivery/using/inbox-rendering.md)。

* 為了更好地區分檢視和資料夾，檢視名稱的顏色已從深藍色更改為深青綠色。[顯示全文](../../platform/using/access-management-folders.md)

* Campaign Classic 現在可以連線至英國、印度和加拿大地區代管的 Microsoft Dynamics CRM 帳戶。此功能適用於 Office 365 和內部部署 (Dynamics 2015) 的部署類型。

* Campaign 現在將執行TLS驗證，以檢查伺服器主機名稱是否符合所提供憑證的主機名稱。

* 「傳遞與追蹤」統計資料表格現在將針對 SMS 通道每次傳遞顯示一個項目，而非每名傳傳收件者顯示一個項目。

* 記錄檔新增了錯誤訊息，以利在下載的檔案大於磁碟空間時警告使用者。

* 下列功能現在可以供 Snowflake 連接器使用：MonthsAgo、DaysAgoInt、ToDateTime、YearsAgo。

**技術演變**

新的組建版本更新了共用記憶體，此更新需要進行額外的步驟。做為 Campaign 管理員，您需要移除記憶體區段。這些步驟為必要操作，因為舊的區段使 nlserver/nlsrvmod 無法成功啟動。

如果是 Windows 系統，需要重新啟動系統。

如果是 Debian/CentOs，則需要刪除共用記憶體。以下是步驟：

升級前，您需要遵循下列步驟操作：

1. 停止 apache2 (CentOS 上的 http2) 服務 (如果服務正在執行)。
1. 如果 nlserver 服務正在運行，停止運行 nlserver (舊組建版本則是 nlserver6) 服務。

升級後：

1. 如果版本早於當前版本，請使用 **ipcrm** 命令刪除共用記憶體。
1. 如果 nlserver 服務先前曾運行，請啟動該服務。
1. 啟動 apache2 服務 (如果先前正在運行)。

以下是 Debian 的命令列：

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

[本頁面](../../configuration/using/additional-parameters.md#redirection-server-configuration)提供 Linux 的示範。

**修補程式**

* 修正了清理工作流程記錄檔的次要迴歸。
* 修正了剖析 WSDL 檔案時，工作流程&#x200B;**載入 (SOAP)** 活動出現的問題。
* 修正使用&#x200B;**調查**&#x200B;活動升級許多工作流程，以有效處理大量工作流程時造成的錯誤 。
* 修正了處理來自 Enhanced MTA 的郵件中訊息時出現的間歇性連線問題。(NEO-20380)
* 修正在 HTML 以100%寬度顯示影像時，無法正確顯示熱門點擊百分比的問題。(NEO-23203)
* 修正無法將傳遞的條件式內容完全顯示於熱門點擊報表的問題。(NEO-18729)
* 修正繼續工作流程以傳送循環傳遞時，跳過目標核准步驟的問題。(NEO-18166)
* 修正了修正工作流程的錯誤後，**重新開始訊息準備**&#x200B;按鈕無法恢復傳遞的問題。(NEO-13488)
* 修正了漸進階段期間，目標包含日文電子郵件格式的收件者時，可能使傳遞在中間來源模式失敗的問題。(NEO-23846)
* 修正 Snowflake Connector 時區轉換的問題 (NEO-20105)
* 修正使用 FTP over SSL 的外部帳戶的問題。(NEO-20498)
* 修正無法在 Line 傳遞顯示影像的問題。(NEO-23207)
* 修正發佈優惠方案時出現錯誤的問題。(NEO-23312)
* 修正推播通知的問題，此問題使測試連線即使憑證已過期，卻仍可以在行動應用程式中運作。(NEO-22991)
* 修正了在高頻率傳送時，可能影響推播通知的問題。(NEO-20516)
* 修正了即使追蹤記錄未包含重複項，追蹤資料仍包含重複項的問題。(NEO-20040)
* 修正了追蹤伺服器通訊失敗經修正後，傳送重複的交易式電子郵件的問題。(NEO-23640)
* 修正了從追蹤 URL 重新導向時，刪除編碼參數值的問題（會影響日文字元）。(NEO-25637)
* 修正了比較浮點數字時，查詢無法運作的問題。(NEO-23243)
* 修正了重新啟動工作流程後，**修改者**&#x200B;欄位的內容無法顯示的問題。(NEO-23035)
* 修正從第二個容器下載記錄檔時，追蹤技術工作流程失敗的問題。(NEO-23159)
* 修正執行&#x200B;**擴充**&#x200B;活動時，工作流程可能失敗的問題。(NEO-17338)
* 已在&#x200B;**重複資料**&#x200B;刪除工作流程活動的&#x200B;**Doubles to keep** 欄位新增檢查機制，以防止輸入空值或負值。
* 已從循環行銷活動移除&#x200B;**排程器精靈**，以避免提及小時和分鐘。移除後，僅納入日期單位。
* 修正了透過&#x200B;**指令碼**&#x200B;工作流程活動的&#x200B;**依指令碼計算**&#x200B;選項建立傳遞時，其他儲存欄位的問題。(NEO-20609)
* 修正了無法在資料庫清理工作刪除 Ghost 工作流程的問題。
* 修正了造成&#x200B;**帳單 (作用中設定檔)** 技術工作流程失敗的問題。(NEO-19777)
* 修正了使用 ACS 連接器功能時，無法連線至 Campaign Standard 執行個體（FOH/FOH2 連線管理錯誤）的迴歸問題。(NEO-23433)
* 修正了無法在 Hadoop 表單擁有多欄位的主要金鑰建立綱要擴展的問題。(NEO-17390)
* 修正了&#x200B;**載入 (SOAP)**&#x200B;活動中，無法從 URL 載入 WSDL 檔案的問題。(NEO-16924)
* 修正了當多個作用中工作流程伺服器負載平衡時，無法透過主控台執行&#x200B;**無條件停止**&#x200B;的問題。(NEO-19556)
* 修正了造成清理工作流程當機的迴歸。
* 修正了在執行實例發佈範本時可能發生的問題。
* 修正了 collectPrivacyRequests 技術工作流程無法執行的問題。(NEO-20513、NEO-25169)
* 已修復在升級到build 9080後嘗試連接到Audience Manager時可能發生的問題。 (NEO-20511、NEO-25167)
* 修正了匯出 PDF 或 XLS 格式報表時可能發生的問題。(NEO-20982、NEO-23493、NEO-23348)
* 修正了傳送傳遞後，傳遞清單可能顯示傳送兩次的問題。
* 修正了傳遞準備問題，路由設定設為透過中間來源傳送傳遞時，可能會發生此問題。
* 修正了按下在 Line 訊息內的 Web 應用程式連結時，可能顯示錯誤訊息的問題。
* 修正了執行清理工作流程後，刪除了&#x200B;**增量查詢**&#x200B;活動歷史記錄的問題。
* 修正了建立中間來源外部帳戶時，NmsMidSourcing_LastBroadLog_&lt;InternalName> 選項遺失的問題.
* 修正了資料庫連線上的迴歸問題，造成 Web 伺服器因資料庫編碼問題而持續重新啟動。這可能導致過度耗用。(NEO-23264)


## 第 20.1 發行版本{#release-20-1}

### ![](assets/do-not-localize/limited_2.png)版本 20.1.4 - 版本編號 9126 {#release-20-1-4-build-9126}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2021年 3 月 22 日_

* 修正迴歸，防止在傳遞中使用主控台的某些元件，例如日期選擇器和影像管理。 （NEO-31453、NEO-31454）

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2020 年 12 月 23 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在 **2021 年 6 月 30 日**&#x200B;後與 Campaign 連線。[深入瞭解](../../technotes/using/ims-updates.md)
>
> * 此版本隨附[安全性修正](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。


* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)

### ![](assets/do-not-localize/red_2.png)版本 20.1.3 - 版本編號 9124{#release-20-1-3-build-9124}

_2020 年 5 月 6 日_

* 修正&#x200B;**檔案傳輸**&#x200B;活動使 SFTP 金鑰驗證無法在 Debian 9 運作的問題。(NEO-23183)

### ![](assets/do-not-localize/red_2.png)版本 20.1.2 - 版本編號 9123{#release-20-1-2-build-9123}

_2020 年 3 月 13 日_

* 已修復阻止在Red Hat 7伺服器上部署版本的問題。 (NEO-23332)

### ![](assets/do-not-localize/red_2.png)版本 20.1 - 版本編號 9122{#release-20-1-build-9122}

_2020年2月17日_

**有哪些新功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>SnowflakeFDA連接器</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake是一個完全托管的雲資料倉庫，旨在在儲存和計算級別進行擴展。 有了這種新的連接器，Adobe Campaign現在可以利用Snowflake的力量來執行大資料分割。 此連接器可供所有客戶使用，包括由Adobe托管。</p>
    <p>有關詳細資訊，請參閱 <a href="../../installation/using/configure-fda-snowflake.md">詳細文檔</a> 和 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">教程視頻</a>。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>HadoopFDA連接器增強</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>hadoopFDA連接器已經改進，以支援Hadoop3.0和Cloudera。</p>
    <p>如需詳細資訊，請參閱<a href="../../installation/using/configure-fda-hadoop.md">詳細文件</a>以瞭解詳情。</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 改進了報告配置中的安全性，以防止點擊劫持。 這適用於新報告。 對於舊報表，您需要重新發佈它們以應用更改。 (NEO-13282)

* 修復cryptString中的小記憶體問題。 (NEO-20071)

* 改進了顯示器JSP以修復內部IP洩漏。 (NEO-16821)

* 修復了可向非管理員用戶顯示堆棧跟蹤資訊的問題。 (NEO-12388)

* 改進了對以前會話中快取資料的管理。 (NEO-17039)

* 已修復阻止logins.log檔案通過IMS記錄成功登錄嘗試的問題。 (NEO-11004)

**功能改進**

* iOS13現在支援HTTP2連接器。

* 改進了推送通知功能（nms:address和nms:appSubscriptionRcp）使用的表的隔離管理和清理。 對於iOS（僅HTTP2連接器），禁用的令牌現在的處理方式與Android相同。 現在，在NmsAppSubscriptionRcp表中設定了禁用標誌。 [閱讀全文](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 已在 **JavaScript代碼** 和 **高級JavaScript代碼** 工作流活動，以定義超時期間。 這可防止JavaScript執行階段運行太長。 如果超時時間已過，則停止工作流。 預設超時為1小時。 [閱讀全文](../../workflow/using/sql-code-and-javascript-code.md)

* 當在中間採購伺服器上找不到匹配的關聯時，現在停止傳遞分析，並顯示相應的錯誤消息。

* 現在支援Postgres的資料庫故障切換：當資料庫伺服器崩潰並重新啟動時，Campaign現在自動重新連接到它。

* 的 **開始掛起** 視圖已添加到「管理」>「審計」>「工作流狀態」節點。 這允許您監視實例上等待由 **操作管理** 處理。 此視圖隨「市場營銷活動」包一起提供。 [閱讀全文](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**其他變更**

* 在Linux上，nlserver服務啟動現在使用系統單元，而不是/etc/init.d/nlserver6指令碼。 在安裝20.1軟體包時，會自動執行到新啟動方案的遷移。 /etc/init.d/nlserver6仍然提供，但是為了與nlserver服務（啟動、重新啟動、停止等）交互，建議您直接使用systemctl命令。

* 最耗用的自定義表已從 **xtkNewId** 序列。

* 改進的查詢效能，這些效能可能受不必要的資料庫連接的影響。

* 改進了資料庫更新嚮導的效能，使SQL陳述式數減少，以優化響應時間。

* 資料庫記錄管理已增強。

* 連接池的健壯性已得到改善，這可以防止意外連接故障的發生太頻繁。

* 增強了電子郵件地址驗證規則，以在軟錯誤時將地址發送到隔離。 [閱讀全文](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 對於Debian,Campign現在使用系統PCRE庫（如果可用）。

* 活動現在允許使用更新的系統ODBC庫。

* 開啟連接以載入富映像時，已向LINE Servlet添加超時。 如果映像載入時間過長，Servlet將停止連接以避免瓶頸。

**修補程式**

* 已修復使用Hadoop連接器時的帳戶密鑰加密問題。

* 已修復因實施SSL認證而導致用戶連接在Windows伺服器上失敗的回歸問題。 (NEO-20629)

* 在工作流ID為負時，已修復增量查詢活動的問題。 (NEO-19779)

* 通過NetezzaFDA連接器運行查詢時，已解決編碼問題。 (NEO-19594)

* 已修復在中使用POST方法時導致錯誤的問題 **Web下載** 工作流事件活動。

* 已通過生成產品建議來解決問題。 (NEO-18176)

* 使用獲取Web表單模板時修復了頁腳顯示問題。

* 解決了分析連續傳遞內容中URL時可能導致其崩潰的問題。 (NEO-16910)

* 已修復 **開始** 和 **結束** 建立新市場活動時未計算的欄位。

* 已修復 **檔案下載** 使用URL時的工作流活動。

* 在報表的查詢活動中預覽導入的清單時修復了問題。 (NEO-13119)

* 已修復在選擇 **由市場活動支援** 電子郵件編輯器中的個性化塊。

* 客戶端與伺服器之間的網路通信得到改進。

* 在同一市場活動中建立過多工作流時，已修復問題。 現在，您不能建立28個以上的工作流。 將顯示警告。

* 使用 **選擇列** 協調選項 **聯合** 工作流活動。

* 修復了使用工作流中損壞的濃縮清單時可能發生的控制台崩潰問題。 (NEO-18096)

* 已修復工作流中可能發生的各種控制台崩潰問題(NEO-18010、NEO-18032)

* 已修復允許執行 **外部信號** 工作流活動，即使它被禁用。 (NEO-17524)

* 已修復建立新架構時的問題。

* 已解決發送SMS消息時的跟蹤問題。 (NEO-19595)

* 已修復在傳遞指示符中顯示不正確的目標受眾編號的問題。

* 修復了在通過工作流活動生成說明性報告時顯示不正確百分比的問題。 (NEO-14314)

* 修復了使交貨吞吐量報告在時間視圖參數時顯示不同數字的問題。 (NEO-11783)

* 已修復阻止事務性消息跟蹤指示符由跟蹤工作流更新的問題。 (NEO-17770)

* 修復了在通過SOAP請求提供服務時導致Web進程崩潰並重新啟動的回歸問題。 (NEO-19482)

* 修復了如果上載目錄是遠程共用位置，則無法將資料上載到公共資源的問題。 (NEO-19361)

* 已修復導致 **從Adobe Experience Cloud引進觀眾** 技術工作流程不斷失敗。 (NEO-18463)

* 已修復在使用從Experience Manager導入的模板時無法發送交貨的問題。 (NEO-17540)

* 已修復升級到build 9032並阻止實例通過SSL協定連接到FTP伺服器後出現的問題。 (NEO-20498)

* 已修復刪除、插入或更新大量資料時出現的問題 **更新資料** 使用FDA架構作為目標維的工作流中的活動。 (NEO-13280)

* 修復了在HTML內容標籤外部存在Javascript代碼時阻止發送電子郵件的問題。 (NEO-18628)

* 已修復嘗試從已發送郵件的傳遞日誌中顯示鏡像頁面時出現的問題。 (NEO-17976)

* 已修復阻止 **連結到鏡像頁** 個性化塊 **文本內容** 頁籤 **導入HTML** 送來。 (NEO-17568)

* 按一下到已過期的鏡像頁的連結時顯示的錯誤消息已澄清。 (NEO-17340)

* 已修復導致某些按鈕無法在 **資料分佈** 建立螢幕。

* 已修復在以Asia/Kolkata為時區的實例中安排交付活動時發生的問題。 (NEO-20001)

* 傳遞出現關聯配置問題時，現在會顯示錯誤。

* 已修復在中顯示錯誤版本標籤號的問題 **關於** 的子菜單。

* 修復了嘗試從工作流中重複交貨的屬性更新工藝路線帳戶時出現的問題。 (NEO-18684)

* 修復了通過重定向模組連接到實例時出現的問題，這防止了連接在關閉後被正確清理。
