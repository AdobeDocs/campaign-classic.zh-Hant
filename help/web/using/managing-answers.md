---
title: 管理答案
seo-title: 管理答案
description: 管理答案
seo-description: null
page-status-flag: never-activated
uuid: 329e2f4a-c5bc-4654-bdef-71a0818fc2b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: affecd87-00a3-4d50-92d3-31ac6228948b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 管理答案{#managing-answers}

## 儲存收集的答案 {#storing-collected-answers}

除了Adobe Campaign中所有Web表單（資料庫欄位和本機變數）常用的標準儲存模式外，調查還可使用封存欄位動態擴充資料模型。

>[!CAUTION]
>
>此選項僅適用於「調 **查類型** 」的Web應用程式。 其他類型的Web表單則不提供。

### 儲存在歸檔欄位中 {#storing-in-an-archived-field}

新增儲存空間以儲存調查中提供的回應，以輕鬆擴充資料範本。 若要這麼做，請在建立輸 **[!UICONTROL Store answers to a question]** 入欄位時選取選項。 按一下連 **[!UICONTROL New field...]** 結並指定其屬性：

![](assets/s_ncs_admin_survey_new_space.png)

輸入欄位的標籤和名稱，然後選擇欄位類型：文字、布林、整數或小數、日期等。

選取的欄位類型包含使用者輸入回應時的資料控制。 對於 **文本欄位** ，可以添加約束（大小寫、格式）或現有枚舉的連結以強制選擇。

若要新增約束，請從下拉式清單中選取它。 約束有兩種類型：

1. 字元大小寫

   輸入的資訊可以以下列格式儲存在欄位中：全部大寫、全部小寫或初始大寫。 此約束不要求用戶以選定格式輸入資料，但在保存時，在欄位中輸入的內容將進行轉換。

1. 資料格式

如果此欄位用於清單，則可以使用值清單上方的連結在值表中自動 **[!UICONTROL Initialize the list of values from the database]** 檢索枚舉的值。

例如，您可以為使用者建立下拉式清單，以選取其原生語言。 對應的已封存欄位可與語言列舉 **關聯** ，其中包含語言清單：

![](assets/s_ncs_admin_survey_database_values_2b.png)

位 **[!UICONTROL Edit link]** 於欄位右側的圖示可讓您編輯此列舉的內容：

![](assets/s_ncs_admin_survey_database_values_2c.png)

在欄位 **[!UICONTROL General]** 的標籤中，連結可 **[!UICONTROL Initialize the list of values from the database]** 讓您自動輸入所提供的標籤清單。

![](assets/s_ncs_admin_survey_database_values_2.png)

**範例**:將收件者的合約儲存在一個欄位中

若要在一個欄位中儲存不同類型的合約，請建立輸 **[!UICONTROL Text]** 入欄位並選取 **[!UICONTROL Store answers to a question]** 選項。

按一下該 **[!UICONTROL New field...]** 連結並輸入欄位屬性。 選取選 **[!UICONTROL Multiple values]** 項以啟用要儲存的數個值。

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

為其他合約建立項目欄位，並將資料儲存在相同的封存欄位中。

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

當使用者核准調查時，其答案會儲存在欄位 **[!UICONTROL Contracts]** 中。

在我們的範例中，以下是答案：

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

回應者的個人檔案將包含所輸入的四份合約。

您可在調查的標籤中 **[!UICONTROL Answers]** 顯示相關欄來檢視這些欄位。

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

您也可以根據答案來篩選收件者，只顯示您感興趣的使用者。 若要這麼做，請建立定位工作流程並使用方 **[!UICONTROL Survey responses]** 塊。

![](assets/s_ncs_admin_survey_read_responses_wf.png)

根據要恢復的配置檔案建立查詢。 在以下示例中，查詢允許您選擇至少具有兩個合同的配置檔案，包括A類型合同。

![](assets/s_ncs_admin_survey_read_responses_edit.png)

對於每個表單，提供的答案都可用於欄位或標籤。 對儲存在封存欄位中的內容使用下列語法：

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>對於其他類型的欄位，本節將詳述語 [法](../../platform/using/about-queries-in-campaign.md)。

### 儲存區設定 {#storage-settings}

您可以以XML格式封存調查的答案。 這可讓您儲存所收集回答的原始副本，當項目清單中的資料過於標準化時，這可以派上用場(如需詳細資訊，請參閱標準化 [資料](../../web/using/publish--track-and-use-collected-data.md#standardizing-data))。

>[!CAUTION]
>
>封存原始回應可大幅增加所需的儲存空間。 小心使用這個選項。

操作步驟：

* 透過標籤的按鈕 **[!UICONTROL Properties]** 編輯調查屬 **[!UICONTROL Edit]** 性。
* 按一下 **[!UICONTROL Advanced parameters]** 連結並勾選 **[!UICONTROL Save a copy of raw answers]** 選項。

![](assets/s_ncs_admin_survey_xml_archive_option.png)

您可依預設為所有調查啟用此選項（此選項會在發佈調查時套用）。 若要這麼做，請建立 **[!UICONTROL NmsWebApp_XmlBackup]** 選項並指派 **[!UICONTROL 1]** 值給它，如下所示：

![](assets/s_ncs_admin_survey_xml_global_option.png)

## 分數管理 {#score-management}

您可以為表單頁面中提供的選項指派分數。 分數只能連結至已結束的問題：核取方塊、下拉式清單中的值、訂閱等。

>[!CAUTION]
>
>分數管理僅適用於 **調查** 。

![](assets/s_ncs_admin_survey_score_create.png)

當確認頁面時（即當使用者按一下或按鈕時），分數會累積並儲存在伺 **[!UICONTROL Next]** 服器 **[!UICONTROL Finish]** 端。

>[!NOTE]
>
>您可以使用正值或負值、整數或非整數值。

分數可用於測試或指令碼。

>[!CAUTION]
>
>分數無法用於相同頁面上欄位的可見性條件。 但是，它們可用於後續頁面。

* 若要在測試中使用分數，請使 **[!UICONTROL Score]** 用測試計算公式中的欄位，如下所示：

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* 您可以在指令檔中使用分數。

**範例**:計算分數，並將其用作顯示下一頁的條件：

* 在調查中，下一頁可讓您根據下拉式清單中選取的值，為使用者指派不同的分數：

   ![](assets/s_ncs_admin_survey_score_exa.png)

* 您可以根據選取的選項，將此分數與第二個值結合：

   ![](assets/s_ncs_admin_survey_score_exb.png)

* 當使用者按一下按 **[!UICONTROL Next]** 鈕時，會加上兩個值。

   ![](assets/s_ncs_admin_survey_score_exe.png)

* 條件可套用至要根據分數顯示的頁面。 此配置如下：

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

