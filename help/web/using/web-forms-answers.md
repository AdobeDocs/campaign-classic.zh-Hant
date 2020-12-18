---
solution: Campaign Classic
product: campaign
title: 網路表單回答
description: 網路表單回答
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---


# 網路表單回答{#web-forms-answers}

## 響應儲存欄位{#response-storage-fields}

表單答案可儲存在資料庫的欄位中，或暫時儲存在本機變數中。 欄位建立期間會選擇答案的儲存模式。 可以通過&#x200B;**[!UICONTROL Edit storage...]**&#x200B;連結編輯。

對於表單中的每個輸入欄位，可使用以下儲存選項：

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   可以選擇資料庫的欄位：使用者的答案會儲存在此欄位中。 對於每個用戶，僅保存最後輸入的值：新增至其設定檔：請參閱[將資料儲存在資料庫中](#storing-data-in-the-database)。

* **[!UICONTROL Variable]**

   如果您不想將資訊儲存在資料庫中，則可使用變數。 局部變數可宣告在上游。 請參閱[將資料儲存在本機變數](#storing-data-in-a-local-variable)。

### 在資料庫{#storing-data-in-the-database}中儲存資料

要將資料保存在資料庫的現有欄位中，請按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;表徵圖，然後從可用欄位清單中選擇它。

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>預設參考文檔是&#x200B;**nms:recipient**&#x200B;模式。 要查看或選擇新表單，請從清單中選擇表單，然後按一下&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕。

### 將資料儲存在本機變數{#storing-data-in-a-local-variable}中

您可以使用局部變數，以便即使資料未儲存在資料庫中，也能在頁面或其他頁面上重複使用資料，例如在顯示欄位時放置條件或個人化訊息。

這表示您可以使用未儲存欄位的值，授權在頁面上顯示一組選項。 在以下頁面中，車輛類型不儲存在資料庫中：

![](assets/s_ncs_admin_survey_no_storage_variable.png)

它儲存在變數中，此變數在建立下拉式方塊時必須加以選取，或透過&#x200B;**[!UICONTROL Edit storage...]**&#x200B;連結。

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

您可以透過&#x200B;**[!UICONTROL Edit variables...]**&#x200B;連結顯示現有變數並建立新變數。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以建立新變數。

![](assets/s_ncs_admin_survey_add_a_variable.png)

建立頁面的輸入欄位時，新增的變數將可在本機變數清單中使用。

>[!NOTE]
>
>您可以針對每個表單在上游建立變數。 若要這麼做，請選取表單，然後按一下&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕。 **[!UICONTROL Variables]**&#x200B;標籤包含表單的本機變數。

**具有條件的本地儲存示例**

在上例中，只有從下拉式清單中選取&#x200B;**[!UICONTROL Private]**&#x200B;選項時，才會顯示包含私人車輛相關資料的容器，如可見性條件所示：

![](assets/s_ncs_admin_survey_add_a_condition.png)

如果使用者選擇私用車輛，Web表格會提供下列選項：

![](assets/s_ncs_admin_survey_no_storage_conda.png)

如果選擇「專業版」選項，則顯示保存與商用車相關資料的容器，如可見性條件所示：

![](assets/s_ncs_admin_survey_view_a_condition.png)

這表示，如果使用者選擇商業車輛，表單會提供下列選項：

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## 使用收集到的資訊{#using-collected-information}

對於每個表單，所提供的答案都可在欄位或標籤中重複使用。 必須使用下列語法：

* 對於儲存在資料庫欄位中的內容：

   ```
   <%=ctx.recipient.@field name%
   ```

* 若是儲存在本機變數中的內容：

   ```
   <%= ctx.vars.variable name %
   ```

* 對於儲存在HTML文字欄位中的內容：

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >與其他欄位中`<%=`字元被轉義字元替換的欄位不同，HTML內容使用`<%==`語法以原樣保存。

## 保存Web表單答案{#saving-web-forms-answers}

要保存在表單頁面中收集的資訊，您需要在圖中放置一個儲存框。

![](assets/s_ncs_admin_survey_save_box.png)

使用此方塊有兩種方式：

* 如果Web表單是通過電子郵件中發送的連結訪問的，並且如果訪問應用程式的用戶已經在資料庫中，則可以檢查&#x200B;**[!UICONTROL Update the preloaded record]**&#x200B;選項。 有關詳細資訊，請參閱[通過電子郵件傳送表單](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email)。

   在這種情況下，Adobe Campaign會使用使用者設定檔的加密主要金鑰，這是Adobe Campaign指派給每個設定檔的唯一識別碼。 您需要設定資訊，以透過預載方塊預載。 有關詳細資訊，請參閱[預載入表單資料](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

   >[!CAUTION]
   >
   >此選項會覆寫使用者資料，如果有欄位要輸入，則包括電子郵件地址。 它無法用於建立新配置檔案，並需要在表單中使用預載入框。

* 要豐富資料庫中收件人的資料，請編輯儲存框並選擇協調密鑰。 對於內部使用（通常是內部網路系統）或用於建立新配置檔案（例如）的表單，您可以選擇協調欄位。 該框提供Web應用程式各頁中所用資料庫的所有欄位：

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

預設情況下，資料通過&#x200B;**[!UICONTROL Update or insertion]**&#x200B;操作導入到資料庫中：如果元素存在於資料庫中，則會更新元素（例如，選取的電子報或輸入的電子郵件地址）。 如果不存在，則會添加資訊。

不過，您可以變更此行為。 要執行此操作，請選擇元素的根，然後從下拉清單中選擇要執行的操作：

![](assets/s_ncs_admin_survey_save_operation.png)

您可以選擇協調的搜索資料夾和新配置檔案的建立資料夾。 如果這些欄位為空白，則會在運算子的預設資料夾中搜尋並建立描述檔。

>[!NOTE]
>
>可能的操作包括：**[!UICONTROL Simple reconciliation]**、**[!UICONTROL Update or insertion]**、**[!UICONTROL Insertion]**、**[!UICONTROL Update]**、**[!UICONTROL Deletion]**。\
>操作員的預設資料夾是操作員具有寫權限的第一個資料夾。\
>請參閱[本區段](../../platform/using/access-management.md)。

