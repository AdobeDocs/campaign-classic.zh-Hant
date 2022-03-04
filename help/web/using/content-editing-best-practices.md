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

為確保編輯的最佳操作，我們建議遵循以下准則：

* 之前 **導入HTML頁模板** 在Adobe Campaign，請確保模板開啟並在各種瀏覽器中正確顯示。
* 如果HTML頁包含 **JavaScript指令碼**&#x200B;他們需要執行 **無錯誤** 編輯之外。
* 建立範本時，建議將 **&#39;type&#39;** 屬性新增至標籤。`<input>`編輯器將處理此資訊，並幫助用戶在配置Web應用程式時將資料庫的欄位連結到表單的欄位。

   範本中的 HTML 程式碼範例：

   ```
   <input id="email" type="email" name="email"/>
   ```

   的 **「類型」** 屬性在介面中以下形式顯示：

   ![](assets/dce_sidebar_inputtypechanges.png)

   「type」屬性的正式清單可用 [此網站](https://www.w3schools.com/tags/att_input_type.asp)。

* 使用DCE模擬結束頁的步驟：

   ![](assets/dce_enchainement.png)

* 確保只有一個 `<body> </body>` 的雙曲餘切值。
* 上載CSS或JS檔案時，不上載.zip檔案中包含的影像。 因此，不會更新對CSS中存在的這些影像的引用。

## 內容編輯器支援的格式 {#content-editor-supported-formats}

數字內容編輯器支援HTML格式：你可以切換到 **源** 模式。

數字內容編輯器的導入功能與以下受支援的格式配合使用：

* CSS:.zip檔案中存在的影像未導入。 不更新CSS中對這些影像的引用。
* 聯署材料：.zip檔案中存在的影像未導入。 不更新JS中對這些影像的引用。
* Iframe:未導入連結的頁面。
* 登錄頁和Web應用：如果 **表格** 標籤丟失，將顯示警告。 A `<form> </form>` 必須始終在消息正文中。

「數字內容編輯器」還可與以下受支援的代碼頁配合使用：

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8（使用BOM時建議）
* iso-8859-15
* usascii
* 換擋符號
* iso-2022-jp
* 大5
* euc-kr
* utf-16

>[!NOTE]
>
>HTML代碼頁必須在元標籤(HTML4或HTML5)或物料清單中定義。 如果沒有可用的代碼頁，請開啟latin1中的檔案。

## HTML內容狀態 {#html-content-statuses}

編輯器的上部分顯示與內容狀態相關的消息。 消息的顏色代碼如下：

* **灰色消息**:消息，無需在編輯器中執行任何操作。
* **藍色消息**:與正在編輯的內容相關的資訊消息。
* **黃色消息**:警告或錯誤消息要求代表用戶執行操作。

### 編輯Web應用程式時的消息清單 {#list-of-messages-when-editing-a-web-application}

* HTML內容有效。
* Web應用程式尚未發佈，無法聯機訪問。
* Web應用程式已聯機，請再次發佈以應用任何更改。
* 頁面內容無法正常工作。 它必須包括HTML表單(`<form>`)
* 沒有要配置的輸入區域或按鈕。
* 要啟用到下一頁的轉換，您需要將「下一頁」操作連結到當前頁上的按鈕或連結。

### 編輯傳遞時的消息清單 {#list-of-messages-when-editing-a-delivery}

* 傳遞內容功能正常
* 沒有要配置的欄位或個性化塊。
* 交付內容已就緒，請再次運行分析以應用任何更改。
* 已準備好發送。
