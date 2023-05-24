---
product: campaign
title: 設定循環匯入
description: 瞭解如何設定重複匯入的工作流程範本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 0%

---

# 設定週期性匯入工作流程 {#setting-up-a-recurring-import}



如果您需要定期匯入具有相同結構的檔案，最佳實務就是使用工作流程範本。

此範例說明如何預先設定工作流程，該工作流程可重複用於匯入來自Adobe Campaign資料庫中CRM的設定檔。 如需每個活動所有可能設定的詳細資訊，請參閱此 [區段](about-activities.md).

1. 建立新的工作流程範本，從 **[!UICONTROL Resources > Templates > Workflow templates]**.
1. 新增下列活動：

   * **[!UICONTROL Data loading (file)]**：定義包含要匯入之資料的檔案的預期結構。
   * **[!UICONTROL Enrichment]**：使用資料庫資料調解匯入的資料。
   * **[!UICONTROL Split]**：建立篩選條件以根據是否可以調解記錄而以不同方式處理記錄。
   * **[!UICONTROL Deduplication]**：在傳入檔案插入資料庫之前，從傳入檔案中刪除重複資料。
   * **[!UICONTROL Update data]**：使用匯入的設定檔更新資料庫。

   ![](assets/import_template_example0.png)

1. 設定 **[!UICONTROL Data Loading (file)]** 活動：

   * 透過上傳範例檔案來定義預期的結構。 範例檔案應僅包含幾行，但應包含匯入所需的所有欄。 檢查並編輯檔案格式，以確定每欄的型別已正確設定：文字、日期、整數等。 例如：

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * 在 **[!UICONTROL Name of the file to load]** 區段，選取 **[!UICONTROL Upload a file from the local machine]** 並將欄位留空。 每次從這個範本建立新工作流程時，只要檔案與定義的結構相對應，您就可以在此處指定想要的檔案。

      您可以使用任何選項，但必須相應地修改範本。 例如，如果您選取 **[!UICONTROL Specified in the transition]**，您可以新增 **[!UICONTROL File Transfer]** 活動，以擷取要從FTP/SFTP伺服器匯入的檔案。 透過S3或SFTP連線，您也可以透過Adobe Real-time Customer Data平台將區段資料匯入Adobe Campaign。 如需詳細資訊，請參閱此 [檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

      ![](assets/import_template_example1.png)

1. 設定 **[!UICONTROL Enrichment]** 活動。 此活動在此情境中的目的是識別傳入的資料。

   * 在 **[!UICONTROL Enrichment]** 索引標籤，選取 **[!UICONTROL Add data]** 和定義匯入資料和收件者目標維度之間的連結。 在此範例中， **CRM ID** 自訂欄位用於建立連線條件。 只要允許您識別唯一記錄，就使用您需要的欄位或欄位組合。
   * 在 **[!UICONTROL Reconciliation]** tab鍵，保留 **[!UICONTROL Identify the document from the working data]** 選項未勾選。

   ![](assets/import_template_example2.png)

1. 設定 **[!UICONTROL Split]** 在某個轉變中擷取已調解收件者的活動，以及無法調解但在第二個轉變中擁有足夠資料的收件者。

   然後可以使用包含已調解收件者的轉變來更新資料庫。 如果檔案中有最少的一組資訊，則可使用具有未知收件者的轉變，在資料庫中建立新的收件者專案。

   無法調解且資料不足的收件者，會在補充傳出轉變中選取，並可在個別檔案中匯出或直接忽略。

   * 在 **[!UICONTROL General]** 索引標籤中，選取 **[!UICONTROL Use the additional data only]** 作為篩選設定，並確定 **[!UICONTROL Targeting dimension]** 自動設為 **[!UICONTROL Enrichment]**.

      檢查 **[!UICONTROL Generate complement]** 選項，以檢視是否有任何記錄無法插入資料庫中。 如有需要，您可以對補充資料套用進一步處理：檔案匯出、清單更新等。

   * 在 **[!UICONTROL Subsets]** 索引標籤上，對入站母體新增篩選條件，以僅選取收件者主索引鍵不等於0的記錄。 如此一來，會在該子集中選取檔案中與資料庫收件者調解的資料。

      ![](assets/import_template_example3.png)

   * 新增第二個子集，選取有足夠資料可插入資料庫中的未調解記錄。 例如：電子郵件地址、名字和姓氏。

      子集會依其建立順序進行處理，這表示在處理此第二個子集時，已在第一個子集中選取資料庫中已存在的所有記錄。

      ![](assets/import_template_example3_2.png)

   * 在前兩個子集中未選取的所有記錄都會在 **[!UICONTROL Complement]**.

1. 設定 **[!UICONTROL Update data]** 位於第一個出站轉變之後的活動 **[!UICONTROL Split]** 活動是先前設定的。

   * 選取 **[!UICONTROL Update]** 作為 **[!UICONTROL Operation type]** 由於入站轉變僅包含資料庫中已存在的收件者。
   * 在 **[!UICONTROL Record identification]** 區段，選取 **[!UICONTROL Using reconciliation keys]** 並定義目標維度與中建立之連結之間的索引鍵 **[!UICONTROL Enrichment]**. 在此範例中， **CRM ID** 使用自訂欄位。
   * 在 **[!UICONTROL Fields to update]** 區段，指出收件者維度中的欄位，以使用檔案中對應欄的值進行更新。 如果檔案欄的名稱相同或幾乎與收件者維度欄位的名稱相同，您可以使用魔術棒按鈕來自動比對不同的欄位。

      ![](assets/import_template_example6.png)

1. 設定 **[!UICONTROL Deduplication]** 位於包含未調解收件者的轉變後的活動：

   * 選取 **[!UICONTROL Edit configuration]** 並將目標維度設定為從中產生的臨時結構描述 **[!UICONTROL Enrichment]** 工作流程的活動。

      ![](assets/import_template_example4.png)

   * 在此範例中，電子郵件欄位用於尋找唯一設定檔。 您可以使用任何您確定已填入的欄位，以及唯一組合的一部分。
   * 在 **[!UICONTROL Deduplication method]** 畫面，選取 **[!UICONTROL Advanced parameters]** 並檢視 **[!UICONTROL Disable automatic filtering of 0 ID records]** 用於確保不排除主鍵等於0 （應該為此轉變的所有記錄）的記錄的選項。

   ![](assets/import_template_example7.png)

1. 設定 **[!UICONTROL Update data]** 活動位於以下專案之後： **[!UICONTROL Deduplication]** 活動是先前設定的。

   * 選取 **[!UICONTROL Insert]** 作為 **[!UICONTROL Operation type]** 因為入站轉變只包含資料庫中不存在的收件者。
   * 在 **[!UICONTROL Record identification]** 區段，選取 **[!UICONTROL Directly using the targeting dimension]** 並選擇 **[!UICONTROL Recipients]** 維度。
   * 在 **[!UICONTROL Fields to update]** 區段，指出收件者維度中的欄位，以使用檔案中對應欄的值進行更新。 如果檔案欄的名稱相同或幾乎與收件者維度欄位的名稱相同，您可以使用魔術棒按鈕來自動比對不同的欄位。

      ![](assets/import_template_example8.png)

1. 在的第三個轉變之後 **[!UICONTROL Split]** 活動，新增 **[!UICONTROL Data extraction (file)]** 活動和 **[!UICONTROL File transfer]** 活動（如果要追蹤未插入資料庫中的資料）。 設定這些活動以匯出您需要的欄，並在可擷取檔案的FTP或SFTP伺服器上傳輸檔案。
1. 新增 **[!UICONTROL End]** 活動並儲存工作流程範本。

範本現在可供使用，並可用於每個新工作流程。 然後只需指定包含要匯入之資料的檔案 **[!UICONTROL Data loading (file)]** 活動。

![](assets/import_template_example9.png)
