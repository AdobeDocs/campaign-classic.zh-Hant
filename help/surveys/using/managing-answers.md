---
product: campaign
title: 管理答案
description: 瞭解如何管理調查答案
feature: Surveys
exl-id: 0b5dc602-e16f-4bf1-bd8f-352e0bc78996
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 1%

---

# 管理答案{#managing-answers}

![](../../assets/v7-only.svg)

## 儲存收集的答案 {#storing-collected-answers}

除了Adobe Campaign所有Web表單（資料庫欄位和本地變數）通用的標準儲存模式之外，調查還使用存檔欄位動態擴展資料模型。

>[!CAUTION]
>
>此選項可用於 **調查** 僅鍵入Web應用程式。 它不適用於其他類型的Web表單。

### 儲存在存檔欄位中 {#storing-in-an-archived-field}

通過添加新的儲存空間來保存調查中提供的響應，可以輕鬆擴展資料模板。 要執行此操作，請選擇 **[!UICONTROL Store answers to a question]** 的子菜單。 按一下 **[!UICONTROL New field...]** 連結並指定其屬性：

![](assets/s_ncs_admin_survey_new_space.png)

輸入欄位的標籤和名稱，然後選擇欄位類型：文本、布爾、整數或小數、日期等。

所選欄位類型涉及在用戶輸入響應時控制資料。 對於 **文本** 欄位中，可以添加約束（大小寫、格式）或連結到現有枚舉以強制選擇。

要添加約束，請從下拉清單中選擇它。 約束有兩種類型：

1. 字元大小寫

   輸入的資訊可以以下列格式儲存在欄位中：全大寫、全小寫或初始大寫。 此約束不要求用戶以選定格式輸入資料，但在欄位中輸入的內容在保存時將被轉換。

1. 資料格式

如果在清單中使用此欄位，則可以使用 **[!UICONTROL Initialize the list of values from the database]** 值清單上方的連結。

例如，您可以為用戶建立一個下拉清單以選擇其母語。 相應的存檔欄位可以與 **語言** 包含語言清單的枚舉：

![](assets/s_ncs_admin_survey_database_values_2b.png)

的 **[!UICONTROL Edit link]** 表徵圖位於欄位右側，可編輯此枚舉的內容：

![](assets/s_ncs_admin_survey_database_values_2c.png)

在 **[!UICONTROL General]** 的 **[!UICONTROL Initialize the list of values from the database]** 連結允許您自動輸入提供的標籤清單。

![](assets/s_ncs_admin_survey_database_values_2.png)

**示例**:將收件人的合同儲存在一個欄位中

要在一個欄位中儲存不同類型的合同，請建立 **[!UICONTROL Text]** 輸入欄位，然後選擇 **[!UICONTROL Store answers to a question]** 的雙曲餘切值。

按一下 **[!UICONTROL New field...]** 連結並輸入欄位屬性。 選擇 **[!UICONTROL Multiple values]** 選項以啟用要儲存的多個值。

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

為其他合同建立條目欄位，並將資料儲存在同一存檔欄位中。

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

當用戶批准調查時，其答案將儲存在 **[!UICONTROL Contracts]** 的子菜單。

在本例中，針對以下答案：

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

被申請人的簡介將包含所輸入的四份合同。

可以在 **[!UICONTROL Answers]** 的子菜單。

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

您還可以根據答案篩選收件人，以僅顯示您感興趣的用戶。 要執行此操作，請建立目標工作流並使用 **[!UICONTROL Survey responses]** 框。

![](assets/s_ncs_admin_survey_read_responses_wf.png)

根據要恢復的配置檔案建立查詢。 在下例中，查詢允許您選擇至少具有兩個合同（包括A類型合同）的配置檔案。

![](assets/s_ncs_admin_survey_read_responses_edit.png)

對於每個表單，提供的答案可用於欄位或標籤中。 對儲存在存檔欄位中的內容使用以下語法：

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>對於其他類型的欄位，語法在 [此部分](../../platform/using/about-queries-in-campaign.md)。

### 儲存設定 {#storage-settings}

您可以以XML格式存檔調查的答案。 這允許您保存收集的答案的原始副本，在對明細清單中的資料進行過度標準化時，此副本非常有用。 [了解更多](../../surveys/using/publish--track-and-use-collected-data.md#standardizing-data)

>[!CAUTION]
>
>歸檔原始響應會影響所需的儲存空間。 謹慎使用此選項。

操作步驟：

* 通過 **[!UICONTROL Properties]** 按鈕 **[!UICONTROL Edit]** 頁籤。
* 按一下 **[!UICONTROL Advanced parameters]** 連結並檢查 **[!UICONTROL Save a copy of raw answers]** 的雙曲餘切值。

![](assets/s_ncs_admin_survey_xml_archive_option.png)

預設情況下，您可以為所有調查啟用此選項（在發佈調查時應用此選項）。 為此，請建立 **[!UICONTROL NmsWebApp_XmlBackup]** 選項和賦值 **[!UICONTROL 1]** 如下所示：

![](assets/s_ncs_admin_survey_xml_global_option.png)

## 分數管理 {#score-management}

您可以為表單頁面中提供的選項分配分數。 分數只能連結到已結問題：複選框、下拉清單中的值、訂閱等。

![](assets/s_ncs_admin_survey_score_create.png)

當確認頁面時，即當用戶按一下頁面時，分數被累積並保存在伺服器端 **[!UICONTROL Next]** 或 **[!UICONTROL Finish]** 按鈕

>[!NOTE]
>
>可以使用正值或負值、整數值或非整數值。

分數可用於test或指令碼。

>[!CAUTION]
>
>分數不能用於同一頁上欄位的可見性條件。 但是，它們可以在後續頁面中使用。

* 要在test中使用分數，請使用 **[!UICONTROL Score]** 欄位，如下所示：

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* 可以在指令碼中使用分數。

**示例**:計算分數並將其用作顯示下一頁的條件：

* 在調查中，下一頁允許您根據下拉清單中選擇的值為用戶分配不同的分數：

   ![](assets/s_ncs_admin_survey_score_exa.png)

* 根據所選選項，可以將此分數與第二個值合併：

   ![](assets/s_ncs_admin_survey_score_exb.png)

* 當用戶按一下 **[!UICONTROL Next]** 按鈕，將這兩個值相加。

   ![](assets/s_ncs_admin_survey_score_exe.png)

* 可根據分數對要顯示的頁面應用條件。 配置如下：

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)
