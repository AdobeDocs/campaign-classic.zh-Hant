---
product: campaign
title: 資料載入 (檔案)
description: 進一步瞭解資料載入（檔案）工作流程活動
feature: Workflows, Data Management Activity
hide: true
hidefromtoc: true
exl-id: a380e486-a40c-4bf6-b7f4-7dcd76c34085
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1140'
ht-degree: 14%

---

# 資料載入 (檔案){#data-loading-file}

## 使用 {#use}

**[!UICONTROL Data loading (File)]**&#x200B;活動可讓您直接存取外部資料來源，並在Adobe Campaign中使用它。 事實上，目標定位作業所需的所有資料並不一定都能在Adobe Campaign資料庫中找到：您可以在外部檔案中取得這些資料。

要載入的檔案可由轉變指定，或在此活動執行期間計算。 例如，它可以是受外部資料庫管理之客戶的10種最喜愛產品的清單。

此活動的設定視窗的上方區段可讓您定義檔案格式。 要執行此操作，請使用與要匯入的範例檔案格式相同的範例檔案。 此檔案可儲存在本機或伺服器上。

>[!CAUTION]
>
>僅支援「平面」結構檔案（例如CSV、TXT等）。 不建議使用XML格式。

![](assets/s_advuser_wf_etl_file.png)

## 套用前置處理階段 {#pre-processing}

您可以定義在檔案匯入期間執行的預先處理程式，例如不必在伺服器上解壓縮檔案（因此可節省解壓縮檔案的空間），而要在檔案處理中包括解壓縮。 [瞭解如何在處理前解壓縮或解密檔案](../../platform/using/unzip-decrypt.md)。

若要這麼做，請選取&#x200B;**[!UICONTROL Pre-process the file]**&#x200B;選項，然後從3個選項中選擇一個： **[!UICONTROL None]**、**[!UICONTROL Decompression]** (zcat)或&#x200B;**[!UICONTROL Decrypt]** (gpg)。

![](assets/preprocessing-dataloading.png)

>[!CAUTION]
>
>如果您使用混合式或內部部署，預先處理命令可能無法立即運作，因為其預設設定使用「zcat」，而Windows不提供此設定。 在這種情況下，您需要調整伺服器組態檔(serverConf.xml)中的&#x200B;**preProcessCommand**&#x200B;節點以符合您的需求。 [瞭解如何在伺服器設定檔中設定前置處理命令](../../installation/using/the-server-configuration-file.md#preprocesscommand)

## 定義檔案格式 {#defining-the-file-format}

載入檔案時，會自動偵測欄格式，以及每種資料型別的預設引數。 您可以修改這些預設參數，以指定要套用至資料的特定程式，尤其是當有錯誤或空值時。

若要這麼做，請在&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活動的主視窗中選取&#x200B;**[!UICONTROL Click here to change the file format...]**。 然後會開啟格式詳細資訊視窗。

![](assets/file_loading_columns_format.png)

然後，您可以修改檔案的一般格式以及每欄的格式。

一般檔案格式設定可讓您定義識別欄的方式（檔案編碼、使用的分隔符號等）。

欄格式化可讓您定義每列的值處理：

>[!NOTE]
>
>您可以視需要新增任意數目的欄。 每欄值的最大長度取決於所選的資料型別。

* **[!UICONTROL Ignore column]**：不會在資料載入期間處理此欄。
* **[!UICONTROL Data type]**：指定每欄所需的資料類型。
* **[!UICONTROL Allow NULLs]**：指定如何管理空值。

   * **[!UICONTROL Adobe Campaign default]**：僅為數字欄位產生錯誤，否則插入 NULL 值。
   * **[!UICONTROL Empty value allowed]**：授權空值。因此插入值 NULL。
   * **[!UICONTROL Always populated]**：如果值為空，則產生錯誤。

* **[!UICONTROL Length]**：指定&#x200B;**字串**&#x200B;資料型別的字元數目上限。
* **[!UICONTROL Format]**：定義時間和日期格式。
* **[!UICONTROL Data transformation]**：定義是否需要在&#x200B;**字串**&#x200B;上套用字元大寫處理程式。

   * **[!UICONTROL None]**：未修改匯入的字串。
   * **[!UICONTROL First letter in upper case]**：字串中每個字詞的第一個字母都以大寫開頭。
   * **[!UICONTROL Upper case]**：字串中的所有字元都是大寫。
   * **[!UICONTROL Lower case]**：字串中的所有字元都是小寫。

* **[!UICONTROL White space management]**：指定字串中是否需要忽略某些空格。 **[!UICONTROL Ignore spaces]**&#x200B;值只允許忽略字串開頭和結尾的空格。
* **[!UICONTROL Error processings]**：會定義發生錯誤時的行為。

   * **[!UICONTROL Ignore the value]**：會忽略值。會在工作流程執行記錄檔中產生警告。
   * **[!UICONTROL Reject line]**：不會處理整行。
   * **[!UICONTROL Use a default value in case of error]**：以在　**[!UICONTROL Default value]**　欄位中定義的預設值取代造成錯誤的值。
   * **[!UICONTROL Reject the line when there is no remapping value]**：除非已針對錯誤值定義對應（請參閱下方的&#x200B;**[!UICONTROL Mapping]**&#x200B;選項），否則不會處理整行。
   * **[!UICONTROL Use a default value in case the value is not remapped]**：以在&#x200B;**[!UICONTROL Default value]**&#x200B;欄位中定義的預設值取代造成錯誤的值，除非已針對錯誤值定義對應（請參閱下方的&#x200B;**[!UICONTROL Mapping]**&#x200B;選項）。

* **[!UICONTROL Default value]**：根據選取的錯誤處理指定預設值。
* **[!UICONTROL Mapping]**：此欄位僅在欄詳細資料設定（透過按兩下或欄清單右側的選項存取）中可用。 這會在匯入特定值時加以轉換。 例如，您可將　&quot;three&quot;　轉換為　&quot;3&quot;。

## 範例：收集資料並將其載入資料庫 {#example--collecting-data-and-loading-it-in-the-database}

以下範例可讓您每天在伺服器上收集檔案、載入其內容，並根據其中包含的資訊更新資料庫中的資料。 要收集的檔案包含客戶的相關資訊，這些客戶可能已購買（3,000歐元或以下）、要求購買退款，或是未購買任何東西就造訪商店。 根據此資訊，各種程式將套用至它們在資料庫中的設定檔。

![](assets/s_advuser_load_file_sample_0.png)

1. 檔案收集器可讓您根據指定的頻率，復原儲存在目錄中的檔案。

   **[!UICONTROL Directory]**&#x200B;索引標籤包含要復原的檔案資訊。 在我們的範例中，將會復原名稱包含&#39;customers&#39;一字且儲存在伺服器的tmp/Adobe/Data/files目錄中的所有文字格式檔案。

   [檔案收集器](file-collector.md)區段中詳細說明使用&#x200B;**[!UICONTROL File collector]**。

   ![](assets/s_advuser_load_file_sample_1.png)

   **[!UICONTROL Schedule]**&#x200B;索引標籤可讓您排程收集器的執行，也就是指定檢查這些檔案是否存在的頻率。

   我們想要在每個工作日晚上9點觸發收集器。

   ![](assets/s_advuser_load_file_sample_2.png)

   若要這麼做，請按一下編輯工具右下角的&#x200B;**[!UICONTROL Change...]**&#x200B;按鈕，並設定排程。

   有關詳細資訊，請參閱[排程器](scheduler.md)。

1. 然後設定資料載入（檔案）活動，以指出應如何讀取收集的檔案。 要執行此操作，請選取與要載入的檔案具有相同結構的範例檔案。

   ![](assets/s_advuser_load_file_sample_3.png)

   在此，檔案包含五欄：

   * 第一欄包含與事件一致的程式碼：購買（大於或小於3,000歐元）、一次或多次購買均不購買或退款。
   * 下列四欄包含使用者端的名字、姓氏、電子郵件和帳號。

   要載入之檔案的格式設定與Adobe Campaign中資料匯入期間定義的格式設定一致。 如需詳細資訊，請參閱本[區段](../../platform/using/executing-import-jobs.md#step-2---source-file-selection)。

1. 在分割活動中，根據&#x200B;**Event**&#x200B;資料行值，指定要建立的子集。

   「分割」活動在一節中有詳細說明。

   ![](assets/s_advuser_load_file_sample_4.png)

   對於每個子集，請在&#x200B;**Event**&#x200B;資料行中指定其中一個值。

   ![](assets/s_advuser_load_file_sample_5.png)

   因此，**[!UICONTROL Split]**&#x200B;活動將包含下列資訊：

   ![](assets/s_advuser_load_file_sample_6.png)

1. 然後指定針對每種母體型別執行的程式。 在我們的範例中，我們將前往資料庫中的&#x200B;**[!UICONTROL Update the data]**。 若要這麼做，請在分割活動的每個出站轉變的結尾處放置&#x200B;**[!UICONTROL Update data]**&#x200B;活動。

   **[!UICONTROL Update data]**&#x200B;活動在[更新資料](update-data.md)區段中詳細說明。
