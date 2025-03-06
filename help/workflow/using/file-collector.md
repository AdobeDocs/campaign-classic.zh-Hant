---
product: campaign
title: 檔案收集器
description: 深入瞭解檔案收集器工作流程活動
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 檔案收集器{#file-collector}



**檔案收集器**&#x200B;會監視一或多個檔案在目錄中的到達，並針對每個收到的檔案啟動其轉換。 對於每個事件，**[!UICONTROL filename]**&#x200B;變數都包含所收到檔案的完整名稱。 收集的檔案會移至另一個目錄以進行封存，並確保只計算一次。

依預設，檔案收集器是持續性的工作，會在排程指定的時間測試檔案是否存在。

檔案必須位於負責執行此工作流程的wfserver模組所在的伺服器上。 如果在單一執行個體上部署了數個wfserver模組，則必須指定使用這些檔案之活動的相似性或工作流程的整體相似性。

## 屬性 {#properties}

**[!UICONTROL File collector]**&#x200B;活動的第一個索引標籤可讓您選取來源目錄，並在必要時篩選收集的檔案。 其他標籤在[傳入電子郵件](inbound-emails.md)中詳細說明（**[!UICONTROL Schedule]**&#x200B;和&#x200B;**[!UICONTROL Expiry]**&#x200B;標籤）。

![](assets/file_collect_edit.png)

1. **正在下載檔案**

   * **[!UICONTROL Directory]**

     包含要下載之檔案的目錄。 必須在伺服器上預先建立此目錄：如果目錄不存在，將會引發錯誤。

   * **[!UICONTROL Filter]**

     只考慮符合此篩選的檔案。 會忽略目錄中的其他檔案。 如果篩選器為空，則會考慮目錄中的所有檔案。 篩選器範例： **&#42;.zip**，**import-&#42;.txt**。

   * **[!UICONTROL Stop as soon as a file has been processed]**

     如果啟用此選項，則任務會在收到第一個檔案後結束。 如果目錄中存在多個與篩選器對應的檔案，則只會考慮一個檔案。 此選項可確保只傳送一個事件。 考慮的檔案是清單中第一個按字母順序排列的檔案。

     針對未排程的活動，如果在指定的目錄中找不到符合篩選的檔案，且未啟用&#x200B;**[!UICONTROL Process file nonexistence]**&#x200B;選項，則會引發錯誤。

   * **[!UICONTROL Execution schedule]**

     透過&#x200B;**[!UICONTROL Schedule]**&#x200B;索引標籤的引數，決定檔案存在檢查的頻率。

1. **錯誤處理**

   下列兩個選項可供使用：

   * **[!UICONTROL Process missing file]**

     每次在指定目錄中找不到符合篩選條件的檔案時，此選項都會起始特殊轉變。

     如果未排程工作，此轉變將僅啟動一次。

   * **[!UICONTROL Process errors]**

     此選項會顯示特殊的轉變，以便在產生錯誤時啟動。 在這種情況下，工作流程不會變更為錯誤狀態，並繼續執行

     考慮的錯誤是檔案系統錯誤（無法移動檔案、無法存取目錄等）。

     此選項不會處理與活動設定相關的錯誤，即無效值。

1. **歷史化**

   請參閱此處的&#x200B;**[!UICONTROL File historization]**&#x200B;步驟： [網頁下載](web-download.md)。

無法判斷檔案處理順序。 若要依序處理一組檔案，請使用&#x200B;**[!UICONTROL Stop as soon as a file has been processed]**&#x200B;選項並建立回圈。 在此情況下，會依字母順序處理檔案。 **[!UICONTROL Process file nonexistence]**&#x200B;選項可讓您完成反複專案。

![](assets/file_collect_loop.png)

## 輸出引數 {#output-parameters}

* 檔案名稱：完整的檔案名稱。 這是檔案名稱移至歷史化目錄後的名稱。 因此，路徑會不同，但如果目錄中已存在相同名稱的另一個檔案，其名稱也會不同。 會保留擴充功能。
