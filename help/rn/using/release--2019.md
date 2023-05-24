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

* 修正了由於實作SSL憑證而導致的回歸問題，該問題導致使用者在Windows伺服器上的連線失敗。 (NEO-20629)
* 修正「 」中顯示錯誤版本標籤編號的問題。 **關於** 功能表。


### ![](assets/do-not-localize/red_2.png)版本 19.2 - 版本編號 9080 {#release-19-2-build-9080}

_2019 年 12 月 2 日_

**有哪些新功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>加州消費者隱私法(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA是加州的新隱私權法律，協調資料保護要求並以現代化方式加以規範，自2020年1月1日起生效。 CCPA適用於所持有資料的主體居住於加州的Adobe Campaign客戶。</p>
    <p>除了現有的隱私權功能（包括同意管理、資料保留設定和使用者角色）之外，Adobe Campaign還可協助您為CCPA做好準備：</p>
    <ul>
      <li>存取權與刪除權：我們妥善運用針對GDPR新增的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">深入了解</a></li>
      <li>您可以追蹤消費者是否已選擇退出個人資訊銷售。 為此，您需要擴充「設定檔」表格並新增 <strong>選擇退出CCPA</strong> 欄位。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">深入了解</a></li></td> 
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
   <td> <p>您現在可以使用預先定義的檢視來監視執行個體上所有工作流程的執行狀態。</p>
   <p>如需詳細資訊，請參閱<a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">詳細文件</a>以瞭解詳情。</p></td> 
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
<td> <p>Adobe Campaign可讓您試用全新的互動式 <a href="https://amp.dev/about/email/">電子郵件AMP</a> format ，此模式可讓行銷人員在訊息中加入AMP元件，以利用豐富、動態和互動式內容提升電子郵件體驗，並直接在訊息中轉化為實際行動。</p>
   <p>此功能已發佈公開測試版。</p>
   <p>如需詳細資訊，請參閱<a href="../../delivery/using/defining-interactive-content.md">詳細文件</a>及<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">教學影片</a>。</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>安全的SMS傳訊(TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>現已透過Extended Generic SMPP Connector支援安全的SMS。 這允許加密連線到提供者。</p> <p><strong>警告</strong> 此功能需要所有伺服器上的最新憑證。 無效、撤銷或過期的憑證將會產生錯誤，影響整體SMS傳送功能。</p><p>如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/sms-connector-protocol-and-settings.html">詳細文件</a>以瞭解詳情。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 修正Campaign介面中儲存的跨網站指令碼弱點 — 輸入資料驗證和輸出編碼。 (NEO-16810)
* 修正了透過強化登入限制原則而允許存取未授權資料的設定檔授權安全性問題。 (NEO-14445)

**功能改進**

* 推播通知的記憶體消耗最佳化。
* 針對效能與儲存最佳化，處理 **logins.log** 檔案已增強。 檔案現在會分割成多個檔案，每天一個檔案，最多可保留365個檔案。 [深入了解](../../production/using/log-files.md)
* 現在可以使用密碼認證（密碼+使用者名稱）或憑證（私密金鑰）來設定Microsoft Dynamics CRM外部帳戶。 [深入了解](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* hadoop FDA聯結器已新增一些增強功能，以提高可靠性
* 已新增特定護欄，以在允許上傳伺服器上的公用資源之前檢查磁碟空間。
* 新增 [行銷活動選項](../../installation/using/configuring-campaign-options.md) 已新增：
   * 此 **WdbcKillSessionPolicy** 設定選項可讓您影響 **無條件停止** 所有工作流程和PostgreSQL資料庫查詢的行為。
   * 此 **NmsOperation_DeliveryPreparationWindow** 選項可讓您定義天數，超過該天數，狀態不一致的傳送將從執行中的傳送計數中排除。
   * 此 **WdbcOptions_TempDbName** 選項可讓您為Microsoft SQL Server上的工作表格設定個別的資料庫。 如此可最佳化備份與復寫。 [深入了解](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * 此 **XtkCleanup_NoStats** 已增強PostgreSQL的選項，以更好地控制資料庫清理工作流程之儲存最佳化步驟的行為。 [深入了解](../../production/using/database-cleanup-workflow.md#statistics-update)
* 帳戶鎖定機制已新增至 **logon()** API。 它可防止在指定時間範圍內連續嘗試登入失敗的特定次數後再次嘗試登入。
* 新 **個人化執行時間上限** 傳遞屬性中的選項可讓您定義個人化執行時間的逾時期間，以防止個人化階段執行太久。 [深入了解](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 此 **ftp通訊協定** 已新增選項，可讓您使用Proxy設定進行SFTP連線。 [深入了解](../../installation/using/file-res-management.md)
* 針對內部部署環境，新支援對SFTP外部伺服器的Proxy存取。
* 已新增特定護欄，以防止安裝與Campaign執行個體不相容的套件。 [深入了解](../../installation/using/installing-campaign-standard-packages.md)

_已棄用的系統_

下列系統現在是 [已棄用](deprecated-features.md) 對於Campaign Classic實作：
* Apache 2.2
* Centos 6

請確保您使用最新Campaign相容性對照表中列出的任何系統的支援版本。 [深入了解](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

iOS SDK的組建版本1.0.26現已可用。 在這個新的組建中，我們新增了iOS 13的支援。 這個新版本現在支援iOS 13推播通知的通知優先順序和新的註冊權杖管理程式。 如果您在舊版SDK上執行應用程式，則需要使用新的SDK重新編譯應用程式。 若要取得SDK，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**修補程式**

* 已修正以下情況下的當機問題： **新增連結的表格** 中的欄位為空白 **資料載入(RDBMS)** 工作流程活動。 (NEO-12213)
* 修正可能導致中間來源伺服器未處理某些訊息的問題。 (NEO-12395)
* 修正搭配Teradata使用查詢分段選項時，資料庫清理工作流程中的問題。 (NEO-12399)
* 已修正影響使用包括ne.jp網域在內的型別規則的傳遞分析的問題。 (NEO-12609)
* 修正SMS更新TLS後隱含較嚴格憑證原則的問題。 若憑證過期，這些更新可能會導致行銷與中間來源伺服器之間的連線失敗。 (NEO-17698)
* 修正使用時發生的問題 **測試連線** 使用儲存庫驗證的中間來源環境中的外部帳戶上的按鈕。 (NEO-12722)
* 修正搭配FDAHadoop連線使用日期函式的查詢問題。 (NEO-12847)
* 修正在電子郵件編輯器中取代影像時的問題。 (NEO-13098)
* 針對已刪除或移至其他位置的資料夾，修正可能導致升級後錯誤的問題。 (NEO-13118)
* 修正使用時影像顯示的問題 **定義每個裝置熒幕大小的影像** 選項線上訊息。 (NEO-13228)
* 修正以下情況下的傳遞準備問題： **傳遞期間排除重複的地址** 選項未選取。 (NEO-13240)
* 修正工作流程中使用時的問題 **檔案傳輸** 使用下載檔案的活動 **傳輸後刪除來源檔案** 選項，名稱中包含空白字元。 (NEO-13411)
* 修正Tomcat快取清理可能導致記憶體問題的問題。 (NEO-13456)
* 修正安裝時發生的問題 **透過執行例項控制優惠方案引擎** 在Microsoft SQL 2017中執行的現有控制執行個體上的內建套件。 (NEO-13539)
* 修正取消核取電子郵件中追蹤的URL時，可能發生的主控台當機問題。 **文字內容** 索引標籤中。 (NEO-13545)
* 修正中文寄件者名稱的編碼問題。 (NEO-13837)
* 修正從總管顯示調查回應資料時可能引發的錯誤。 (NEO-14590)
* 修正可能導致傳遞記錄分類與隔離表格不一致的問題。 (NEO-16547)
* 修正DKIM金鑰未內嵌在電子郵件中的問題。 (NEO-16804)
* 修正在API呼叫的內容中使用無效工作階段權杖來觸發事件時，顯示錯誤錯誤錯誤錯誤程式碼的問題。 錯誤碼是&#39;HTTP 200 OK&#39;而不是&#39;HTTP 403 Forbidden&#39;。 (NEO-16826)
* 修正透過網頁存取顯示傳遞報告時的問題。 (NEO-17015)
* 修正登入Adobe Campaign時的IMS驗證問題。 (NEO-17312)
* 修正隱私權管理程式無法刪除隔離電子郵件的問題。 (NEO-17314)
* 修正使用SQL資料庫升級至9031後的輸送量問題。 (NEO-17558)
* 修正影響CRM Connector with Salesforce的問題。 (NEO-17712)
* 修正從外部SFTP匯入資料時的逾時問題。 (NEO-19723)
* 修正存取預測模型時的問題。 (NEO-19713)
* 修正中影響隨機抽樣的問題 **Split** hadoopFDA資料庫的工作流程活動。 (NEO-16636)
* 修正Oracle的回歸，某些函式在升級後後會被視為無效。 (NEO-12759)


## 第 19.1 發行版本{#release-19-1}

### ![](assets/do-not-localize/limited_2.png)版本 19.1.8 - 版本編號 9039 {#release-19-1-8-build-9039}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)
* 修正了可能封鎖將工作流程資料匯出至FDA資料庫(Teradata、Snowflake)的回歸。

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
> * 如果您透過 oAuth 驗證使用 Experience Cloud 觸發程式整合，您必須依照[本頁](../../integrations/using/configuring-adobe-io.md)所述移至 Adobe I/O。**2021 年 9 月**[已淘汰](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)具有 Campaign 的舊版 oAuth 驗證模式。 託管環境繼續使用延伸功能，直到 **2022 年 2 月 23 日**。若為內部部署或混合客戶，請聯絡Adobe客戶服務，將支援延長至2022年2月。 您必須向 Adobe 提供 [OAuth 應用程式的 AppID](../../integrations/using/configuring-pipeline.md#step-optional)。



**功能改進**

* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 已變更原本以oAUTH驗證設定為基礎而用於存取管道的觸發器整合驗證，並將其移動至Adobe I/O。 [瞭解更多](../../integrations/using/configuring-adobe-io.md)
* 在 iOS APN 舊版二進位通訊協定支援結束之後，在升級後期間，使用此通訊協定的所有執行個體都會更新為 HTTP/2 通訊協定。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)
* 修正在連線錯誤後停用SMPP聯結器、無法傳送其他SMS傳遞並導致效能問題的問題。
* 修正透過工作流程活動產生描述性報告時顯示錯誤百分比的問題。 (NEO-14314)
* 修正以下情況下的傳遞準備問題： **傳遞期間排除重複的地址** 選項未選取。 (NEO-13240)
* 修正執行&#x200B;**擴充**&#x200B;活動時，工作流程可能失敗的問題。(NEO-17338)
* 修正了從外部資料庫擷取記錄並將記錄插入 Campaign 資料庫時，所發生的工作流程問題。(NEO-26359)
* 修正了在清除運算式剖析器時，防止記憶體損毀所造成的伺服器當機問題。
* 已修正導致無法 **NoNull** 升級至建置9032後，可在Oracle資料庫中運作的函式。 (NEO-26488)
* 修正了當編輯行銷活動範本說明，在複製貼上像是日文字元等符號時，無法顯示&#x200B;**「儲存」**&#x200B;按鈕的問題。(NEO-27071)
* 修正了無法儲存行銷活動說明或行銷活動範本的問題，其發生於在按一下&#x200B;**「儲存」**&#x200B;按鈕前按了視窗外部。(NEO-27449)
* 修正了在代理配置層級，導致您無法在更新到最新 Windows 10 後登入 Adobe Campaign 的問題。(NEO-27813)
* 修正與管理記錄檔中的空白行相關的問題，其會導致MTA程式行為失敗，並導致傳送作業的效能下降。

**技術演變**

已將 Tomcat 從第 7 版 (7.0.103) 更新為第 8 版 (8.5.57)。已將`tomcat-7`目錄取代為`tomcat-8`目錄。在 windows 上，現在可將 _iis_neolane_setup.vbs_ 和 _apache_neolane.conf_ 安裝在目錄`conf`中（而非上一個`tomcat-7/conf`）。在 linux 上，現在可將 _apache_neolane.conf_ 安裝在`conf`目錄中。

在Linux上， nlserver服務啟動現在會使用系統單元，而不是/etc/init.d/nlserver6指令碼。 安裝19.1.8套件時，會自動移轉至新的啟動配置。 仍提供/etc/init.d/nlserver6，但若與nlserver服務（啟動、重新啟動、停止等）互動，建議您直接使用systemctl命令。


### ![](assets/do-not-localize/red_2.png)版本 19.1.7 - 版本編號 9036 {#release-19-1-7-build-9036}

_2020年9月15日_

**功能改進**

* 改善Apache 2.4執行緒的nlsrvmod使用方式，以修正nlsrvmod當機。
* 修正搭配Azure外部帳戶和SSL加密使用檔案傳輸活動的問題。 連線是透過HTTP而非HTTPS執行的。 (NEO-26720)
* 修正URL快取機制未擷取標籤或類別的問題。
* 修正了導致在電子郵件傳送中錯誤定義鏡像頁面 URL（因為 ASCII 字元控制不當）的問題。(NEO-26084)
* catalina.properties 中的 jarToSkip 清單已更新，而可刪除對不再使用的 jar 檔案的參照（iOS 通知）。
* 修正了升級後發佈後無法解決的回歸問題。
* 修正現成可用的傳遞報告回歸，在匯出至PDF時似乎遭到截斷。 (NEO-25757)
* 修正了從追蹤 URL 重新導向時，刪除編碼參數值的問題（會影響日文字元）。(NEO-25637)
* 修正了造成個人化網域中未簽署的連結在允許時遭到封鎖的問題。(NEO-25210)
* 修正了影響工作流程中計算欄位的迴歸，導致工作流程失敗。(NEO-25194)
* 修正Microsoft Dynamics （8.2版）相容性問題，此問題可能會阻止某些API呼叫執行(RetrieveAllEntities)。 (NEO-24528)
* 修正了使用 ACS 連接器功能時，無法連線至 Campaign Standard 執行個體（FOH/FOH2 連線管理錯誤）的迴歸問題。(NEO-23433)
* 修正了資料庫連線上的迴歸問題，造成 Web 伺服器因資料庫編碼問題而持續重新啟動。這可能導致過度耗用。(NEO-23264)
* 修正了資料庫清除工作流程因非受管理資料來源而可能失敗的問題。(NEO-23160、NEO-23364)
* 清除工作流程現在會依 100 的批次清除過期清單，而非逐一清除。
* 在切換至新序列 ID 機制後，所有更新收件者表格的 Web 應用程式都會在升級後期間重新發佈。
* 修正當HTML內容標籤以外有Javascript程式碼時，無法傳送電子郵件的問題。 (NEO-18628)
* 修正追蹤工作流程無法更新交易式訊息追蹤指標的問題。 (NEO-17770)
* 已改善資料庫更新精靈的效能，以減少SQL敘述句，進而最佳化回應時間。
* 修正取消核取電子郵件中追蹤的URL時，可能發生的主控台當機問題。 **文字內容** 索引標籤中。 (NEO-13545)
* 修正由於未初始化的變數(m_pCurlReader)，導致您無法使用Azure Blob儲存外部帳戶在檔案傳輸活動中上傳檔案的問題。 (NEO-13717)
* 修正了在重新發佈 Web 應用程式之前，關閉 Apache 和 Web 伺服器的升級後問題。(NEO-27155)
* 修正了在中設定時間時，導致擷取到錯誤時區的回歸 **排程器** 工作流程活動。


### ![](assets/do-not-localize/red_2.png)版本 19.1.6 - 版本編號 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>此組建版本僅供內部部署使用。 對於混合部署，託管例項將繼續執行9032版本編號。 請勿將您的行銷執行個體升級至9035版本編號，因為它與9032不相容。

_2019年10月3日_

**功能改進**

* 修正了為 Salesforce 而使用 CRM 連接器所產生的問題。(NEO-17712)
* 修正了正在傳送異動訊息時，可能導致效能問題的索引問題。
* 修正傳送訊息時的效能問題。 (NEO-17558)
* 修正可能導致中間來源伺服器未處理某些訊息的問題。 (NEO-12395)
* 修正無法完整使用SQL資料管理活動的問題（遺失名為許可權的「SQL資料管理」）。

### ![](assets/do-not-localize/red_2.png)版本 19.1.5 - 版本編號 9033{#release-19-1-5-build-9033}

_2019 年 8 月 13 日_

**功能改進**

* 修正在資料管理活動的資料擷取期間，在預設資料庫而非FDA資料庫上執行的SQL陳述式「SELECT COUNT」的問題。
* 為了改善客戶基礎結構功能，現在可在伺服器設定檔案中使用SFTP Proxy宣告。
* 已修正以下情況下的當機問題： **新增連結的表格** 中的欄位為空白 **資料載入(RDBMS)** 工作流程活動。 (NEO-12213)
* 已透過命令列修正midEmitter套件安裝的問題。
* 已新增驗證選項，以透過Microsoft Dynamics支援AC聯結器中的OAuth憑證。 (NEO-11982)
* 修正UUID （唯一通用識別碼）管理導致Hive FDA的查詢和資料載入工作流程活動失敗的問題。
* 修正Oracle的回歸，某些函式在升級後後會被視為無效。 (NEO-12759)
* 修正了在「排程器」工作流程活動中設定時間時，導致擷取到錯誤時區的回歸。

### ![](assets/do-not-localize/green_2.png) 發行版本 19.1.4 - 版本編號 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4 [!DNL Gold Standard] 此版本中列出發行版本 [頁面](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png)版本 19.1.2 - 版本編號 9029{#release-19-1-2-build-9029}

_2019年6月21_

**安全性改善功能**

* 為了最佳化安全性，Java程式庫(Netty)已更新至最新版本(4.1.34)。 (NEO-12788)

**功能改進**

* 修正連結至網域欄管理的回歸，該回歸阻止在特定設定上傳送電子郵件。
* 為了提高效能，已將_operation=&quot;none&quot;屬性新增至rtEvent SOAP呼叫，以避免&quot;SELECT FOR UPDATE&quot;請求。
* 修正測試活動後傳出轉變的工作流程顯示問題。 (NEO-12727)
* 我們現在允許在匯入工作流程期間刪除Microsoft Dynamics中建立的虛擬記錄。
* 改善使用內部帳戶時執行安全性區域套件的許可權。


### ![](assets/do-not-localize/red_2.png)版本 19.1 - 版本編號 9026{#release-19-1-build-9026}

_2019年5月30_

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
   <td> <p>若要提高身為管理員使用者的工作效率，請監控儲存空間、將IP位址新增至允許清單，以及為每個執行個體安裝SSH金鑰，以管理SFTP伺服器的設定。 請注意，「控制面板」目前僅適用於AWS上代管的客戶(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">今天透過Experience Cloud登入</a>)。</p> <p>如需詳細資訊，請參閱<a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant">詳細文件</a>及<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=zh-Hant">作法影片</a>。 </p><p>注意：存取「控制面板」並不需要升級至最新的Campaign版本編號。</p> </td> 
  </tr> 
    <tr> 
   <td> 稽核軌跡<br /> </td> 
   <td> <p>以管理員的身分，監控及管理Adobe Campaign Classic執行個體中所做的變更，以提高生產力。 稽核軌跡會記錄對來源結構描述、工作流程和選項所做的動作。 您可以快速檢視元素是否已建立、修改或刪除。</p><p>如需詳細資訊，請參閱 <a href="../../production/using/audit-trail.md">詳細檔案</a> 和 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">操作說明影片</a>.</p></td> 
  </tr> 
  <tr> 
   <td> 護欄、健全性與可擴充性<br /> </td> 
   <td> Campaign Classic已新增一系列改善專案。 以下列出防護措施、健全性和可擴充性改善專案。<br /> </td> 
  </tr> 
  <tr> 
   <td> 相容性對照表更新<br /> </td> 
   <td> 透過此新版本，Adobe Campaign現在支援下列資料庫系統。 請參閱 <a href="https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html">相容性對照表</a>.<br /> 
    <ul> 
     <li> <p>oracle18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>teradata16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 基於安全考量，您在使用時，無法再插入任意命令 **[!UICONTROL Pre-process the file]** 中的選項 **[!UICONTROL Data loading (file)]** 工作流程活動。 您現在可以使用下拉式清單，從3個選項中進行選取： **[!UICONTROL None]**， **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg)。 已新增XtkSecurity_Disable_Preproc安全性旗標。 若為新客戶，此選項將設為0。 對於現有客戶，升級後此選項將設為1以保留之前的行為。 請參閱本[章節](../../workflow/using/data-loading--file-.md)。
* 修正測試FDA外部帳戶（未設定時區）的連線時，所發生的密碼可見性問題。
* 已移除PDFBox資料庫。
* Tomcat已更新至7.0.93版。
* 修正安全性權杖無效時發生的權杖可見性問題。
* 修正WSDL JSP (schemawsdl.jsp)中潛在的XTK插入問題。
* 應用程式原始程式碼和記憶體中的認證和密碼儲存已最佳化。
* 已最佳化PII檢視限制。 (NEO-12339， NEO-12396， NEO-12398， NEO-12339， NEO-12667)
* 修正秘密金鑰管理中的不一致問題。
* 使用有效或無效的使用者名稱嘗試登入失敗時，現在會顯示相同的一般錯誤。
* 已增強上傳檔案的命名。
* 已新增新的XtkSecurity_Disable_GetSetEnv選項，以封鎖setEnv和getEnv函式的使用。
* 敏感資訊現在隱藏在應用程式棧疊追蹤中。

**護欄、健全性與可擴充性改善**

* 有效期限 — XtkNewId序列使用方式最佳化：最耗用的表格已從xtkNewId序列移至專用序列。
* FDA over HTTP v2： FDA over HTTP通訊協定廣泛用於混合部署，特別是用於broadLog擷取和傳送準備。 健全性已增強，以避免擷取或推送資料時發生網路問題和可能的錯誤。 這要求連線兩端的組建都是最新的，否則仍會使用舊通訊協定。
* 追蹤工作流程：已增強追蹤工作流程的健全性。 已修正幾個與追蹤記錄插入/更新和URL追蹤自訂相關的問題。 此外，追蹤工作流程現在會偵測可能導致錯誤的追蹤記錄問題，並停止工作流程。 這些問題現在會被捨棄且不會處理。
* 清理工作流程：已改善清理工作流程，以避免潛在的錯誤和停止。 如此可最佳化資料庫大小和效能。
* 交易式訊息中的內嵌影像：我們已在交易式訊息中新增完整的內嵌影像支援，以避免可能的當機或遺失影像。
* 資料庫大小 — XtkJobLog：此表格已新增清除機制。 這對資料庫大小有正面影響。
* BCC封存： BCC封存的預設引數已變更，以提高封存速度。 [深入了解](../../installation/using/email-archiving.md#parameters)
* 資料庫結構更新：已改善資料庫結構更新精靈產生的SQL要求，以加快執行。
* 操作員動作的護欄：已實作數個護欄，以防止操作員執行可能影響平台完整性的動作。 無法再透過介面刪除內建方案。 此外，非管理員使用者無法再編輯工作流程來源XML。
* 提供兩個新選項： **XtkSecurity_Restrict_EditXML** （可讓您停用傳遞的XML程式碼版本）及 **NmsOperation_OperationMgtDebug** （可讓您監視operationMgt技術工作流程執行）。 [閱讀全文](../../installation/using/configuring-campaign-options.md)

**其他變更**

* 推播通知：我們現在支援iOS推播的「執行緒ID」選項。
* 改善可能導致升級後問題的長名稱索引管理。
* 現在，在分析分解傳遞期間，如果發佈模式設為 **[!UICONTROL None]** 部署精靈中會記錄錯誤並停止分析：「發佈模式設為&#39;none&#39;：無法內嵌影像。 影像不會顯示在功能電話上。」 (NEO-12208)
* 已改善異動訊息的broadlog管理。 當broadlog從執行例項同步到控制例項時，@lastModified欄位會更新為系統的目前日期。 已針對控制例證新增MC_Update_BlLastModified選項。 True表示控制例項將使用目前日期（預設行為）。 False表示我們使用執行例項broadlog的@lastModified行日期。 (NEO-12579)
* 在優惠券臨時表格中新增了索引，以最佳化傳送傳遞。 (NEO-12437)
* 在Analytics整合中，現在允許擷取含有%字元的AAM區段資料。 (NEO-12025)
* 已移除「工作流程熱度圖」中的10,000筆記錄限制，以修正遺失資料的問題。 (NEO-12329)
* 不支援Open Office，現在已從應用程式中完全移除。 如果您仍在使用它，請移至Libre Office，因為從19.1版開始將無法再使用。
* 您現在可以使用sysfilter屬性來限制「工作流程」中「更新」資料活動的寫入許可權。 [閱讀全文](../../configuration/using/filtering-schemas.md)

**修補程式**

* 修正無法為iOS行動推播通知上傳憑證的問題。
* 修正異動推播通知可能一再發生的伺服器當機問題。 其他當機問題已修正。
* 修正造成使用者活動與未完成傳遞指標追蹤報告之間報告不一致的問題。 (NEO-11742)
* 修正IMS登入的問題。
* 修正從資料庫新增影像時，可能導致傳送中遺失影像的問題。 (NEO-11900)
* 修正在直接郵件傳遞中擷取優惠方案詳細資料時可能發生的問題。 (NEO-11700)
* 修正可能影響SMS交易式訊息效能的問題。 (NEO-9812)
* 修正針對傳送的主要目標使用「在外部檔案中定義」選項時可能發生的主控台當機問題。 (NEO-12349)
* 修正分析以日文(.JP)網域為目標的收件者時所發生的問題。 (NEO-12246)
* 修正搭配1：N連結使用值分佈時的顯示問題。 (NEO-12212、NEO-11820)
* 修正了在升級後可能導致MTA記錄中出現NmsMxDomain錯誤的問題。 (NEO-12752)
* 修正在擴充工作流程活動中使用「保留主要集的所有其他資料」選項的問題。 (NEO-13291)
* 修正使用HTTP2傳送推播通知時的Tomcat當機問題。 (NEO-12701)
* 修正HTTPRequest API未等待所有回呼完成的問題。 (NEO-12628)
* 修正交易式訊息追蹤指標的計算程式問題。 (NEO-12529)
* 已修正Offer Management中使用主題的問題。 (NEO-11804)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正在Offer Management中預覽直接郵件傳遞的傳出XML或CSV檔案時的問題。 (NEO-11290)
* 修正安裝時發生的問題 **管理社交網路** （社交行銷）套件。 (NEO-12081)
* 修正即使您擁有正確的存取許可權，仍無法刪除Web應用程式的問題。 (NEO-12072)
* 修正在匯出然後透過XML匯入物件時，可能會導致某些值被覆寫的問題。 已新增XtkExport_IncludeDefaultValues選項。 設定為True （預設行為）時，會匯出所有值。 設定為False時，會以預設值覆寫修改。 (NEO-11979)
* 修正導致下列專案的問題： **[!UICONTROL Alert]** 在查詢後新增擴充活動時的工作流程活動失敗。 (NEO-12132)
* 修正Oracle設定中，未從資料庫成功擷取管道（觸發器）位移而導致重複的問題。 (NEO-12121)
* 修正使用Analytics整合時，可能導致樞紐分析表顯示錯誤的問題(NEO-12103)
* 修正描述性分析報表的問題。 (NEO-11414)
* 修正遠端表格名稱含有底線欄位時，CRM聯結器發生的問題。
* 修正可能導致「假設」報告中貨幣符號顯示問題的問題。 (NEO-11634)
* 修正在追蹤連結中使用特定字元時的重新導向和追蹤問題。
* 修正無法正確預覽選件的問題。
* 修正未從位址表格移除軟退信的問題。
* 修正使用條碼時的JAVA錯誤。
* 修正網站應用程式中的翻譯問題(NEO-12460)
* 修正s3檔案傳輸工作流程活動的問題。 (NEO-12473)
* 修正網站應用程式中日期欄位的問題。 (NEO-12496)
* 修正在傳送中使用種子地址時，ID用盡的問題。 (NEO-11842)
* 修正phantomjs和Debian 9相容性的問題。
* 修正核准校樣內容時的錯誤。 (NEO-12725)
* 修正「從母體排除此子集」工作流程功能的問題。 (NEO-12441)
* 修正HTTPRequest-wait API未等待所有回呼完成的問題。 (NEO-12628)
* 修正分割活動中的「更新共用對象」任務的問題。 (NEO-11562)
* 修正Web伺服器當機問題。 (NEO-12904)
* 修正異動範本中Nature引數的問題。 (NEO-12334)
* 修正在電子郵件文字編輯器中顯示追蹤的URL時，主控台當機問題。 (NEO-13122)
* 修正從Audience Manager匯入對象時，「分割檔案」活動的問題。 (NEO-11550)
* 修正造成熱門點選報告發生錯誤的問題。 (NEO-11459)
* 修正優惠方案呈現的問題。 (NEO-11565)
* 修正從Audience Manager匯入對象時，清單更新活動的問題。 (NEO-11226)
* 修正排程活動和時區設定的問題。 (NEO-11662)
* 已修正造成URL格式錯誤時追蹤工作流程失敗的問題。
* 修正匯入行動應用程式套件後外部帳戶的問題。
* 修正將時區指派給運運算元的問題。 (NEO-12464)
* 修正可能導致配對記錄中發生錯誤的問題。 (NEO-11539、NEO-8978)
* 修正按一下已儲存報表中的「歷程記錄」圖示的問題。 (NEO-11620)
* 修正在報表中編輯樞紐分析表時的問題。 (NEO-12068)
