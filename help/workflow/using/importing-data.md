---
title: 匯入資料
description: 瞭解如何在Adobe Campaign Classic中匯入資料
page-status-flag: never-activated
uuid: c8cf2bf1-f7a5-4de4-9e53-a961c9e5beca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: e53af1c2-b50c-4a8c-b5b8-f23a85bd3211
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e16d4de068f8cb1e61069aa53626f7bf7021466

---


# 匯入資料{#importing-data}

## 如何收集資料 {#how-to-collect-data}

### 使用清單中的資料：讀取清單 {#using-data-from-a-list--read-list}

在工作流中發送的資料可以來自清單，其中資料已事先準備並結構化。

此清單可能是直接在Adobe Campaign中建立，或是由選項匯 **[!UICONTROL Import a list]** 入。 For more on this option, refer to this [page](../../platform/using/generic-imports-and-exports.md).

有關在工作流中使用讀清單活動的詳細資訊，請參閱 [讀清單](../../workflow/using/read-list.md)。

### 從檔案載入資料 {#loading-data-from-a-file}

在工作流程中處理的資料可以從結構化檔案中擷取，以便匯入Adobe Campaign。

在「資料載入（檔案）」區段中，可找到載入資 [料活動的說明](../../workflow/using/data-loading--file-.md) 。

要導入的結構化檔案示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

### 在處理前解壓縮或解密檔案 {#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign可讓您匯入壓縮或加密的檔案。 在活動中讀取它們之 **[!UICONTROL Data loading (file)]** 前，您可以定義要解壓縮或解密檔案的預處理。

若要這麼做：

* 如果您的Adobe Campaign安裝是由Adobe代管：向Support(支 [持](https://support.neolane.net) )發送請求，要求在伺服器上安裝必要的實用程式。
* 如果您的Adobe Campaign安裝是在現場進行：安裝您要使用的實用程式(例如：GPG、GZIP)以及應用程式伺服器上的必要金鑰（加密金鑰）。

1. 在工作流程中新 **[!UICONTROL File transfer]** 增及設定活動。
1. 新增活 **[!UICONTROL Data loading (file)]** 動並定義檔案格式。
1. 勾選 **[!UICONTROL Pre-process the file]** 選項。
1. 指定要套用的預處理命令。 例如，要使用PGP解密檔案：

   ```
   <path-to_pgp_if-not_global_or_server/>pgp.exe --decrypt --input nl6/var/vp/import/filename.pgp --passphrase "your password" --recipient recipient @email.com --verbose --output nl6/var/vp/import/filename
   ```

1. 新增其他活動以管理來自檔案的資料。
1. 儲存並執行您的工作流程。

匯出檔案時，您也可以壓縮或加密檔案。 請參 [閱壓縮或加密檔案](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

## 匯入資料時的最佳實務 {#best-practices-when-importing-data}

謹慎並遵循下面詳述的幾個簡單規則，將有助於確保資料庫內的資料一致性，並避免在資料庫更新或資料匯出期間發生常見錯誤。

### 使用匯入範本 {#using-import-templates}

大部分的匯入工作流程應包含下列活動： **[!UICONTROL Data loading (file)]**, **[!UICONTROL Enrichment]****[!UICONTROL Split]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**。

使用匯入範本可讓您非常方便地準備類似的匯入，並確保資料庫中的資料一致性。 瞭解如何在「工作流程範本」區段中建 [立工作流程範本](../../workflow/using/building-a-workflow.md#workflow-templates) 。

在許多專案中，匯入建置時不 **[!UICONTROL Deduplication]** 會執行任何活動，因為專案中使用的檔案不會重複。 有時會從匯入不同的檔案中顯示重複項目。 因此，消除重複就很困難。 因此，重複資料消除步驟是所有導入工作流中的良好預防措施。

切勿假設傳入的資料是一致且正確的，或IT部門或Adobe Campaign主管負責處理。 在專案期間，請牢記資料清理。 在匯入資料時，可消除重複資料、進行協調並維持一致性。

「設定循環匯入」區段中提供 [了匯入範本範例](#setting-up-a-recurring-import) 。

### 使用平面檔案格式 {#using-flat-file-formats}

匯入時最有效的格式是平面檔案。 平面檔案可以在資料庫級別以批量模式導入。

例如：

* 分隔符號：制表符或分號
* 首行含標題
* 無字串分隔字元
* 日期格式：YYYY/MM/DD HH:mm:SS

Adobe Campaign無法使用標準檔案匯入活動匯入XML檔案。 您可以使用JavaScript匯入XML檔案，但只能使用小卷：每個檔案的記錄不到10K。

### 使用壓縮和加密 {#using-compression-and-encryption}

盡可能使用壓縮檔案進行匯入和匯出。

在Linux上，可以使用命令行解壓縮檔案並同時導入。 例如：

```
zcat nl6/var/vp/import/filename.gz
```

如果檔案不安全，則最好對通過網路發送的檔案進行加密。 GPG可以用於此。

### 從檔案批次載入資料 {#loading-data-in-batch-from-files}

從檔案批次載入資料比一次並即時載入一行資料（例如透過Web服務）更有效。

使用Web services匯入並不有效率。 最好盡可能使用檔案。

呼叫外部Web服務以即時豐富描述檔也會造成效能問題和記憶體流失，因為它可線上層級運作。

如果您需要匯入資料，最好是使用工作流程批次執行，而非使用Web應用程式或Web服務即時執行。

### 使用資料管理 {#using-data-management}

使用JavaScript以迭代模式（逐行）載入時，應限制為小卷。

為提高效率，請務必在資料管 **[!UICONTROL Data Loading (File)]** 理工作流程中使用活動。

### 在增量模式中導入 {#importing-in-delta-mode}

常規導入必須在delta模式下完成。 這表示每次只會傳送已修改或新資料至Adobe Campaign，而非整個表格。

完整匯入應僅用於初始載入。

使用資料管理而非JavaScript匯入資料。

### 維護一致性 {#maintaining-consistency}

若要維持Adobe Campaign資料庫中的資料一致性，請遵循下列原則：

* 如果匯入的資料與Adobe Campaign中的參考表格相符，則應與工作流程中的該表格協調。 不應拒絕不符合的記錄。
* 確保匯入的資料一律「 **標準化」** （電子郵件、電話號碼、直效郵件位址），而且此標準化是可靠的，多年來不會變更。 如果不是這樣，有些復本可能會出現在資料庫中，而Adobe Campaign不提供進行「模糊」比對的工具，因此很難管理和移除它們。
* 事務性資料應具有協調密鑰，並與現有資料協調以避免建立重複資料。
* **依順序匯入相關檔案**。

   如果匯入由多個彼此依存的檔案組成，工作流程應確保檔案的匯入順序正確。 檔案失敗時，不會導入其他檔案。

* **匯入資料**&#x200B;時，可以消除重複資料、進行協調並維持一致性。

## 設定循環匯入 {#setting-up-a-recurring-import}

如果您需要定期匯入具有相同結構的檔案，請使用匯入範本是最佳做法。

此範例說明如何預先設定可重複用於匯入來自Adobe Campaign資料庫中CRM的設定檔的工作流程。 如需每個活動所有可能設定的詳細資訊，請參閱本 [節](../../workflow/using/about-activities.md)。

1. 從中建立新的工作流模板 **[!UICONTROL Resources > Templates > Workflow templates]**。
1. 新增下列活動：

   * **[!UICONTROL Data loading (file)]**:定義包含要導入資料的檔案的預期結構。
   * **[!UICONTROL Enrichment]**:協調導入的資料與資料庫資料。
   * **[!UICONTROL Split]**:根據記錄是否可以調節，建立篩選器以不同方式處理記錄。
   * **[!UICONTROL Deduplication]**:在將傳入檔案插入資料庫之前，先從該檔案中消除重複資料。
   * **[!UICONTROL Update data]**:使用導入的配置檔案更新資料庫。
   ![](assets/import_template_example0.png)

1. 設定活 **[!UICONTROL Data Loading (file)]** 動：

   * 上傳範例檔案以定義預期的結構。 範例檔案應僅包含幾行，但是導入時需要的所有列。 檢查並編輯檔案格式，以確保每列的類型設定正確：文字、日期、整數等。 例如：

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * 在區 **[!UICONTROL Name of the file to load]** 段中，選 **[!UICONTROL Upload a file from the local machine]** 取並保留空白欄位。 每次從此模板建立新工作流時，您都可以在此處指定所需的檔案，只要該檔案與定義的結構相對應。

      您可以使用任何選項，但必須相應修改模板。 例如，如果您選 **[!UICONTROL Specified in the transition]**&#x200B;取，則可在 **[!UICONTROL File Transfer]** 擷取要從FTP/SFTP伺服器匯入的檔案之前新增活動。 有了S3或SFTP連線，您也可以使用Adobe即時客戶資料平台，將區段資料匯入Adobe Campaign。 For more on this, refer to this [documentation](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).

      ![](assets/import_template_example1.png)

1. 設定活 **[!UICONTROL Enrichment]** 動。 此活動的目的是識別傳入的資料。

   * 在標籤 **[!UICONTROL Enrichment]** 中，選 **[!UICONTROL Add data]** 取並定義匯入資料與收件者定位維度之間的連結。 在此範例中， **CRM ID** custom欄位用來建立連結條件。 只要您需要欄位或欄位組合，就能識別唯一記錄。
   * 在頁籤 **[!UICONTROL Reconciliation]** 中，將選項保留為未 **[!UICONTROL Identify the document from the working data]** 選中狀態。
   ![](assets/import_template_example2.png)

1. 設定活 **[!UICONTROL Split]** 動，以擷取一個轉場中已協調的收件者，以及在第二個轉場中無法協調但擁有足夠資料的收件者。

   然後，可以使用與已調節的收件人之間的轉換來更新資料庫。 然後，如果檔案中有一組最小資訊，則與未知收件人的轉換可用於在資料庫中建立新收件人條目。

   無法協調且沒有足夠資料的收件者會在補充的對外轉場中選取，並可匯出成個別檔案或略過。

   * 在活 **[!UICONTROL General]** 動的標籤中，選 **[!UICONTROL Use the additional data only]** 取為篩選設定，並確定 **[!UICONTROL Targeting dimension]** 自動設定為 **[!UICONTROL Enrichment]**。

      選中 **[!UICONTROL Generate complement]** 該選項可查看是否無法在資料庫中插入任何記錄。 如果需要，您可以對補充資料套用進一步的處理：檔案匯出、清單更新等。

   * 在標籤的第一個子集 **[!UICONTROL Subsets]** 中，在入站人口中添加過濾條件，以僅選擇收件者主鍵不等於0的記錄。 這樣，在該子集中選擇與資料庫收件人協調的檔案資料。

      ![](assets/import_template_example3.png)

   * 添加第二個子集，選擇具有足夠資料要插入到資料庫中的未協調記錄。 例如：電子郵件地址、名字和姓氏。

      子集按其建立順序進行處理，這意味著當處理此第二子集時，已存在於資料庫中的所有記錄都已在第一子集中選擇。

      ![](assets/import_template_example3_2.png)

   * 未在前兩個子集中選擇的所有記錄都在中選擇 **[!UICONTROL Complement]**。

1. 設定位 **[!UICONTROL Update data]** 於先前設定之活動首次出站轉 **[!UICONTROL Split]** 移後的活動。

   * 選 **[!UICONTROL Update]** 擇為 **[!UICONTROL Operation type]** ，因為入站轉換只包含資料庫中已存在的收件人。
   * 在區段 **[!UICONTROL Record identification]** 中，選 **[!UICONTROL Using reconciliation keys]** 取並定義定位維度與在中建立的連結之間的索引鍵 **[!UICONTROL Enrichment]**。 在此範例中，會 **使用CRM ID** custom欄位。
   * 在該部 **[!UICONTROL Fields to update]** 分中，指定收件人維中的欄位，以使用檔案中相應列的值進行更新。 如果檔案列的名稱與收件人維欄位的名稱相同或幾乎相同，則可以使用魔術棒按鈕自動匹配不同的欄位。

      ![](assets/import_template_example6.png)

1. 設定轉 **[!UICONTROL Deduplication]** 換後包含未協調收件者的活動：

   * 選 **[!UICONTROL Edit configuration]** 擇並將定位維設定為從工作流活動生成的 **[!UICONTROL Enrichment]** 臨時方案。

      ![](assets/import_template_example4.png)

   * 在此範例中，電子郵件欄位可用來尋找獨特的描述檔。 您可以使用任何您確定已填入的欄位，以及唯一組合的一部分。
   * 在螢幕 **[!UICONTROL Deduplication method]** 中，選 **[!UICONTROL Advanced parameters]** 擇並選中 **[!UICONTROL Disable automatic filtering of 0 ID records]** 選項，以確保主鍵為0的記錄（該記錄應為此轉換的所有記錄）未被排除。
   ![](assets/import_template_example7.png)

1. 設定先前 **[!UICONTROL Update data]** 設定之活動之 **[!UICONTROL Deduplication]** 後的活動。

   * 選 **[!UICONTROL Insert]** 擇為 **[!UICONTROL Operation type]** ，因為入站轉換只包含資料庫中不存在的收件人。
   * 在節 **[!UICONTROL Record identification]** 中，選 **[!UICONTROL Directly using the targeting dimension]** 擇並選擇 **[!UICONTROL Recipients]** 尺寸。
   * 在該部 **[!UICONTROL Fields to update]** 分中，指定收件人維中的欄位，以使用檔案中相應列的值進行更新。 如果檔案列的名稱與收件人維欄位的名稱相同或幾乎相同，則可以使用魔術棒按鈕自動匹配不同的欄位。

      ![](assets/import_template_example8.png)

1. 在活動的第三次轉 **[!UICONTROL Split]** 換後，如果要跟蹤未插入數 **[!UICONTROL Data extraction (file)]****[!UICONTROL File transfer]** 據庫的資料，請添加活動和活動。 設定這些活動，以匯出您需要的欄，並在FTP或SFTP伺服器上傳輸檔案，您可在其中擷取該欄。
1. 新增活 **[!UICONTROL End]** 動並儲存工作流程範本。

範本現在可以使用，而且適用於每個新的工作流程。 然後，需要全部指定包含要在活動中導入的資料的文 **[!UICONTROL Data loading (file)]** 件。

![](assets/import_template_example9.png)

