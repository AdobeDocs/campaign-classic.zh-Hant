---
product: campaign
title: 第 20.2 發行版本
description: 第 20.2 發行版本
feature: 概覽
role: User
level: Beginner
exl-id: fcaab1aa-c8f9-4606-b0d8-eb481a38f588
source-git-commit: 550c4afc5cc77867b56d17565bef3f18b1df12a2
workflow-type: tm+mt
source-wordcount: '3008'
ht-degree: 87%

---

# 第 20.2 發行版本{#release-20-2}

## ![](assets/do-not-localize/limited_2.png) 發行版本 20.2.5 - 版本編號 9188 {#release-20-2-5-build-9188}

_2021年 4 月 15 日_

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2021年 3 月 31 日_

**功能改善**

* 已進行改善，以防止無效soap呼叫上當機。 這可能會導致執行個體在嘗試執行特定複雜查詢時停止運作。 （NEO-28796、NEO-30553）
* 修正了因主機名稱驗證而無法傳送具有TLS之SMS傳送的回歸。 (NEO-29581)
* 修正已簽署的追蹤連結無法用於某些電子郵件用戶端的問題。 （NEO-28414、NEO-29615）
* 修正了使用webApp追蹤標籤時，可能會與重複ID產生衝突的追蹤ID序列。 (NEO-27931)
* 修正導致每日wfserver重新啟動停止執行工作流程的問題。 (NEO-30047)
* 修正了在非管理員使用者嘗試同步 Adobe Experience Manager 範本時，使用 API 調用的安全性問題。（NEO-32389、NEO-23487）
* 修正在透過範本建立的傳送上，關閉傳送對話方塊時，造成主控台當機的問題。 (NEO-31547)
* 修正在促銷活動的&#x200B;**目標與工作流程**&#x200B;標籤內建立和儲存傳送時發生的問題：預覽會失敗，並出現下列錯誤。(NEO-29440)
* 修正Tomcat 8.5傳送無效答案，而導致「交易式傳訊」記錄檔發生錯誤的問題。 (NEO-30858)
* 修正了導致外部執行緒管理中記憶體損毀並影響效能的回歸問題。
* 修正使用自訂目標對應時，帳單工作流程可能失敗的問題。 自訂架構的主索引鍵儲存在「sourceId」欄中，該欄僅允許整數值。 它現在允許整數和字串值。 （NEO-25914、NEO-28146）
* 修正迴歸，防止在傳遞中使用主控台的某些元件，例如日期選擇器和影像管理。 (NEO-31453)

## ![](assets/do-not-localize/red_2.png) 發行版本 20.2.4 - 版本編號 9187 {#release-20-2-4-build-9187}

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
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在 **2021 年 6 月 30 日**&#x200B;後與 Campaign 連線。[深入瞭解](../../technotes/ims-updates.md)
> * 此版本隨附[安全性修正](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。
> * 如果您透過 oAuth 驗證使用 Experience Cloud 觸發程式整合，您必須依照[本頁](../../integrations/using/configuring-adobe-io.md)所述移至 Adobe I/O。**2021年8月18日**&#x200B;已淘汰具有Campaign [的舊版oAuth驗證模式](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 托管環境可從延伸功能中獲益，直到2021年11月30日&#x200B;**。**&#x200B;身為內部部署或混合客戶，請聯絡Adobe客戶服務，將支援延長至2021年11月30日。 您必須提供[OAuth應用程式](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)的AppID以Adobe。


**功能改善**

* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 已變更原本以oAUTH驗證設定為基礎而用於存取管道的觸發器整合驗證，並將其移至Adobe I/O。 [了解更多](../../integrations/using/configuring-adobe-io.md)
* [在 iOS APN 舊版二進位通訊協定支援結束之後，在升級後期間，](https://developer.apple.com/news/?id=c88acm2b)使用此通訊協定的所有執行個體都會更新為 HTTP/2 通訊協定。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)
* 修正了在連線錯誤後導致SMPP連接器停用、無法傳送其他SMS傳遞並導致效能問題的問題。 (NEO-28609)
* 修正了在清除運算式剖析器時，防止記憶體損毀所造成的伺服器當機問題。(NEO-26856)
* 修正了在工作流程&#x200B;**「分割」**&#x200B;活動中顯示目標資料餘數時，而造成伺服器當機的問題。
* 修正了嘗試在查詢後預覽 SMS 訊息時，除&#x200B;**收件者** (nms:recipient) 以外的其他方案可能會顯示錯誤訊息的問題。(NEO-27517)
* 修正了在主機名稱中明確定義埠號的HTTPS連線要求時，呼叫因憑證錯誤而失敗的問題。 (NEO-29146)
* 修正了POSIX執行緒管理中，在行銷執行個體上產生大型核心轉儲檔案的問題。 （NEO-28117、NEO-29281）
* 修正準備傳送或重複傳送預覽時，Web程式可能當機的問題。 （NEO-27790、NEO-27517）
* 修正由非管理員運算子觸發時，傳送或校樣傳送失敗的問題。 (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **新控制面板 10 月發行版本**，其中包含使用 CNAME 的網域設定及新的資料庫監控功能。[進一步瞭解](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=zh-Hant)。

## ![](assets/do-not-localize/red_2.png) 發行版本 20.2.3 - 版本編號 9182 {#release-20-2-3-build-9182}

_2020 年 9 月 11 日_

* 修正了由於傳送組件上單一錯誤功能導致記憶體過載，導致傳送準備遭到封鎖的迴歸。(NEO-27346)
* 修正了在重新發佈 Web 應用程式之前，關閉 Apache 和 Web 伺服器的升級後問題。(NEO-27155)
* 修正了 HTML 範本管理上的迴歸，導致追蹤 URL 因索引錯誤表示而變得可見。(NEO-25909)
* 修正了資料庫清除工作流程因非受管理資料來源而可能失敗的問題。(NEO-23160、NEO-23364)
* 清除工作流程現在會依 100 的批次清除過期清單，而非逐一清除。
* 修正了導致無法修改外部帳戶內部名稱的迴歸。(NEO-27323)
* 修正了升級後期間的迴歸，而導致 nlserver（錯誤記錄）錯誤啟動。
* 已改善共用記憶體的更新管理。20.2 中所需的其他步驟已不再需要。

## ![](assets/do-not-localize/red_2.png) 發行版本 20.2.2 - 版本編號 9180 {#release-20-2-2-build-9180}

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
* 在切換至[新序列 ID 機制](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)後，所有更新收件者表格的 Web 應用程式都會在升級後期間重新發佈。
* 修正了傳送內容中的潛在 XSS 弱點。(NEO-17987、NEO-26073)

![](assets/do-not-localize/cp-icon.png) **新的控制面板 6 月版本**，包含作用中設定檔監控、子網域傳遞送能力稽核及 GPG 金鑰管理。[進一步瞭解](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html)。

## ![](assets/do-not-localize/red_2.png) 發行版本 20.2.1 - 版本編號 9178 {#release-20-2-1-build-9178}

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
* 修正了更新至 9080 組建版本後，嘗試連線至 Audience Manager 時可能發生的問題。(NEO-20511、NEO-25167)
* 修正了匯出 PDF 或 XLS 格式報表時可能發生的問題。(NEO-20982、NEO-23493、NEO-23348)
* 修正了傳送傳遞後，傳遞清單可能顯示傳送兩次的問題。
* 修正了傳遞準備問題，路由設定設為透過中間來源傳送傳遞時，可能會發生此問題。
* 修正了按下在 Line 訊息內的 Web 應用程式連結時，可能顯示錯誤訊息的問題。
* 修正了執行清理工作流程後，刪除了&#x200B;**增量查詢**&#x200B;活動歷史記錄的問題。
* 修正了建立中間來源外部帳戶時，NmsMidSourcing_LastBroadLog_&lt;InternalName> 選項遺失的問題.
* 修正了資料庫連線上的迴歸問題，造成 Web 伺服器因資料庫編碼問題而持續重新啟動。這可能導致過度耗用。(NEO-23264)
