---
product: campaign
title: 網路表單回答
description: 網路表單回答
feature: Web Forms
exl-id: 5d48bb27-1884-47f1-acb7-dff5113565bc
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---

# 網路表單回答{#web-forms-answers}

![](../../assets/common.svg)

## 響應儲存欄位 {#response-storage-fields}

表單的答案可以保存在資料庫的欄位中，也可以臨時保存在本地變數中。 在建立欄位期間選擇答案的儲存模式。 可通過 **[!UICONTROL Edit storage...]** 的子菜單。

對於表單中的每個輸入欄位，可以使用以下儲存選項：

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   您可以選擇資料庫的欄位：用戶的答案將儲存在此欄位中。 對於每個用戶，只保存最後輸入的值：它被添加到他們的個人資料中：請參閱 [在資料庫中儲存資料](#storing-data-in-the-database)。

* **[!UICONTROL Variable]**

   如果不想在資料庫中儲存資訊，則可以使用變數。 局部變數可以在上游聲明。 請參閱 [將資料儲存在局部變數中](#storing-data-in-a-local-variable)。

### 在資料庫中儲存資料 {#storing-data-in-the-database}

要將資料保存在資料庫的現有欄位中，請按一下 **[!UICONTROL Edit expression]** 表徵圖，然後從可用欄位清單中選擇它。

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>預設引用文檔為 **nms：收件人** 架構。 要查看或選擇新表單，請從清單中選擇表單，然後按一下 **[!UICONTROL Properties]** 按鈕

### 將資料儲存在局部變數中 {#storing-data-in-a-local-variable}

您可以使用局部變數，這樣即使資料未儲存在資料庫中，也可以在頁面或其他頁面上重複使用，例如在顯示欄位時放置條件或個性化消息。

這意味著您可以使用未保存欄位的值授權在頁面上顯示一組選項。 在下面的頁面中，車輛類型未儲存在資料庫中：

![](assets/s_ncs_admin_survey_no_storage_variable.png)

它儲存在建立下拉框時必須選擇的變數中，或通過 **[!UICONTROL Edit storage...]** 的子菜單。

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

可以通過 **[!UICONTROL Edit variables...]** 的子菜單。 按一下 **[!UICONTROL Add]** 按鈕

![](assets/s_ncs_admin_survey_add_a_variable.png)

在建立頁面的輸入欄位時，添加的變數將在局部變數清單中可用。

>[!NOTE]
>
>對於每個表單，可以在上游建立變數。 要執行此操作，請選擇表單，然後按一下 **[!UICONTROL Properties]** 按鈕 的 **[!UICONTROL Variables]** 的子菜單。

**帶條件的本地儲存示例**

在上例中，僅當包含與私家車有關的資料的容器 **[!UICONTROL Private]** 選項，如可見性條件所示：

![](assets/s_ncs_admin_survey_add_a_condition.png)

如果用戶選擇專用車輛，則Web表單將提供以下選項：

![](assets/s_ncs_admin_survey_no_storage_conda.png)

如果選擇了「專業」選項，則保存有關商用車輛資料的容器將顯示，如可見性條件所表示：

![](assets/s_ncs_admin_survey_view_a_condition.png)

這意味著，如果用戶選擇了商用車輛，則表單將提供以下選項：

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## 使用收集的資訊 {#using-collected-information}

對於每個表單，所提供的答案可以在欄位或標籤中重新使用。 必須使用以下語法：

* 對於儲存在資料庫欄位中的內容：

   ```
   <%=ctx.recipient.@field name%
   ```

* 對於儲存在本地變數中的內容：

   ```
   <%= ctx.vars.variable name %
   ```

* 對於儲存在HTML文本欄位中的內容：

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >不像其他 `<%=` 將字元替換為轉義字元，HTML內容將按原樣保存 `<%==` 語法。

## 保存Web表單答案 {#saving-web-forms-answers}

要保存在表單頁面中收集的資訊，需要在圖中放置一個儲存框。

![](assets/s_ncs_admin_survey_save_box.png)

使用此框有兩種方法：

* 如果Web表單是通過電子郵件中發送的連結訪問的，並且訪問應用程式的用戶已在資料庫中，則可以檢查 **[!UICONTROL Update the preloaded record]** 的雙曲餘切值。 有關此內容的詳細資訊，請參閱 [通過電子郵件提交表單](publishing-a-web-form.md#delivering-a-form-via-email)。

   在這種情況下，Adobe Campaign使用用戶配置檔案的加密主鍵，這是Adobe Campaign為每個配置檔案分配的唯一標識符。 您需要通過預載入框配置資訊以預載入。 有關此內容的詳細資訊，請參閱 [預載入表單資料](publishing-a-web-form.md#pre-loading-the-form-data)。

   >[!CAUTION]
   >
   >此選項將覆蓋用戶資料，包括在其中輸入該資料的欄位的電子郵件地址。 它不能用於建立新的配置檔案，並且需要使用表單中的預載入框。

* 要豐富資料庫中收件人的資料，請編輯儲存框並選擇協調密鑰。 對於內部使用（通常為Intranet系統）或用於建立新配置檔案（例如）的表單，您可以選擇協調欄位。 該框提供了Web應用程式各頁中使用的資料庫的所有欄位：

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

預設情況下，資料由 **[!UICONTROL Update or insertion]** 操作：如果該元素存在於資料庫中，則會更新該元素（例如，所選新聞簡報或輸入的電子郵件地址）。 如果不存在，則添加該資訊。

但是，您可以更改此行為。 為此，請選擇元素的根，然後從下拉清單中選擇要執行的操作：

![](assets/s_ncs_admin_survey_save_operation.png)

您可以選擇用於協調的搜索資料夾和用於新配置檔案的建立資料夾。 如果這些欄位為空，則在運算子的預設資料夾中搜索並建立配置檔案。

>[!NOTE]
>
>可能的操作包括： **[!UICONTROL Simple reconciliation]**。 **[!UICONTROL Update or insertion]**。 **[!UICONTROL Insertion]**。 **[!UICONTROL Update]**。 **[!UICONTROL Deletion]**。\
>運算子的預設資料夾是運算子具有寫權限的第一個資料夾。\
>請參閱[本節](../../platform/using/access-management.md)。
