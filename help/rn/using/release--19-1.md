---
title: 版本19.1
seo-title: 版本19.1
description: 版本19.1
seo-description: null
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
source-git-commit: ba5496a008a28a29fc8e2032f31355a7c34f3ef8

---


# 版本19.1{#release-19-1}

## 版本19.1.6 - Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>此版本僅用於內部部署安裝。 對於混合部署，代管例項將持續執行9032組建版本。 請勿將行銷實例升級至9035組建版本，因為它與9032不相容。

2019年10月3日

**改進**

* 修正使用Salesforce的CRM連接器時的問題。 (NEO-17712)
* 修正在傳送事務性訊息時，可能導致效能問題的索引問題。
* 修正傳送訊息時的效能問題。 (NEO-17558)
* 修正Mid-Sourcing伺服器無法處理某些訊息的問題。 (NEO-12395)
* 修正無法充分使用SQL資料管理活動（缺少名為右的「SQL資料管理」）的問題。

## 版本19.1.5 - Build 9033{#release-19-1-5-build-9033}

2019年8月13日

>[!CAUTION]
>
>這個建築已經召回。 請升 [級至最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或聯絡 [技術支援](https://support.neolane.net/)。

**改進**

* 修正在「資料管理」活動的「資料擷取」期間，在預設資料庫而非FDA資料庫上執行的SQL陳述式&#39;SELECT COUNT&#39;問題。
* 為改善客戶基礎架構功能，伺服器組態檔中現在提供SFTP代理宣告。
* 修正在「資料載入(RDBMS)」工作流活動中「添加連結表」時，沒有表名的客戶端控制台崩潰的問題。 (NEO-12213)
* 已修正透過命令列安裝midEmetter套件的問題。
* 已新增驗證選項，以支援使用Microsoft Dynamics的AC連接器中的OAuth認證。 (NEO-11982)
* 修正UUID（唯一通用識別碼）的問題會導致Hive FDA的擴充活動失敗。

## 版本19.1.4 - Build 9032{#release-19-1-4-build-9032}

**2019年12月17日**:新組建版本(9032-9d34fb17e)，包含下列修正：

* 修正下列通訊管道的追蹤問題：行動(SMS、MMS)、推播(iOS、Android)和社交網路(Facebook、Twitter)。
(NEO-19595)

**2019年12月11日**:新建版本(9032-e28b428b7)，包含下列修正：

>[!CAUTION]
>
>這個建築已經召回。 請升 [級至最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或聯絡 [技術支援](https://support.neolane.net/)。

* 修正了使用MSSQL資料庫發送消息時的效能問題。 (NEO-17558)

**2019年11月20日**:新建版本(9032-3468c7bb5)，包含下列修正：

>[!CAUTION]
>
>這個建築已經召回。 請升 [級至最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或聯絡 [技術支援](https://support.neolane.net/)。

* 已修正透過IMS驗證的登入問題。 (NEO-17312)
* 修正在多個傳送上顯示累積報表的問題。 (NEO-18165)
* 已修正可能會封鎖或造成Web伺服器當機的問題。

**2019年9月19日**:新建版本(9032-cee805c93)，包含下列修正：

>[!CAUTION]
>
>這個建築已經召回。 請升 [級至最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或聯絡 [技術支援](https://support.neolane.net/)。

* 修正使用Salesforce的CRM連接器時的問題。 (NEO-17712)
* 修正在傳送事務性訊息時，可能導致效能問題的索引問題。

**2019年8月13日**:初始19.1.4版本，包含下列修正：

>[!CAUTION]
>
>這個建築已經召回。 請升 [級至最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或聯絡 [技術支援](https://support.neolane.net/)。

* 修正在精靈設定期間，排程器活動產生不想要的錯誤訊息的問題。 回復NEO-11662的更新。 (NEO-17097)
* 修正NEO-12727造成的回歸，當執行兩次測試活動時，此回歸可能導致工作流程停止。 (NEO-16835)
* 修正當API呼叫中使用無效或過期的作業Token時，會傳回錯誤的HTTP程式碼（HTTP 200 OK，而非HTTP 403 Forbidden）的問題。 (NEO-16826)
* 已修正DKIM金鑰不再內嵌在電子郵件中的問題，因此造成傳遞能力問題。 (NEO-16804)
* 已修正工作流程排程的各種問題。 排程的工作流程會排程為每天執行一次，而不會考慮排程器設定。 (NEO-16619、NEO-16426)

## 版本19.1.2 - Build 9029{#release-19-1-2-build-9029}

2019年6月21日

>[!CAUTION]
>
>這個建築已經召回。 請升 [級至最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或聯絡 [技術支援](https://support.neolane.net/)。

**安全性增強功能**

* 為了最佳化安全性，Java程式庫(Netty)已更新至最新版本(4.1.34)。 (NEO-12788)

**改進**

* 修正連結至網域欄管理的回歸，使某些設定無法傳送電子郵件。
* 為了改善效能，已在rtEvent SOAP呼叫中新增_operation=&quot;none&quot;屬性，以避免「SELECT FOR UPDATE」要求。
* 修正「測試」活動後出站轉場的工作流程顯示問題。 (NEO-12727)
* 現在，我們允許在匯入工作流程期間刪除在Microsoft Dynamics中建立的虛擬記錄。
* 改進使用內部帳戶時執行安全區套件的權限。

## 版本19.1 - Build 9026{#release-19-1-build-9026}

2019年5月30日

>[!CAUTION]
>
>這個建築已經召回。 請升 [級至最新版本](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) ，或聯絡 [技術支援](https://support.neolane.net/)。

**新增功能？**

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
   <td> <p>為了提高管理員使用者的工作效率，請監控儲存空間、將IP位址列入白名單，以及為每個例項安裝SSH金鑰，以管理SFTP伺服器的設定。 請注意，控制面板僅適用於當天AWS托管的客戶(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">今天透過Experience cloud登入</a>)。</p> <p>如需詳細資訊，請參 <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">閱詳細說明</a><a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">檔案和操作視訊</a>。 </p><p>注意：升級至最新的促銷活動組建版本並不需要存取控制面板。</p> </td> 
  </tr> 
    <tr> 
   <td> 稽核記錄<br /> </td> 
   <td> <p>身為管理員，透過監控和管理在Adobe Campaign Classic例項中所做的變更，提高生產力。 審計線索將記錄對源方案、工作流和選項執行的操作。 您可以快速查看元素是否已建立、修改或刪除。</p><p>如需詳細資訊，請參閱詳 <a href="../../production/using/audit-trail.md">細檔案</a><a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">和操作說明影片</a>。</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail、強穩性與可擴充性<br /> </td> 
   <td> Campaign Classic已新增一系列改良功能。 下面列出了增強的護欄、魯棒性和可擴充性。<br /> </td> 
  </tr> 
  <tr> 
   <td> 相容性矩陣更新<br /> </td> 
   <td> 有了這個新版本，Adobe Campaign現在支援下列資料庫系統。 請參閱「 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Compatibility Matrix</a>」。<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7(FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16(FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 出於安全原因，在工作流活動中使用該選項時，您不 **[!UICONTROL Pre-process the file]** 能再插入任 **[!UICONTROL Data loading (file)]** 意命令。 現在提供下拉式清單，讓您從3個選項中選擇： **[!UICONTROL None]**、 **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg)。 已添加XtkSecurity_Disable_Preproc安全標誌。 對於新客戶，此選項將設為0。 對於現有客戶，此選項將由postupgrade設為1，以保留先前的行為。 請參閱本 [節](../../workflow/using/data-loading--file-.md)。
* 修正測試未設定時區的FDA外部帳戶連線時發生的密碼可見度問題。
* 已移除PDFBox資料庫。
* Tomcat已更新至7.0.93版。
* 修正當安全性Token無效時發生的Token可見性問題。
* 修正WSDL JSP(schemawsdl.jsp)中潛在的XTK插入問題。
* 已優化應用程式原始碼和記憶體中的憑據和密碼儲存。
* PII視圖限制已優化。 (NEO-12339、NEO-12396、NEO-12398、NEO-12339、NEO-12667)
* 已修正密鑰管理中的不一致問題。
* 使用有效或無效的使用者名稱時，失敗的登入嘗試現在會顯示相同的一般錯誤。
* 已增強已上傳檔案的命名。
* 已新增新的XtkSecurity_Disable_GetSetEnv選項，以阻止使用setEnv和getEnv函式。
* 敏感資訊現在會隱藏在應用程式堆疊追蹤中。

**護欄、穩健性與可擴充性改進**

* 使用期限- XtkNewId序列使用最佳化：最耗用的表格已從xtkNewId序列移至專用序列。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* HTTP v2的FDA:fda over HTTP通訊協定廣泛用於混合部署，尤其是廣泛的Log擷取與傳送準備。 已增強穩健性，以避免在擷取或推送資料時發生網路問題和可能的錯誤。 這要求連接兩端的內建都是最新的，否則仍會使用舊協定。
* 追蹤工作流程：增強了跟蹤工作流的魯棒性。 與追蹤記錄插入／更新和URL追蹤自訂相關的數個問題已修正。 此外，追蹤工作流程現在會偵測可能導致錯誤並停止工作流程的追蹤記錄問題。 現在會捨棄這些問題，而不加以處理。
* 清除工作流程：已改善清除工作流程，以避免可能的錯誤和停止。 這樣可以優化資料庫大小和效能。
* 將映像嵌入事務性消息：我們新增了對交易訊息中內嵌影像的完整支援，以避免可能當機或遺失影像。
* 資料庫大小- XtkJobLog:已將清除機制添加到此表中。 這對資料庫大小有積極影響。
* 密件副本歸檔：BCC封存的預設參數已變更，以提高封存速度。 [閱讀更多資訊](../../installation/using/email-archiving.md#parameters)
* 資料庫結構更新：資料庫結構更新嚮導生成的SQL請求已得到改進，以加快執行速度。
* 操作員操作的護欄：為防止營運商執行可能影響平台完整性的動作，已實施數項防護措施。 無法再透過介面刪除內建結構描述。 此外，非管理員使用者無法再編輯工作流程來源XML。
* 已提供兩個新選項： **XtkSecurity_Restrict_EditXML** （可讓您停用傳送的XML程式碼版本）和 **NmsOperation_OperationMgtDebug** （可讓您監控操作管理技術工作流程執行）。 [閱讀更多資訊](../../installation/using/configuring-campaign-options.md)

**其他變更**

* 推播通知：我們現在支援iOS推播的「執行緒ID」選項。
* 已改善可能導致錯誤等級問題的長名稱索引管理。
* 現在，在分析反編譯傳送期間，如果發佈模式在部署精靈中設 **[!UICONTROL None]** 定為，則會記錄錯誤並停止分析：&quot;發佈模式設定為&#39;無&#39;:無法嵌入影像。 功能手機無法顯示影像。」 (NEO-12208)
* 交易訊息的廣播管理已經改善。 當廣播從執行例項同步到控制例項時，@lastModified欄位會更新至系統的目前日期。 MC_Update_BlLastModified選項已添加到控制實例。 True表示目前日期將用於控制例項（預設行為）。 False表示我們使用執行例項廣告的@lastModified日期。 (NEO-12579)
* 已在抵用券臨時表格中新增索引，以最佳化傳送。 (NEO-12437)
* 在Analytics整合中，現在允許擷取含%字元的AAM區段資料。 (NEO-12025)
* 已移除「工作流程熱圖」中的10,000個記錄限制，以修正遺失的資料問題。 (NEO-12329)
* 不支援Open Office，現在已完全從應用程式移除。 如果您仍在使用它，請移至Libre Office，因為從19.1開始，它將無法運作。
* 您現在可以使用sysfilter屬性限制對工作流中更新資料活動的「寫入」訪問。 [閱讀更多資訊](../../configuration/using/filtering-schemas.md)

**修補程式**

* 修正iOS行動推播通知無法上傳憑證的問題。
* 已修正交易推播通知的伺服器經常性當機問題。 其他當機問題已修正。
* 修正造成使用者活動與未結傳送指標的追蹤報表不一致的問題。 (NEO-11742)
* 修正IMS登入的問題。
* 修正從程式庫新增影像時，傳送中可能遺失影像的問題。 (NEO-11900)
* 修正在直接郵件傳送中擷取選件詳細資訊時可能發生的問題。 (NEO-11700)
* 修正可能影響SMS交易訊息效能的問題。 (NEO-9812)
* 修正當使用傳送之主要目標之外部檔案中的「定義」選項時，可能會發生的主控台當機問題。 (NEO-12349)
* 修正分析日文(.JP)網域的目標收件者訊息時的問題。 (NEO-12246)
* 修正使用1:N連結的值分佈時的顯示問題。 (NEO-12212、NEO-11820)
* 修正MTA記錄檔中，在錯誤升級後可能會發生NmsMxDomain錯誤的問題。 (NEO-12752)
* 修正在擴充工作流程活動中使用「保留主集的所有其他資料」選項的問題。 (NEO-13291)
* 修正使用HTTP2傳送推播通知時的Tomcat當機問題。 (NEO-12701)
* 修正HTTPRequest API未等待所有回呼完成的問題。 (NEO-12628)
* 修正交易訊息追蹤指標的計算程式問題。 (NEO-12529)
* 修正選件管理中使用主題的問題。 (NEO-11804)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 已修正在選件管理中預覽傳出XML或CSV檔案以傳送直接郵件時的問題。 (NEO-11290)
* 修正安裝「管理社交網 **路** (Social Marketing)」套件時的問題。 (NEO-12081)
* 修正即使您擁有正確的存取權限，仍無法刪除Web應用程式的問題。 (NEO-12072)
* 修正匯出後再透過XML匯入物件時，可能會覆寫某些值的問題。 已添加XtkExport_IncludeDefaultValues選項。 設為True（預設行為）時，會匯出所有值。 設為False時，會以預設值覆寫修改。 (NEO-11979)
* 修正在查詢後新增 **[!UICONTROL Alert]** 擴充活動時，工作流程活動失敗的問題。 (NEO-12132)
* 修正Oracle設定中，無法從資料庫成功檢索管線（觸發器）偏移而導致重複的問題。 (NEO-12121)
* 修正使用Analytics整合時，可能導致樞紐表格顯示錯誤的問題(NEO-12103)
* 修正「描述性分析」報表的問題。 (NEO-11414)
* 修正CRM連接器的問題：當遠端表格包含名稱有底線的欄位時。
* 修正「假設」報表中貨幣符號的顯示問題。 (NEO-11634)
* 修正在追蹤連結中使用特定字元時的重新導向與追蹤問題。
* 修正選件預覽無法正常運作的問題。
* 修正無法從位址表移除軟彈回數的問題。
* 修正使用條碼時的JAVA錯誤。
* 修正Web應用程式的翻譯問題(NEO-12460)
* 修正s3檔案傳輸工作流程活動的問題。 (NEO-12473)
* 修正Web應用程式中的日期欄位問題。 (NEO-12496)
* 修正傳送中使用種子位址時的ID耗盡問題。 (NEO-11842)
* 修正phantomjs和Debian 9相容性的問題。
* 修正核准證明內容時的錯誤。 (NEO-12725)
* 修正「從人口中排除此子集」工作流程功能的問題。 (NEO-12441)
* 修正HTTPRequest-wait API未等待所有回呼完成的問題。 (NEO-12628)
* 修正分割活動中「更新共用對象」工作的問題。 (NEO-11562)
* 已修正Web伺服器當機問題。 (NEO-12904)
* 修正交易範本中「自然」參數的問題。 (NEO-12334)
* 修正在電子郵件文字編輯器中顯示追蹤的URL時的主控台當機問題。 (NEO-13122)
* 修正從Audience manager匯入觀眾時，「分割檔案」活動的問題。 (NEO-11550)
* 修正熱點按報告中發生錯誤的問題。 (NEO-11459)
* 已修正選件轉換的問題。 (NEO-11565)
* 修正從Audience manager匯入觀眾時，「清單更新」活動的問題。 (NEO-11226)
* 修正「排程」活動和時區設定的問題。 (NEO-11662)
* 修正當URL格式錯誤時，追蹤工作流程失敗的問題。
* 修正匯入行動應用程式套件後，外部帳戶的問題。
* 修正將時區指派給運算子的問題。 (NEO-12464)
* 修正可能導致像片記錄檔錯誤的問題。 (NEO-11539、NEO-8978)
* 修正按一下儲存報表中「步驟記錄」圖示的問題。 (NEO-11620)
* 修正在報表中編輯樞紐表時的問題。 (NEO-12068)
