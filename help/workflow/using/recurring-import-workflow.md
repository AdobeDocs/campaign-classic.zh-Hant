---
solution: Campaign Classic
product: campaign
title: 設定循環匯入
description: 瞭解如何為循環匯入設定工作流程範本。
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---


# 設定循環匯入工作流程 {#setting-up-a-recurring-import}

如果您需要定期匯入具有相同結構的檔案，請使用工作流程範本是最佳做法。

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
