---
product: campaign
title: 檔案收集器
description: 深入了解檔案收集器工作流程活動
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 檔案收集器{#file-collector}

![](../../assets/common.svg)

此 **檔案收集器** 監視一個或多個檔案到達目錄中，並為收到的每個檔案激活其轉變。 對於每個事件， **[!UICONTROL filename]** 變數包含收到的檔案完整名稱。 收集的檔案會移至其他目錄以用於封存，並確保只計算一次。

預設情況下，檔案收集器是一項持久性任務，用於在調度指定的時間測試檔案是否存在。

檔案必須位於執行此工作流的wfserver模組所在的伺服器上。 如果在單一執行個體上部署了多個wfserver模組，則必須指定使用這些檔案的活動的相關性或工作流程的整體相關性。

## 屬性 {#properties}

的第一個標籤 **[!UICONTROL File collector]** 活動可讓您選取來源目錄，並視需要篩選收集的檔案。 其他標籤在 [傳入電子郵件](inbound-emails.md) (**[!UICONTROL Schedule]** 和 **[!UICONTROL Expiry]** 標籤)。

![](assets/file_collect_edit.png)

1. **下載檔案**

   * **[!UICONTROL Directory]**

      包含要下載的檔案的目錄。 必須在伺服器上預先建立此目錄：如果不存在，則會引發錯誤。

   * **[!UICONTROL Filter]**

      只考慮與此篩選器匹配的檔案。 目錄中的其他檔案會被忽略。 如果篩選器為空，則會考慮目錄中的所有檔案。 篩選範例： ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      如果啟用此選項，則任務在接收到第一個檔案後結束。 如果目錄中存在與篩選器對應的數個檔案，則只會考慮一個檔案。 此選項保證只會傳送一個事件。 已考慮的檔案是清單中按字母順序排列的第一個檔案。

      對於未調度的活動，如果在指定目錄中找不到與篩選器匹配的檔案，以及 **[!UICONTROL Process file nonexistence]** 選項，則會引發錯誤。

   * **[!UICONTROL Execution schedule]**

      透過 **[!UICONTROL Schedule]** 標籤。

1. **錯誤處理**

   下列兩個選項可供使用：

   * **[!UICONTROL Process file nonexistence]**

      每當在指定目錄中找不到與篩選器匹配的檔案時，此選項就會啟動特殊轉換。

      如果未排程任務，則此轉變只會啟動一次。

   * **[!UICONTROL Processing errors]**

      此選項會顯示特殊轉變，以在產生錯誤時啟動。 在此情況下，工作流程不會變更為錯誤狀態，並繼續執行

      考慮的錯誤是檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

      此選項不會處理與活動配置相關的錯誤，即無效值。

1. **歷史化**

   請參閱 **[!UICONTROL File historization]** 步驟如下： [網頁下載](web-download.md).

無法確定檔案處理順序。 若要依序處理一組檔案，請使用 **[!UICONTROL Stop as soon as a file has been processed]** 選項並建立回圈。 在這種情況下，會以字母順序處理檔案。 此 **[!UICONTROL Process file nonexistence]** 選項，即可完成小版本。

![](assets/file_collect_loop.png)

## 輸出參數 {#output-parameters}

* 檔案名：完整的檔案名。 這是檔案名稱移至歷史化目錄後的檔案名稱。 因此，路徑不同，但如果目錄中已存在另一個同名檔案，則名稱也不同。 會保留擴充功能。
