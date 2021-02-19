---
solution: Campaign Classic
product: campaign
title: 內容編輯最佳實務
description: 內容編輯最佳實務
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---


# 內容編輯最佳實務{#content-editing-best-practices}

為確保編輯的最佳作業，我們建議遵守下列准則：

* 在&#x200B;**匯入Adobe Campaign中的HTML頁面範本**&#x200B;之前，請確定範本已開啟並正確顯示在各種瀏覽器中。
* 如果HTML頁面包含&#x200B;**JavaScript指令碼**，則需要在編輯器外執行&#x200B;**，而不需出現錯誤**。
* 建立範本時，建議將 **&#39;type&#39;** 屬性新增至標籤。`<input>`編輯器將處理此資訊，並幫助用戶在配置Web應用程式時將資料庫的欄位連結到表單的欄位。

   範本中的 HTML 程式碼範例：

   ```
   <input id="email" type="email" name="email"/>
   ```

   **&#39;type&#39;**&#x200B;屬性在介面中以下列格式顯示：

   ![](assets/dce_sidebar_inputtypechanges.png)

   此網站](https://www.w3schools.com/tags/att_input_type.asp)提供「類型」屬性的正式清單。[

* 使用DCE模擬結束頁的步驟：

   ![](assets/dce_enchainement.png)

* 請確定頁面中只有一個`<body> </body>`。
* 上傳CSS或JS檔案時，不會上傳包含在。zip檔案中的影像。 因此，CSS中這些影像的參考不會更新。

## 內容編輯器支援的格式{#content-editor-supported-formats}

數位內容編輯器支援HTML格式：您可以隨時切換至&#x200B;**source**&#x200B;模式。

數位內容編輯器的匯入功能與下列支援的格式如下：

* CSS:.zip檔案中的影像不會匯入。 CSS中這些影像的參考不會更新。
* JS:.zip檔案中的影像不會匯入。 JS中對這些影像的參照不會更新。
* Iframe:連結的頁面不會匯入。
* 著陸頁面與網頁應用程式：如果&#x200B;**form**&#x200B;標籤遺失，則會出現警告。 `<form> </form>`必須始終存在於消息主體中。

數位內容編輯器也適用於下列支援的程式碼頁面：

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8（使用BOM時建議）
* iso-8859-15
* us-ascii
* shift jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>HTML程式碼頁面必須定義在meta標籤（HTML 4或HTML 5）或BOM中。 如果沒有可用的代碼頁，請開啟latin1中的檔案。

## HTML內容狀態{#html-content-statuses}

編輯器的上部區域顯示與內容狀態相關的消息。 消息的顏色代碼如下：

* **灰色訊息**:資訊消息，編輯器中不需要執行任何操作。
* **藍色訊息**:與正在編輯的內容相關的資訊消息。
* **黃色消息**:警告或錯誤訊息，要求代表使用者採取行動。

### 編輯Web應用程式{#list-of-messages-when-editing-a-web-application}時的消息清單

* HTML內容可正常運作。
* Web應用程式尚未發佈，無法線上存取。
* Web應用程式已線上，請再次發佈以套用任何變更。
* 頁面內容無法正常運作。 它必須包含HTML表單(`<form>`)
* 沒有要配置的輸入區域或按鈕。
* 若要啟用轉換至下一頁，您必須將「下一頁」動作連結至目前頁面上的按鈕或連結。

### 編輯傳送{#list-of-messages-when-editing-a-delivery}時的訊息清單

* 傳送內容具功能
* 沒有欄位或個人化區塊可供設定。
* 傳送內容已就緒，請重新執行分析以套用任何變更。
* 傳送已準備好。

