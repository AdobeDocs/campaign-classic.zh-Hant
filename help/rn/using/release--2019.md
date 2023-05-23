---
product: campaign
title: Campaign Classic 2019 版本
description: 進一步瞭解 Campaign Classic 2019 版本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '4825'
ht-degree: 24%

---

# 2019 版本{#release-2019}



## 第 19.2 發行版本{#release-19-2}

### ![](assets/do-not-localize/limited_2.png)版本 19.2.4 - 版本編號 9082 {#release-19-2-4-build-9082}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2021年3月22日_

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

### ![](assets/do-not-localize/red_2.png)版本 19.2.3 - 版本編號 9081 {#release-19-2-3-build-9081}

_2020年2月7日_

**功能改進**

* 已修復因實施SSL認證而導致用戶連接在Windows伺服器上失敗的回歸問題。 (NEO-20629)
* 已修復在中顯示錯誤版本標籤號的問題 **關於** 的子菜單。


### ![](assets/do-not-localize/red_2.png)版本 19.2 - 版本編號 9080 {#release-19-2-build-9080}

_2019 年 12 月 2 日_

**有哪些新功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>加利福尼亞消費者隱私法(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA是加利福尼亞州新的隱私法，它統一和現代化了將於2020年1月1日生效的資料保護要求。 CCPA適用於Adobe Campaign客戶，這些客戶持有位於加利福尼亞的資料主題資料。</p>
    <p>除了現有的隱私功能（包括許可管理、資料保留設定和用戶角色）外，Adobe Campaign還幫助您做好CCPA的準備：</p>
    <ul>
      <li>訪問權和刪除權：我們正在利用為GDPR添加的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">深入了解</a></li>
      <li>您可以跟蹤消費者是否已選擇出售個人資訊。 為此，需要擴展「配置式」表並添加 <strong>CCPA的退出選項</strong> 的子菜單。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">深入了解</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>工作流即時監視</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>現在，您可以使用預定義視圖監視實例上所有工作流的執行狀態。</p>
   <p>如需詳細資訊，請參閱<a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">詳細文件</a>以瞭解詳情。</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>使用AMP的互動式內容</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign讓你嘗試新的互動式 <a href="https://amp.dev/about/email/">電子郵件的AMP</a> format ，它允許營銷人員在郵件中包括AMP元件，以增強電子郵件體驗，內容豐富，動態和互動式，可直接在郵件中操作。</p>
   <p>此功能作為公共測試版發佈。</p>
   <p>如需詳細資訊，請參閱<a href="../../delivery/using/defining-interactive-content.md">詳細文件</a>及<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">教學影片</a>。</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>安全SMS消息(TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>現在，通過擴展通用SMPP連接器支援安全SMS。 這允許與提供程式的加密連接。</p> <p><strong>警告</strong> 此功能要求所有伺服器上都有最新的證書。 無效、吊銷或過期的證書將生成影響整體SMS發送功能的錯誤。</p><p>如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/sms-connector-protocol-and-settings.html">詳細文件</a>以瞭解詳情。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 市場活動介面中的固定儲存跨站點指令碼漏洞 — 輸入資料驗證和輸出編碼。 (NEO-16810)
* 通過加強登錄限制策略，解決了配置檔案授權的安全問題，該安全問題允許訪問未授權資料。 (NEO-14445)

**功能改進**

* 推送通知的記憶體消耗優化。
* 對於效能和儲存優化， **登錄.log** 檔案已增強。 現在，該檔案被拆分為多個檔案，每天一個，最多保留365個檔案。 [深入了解](../../production/using/log-files.md)
* MicrosoftDynamics CRM外部帳戶現在可以使用密碼憑據（密碼+用戶名）或證書（私鑰）進行配置。 [深入了解](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* hadoopFDA連接器已添加了一些增強功能，以提高可靠性
* 已添加特定保護欄，以在允許上載伺服器上的公共資源之前檢查磁碟空間。
* 新建 [市場活動選項](../../installation/using/configuring-campaign-options.md) 已添加：
   * 的 **WdbcKillSessionPolicy** 配置選項允許您 **無條件停止** 所有工作流和PostgreSQL資料庫查詢的行為。
   * 的 **NmsOperation_DeliveryPreparation窗口** 選項允許您定義在運行交貨數量中排除狀態不一致的交貨的天數。
   * 的 **WdbcOptions_TempDbName** 選項，用於為MicrosoftSQL Server上的工作表配置單獨的資料庫。 這可優化備份和複製。 [深入了解](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * 的 **XtkCleanup_NoStats** 已對PostgreSQL的選項進行了增強，以更好地控制資料庫清理工作流的儲存優化步驟的行為。 [深入了解](../../production/using/database-cleanup-workflow.md#statistics-update)
* 已將帳戶鎖定機制添加到 **登錄()** API。 它防止在指定時間範圍內連續嘗試一定數量的登錄失敗後再嘗試登錄。
* 新 **最大個性化運行時間** 交付屬性中的選項允許您定義個性化運行時間的超時期間，以防止個性化階段運行過長。 [深入了解](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 的 **ftp協定** 已添加選項，以允許您對SFTP連接使用代理配置。 [深入了解](../../installation/using/file-res-management.md)
* 新支援對SFTP外部伺服器的代理訪問，用於內部環境。
* 已添加特定的保護欄，以防止安裝與市場活動實例不相容的包。 [深入了解](../../installation/using/installing-campaign-standard-packages.md)

_不建議使用的系統_

以下系統現在 [棄用](deprecated-features.md) 用於Campaign Classic實現：
* Apache 2.2
* 琴托斯6

請確保您位於最新市場活動相容性清單中列出的所有系統的受支援版本。 [深入了解](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

_活動移動SDK_

iOSSDK的1.0.26版現已提供。 在這個新的建築里，我們增加了iOS十三號的支援。 此新版本現在支援iOS13推送通知的通知優先順序和新的註冊令牌管理過程。 如果您在SDK的早期版本上運行應用程式，則需要使用新SDK重新編譯應用程式。 要獲取SDK，請聯繫 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**修補程式**

* 已修復崩潰問題 **添加連結表** 欄位為空 **資料載入(RDBMS)** 工作流活動。 (NEO-12213)
* 已修復可能導致中間採購伺服器無法處理某些消息的問題。 (NEO-12395)
* 將查詢分段選項與Teradata一起使用時，已修復資料庫清理工作流中的問題。 (NEO-12399)
* 通過包括ne.jp域的類型規則解決了影響傳遞分析的問題。 (NEO-12609)
* 已修復與TLS更新上的SMS相關的問題，這意味著證書策略的限制更嚴格。 這些更新可能導致市場營銷和中間採購伺服器之間的連接失敗，以防證書過期。 (NEO-17698)
* 使用 **Test連接** 的子菜單。 (NEO-12722)
* 使用帶有FDAHadoop連接的日期函式修複查詢問題。 (NEO-12847)
* 在電子郵件編輯器中替換影像時已修復問題。 (NEO-13098)
* 已修復可能導致已刪除或移動到其他位置的資料夾升級後錯誤的問題。 (NEO-13118)
* 使用 **按設備螢幕大小定義影像** 選項。 (NEO-13228)
* 在 **在交貨期間排除重複地址** 選項。 (NEO-13240)
* 使用 **檔案傳輸** 活動：使用 **傳輸後刪除源檔案** 選項，其中名稱包含空格字元。 (NEO-13411)
* 修復了Tomcat快取清理問題，這可能導致記憶體問題。 (NEO-13456)
* 已修復安裝時的問題 **具有執行實例的供應引擎的控制** 在MicrosoftSQL 2017中運行的現有控制實例上內置的包。 (NEO-13539)
* 修復了在取消檢查電子郵件中跟蹤的URL時可能發生的控制台崩潰問題 **文本內容** 頁籤。 (NEO-13545)
* 已修復中文發件人名稱的編碼問題。 (NEO-13837)
* 已修復在顯示瀏覽器的調查響應資料時可能引起的錯誤。 (NEO-14590)
* 已修復可能導致交貨日誌分類與隔離表不一致的問題。 (NEO-16547)
* 已解決未嵌入電子郵件的DKIM鍵的問題。 (NEO-16804)
* 修復了在API調用上下文中使用無效會話令牌以觸發事件時顯示錯誤錯誤代碼的問題。 錯誤代碼為「HTTP 200 OK」，而不是「HTTP 403 Forbidded」。 (NEO-16826)
* 通過Web訪問顯示交貨報告時已修復問題。 (NEO-17015)
* 已解決登錄Adobe Campaign時的IMS身份驗證問題。 (NEO-17312)
* 已修復阻止隱私管理進程刪除隔離電子郵件的問題。 (NEO-17314)
* 使用SQL資料庫升級到9031後，已解決吞吐量問題。 (NEO-17558)
* 已修復影響Salesforce的CRM連接器的問題。 (NEO-17712)
* 從外部SFTP導入資料時已修復超時問題。 (NEO-19723)
* 已修復訪問預測模型時的問題。 (NEO-19713)
* 修復影響中隨機採樣的問題 **拆分** 與HadoopFDA資料庫的工作流活動。 (NEO-16636)
* 修復Oracle上的回歸，導致某些函式在放置後被視為無效。 (NEO-12759)


## 第 19.1 發行版本{#release-19-1}

### ![](assets/do-not-localize/limited_2.png)版本 19.1.8 - 版本編號 9039 {#release-19-1-8-build-9039}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)
* 已修復可阻止工作流資料導出到FDA資料庫的回歸(Teradata、Snowflake)。

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2021年3月22日_

* 修正迴歸，防止在傳遞中使用主控台的某些元件，例如日期選擇器和影像管理。 （NEO-31453、NEO-31454）

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2020 年 12 月 16 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在 **2021 年 6 月 30 日**&#x200B;後與 Campaign 連線。[深入瞭解](../../technotes/using/ims-updates.md)
> * 此版本隨附[安全性修正](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。
> * 如果您透過 oAuth 驗證使用 Experience Cloud 觸發程式整合，您必須依照[本頁](../../integrations/using/configuring-adobe-io.md)所述移至 Adobe I/O。**2021 年 9 月**[已淘汰](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)具有 Campaign 的舊版 oAuth 驗證模式。 託管環境繼續使用延伸功能，直到 **2022 年 2 月 23 日**。作為本地或混合型客戶，請與Adobe客戶服務部門聯繫，將支援期限延長至2022年2月。 您必須向 Adobe 提供 [OAuth 應用程式的 AppID](../../integrations/using/configuring-pipeline.md#step-optional)。



**功能改進**

* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 最初基於oAUTH身份驗證設定訪問管道的觸發器整合身份驗證已更改並移到Adobe I/O。 [瞭解更多資訊](../../integrations/using/configuring-adobe-io.md)
* 在 iOS APN 舊版二進位通訊協定支援結束之後，在升級後期間，使用此通訊協定的所有執行個體都會更新為 HTTP/2 通訊協定。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)
* 已修復連接錯誤後導致SMPP連接器停用的問題，防止發送其他SMS傳送，並導致效能問題。
* 修復了在通過工作流活動生成說明性報告時顯示不正確百分比的問題。 (NEO-14314)
* 在 **在交貨期間排除重複地址** 選項。 (NEO-13240)
* 修正執行&#x200B;**擴充**&#x200B;活動時，工作流程可能失敗的問題。(NEO-17338)
* 修正了從外部資料庫擷取記錄並將記錄插入 Campaign 資料庫時，所發生的工作流程問題。(NEO-26359)
* 修正了在清除運算式剖析器時，防止記憶體損毀所造成的伺服器當機問題。
* 已修復阻止 **無空** 函式從升級到build 9032後在Oracle資料庫中工作。 (NEO-26488)
* 修正了當編輯行銷活動範本說明，在複製貼上像是日文字元等符號時，無法顯示&#x200B;**「儲存」**&#x200B;按鈕的問題。(NEO-27071)
* 修正了無法儲存行銷活動說明或行銷活動範本的問題，其發生於在按一下&#x200B;**「儲存」**&#x200B;按鈕前按了視窗外部。(NEO-27449)
* 修正了在代理配置層級，導致您無法在更新到最新 Windows 10 後登入 Adobe Campaign 的問題。(NEO-27813)
* 修復了與日誌檔案中空行的管理相關的問題，導致MTA進程行為失敗，並導致傳遞發送時效能下降。

**技術演變**

已將 Tomcat 從第 7 版 (7.0.103) 更新為第 8 版 (8.5.57)。已將`tomcat-7`目錄取代為`tomcat-8`目錄。在 windows 上，現在可將 _iis_neolane_setup.vbs_ 和 _apache_neolane.conf_ 安裝在目錄`conf`中（而非上一個`tomcat-7/conf`）。在 linux 上，現在可將 _apache_neolane.conf_ 安裝在`conf`目錄中。

在Linux上，nlserver服務啟動現在使用系統單元，而不是/etc/init.d/nlserver6指令碼。 在安裝19.1.8軟體包時，會自動執行到新啟動方案的遷移。 /etc/init.d/nlserver6仍然提供，但是為了與nlserver服務（啟動、重新啟動、停止等）交互，建議您直接使用systemctl命令。


### ![](assets/do-not-localize/red_2.png)版本 19.1.7 - 版本編號 9036 {#release-19-1-7-build-9036}

_2020年9月15日_

**功能改進**

* 針對Apache 2.4線程使用的nlsrvmod改進了nlsrvmod，以修復nlsrvmod崩潰。
* 在Azure外部帳戶和SSL加密中使用「檔案傳輸」活動時，已修復問題。 連接是通過HTTP而不是HTTPS執行的。 (NEO-26720)
* 修復了未檢索標籤或類別的url快取機制問題。
* 修正了導致在電子郵件傳送中錯誤定義鏡像頁面 URL（因為 ASCII 字元控制不當）的問題。(NEO-26084)
* catalina.properties 中的 jarToSkip 清單已更新，而可刪除對不再使用的 jar 檔案的參照（iOS 通知）。
* 修復了在放置後發佈後阻止的回歸問題。
* 已修復帶有出廠預裝交貨報告的回歸，該報告在導出到PDF時似乎被截斷。 (NEO-25757)
* 修正了從追蹤 URL 重新導向時，刪除編碼參數值的問題（會影響日文字元）。(NEO-25637)
* 修正了造成個人化網域中未簽署的連結在允許時遭到封鎖的問題。(NEO-25210)
* 修正了影響工作流程中計算欄位的迴歸，導致工作流程失敗。(NEO-25194)
* 修復了與MicrosoftDynamics（版本8.2）的相容性問題，該問題可能會阻止某些API調用執行(RetrieveAllEntities)。 (NEO-24528)
* 修正了使用 ACS 連接器功能時，無法連線至 Campaign Standard 執行個體（FOH/FOH2 連線管理錯誤）的迴歸問題。(NEO-23433)
* 修正了資料庫連線上的迴歸問題，造成 Web 伺服器因資料庫編碼問題而持續重新啟動。這可能導致過度耗用。(NEO-23264)
* 修正了資料庫清除工作流程因非受管理資料來源而可能失敗的問題。(NEO-23160、NEO-23364)
* 清除工作流程現在會依 100 的批次清除過期清單，而非逐一清除。
* 在切換至新序列 ID 機制後，所有更新收件者表格的 Web 應用程式都會在升級後期間重新發佈。
* 修復了在HTML內容標籤外部存在Javascript代碼時阻止發送電子郵件的問題。 (NEO-18628)
* 已修復阻止事務性消息跟蹤指示符由跟蹤工作流更新的問題。 (NEO-17770)
* 改進了資料庫更新嚮導的效能，使SQL陳述式數減少，以優化響應時間。
* 修復了在取消檢查電子郵件中跟蹤的URL時可能發生的控制台崩潰問題 **文本內容** 頁籤。 (NEO-13545)
* 修復了因未初始化變數(m_pCurlReader)而無法使用Azure Blob儲存外部帳戶在檔案傳輸活動中上載檔案的問題。 (NEO-13717)
* 修正了在重新發佈 Web 應用程式之前，關閉 Apache 和 Web 伺服器的升級後問題。(NEO-27155)
* 已修復在中設定時間時導致選取錯誤時區的回歸 **調度程式** 工作流活動。


### ![](assets/do-not-localize/red_2.png)版本 19.1.6 - 版本編號 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>此版本僅用於內部安裝。 對於混合部署，托管實例將繼續運行9032內部版本。 不要將營銷實例升級到9035版本，因為它與9032不相容。

_2019年10月3日_

**功能改進**

* 修正了為 Salesforce 而使用 CRM 連接器所產生的問題。(NEO-17712)
* 修正了正在傳送異動訊息時，可能導致效能問題的索引問題。
* 已修復發送消息時的效能問題。 (NEO-17558)
* 已修復可能導致中間採購伺服器無法處理某些消息的問題。 (NEO-12395)
* 已修復導致無法充分使用SQL資料管理活動的問題（缺少名為right的「SQL資料管理」）。

### ![](assets/do-not-localize/red_2.png)版本 19.1.5 - 版本編號 9033{#release-19-1-5-build-9033}

_2019 年 8 月 13 日_

**功能改進**

* 修復了SQL陳述式「SELECT COUNT」的問題，該語句在資料管理活動的資料抽取期間在預設資料庫而不是FDA資料庫上執行。
* 為了改進客戶基礎架構功能，SFTP代理聲明現在可在伺服器配置檔案中提供。
* 已修復崩潰問題 **添加連結表** 欄位為空 **資料載入(RDBMS)** 工作流活動。 (NEO-12213)
* 通過命令行修復了midEmitter軟體包安裝問題。
* 已添加新的身份驗證選項，以支援帶MicrosoftDynamics的AC連接器中的OAuth憑據。 (NEO-11982)
* 解決了UUID（唯一通用標識符）管理問題，導致Hive FDA的查詢和資料載入工作流活動失敗。
* 修復Oracle上的回歸，導致某些函式在放置後被視為無效。 (NEO-12759)
* 修復了導致在調度程式工作流活動中設定時間時選取的時區不正確的回歸。

### ![](assets/do-not-localize/green_2.png) 發行版本 19.1.4 - 版本編號 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4 [!DNL Gold Standard] 本中列出的版本 [頁](../../rn/using/gold-standard.md)。


### ![](assets/do-not-localize/red_2.png)版本 19.1.2 - 版本編號 9029{#release-19-1-2-build-9029}

_2019年6月21日_

**安全性改善功能**

* 為優化安全性，Java庫(Netty)已更新為最新版本(4.1.34)。 (NEO-12788)

**功能改進**

* 已修復連結到域列管理的回歸，該回歸阻止在某些配置上發送電子郵件。
* 為了提高效能，已將_operation=&quot;none&quot;屬性添加到rtEvent SOAP調用中，以避免「SELECT FOR UPDATE」請求。
* 修復了Test活動後具有出站過渡的工作流顯示問題。 (NEO-12727)
* 現在，我們允許在導入工作流期間刪除在MicrosoftDynamics中建立的虛擬記錄。
* 使用內部帳戶時改進了執行安全區域包的權限。


### ![](assets/do-not-localize/red_2.png)版本 19.1 - 版本編號 9026{#release-19-1-build-9026}

_2019年5月30日_

**有哪些新功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 控制面板<br /> </td> 
   <td> <p>為了提高作為管理員用戶的工作效率，請通過監視儲存來管理SFTP伺服器的設定，將IP地址添加到允許清單，並為每個實例安裝SSH密鑰。 請注意，自今天起，控制面板僅適用於在AWS托管的客戶(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">立即通過Experience Cloud登錄</a>)。</p> <p>如需詳細資訊，請參閱<a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant">詳細文件</a>及<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=zh-Hant">作法影片</a>。 </p><p>注：升級到最新的市場活動版本不是訪問控制面板所必需的。</p> </td> 
  </tr> 
    <tr> 
   <td> 稽核軌跡<br /> </td> 
   <td> <p>作為管理員，通過監控和管理在Adobe Campaign Classic實例內所做的更改來提高生產效率。 審核跟蹤將記錄在源架構、工作流和選項上執行的操作。 您可以快速查看是否已建立、修改或刪除元素。</p><p>有關詳細資訊，請參閱 <a href="../../production/using/audit-trail.md">詳細文檔</a> 和 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">如何錄制視頻</a>。</p></td> 
  </tr> 
  <tr> 
   <td> 護欄、穩健性和可擴充性<br /> </td> 
   <td> 在Campaign Classic方面增加了一系列改進。 下面列出了護欄、魯棒性和可擴充性改進。<br /> </td> 
  </tr> 
  <tr> 
   <td> 相容性矩陣更新<br /> </td> 
   <td> 通過此新版本，Adobe Campaign現在支援以下資料庫系統。 請參閱 <a href="https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html">相容性清單</a>。<br /> 
    <ul> 
     <li> <p>Oracle18c</p> </li> 
     <li> <p>MySQL 5.7(FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata16</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 出於安全原因，在使用 **[!UICONTROL Pre-process the file]** 的 **[!UICONTROL Data loading (file)]** 工作流活動。 現在可以使用下拉清單，您可以從3個選項中選擇： **[!UICONTROL None]**。 **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg) 已添加XtkSecurity_Disable_Preproc安全標誌。 對於新客戶，此選項將設定為0。 對於現有客戶，此選項將按策略級設定為1以保留先前的行為。 請參閱本[章節](../../workflow/using/data-loading--file-.md)。
* 修復了測試未設定時區的FDA外部帳戶連接時出現的密碼可見性問題。
* 已刪除PDFBox庫。
* Tomcat已更新為7.0.93版。
* 修復了當安全令牌無效時發生的令牌可見性問題。
* 已修復WSDL JSP(schemawsdl.jsp)中潛在的XTK注入問題。
* 應用程式的原始碼和記憶體中的憑據和密碼儲存已優化。
* 已優化PII視圖限制。 (NEO-12339、NEO-12396、NEO-12398、NEO-12339、NEO-12667)
* 解決了密鑰管理中的不一致問題。
* 現在，對於使用有效或無效用戶名的失敗登錄嘗試，將顯示相同的常規錯誤。
* 已增強上載檔案的命名。
* 已添加一個新的XtkSecurity_Disable_GetSetEnv選項，以阻止使用setEnv和getEnv函式。
* 敏感資訊現在隱藏在應用程式堆棧跟蹤中。

**護欄、魯棒性和可擴充性改進**

* 生命週期 — XtkNewId序列使用優化：最耗用的表已從xtkNewId序列移動到專用序列。
* FDA over HTTP v2 :FDA over HTTP協定廣泛用於混合部署，特別是用於broadLog檢索和傳遞準備。 增強了魯棒性，以避免在檢索或推送資料時出現網路問題和可能的錯誤。 這要求連接兩端的內部版本是最新的，否則仍將使用舊協定。
* 跟蹤工作流：提高了跟蹤工作流的魯棒性。 已解決與跟蹤日誌插入/更新和URL跟蹤自定義相關的幾個問題。 此外，跟蹤工作流現在會檢測可能導致錯誤並停止工作流的跟蹤日誌問題。 這些問題現在被丟棄，而未處理。
* 清除工作流：已對清理工作流進行了改進，以避免潛在錯誤和停止。 這可優化資料庫大小和效能。
* 事務性消息中嵌入的影像：我們已在事務性消息中添加了對嵌入式映像的完全支援，以避免可能的崩潰或丟失映像。
* 資料庫大小 — XtkJobLog:已將清除機制添加到此表。 這對資料庫大小有積極影響。
* 密件抄送存檔：BCC存檔的預設參數已更改，以提高存檔速度。 [深入了解](../../installation/using/email-archiving.md#parameters)
* 資料庫結構更新：資料庫結構更新嚮導生成的SQL請求已得到改進，以加快執行速度。
* 操作員操作的護欄：已實施若干護欄，以防止操作員執行可能影響平台完整性的操作。 無法再通過介面刪除內置架構。 此外，非管理員用戶無法再編輯工作流源XML。
* 已提供兩個新選項： **XtkSecurity_Restrict_EditXML** （允許您禁用交貨的XML代碼版本）和 **NmsOperation_OperationMgtDebug** （允許您監視操作管理技術工作流執行）。 [閱讀全文](../../installation/using/configuring-campaign-options.md)

**其他變更**

* 推送通知：現在，我們支援「線程ID」(Thread ID)選項，用於iOS推送。
* 改進了長名稱索引的管理，這可能導致錯位問題。
* 現在，在分析反編譯傳遞時，如果發佈模式設定為 **[!UICONTROL None]** 在部署嚮導中，記錄了錯誤並停止了分析：&quot;發佈模式設定為&#39;none&#39;:無法嵌入影像。 影像不會顯示在功能電話上。」 (NEO-12208)
* 事務消息傳送的廣播管理已得到改進。 當廣播從執行實例同步到控制實例時，@lastModified欄位將更新到系統的當前日期。 已為控制實例添加MC_Update_BlLastModified選項。 True表示當前日期將用於控制實例（預設行為）。 False表示我們使用執行實例broadlog的@lastModified日期。 (NEO-12579)
* 已在優惠券臨時表中添加索引，以優化交付發送。 (NEO-12437)
* 在分析整合中，現在允AAM許檢索帶%字元的段資料。 (NEO-12025)
* 已刪除工作流熱度映射中的10,000條記錄限制以修復丟失的資料問題。 (NEO-12329)
* 不支援Open Office，現在已從應用程式中完全刪除。 如果你還在使用它，請轉到「自由辦公室」，因為從19.1開始，它將不再工作。
* 現在，您可以使用sysfilter屬性限制對工作流中更新資料活動的寫入權限。 [閱讀全文](../../configuration/using/filtering-schemas.md)

**修補程式**

* 已修復阻止為iOS移動推送通知上載證書的問題。
* 為事務推式通知修復了潛在的週期性伺服器崩潰。 其他崩潰問題已經解決。
* 修復了導致用戶活動與未結交付指標跟蹤報告之間報告差異的問題。 (NEO-11742)
* 解決了IMS登錄問題。
* 修復了在從庫中添加影像時可能導致傳遞中丟失影像的問題。 (NEO-11900)
* 修復了在直接郵件傳遞中提取優惠詳細資訊時可能出現的問題。 (NEO-11700)
* 已修復可能影響SMS事務性消息效能的問題。 (NEO-9812)
* 已修復當將外部檔案中的「定義」選項用於傳遞的主要目標時可能發生的控制台崩潰。 (NEO-12349)
* 分析以日文(.JP)域為目標的收件人的郵件時，已修復問題。 (NEO-12246)
* 使用帶有1:N連結的值分佈時，解決了顯示問題。 (NEO-12212、NEO-11820)
* 修復了在錯誤升級後可能導致MTA日誌中NmsMxDomain錯誤的問題。 (NEO-12752)
* 在濃縮工作流活動中使用「保留主集中的所有其他資料」選項時，已修復問題。 (NEO-13291)
* 使用HTTP2發送推送通知時，已修復Tomcat崩潰問題。 (NEO-12701)
* 修復了HTTPRequest API的問題，該API未等待所有回調完成。 (NEO-12628)
* 解決了事務性消息跟蹤指示符的計算過程的問題。 (NEO-12529)
* 解決了在服務管理中使用主題的問題。 (NEO-11804)
* 已解決發送推送通知時的效能問題。 (NEO-11787)
* 在提供管理中預覽出站XML或CSV檔案以直接郵件傳遞時，已解決問題。 (NEO-11290)
* 已修復安裝時的問題 **管理社交網路** （社會營銷）包。 (NEO-12081)
* 修復了一個問題，即使您擁有正確的訪問權限，也無法刪除Web應用程式。 (NEO-12072)
* 修復了一個問題，在導出並通過XML導入對象時，可能會覆蓋某些值。 已添加XtkExport_IncludeDefaultValues選項。 如果設定為True（預設行為），則會導出所有值。 設定為False時，修改將被預設值覆蓋。 (NEO-11979)
* 已修復導致 **[!UICONTROL Alert]** 在查詢後添加富集活動時工作流活動失敗。 (NEO-12132)
* 修復了Oracle設定問題，其中管線（觸發器）偏移未從資料庫成功檢索，導致重複。 (NEO-12121)
* 已修復在使用分析整合時可能導致透視表中顯示錯誤的問題(NEO-12103)
* 已使用「說明性分析」報表修復問題。 (NEO-11414)
* 當遠程表名稱中包含帶下划線的欄位時，解決了CRM連接器的問題。
* 已修復可能導致假設報告中貨幣符號顯示問題的問題。 (NEO-11634)
* 在跟蹤連結中使用某些字元時，已解決重定向和跟蹤問題。
* 已修復導致提供預覽無法正確工作的問題。
* 修復了未從地址表中刪除軟邊界的問題。
* 使用條形碼時修復了JAVA錯誤。
* 已修復Web應用程式中的翻譯問題(NEO-12460)
* 已修復s3「檔案傳輸」工作流活動的問題。 (NEO-12473)
* 已修復Web應用程式中日期欄位的問題。 (NEO-12496)
* 在交貨中使用種子地址時已修復ID耗盡問題。 (NEO-11842)
* 已解決phantomjs和Debian 9相容性問題。
* 批准證明內容時已修復錯誤。 (NEO-12725)
* 使用「從填充中排除此子集」工作流功能解決了問題。 (NEO-12441)
* 修復了HTTPRequest-wait API的問題，該API未等待所有回調完成。 (NEO-12628)
* 在拆分活動中修復了「更新共用受眾」任務的問題。 (NEO-11562)
* 已修復Web伺服器崩潰問題。 (NEO-12904)
* 已修復事務模板中的「自然」參數問題。 (NEO-12334)
* 在電子郵件文本編輯器中顯示跟蹤的URL時，已修復控制台崩潰問題。 (NEO-13122)
* 從Audience Manager導入訪問群體時，已修復「拆分檔案」活動的問題。 (NEO-11550)
* 已修復導致熱按一下報告錯誤的問題。 (NEO-11459)
* 解決了提供呈現的問題。 (NEO-11565)
* 從Audience Manager導入訪問群體時，已修復「清單更新」活動的問題。 (NEO-11226)
* 解決了「計畫」活動和時區配置問題。 (NEO-11662)
* 已修復導致跟蹤工作流在URL格式錯誤時失敗的問題。
* 在導入移動應用程式套件後解決了外部帳戶的問題。
* 將時區分配給運算子時，已修復問題。 (NEO-12464)
* 已修復可能導致mtachild日誌錯誤的問題。 (NEO-11539、NEO-8978)
* 在已保存的報表中按一下「歷史記錄」表徵圖時修復了問題。 (NEO-11620)
* 在報表中編輯透視表時修復了問題。 (NEO-12068)
