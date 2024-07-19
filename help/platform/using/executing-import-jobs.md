---
product: campaign
title: 設定匯入工作
description: 瞭解如何在Campaign中設定並執行匯入作業
feature: Overview
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 05909ea6-2c93-42ff-9142-1dd14fa6fdec
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '2973'
ht-degree: 34%

---

# 設定匯入作業 {#executing-import-jobs}



Adobe Campaign可讓您以文字、CSV、TAB或XML格式，從一或多個檔案將資料匯入資料庫。 這些檔案與表 (主要或連結) 相關聯，並且源檔的每個欄位與資料庫的欄位相關聯。

>[!NOTE]
>
>您可以使用&#x200B;**[!UICONTROL Import a list]**&#x200B;函式，匯入資料時不必與資料庫資料對應。 然後可透過&#x200B;**[!UICONTROL Read list]**&#x200B;物件將資料僅用於工作流程中。 如需詳細資訊，請參閱[此頁面](../../workflow/using/read-list.md)。

匯入精靈可讓您設定匯入、定義其選項（例如資料轉換）並啟動執行。 它是一系列屏幕，其內容取決於匯入類型 (簡單或多個) 和操作員權限。

建立新的匯入工作後，匯入精靈便會顯示（請參閱[建立匯入和匯出工作](../../platform/using/creating-import-export-jobs.md)）。

>[!NOTE]
>
>如果您使用IIS網頁伺服器，可能需要設定以授權上傳大型檔案(>28 MB)。 如需詳細資訊，請參閱[本區段](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit)。

## 來源檔案 {#source-file}

在來源檔案中，每一行都與記錄一致。 記錄中的資料以分隔符號（空格、定位字元、字元等）分隔。 這意味著以行的形式檢索資料，並且每行與資料庫的欄位相關聯。

## 步驟1 — 選擇匯入範本 {#step-1---choosing-the-import-template}

啟動匯入精靈時，您必須先選取範本。 例如，要配置收到簡報的收件者的匯入，請按照以下步驟操作：

1. 選取&#x200B;**[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**&#x200B;資料夾。
1. 點擊&#x200B;**新建**，然後點擊&#x200B;**匯入**&#x200B;以建立匯入範本。

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. 按一下&#x200B;**[!UICONTROL Import template]**&#x200B;欄位右側的箭頭以選取您的範本，或按一下&#x200B;**[!UICONTROL Select link]**&#x200B;以瀏覽樹狀結構。

   原生範本為&#x200B;**[!UICONTROL New text import]**。 此範本不得修改，但您可以複製此範本，以根據您的需求設定新範本。 匯入範本預設會儲存在&#x200B;**[!UICONTROL Profiles and targets > Templates > Job templates]**&#x200B;節點中。

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入此匯入的名稱。 您可以添加描述。
1. 在適當的欄位中選取匯入型別。 有兩種可能的匯入型別： **[!UICONTROL Simple import]**&#x200B;僅匯入一個檔案，以及&#x200B;**[!UICONTROL Multiple import]**&#x200B;在單一執行中匯入多個檔案。

   若要多重匯入，請從匯入精靈的第一個畫面中的&#x200B;**[!UICONTROL Import type]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Multiple import]**。

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以指定要匯入的欄位。

   ![](assets/s_ncs_user_import_wizard01_3.png)

   每次新增檔案時，都會顯示&#x200B;**[!UICONTROL File to import]**&#x200B;精靈的畫面。 請參閱區段[步驟2 - Source檔案選擇](#step-2---source-file-selection)，並依照精靈中的步驟將匯入選項定義為簡單匯入。

   >[!NOTE]
   >
   >多次匯入應僅滿足特定需求，不建議使用。

### 高級參數 {#advanced-parameters}

**[!UICONTROL Advanced parameters]**&#x200B;連結可讓您存取下列選項：

* **[!UICONTROL General]**&#x200B;索引標籤

   * **[!UICONTROL Stop execution if there are too many rejects]**

     依預設，會選取此選項。 如果您想要繼續執行匯入（無論拒絕次數為何），可以取消選取它。 按照預設，如果拒絕前100行，則停止執行。

   * **[!UICONTROL Trace mode]**

     選擇此選項可追蹤每行的匯入執行情況。

   * **[!UICONTROL Start the job in a detached process]**

     依預設，會選取此選項。 它允許您分離匯入的執行，以便它不會影響資料庫中正在進行的其他作業。

   * **[!UICONTROL Do not update enumerations]**

     選取此選項可避免擴充資料庫中的列舉值清單。 請參閱[管理分項清單](../../platform/using/managing-enumerations.md)。

* **[!UICONTROL Variables]**&#x200B;索引標籤

  您可以定義與作業關聯的變數，這些變數可在查詢編輯器和計算欄位中存取。 若要建立變數，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;並使用變數編輯器。

  >[!IMPORTANT]
  >
  >**[!UICONTROL Variables]**&#x200B;索引標籤僅供工作流程型別程式設計使用，且僅應由專家使用者設定。

## 第 2 步 - 源檔選擇 {#step-2---source-file-selection}

源檔可以是文字格式 (txt、csv、tab、固定行) 或 xml。

預設會選取&#x200B;**[!UICONTROL Upload file on the server]**。 按一下&#x200B;**[!UICONTROL Local file]**&#x200B;欄位右側的資料夾，以瀏覽本機磁碟並選取要匯入的檔案。 您可以取消選擇此選項以輸入存取路徑以及要在伺服器上匯入的檔案名稱。

![](assets/s_ncs_user_import_wizard02_1.png)

指定檔案後，您可以按一下&#x200B;**[!UICONTROL Auto-detect format]**，在視窗的下半部檢視其資料。 此預覽顯示源檔案的前 200 行。

![](assets/s_ncs_user_import_wizard02_2.png)

使用此檢視上方提供的選項來設定匯入。 透過這些選項定義的引數會傳輸到預覽中。 可以使用以下選項：

* **[!UICONTROL Click here to change the file format...]**&#x200B;可讓您檢查檔案格式並微調組態。
* **[!UICONTROL Update on server...]**&#x200B;可讓您將本機檔案傳輸至伺服器。 只有在選取&#x200B;**[!UICONTROL Upload file on the server]**&#x200B;時，才能使用此選項。
* **[!UICONTROL Download]**&#x200B;只有在檔案已上傳至伺服器時才可使用。
* **[!UICONTROL Auto-detect format]**&#x200B;用來重新初始化資料來源的格式。 此選項可讓您將原始格式重新套用至已透過&#x200B;**[!UICONTROL Click here to change the file format...]**&#x200B;選項格式化的資料。
* **[!UICONTROL Advanced parameters]**&#x200B;連結可讓您篩選來源資料並存取進階選項。 在此熒幕中，您可以選擇僅匯入檔案的一部分。 您也可以定義篩選器，例如根據對應行的值，僅匯入「Prospect」或「Customer」型別的使用者。 這些選項僅供專業 JavaScript 用戶使用。

### 變更檔案格式 {#changing-the-file-format}

**[!UICONTROL Click here to change the file format...]**&#x200B;選項可讓您格式化來源檔案的資料，尤其是指定欄分隔符號和每個欄位的資料型別。 此配置通過以下視窗執行：

![](assets/s_ncs_user_import_wizard02_3.png)

此步驟可讓您說明應如何讀取檔案欄位的值。 例如，若是日期，日期或日期+時間資料可能與格式（dd/mm/yyyy、mm/dd/yy等）相關聯。 如果輸入資料與預期格式不匹配，則在匯入期間將發生拒絕。

您可以在視窗下部的預覽區欄位中查看配置結果。

按一下&#x200B;**[!UICONTROL OK]**&#x200B;儲存格式，然後按一下&#x200B;**[!UICONTROL Next]**&#x200B;顯示下一步。

## 第 3 步 - 欄位對應 {#step-3---field-mapping}

然後，您必須選擇目標架構並將每行的資料對應到資料庫中的欄位。

![](assets/s_ncs_user_import_wizard03_1.png)

* **[!UICONTROL Destination schema]**&#x200B;欄位可讓您選取要匯入資料的結構描述。 此資訊為必填。 按一下&#x200B;**[!UICONTROL Select link]**&#x200B;圖示以選取其中一個現有結構描述。 按一下&#x200B;**[!UICONTROL Edit link]**&#x200B;以顯示所選資料表的內容。
* 中央表格會顯示來源檔案中定義的所有欄位。 選取要匯入的欄位，以將目的地檔案與其建立關聯。 可以手動或自動對應這些欄位。

  若要手動對應欄位，請按一下核取方塊以選取來源欄位，然後按一下第二欄以啟動與所選欄位相對應的儲存格。 接著，按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;圖示以顯示目前表格的所有欄位。 選取目的地欄位並按一下&#x200B;**[!UICONTROL OK]**&#x200B;以驗證對應。

  若要自動關聯來源欄位和目的地欄位，請按一下欄位清單右側的&#x200B;**[!UICONTROL Guess the destination fields]**&#x200B;圖示。 如果需要，可以修改建議的欄位。

  >[!IMPORTANT]
  >
  >在繼續執行下一步之前，必須始終驗證此操作的結果。

* 您可以將轉換套用至匯入的欄位。 若要這麼做，請按一下與相關欄位相關的&#x200B;**[!UICONTROL Transformation]**&#x200B;欄儲存格，然後選取要套用的轉換。

  ![](assets/s_ncs_user_import_wizard03_2.png)

  >[!IMPORTANT]
  >
  >轉換會在匯入時套用。 但是，如果已定義了對目標欄位的約束 (在上面的示例中為 @lastname 欄位)，則這些約束優先。

* 您可以使用位於中央表格右側的適當圖示來新增計算欄位。 計算欄位可讓您執行複雜的轉換、新增虛擬欄或合併多個欄的資料。 有關各種可能性的詳細資訊，請參見以下部分。

### 計算欄位 {#calculated-fields}

計算欄位是指新增至來源檔案的新欄，以及從其他欄計算。 計算欄位隨後可與Adobe Campaign資料庫的欄位建立關聯。 但是，在計算欄位中無法進行對帳操作。

有四種類型的計算欄位：

* **[!UICONTROL Fixed string]**：來源檔案的所有行，計算欄位的值都相同。 可讓您設定插入或更新之記錄的欄位值。 例如，您可以為所有匯入的記錄將標記設置為「是」。
* **[!UICONTROL String with JavaScript tags]**：計算欄位的值是包含JavaScript命令的字元字串。
* **[!UICONTROL JavaScript expression]**：計算欄位的值是JavaScript函式評估的結果。 返回的值可以是數字、日期等。
* **[!UICONTROL Enumeration]**：欄位的值是根據來源檔案中包含的值所歸因。 編輯器允許您指定源行並輸入枚舉值清單，如以下示例所示：

  ![](assets/s_ncs_user_import_wizard03_3.png)

  **[!UICONTROL Preview]**&#x200B;索引標籤可讓您檢視已定義組態的結果。 已在此新增&#x200B;**[!UICONTROL Subscription]**&#x200B;欄。 該值計算自&#x200B;**狀態**&#x200B;欄位。

  ![](assets/s_ncs_user_import_wizard03_4.png)

## 第 4 步 – 調解 {#step-4---reconciliation}

匯入精靈的調解步驟可讓您定義從檔案中調解資料與資料庫中現有資料的模式，並設定檔案資料與資料庫資料之間的優先順序規則。 配置視窗如下所示：

![](assets/s_ncs_user_import_wizard04_1.png)

屏幕的中央部分包含一個樹結構，其中包含要匯入資料的 Adobe Campaign 資料庫的欄位和表。

每個節點（表格或欄位）都有特殊選項可用。 當您按一下清單中相關的節點時，其引數和簡短說明會顯示在下方。 為每個元素定義的行為會顯示在對應的&#x200B;**[!UICONTROL Behavior]**&#x200B;欄中。

![](assets/s_ncs_user_import_wizard04_2.png)

### 操作類型 {#types-of-operation}

對於匯入涉及的每個表格，您必須定義作業型別。 以下操作可用於資料庫的主要元素：

* **[!UICONTROL Update or insertion]**：如果記錄存在於資料庫中，則更新記錄，否則建立記錄。
* **[!UICONTROL Insertion]**：將記錄插入資料庫。
* **[!UICONTROL Update]**：僅更新現有記錄（忽略其他記錄）。
* **[!UICONTROL Reconciliation only]**：在資料庫中尋找記錄，但未執行更新。 例如，允許您根據檔案行關聯要匯入的收件者資料夾，而不更新資料夾中的資料。
* **[!UICONTROL Deletion]**：可讓您銷毀資料庫中的記錄。

匯入所涉及的表中的每個欄位都有以下選項：

* **[!UICONTROL Update (empty) if source value is empty]**：在更新事件中，如果來源檔案中的欄位為空，則欄位中的值將會移除資料庫值。 否則，保留資料庫欄位。
* **[!UICONTROL Update only if destination is empty]**：除非資料庫欄位是空的，否則來源檔案中的值不會覆寫資料庫欄位中的值。 在這種情況下，它採用源檔的值。
* **[!UICONTROL Update the field only when the record is inserted]**：在更新或插入作業期間，只會匯入新的來源檔案記錄。

>[!NOTE]
>
>除非在沒有重複資料刪除的情況下插入，否則調解金鑰的定義始終是&#x200B;**必需的**。

### 調解金鑰 {#reconciliation-keys}

必須至少填寫一個調解金鑰才能管理重複資料刪除。

調解金鑰是用於識別記錄的一組欄位。 例如，若要匯入收件者，調解金鑰可以是帳號、「電子郵件」欄位或「姓氏、名字、公司」欄位等。

在此情況下，為了找出檔案的一行是否符合資料庫中的現有收件者，匯入引擎會比較檔案的值與資料庫中索引鍵所有欄位的值。 當欄位是記錄專屬時，可以執行來源和目的地資料之間的精細比較，以確保匯入後資料的完整性。 可以為同一個表填寫第二個調解金鑰；它用於第一個金鑰為空的行。

避免選擇在匯入期間可能被修改的欄位；如果發生這種情況，引擎可以建立其他記錄。

![](assets/s_ncs_user_import_wizard04_3.png)

>[!NOTE]
>
>對於收件者匯入，所選資料夾的標識符將隱含地添加到金鑰中。
>
>因此，僅對此資料夾執行調解 (除非未選擇資料夾)。

### 去重複化 {#deduplication}

>[!NOTE]
>
>「兩次」是在要匯入的檔案中存在兩次或更多次的項目。
>
>「重複」是同時存在於要匯入的檔案和資料庫中的項目。

**[!UICONTROL Management of doubles]**&#x200B;欄位可讓您設定重複資料刪除。 重複資料刪除涉及&#x200B;**在源檔中**&#x200B;多次出現的記錄 (或多檔案匯入時的源檔)，即調解金鑰的欄位相同的行。

* 在&#x200B;**[!UICONTROL Update]**&#x200B;模式（預設模式）下的重複資料刪除管理不會執行重複資料刪除。 因此，最後的記錄具有優先權（因為它會更新先前記錄的資料）。 在此模式下不執行重複計數。
* 在&#x200B;**[!UICONTROL Ignore]**&#x200B;模式或&#x200B;**[!UICONTROL Reject entity]**&#x200B;中的重複管理會排除匯入中的重複專案。 在這種情況下，不會匯入任何記錄。
* 在&#x200B;**[!UICONTROL Reject entity]**&#x200B;模式中，不會匯入元素，而且匯入記錄檔中會產生錯誤。
* 在&#x200B;**[!UICONTROL Ignore]**&#x200B;模式中，未匯入元素，但並未保留任何錯誤追蹤。 此模式可讓您優化性能。

>[!IMPORTANT]
>
>重複資料刪除僅在記憶體中執行。 因此，具有重複資料刪除之匯入的大小會受到限制。 此限制取決於幾個引數（應用程式伺服器的容量、活動、索引鍵中的欄位數等）。 重複資料刪除的最大大小為 1,000,000 行。

重複資料刪除涉及同時存在於來源檔案和資料庫中的記錄。 它只與更新有關的作業（亦即&#x200B;**[!UICONTROL Update and insertion]**&#x200B;或&#x200B;**[!UICONTROL Update]**）。 **[!UICONTROL Duplicate management]**&#x200B;選項可讓您更新或忽略記錄（如果記錄同時位於來源檔案和資料庫中）。 **[!UICONTROL Update or insert based on origin]**&#x200B;選項屬於選擇性模組，無法用於標準內容。

選項&#x200B;**[!UICONTROL Reject]**&#x200B;和&#x200B;**[!UICONTROL Ignore]**&#x200B;的運作方式如上所示。

### 發生錯誤時 {#behavior-in-the-event-of-an-error}

大部分的資料傳輸作業會產生各種型別的錯誤（不一致的行格式、無效的電子郵件地址等）。 匯入引擎生成的所有錯誤和所有警告都將儲存並連結到匯入執行個體。

![](assets/s_ncs_user_import_general_tab.png)

您可以透過&#x200B;**[!UICONTROL Rejects]**&#x200B;索引標籤檢視這些拒絕的詳細資料。

![](assets/s_ncs_user_import_rejets_tab.png)

拒絕有兩種型別（型別會顯示在&#x200B;**[!UICONTROL Connector]**&#x200B;欄中）：

* 拒絕文字聯結器與處理檔案行時發生的錯誤有關（計算欄位、資料分析等）。 在這種情況下，如果發生錯誤，則始終拒絕整行。
* 資料庫聯結器拒絕與資料協調或寫入資料庫期間發生的錯誤有關。 在匯入到多個表的情況下，拒絕只涉及記錄的一部分 (例如，對於收件者和相關事件的匯入，錯誤可以阻止更新事件而不拒絕接收者)。

在資料調解頁面中，您可以按欄位和逐個表定義所需的錯誤管理類型欄位。

* **[!UICONTROL Ignore and log a warning]**：所有欄位都已匯入資料庫，但產生錯誤的欄位除外。
* **[!UICONTROL Reject parent element]**：記錄的整行被拒絕，而不僅僅是造成錯誤的欄位。
* **[!UICONTROL Reject all elements]**：匯入停止，且記錄的所有元素都遭到拒絕。

  ![](assets/s_ncs_user_import_wizard04_4.png)

匯入執行個體的拒絕屏幕中的樹結構指示哪些欄位被拒絕以及錯誤發生的位置。

您可以透過&#x200B;**[!UICONTROL Export rejects]**&#x200B;圖示產生包含這些記錄的檔案：

![](assets/s_ncs_user_import_errors_export.png)

## 第 5 步 - 匯入收件者時的附加步驟 {#step-5---additional-step-when-importing-recipients}

匯入精靈的下一步允許您選擇或建立將匯入資料的資料夾，自動將匯入的收件者對應於 (新的或現有的) 清單，並將收件者訂閱到服務。

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>在僅匯入收件者時以及使用預設的 Adobe Campaign 收件者表 (**nms:recipient**) 時，將顯示此步驟。

* 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;連結以選取資料夾、清單，或您要與收件者建立關聯或訂閱的服務。

   1. 匯入到資料夾中

      **[!UICONTROL Import into a folder]**&#x200B;區段的&#x200B;**[!UICONTROL Edit...]**&#x200B;連結可讓您選取或建立收件者將匯入的資料夾。 按照預設，如果未定義分區，則會將資料匯入到操作員的預設資料夾中。

      >[!NOTE]
      >
      >運運算元的預設資料夾是該運運算元具有寫入許可權的第一個資料夾。 深入瞭解[資料夾存取管理](../../platform/using/access-management-folders.md)。

      若要選取匯入資料夾，請按一下&#x200B;**[!UICONTROL Folder]**&#x200B;欄位右側的箭頭，然後選取相關的資料夾。 您也可以使用&#x200B;**[!UICONTROL Select link]**&#x200B;圖示在新視窗中顯示樹狀結構或建立新資料夾。

      ![](assets/s_ncs_user_import_wizard05_2.png)

      若要建立新資料夾，請選取您要新增資料夾的節點，然後按一下滑鼠右鍵。 選取 **[!UICONTROL Create a new 'Recipients' folder]**。

      ![](assets/s_ncs_user_import_wizard05_3.png)

      資料夾會新增至目前節點下方。 輸入新資料夾的名稱，按一下Enter進行確認，然後按一下&#x200B;**[!UICONTROL OK]**。

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. 與清單相關聯

      **[!UICONTROL Add recipients to a list]**&#x200B;區段中的&#x200B;**[!UICONTROL Edit...]**&#x200B;連結可讓您選取或建立收件者將匯入其中的清單。

      ![](assets/s_ncs_user_import_wizard05_5.png)

      您可以按一下&#x200B;**[!UICONTROL Select link]**，然後按&#x200B;**[!UICONTROL Create]**，為這些收件者建立新清單。 清單的建立和管理會顯示在[本節](../../platform/using/creating-and-managing-lists.md)中。

      ![](assets/s_ncs_user_import_wizard05_6.png)

      您可以決定將收件者新增至清單中已存在的收件者，或使用新收件者重新建立清單。 在這種情況下，如果清單已包含收件者，則它們將被刪除並由匯入的收件者替換。

   1. 訂閱服務

      若要讓所有匯入的收件者訂閱資訊服務，請按一下&#x200B;**[!UICONTROL Subscribe recipients to a service]**&#x200B;區段的&#x200B;**[!UICONTROL Edit...]**&#x200B;連結，以選取或建立收件者將訂閱的資訊服務。 您可以選取&#x200B;**[!UICONTROL Send a confirmation message]**&#x200B;選項：此訊息的內容定義在與訂閱服務相關聯的傳遞範本中。

      ![](assets/s_ncs_user_import_wizard05_7.png)

      您可以按一下&#x200B;**[!UICONTROL Select link]**，然後按一下&#x200B;**[!UICONTROL Create]**&#x200B;圖示，為這些收件者建立新的服務。 [本節](../../delivery/using/managing-subscriptions.md)介紹了資訊服務的管理。

* 使用&#x200B;**[!UICONTROL Origin]**&#x200B;欄位將收件者來源的相關資訊新增至其設定檔。 此資訊在多重匯入的框架內特別有用。

按一下&#x200B;**[!UICONTROL Next]**&#x200B;以驗證此步驟並顯示下列步驟。

## 步驟6 — 啟動匯入 {#step-6---launching-the-import}

精靈的最後一步可讓您啟動資料匯入。 若要這麼做，請按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕。

![](assets/s_ncs_user_import_wizard06_1.png)

然後，您可以監視匯入工作的執行（請參閱[監視工作的執行](../../platform/using/monitoring-jobs-execution.md)）。
