---
solution: Campaign Classic
product: campaign
title: Campaign 20.3發行說明
description: Campaign 20.3的發行說明
feature: Overview
role: Business Practitioner
level: Beginner
translation-type: tm+mt
source-git-commit: 1f718e26aeaa5ed5a58dfd0e3bc29d2dd9e995ee
workflow-type: tm+mt
source-wordcount: '1952'
ht-degree: 95%

---


# 20.3 發行版本{#release-20-3}

## ![](assets/do-not-localize/red_2.png) 版本 20.3.3 - Build 9234 {#release-20-3-3-build-9234}

_2021年1月11日_

* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)
* 修正了與 broadlog 產生程序相關的迴歸問題，而此問題可能導致 MTA 程序當機。

## ![](assets/do-not-localize/red_2.png) 版本 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_2020 年 10 月 27 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您透過Adobe身分服務(IMS)連線至促銷活動，則促銷活動伺服器和用戶端主控台都必須進行升級，才能在2021年6月30日&#x200B;**之後連線至促銷活動。**
> * 此版本隨附於[安全性修正](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：升級是強化環境安全的必備條件。
> * 如果您正透過驗證使用Experience Cloud觸發器整合，則需依照本頁[所述移至Adobe I/O。 ](../../integrations/using/configuring-adobe-io.md)具有促銷活動的舊式驗證模式將於2021年11月30日&#x200B;****&#x200B;淘汰。


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
   * 已更新連線通訊協定，以遵循新的 IMS 驗證機制。在2021年6月30日之後必須能連線伺服器和用戶端主控台升級。
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
