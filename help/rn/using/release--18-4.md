---
product: campaign
title: Campaign 18.4發行說明
description: Release notes for Campaign 18.4
exl-id: bbad81ba-a09f-4d67-9309-628ea7a08c9b
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 7%

---

# 第 18.4 發行版本{#release-18-4}

![](../../assets/v7-only.svg)

## 發行版本 18.4.5 - 版本編號 8937{#release-18-4-5-build-8937}

2018年11月21日

**功能改善**

* 修正在FDA上使用MySQL執行工作流程時的各種問題。 (NEO-11652)
* 修正特定情況下，傳送母體的一部分仍處於待定狀態的問題。 (NEO-11336)
* 修正SMS自動回應的間歇性問題。 (NEO-11811)
* Fixed an ID exhaustion issue when using seed addresses in a delivery. (NEO-11842)
* 修正在擴充工作流程活動中執行排序時的語法錯誤。 (NEO-11394)
* 修正了重新啟動IIS時，可能導致Web伺服器當機的問題。 (NEO-10862)
* 修正組建升級(FDA - SQL)後，追蹤工作流程可能失敗的問題。 (NEO-11635)
* 修正可能導致工作流程清單資料遺失的問題。 (NEO-11696)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* Fixed an issue which prevented web tracking from working for &quot;com.au&quot; domains (NEO-4385).
* 修正使用複雜工作流程時可能發生的用戶端凍結問題。 (NEO-11847)
* 修正選取特定結構的元素後儲存新傳送時的Oracle錯誤(NEO-11682)。
* 修正查詢包含重音字元的欄位時的問題(FDA/Teradata)。 外部帳戶現在可讓您變更用於與Teradata驅動程式通訊的編碼。 (NEO-11818).
* 修正在推播通知中傳遞其他變數中的URL時，可能導致行動應用程式收到格式錯誤或資料不正確的追蹤問題。 （NEO-11468、NEO-11960）
* 修正將值分佈與1:N連結搭配使用時，造成顯示問題的問題。 (NEO-11820)
* 修正批量載入無法用於Teradata16的問題。
* 增加Teradata上時間戳記的緩衝區大小，以避免與15.10驅動程式發生捆綁問題。
* 改善了長名稱索引的管理，這可能造成升級後問題。
* 改善子程式死機處理(MTA)期間的共用記憶體可用時間。
* 修正Apache（追蹤）中的潛在鎖死。

## 發行版本 18.4.4 - 版本編號 8936{#release-18-4-4-build-8936}

2018年8月1日

**功能改善**

* 電子郵件封存記錄已增強，讓您更輕鬆更清楚地檢查哪些電子郵件已成功傳送或透過密件副本封存失敗。 (NEO-10675)
* 修正了導致在追蹤廣播中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用 **[!UICONTROL Prepare the personalization data with a workflow]** 傳遞選項。 （NEO-11047、NEO-11301）
* 修正傳遞屬性遭錯誤覆寫的隨機問題。 (NEO-11015)
* 修正在 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-11382)
* 修正在 **[!UICONTROL Survey answers]** 工作流程活動。 (NEO-10816)
* 修正了使用版本編號8935執行伺服器升級時的問題。
* 修正了在升級後記錄中，若 **[!UICONTROL Survey answers]** 工作流程活動未完全設定。
* FDATeradata:修正SQL表格中自動增加欄位和索引的問題。

## 發行版本 18.4.3 - 版本編號 8935{#release-18-4-3-build-8935}

2018年6月22日

**功能改善**

* 修正Microsoft Edge和Internet Explorer的追蹤編碼問題。 (NEO-11257)
* 修正LINE傳送中影像連結個人化的問題。 (NEO-11077)
* 修正ID序列產生機制無法正常運作的問題。 (NEO-11115)
* 修正使用具有整數類型調解金鑰的自訂命名空間時，隱私權(GDPR)要求無法運作的問題。 (NEO-11123)
* 修正使用 **[!UICONTROL Distribution of values]** 選項 **[!UICONTROL Query]** 工作流程活動。 (NEO-10958)
* 修正從行銷例項同步選件空間至互動例項的問題。 (NEO-11162)
* Improved the management of long name indexes during postupgrade

## 發行版本 18.4.2 - 版本編號 8932{#release-18-4-2-build-8932}

2018年5月22日

**功能改善**

* 修正Windows Server更新無法正常運作的問題。
* 修正 **[!UICONTROL Survey Result]** 活動。 報告顯示不正確。 (NEO-10816)
* 修正了使用退信郵件伺服器時，inMail程式可能發生的效能問題。 (NEO-10641)
* 修正了升級超過1000個結構時可能發生的資料庫升級問題。

## 發行版本 18.4 - 版本編號 8931{#release-18-4-build-8931}

2018年4月24日

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
   <td> EU General Data Protection Regulation (GDPR)<br /> </td> 
   <td> <p>GDPR是歐盟(EU)的新隱私權法，協調2018年5月25日生效的資料保護要求並以現代化方式規範這些要求。 GDPR 適用於所持有資料的主體居住於歐盟的 Adobe Campaign 客戶。</p> <p>除了Adobe Campaign中已提供的隱私權功能（包括同意管理、資料保留設定和使用者角色）之外，我們也趁此次機會，以資料處理者的角色加入其他功能，以協助您做好準備，以便擔任資料控管單位，處理特定GDPR請求：</p> 
    <ul> 
     <li> <p>訪問權限：可讓資料主體接收資料控制者擷取的其個人資料副本，可能包括儲存在Adobe Campaign中的資料。</p> </li> 
     <li> <p>刪除權限：為資料主體賦予權利，讓資料控制者擷取的個人資料遭到清除，可能包括儲存在Adobe Campaign中的資料。</p> </li> 
    </ul> 如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">詳細文件</a>以瞭解詳情。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的設定檔案<br /> </td> 
   <td> <p>Adobe Campaign現在提供作用中設定檔的清單，並透過專用的工作流程每月更新。</p> <p>如需詳細資訊，請參閱<a href="../../platform/using/about-profiles.md#active-profiles">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推播連接器增強功能<br /> </td> 
   <td> <p>已增強Android連接器，以支援更高的吞吐量。 </p> <p>如需詳細資訊，請參閱<a href="../../delivery/using/configuring-the-mobile-application.md">詳細文件</a>以瞭解詳情。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性改善功能**

* 現在已停用外部實體的擴充，以防止未驗證使用者發生潛在攻擊。 (NEO-10173)
* 強化權限，以防止標準使用者變更執行個體設定參數，例如應用程式存取URL、LDAP設定等。 (NEO-10171)
* 修正了可能透過堆疊追蹤顯示敏感資訊的問題。 錯誤詳細資訊現在記錄在無法從外部網路存取的位置的後端。 (NEO-10176)
* 強化的權限，以防止標準使用者檢視管理員的已上傳檔案和/或已匯出套件。 (NEO-10170)

**功能改善**

* **LINE通道 — 架構增強**:與Adobe Campaign中的所有其他管道一樣，現在所有部署類型都支援LINE管道：托管、混合和內部部署。
* **序列自動生成**:已增強ID產生機制，以增加具有大量物件之Campaign執行個體的有效期限。 如需詳細資訊，請參閱 [技術檔案](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html).

**其他變更**

* 使用命令行導入包時可使用新模式，允許循環依賴項（對於大型包不建議使用）。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-8979)
* 改善Teradata中載入大量資料的效能，並修正無法顯示記錄中處理之資料的正確值的問題。 (NEO-10429)
* 從Audience Manager匯入對象現在可處理分割檔案。 以前，只有匯入SharedAudience技術工作流程匯入了區段的最後一個檔案。 (NEO-10156)
* 在Windows上，Campaign伺服器的預設安裝路徑已變更。 啟動64位元版本設定時，預設安裝路徑現在為： **C:\Program Files\Adobe\Adobe Campaign Classic v7** 而非 **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 已增強預設的MX規則，以包含更多網域並最佳化輸送量。
* 對部署精靈SOAP呼叫(xtk:serverOptions#SaveOptions)強制存取限制。
* weka.jar淘汰程式庫已移除，OpenSSL程式庫已更新，以最佳化安全性。
* 改善帳單技術工作流程以保護執行個體效能。
* 管理員設定或重設任何運算子密碼的功能已還原。 若要這麼做，請以滑鼠右鍵按一下運算子，選取 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 並設定操作員的新密碼。 建議操作員在首次重新連線時變更其密碼。 如需詳細資訊，請參閱[詳細文件](../../production/using/lost-password.md)以瞭解詳情。
* 為了支援Adobe Target中的新多租用戶功能，現在當設定與Target整合的選項和外部帳戶時，可以將新的「at_property」參數新增至URL。 可在Adobe Target中找到此參數使用的值，且將供Campaign在對Target執行呼叫時使用。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 您現在可以指定在按一下Adobe Target提供的影像時要開啟的預設登陸頁面。 過去，點按該影像會改為建立電子郵件時產生預設影像集。 如需詳細資訊，請參閱[詳細文件](../../integrations/using/inserting-a-dynamic-image.md)以瞭解詳情。
* 新增 **啟用SMPP跟蹤** 外部帳戶中的複選框以強制跟蹤輸出。 如需詳細資訊，請參閱[詳細文件](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)以瞭解詳情。

**技術演變**

queryDef

已針對&quot;orderBy&quot;子句修改queryDef。 Before the change, the primary key of the queried table would implicitly be added to the &quot;orderBy&quot; clauses. 在某些資料庫引擎（至少是postgresql）上，它會阻止索引的使用（orderBy子句的所有欄位必須由同一索引覆蓋）。 如果您與此行為相依，則必須在「orderBy」子句中明確新增主鍵。

例如，如果您有下列查詢：

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

以（在18.4變更前）的形式隱含：

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode函式

「urlEncode」 JavaScript函式無法正常用於非ASCII字元。 已修正，現在應可搭配所有Unicode字元（包括日文字元）使用。 如果您依賴非ASCII字元的「urlEncode」行為，則必須調整您的代碼。

包導入新模式

使用命令行導入包時可使用新模式，允許循環依賴項（對於大型包不建議使用）。 會保留現有功能。 對於具有循環依賴項的此類包，將添加一個新標籤 **-usejs** 已新增至命令列套件匯入。 執行時，會像從介面執行套件匯入時一樣使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修補程式**

* Fixed a synchronization issue when replicating delivery and tracking logs from Adobe Campaign Standard to Adobe Campaign Classic. (NEO-10023)
* Fixed an issue with the handling of Error and Log tables in Teradata when an ETL workflow was resuming after a failure on a fast load operation. 現在，每次工作流恢復時，錯誤和日誌表都會被正確刪除。 (NEO-10672)
* 修正了升級後問題，若已安裝FDA套件，則會自動安裝Hive套件(Hadoop所需)。 (NEO-10592)
* Fixed an error that treated invalid domains as a **Not defined** error. (NEO-10248)
* 修正傳送android推播傳送時，deliveryLogStats表格中重複記錄的問題。 (NEO-10234)
* 修正條碼掃描器無法讀取某些條碼格式的問題。 (NEO-10125)
* 修正使用非ASCII字元時，「urlEncode」 JavaScript函式的問題。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-10123)
* 修正在Teradata資料庫上執行包含sha256函式的查詢時的問題。 (NEO-10119)
* 修正了使用超大的SalesForce表時，SalesForce活動中可能發生的工作流記憶體錯誤。 (NEO-9900)
* 修正 **生成補充** 選項（使用FDA時在目標工作流程活動中）。 (NEO-9878)
* Fixed an issue which could lead to the **Processed** and **Success** metrics not being updated on the marketing instance when using mid-sourcing. (NEO-9454)
* 修正平台總共提供超過10,000個選件時的互動非主張規則(NEO-9352)
* 修正了使用XML外部檔案時無法指定傳送目標的問題。 (NEO-9312)
* 修正在選件上執行假設並更新主張狀態時，可能導致工作流程錯誤的問題。 (NEO-9304)
* 修正根據Android傳送對應的屬性使用壓力規則時，在傳送分析期間發生的錯誤。 (NEO-9202)
* 修正排序收件者清單中的欄時，可能導致效能問題的問題。 有關queryDef修改的詳細資訊，請參閱下面的「技術演變」一節。 (NEO-9042)
* 修正核准電子郵件中的連結可能指向錯誤登入URL的問題，尤其是使用Federated ID登入類型時。 (NEO-9011)
* 修正某些時區的報表日期選擇器顯示錯誤日期的問題。 (NEO-9007)
* 修正使用FDA SQL資料庫時無法檢視傳出目標的問題。 (NEO-8924)
* 修正導致MS Dynamics CRM連接器無法提取前7天資料的問題。 (NEO-8803)
* 修正Analytics整合的錯誤，該錯誤會讓使用者無法加入國際字元。 (NEO-8719)
* 修正了在沒有適當權限的情況下，可能會啟用工作流程編輯的問題。 (NEO-8708)
* 修正在混合架構中使用訊息中心時，導致連線中斷或連線遺失（逾時）的FDA over HTTP問題。 (NEO-8438)
* 修正負ID的增量查詢活動中發生的工作流程錯誤。 (NEO-8229)
* 修正某些畫面中可能顯示雙捲軸的問題。 (NEO-8208)
* 修正了在執行更新資料庫結構精靈時，顯示錯誤訊息的問題。 PostUpgrade將對名稱超過30的索引執行更名。 請注意，對於大型表，替換索引需要時間。 (NEO-7983)
* 修正追蹤記錄無法從Message Center執行例項正確同步至控制例項的問題。 (NEO-7286)
* 修正選件擴充活動的效能問題。 (NEO-7263)
* 修正了透過FDA查詢Redshift資料庫時無法使用DaysAgo函式的問題。 (NEO-7099)
* 修正資料管理中無法在類似擴充的工作流程活動上建立索引的回歸。
* 修正以標題建立外部資源時可能發生的問@id
* 修正透過FTP伺服器上傳壓縮檔案，或上傳檔案名稱中含有萬用字元的檔案時，可能發生的問題。
* Fixed an issue with long base type enumerations in external custom resources created into Campaign Standard.
* 修正即使與提供者的連線失敗，仍可能傳送簡訊，導致簡訊遺失的問題。
* 修正導致SMTP連線無限期卡住的錯誤。
* 修正使用LINE對應或篩選及定位結構不同時，訊息準備期間壓力類型規則的問題。
