---
title: 最新版本
description: 最新Campaign Classic發行說明
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 3%

---


# 最新版本{#latest-release}

本頁列出最新版Campaign Classic Release Candidate隨附的新功 **能、改進和修正**。

如需Campaign Classic Gold Standard版本（最新的GA組建版本）, [請參閱本頁](../../rn/using/gold-standard.md)。

## ![](assets/do-not-localize/blue_2.png) 版本 20.3.1 - Build 9228 {#release-20-3-1-build-9228}

_2020年10月27日_

**新增功能？**

<table> 
<thead>
<tr> 
<th> <strong>iOS推播通知改進</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>將行動應用程式與Campaign整合時，您需要使用Apple推播通知服務(APN)保護您的通訊安全。 您可以使用憑證式或Token式驗證。
</p>
<p>這兩種驗證模式現在可用於Campaign Classic中的iOS行動應用程式：
</p>
<ul> 
<li><p>Token型驗證（建議）:此驗證模式以。p8檔案為基礎。 對APN的每個請求都包含令牌，因此此驗證模式更快。 <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">進一步瞭解</a></p></li>
<li><p>憑證式驗證：此驗證模式是以。p12檔案為基礎。 對於每個應用程式，都需要個別的憑證。 此憑證由Apple透過您的開發人員帳戶傳送。 <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">進一步瞭解</a></p></li> 
</ul>
<p>在詳細檔案中瞭解如何在Campaign中選取驗 <a href="../../delivery/using/configuring-the-mobile-application.md">證模式</a>。</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Android推播通知改進</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Android推播通知已改進，可支援FCM HTTP v1 API，以用於Android推播頻道驗證。 </p>
<p>有了新的支援的API版本，您現在可以傳送FCM通知訊息，提供增強的豐富式推播訊息功能。 <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">進一步瞭解</a></p> 
<p>在本節中瞭解如何在Adobe Campaign中為Android設定FCM HTTP v1 <a href="../../delivery/using/configuring-the-mobile-application-android.md">API</a> 。</p>
</td> 
</tr> 
</tbody> 
</table>

**安全性增強功能**

* 安全載入程式庫：為了防止DLL預載攻擊，Campaign現在僅從Windows預設系統DLL路徑載入Windows DLL，同時載入Campaign用戶端(nlclient)。 [更多資訊](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* 已修正安全性問題，以加強針對伺服器端偽造要求(SSRF)攻擊的保護。 (NEO-25661)
* 修正處理GDPR隱私權要求時，無法從與收件者表格具有第二層級關係的自訂表格中刪除記錄的問題。 (NEO-25967)
* 修正非管理員使用者在嘗試同步Adobe Experience Manager範本時，使用API呼叫的安全性問題。 (NEO-23487)

**相容性更新**

下列系統現在已支援 Campaign：
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**棄用的功能**

20.3中不建議使用下列功能：

* 用於匯入觀眾並匯出至Adobe Experience Cloud的Demdex網域已過時。 如果您使用Demdex網域做為匯入／匯出外部帳戶，則需要依此調整實作。 [進一步瞭解](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* 觸發整合驗證原本以oAUTH驗證設定為基礎，以存取管道，現在已變更並移至Adobe I/O。 [進一步瞭解](../../integrations/using/about-triggers.md)

進一步瞭解「已過時 [和已移除的功能」頁面](../../rn/using/deprecated-features.md)。

**功能改善**

* 對客戶端控制台進行了幾 **項改進**:
   * 為避免與某些網際網路安全GPO規則限制不相容，Campaign用戶端主控台登入畫面已由內建的標準Windows表單取代。
   * 修正使用64位元用戶端主控台在工作流程中複製／貼上活動的問題。 (NEO-27635)
   * 在「關 **於** 」菜單中，已添加資訊來區分64位和32位控制台。
* 當繼續工作流程時，工作流程識別碼現在會顯示在記錄檔中，這可讓您更清楚地識別已繼續的工作流程。
* 已引入新的永久Cookie:nllastdelid. 此Cookie（UUID230除外）將儲存deliveryId。 當作業Cookie不存在時，會從此Cookie中存在的deliveryId擷取廣播資訊。
此變更修正了瀏覽器工作階段結束時發生的問題：已刪除包含deliveryId和broadlogId的作業Cookie。 若沒有deliveryId，則找不到Broadlog資訊，而且若是永久追蹤（上次傳送），追蹤表格資訊將會遺失。
在本節中進一步了 [解Cookie](../../platform/using/privacy-and-recommendations.md#cookies)。
* 透過傳送傳送前重新啟動MTA程式，改善可傳送性伺服器的高容量傳送總處理能力。

**其他變更**

* 當使用SFTP的相對路徑時， `~/` 不再自動新增字元。 如有需要，您可以手動 `~/` 將字元新增至路徑，但Adobe建議使用絕 **對路徑**。
* 使用Microsoft SQL Server配置新資料庫時，已從可用的驗證方法中刪除Windows NT驗證。 [顯示全文](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* 資料庫清理工作流已針對Teradata進行優化，以提高效能。 (NEO-19959)
* 已改善從Adobe Target插入影像時顯示的錯誤訊息，而外部帳戶中的租用戶名稱為空。
* 在傳送屬性中， **[!UICONTROL Archive emails]** 選項已重新命名 **[!UICONTROL Email BCC]**。
* 為了提高魯棒性，現在拒絕選擇具有無效節點的所有查詢。 如果您需要停用檢查並返回先前的行為，可將XtkSecurity_Disable_QueryCheck設為0。

**技術演變**

Tomcat已從7版(7.0.103)更新為8版(8.5.57)。

目 `tomcat-7` 錄將替換為目 `tomcat-8` 錄。

在windows上， _iis_neolane_setup.vbs_ 和 _apache_neolane.conf_ 現在安裝在目錄 `conf` 中(而非 `tomcat-7/conf` 先前)。

在linux上， _apache_neolane.conf_ 現在安裝在目 `conf` 錄中。

**修補程式**

* 修正無法重新計算傳送統計資料的問題。
* 修正當使用舊版建置連結至伺服器的Campaign Classic 9080建置上傳CSV檔案時，顯示錯誤訊息的問題。 (NEO-23218)
* 修正為外部帳戶設定Microsoft Dynamics CRM精靈時，可能顯示錯誤訊息的問題。 這是由於與最新MS Dynamics CRM API版本的相容性問題。 (NEO-24528)
* 修正無法使用CRM連接器，將查詢類型記錄（即由與其他表格連接的外鍵記錄組成的資料）從Campaign Classic匯出至Microsoft Dynamics的問題。 (NEO-23864)
* 修正在CRM連接器中啟用「自動索引」選項時，無法擷取Microsoft Dynamics **資料** 的問題。 (NEO-25981)
* 修正IMS驗證問題，即使連線已結束，仍可能會開啟連線。 終止的連接現在會在結束時自動關閉，以避免累積連接並佔用系統資源。 (NEO-25996)
* 修正由於外部帳戶（帳戶或密碼不正確）的設定錯誤，導致Adobe Experience Manager內容同步傳送失敗時，未顯示錯誤訊息的問題。 現在會在失敗時顯示訊息，讓您更輕鬆地識別問題。 (NEO-25586)
* 修正在「更新」資料活動中選取「 **更新** 」作業類型時 **發生的問題** 。 如果要更新的資料不正確，工作流程將會出錯並失敗。 如果資料不正確，工作流程不會失敗，且記錄會儲存至「拒絕 **出站** 」轉場。 (NEO-23794)
* 修正包含子工作流程的工作流程無法運作的問題。 (NEO-24036)
* 修正編輯促銷活動範本說明時，複製貼上符號（例如日文字元）時無法顯示「 **Save** 」（儲存）按鈕的問題。 (NEO-27071)
* 修正無法變更執行個體設定精靈中追蹤伺服器的問題。
* 修正在按一下「儲存」按鈕之前，按一下視窗外部時無法儲存促銷活動或促銷活動範本說 **明的** 問題。 (NEO-27449)
* 修正「有效帳單設定檔數 **目」(billingActiveContactCount** )技術工作流程無法運作的問題。 如果已在架構擴充的計算欄位上執行連結，就會發生此情況。 大量的資料被建立，這可能導致資料庫用盡臨時空間。 (NEO-24062)
* 修正「資料載入(檔 **案)** 」活動的問題，如果日文字元位於檔案結尾，就無法從txt和csv檔案匯入。 (NEO-24957)
* 修正連續傳送無法正確填入「分 **析已開始****」和「分析已完成** 」欄位的問題。 (NEO-20755)
* 修正嘗試在 **Recipient** (nms:recipient)以外的其他架構上的查詢後預覽SMS訊息時，可能顯示錯誤訊息的問題。 (NEO-27517)
* 已修正使用雪花FDA連接器時的問題。 具有雪花FDA訪問名稱權限的用戶無法對雪花架構執行查詢。 記錄檔中顯示「找不到密碼」類型的錯誤。 (NEO-23851)
* 修正使用FDA連接器時，連結的FDA架構名稱是目前架構之元素名稱的子字串時所發生的問題。 例如，如果FDA架構是「cust」，而收件者架構中的其中一個元素是「customer」，就會發生這種情況。 在提取&quot;customer&quot;元素內的列並從&quot;cust&quot; FDA架構中添加列時，缺少本地列的值。 (NEO-20193)
* 修正從外部資料庫擷取記錄並將記錄插入促銷活動資料庫時，工作流程中的問題。 (NEO-26359)
* 修正「更新事件狀態」 **技術工作流程中** :為了符合傳送統計資料活動中傳入對應欄位的大小 ******** ,「更新傳送統計資料」活動中三個目標欄位的大小已從32位變更為64位。 (NEO-11557)在本節中進一步瞭解 **更新事件狀態**[工作流程](../../workflow/using/message-center--execution-.md)。
* 修正「訊息中心事 **** 件歷史記錄」報表中，嘗試套用篩選器時造成指令碼錯誤，且無法依日期範圍篩選的問題。 (NEO-23365)
* 修正促銷活動工作 **(operationMgt)與** Preview **** (forecasting)技術工作流程之間的干擾問題。 當排程的傳送維持在「目標就緒」或「就緒即可傳送」狀態時，就會發生此情況。 (NEO-20819)
* 修正xtkOperator的mdata欄位中未顯示XML識別碼時的XML剖析問題。 它導致了腳蹬故障。 (NEO-26113)
* 修正使用連結至SSL中加密之Azure外部帳戶的 **File Transfer** （檔案傳輸）活動時，使用HTTP而非HTTPS進行連線的問題。 (NEO-26720)
* 修正MSSQL資料庫在清除工作流程期間，up_updatestats程式可能發生錯誤的問題。
* 修正當Web進程關閉期間，如果仍在處理互動請求時發生當機的問題。 (NEO-26447)
* 修正Oracle DB中的 **NoNull** 函式在升級9032後無法再工作的問題。 (NEO-26488)
* 修正如果未安裝訊息中心套件而安裝LINEV2套件，在升級9171後追蹤工作流程失敗的問題。
* 修正由於屬性&#39;APP&#39;的資料庫連線字串最終獲得無效值，導致連線池無法增加至所需連線數的可擴充性問題。 (NEO-25105)
* 修正在代理設定層級，導致您無法在最新Windows 10更新後登入Adobe Campaign的問題。 (NEO-27813)
* 修正匯入包含追蹤連結的HTML範本後，傳送的電子郵件中會顯示不想要的URL的問題。 (NEO-25909)
* 修正在工作流程中顯示「分割」活動之餘項的目標資料時，造成伺服器當機 **的問** 題。
* 修正清除運算式剖析器時防止記憶體損毀的伺服器損毀問題。 (NEO-26856)
* 修正非管理員使用者定義例項變數的擴充活動問題。 (NEO-25653)