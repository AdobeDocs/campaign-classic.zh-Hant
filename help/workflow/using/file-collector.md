---
title: 檔案收集器
seo-title: 檔案收集器
description: 檔案收集器
seo-description: null
page-status-flag: never-activated
uuid: 57ef7b2b-f257-4d76-970f-55aece719cec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 9b937d4d-55ae-4bd4-8dc6-eea42f15b69f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# 檔案收集器{#file-collector}

「文 **件」(File** )收集器監視一個或多個檔案在目錄中的到達情況，並為收到的每個檔案激活其過渡。 對於每個事件， **[!UICONTROL filename]** 變數會包含收到的檔案的完整名稱。 收集到的檔案會移至另一個目錄以進行封存，並確保只計算一次。

預設情況下，檔案收集器是一個持久性任務，在計畫指定的時間測試檔案是否存在。

檔案必須位於負責執行此工作流的wfserver模組所在的伺服器上。 如果在單個實例上部署了多個wfserver模組，則必須指定使用這些檔案的活動的相關性或工作流的整體相關性。

## 屬性 {#properties}

活動的第一個選 **[!UICONTROL File collector]** 項卡可讓您選擇源目錄，並根據需要篩選收集的檔案。 其他標籤在「傳入電子郵 [件](../../workflow/using/inbound-emails.md) (**[!UICONTROL Schedule]** 和標籤 **[!UICONTROL Expiry]** )」中詳述。

![](assets/file_collect_edit.png)

1. **下載檔案**

   * **[!UICONTROL Directory]**

      包含要下載的檔案的目錄。 必須事先在伺服器上建立此目錄： 如果不存在，則會引發錯誤。

   * **[!UICONTROL Filter]**

      只會考量符合此篩選的檔案。 目錄中的其他檔案將被忽略。 如果篩選器為空，則將考慮目錄中的所有檔案。 篩選範例： ***.zip**, **import-*.txt**。

   * **[!UICONTROL Stop as soon as a file has been processed]**

      如果啟用此選項，則任務在接收到第一個檔案後結束。 如果目錄中存在與篩選器對應的多個檔案，則只會考慮一個檔案。 此選項可保證只傳送一個事件。 在清單中，第一個考慮到的檔案是字母順序。

      對於未調度的活動，如果在指定目錄中未找到與篩選器匹配的檔案，並且如果 **[!UICONTROL Process file nonexistence]** 未啟用該選項，則會引發錯誤。

   * **[!UICONTROL Execution schedule]**

      通過頁籤的參數確定檔案存在檢查的頻 **[!UICONTROL Schedule]** 率。

1. **錯誤處理**

   有下列兩個選項可供使用：

   * **[!UICONTROL Process file nonexistence]**

      每次在指定目錄中找不到與篩選器匹配的檔案時，此選項都會啟動一個特殊轉換。

      如果未排程任務，則此轉場只會啟動一次。

   * **[!UICONTROL Processing errors]**

      此選項會顯示特殊的轉場，以在產生錯誤時啟動。 在這種情況下，工作流不會更改為錯誤狀態，並繼續執行

      考慮到的錯誤是檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

      此選項不處理與活動配置相關的錯誤，即無效值。

1. **歷史化**

   請參閱此處 **[!UICONTROL File historization]** 的步驟： [網頁下載](../../workflow/using/web-download.md)。

無法確定檔案處理順序。 要按順序處理一組檔案，請使用 **[!UICONTROL Stop as soon as a file has been processed]** 該選項並建立循環。 在這種情況下，檔案將按字母順序進行處理。 此選 **[!UICONTROL Process file nonexistence]** 項可讓您完成小版本。

![](assets/file_collect_loop.png)

## 輸出參數 {#output-parameters}

* 檔案名： 完整的檔案名稱。 這是檔案名被移到歷史目錄後的檔案名。 因此，路徑不同，但如果目錄中已存在同名的另一個檔案，則名稱也不同。 保留擴展。
