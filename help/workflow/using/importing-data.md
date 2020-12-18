---
solution: Campaign Classic
product: campaign
title: 匯入資料
description: 瞭解如何匯入Adobe Campaign中的資料
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '2476'
ht-degree: 1%

---


# 匯入資料{#importing-data}

>[!CAUTION]
>
>匯入資料時，請記住SFTP儲存、資料庫儲存和作用中的設定檔限制，如您的Adobe Campaign合約所定。

## 如何收集資料{#how-to-collect-data}

### 使用清單中的資料：讀取清單{#using-data-from-a-list--read-list}

在工作流中發送的資料可以來自清單，其中資料已事先準備並結構化。

此清單可能是直接在Adobe Campaign中建立或由&#x200B;**[!UICONTROL Import a list]**&#x200B;選項匯入。 有關此選項的詳細資訊，請參閱此[頁](../../platform/using/generic-imports-and-exports.md)。

有關在工作流中使用讀清單活動的詳細資訊，請參閱[讀清單](../../workflow/using/read-list.md)。

### 從檔案{#loading-data-from-a-file}載入資料

在工作流程中處理的資料可以從結構化檔案中擷取，以便匯入Adobe Campaign。

在[資料載入（檔案）](../../workflow/using/data-loading--file-.md)區段中可找到載入資料活動的說明。

要導入的結構化檔案示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 匯入資料{#best-practices-when-importing-data}時的最佳實務

謹慎並遵循下面詳述的幾個簡單規則，將有助於確保資料庫內的資料一致性，並避免在資料庫更新或資料匯出期間發生常見錯誤。

### 使用導入模板{#using-import-templates}

大部分的匯入工作流程應包含下列活動：**[!UICONTROL Data loading (file)]**、**[!UICONTROL Enrichment]**、**[!UICONTROL Split]**、**[!UICONTROL Deduplication]**、**[!UICONTROL Update data]**。

使用匯入範本可讓您非常方便地準備類似的匯入，並確保資料庫中的資料一致性。 瞭解如何在[Workflow templates](../../workflow/using/building-a-workflow.md#workflow-templates)區段中建立工作流程範本。

在許多項目中，導入是在沒有&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動的情況下構建的，因為項目中使用的檔案沒有重複項。 有時會從匯入不同的檔案中顯示重複項目。 因此，消除重複就很困難。 因此，重複資料消除步驟是所有導入工作流中的良好預防措施。

切勿假設傳入的資料是一致且正確的，或IT部門或Adobe Campaign主管負責處理。 在專案期間，請牢記資料清理。 在匯入資料時，可以消除重複資料、進行協調並維持一致性。

[設定循環匯入](#setting-up-a-recurring-import)區段中提供匯入範本範例。

### 使用平面檔案格式{#using-flat-file-formats}

匯入時最有效的格式是平面檔案。 平面檔案可以在資料庫級別以批量模式導入。

例如：

* 分隔符號：制表符或分號
* 首行含標題
* 無字串分隔字元
* 日期格式：YYYY/MM/DD HH:mm:SS

Adobe Campaign無法使用標準檔案匯入活動匯入XML檔案。 您可以使用JavaScript匯入XML檔案，但只能使用小卷：每個檔案的記錄不到10K。

### 使用壓縮和加密{#using-compression-and-encryption}

盡可能使用壓縮檔案進行匯入和匯出。

在Linux上，可以使用命令行解壓縮檔案並同時導入。 例如：

```
zcat nl6/var/vp/import/filename.gz
```

如果檔案不安全，則最好對通過網路發送的檔案進行加密。 GPG可以用於此。

### 從檔案{#loading-data-in-batch-from-files}中批次載入資料

從檔案批次載入資料比一次並即時載入一行資料（例如透過Web服務）更有效。

使用Web services匯入並不有效率。 最好盡可能使用檔案。

呼叫外部Web服務以即時豐富描述檔也會造成效能問題和記憶體流失，因為它可在行層級運作。

如果您需要匯入資料，最好是使用工作流程批次執行，而非使用Web應用程式或Web服務即時執行。

### 使用資料管理{#using-data-management}

使用JavaScript以迭代模式（逐行）載入時，應限制為小卷。

為提高效率，請務必在資料管理工作流程中使用&#x200B;**[!UICONTROL Data Loading (File)]**&#x200B;活動。

### 在增量模式下導入{#importing-in-delta-mode}

常規導入必須在delta模式下完成。 這表示每次只會傳送已修改或新資料至Adobe Campaign，而非整個表格。

完整匯入應僅用於初始載入。

使用資料管理而非JavaScript匯入資料。

### 維持一致性{#maintaining-consistency}

若要維持Adobe Campaign資料庫中的資料一致性，請遵循下列原則：

* 如果匯入的資料與Adobe Campaign中的參考表格相符，則應與工作流程中的該表格協調。 不應拒絕不符合的記錄。
* 請確定匯入的資料一律是&#x200B;**「已標準化」**（電子郵件、電話號碼、直接郵件位址），且此標準化是可靠的，多年內不會變更。 如果不是這樣，有些復本可能會出現在資料庫中，而Adobe Campaign不提供進行「模糊」比對的工具，因此很難管理和移除它們。
* 事務性資料應具有協調密鑰，並與現有資料協調以避免建立重複資料。
* **依順序匯入相關檔案**。

   如果匯入由多個彼此依存的檔案組成，工作流程應確保檔案的匯入順序正確。 檔案失敗時，不會導入其他檔案。

* **匯入資料**&#x200B;時，可以消除重複資料、進行協調並維持一致性。

## 使用案例：設定循環導入{#setting-up-a-recurring-import}

如果您需要定期匯入具有相同結構的檔案，請使用匯入範本是最佳做法。

此範例說明如何預先設定可重複用於匯入來自Adobe Campaign資料庫中CRM的設定檔的工作流程。 有關每個活動的所有可能設定的詳細資訊，請參閱此[部分](../../workflow/using/about-activities.md)。

1. 從&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;建立新的工作流程範本。
1. 新增下列活動：

   * **[!UICONTROL Data loading (file)]**:定義包含要導入資料的檔案的預期結構。
   * **[!UICONTROL Enrichment]**:協調導入的資料與資料庫資料。
   * **[!UICONTROL Split]**:根據記錄是否可以調節，建立篩選器以不同方式處理記錄。
   * **[!UICONTROL Deduplication]**:在將傳入檔案插入資料庫之前，先從該檔案中消除重複資料。
   * **[!UICONTROL Update data]**:使用導入的配置檔案更新資料庫。

   ![](assets/import_template_example0.png)

1. 配置&#x200B;**[!UICONTROL Data Loading (file)]**&#x200B;活動：

   * 上傳範例檔案以定義預期的結構。 範例檔案應僅包含幾行，但是導入時需要的所有列。 檢查並編輯檔案格式，以確保每列的類型設定正確：文字、日期、整數等。 例如：

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * 在&#x200B;**[!UICONTROL Name of the file to load]**&#x200B;區段中，選擇&#x200B;**[!UICONTROL Upload a file from the local machine]**&#x200B;並將欄位留空。 每次從此模板建立新工作流時，您都可以在此處指定所需的檔案，只要該檔案與定義的結構相對應。

      您可以使用任何選項，但必須相應修改模板。 例如，如果您選擇&#x200B;**[!UICONTROL Specified in the transition]**，則可以先添加&#x200B;**[!UICONTROL File Transfer]**&#x200B;活動，然後再檢索要從FTP/SFTP伺服器導入的檔案。 有了S3或SFTP連線，您也可以使用Adobe即時客戶資料平台，將區段資料匯入Adobe Campaign。 有關詳細資訊，請參閱[文檔](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)。

      ![](assets/import_template_example1.png)

1. 設定&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動。 此活動的目的是識別傳入的資料。

   * 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL Add data]**&#x200B;並定義匯入資料與收件者定位維度之間的連結。 在此範例中，**CRM ID**&#x200B;自訂欄位用於建立連結條件。 只要您需要欄位或欄位組合，就能識別唯一記錄。
   * 在&#x200B;**[!UICONTROL Reconciliation]**&#x200B;標籤中，保留&#x200B;**[!UICONTROL Identify the document from the working data]**&#x200B;選項未選中。

   ![](assets/import_template_example2.png)

1. 設定&#x200B;**[!UICONTROL Split]**&#x200B;活動，以擷取一個轉場中已協調的收件者，以及在第二個轉場中無法協調但擁有足夠資料的收件者。

   然後，可以使用與已調節的收件人之間的轉換來更新資料庫。 然後，如果檔案中有一組最小資訊，則與未知收件人的轉換可用於在資料庫中建立新收件人條目。

   無法協調且沒有足夠資料的收件者會在補充的對外轉場中選取，並可匯出成個別檔案或略過。

   * 在活動的&#x200B;**[!UICONTROL General]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL Use the additional data only]**&#x200B;作為篩選設定，並確保&#x200B;**[!UICONTROL Targeting dimension]**&#x200B;自動設定為&#x200B;**[!UICONTROL Enrichment]**。

      選中&#x200B;**[!UICONTROL Generate complement]**&#x200B;選項，可查看是否無法在資料庫中插入任何記錄。 如果需要，您可以對補充資料套用進一步的處理：檔案匯出、清單更新等。

   * 在&#x200B;**[!UICONTROL Subsets]**&#x200B;標籤的第一個子集中，在入站人口中添加過濾條件，以僅選擇收件者主鍵不等於0的記錄。 這樣，在該子集中選擇與資料庫收件人協調的檔案資料。

      ![](assets/import_template_example3.png)

   * 添加第二個子集，選擇具有足夠資料要插入到資料庫中的未協調記錄。 例如：電子郵件地址、名字和姓氏。

      子集按其建立順序進行處理，這意味著當處理此第二子集時，已存在於資料庫中的所有記錄都已在第一子集中選擇。

      ![](assets/import_template_example3_2.png)

   * 在&#x200B;**[!UICONTROL Complement]**&#x200B;中選擇前兩個子集中未選擇的所有記錄。

1. 配置位於先前配置的&#x200B;**[!UICONTROL Split]**&#x200B;活動首次出站轉移後的&#x200B;**[!UICONTROL Update data]**&#x200B;活動。

   * 選擇&#x200B;**[!UICONTROL Update]**&#x200B;作為&#x200B;**[!UICONTROL Operation type]** ，因為入站過渡僅包含資料庫中已存在的收件人。
   * 在&#x200B;**[!UICONTROL Record identification]**&#x200B;區段中，選擇&#x200B;**[!UICONTROL Using reconciliation keys]**&#x200B;並定義定位維度與在&#x200B;**[!UICONTROL Enrichment]**&#x200B;中建立的連結之間的索引鍵。 在此範例中，會使用&#x200B;**CRM ID**&#x200B;自訂欄位。
   * 在&#x200B;**[!UICONTROL Fields to update]**&#x200B;節中，指定收件者維中的欄位，以使用檔案中相應列的值進行更新。 如果檔案列的名稱與收件人維欄位的名稱相同或幾乎相同，則可以使用魔術棒按鈕自動匹配不同的欄位。

      ![](assets/import_template_example6.png)

1. 配置位於包含未協調收件者之轉場後的&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動：

   * 選擇&#x200B;**[!UICONTROL Edit configuration]**，並將定位維設定為從工作流的&#x200B;**[!UICONTROL Enrichment]**&#x200B;活動生成的臨時方案。

      ![](assets/import_template_example4.png)

   * 在此範例中，電子郵件欄位可用來尋找獨特的描述檔。 您可以使用任何您確定已填入的欄位，以及唯一組合的一部分。
   * 在&#x200B;**[!UICONTROL Deduplication method]**&#x200B;螢幕中，選擇&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;並選中&#x200B;**[!UICONTROL Disable automatic filtering of 0 ID records]**&#x200B;選項，以確保未排除主鍵等於0的記錄（這應是此轉換的所有記錄）。

   ![](assets/import_template_example7.png)

1. 配置位於先前配置的&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動之後的&#x200B;**[!UICONTROL Update data]**&#x200B;活動。

   * 選擇&#x200B;**[!UICONTROL Insert]**&#x200B;作為&#x200B;**[!UICONTROL Operation type]** ，因為入站過渡僅包含資料庫中不存在的收件人。
   * 在&#x200B;**[!UICONTROL Record identification]**&#x200B;節中，選擇&#x200B;**[!UICONTROL Directly using the targeting dimension]**&#x200B;並選擇&#x200B;**[!UICONTROL Recipients]**&#x200B;維。
   * 在&#x200B;**[!UICONTROL Fields to update]**&#x200B;節中，指定收件者維中的欄位，以使用檔案中相應列的值進行更新。 如果檔案列的名稱與收件人維欄位的名稱相同或幾乎相同，則可以使用魔術棒按鈕自動匹配不同的欄位。

      ![](assets/import_template_example8.png)

1. 在&#x200B;**[!UICONTROL Split]**&#x200B;活動進行第三次轉換後，如果要跟蹤未插入資料庫的資料，請添加&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活動和&#x200B;**[!UICONTROL File transfer]**&#x200B;活動。 設定這些活動，以匯出您需要的欄，並在FTP或SFTP伺服器上傳輸檔案，您可在其中擷取該欄。
1. 新增&#x200B;**[!UICONTROL End]**&#x200B;活動並儲存工作流程範本。

範本現在可以使用，而且適用於每個新的工作流程。 然後，需要全部指定包含要在&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動中導入的資料的檔案。

![](assets/import_template_example9.png)

## 在處理{#unzipping-or-decrypting-a-file-before-processing}之前解壓縮或解密檔案

### 關於預處理階段{#about-pre-processing-stages}

Adobe Campaign可讓您匯入壓縮或加密的檔案。 在[資料載入（檔案）](../../workflow/using/data-loading--file-.md)活動中讀取之前，您可以先定義預先處理來解壓縮或解密檔案。

若要這麼做：

1. 使用[控制面板](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)來產生公用／私用金鑰對。

   >[!NOTE]
   >
   >控制面板適用於AWS托管的所有客戶（現場托管其行銷實例的客戶除外）。

1. 如果您的Adobe Campaign安裝是由Adobe代管，請聯絡Adobe客戶服務，以便在伺服器上安裝必要的公用程式。
1. 如果您的Adobe Campaign安裝是內部部署，請安裝您要使用的公用程式(例如：GPG、GZIP)以及應用程式伺服器上的必要金鑰（加密金鑰）。

然後，您就可以在工作流程中使用所需的預處理命令：

1. 在工作流程中新增及設定&#x200B;**[!UICONTROL File transfer]**&#x200B;活動。
1. 新增&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動並定義檔案格式。
1. 核取 **[!UICONTROL Pre-process the file]** 選項。
1. 指定要套用的預處理命令。
1. 新增其他活動以管理來自檔案的資料。
1. 儲存並執行您的工作流程。

在下面的使用案例中提供了示例。

**相關主題：**

* [資料載入（檔案）活動](../../workflow/using/data-loading--file-.md)。
* [壓縮或加密檔案](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

### 使用案例：導入使用控制面板{#use-case-gpg-decrypt}生成的密鑰加密的資料

在此使用案例中，我們將建立工作流程，以便使用「控制面板」中產生的金鑰，匯入在外部系統中加密的資料。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#video)

執行此使用案例的步驟如下：

1. 使用「控制面板」產生金鑰對（公開／私用）。 [控制面板文檔](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)中提供了詳細步驟。

   * 公開金鑰將會與外部系統共用，外部系統會使用它來加密要傳送至Campaign的資料。
   * Campaign Classic將使用私密金鑰解密傳入的加密資料。

   ![](assets/gpg_generate.png)

1. 在外部系統中，使用從「控制面板」下載的公開金鑰來加密要匯入Campaign Classic的資料。

1. 在Campaign Classic中，建立工作流程以匯入加密資料，並使用透過控制面板安裝的私密金鑰加以解密。 為此，我們將建立以下工作流程：

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 活動：將檔案從外部來源傳輸至Campaign Classic。在此範例中，我們要從SFTP伺服器傳輸檔案。
   * **[!UICONTROL Data loading (file)]** 活動：將檔案中的資料載入到資料庫中，然後使用「控制面板」中生成的專用密鑰對其進行解密。

1. 開啟&#x200B;**[!UICONTROL File transfer]**&#x200B;活動，然後指定您要從中匯入加密。gpg檔案的外部帳戶。

   ![](assets/gpg_key_transfer.png)

   有關如何配置活動的全局概念，請參閱[本節](../../workflow/using/file-transfer.md)。

1. 開啟&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動，然後根據您的需求進行設定。 有關如何配置活動的全局概念可在[本節](../../workflow/using/data-loading--file-.md)中獲得。

   將預處理階段添加到活動中，以便解密傳入資料。 要執行此操作，請選擇&#x200B;**[!UICONTROL Pre-process the file]**&#x200B;選項，然後在&#x200B;**[!UICONTROL Command]**&#x200B;欄位中複製並貼上此解密命令：

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >在此示例中，我們使用「控制面板」預設使用的密碼短語，即「密碼短語」。
   >
   >如果您過去透過客戶服務要求在實例上安裝了GPG金鑰，密碼短語可能已變更，而且依預設會與密碼短語不同。

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;確認活動配置。

1. 您現在可以執行工作流程。 執行完該操作後，您可以簽入工作流日誌，確認已執行解密，且已導入檔案中的資料。

   ![](assets/gpg_run.png)

### 教學課程影片{#video}

本視訊說明如何使用GPG金鑰解密資料。

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

其他Campaign Classic操作視訊可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
