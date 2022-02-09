---
product: campaign
title: 設定定期導入
description: 瞭解如何為循環導入配置工作流模板。
feature: Workflows
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 0%

---

# 設定週期性匯入工作流程 {#setting-up-a-recurring-import}

![](../../assets/common.svg)

如果您需要定期導入具有相同結構的檔案，則使用工作流模板是最佳做法。

此示例說明如何預先設定可重複使用的工作流，以導入來自Adobe Campaign資料庫中CRM的配置檔案。 有關每個活動的所有可能設定的詳細資訊，請參閱此 [節](about-activities.md)。

1. 從建立新工作流模板 **[!UICONTROL Resources > Templates > Workflow templates]**。
1. 添加以下活動：

   * **[!UICONTROL Data loading (file)]**:定義包含要導入的資料的檔案的預期結構。
   * **[!UICONTROL Enrichment]**:調節導入的資料與資料庫資料。
   * **[!UICONTROL Split]**:建立篩選器以根據記錄是否可對帳的不同方式處理記錄。
   * **[!UICONTROL Deduplication]**:在將資料插入資料庫之前，從傳入檔案中消除重複資料。
   * **[!UICONTROL Update data]**:使用導入的配置檔案更新資料庫。

   ![](assets/import_template_example0.png)

1. 配置 **[!UICONTROL Data Loading (file)]** 活動：

   * 通過上載示例檔案來定義預期的結構。 示例檔案應僅包含幾行，但必須包含導入所需的所有列。 檢查並編輯檔案格式以確保正確設定每列的類型：文本、日期、整數等。 例如：

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * 在 **[!UICONTROL Name of the file to load]** 選擇 **[!UICONTROL Upload a file from the local machine]** 將欄位留空。 每次根據此模板建立新工作流時，都可以在此處指定所需的檔案，只要該檔案與定義的結構對應。

      可以使用任何選項，但必須相應修改模板。 例如，如果您選擇 **[!UICONTROL Specified in the transition]**，您可以 **[!UICONTROL File Transfer]** 活動，以從FTP/SFTP伺服器中檢索要導入的檔案。 通過S3或SFTP連接，您還可以通過Adobe即時客戶資料平台將段資料導入Adobe Campaign。 有關此的詳細資訊，請參閱此 [文檔](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)。

      ![](assets/import_template_example1.png)

1. 配置 **[!UICONTROL Enrichment]** 的子菜單。 此上下文中此活動的目的是標識傳入資料。

   * 在 **[!UICONTROL Enrichment]** 頁籤 **[!UICONTROL Add data]** 並定義導入的資料與目標維的收件人之間的連結。 在此示例中， **CRM ID** custom欄位用於建立聯接條件。 使用需要的欄位或欄位組合，只要它允許標識唯一記錄。
   * 在 **[!UICONTROL Reconciliation]** 頁籤 **[!UICONTROL Identify the document from the working data]** 複選框。

   ![](assets/import_template_example2.png)

1. 配置 **[!UICONTROL Split]** 活動，用於檢索一個轉換中已協調的收件人和在第二個轉換中具有足夠資料的無法協調的收件人。

   然後，可以使用與已協調的收件人進行的轉換來更新資料庫。 如果檔案中有最小資訊集，則具有未知收件人的轉換可用於在資料庫中建立新收件人條目。

   無法協調且沒有足夠資料的收件人將在補充出站轉換中選擇，並可以在單獨的檔案中導出，或只是忽略。

   * 在 **[!UICONTROL General]** 頁籤，選擇 **[!UICONTROL Use the additional data only]** 作為篩選設定，並確保 **[!UICONTROL Targeting dimension]** 自動設定為 **[!UICONTROL Enrichment]**。

      檢查 **[!UICONTROL Generate complement]** 的子菜單。 如果需要，可對補充資料應用進一步處理：檔案導出、清單更新等。

   * 在 **[!UICONTROL Subsets]** 頁籤，在入站人口中添加篩選條件，以僅選擇收件人主鍵不等於0的記錄。 這樣，在該子集中選擇與來自資料庫的接收者協調的檔案中的資料。

      ![](assets/import_template_example3.png)

   * 添加第二個子集，該子集選擇具有足夠資料要插入資料庫的未協調記錄。 例如：電子郵件地址、名字和姓氏。

      子集按其建立順序進行處理，這意味著當處理此第二子集時，已存在於資料庫中的所有記錄都已在第一子集中選定。

      ![](assets/import_template_example3_2.png)

   * 未在前兩個子集中選擇的所有記錄將在 **[!UICONTROL Complement]**。

1. 配置 **[!UICONTROL Update data]** 位於 **[!UICONTROL Split]** 活動。

   * 選擇 **[!UICONTROL Update]** 如 **[!UICONTROL Operation type]** 因為入站轉換僅包含資料庫中已存在的收件人。
   * 在 **[!UICONTROL Record identification]** 選擇 **[!UICONTROL Using reconciliation keys]** 定義目標維與在 **[!UICONTROL Enrichment]**。 在此示例中， **CRM ID** 自定義欄位。
   * 在 **[!UICONTROL Fields to update]** 部分，指明要使用檔案中相應列的值更新的收件人維中的欄位。 如果檔案列的名稱與收件人維欄位的名稱相同或幾乎相同，則可以使用魔棒按鈕自動匹配不同的欄位。

      ![](assets/import_template_example6.png)

1. 配置 **[!UICONTROL Deduplication]** 位於包含未協調收件人的轉換後的活動：

   * 選擇 **[!UICONTROL Edit configuration]** 並將目標維設定為從 **[!UICONTROL Enrichment]** 的子目錄。

      ![](assets/import_template_example4.png)

   * 在此示例中，電子郵件欄位用於查找唯一的配置檔案。 您可以使用您確定已填充的任何欄位，並使用唯一組合的一部分。
   * 在 **[!UICONTROL Deduplication method]** 螢幕，選擇 **[!UICONTROL Advanced parameters]** 檢查 **[!UICONTROL Disable automatic filtering of 0 ID records]** 選項，確保不排除主鍵等於0（應為此轉換的所有記錄）的記錄。

   ![](assets/import_template_example7.png)

1. 配置 **[!UICONTROL Update data]** 位於 **[!UICONTROL Deduplication]** 活動。

   * 選擇 **[!UICONTROL Insert]** 如 **[!UICONTROL Operation type]** 因為入站轉換僅包含資料庫中不存在的收件人。
   * 在 **[!UICONTROL Record identification]** 選擇 **[!UICONTROL Directly using the targeting dimension]** 選擇 **[!UICONTROL Recipients]** 維。
   * 在 **[!UICONTROL Fields to update]** 部分，指明要使用檔案中相應列的值更新的收件人維中的欄位。 如果檔案列的名稱與收件人維欄位的名稱相同或幾乎相同，則可以使用魔棒按鈕自動匹配不同的欄位。

      ![](assets/import_template_example8.png)

1. 在 **[!UICONTROL Split]** 活動，添加 **[!UICONTROL Data extraction (file)]** 活動和 **[!UICONTROL File transfer]** 活動。 配置這些活動以導出所需的列，並在FTP或SFTP伺服器上傳輸檔案，在該伺服器上可以檢索該檔案。
1. 添加 **[!UICONTROL End]** 並保存工作流模板。

現在可以使用該模板，並且可用於每個新工作流。 然後，需要指定包含要在 **[!UICONTROL Data loading (file)]** 的子菜單。

![](assets/import_template_example9.png)
