---
solution: Campaign Classic
product: campaign
title: 第 19.2 發行版本
description: 第 19.2 發行版本
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: b5b9e42eca25193cf4d69f654e74a02afd8adca9
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 14%

---


# 第 19.2 發行版本{#release-19-2}

## ![](assets/do-not-localize/limited_2.png) 版本 19.2.4 - Build 9082 {#release-19-2-4-build-9082}

_2020 年 12 月 23 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在&#x200B;**2021 年 3 月 31 日後連線至 Campaign。**
>
> * 此版本隨附於[安全性修正](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：升級是強化環境安全的必備條件。



* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)

## ![](assets/do-not-localize/red_2.png) 版本 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_2020年2月07日_

**功能改善**

* 修正因實施SSL認證而導致使用者連線在Windows伺服器上失敗的回歸問題。 (NEO-20629)
* 修正在&#x200B;**關於**&#x200B;功能表中顯示錯誤版本標籤號碼的問題。

## ![](assets/do-not-localize/red_2.png) 版本 19.2 - Build 9080 {#release-19-2-build-9080}

_2019年12月2日_

**新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> <strong>加州消費者隱私法(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA是加州新推出的隱私權法，協調並現代化資料保護要求，將於2020年1月1日生效。 CCPA適用於持有居住在加州之資料主體資料的Adobe Campaign客戶。</p>
    <p>除了現有的隱私權功能（包括許可管理、資料保留設定和使用者角色）外，Adobe Campaign還可協助您做好CCPA的準備：</p>
    <ul>
      <li>存取權與刪除權：我們運用了為GDPR新增的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">顯示全文</a></li>
      <li>您可以追蹤消費者是否已選擇退出個人資訊的銷售。 為此，您需要擴展「配置式」表並添加<strong>CCPA</strong>欄位。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">顯示全文</a></li></td> 
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
   <p>如需詳細資訊，請參閱<a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">相關的文件</a>，以瞭解詳情。</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>使用AMP製作互動式內容</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign可讓您試用新的互動式<a href="https://amp.dev/about/email/">AMP for Email</a>格式，讓行銷人員在訊息中加入AMP元件，以利用豐富、動態和互動式內容來增強電子郵件體驗，並直接在訊息中採取行動。</p>
   <p>此功能會以公開測試版發佈。</p>
   <p>如需詳細資訊，請參閱<a href="../../delivery/using/defining-interactive-content.md">詳細文件</a>及<a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">教學影片</a>。</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>安全的SMS訊息(TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>安全SMS現在通過擴展通用SMPP連接器受支援。 這允許與提供程式的加密連接。</p> <p><strong>警</strong> 告：這項功能要求所有伺服器都有最新憑證。無效、已撤銷或已過期的憑證會產生影響整體SMS傳送功能的錯誤。</p><p>如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/sms-connector-protocol-and-settings.html">相關的文件</a>，以瞭解詳情。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 修正Campaign介面中儲存的跨網站指令碼弱點——輸入資料驗證和輸出編碼。 (NEO-16810)
* 修正描述檔授權的安全性問題，此問題可能允許存取未經授權的資料，方法是加強登入限制原則。 (NEO-14445)

**功能改善**

* 推播通知的記憶體耗用最佳化。
* 對於效能和儲存優化，**logins.log**&#x200B;檔案的處理已增強。 檔案現在會分割為多個檔案，每天一個，最多可保留365個檔案。 [顯示全文](../../production/using/log-files.md)
* Microsoft Dynamics CRM外部帳戶現在可使用密碼憑證（密碼+使用者名稱）或憑證（私密金鑰）來設定。 [顯示全文](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Hadoop FDA連接器已新增一些增強功能，以提升可靠性
* 在允許上傳伺服器上的公共資源之前，已添加了一個特定的保護欄來檢查磁碟空間。
* 已新增[促銷活動選項](../../installation/using/configuring-campaign-options.md):
   * **WdbcKillSessionPolicy**&#x200B;配置選項允許您在所有工作流和PostgreSQL資料庫查詢上影響&#x200B;**無條件停止**&#x200B;行為。
   * **NmsOperation_DeliveryPreparationWindow**&#x200B;選項允許您定義超過天數，在超過天數後，狀態不一致的交貨將被排除在運行交貨的計數之外。
   * **WdbcOptions_TempDbName**&#x200B;選項允許您為Microsoft SQL Server上的工作表配置單獨的資料庫。 這樣可以優化備份和複製。 [顯示全文](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * PostgreSQL的&#x200B;**XtkCleanup_NoStats**&#x200B;選項已增強，可更好地控制資料庫清理工作流的儲存優化步驟的行為。 [顯示全文](../../production/using/database-cleanup-workflow.md#statistics-update)
* 帳戶鎖定機制已添加到&#x200B;**logon()** API。 它可防止在指定時間範圍內連續嘗試若干次登入失敗後，再進行任何登入嘗試。
* 傳送屬性中新的&#x200B;**最大個人化執行時間**&#x200B;選項可讓您定義個人化執行時間的逾時期，以防止個人化階段執行太長。 [顯示全文](../../delivery/using/personalization-fields.md#timing-out-personalization)
* **ftp通訊協定**&#x200B;選項已新增，可讓您使用SFTP連線的代理設定。 [顯示全文](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* 針對內部部署環境，新支援對SFTP外部伺服器的Proxy存取。
* 已新增特定保護欄，以防止安裝與促銷活動例項不相容的套件。 [顯示全文](../../installation/using/installing-campaign-standard-packages.md)

_不建議使用的系統_

下列系統現在[不建議使用](https://helpx.adobe.com/tw/campaign/kb/deprecated-and-removed-features.html)，適用於Campaign Classic實作：
* Apache 2.2
* Centos 6

請確定您使用最新「促銷活動相容性」表所列任何系統的支援版本。 [顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

iOS SDK的組建版本1.0.26現已推出。 在這個新版本中，我們新增了iOS 13的支援。 這個新版本現在支援iOS 13推播通知的通知優先順序和新的註冊Token管理程式。 如果您正在舊版SDK上執行應用程式，則需要使用新的SDK重新編譯應用程式。 若要取得SDK，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**修補程式**

* 修正&#x200B;**資料載入(RDBMS)**&#x200B;工作流程活動中，**新增連結的表格**&#x200B;欄位空白的當機問題。 (NEO-12213)
* 修正Mid-Sourcing伺服器無法處理某些訊息的問題。 (NEO-12395)
* 修正搭配Teradata使用查詢色帶選項時，資料庫清除工作流程中的問題。 (NEO-12399)
* 修正影響含有ne.jp網域之類型規則之傳送分析的問題。 (NEO-12609)
* 修正TLS更新的SMS相關問題，此問題暗示憑證政策限制較嚴格。 這些更新可能導致行銷和中部採購伺服器之間發生連線失敗，以備憑證過期時使用。 (NEO-17698)
* 修正在具有Vault驗證的中部採購環境中，在外部帳戶上使用&#x200B;**Test connection**&#x200B;按鈕的問題。 (NEO-12722)
* 修正使用FDA Hadoop連線之日期函式的查詢問題。 (NEO-12847)
* 已修正在電子郵件編輯器中取代影像的問題。 (NEO-13098)
* 已修正可能導致已刪除或移至其他位置的檔案夾發生升級後錯誤的問題。 (NEO-13118)
* 修正在LINE訊息上使用&#x200B;**「依裝置螢幕大小定義影像」選項時，影像顯示的問題。**(NEO-13228)
* 修正未選取「在傳送期間排除重複位址」選項時的傳送準備問題。 ****(NEO-13240)
* 修正使用&#x200B;**檔案傳輸**&#x200B;活動使用&#x200B;**傳輸**&#x200B;後刪除來源檔案選項（名稱包含空格字元）下載檔案時，工作流程中的問題。 (NEO-13411)
* 修正Tomcat快取清除可能導致記憶體問題的問題。 (NEO-13456)
* 修正在Microsoft SQL 2017中執行的現有控制例項上安裝&#x200B;**Control of of offer engine with execution instance** built-in套件的問題。 (NEO-13539)
* 修正由於未初始化變數，從&#x200B;**Text content**&#x200B;標籤取消勾選電子郵件中追蹤的URL時，可能發生的主控台當機問題。 (NEO-13545)
* 修正中文傳送者名稱的編碼問題。 (NEO-13837)
* 修正從「檔案總管」顯示調查回應資料時可能會引發的錯誤。 (NEO-14590)
* 修正可能導致傳送記錄分類與隔離表格不一致的問題。 (NEO-16547)
* 修正未內嵌至電子郵件的DKIM金鑰問題。 (NEO-16804)
* 修正在API呼叫中使用無效作業Token來觸發事件時，顯示錯誤錯誤錯誤代碼的問題。 錯誤代碼是&#39;HTTP 200 OK&#39;，而不是&#39;HTTP 403 Forbidden&#39;。 (NEO-16826)
* 修正透過Web存取顯示傳送報表的問題。 (NEO-17015)
* 已修正登入Adobe Campaign時的IMS驗證問題。 (NEO-17312)
* 修正「隱私權管理」程式無法刪除隔離電子郵件的問題。 (NEO-17314)
* 修正使用SQL資料庫升級至9031後的總處理能力問題。 (NEO-17558)
* 修正影響Salesforce CRM連接器的問題。 (NEO-17712)
* 修正從外部SFTP匯入資料時的逾時問題。 (NEO-19723)
* 修正存取預測性模型時的問題。 (NEO-19713)
* 修正影響&#x200B;**Split**&#x200B;工作流程活動與Hadoop FDA資料庫的隨機取樣的問題。 (NEO-16636)
* 修正Oracle上的回歸，導致部分函式在發佈後被視為無效。 (NEO-12759)


