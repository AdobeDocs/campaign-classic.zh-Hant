---
solution: Campaign Classic
product: campaign
title: 資料模型最佳實務
description: 瞭解如何使用Campaign Classic資料模型
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '4010'
ht-degree: 1%

---


# 資料模型最佳實務{#data-model-best-practices}

本檔案概述設計您的Adobe Campaign資料模型時的主要建議。

如需深入瞭解促銷活動內建表格及其互動，請參閱[本節](../../configuration/using/about-data-model.md)一節。

請閱讀[本檔案](../../configuration/using/about-schema-reference.md)以開始使用促銷活動結構。 瞭解如何配置擴展方案以擴展[本文檔](../../configuration/using/about-schema-edition.md)中的Adobe Campaign資料庫的概念資料模型。

## 概觀 {#overview}

Adobe Campaign系統極為靈活，可以擴展至最初的實施範圍之外。 不過，儘管可能性無限，但必須做出明智決策並建立堅實的基礎，才能開始設計您的資料模型。

本檔案提供常見的使用案例和最佳範例，以瞭解如何正確設計您的Adobe Campaign工具。

## 資料模型體系結構{#data-model-architecture}

Adobe Campaign Standard是功能強大的跨通道宣傳管理系統，可協助您調整線上和線下策略，以建立個人化客戶體驗。

### 以客戶為中心的方法{#customer-centric-approach}

雖然大多數電子郵件服務供應商都是透過以清單為中心的方式與客戶溝通，但Adobe Campaign仍依賴關係資料庫，以運用更廣泛的客戶及其屬性檢視。

以客戶為中心的方法如下圖所示。 **Recipient**&#x200B;灰色表格代表正在構建所有內容的主要客戶表：

![](assets/customer-centric-data-model.png)

要訪問每個表的說明，請轉至&#x200B;**[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選擇資源，然後按一下&#x200B;**[!UICONTROL Documentation]**&#x200B;頁籤。

Adobe Campaign預設資料模型顯示在[本文檔](../../configuration/using/data-model-description.md)中。

>[!NOTE]
>
>Adobe Campaign Classic允許建立自訂客戶表。 但是，在大多數情況下，建議使用已預先建立其他表格和功能的標準[收件者表格](../../configuration/using/about-data-model.md#default-recipient-table)。

### Adobe Campaign資料{#data-for-campaign}

哪些資料應該傳送至Adobe Campaign? 確定行銷活動所需的資料至關重要。

>[!NOTE]
>
>Adobe Campaign既不是資料倉庫，也不是報告工具。 因此，請勿嘗試將所有可能的客戶及其相關資訊匯入Adobe Campaign，或匯入僅用於建立報表的資料。

要決定是否需要某個屬性在Adobe Campaign，請問問自己是否屬於以下類別：

* 用於&#x200B;**segmentation**&#x200B;的屬性
* 用於&#x200B;**資料管理進程**&#x200B;的屬性（例如聚合計算）
* 用於&#x200B;**個人化**&#x200B;的屬性

如果不是落入其中任何一個圈套，你很可能不需要Adobe Campaign的這個屬性。

### 資料類型選擇{#data-types}

為確保系統的良好架構和效能，請遵循下列最佳實務，在Adobe Campaign設定資料。

* 大型表格大多應包含數字欄位，並包含參考表格的連結（使用值清單時）。
* **expr**&#x200B;屬性允許將模式屬性定義為計算欄位，而不是表中的物理集值。 這可讓您存取不同格式的資訊（例如年齡和出生日期），而不需儲存兩個值。 這是避免重複欄位的好方法。 例如，「收件者」表格使用網域的運算式，該運算式已存在於電子郵件欄位中。
* 但是，當運算式計算複雜時，不建議使用&#x200B;**expr**&#x200B;屬性作為即時計算，可能會影響查詢的效能。
* **XML**&#x200B;類型是避免建立過多欄位的好方法。 但是，當它使用資料庫中的CLOB列時，它也佔用了磁碟空間。 它還可能導致複雜的SQL查詢，並可能影響效能。
* **string**&#x200B;欄位的長度應一律以欄定義。 依預設，Adobe Campaign的最大長度為255，但Adobe建議在您已知道大小不會超過較短長度時，將欄位保持在較短。
* 如果您確定源系統的大小被高估且無法達到，那麼在Adobe Campaign的欄位比源系統的欄位短是可以接受的。 這可能意味著Adobe Campaign的字串較短或整數較小。

### 欄位選擇{#choice-of-fields}

如果欄位具有定位或個人化目的，則必須將其儲存在表格中。 換言之，如果欄位不是用來傳送個人化電子郵件，或是用作查詢中的標準，則會佔用磁碟空間，但是卻毫無用處。

對於混合式和內部部署例項，FDA（Federated Data Access，允許存取外部資料的選用功能）涵蓋在促銷活動程式中新增「即時」欄位的需求。 如果你有食品藥物管理局的話，您不需要進口任何產品。 有關詳細資訊，請參見[關於同盟資料存取](../../installation/using/about-fda.md)。

### 鍵選擇{#choice-of-keys}

除了大多數表中預設定義的&#x200B;**autopk**&#x200B;外，您還應考慮添加一些邏輯或業務密鑰（帳戶號、客戶機號等）。 它稍後可用於導入／協調或資料包。 如需詳細資訊，請參閱[識別碼](#identifiers)。

高效的密鑰對效能至關重要。 數值資料類型應始終作為表的鍵。

對於SQLServer資料庫，如果需要效能，可考慮使用「聚簇索引」。 由於Adobe不處理此問題，因此您需要在SQL中建立它。

### 專用表空間{#dedicated-tablespaces}

方案中的表空間屬性允許您為表指定專用表空間。

安裝嚮導允許您按類型（資料、臨時和索引）儲存對象。

專用表空間更適合分區、安全規則，並允許流暢、靈活的管理、更好的優化和效能。

## 標識符{#identifiers}

Adobe Campaign資源有三個識別碼，並且可以添加一個附加的識別碼。

下表說明這些識別碼及其用途。

| 識別碼 | 說明 | 最佳實務 |
|--- |--- |--- |
| ID | <ul><li>id是Adobe Campaign表的物理主鍵。 對於現成可用的表，它是從序列中產生的32位元數</li><li>此識別碼通常對特定的Adobe Campaign例項唯一。 </li><li>自動產生的ID可在架構定義中顯示。 搜尋&#x200B;*autopk=&quot;true&quot;*&#x200B;屬性。</li></ul> | <ul><li>自動產生的識別碼不應用於工作流程或套件定義中的參考。</li><li>不應假設ID永遠是遞增的數字。</li><li>現成可用表格中的ID是32位元數字，此類型不應變更。 此編號取自相同名稱之區段中涵蓋的「序列」。</li></ul> |
| 名稱（或內部名稱） | <ul><li>此資訊是表中記錄的唯一標識符。 此值可以手動更新，通常使用生成的名稱。</li><li>此識別碼會在部署在不同的Adobe Campaign例項時保留其值，且不應為空。</li></ul> | <ul><li>如果對象應從一個環境部署到另一個環境，請更名Adobe Campaign生成的記錄名稱。</li><li>當對象具有namespace屬性（例如&#x200B;*schema*）時，此通用命名空間將用於所有建立的自定義對象。 不應使用某些保留的名稱空間：*nms*、*xtk*。</li><li>當物件沒有任何名稱空間（例如&#x200B;*workflow*&#x200B;或&#x200B;*delivery*）時，此名稱空間概念會新增為內部名稱物件的首碼：*namespaceMyObjectName*。</li><li>請勿使用特殊字元，例如空格&quot;&quot;、半欄&quot;:&quot;或連字型大小&quot;-&quot;。 所有這些字元都會以底線&quot;_&quot;（允許的字元）取代。 例如，&quot;abc-def&quot;和&quot;abc:def&quot;會儲存為&quot;abc_def&quot;，並互相覆寫。</li></ul> |
| 標籤 | <ul><li>標籤是Adobe Campaign中對象或記錄的業務標識符。</li><li>此對象允許空格和特殊字元。</li><li>它不保證記錄的獨特性。</li></ul> | <ul><li>建議您決定物件標籤的結構。</li><li>這是最易於使用的解決方案，可為Adobe Campaign用戶識別記錄或對象。</li></ul> |

## 自訂內部金鑰{#custom-internal-keys}

在Adobe Campaign建立的每個表都需要主鍵。

大多陣列織都從外部系統導入記錄。 雖然「收件者」表格的實體金鑰是「id」屬性，但您也可以另外決定自訂金鑰。

此自訂金鑰是外部系統餵送Adobe Campaign時的實際記錄主要金鑰。

當現成可用的表同時具有自動鍵和內部鍵時，內部鍵將被設定為物理資料庫表中的唯一索引。

建立自訂表格時，有兩個選項：
* 自動產生的金鑰(id)和內部金鑰（自訂）的組合。 如果您的系統金鑰是複合金鑰或非整數，這個選項就很有趣。 整數在大表格和與其他表格連接時，可提供更高的效能。
* 使用主鍵作為外部系統主鍵。 此解決方案通常較為受歡迎，因為它可簡化資料匯入和匯出的方式，而且不同系統之間的索引鍵一致。 如果索引鍵名為&quot;id&quot;，且預期會填入外部值（非自動產生），應停用Autopk。

>[!IMPORTANT]
>
>在工作流程中，不應使用自訂作品做為參考。

## 序列{#sequences}

Adobe Campaign主鍵是自動生成的所有現成可用表ID，對於自定義表可以是相同的。 如需詳細資訊，請參閱[本節](#identifiers)。

此值取自稱為&#x200B;**sequence**&#x200B;的值，此為用於生成數字序列的資料庫對象。

序列有兩種類型：
* **共用**:多個表格會從相同的序列中挑選其ID。這表示，如果某個表使用id &#39;X&#39;，則共用相同序列的其他表將沒有該id &#39;X&#39;的記錄。 **** XtkNewId是Adobe Campaign的預設共用序列。
* **專用**:只有一個表從序列中挑選其ID。序列名稱通常包含表名。

>[!IMPORTANT]
>
>序列是32位元的整數值，可用值數目上限為有限：21.4億。 達到最大值後，序列會回到0，以便循環使用ID。
>
>如果舊資料未清除，則結果將是唯一密鑰違規，這將成為平台運行狀況和使用情況的阻止程式。 Adobe Campaign將無法發送通信（當它影響到交付日誌表時），效能將受到很大影響。

因此，每年傳送60億封電子郵件，其記錄的保留期為180天，但4個月內就會用完ID。 為避免此類挑戰，請務必根據捲進行清除設定。 如需詳細資訊，請參閱[本節](#data-retention)。

當在Adobe Campaign建立具有主鍵作為autoPK的自定義表時，應將自定義專用序列與該表系統地關聯。

依預設，自訂序列的值會介於+1,000到+2.1BB之間。 從技術上講，通過啟用負ID,4BB的全範圍是可能的。 這應該謹慎使用，當從負數轉換為正數時，會遺失一個ID:記錄0通常被Adobe Campaign在生成的SQL查詢中忽略。

**相關主題：**
* 有關&#x200B;**序列自動生成**&#x200B;功能的詳細資訊，請參閱[本文檔](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html)。
* 如需序列耗盡的詳細資訊，請觀賞此影片](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html)。[

## 索引 {#indexes}

索引對於效能至關重要。 當您在架構中聲明索引時，Adobe將自動在索引鍵的欄位上建立索引。 您也可以為不使用索引鍵的查詢聲明更多索引。

Adobe建議定義其他索引，因為它可以改善效能。

但是，請記住下列事項：

* 索引使用量會與您的存取模式綁定。 最佳化索引通常是資料庫設計的關鍵部分，必須由專家處理。 添加索引通常是附加到資料庫維護的迭代工作流。 它會隨著時間逐步完成，以解決發生時的效能問題。
* 索引會增加表的整體大小（以儲存索引本身）。
* 在列上添加索引可以改善資料讀取訪問(SELECT)的效能，但會降低資料寫入訪問(UPDATE)的效能。
* 由於這會影響插入資料時的效能，因此索引的大小和數目應受到限制。
* 不必要時不添加索引。 請確定此為必要項目，並提高查詢（測試和學習）的整體效能。
* 一般而言，如果您知道查詢不會帶回超過10%的記錄，則索引是有效的。
* 仔細選擇需要定義的索引。
* 請勿從現成可用的表中刪除本機索引。

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### 範例

管理索引可能變得非常複雜，因此，瞭解索引如何運作非常重要。 為了說明這種複雜性，我們以一個基本範例為例，例如透過篩選名字和姓氏來搜尋收件者。 操作步驟：
1. 轉到列出資料庫中所有收件人的資料夾。 有關詳細資訊，請參閱[管理配置檔案](../../platform/using/managing-profiles.md)。
1. 按一下右鍵&#x200B;**[!UICONTROL First name]**&#x200B;欄位。
1. 選取 **[!UICONTROL Filter on this field]**。

   ![](assets/data-model-index-example.png)

1. 對&#x200B;**[!UICONTROL Last name]**&#x200B;欄位重複此操作。

這兩個對應的濾鏡會新增至畫面的頂端。

![](assets/data-model-index-search.png)

您現在可以根據各種篩選條件，對&#x200B;**[!UICONTROL First name]**&#x200B;和&#x200B;**[!UICONTROL Last name]**&#x200B;欄位執行搜尋篩選。

現在，若要加速這些篩選器的搜尋，您可以新增索引。 但應該使用哪些索引？

>[!NOTE]
>
>此示例適用於使用PostgreSQL資料庫的托管客戶。

下表顯示了在哪些情況下，根據第一列中顯示的訪問模式使用或不使用下面所述的三個索引。

| 搜尋條件 | 索引1（名字+姓氏） | 索引2（僅名字） | 索引3（僅限姓氏） | 注釋 |
|--- |--- |--- |--- |--- |
| 名字等於&quot;強尼&quot; | 已使用 | 已使用 | 未使用 | 由於名字在索引1的第一位置，因此仍會使用它：無需在姓氏上添加標準。 |
| 名字等於&quot;Johnny&quot;，姓氏等於&quot;Smith&quot; | 已使用 | 未使用 | 未使用 | 由於同一查詢中同時搜索了兩個屬性，因此將只使用結合兩個屬性的索引。 |
| 姓氏等於&quot;Smith&quot; | 未使用 | 未使用 | 已使用 | 索引中的屬性順序被考慮在內。 如果您不符合此順序，則可能不會使用索引。 |
| 名字開頭為&quot;Joh&quot; | 已使用 | 已使用 | 未使用 | 「左搜索」將啟用索引。 |
| 名字結尾為&quot;ny&quot; | 未使用 | 未使用 | 未使用 | 「右搜索」將禁用索引，並執行完全掃描。 某些特定索引類型可處理此使用案例，但在Adobe Campaign，預設不提供。 |
| 名字包含&quot;John&quot; | 未使用 | 未使用 | 未使用 | 這是「左」和「右」搜尋的組合。 由於後者，它將禁用索引並執行完全掃描。 |
| 名字等於&quot;john&quot; | 未使用 | 未使用 | 未使用 | 索引區分大小寫。 要使其不區分大小寫，您應建立包含SQL函式(如「upper(firstname)」)的特定索引。 您應該對其他資料轉換(例如「unaccent(firstname)」)執行相同的動作。 |

## 連結和基數{#links-and-cardinality}

### 連結 {#links}

小心大桌上的「自己」誠信。 刪除具有「擁有」完整性的寬表的記錄可以停止實例。 表被鎖定，刪除操作逐個執行。 因此，最好對具有大卷的子表使用「中性」完整性。

將連結聲明為外部連接不利於效能。 零ID記錄模擬外部連接功能。 如果連結使用autopk，則無需聲明外部連接。

雖然可以在工作流中連接任何表，但Adobe建議直接在資料結構定義中定義資源之間的公共連結。

連結的定義應與表格中的實際資料一致。 錯誤的定義可能會影響透過連結擷取的資料，例如意外重複記錄。

以表名稱一致命名連結：連結名稱應有助於瞭解遠程表是什麼。

請勿將連結命名為「id」為尾碼。 例如，將其命名為&quot;transaction&quot;，而非&quot;transactionId&quot;。

預設情況下，Adobe Campaign將使用外部表的主鍵建立連結。 為了更清楚，最好在連結定義中明確定義連結。

索引將添加到連結中使用的屬性中。

The   「建立者」和「上次修改者」連結在許多表中都顯示。 如果業務未使用該資訊，則可以通過在連結上使用屬性noDbIndex來禁用該索引。

### 基數{#cardinality}

當您設計連結時，請確定目標籤錄在宣告1-1關係時是唯一的。 否則，當僅需要一條記錄時，連接可能會返回多個記錄。 這會在「查詢傳回的列比預期多」時，在傳送準備期間產生錯誤。 將連結名稱設定為與目標方案相同的名稱。

在架構(1)側定義具有基數(1-N)的連結。 例如，應在事務方案中定義關係收件人(1)-(N)事務。

請注意，連結的反向基數預設為(N)。 通過將屬性revCardinality=&#39;single&#39;添加到連結定義中，可以定義連結(1-1)。

如果使用者看不到反向連結，您可使用連結定義revLink=&#39;_NONE_&#39;來隱藏該連結。 例如，最好的使用案例是定義從收件者到最後完成交易的連結。 您只需查看從收件人到最後一個事務處理的連結，並且不需要從事務處理表中查看任何反向連結。

執行外部連接(1-0..1)的連結應小心使用，因為它將影響系統效能。

## 資料保留——清除和清除{#data-retention}

Adobe Campaign既不是資料倉庫，也不是報告工具。 因此，為了確保Adobe Campaign解決方案的良好效能，資料庫增長應保持在可控範圍內。 為達成此目的，請遵循下列一些最佳實務。

依預設，Adobe Campaign傳送和追蹤記錄檔的保留期為180天。 執行清除程式以刪除任何早於該進程的日誌。

* 如果希望將日誌保留更長時間，則應根據資料庫大小和發送的消息量仔細作出此決定。 提醒您，Adobe Campaign序列是32位元整數。
* 建議在這些表格中，每次不要有超過10億份記錄（21.4億個ID中的50%），以限制使用所有可用ID的風險。 這將要求某些客戶將保留期限降低到180天以下。

進一步瞭解[促銷活動隱私與安全性准則](https://helpx.adobe.com/tw/campaign/kb/campaign-privacy-overview.html#consent)中的資料保留。

在本節](../../production/using/database-cleanup-workflow.md)中進一步瞭解促銷活動資料庫清除工作流程[。

>[!IMPORTANT]
>
>自定義表不會使用標準清除流程進行清除。 雖然第一天可能不需要這個選項，但別忘了為自訂表格建立清除程式，因為這可能會導致效能挑戰。

有幾種解決方案可將Adobe Campaign記錄的需求降到最低：
* 將資料匯出至Adobe Campaign以外的資料倉庫。
* 產生匯整值，以節省空間，同時符合行銷實務。 例如，您不需要Adobe Campaign的完整客戶交易記錄，就能追蹤上次購買。

您可以在架構中宣告&quot;deleteStatus&quot;屬性。 將記錄標籤為已刪除，然後延遲清除任務中的刪除會更有效。

## 效能{#performance}

為了確保隨時都能提供更佳的效能，請遵循下列最佳實務。

### 一般性建議 {#general-recommendations}

* 請避免在查詢中使用「CONTAINS」等操作。 如果您知道要篩選的項目，請使用「EQUAL TO」或其他特定篩選運算子套用相同的條件。
* 在工作流程中建立資料時，請避免加入非索引欄位。
* 請試著確保在工作時間完成匯入和匯出等程式。
* 請確定所有日常活動都有排程，並遵守排程。
* 如果一個或幾個日進程失敗，並且如果強制在同一天運行該進程，請確保手動進程啟動時沒有運行衝突的進程，因為這可能影響系統效能。
* 請確定匯入程式期間或執行任何手動程式時，未執行任何每日促銷活動。
* 使用一或多個參考表，而不是在每一列中複製欄位。 使用鍵／值對時，最好選擇數字鍵。
* 短字串仍可接受。 如果引用表已在外部系統中就位，則重複使用表將有助於與Adobe Campaign的資料整合。

### 一對多關係{#one-to-many-relationships}

* 資料設計會影響可用性和功能。 如果您設計的資料模型具有許多一對多關係，使用者就很難在應用程式中建構有意義的邏輯。 一對多篩選邏輯對於不具備技術背景的行銷人員而言可能很難正確建構和理解。
* 將所有必要欄位都放在一個表格中是好事，因為這可讓使用者更輕鬆地建立查詢。 有時，如果在表中複製某些欄位，則避免連接也會對效能有好處。
* 某些內建功能將無法參考一對多關係，例如選件加權公式和傳送。

## 大表{#large-tables}

Adobe Campaign依賴第三方資料庫引擎。 根據提供方的不同，為較大的表優化效能可能需要特定的設計。

以下是使用大型表和複雜連接設計資料模型時應遵循的一些常見最佳做法。

* 使用其他自訂收件者表格時，請確定每個傳送對應都有專用的記錄表。
* 減少欄數，尤其是識別未使用的欄數。
* 通過避免複雜的連接（如多個條件和／或多個列上的連接）來優化資料模型關係。
* 對於連接鍵，請始終使用數字資料，而不是字串。
* 盡可能減少日誌保留深度。 如果您需要更深入的歷史記錄，您可以匯總計算和／或處理自訂的日誌表，以儲存較大的歷史記錄。

### 表大小{#size-of-tables}

表大小是記錄數和每個記錄列數的組合。 這兩種方法都會影響查詢的效能。

* **small-size**&#x200B;表與「傳送」表類似。
* **中等大小**&#x200B;表與Recipient表的大小相同。 每位客戶有一個記錄。
* **large-size**表與Broad日誌表類似。 每個客戶都有許多記錄。
例如，如果您的資料庫包含1000萬個收件者，「廣泛」記錄表包含約1億到2億條訊息，而「傳送」表則包含數千條記錄。

在PostgreSQL上，行不應超過8KB以避免[TOAST](https://wiki.postgresql.org/wiki/TOAST)機制。 因此，請盡量減少列數和每行的大小，以保留系統（記憶體和CPU）的最佳效能。

行數也會影響效能。 Adobe Campaign資料庫不是用於儲存不主動用於定位或個人化目的的歷史資料——這是一個操作資料庫。

要防止與行數較多相關的任何效能問題，請僅在資料庫中保存必要的記錄。 應將任何其他記錄導出到第三方資料倉庫，並從Adobe Campaign業務資料庫中刪除。

以下是關於表大小的一些最佳做法：

* 使用較少的欄位和更多數值資料，設計大型表格。
* 請勿使用大量的欄類型(例如：Int64)儲存小數字，例如布林值。
* 從表定義中刪除未使用的列。
* 請勿將歷史或非活動資料保留在您的Adobe Campaign資料庫（匯出和清除）中。

以下是範例：

![](assets/transaction-table-example.png)

在此範例中：
* *事務*&#x200B;和&#x200B;*事務項*&#x200B;表大：超過一千萬。
* *Product*&#x200B;和&#x200B;*Store*&#x200B;表較小：少於一萬。
* 產品標籤和參考已放在&#x200B;*Product*&#x200B;表中。
* *事務項*&#x200B;表只具有到&#x200B;*產品*&#x200B;表的連結，該表是數字的。

<!--For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).-->