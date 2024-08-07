---
product: campaign
title: 一般匯入範例
description: 深入瞭解您可以使用匯入作業執行的一般匯入
feature: Data Management
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4582b524-2b6d-484c-bace-29d2e69f60e9
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 55%

---

# 一般匯入範例 {#import-operations-samples}



## 從收件者清單匯入 {#example--import-from-a-list-of-recipients}

要從清單概述建立和提供收件者清單，請應用以下步驟：

1. 建立清單

   * 按一下Adobe Campaign首頁&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;功能表中的&#x200B;**[!UICONTROL Lists]**&#x200B;連結。
   * 按一下&#x200B;**[!UICONTROL Create]**，然後按一下&#x200B;**[!UICONTROL Import a list]**&#x200B;按鈕。

1. 選擇要匯入的檔案

   按一下&#x200B;**[!UICONTROL Local file]**&#x200B;欄位右側的資料夾，並選取包含要匯入清單的檔案。

   ![](assets/s_ncs_user_import_example00_01.png)

1. 清單名稱和儲存

   輸入清單的名稱，然後選擇應保存的目錄。

   ![](assets/s_ncs_user_import_example00_02.png)

1. 啟動匯入

   按一下&#x200B;**[!UICONTROL Next]**，然後按&#x200B;**[!UICONTROL Start]**，開始匯入清單。

   ![](assets/s_ncs_user_import_example00_03.png)

## 從文字檔匯入新記錄 {#example--import-new-records-from-a-text-file-}

要將儲存在文字檔中的新收件者設定檔匯入 Adobe Campaign 資料庫，請使用以下步驟：

1. 選擇範本

   * 從Adobe Campaign首頁，按一下&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;連結，然後按&#x200B;**[!UICONTROL Jobs]**。 按一下工作清單上方的&#x200B;**[!UICONTROL New import]**。
   * 依預設保持選取&#x200B;**[!UICONTROL New text import]**&#x200B;範本。
   * 更改標籤和描述。
   * 選取 **[!UICONTROL Simple import]**。
   * 保留預設作業資料夾。
   * 按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;並選取&#x200B;**[!UICONTROL Tracking mode]**&#x200B;選項，以檢視執行期間匯入的詳細資料。

1. 選擇要匯入的檔案

   按一下&#x200B;**[!UICONTROL Local file]**&#x200B;欄位右側的資料夾，然後選取您要匯入的檔案。

   ![](assets/s_ncs_user_import_example01_01.png)

1. 關聯欄位

   按一下&#x200B;**[!UICONTROL Guess the destination fields]**&#x200B;圖示以自動對應來源和目的地結構描述。 按一下&#x200B;**[!UICONTROL Next]**&#x200B;之前，請先檢查此視窗中的資訊。

   ![](assets/s_ncs_user_import_example03_01.png)

1. 調和

   * 轉到&#x200B;**收件者 (nms:recipient)** 表。
   * 選取&#x200B;**[!UICONTROL Insertion]**&#x200B;作業，並將預設值保留在其他欄位中。

     ![](assets/s_ncs_user_import_example04_01.png)

1. 匯入收件者

   * 如有必要，請為要匯入的記錄指定一個資料夾。

     ![](assets/s_ncs_user_import_example05_01.png)

1. 啟動匯入

   * 按一下&#x200B;**[!UICONTROL Start]**。

     在編輯器的中心區欄位，您可以檢查匯入操作是否成功並查看已處理的記錄數。

     ![](assets/s_ncs_user_import_example06_01.png)

     **[!UICONTROL Tracking]**&#x200B;模式可讓您追蹤來源檔案中每個記錄的匯入詳細資料。 若要這麼做，請從首頁按一下&#x200B;**[!UICONTROL Profiles and Targets]**，然後按一下&#x200B;**[!UICONTROL Processes]**，選取相關的匯入，並查閱&#x200B;**[!UICONTROL General]**、**[!UICONTROL Journal]**&#x200B;和&#x200B;**[!UICONTROL Rejects]**&#x200B;索引標籤。

      * 檢查匯入進度

        ![](assets/s_ncs_user_import_example07_01.png)

      * 處理每條記錄的查看

        ![](assets/s_ncs_user_import_example07_02.png)

## 更新並插入收件者 {#example--update-and-insert-recipients}

我們想要更新資料庫中的現有記錄，並從文字檔建立新的記錄。 以下是該過程的示例：

1. 選擇範本

   重複上面示例 2 中描述的步驟。

1. 要匯入的檔案

   選擇要匯入的檔案。

   在我們的示例中，檔案第一行的概述顯示該檔案包含三個記錄的更新和記錄的建立。

   ![](assets/s_ncs_user_import_example02_02.png)

1. 關聯欄位

   應用上面示例 2 中的過程。

1. 調和

   * 保留&#x200B;**[!UICONTROL Update or insert]**&#x200B;預設為選取。
   * 將選項&#x200B;**[!UICONTROL Management of duplicates]**&#x200B;保留在&#x200B;**[!UICONTROL Update]**&#x200B;模式，以便使用文字檔中的資料修改資料庫中的現有記錄。
   * 選取欄位&#x200B;**[!UICONTROL Birth date]**、**[!UICONTROL Name]**&#x200B;和&#x200B;**[!UICONTROL Company]**，並指派調解金鑰給它們。

     ![](assets/s_ncs_user_import_example04_02.png)

1. 啟動匯入

   * 按一下&#x200B;**[!UICONTROL Start]**。

     在追蹤視窗中，您可以檢查匯入是否成功並查看已處理的記錄數。

     ![](assets/s_ncs_user_import_example06_02.png)

   * 查看收件者表以檢查此操作已修改記錄。

     ![](assets/s_ncs_user_import_example06_03.png)

## 使用外部檔案的值增補該值 {#example--enrich-the-values-with-those-of-an-external-file}

我們希望從文字檔中修改資料庫表中的某些欄位，優先考慮資料庫中包含的值。

在此範例中，您可以看到文字檔中的某些欄位有值，而資料庫中的對應欄位是空的。 其他欄位包含與資料庫中包含的值不同的值。

* 要匯入的文字檔的內容。

  ![](assets/s_ncs_user_import_example02_03.png)

* 匯入前的資料庫狀態

  ![](assets/s_ncs_user_import_example06_04.png)

應用以下步驟：

1. 選擇範本

   應用上面示例 2 中的過程。

1. 要匯入的檔案

   選擇要匯入的檔案。

1. 關聯欄位

   應用上面示例 2 中的過程。

   在預覽檔案的第一行時，您可以看到該檔案包含某些記錄的更新。

1. 調和

   * 移至表格並選取&#x200B;**[!UICONTROL Update]**&#x200B;作業。
   * 為&#x200B;**[!UICONTROL Management of doubles]**&#x200B;欄位選取選項&#x200B;**[!UICONTROL Reject entity]**。
   * 將選項&#x200B;**[!UICONTROL Management of duplicates]**&#x200B;保留在&#x200B;**[!UICONTROL Update]**&#x200B;模式，以便使用文字檔中的資料修改資料庫中的現有記錄。
   * 將游標放在&#x200B;**[!UICONTROL Last name (@lastName)]**&#x200B;節點上，並選取&#x200B;**[!UICONTROL Update only if destination is empty]**&#x200B;選項。
   * 對&#x200B;**[!UICONTROL Company (@company)]**&#x200B;節點重複此作業。
   * 指派調解金鑰給欄位&#x200B;**[!UICONTROL Birth date]**、**[!UICONTROL Email]**&#x200B;和&#x200B;**[!UICONTROL First name]**。

     ![](assets/s_ncs_user_import_example04_03.png)

1. 啟動匯入

   按一下&#x200B;**[!UICONTROL Start]**。

   查看收件者表以檢查匯入已修改記錄。

   ![](assets/s_ncs_user_import_example06_05.png)

   只有空值才被文字檔中的值替換，但資料庫中的現有值未被匯入檔案中的值覆寫。

## 使用外部檔案更新並增補值 {#example--update-and-enrich-the-values-from-those-in-an-external-file}

我們希望使用文字檔修改資料庫表中的某些欄位，優先套用文字檔中包含的值。

在此範例中，您會看到文字檔中的某些欄位具有空白值，而資料庫中的對應欄位並非空白。 其他欄位包含與資料庫中的值不同的值。

* 要匯入的文字檔的內容。

  ![](assets/s_ncs_user_import_example02_04.png)

* 匯入前的資料庫狀態

  ![](assets/s_ncs_user_import_example06_07.png)

1. 選擇範本

   應用上面示例 2 中的過程。

1. 要匯入的檔案

   選擇要匯入的檔案。

   在預覽檔案的第一行時，您可以看到該檔案包含空欄位和某些記錄的更新。

1. 關聯欄位

   應用上面示例 2 中的過程。

1. 調和

   * 移至表格並選取&#x200B;**[!UICONTROL Update]**。
   * 為&#x200B;**[!UICONTROL Management of doubles]**&#x200B;欄位選取選項&#x200B;**[!UICONTROL Reject entity]**。
   * 保留選項&#x200B;**[!UICONTROL Management of duplicates]**&#x200B;為&#x200B;**[!UICONTROL Update]**&#x200B;模式，以便使用文字檔中的資料修改資料庫中的現有記錄。
   * 將游標放在&#x200B;**[!UICONTROL Account number (@account)]**&#x200B;節點上，並選取選項&#x200B;**[!UICONTROL Take empty values into account]**。
   * 選取欄位&#x200B;**[!UICONTROL Birth date]**、**[!UICONTROL Email]**&#x200B;和&#x200B;**[!UICONTROL First name]**，並指派調解金鑰給它們。

     ![](assets/s_ncs_user_import_example04_04.png)

1. 啟動匯入

   * 按一下&#x200B;**[!UICONTROL Start]**。
   * 查看收件者表以檢查操作已修改記錄。

     ![](assets/s_ncs_user_import_example06_06.png)

     清空的文字檔值已覆寫資料庫中的值。 資料庫中的現有值已更新為匯入檔案中的值，以符合在步驟4中為重複專案選取的&#x200B;**[!UICONTROL Update]**&#x200B;選項。
