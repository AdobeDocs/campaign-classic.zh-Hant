---
product: campaign
title: 檔案收集器
description: 瞭解有關「檔案」收集器工作流活動的詳細資訊
feature: Workflows, Data Management
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 檔案收集器{#file-collector}

![](../../assets/v7-only.svg)

的 **檔案收集器** 監視一個或多個檔案在目錄中的到達，並為收到的每個檔案激活其轉換。 對於每個事件， **[!UICONTROL filename]** 變數包含收到的檔案的全名。 收集的檔案將移到另一個目錄以進行存檔，並確保只計數一次。

預設情況下，檔案收集器是一個持久性任務，它在調度指定的時間test檔案的存在。

檔案必須位於負責執行此工作流的wfserver模組的伺服器上。 如果在單個實例上部署了多個wfserver模組，則必須指定使用這些檔案的活動的關聯性或工作流的整體關聯性。

## 屬性 {#properties}

第一個頁籤 **[!UICONTROL File collector]** 「活動」(Activity)，您可以選擇源目錄，並根據需要篩選收集的檔案。 其他頁籤的詳細資訊 [入站電子郵件](inbound-emails.md) (**[!UICONTROL Schedule]** 和 **[!UICONTROL Expiry]** )。

![](assets/file_collect_edit.png)

1. **正在下載檔案**

   * **[!UICONTROL Directory]**

      包含要下載的檔案的目錄。 必須在伺服器上預先建立此目錄：如果不存在，將引發錯誤。

   * **[!UICONTROL Filter]**

      只考慮與此篩選器匹配的檔案。 目錄中的其他檔案將被忽略。 如果篩選器為空，則目錄中的所有檔案都會被考慮在內。 篩選示例： **&#42;.zip**。 **導入 — &#42;.txt**。

   * **[!UICONTROL Stop as soon as a file has been processed]**

      如果啟用此選項，則任務在接收到第一個檔案後結束。 如果目錄中存在與篩選器對應的多個檔案，則只會考慮一個檔案。 此選項確保只發送一個事件。 所考慮的檔案是清單中按字母順序排列的第一個檔案。

      對於未調度的活動，如果在指定的目錄中找不到與篩選器匹配的檔案，以及 **[!UICONTROL Process file nonexistence]** 選項未啟用，將引發錯誤。

   * **[!UICONTROL Execution schedule]**

      通過檔案的參數確定檔案存在檢查的頻率 **[!UICONTROL Schedule]** 頁籤。

1. **錯誤處理**

   以下兩個選項可用：

   * **[!UICONTROL Process file nonexistence]**

      每次在指定目錄中找不到與篩選器匹配的檔案時，此選項將啟動特殊轉換。

      如果未計畫任務，則此轉換將僅激活一次。

   * **[!UICONTROL Processing errors]**

      此選項將顯示特殊的過渡，如果生成錯誤，則激活該過渡。 在這種情況下，工作流不會更改為錯誤狀態，並繼續執行

      考慮的錯誤包括檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

      此選項不處理與活動配置相關的錯誤，即無效值。

1. **歷史化**

   請參閱 **[!UICONTROL File historization]** 步驟： [Web下載](web-download.md)。

無法確定檔案處理順序。 要按順序處理一組檔案，請使用 **[!UICONTROL Stop as soon as a file has been processed]** 的子菜單。 在這種情況下，檔案將按字母順序處理。 的 **[!UICONTROL Process file nonexistence]** 的子菜單。

![](assets/file_collect_loop.png)

## 輸出參數 {#output-parameters}

* 檔案名：完整檔案名。 這是檔案名被移動到歷史記錄目錄後的檔案名。 因此，路徑不同，但如果目錄中已存在同名的另一個檔案，則名稱也不同。 分機已保留。
