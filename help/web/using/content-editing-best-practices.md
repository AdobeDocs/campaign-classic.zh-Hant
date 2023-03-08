---
product: campaign
title: 內容編輯最佳實務
description: 內容編輯最佳實務
feature: Web Apps, Web Forms, Landing Pages
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---

# 內容編輯最佳實務{#content-editing-best-practices}

![](../../assets/common.svg)

為確保編輯者的最佳操作，建議您遵循下列准則：

* 之前 **匯入HTML頁面範本** 在Adobe Campaign中，請確定範本會在各種瀏覽器中開啟並正確顯示。
* 如果HTML頁面包含 **JavaScript指令碼**，需執行 **無錯誤** 編輯之外。
* 建立範本時，建議將 **&#39;type&#39;** 屬性新增至標籤。`<input>`編輯器將處理此資訊，並幫助用戶在配置Web應用程式時將資料庫的欄位連結到表單的欄位。

   範本中的 HTML 程式碼範例：

   ```
   <input id="email" type="email" name="email"/>
   ```

   此 **&#39;type&#39;** 屬性以下列形式顯示在介面中：

   ![](assets/dce_sidebar_inputtypechanges.png)

   可使用「類型」屬性的正式清單 [在](https://www.w3schools.com/tags/att_input_type.asp).

* 使用DCE模擬結束頁的步驟：

   ![](assets/dce_enchainement.png)

* 確定只有一個 `<body> </body>` 中。
* 上傳CSS或JS檔案時，不會上傳.zip檔案中包含的影像。 因此，CSS中對這些影像的參考不會更新。

## 內容編輯器支援的格式 {#content-editor-supported-formats}

數位內容編輯器支援HTML格式：您可以切換至 **來源** 模式。

數位內容編輯器的匯入功能可搭配下列支援的格式運作：

* CSS:系統不會匯入.zip檔案中顯示的影像。 CSS中對這些影像的參考不會更新。
* JS:系統不會匯入.zip檔案中顯示的影像。 JS中對這些影像的參考不會更新。
* Iframe:連結的頁面不會匯入。
* 登錄頁面和網頁應用程式：如果 **表單** 標籤遺失，則會出現警告。 A `<form> </form>` 訊息內文中必須一律存在。

數位內容編輯器也可搭配下列支援的程式碼頁面使用：

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
>HTML代碼頁必須在元標籤(HTML4或HTML5)或物料清單中定義。 如果沒有可用的代碼頁，請開啟latin1中的檔案。

## HTML內容狀態 {#html-content-statuses}

編輯器的上方區段顯示與內容狀態相關的訊息。 訊息的顏色代碼如下：

* **灰色訊息**:資訊訊息，編輯器中不需要執行任何動作。
* **藍色訊息**:與正在編輯的內容相關的資訊消息。
* **黃色訊息**:需要代表使用者採取動作的警告或錯誤訊息。

### 編輯Web應用程式時的消息清單 {#list-of-messages-when-editing-a-web-application}

* HTML內容可正常運作。
* Web應用程式尚未發佈，無法聯機訪問。
* Web應用程式已聯機，請重新發佈以應用任何更改。
* 頁面內容無法正常運作。 必須包含HTML表單(`<form>`)
* 沒有要配置的輸入區域或按鈕。
* 若要啟用轉變至下一頁，您必須將「下一頁」動作連結至目前頁面上的按鈕或連結。

### 編輯傳送時的訊息清單 {#list-of-messages-when-editing-a-delivery}

* 傳遞內容可正常運作
* 沒有要設定的欄位或個人化區塊。
* 傳遞內容已就緒，請再次執行分析以套用任何變更。
* 已準備好傳送。
