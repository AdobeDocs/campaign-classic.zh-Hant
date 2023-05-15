---
product: campaign
title: 資料載入 (檔案)
description: 深入了解資料載入（檔案）工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management Activity
exl-id: a380e486-a40c-4bf6-b7f4-7dcd76c34085
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 15%

---

# 資料載入 (檔案){#data-loading-file}



## 使用 {#use}

此 **[!UICONTROL Data loading (File)]** 活動可讓您直接存取外部資料來源，並在Adobe Campaign中使用。 事實上，鎖定目標作業所需的所有資料並非一律在Adobe Campaign資料庫中找到：可在外部檔案中使用。

要載入的檔案可由轉換指定，或在執行此活動期間計算。 例如，它可以是客戶10個最喜愛產品的清單，這些產品的採購在外部資料庫中進行管理。

此活動的設定視窗的上方區段可讓您定義檔案格式。 要執行此操作，請使用與要匯入的檔案格式相同的範例檔案。 此檔案可儲存在本機或伺服器上。

>[!CAUTION]
>
>僅支援「一般」結構檔案（例如CSV、TXT等）。 不建議使用XML格式。

![](assets/s_advuser_wf_etl_file.png)

您可以定義要在檔案匯入期間執行的預先處理，例如，這樣就不必在伺服器上解壓縮檔案（因此，為解壓縮的檔案節省空間），而是在檔案處理中納入解壓縮。 選取 **[!UICONTROL Pre-process the file]** 選項，然後從3個選項之一中選擇： **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg)。

![](assets/preprocessing-dataloading.png)

如需詳細資訊，請參閱本區段： [在處理前解壓縮或解密檔案](../../platform/using/unzip-decrypt.md).

## 定義檔案格式 {#defining-the-file-format}

載入檔案時，會自動偵測欄格式並使用每個資料類型的預設參數。 您可以修改這些預設參數，以指定要套用至資料的特定程式，尤其是當有錯誤或空值時。

要執行此操作，請選取 **[!UICONTROL Click here to change the file format...]** 在 **[!UICONTROL Data loading (file)]** 活動。 然後會開啟格式詳細資訊視窗。

![](assets/file_loading_columns_format.png)

然後，您可以修改檔案的一般格式以及每欄的格式。

一般檔案格式可讓您定義識別欄的方式（檔案編碼、使用的分隔符號等）。

欄格式化可讓您定義每列的值處理：

* **[!UICONTROL Ignore column]**：不會在資料載入期間處理此欄。
* **[!UICONTROL Data type]**：指定每欄所需的資料類型。
* **[!UICONTROL Allow NULLs]**:指定如何管理空值。

   * **[!UICONTROL Adobe Campaign default]**：僅為數字欄位產生錯誤，否則插入 NULL 值。
   * **[!UICONTROL Empty value allowed]**：授權空值。因此插入值 NULL。
   * **[!UICONTROL Always populated]**：如果值為空，則產生錯誤。

* **[!UICONTROL Length]**:指定 **字串** 資料類型。
* **[!UICONTROL Format]**:定義時間和日期格式。
* **[!UICONTROL Data transformation]**:定義是否需要在 **字串**.

   * **[!UICONTROL None]**:未修改匯入的字串。
   * **[!UICONTROL First letter in upper case]**:字串每個字詞的第一個字母以大寫開頭。
   * **[!UICONTROL Upper case]**:字串中的所有字元都以大寫表示。
   * **[!UICONTROL Lower case]**:字串中的所有字元都以小寫表示。

* **[!UICONTROL White space management]**:指定字串中是否需要忽略某些空格。 此 **[!UICONTROL Ignore spaces]** 值只允許忽略字串開頭和結尾的空格。
* **[!UICONTROL Error processings]**：會定義發生錯誤時的行為。

   * **[!UICONTROL Ignore the value]**：會忽略值。會在工作流程執行記錄檔中產生警告。
   * **[!UICONTROL Reject line]**：不會處理整行。
   * **[!UICONTROL Use a default value in case of error]**：以在　**[!UICONTROL Default value]**　欄位中定義的預設值取代造成錯誤的值。
   * **[!UICONTROL Reject the line when there is no remapping value]**:除非已為錯誤值定義對應(請參閱 **[!UICONTROL Mapping]** 選項)。
   * **[!UICONTROL Use a default value in case the value is not remapped]**:以 **[!UICONTROL Default value]** 欄位，除非已為錯誤值定義對應(請參閱 **[!UICONTROL Mapping]** 選項)。

* **[!UICONTROL Default value]**：根據選取的錯誤處理指定預設值。
* **[!UICONTROL Mapping]**:此欄位僅在欄詳細資料設定中可用（透過按兩下或欄清單右側的選項存取）。 這會在匯入特定值時轉換這些值。 例如，您可將　&quot;three&quot;　轉換為　&quot;3&quot;。

## 範例：收集資料並將其載入資料庫 {#example--collecting-data-and-loading-it-in-the-database}

以下範例可讓您每天在伺服器上收集檔案、載入其內容，以及根據資料庫中包含的資訊更新資料。 要收集的檔案包含可能已購買（價值3,000歐元以上）、要求購買退款或未購買任何商品就去商店的客戶資訊。 根據此資訊，各種程式將套用至資料庫中的設定檔。

![](assets/s_advuser_load_file_sample_0.png)

1. 檔案收集器允許您根據給定頻率恢復儲存在目錄中的檔案。

   此 **[!UICONTROL Directory]** 頁簽包含要恢復的檔案的資訊。 在本例中，所有文本格式的檔案（其名稱中包含「customers」字）以及儲存在伺服器的tmp/Adobe/Data/files目錄中的檔案都將被恢復。

   使用 **[!UICONTROL File collector]** 在 [檔案收集器](file-collector.md) 區段。

   ![](assets/s_advuser_load_file_sample_1.png)

   此 **[!UICONTROL Schedule]** 頁簽可讓您排程收集器的執行，即指定檢查這些檔案是否存在的頻率。

   在此，我們要在每個工作日晚上9點觸發收集器。

   ![](assets/s_advuser_load_file_sample_2.png)

   若要這麼做，請按一下 **[!UICONTROL Change...]** 按鈕（位於編輯工具的右下角），並配置計畫。

   有關詳細資訊，請參閱 [排程器](scheduler.md).

1. 然後設定資料載入（檔案）活動，以指出應如何讀取收集的檔案。 要執行此操作，請選擇一個與要載入的檔案具有相同結構的示例檔案。

   ![](assets/s_advuser_load_file_sample_3.png)

   此檔案包含五欄：

   * 第一欄包含與事件相符的程式碼：購買（3,000歐元以上），一次或多次購買時無購買或退款。
   * 以下四列包含客戶的名字、姓氏、電子郵件和帳號。

   要載入的檔案格式設定與Adobe Campaign中資料匯入期間所定義的格式設定一致。 如需詳細資訊，請參閱本[區段](../../platform/using/executing-import-jobs.md#step-2---source-file-selection)。

1. 在分割活動中，根據 **事件** 欄值。

   分割活動在區段中詳細說明。

   ![](assets/s_advuser_load_file_sample_4.png)

   對於每個子集，請在 **事件** 欄。

   ![](assets/s_advuser_load_file_sample_5.png)

   此 **[!UICONTROL Split]** 活動因此將包含下列資訊：

   ![](assets/s_advuser_load_file_sample_6.png)

1. 然後指定要針對每種母體類型執行的程式。 在我們的範例中，我們將 **[!UICONTROL Update the data]** 在資料庫中。 若要這麼做，請將 **[!UICONTROL Update data]** 活動（在分割活動的每個出站轉變結束時）。

   此 **[!UICONTROL Update data]** 活動在 [更新資料](update-data.md) 區段。
