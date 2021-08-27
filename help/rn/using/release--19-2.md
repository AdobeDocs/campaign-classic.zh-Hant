---
product: campaign
title: 第 19.2 發行版本
description: Campaign 19.2發行說明
exl-id: 3c529e4e-8787-41d2-b85d-3feaa5432196
source-git-commit: 84312974b9b7372c8a46fd1c7ead1148690bcd83
workflow-type: tm+mt
source-wordcount: '1542'
ht-degree: 21%

---

# 第 19.2 發行版本{#release-19-2}

![](../../assets/v7-only.svg)

## ![](assets/do-not-localize/limited_2.png) 發行版本 19.2.4 - 版本編號 9082 {#release-19-2-4-build-9082}

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
> * 此版本隨附[安全性修正](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。



* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)

## ![](assets/do-not-localize/red_2.png) 發行版本 19.2.3 - 版本編號 9081 {#release-19-2-3-build-9081}

_2020年2月7日_

**功能改善**

* 修正因實作SSL憑證而導致使用者連線在Windows伺服器上失敗的回歸問題。 (NEO-20629)
* 修正&#x200B;**關於**&#x200B;功能表中顯示錯誤版本標籤編號的問題。

## ![](assets/do-not-localize/red_2.png) 發行版本 19.2 - 版本編號 9080 {#release-19-2-build-9080}

_2019 年 12 月 2 日_

**有哪些新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>加州消費者隱私法(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA是加州新推出的隱私權法，協調2020年1月1日起生效的資料保護要求並以現代化方式規範資料保護要求。 CCPA適用於為居住在加州的資料主體保管資料的Adobe Campaign客戶。</p>
    <p>除了現有的隱私權功能（包括同意管理、資料保留設定和使用者角色）之外，Adobe Campaign還可協助您為CCPA做好準備：</p>
    <ul>
      <li>存取權與刪除權：我們善用針對GDPR新增的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">顯示全文</a></li>
      <li>您可以追蹤消費者是否選擇退出個人資訊銷售。 為此，您需要擴充「設定檔」表格，並新增<strong>CCPA</strong>選擇退出欄位。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">顯示全文</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>工作流程即時監控</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>您現在可以使用預先定義的檢視，監控執行個體上所有工作流程的執行狀態。</p>
   <p>如需詳細資訊，請參閱<a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">詳細文件</a>，以瞭解詳情。</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>AMP互動式內容</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign可讓您試用全新互動式<a href="https://amp.dev/about/email/"> AMP for Email</a>格式，讓行銷人員能在訊息中加入AMP元件，以利用豐富、動態的互動式內容提升電子郵件體驗，並直接在訊息中轉化為實際行動。</p>
   <p>此功能已發佈公開測試版。</p>
   <p>如需詳細資訊，請參閱<a href="../../delivery/using/defining-interactive-content.md">詳細文件</a>及<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">教學影片</a>。</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>安全SMS傳訊(TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>現在透過Extended Generic SMPP連接器支援安全SMS。 這允許與提供者的加密連線。</p> <p><strong></strong> 警告：所有伺服器上都需要最新憑證才能使用此功能。憑證無效、撤銷或過期將產生錯誤，影響整體SMS傳送功能。</p><p>如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/sms-connector-protocol-and-settings.html">詳細文件</a>，以瞭解詳情。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 修正Campaign介面中儲存的跨網站指令碼漏洞 — 輸入資料驗證和輸出編碼。 (NEO-16810)
* 修正設定檔授權的安全問題，此問題可借由加強登入限制政策允許存取未授權的資料。 (NEO-14445)

**功能改善**

* 推播通知的記憶體耗用最佳化。
* 為達到效能和儲存最佳化，已增強&#x200B;**logins.log**&#x200B;檔案的處理。 檔案現在會分割為多個檔案，每天最多可保留365個檔案。 [顯示全文](../../production/using/log-files.md)
* 現在可以使用密碼憑證（密碼+使用者名稱）或憑證（私密金鑰）來設定Microsoft Dynamics CRM外部帳戶。 [顯示全文](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* hadoopFDA連接器已新增一些增強功能，以改善可靠性
* 已添加特定防護欄，以在允許上載伺服器上的公共資源之前檢查磁碟空間。
* 已新增新的[促銷活動選項](../../installation/using/configuring-campaign-options.md):
   * **WdbcKillSessionPolicy**&#x200B;配置選項允許您在所有工作流和PostgreSQL資料庫查詢上影響&#x200B;**無條件停止**&#x200B;行為。
   * **NmsOperation_DeliveryPreparationWindow**&#x200B;選項可讓您定義超過天數，系統會將狀態不一致的傳送從執行中的傳送計數中排除。
   * **WdbcOptions_TempDbName**&#x200B;選項允許您為Microsoft SQL Server上的工作表配置單獨的資料庫。 這樣可優化備份和複製。 [顯示全文](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * 已增強PostgreSQL的&#x200B;**XtkCleanup_NoStats**&#x200B;選項，以更好地控制資料庫清理工作流的儲存優化步驟的行為。 [顯示全文](../../production/using/database-cleanup-workflow.md#statistics-update)
* 帳戶鎖定機制已添加到&#x200B;**logon()** API中。 它可防止在指定時間範圍內連續嘗試某些次數的失敗登入之後，再嘗試任何登入。
* 傳遞屬性中新的&#x200B;**最大個人化執行時間**&#x200B;選項可讓您定義個人化執行時間的逾時期間，以防止個人化階段執行時間過長。 [顯示全文](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 已新增&#x200B;**ftp通訊協定**&#x200B;選項，可讓您為SFTP連線使用代理設定。 [顯示全文](../../installation/using/file-res-management.md)
* 針對內部部署環境，全新支援代理存取SFTP外部伺服器。
* 已新增特定護欄，以防止安裝與Campaign執行個體不相容的套件。 [顯示全文](../../installation/using/installing-campaign-standard-packages.md)

_棄用的系統_

下列系統現在[已棄用](https://helpx.adobe.com/tw/campaign/kb/deprecated-and-removed-features.html)，適用於Campaign Classic實施：
* Apache 2.2
* 琴托斯6

請確定您使用最新Campaign相容性矩陣所列之任何系統的支援版本。 [顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

_Campaign行動SDK_

iOS SDK的組建版本1.0.26現已可用。 在這個新組建中，我們新增了iOS 13的支援。 這個新版本現在支援iOS 13推播通知的通知優先順序和新的註冊代號管理程式。 如果您在舊版SDK上執行應用程式，則需使用新SDK重新編譯應用程式。 若要取得SDK，請聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**修補程式**

* 修正&#x200B;**資料載入(RDBMS)**&#x200B;工作流程活動中，**新增連結的表格**&#x200B;欄位空白時的當機問題。 (NEO-12213)
* 修正了可能導致Mid-Sourcing伺服器無法處理某些訊息的問題。 (NEO-12395)
* 修正將查詢區段選項與Teradata搭配使用時，資料庫清理工作流程中的問題。 (NEO-12399)
* 修正影響傳遞分析的類型規則（包括ne.jp網域）問題。 (NEO-12609)
* 修正暗示憑證原則限制較嚴格的TLS更新簡訊相關問題。 這些更新可能會在發出過期憑證時，導致行銷與中間來源伺服器之間發生連線失敗。 (NEO-17698)
* 修正了在具有保管庫驗證的中間來源環境中，對外部帳戶使用&#x200B;**測試連線**&#x200B;按鈕的問題。 (NEO-12722)
* 修正搭配FDAHadoop連線使用日期函式進行查詢的問題。 (NEO-12847)
* 修正在電子郵件編輯器中取代影像時的問題。 (NEO-13098)
* 修正了可能導致資料夾升級後錯誤的問題，這些資料夾已被刪除或移至其他位置。 (NEO-13118)
* 修正在LINE訊息上使用&#x200B;**Define image per device screen size**&#x200B;選項時，影像顯示的問題。 (NEO-13228)
* 修正取消選取「在傳送期間排除重複位址&#x200B;**」選項時的傳送準備問題。**(NEO-13240)
* 修正了工作流程中使用&#x200B;**檔案傳輸**&#x200B;活動，使用&#x200B;**傳輸**&#x200B;後刪除來源檔案選項（名稱包含空格字元）下載檔案的問題。 (NEO-13411)
* 修正了Tomcat快取清除可能導致記憶體問題的問題。 (NEO-13456)
* 修正在Microsoft SQL 2017中執行的現有控制執行個體上安裝具有執行執行個體&#x200B;**內建套件的選件引擎控制項時的問題。**(NEO-13539)
* 修正了由於未初始化變數，從&#x200B;**Text content**&#x200B;標籤取消勾選電子郵件中追蹤的URL時，可能發生的主控台當機問題。 (NEO-13545)
* 修正中文寄件者名稱的編碼問題。 (NEO-13837)
* 修正從「瀏覽器」顯示調查回應資料時可能會引發的錯誤。 (NEO-14590)
* 修正了可能導致傳送記錄檔分類與隔離表格不一致的問題。 (NEO-16547)
* 修正未內嵌至電子郵件的DKIM金鑰問題。 (NEO-16804)
* 修正在API呼叫的內容中使用無效工作階段代號來觸發事件時，顯示錯誤錯誤代碼的問題。 錯誤代碼為「HTTP 200 OK」，而非「HTTP 403 Forbidden」。 (NEO-16826)
* 修正透過網頁存取顯示傳送報告時的問題。 (NEO-17015)
* 修正登入Adobe Campaign時的IMS驗證問題。 (NEO-17312)
* 修正隱私權管理程式無法刪除隔離電子郵件的問題。 (NEO-17314)
* 修正使用SQL資料庫升級至9031後的輸送量問題。 (NEO-17558)
* 修正了影響CRM連接器與Salesforce的問題。 (NEO-17712)
* 修正從外部SFTP匯入資料時的逾時問題。 (NEO-19723)
* 修正存取預測模型時的問題。 (NEO-19713)
* 修正&#x200B;**Split**&#x200B;工作流程活動中，影響HadoopFDA資料庫的隨機取樣的問題。 (NEO-16636)
* 修正Oracle上的回歸，導致在升級後後部分函式被視為無效。 (NEO-12759)
