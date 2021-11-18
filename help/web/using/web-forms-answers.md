---
product: campaign
title: 網路表單回答
description: 網路表單回答
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 5d48bb27-1884-47f1-acb7-dff5113565bc
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---

# 網路表單回答{#web-forms-answers}

![](../../assets/common.svg)

## 回應儲存欄位 {#response-storage-fields}

表單的答案可儲存在資料庫的欄位中，或暫時儲存在本機變數中。 欄位建立期間會選擇答案的儲存模式。 您可以透過 **[!UICONTROL Edit storage...]** 連結。

對於表單中的每個輸入欄位，可使用下列儲存選項：

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   您可以選取資料庫的欄位：用戶的答案將儲存在此欄位中。 對於每個使用者，只會儲存最後輸入的值：會新增至其設定檔：請參閱 [將資料儲存在資料庫中](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   如果您不想將資訊儲存在資料庫中，則可以使用變數。 局部變數可在上游宣告。 請參閱 [將資料儲存在本機變數中](#storing-data-in-a-local-variable).

### 將資料儲存在資料庫中 {#storing-data-in-the-database}

若要將資料儲存在資料庫的現有欄位中，請按一下 **[!UICONTROL Edit expression]** 表徵圖並從可用欄位清單中選取它。

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>預設的參考文檔為 **nms:recipient** 綱要。 要查看或選擇新表單，請從清單中選擇表單，然後按一下 **[!UICONTROL Properties]** 按鈕。

### 將資料儲存在本機變數中 {#storing-data-in-a-local-variable}

您可以使用本機變數，這樣即使資料未儲存在資料庫中，也可以在頁面或其他頁面上重複使用，例如在欄位顯示上放置條件，或個人化訊息。

這表示您可以使用未儲存欄位的值，授權在頁面上顯示一組選項。 在下面的頁面中，車輛類型不會儲存在資料庫中：

![](assets/s_ncs_admin_survey_no_storage_variable.png)

它會儲存在建立下拉式方塊時必須選取的變數中，或透過 **[!UICONTROL Edit storage...]** 連結。

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

您可以顯示現有變數，並透過 **[!UICONTROL Edit variables...]** 連結。 按一下 **[!UICONTROL Add]** 按鈕以建立新變數。

![](assets/s_ncs_admin_survey_add_a_variable.png)

建立頁面的輸入欄位時，新增的變數將可供本機變數清單使用。

>[!NOTE]
>
>您可以對每個表單上游建立變數。 要執行此操作，請選取表單並按一下 **[!UICONTROL Properties]** 按鈕。 此 **[!UICONTROL Variables]** 索引標籤包含表單的本機變數。

**帶調節的本地儲存示例**

在上述範例中，只有在 **[!UICONTROL Private]** 選項，如可見性條件中所示：

![](assets/s_ncs_admin_survey_add_a_condition.png)

如果使用者選取私人車輛，Web表單會提供下列選項：

![](assets/s_ncs_admin_survey_no_storage_conda.png)

如果選擇「專業」選項（如可見性條件所表示），則顯示包含有關商用車資料的容器：

![](assets/s_ncs_admin_survey_view_a_condition.png)

這表示，如果使用者選取商業車輛，表單會提供下列選項：

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## 使用收集的資訊 {#using-collected-information}

對於每個表單，提供的答案可在欄位或標籤中重複使用。 必須使用下列語法：

* 對於儲存在資料庫欄位中的內容：

   ```
   <%=ctx.recipient.@field name%
   ```

* 若是儲存於本機變數的內容：

   ```
   <%= ctx.vars.variable name %
   ```

* 對於儲存在HTML文本欄位中的內容：

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >不同於 `<%=` 字元會被逸出字元取代，而HTML內容會使用 `<%==` 語法。

## 保存網路表單答案 {#saving-web-forms-answers}

若要儲存在表單頁面中收集的資訊，您必須在圖表中放置儲存方塊。

![](assets/s_ncs_admin_survey_save_box.png)

使用此方塊有兩種方式：

* 如果Web表單是通過電子郵件中發送的連結訪問的，並且如果訪問應用程式的用戶已在資料庫中，則可以檢查 **[!UICONTROL Update the preloaded record]** 選項。 有關詳細資訊，請參閱 [透過電子郵件傳送表單](publishing-a-web-form.md#delivering-a-form-via-email).

   在此情況下，Adobe Campaign會使用使用者設定檔的加密主要金鑰，這是Adobe Campaign為每個設定檔指派的唯一識別碼。 您需要透過預先載入方塊來設定要預先載入的資訊。 有關詳細資訊，請參閱 [預先載入表單資料](publishing-a-web-form.md#pre-loading-the-form-data).

   >[!CAUTION]
   >
   >如果有要輸入的欄位，此選項會覆寫使用者資料，包括電子郵件地址。 它無法用來建立新設定檔，且需要在表單中使用預先載入方塊。

* 要豐富資料庫中收件者的資料，請編輯儲存框並選擇調解密鑰。 對於內部使用（通常是內部網路系統）或用於建立新配置檔案（例如）的表單，您可以選擇協調欄位。 該框提供Web應用程式各頁中所用資料庫的所有欄位：

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

依預設，資料會由 **[!UICONTROL Update or insertion]** 操作：如果元素存在於資料庫中，則會更新該元素（例如，選取的電子報或輸入的電子郵件地址）。 如果不存在，則會新增資訊。

不過，您可以變更此行為。 要執行此操作，請選取元素的根，然後從下拉式清單中選取要執行的操作：

![](assets/s_ncs_admin_survey_save_operation.png)

您可以選取要協調的搜尋資料夾，以及新設定檔的建立資料夾。 如果這些欄位為空，則會搜尋設定檔，並在運算子的預設資料夾中建立。

>[!NOTE]
>
>可能的操作包括： **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>運算子的預設資料夾是運算子具有寫入權限的第一個資料夾。\
>請參閱[本節](../../platform/using/access-management.md)。
