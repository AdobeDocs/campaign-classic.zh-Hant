---
solution: Campaign Classic
product: campaign
title: Campaign 18.4發行說明
description: Campaign 18.4的發行說明
feature: null
role: null
level: null
translation-type: tm+mt
source-git-commit: ce60b2bd0a9d75ca429af2f740832b408ce3c48b
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 7%

---


# 18.4 發行版本{#release-18-4}

## 發行版本 18.4.5 - Build 8937{#release-18-4-5-build-8937}

2018年11月21日

**功能改善**

* 已修正使用FDA上的MySQL執行工作流程時的各種問題。 (NEO-11652)
* 修正特定情況下，部分交貨人口仍處於擱置狀態的問題。 (NEO-11336)
* 修正SMS自動回應的間歇性問題。 (NEO-11811)
* 修正傳送中使用種子位址時的ID耗盡問題。 (NEO-11842)
* 修正在擴充工作流程活動中執行排序時的語法錯誤。 (NEO-11394)
* 修正重新啟動IIS時，可能導致Web伺服器當機的問題。 (NEO-10862)
* 修正在建置升級(FDA - SQL)後，追蹤工作流程可能會失敗的問題。 (NEO-11635)
* 修正工作流程清單資料遺失的問題。 (NEO-11696)
* 修正傳送推播通知時的效能問題。 (NEO-11787)
* 修正網頁追蹤無法用於&quot;com.au&quot;網域(NEO-4385)的問題。
* 修正使用複雜工作流程時可能發生的用戶端凍結問題。 (NEO-11847)
* 修正在選取特定架構的元素後儲存新傳送時的Oracle錯誤(NEO-11682)。
* 修正查詢包含重音字元的欄位時的問題(FDA/Teradata)。 外部帳戶現在允許您更改用於與Teradata驅動程式通信的編碼。 (NEO-11818).
* 修正在推播通知中傳送其他變數中的URL時，可能導致行動應用程式收到格式錯誤或資料不正確的追蹤問題。 (NEO-11468、NEO-11960)
* 修正當使用1:N連結的值分佈時，造成顯示問題的問題。 (NEO-11820)
* 修正批量載入無法在Teradata16上運作的問題。
* 增加Teradata上時間戳記的緩衝區大小，以避免與15.10驅動程式發生系結問題。
* 已改善可能導致錯誤等級問題的長名稱索引管理。
* 已改善子代停用處理(MTA)期間的共用記憶體可用時間。
* 修正Apache（追蹤）中的潛在死鎖。

## 發行版本 18.4.4 - Build 8936{#release-18-4-4-build-8936}

2018年8月1日

**功能改善**

* 電子郵件封存記錄已增強，因此檢查哪些電子郵件已透過密件副本封存成功傳送或失敗，變得更輕鬆更清楚。 (NEO-10675)
* 修正導致在追蹤廣播中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;傳送選項時發生的問題。 (NEO-11047、NEO-11301)
* 修正導致傳送屬性覆寫錯誤的隨機問題。 (NEO-11015)
* 修正在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流程活動中使用計算欄位的問題。 (NEO-11382)
* 修正在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流程活動中使用儲存在XML中的資料時的問題。 (NEO-10816)
* 修正使用build 8935執行伺服器升級時的問題。
* 修正當&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流程活動未完整設定時，在設定檔記錄檔中顯示無用錯誤的問題。
* FDATeradata:修正SQL表格中自動遞增欄位和索引的問題。

## 發行版本 18.4.3 - Build 8935{#release-18-4-3-build-8935}

2018年6月22日

**功能改善**

* 修正Microsoft Edge和Internet Explorer的追蹤編碼問題。 (NEO-11257)
* 修正LINE傳送中影像連結個人化的問題。 (NEO-11077)
* 修正ID序列產生機制無法正確運作的問題。 (NEO-11115)
* 修正使用具有整數類型協調金鑰的自訂命名空間時，隱私權(GDPR)要求無法運作的問題。 (NEO-11123)
* 修正在&#x200B;**[!UICONTROL Query]**&#x200B;工作流程活動中使用&#x200B;**[!UICONTROL Distribution of values]**&#x200B;選項時可能發生的錯誤。 (NEO-10958)
* 修正從行銷實例同步選件空間至互動實例的問題。 (NEO-11162)
* 改進配置期間長名稱索引的管理

## 發行版本 18.4.2 - Build 8932{#release-18-4-2-build-8932}

2018年5月22日

**功能改善**

* 修正Windows Server更新無法正常運作的問題。
* 修正使用XML中儲存的資料時，**[!UICONTROL Survey Result]**&#x200B;活動中的問題。 報表顯示不正確。 (NEO-10816)
* 修正使用彈回郵件伺服器時，inMail程式可能會發生的效能問題。 (NEO-10641)
* 修正在升級超過1000個結構描述時可能發生的資料庫升級問題。

## 發行版本 18.4 - Build 8931{#release-18-4-build-8931}

2018年4月24日

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
   <td> 歐盟通用資料保護規則(GDPR)<br /> </td> 
   <td> <p>GDPR是歐盟(EU)的新隱私權法，協調並現代化將於2018年5月25日生效的資料保護要求。 GDPR 適用於所持有資料的主體居住於歐盟的 Adobe Campaign 客戶。</p> <p>除了Adobe Campaign已具備的隱私權功能（包括同意管理、資料保留設定和使用者角色）外，我們還將利用這個機會作為資料處理者加入額外的功能，以協助您做好準備，以因應特定GDPR要求：</p> 
    <ul> 
     <li> <p>存取權：允許資料主體接收資料掌控者所擷取的個人資料副本，可能包括儲存在Adobe Campaign的資料。</p> </li> 
     <li> <p>刪除權：資料主體有權清除資料掌控者擷取的個人資料，可能包括儲存在Adobe Campaign的資料。</p> </li> 
    </ul> 如需詳細資訊，請參閱<a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">相關的文件</a>，以瞭解詳情。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用中的設定檔案<br /> </td> 
   <td> <p>Adobe Campaign現在提供作用中個人檔案的清單，透過專屬的工作流程每月更新。</p> <p>如需詳細資訊，請參閱<a href="../../platform/using/about-profiles.md#active-profiles">相關的文件</a>，以瞭解詳情。</p> </td> 
  </tr> 
  <tr> 
   <td> Android推播連接器增強功能<br /> </td> 
   <td> <p>Android連接器已增強，可支援更高的總處理能力。 </p> <p>如需詳細資訊，請參閱<a href="../../delivery/using/configuring-the-mobile-application.md">相關的文件</a>，以瞭解詳情。</p> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

* 現在已停用外部實體的擴充功能，以防止未驗證的使用者可能受到攻擊。 (NEO-10173)
* 強化權限，防止標準使用者變更例項設定參數，例如應用程式存取URL、LDAP設定等。 (NEO-10171)
* 修正可能透過堆疊追蹤顯示敏感資訊的問題。 錯誤詳細資訊現在記錄在後端到外部網路無法訪問的位置。 (NEO-10176)
* 強化權限，防止標準使用者檢視管理員上傳的檔案和／或匯出的套件。 (NEO-10170)

**功能改善**

* **LINE通道——體系結構增強**:與Adobe Campaign的所有其他通道一樣，LINE通道現在支援所有部署類型：代管、混合式和內部部署。
* **序列自動產生**:ID產生機制已增強，以增加具有大量物件之促銷活動例項的期限。如需詳細資訊，請參閱此[technote](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html)。

**其他變更**

* 使用命令行可以使用新模式導入包，允許循環從屬關係（對於大型包不建議使用）。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-8979)
* 已改善Teradata中大量資料載入的效能，並修正無法顯示記錄中處理之資料正確值的問題。 (NEO-10429)
* 從Audience Manager匯入觀眾現在可處理分割檔案。 以前，只有區段的最後一個檔案是由importSharedAudience技術工作流程匯入的。 (NEO-10156)
* 在Windows上，促銷活動伺服器預設安裝路徑已變更。 啟動64位元版本設定時，預設安裝路徑現在為：**C:\Program Files\Adobe\Adobe Campaign Classic v7**&#x200B;而非&#x200B;**C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 預設MX規則已增強，加入更多網域並最佳化總處理能力。
* 對部署精靈SOAP呼叫(xtk:serverOptions#SaveOptions)強制執行存取限制。
* weka.jar過時的程式庫已移除，OpenSSL程式庫已更新，以進行安全性最佳化。
* 改善帳單技術工作流程，以保護例項效能。
* 管理員設定或重設任何運算子密碼的能力已恢復。 若要這麼做，請在運算子上按一下滑鼠右鍵，選取&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**&#x200B;並設定運算子的新密碼。 我們建議營運商在第一次重新連線時變更其密碼。 如需詳細資訊，請參閱[相關的文件](../../production/using/lost-password.md)，以瞭解詳情。
* 為支援Adobe Target的新多租賃功能，現在在設定選項和外部帳戶以與Target整合時，可將新的&quot;at_property&quot;參數新增至URL。 此參數的值可在Adobe Target找到，且在執行對Target的呼叫時，促銷活動將會使用。 如需詳細資訊，請參閱[相關的文件](../../integrations/using/inserting-a-dynamic-image.md)，以瞭解詳情。
* 您現在可以指定在按一下Adobe Target提供的影像時開啟的預設登陸頁面。 以前，按一下該影像會在建立電子郵件時產生預設影像集。 如需詳細資訊，請參閱[相關的文件](../../integrations/using/inserting-a-dynamic-image.md)，以瞭解詳情。
* 已在外部帳戶中添加「啟用SMPP跟蹤&#x200B;**」複選框以強制跟蹤輸出。**&#x200B;如需詳細資訊，請參閱[相關的文件](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)，以瞭解詳情。

**技術演變**

queryDef

queryDef已針對&quot;orderBy&quot;子句進行修改。 在更改前，查詢表的主鍵將隱式添加到&quot;orderBy&quot;子句中。 在某些資料庫引擎（至少是postgresql）上，它會防止使用索引（orderBy子句的所有欄位必須由同一索引覆蓋）。 如果您與此行為相關，則必須在&quot;orderBy&quot;子句中顯式添加主鍵。

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

它將含蓄地遞交為（在18.4變更之前）:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode函式

&#39;urlEncode&#39; JavaScript函式無法正常用於非ASCII字元。 它已修正，現在應可處理所有Unicode字元（包括日文字元）。 如果您依賴「urlEncode」行為來處理非ASCII字元，則必須調整程式碼。

包導入新模式

使用命令行可以使用新模式導入包，允許循環從屬關係（對於大型包不建議使用）。 保留現有功能。 對於具有循環依賴性的此類軟體包，命令行軟體包導入中已添加了新標籤&#x200B;**-usejs**。 執行時，它將像從介面執行包導入時一樣使用JSEngine。

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**修補程式**

* 修正從Adobe Campaign Standard複製傳送和追蹤記錄檔至Adobe Campaign Classic時的同步問題。 (NEO-10023)
* 修正在快速載入作業失敗後，ETL工作流程繼續執行時，在Teradata中處理「錯誤」和「記錄檔」表格的問題。 現在，每次工作流恢復時，錯誤和日誌表都會正確刪除。 (NEO-10672)
* 修正當安裝FDA封裝時，自動安裝Hive封裝(Hadoop需要)的Postupgrade問題。 (NEO-10592)
* 修正將無效網域視為&#x200B;**Not defined**&#x200B;錯誤的錯誤。 (NEO-10248)
* 修正傳送Android推播傳送時，deliveryLogStats表格中重複記錄的問題。 (NEO-10234)
* 修正可能導致某些條形碼格式無法由條形碼掃描器讀取的問題。 (NEO-10125)
* 修正使用非ASCII字元時，「urlEncode」 JavaScript函式的問題。 如需詳細資訊，請參閱「技術演變」一節。 (NEO-10123)
* 修正在Teradata資料庫上執行包含sha256函式的查詢時的問題。 (NEO-10119)
* 修正當使用非常大的SalesForce表時，SalesForce活動中可能發生的工作流記憶體錯誤。 (NEO-9900)
* 修正使用FDA時，定位工作流程活動中的&#x200B;**產生補體**&#x200B;選項問題。 (NEO-9878)
* 修正當使用中間來源補充時，行銷例項上的&#x200B;**Processed**&#x200B;和&#x200B;**Success**&#x200B;量度無法更新的問題。 (NEO-9454)
* 修正在平台中總共超過10k個選件時的互動非重新命題規則(NEO-9352)
* 修正使用XML外部檔案時無法指定傳送目標的問題。 (NEO-9312)
* 修正在選件上執行假設並更新提案狀態時，可能導致工作流程錯誤的問題。 (NEO-9304)
* 修正根據Android傳送對應的屬性使用壓力規則時，在傳送分析期間發生的錯誤。 (NEO-9202)
* 修正在收件者清單中排序欄時，可能導致效能問題的問題。 有關queryDef修改的詳細資訊，請參閱下方的「技術演變」一節。 (NEO-9042)
* 修正核准電子郵件中的連結可能指向錯誤登入URL的問題，尤其是使用Federated ID登入類型時。 (NEO-9011)
* 修正某些時區的報表日期選擇器中顯示錯誤日期的問題。 (NEO-9007)
* 修正使用FDA SQL資料庫時無法檢視傳出目標的問題。 (NEO-8924)
* 修正導致MS Dynamics CRM連接器無法提取每月前7天資料的問題。 (NEO-8803)
* 修正Analytics整合導致使用者無法包含國際字元的錯誤。 (NEO-8719)
* 修正在沒有適當權限的情況下啟用工作流程編輯的問題。 (NEO-8708)
* 修正在混合式架構中使用訊息中心時，FDA over HTTPs導致連線中斷或連線遺失（逾時）的問題。 (NEO-8438)
* 修正負ID的遞增查詢活動中發生的工作流程錯誤。 (NEO-8229)
* 修正某些畫面中顯示雙捲軸的問題。 (NEO-8208)
* 修正在執行更新資料庫結構精靈時，顯示錯誤訊息的問題。 PostUpgrade將對名稱超過30的索引執行更名。 請注意，對於大型表，索引替換將需要時間。 (NEO-7983)
* 修正追蹤記錄無法從「訊息中心」執行例項正確同步以控制例項的問題。 (NEO-7286)
* 修正選件擴充活動的效能問題。 (NEO-7263)
* 修正透過FDA查詢Redshift資料庫時無法使用DaysAgo函式的問題。 (NEO-7099)
* 修正資料管理中無法在類似擴充的工作流程活動上建立索引的回歸。
* 修正建立標題為@id的外部資源時可能發生的問題
* 修正透過FTP伺服器上傳壓縮檔案或上傳檔案名稱中含萬用字元的檔案時，可能會發生的問題。
* 修正外部自訂資源中建立至Campaign Standard的長基本類型列舉問題。
* 修正即使與提供者的連線失敗，也可能導致SMS遺失的問題。
* 修正SMTP連線無限期卡住的錯誤。
* 修正在使用LINE對應或篩選和定位結構不同時，訊息準備期間壓力類型規則的問題。
