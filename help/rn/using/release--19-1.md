---
product: campaign
title: Campaign 19.1發行說明
description: Campaign 19.1發行說明
exl-id: 8540b5f0-194b-45f3-b497-5d30efb318b8
source-git-commit: 2a92cfc705e27332cfdf8c7357a6a03c84dc6c9f
workflow-type: tm+mt
source-wordcount: '3292'
ht-degree: 25%

---

# 第 19.1 發行版本{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) 發行版本 19.1.8 - 版本編號 9039 {#release-19-1-8-build-9039}

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

_2020 年 12 月 16 日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您要透過 Adobe Identity Service (IMS) 連線至 Campaign，則必須升級至 Campaign 伺服器和用戶端主控台，才能在 **2021 年 6 月 30 日**&#x200B;後與 Campaign 連線。[深入瞭解](../../technotes/ims-updates.md)
> * 此版本隨附[安全性修正](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。
> * 如果您透過 oAuth 驗證使用 Experience Cloud 觸發程式整合，您必須依照[本頁](../../integrations/using/configuring-adobe-io.md)所述移至 Adobe I/O。**2021年8月18日**&#x200B;已淘汰具有Campaign [的舊版oAuth驗證模式](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 托管環境可從延伸功能中獲益，直到2021年11月30日&#x200B;**。**&#x200B;身為內部部署或混合客戶，請聯絡Adobe客戶服務，將支援延長至2021年11月30日。 您必須提供[OAuth應用程式](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)的AppID以Adobe。



**功能改善**

* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。
* 已變更原本以oAUTH驗證設定為基礎而用於存取管道的觸發器整合驗證，並將其移至Adobe I/O。 [了解更多](../../integrations/using/configuring-adobe-io.md)
* 在 iOS APN 舊版二進位通訊協定支援結束之後，在升級後期間，使用此通訊協定的所有執行個體都會更新為 HTTP/2 通訊協定。
* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)
* 修正了在連線錯誤後導致SMPP連接器停用、無法傳送其他SMS傳遞並導致效能問題的問題。
* 修正透過工作流程活動產生描述性報表時，顯示錯誤百分比的問題。 (NEO-14314)
* 修正取消選取「在傳送期間排除重複位址&#x200B;**」選項時的傳送準備問題。**(NEO-13240)
* 修正執行&#x200B;**擴充**&#x200B;活動時，工作流程可能失敗的問題。(NEO-17338)
* 修正了從外部資料庫擷取記錄並將記錄插入 Campaign 資料庫時，所發生的工作流程問題。(NEO-26359)
* 修正了在清除運算式剖析器時，防止記憶體損毀所造成的伺服器當機問題。
* 修正了在升級至9032組建後，**NoNull**&#x200B;函式無法在Oracle資料庫中運作的問題。 (NEO-26488)
* 修正了當編輯行銷活動範本說明，在複製貼上像是日文字元等符號時，無法顯示&#x200B;**「儲存」**&#x200B;按鈕的問題。(NEO-27071)
* 修正了無法儲存行銷活動說明或行銷活動範本的問題，其發生於在按一下&#x200B;**「儲存」**&#x200B;按鈕前按了視窗外部。(NEO-27449)
* 修正了在代理配置層級，導致您無法在更新到最新 Windows 10 後登入 Adobe Campaign 的問題。(NEO-27813)
* 修正了與管理記錄檔中空行相關的問題，導致MTA處理行為失敗，並導致傳送效能下降。

**技術演變**

已將 Tomcat 從第 7 版 (7.0.103) 更新為第 8 版 (8.5.57)。已將`tomcat-7`目錄取代為`tomcat-8`目錄。在 windows 上，現在可將 _iis_neolane_setup.vbs_ 和 _apache_neolane.conf_ 安裝在目錄`conf`中（而非上一個`tomcat-7/conf`）。在 linux 上，現在可將 _apache_neolane.conf_ 安裝在`conf`目錄中。

在Linux上，nlserver服務啟動現在使用系統單元，而非/etc/init.d/nlserver6指令碼。 安裝19.1.8套件時，會自動移轉至新的啟動方案。 仍提供/etc/init.d/nlserver6，但為了與nlserver服務（啟動、重新啟動、停止等）互動，我們建議您直接使用systemctl命令。

## ![](assets/do-not-localize/red_2.png) 發行版本 19.1.7 - 版本編號 9036 {#release-19-1-7-build-9036}

_2020 年 9 月 15 日_

**功能改善**

* 改善Apache 2.4執行緒的nlsrvmod，以修正nlsrvmod當機。
* 修正搭配Azure外部帳戶和SSL加密使用檔案傳輸活動的問題。 連線是透過HTTP而非HTTPS執行。 (NEO-26720)
* 修正url快取機制未擷取標籤或類別的問題。
* 修正了導致在電子郵件傳送中錯誤定義鏡像頁面 URL（因為 ASCII 字元控制不當）的問題。(NEO-26084)
* catalina.properties 中的 jarToSkip 清單已更新，而可刪除對不再使用的 jar 檔案的參照（iOS 通知）。
* 修正了在升級後發佈後無法顯示的回歸問題。
* 修正現成可用的傳送報表回歸，在匯出為PDF時，這些報表會顯示為截斷。 (NEO-25757)
* 修正了從追蹤 URL 重新導向時，刪除編碼參數值的問題（會影響日文字元）。(NEO-25637)
* 修正了造成個人化網域中未簽署的連結在允許時遭到封鎖的問題。(NEO-25210)
* 修正了影響工作流程中計算欄位的迴歸，導致工作流程失敗。(NEO-25194)
* 修正了與Microsoft Dynamics（來自8.2版）的相容性問題，此問題可能會導致部分API呼叫無法執行(RetrieveAllEntities)。 (NEO-24528)
* 修正了使用 ACS 連接器功能時，無法連線至 Campaign Standard 執行個體（FOH/FOH2 連線管理錯誤）的迴歸問題。(NEO-23433)
* 修正了資料庫連線上的迴歸問題，造成 Web 伺服器因資料庫編碼問題而持續重新啟動。這可能導致過度耗用。(NEO-23264)
* 修正了資料庫清除工作流程因非受管理資料來源而可能失敗的問題。(NEO-23160、NEO-23364)
* 清除工作流程現在會依 100 的批次清除過期清單，而非逐一清除。
* 在切換至[新序列 ID 機制](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)後，所有更新收件者表格的 Web 應用程式都會在升級後期間重新發佈。
* 修正當HTML內容標籤外部有Javascript程式碼時，無法傳送電子郵件的問題。 (NEO-18628)
* 修正「追蹤」工作流程無法更新交易式訊息追蹤指標的問題。 (NEO-17770)
* 改進資料庫更新嚮導的效能，以減少SQL陳述式，以優化響應時間。
* 修正了由於未初始化變數，從&#x200B;**Text content**&#x200B;標籤取消勾選電子郵件中追蹤的URL時，可能發生的主控台當機問題。 (NEO-13545)
* 修正因未初始化的變數(m_pCurlReader)，您無法使用Azure Blob儲存外部帳戶上傳檔案傳輸活動中的檔案的問題。 (NEO-13717)
* 修正了在重新發佈 Web 應用程式之前，關閉 Apache 和 Web 伺服器的升級後問題。(NEO-27155)
* 修正在&#x200B;**排程器**&#x200B;工作流程活動中設定時間時，導致挑選錯誤時區的回歸。

## ![](assets/do-not-localize/red_2.png) 發行版本 19.1.6 - 版本編號 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>此版本編號僅用於內部部署安裝。 對於混合部署，托管執行個體將持續執行9032組建。 請勿將行銷執行個體升級至9035組建，因為它與9032不相容。

_2019年10月3日_

**功能改善**

* 修正了為 Salesforce 而使用 CRM 連接器所產生的問題。(NEO-17712)
* 修正了正在傳送異動訊息時，可能導致效能問題的索引問題。
* 修正傳送訊息時的效能問題。 (NEO-17558)
* 修正了可能導致Mid-Sourcing伺服器無法處理某些訊息的問題。 (NEO-12395)
* 修正了無法完全使用SQL資料管理活動的問題（缺少「SQL資料管理」的名為權限）。

## ![](assets/do-not-localize/red_2.png) 發行版本 19.1.5 - 版本編號 9033{#release-19-1-5-build-9033}

_2019 年 8 月 13 日_

**功能改善**

* 修正SQL陳述式「SELECT COUNT」的問題，此問題在「資料管理」活動的資料擷取期間，會在預設資料庫而非FDA資料庫執行。
* 為了改善客戶基礎架構功能，伺服器設定檔案中現在提供SFTP代理聲明。
* 修正&#x200B;**資料載入(RDBMS)**&#x200B;工作流程活動中，**新增連結的表格**&#x200B;欄位空白時的當機問題。 (NEO-12213)
* 修正了透過命令列安裝midEmitter套件的問題。
* 已新增驗證選項，以支援Microsoft Dynamics AC連接器內的OAuth憑證。 (NEO-11982)
* 修正UUID（唯一通用識別碼）管理的問題，此問題造成Hive FDA導致查詢和資料載入工作流程活動失敗。
* 修正Oracle上的回歸，導致在升級後後部分函式被視為無效。 (NEO-12759)
* 修正了在排程器工作流程活動中設定時間時，導致挑選錯誤時區的回歸。

## ![](assets/do-not-localize/green_2.png) 發行版本 19.1.4 - 版本編號 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>19.1.4 [!DNL Gold Standard]版本列在此[page](../../rn/using/gold-standard.md)中。


## ![](assets/do-not-localize/red_2.png) 發行版本 19.1.2 - 版本編號 9029{#release-19-1-2-build-9029}

_2019年6月21日_

**安全性增強功能**

* 為了最佳化安全性，Java庫(Netty)已更新至最新版本(4.1.34)。 (NEO-12788)

**功能改善**

* 修正連結至網域欄管理的回歸，該回歸會防止在某些設定中傳送電子郵件。
* 為了改善效能，已將_operation=&quot;none&quot;屬性新增至rtEvent SOAP呼叫，以避免「SELECT FOR UPDATE」請求。
* 修正測試活動後，外站轉變的工作流程顯示問題。 (NEO-12727)
* 現在，我們允許在匯入工作流程期間刪除在Microsoft Dynamics中建立的虛擬記錄。
* 改善使用內部帳戶時執行安全區域套件的權限。

## ![](assets/do-not-localize/red_2.png) 發行版本 19.1 - 版本編號 9026{#release-19-1-build-9026}

_2019年5月30日_

**有哪些新增功能？**

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
   <td> <p>若要提高身為管理員使用者的工作效率，請透過監控儲存空間來管理SFTP伺服器的設定、新增IP位址以允許清單，並為每個執行個體安裝SSH金鑰。 請注意，「控制面板」僅適用於目前由AWS托管的客戶(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">透過今天的Experience Cloud登入</a>)。</p> <p>如需詳細資訊，請參閱<a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant">詳細文件</a>及<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=zh-Hant">作法影片</a>。 </p><p>注意：存取「控制面板」不需要升級至最新的Campaign版本編號。</p> </td> 
  </tr> 
    <tr> 
   <td> 稽核軌跡<br /> </td> 
   <td> <p>身為管理員，監控及管理在Adobe Campaign Classic例項內進行的變更，以提高生產力。 稽核軌跡將記錄在來源結構、工作流程和選項上執行的動作。 您可以快速查看元素是否已建立、修改或刪除。</p><p>如需詳細資訊，請參閱<a href="../../production/using/audit-trail.md">詳細檔案</a>和<a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">how-to video</a>。</p></td> 
  </tr> 
  <tr> 
   <td> 防護性、健全性和可擴充性<br /> </td> 
   <td> 已新增一系列改善項目至Campaign Classic。 下面列出了防護性、健全性和可擴充性改進。<br /> </td> 
  </tr> 
  <tr> 
   <td> 相容性矩陣更新<br /> </td> 
   <td> 透過這個新版本，Adobe Campaign現在支援下列資料庫系統。 請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html">相容性矩陣</a>。<br /> 
    <ul> 
     <li> <p>Oracle18c</p> </li> 
     <li> <p>MySQL 5.7(FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata16(FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 出於安全原因，在&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;工作流活動中使用&#x200B;**[!UICONTROL Pre-process the file]**&#x200B;選項時，無法再插入任意命令。 現在提供下拉式清單，可讓您從3個選項中選取：**[!UICONTROL None]**、**[!UICONTROL Decompression]**(zcat)或&#x200B;**[!UICONTROL Decrypt]**(gpg)。 已新增XtkSecurity_Disable_Preproc安全標幟。 若為新客戶，此選項將設為0。 對於現有客戶，此選項會由升級後設為1，以保留先前的行為。 請參閱此[節](../../workflow/using/data-loading--file-.md)。
* 修正測試未設定時區之FDA外部帳戶的連線時發生的密碼可見性問題。
* 已移除PDFBox程式庫。
* 已將Tomcat更新至7.0.93版。
* 修正了安全性權杖無效時發生的權杖可見性問題。
* 修正了WSDL JSP(schemawsdl.jsp)中可能插入XTK的問題。
* 已優化應用程式原始碼和記憶體中的憑據和密碼儲存。
* PII檢視限制已最佳化。 (NEO-12339、NEO-12396、NEO-12398、NEO-12339、NEO-12667)
* 修正密鑰管理中的不一致問題。
* 現在會以有效或無效的使用者名稱，針對失敗的登入嘗試顯示相同的一般錯誤。
* 已增強上傳檔案的命名功能。
* 已新增新的XtkSecurity_Disable_GetSetEnv選項，以阻止使用setEnv和getEnv函式。
* 敏感資訊現在隱藏在應用程式堆疊追蹤中。

**防護性、健全性和可擴充性改善**

* 有效期限 — XtkNewId序列使用優化：最耗用的表格已從xtkNewId序列移至專用序列。 [顯示全文](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA over HTTP v2:fda over HTTP通訊協定廣泛用於混合部署，尤其是廣泛記錄擷取和傳送準備。 已增強健全性，以避免擷取或推送資料時出現網路問題和可能的錯誤。 這要求連線兩端的組建都為最新狀態，否則仍會使用舊通訊協定。
* 追蹤工作流程：已增強追蹤工作流程的健全性。 已修正數個與追蹤記錄插入/更新和URL追蹤自訂相關的問題。 此外，追蹤工作流程現在會偵測可能導致錯誤的追蹤記錄問題並停止工作流程。 系統現在會捨棄這些問題，且不會加以處理。
* 清除工作流程：已改善清理工作流程，以避免可能的錯誤和停止。 這樣可優化資料庫大小和效能。
* 交易式訊息中內嵌的影像：我們已新增對交易式訊息中內嵌影像的完整支援，以避免可能當機或遺失影像。
* 資料庫大小 — XtkJobLog:已將清除機制新增至此表格。 這對資料庫大小有正面影響。
* 密件副本歸檔：已變更BCC封存的預設參數，以提高封存速度。 [顯示全文](../../installation/using/email-archiving.md#parameters)
* 資料庫結構更新：資料庫結構更新嚮導生成的SQL請求已得到改進，以加快執行速度。
* 運算子動作的護欄：已實施多個護欄，以防止操作員執行可能影響平台完整性的操作。 您無法再透過介面刪除內建結構。 此外，非管理員使用者無法再編輯工作流程來源XML。
* 已提供兩個新選項：**XtkSecurity_Restrict_EditXML**（允許您禁用傳送的版本&#39; XML代碼）和&#x200B;**NmsOperation_OperationMgtDebug**（允許您監視operationMgt技術工作流執行）。 [顯示全文](../../installation/using/configuring-campaign-options.md)

**其他變更**

* 推播通知：現在，iOS推播支援「執行緒ID」選項。
* 改善了長名稱索引的管理，這可能造成升級後問題。
* 現在，在分析解壓縮傳送期間，如果在部署精靈中將發佈模式設為&#x200B;**[!UICONTROL None]**，則會記錄錯誤並停止分析：&quot;發佈模式設定為&#39;none&#39;:無法嵌入影像。 功能電話上不會顯示影像。」 (NEO-12208)
* 已針對交易式訊息改善broadlog管理。 從執行例項同步到控制例項時，@lastModified欄位會更新為系統的目前日期。 已為控制實例添加MC_Update_BlLastModified選項。 True表示將在控制例項上使用目前的日期（預設行為）。 False表示我們使用執行例項broadlog的@lastModified日期。 (NEO-12579)
* 已在抵用券臨時表格中新增索引，以最佳化傳送。 (NEO-12437)
* 在Analytics整合中，現在允許擷取包含%字元的AAM區段資料。 (NEO-12025)
* 移除「工作流程熱度圖」中的10,000筆記錄限制，以修正遺失的資料問題。 (NEO-12329)
* 不支援Open Office，現在已從應用程式中完全刪除。 如果您仍在使用它，請移至Libre Office，因為從19.1開始，它將無法再運作。
* 您現在可以使用sysfilter屬性限制對工作流中更新資料活動的寫權限。 [顯示全文](../../configuration/using/filtering-schemas.md)

**修補程式**

* 修正無法針對iOS行動推播通知上傳憑證的問題。
* 修正交易推播通知的潛在經常性伺服器當機問題。 已修正其他當機問題。
* 修正造成使用者活動與未結傳送指標的追蹤報表不一致的問題。 (NEO-11742)
* 修正IMS登入的問題。
* 修正從程式庫新增影像時，傳送中可能會遺失影像的問題。 (NEO-11900)
* 修正以直接郵件傳送擷取選件詳細資料時可能發生的問題。 (NEO-11700)
* 修正可能影響SMS交易式訊息效能的問題。 (NEO-9812)
* 修正針對傳送的主要目標使用外部檔案中的已定義選項時，可能會發生主控台當機的問題。 (NEO-12349)
* 修正分析以日文(.JP)網域的收件者為目標的訊息時的問題。 (NEO-12246)
* 修正搭配1:N連結使用值分佈時的顯示問題。 （NEO-12212、NEO-11820）
* 修正了在升級後，MTA記錄中可能會出現NmsMxDomain錯誤的問題。 (NEO-12752)
* 修正在擴充工作流程活動中使用「從主要集保留所有其他資料」選項的問題。 (NEO-13291)
* 修正了使用HTTP2傳送推播通知時，發生Tomcat當機問題。 (NEO-12701)
* 修正HTTPRequest API未等待所有回呼完成的問題。 (NEO-12628)
* 修正交易式訊息追蹤指標的運算程式問題。 (NEO-12529)
* 已修正在offer management中使用主題的問題。 (NEO-11804)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正在選件管理中預覽傳出XML或CSV檔案以傳送直接郵件時的問題。 (NEO-11290)
* 修正安裝&#x200B;**管理社交網路**（社交行銷）套件時的問題。 (NEO-12081)
* 修正即使您擁有正確的存取權限，仍無法刪除Web應用程式的問題。 (NEO-12072)
* 修正了在匯出後透過XML匯入物件時，可能會覆寫某些值的問題。 已新增XtkExport_IncludeDefaultValues選項。 設為True時（預設行為），會匯出所有值。 設為False時，會以預設值覆寫修改。 (NEO-11979)
* 修正在查詢後新增擴充活動時，造成&#x200B;**[!UICONTROL Alert]**&#x200B;工作流程活動失敗的問題。 (NEO-12132)
* 修正Oracle設定中，管道（觸發器）偏移未從資料庫成功擷取而造成重複的問題。 (NEO-12121)
* 修正使用Analytics整合時，可能導致樞紐表格顯示錯誤的問題(NEO-12103)
* 修正「描述性分析」報表的問題。 (NEO-11414)
* 修正CRM連接器的問題：遠端表格包含名稱帶有底線的欄位。
* 修正了可能導致「假設」報表中貨幣符號顯示的問題。 (NEO-11634)
* 修正在追蹤連結中使用特定字元時的重新導向與追蹤問題。
* 修正無法正確預覽選件的問題。
* 修正無法從位址表格移除軟退信的問題。
* 修正使用條碼時的JAVA錯誤。
* 修正Web應用程式的翻譯問題(NEO-12460)
* 修正s3檔案傳輸工作流程活動的問題。 (NEO-12473)
* 修正Web應用程式中日期欄位的問題。 (NEO-12496)
* 修正了在傳送中使用種子地址時，ID耗盡的問題。 (NEO-11842)
* 修正phantomjs與Debian 9相容性的問題。
* 修正核准校樣內容時的錯誤。 (NEO-12725)
* 修正「從母體中排除此子集」工作流程功能的問題。 (NEO-12441)
* 修正HTTPRequest-wait API未等待所有回呼完成的問題。 (NEO-12628)
* 修正分割活動中「更新共用對象」任務的問題。 (NEO-11562)
* 修正Web伺服器當機問題。 (NEO-12904)
* 修正交易範本中「自然」參數的問題。 (NEO-12334)
* 修正在電子郵件文字編輯器中顯示追蹤的URL時，主控台當機問題。 (NEO-13122)
* 修正從Audience Manager匯入對象時，分割檔案活動的問題。 (NEO-11550)
* 修正造成熱點點按報告錯誤的問題。 (NEO-11459)
* 修正選件呈現的問題。 (NEO-11565)
* 修正從Audience Manager匯入對象時，「清單更新」活動的問題。 (NEO-11226)
* 修正排程活動和時區設定的問題。 (NEO-11662)
* 修正了在URL格式錯誤時，追蹤工作流程失敗的問題。
* 修正匯入行動應用程式套件後的外部帳戶問題。
* 修正將時區指派給運算子時的問題。 (NEO-12464)
* 修正了可能導致母體記錄檔發生錯誤的問題。 （NEO-11539、NEO-8978）
* 修正按一下已儲存報表中「歷史記錄」圖示的問題。 (NEO-11620)
* 修正編輯報表中的樞紐表格時的問題。 (NEO-12068)
