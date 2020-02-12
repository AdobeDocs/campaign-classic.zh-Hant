---
title: 最新版本
description: Campaign Classic 19.2發行說明
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 37946a63a0cd0312de31b26dd4d115895d959638

---


# 最新版本{#latest-release}

[建立升級](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) |控 [制面板版本](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) |文 [件更新](../../rn/using/documentation-updates.md) |舊 [版](../../rn/using/release--19-1.md) |已過 [時的功能](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>一般可用性</strong></td>
   <td><img src="assets/blue3.png"/><strong>發行候選人</strong></td> 
   <td><img src="assets/orange3.png"/><strong>不再提供</strong></td> 
   <td><img src="assets/red3.png"/><strong>已過時</strong></td> 
  </tr> 
   <tr> 
   <td>提供最新的穩定版本。 <br>在生產環境中經過驗證。 </td>
   <td>經Adobe驗證的建置。 <br>等待生產校對。 </td>
   <td>更新的版本已修正錯誤。 <br>需要更新。 </td>
   <td>包含已知的回歸。 <br>更新是必備的。 </td>
  </tr> 
 </tbody> 
</table>

單 [擊此處](../../rn/using/release--19-1.md#release-19-1-4-build-9032) ，查看上 **一個穩定構建** (GA)。

## ![](assets/orange2.png) 版本19.2.3 - Build 9081 {#release-19-2-2-build-9081}

2020年2月07日_

**改進**

* 修正因實施SSL認證而導致使用者連線在Windows伺服器上失敗的回歸問題。 (NEO-20629)
* 修正「關於」功能表中顯示錯誤版本標 **簽** 。

## ![](assets/orange2.png) 版本19.2 - Build 9080 {#release-19-2-build-9080}

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
   <td> <p>CCPA是加州新推出的隱私權法，協調並現代化將於2020年1月1日生效的資料保護要求。 CCPA適用於持有居住在加州之資料主體資料的Adobe Campaign客戶。</p>
    <p>除了現有的隱私權功能（包括許可管理、資料保留設定和使用者角色）外，Adobe Campaign還可協助您做好CCPA的準備：</p>
    <ul>
      <li>存取權與刪除權：我們運用了為GDPR新增的功能。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">閱讀更多資訊</a></li>
      <li>您可以追蹤消費者是否已選擇退出個人資訊的銷售。 為此，您需要擴展「配置式」表並添加「 <strong>退出CCPA」欄位</strong> 。 <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">閱讀更多資訊</a></li></td> 
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
   <p>如需詳細資訊，請參閱詳 <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">細檔案</a>。</p></td> 
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
<td> <p>Adobe Campaign可讓您試用新的互動式 <a href="https://amp.dev/about/email/">AMP for Email</a> （電子郵件格式），讓行銷人員在訊息中加入AMP元件，以利用豐富、動態和互動式內容來增強電子郵件體驗，並直接在訊息中採取行動。</p>
   <p>此功能會以公開測試版發佈。</p>
   <p>如需詳細資訊，請參閱詳細 <a href="../../delivery/using/defining-interactive-content.md">的檔案</a> ，以及 <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">教學影片</a>。</p><br /></td> 
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
<td> <p>安全SMS現在通過擴展通用SMPP連接器受支援。 這允許與提供程式的加密連接。</p> <p><strong>警告</strong> ：此功能要求所有伺服器上都有最新的憑證。 無效、已撤銷或已過期的憑證會產生影響整體SMS傳送功能的錯誤。</p><p>如需詳細資訊，請參閱詳 <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html">細檔案</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 修正Campaign介面中儲存的跨網站指令碼弱點——輸入資料驗證和輸出編碼。 (NEO-16810)
* 修正描述檔授權的安全性問題，此問題可能允許存取未經授權的資料，方法是加強登入限制原則。 (NEO-14445)

**改進**

* 推播通知的記憶體耗用最佳化。
* 為達到效能和儲存空間最佳化， **已增強logins.log** 檔案的處理。 檔案現在會分割為多個檔案，每天一個，最多可保留365個檔案。 [閱讀更多資訊](../../production/using/log-files.md)
* Microsoft Dynamics CRM外部帳戶現在可使用密碼憑證（密碼+使用者名稱）或憑證（私密金鑰）來設定。 [閱讀更多資訊](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Hadoop FDA連接器已新增一些增強功能，以提升可靠性
* 在允許上傳伺服器上的公共資源之前，已添加了一個特定的保護欄來檢查磁碟空間。
* 已新 [增促銷活動](../../installation/using/configuring-campaign-options.md) 選項：
   * 使用 **WdbcKillSessionPolicy** 配置選項，可以影響所有工作流和PostgreSQL資料庫查詢上的「無條件停止 **** 」行為。
   * 使 **用NmsOperation_DeliveryPreparationWindow** 選項，可以定義在運行交貨計數中排除狀態不一致交貨的天數。
   * 使 **用WdbcOptions_TempDbName** 選項，可以為Microsoft SQL server上的工作表配置單獨的資料庫。 這樣可以優化備份和複製。 [閱讀更多資訊](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * PostgreSQL **的XtkCleanup_NoStats** 選項已增強，可更好地控制資料庫清理工作流中儲存優化步驟的行為。 [閱讀更多資訊](../../production/using/database-cleanup-workflow.md#statistics-update)
* 帳戶鎖定機制已新增至 **logon()** API。 它可防止在指定時間範圍內連續嘗試若干次登入失敗後，再進行任何登入嘗試。
* 傳送屬 **性中新的「最大個人化執行時間** 」選項可讓您定義個人化執行時間的逾時期，以防止個人化階段執行太長。 [閱讀更多資訊](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 已 **新增ftp通訊協定** 選項，可讓您使用SFTP連線的Proxy設定。 [閱讀更多資訊](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* 針對內部部署環境，新支援對SFTP外部伺服器的Proxy存取。
* 已新增特定保護欄，以防止安裝與促銷活動例項不相容的套件。 [閱讀更多資訊](../../installation/using/installing-campaign-standard-packages.md)

_不建議使用的系統_

Campaign Classic實作現在不 [再使用](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) 下列系統：
* Apache 2.2
* Centos 6

請確定您使用最新「促銷活動相容性」表所列任何系統的支援版本。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

iOS SDK的組建版本1.0.26現已推出。 在這個新版本中，我們新增了iOS 13的支援。 這個新版本現在支援iOS 13推播通知的通知優先順序和新的註冊Token管理程式。 如果您正在舊版SDK上執行應用程式，則需要使用新的SDK重新編譯應用程式。 若要取得SDK，請聯絡Adobe客戶服務。

**修補程式**

* 修正在「資料載入(RDBMS)」工作流程活動中新增空連結表 **格時可能發生的控制台當機** 。 (NEO-12213)
* 修正Mid-Sourcing伺服器無法處理某些訊息的問題。 (NEO-12395)
* 修正搭配Teradata使用查詢色帶選項時，資料庫清除工作流程中的問題。 (NEO-12399)
* 修正影響含有ne.jp網域之類型規則之傳送分析的問題。 (NEO-12609)
* 修正TLS更新的SMS相關問題，此問題暗示憑證政策限制較嚴格。 這些更新可能導致行銷和中部採購伺服器之間發生連線失敗，以備憑證過期時使用。 (NEO-17698)
* 修正在具有Vault驗證的中 **部採購環境中，在外部帳戶上使用** 「測試連線」按鈕的問題。 (NEO-12722)
* 修正使用FDA Hadoop連線之日期函式的查詢問題。 (NEO-12847)
* 已修正在電子郵件編輯器中取代影像的問題。 (NEO-13098)
* 已修正可能導致已刪除或移至其他位置的檔案夾發生升級後錯誤的問題。 (NEO-13118)
* 修正在LINE訊息上使用「依裝置螢幕大小定 **義影像」選項時** ，影像顯示的問題。 (NEO-13228)
* 修正取消選取「在傳送期間排除重複 **位址」選項時的傳送準備** 問題。 (NEO-13240)
* 修正使用檔案傳輸活動使用 **Delete the source files after transfer****** （名稱包含空格字元）選項下載檔案時，在工作流程中的問題。 (NEO-13411)
* 修正Tomcat快取清除可能導致記憶體問題的問題。 (NEO-13456)
* 修正在Microsoft SQL 2017中執行的現有控制例項上，安裝 **Control of offer engine with execution instance** built-in package時的問題。 (NEO-13539)
* 修正從「文字內容」標籤取消勾選電子郵件中追蹤的URL時，可能發生的主控 **台當機** 。 (NEO-13545)
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
* 修正影響Hadoop FDA資料庫 **Split** workflow活動中隨機取樣的問題。 (NEO-16636)

