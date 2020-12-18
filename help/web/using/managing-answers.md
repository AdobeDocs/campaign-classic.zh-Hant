---
solution: Campaign Classic
product: campaign
title: 管理答案
description: 管理答案
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 1%

---


# 管理答案{#managing-answers}

## 儲存收集的答案{#storing-collected-answers}

除了Adobe Campaign中所有Web表單（資料庫欄位和本機變數）常用的標準儲存模式外，調查還可使用封存欄位動態擴充資料模型。

>[!CAUTION]
>
>此選項僅適用於&#x200B;**Survey**&#x200B;類型的Web應用程式。 其他類型的Web表單則不提供。

### 儲存在存檔欄位{#storing-in-an-archived-field}中

新增儲存空間以儲存調查中提供的回應，以輕鬆擴充資料範本。 要執行此操作，請在建立輸入欄位時選擇&#x200B;**[!UICONTROL Store answers to a question]**&#x200B;選項。 按一下&#x200B;**[!UICONTROL New field...]**&#x200B;連結並指定其屬性：

![](assets/s_ncs_admin_survey_new_space.png)

輸入欄位的標籤和名稱，然後選擇欄位類型：文字、布林、整數或小數、日期等。

選取的欄位類型包含使用者輸入回應時的資料控制。 對於&#x200B;**text**&#x200B;欄位，可以添加約束（大小寫、格式）或現有枚舉的連結以強制選擇。

若要新增約束，請從下拉式清單中選取它。 約束有兩種類型：

1. 字元大小寫

   輸入的資訊可以以下列格式儲存在欄位中：全部大寫、全部小寫或初始大寫。 此約束不要求用戶以選定格式輸入資料，但在保存時，在欄位中輸入的內容將進行轉換。

1. 資料格式

如果此欄位用於清單，則可以使用值清單上方的&#x200B;**[!UICONTROL Initialize the list of values from the database]**&#x200B;連結在值表中自動檢索枚舉的值。

例如，您可以為使用者建立下拉式清單，以選取其原生語言。 對應的已封存欄位可與&#x200B;**language**&#x200B;列舉關聯，該列舉包含語言清單：

![](assets/s_ncs_admin_survey_database_values_2b.png)

位於欄位右側的&#x200B;**[!UICONTROL Edit link]**&#x200B;圖示可讓您編輯此列舉的內容：

![](assets/s_ncs_admin_survey_database_values_2c.png)

在欄位的&#x200B;**[!UICONTROL General]**&#x200B;標籤中， **[!UICONTROL Initialize the list of values from the database]**&#x200B;連結可讓您自動輸入提供的標籤清單。

![](assets/s_ncs_admin_survey_database_values_2.png)

**範例**:將收件者的合約儲存在一個欄位中

要在一個欄位中儲存不同類型的合同，請建立一個&#x200B;**[!UICONTROL Text]**&#x200B;輸入欄位並選擇&#x200B;**[!UICONTROL Store answers to a question]**&#x200B;選項。

按一下&#x200B;**[!UICONTROL New field...]**&#x200B;連結並輸入欄位屬性。 選擇&#x200B;**[!UICONTROL Multiple values]**&#x200B;選項以啟用要儲存的多個值。

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

為其他合約建立項目欄位，並將資料儲存在相同的封存欄位中。

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

當使用者核准調查時，其答案會儲存在&#x200B;**[!UICONTROL Contracts]**&#x200B;欄位中。

在我們的範例中，以下是答案：

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

回應者的個人檔案將包含所輸入的四份合約。

您可在調查的&#x200B;**[!UICONTROL Answers]**&#x200B;標籤中，顯示相關欄以檢視這些欄。

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

您也可以根據答案來篩選收件者，只顯示您感興趣的使用者。 若要這麼做，請建立定位工作流程並使用&#x200B;**[!UICONTROL Survey responses]**&#x200B;方塊。

![](assets/s_ncs_admin_survey_read_responses_wf.png)

根據要恢復的配置檔案建立查詢。 在以下示例中，查詢允許您選擇至少具有兩個合同的配置檔案，包括A類型合同。

![](assets/s_ncs_admin_survey_read_responses_edit.png)

對於每個表單，提供的答案都可用於欄位或標籤。 對儲存在封存欄位中的內容使用下列語法：

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>對於其他類型的欄位，[本節](../../platform/using/about-queries-in-campaign.md)將詳細介紹語法。

### 儲存設定{#storage-settings}

您可以以XML格式封存調查的答案。 這可讓您儲存所收集回答的原始副本，當項目清單中的資料標準化程度過高時，此功能會很有用（如需詳細資訊，請參閱[標準化資料](../../web/using/publish--track-and-use-collected-data.md#standardizing-data)）。

>[!CAUTION]
>
>封存原始回應可大幅增加所需的儲存空間。 小心使用這個選項。

操作步驟：

* 透過&#x200B;**[!UICONTROL Edit]**&#x200B;標籤的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕編輯調查屬性。
* 按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結並選中&#x200B;**[!UICONTROL Save a copy of raw answers]**&#x200B;選項。

![](assets/s_ncs_admin_survey_xml_archive_option.png)

您可依預設為所有調查啟用此選項（此選項會在發佈調查時套用）。 若要這麼做，請建立&#x200B;**[!UICONTROL NmsWebApp_XmlBackup]**&#x200B;選項並指派值&#x200B;**[!UICONTROL 1]**，如下所示：

![](assets/s_ncs_admin_survey_xml_global_option.png)

## 分數管理{#score-management}

您可以為表單頁面中提供的選項指派分數。 分數只能連結至已結束的問題：核取方塊、下拉式清單中的值、訂閱等。

>[!CAUTION]
>
>分數管理僅適用於&#x200B;**調查**。

![](assets/s_ncs_admin_survey_score_create.png)

當確認頁面時，即當使用者按一下&#x200B;**[!UICONTROL Next]**&#x200B;或&#x200B;**[!UICONTROL Finish]**&#x200B;按鈕時，分數會累積並儲存在伺服器端。

>[!NOTE]
>
>您可以使用正值或負值、整數或非整數值。

分數可用於測試或指令碼。

>[!CAUTION]
>
>分數無法用於相同頁面上欄位的可見性條件。 但是，它們可用於後續頁面。

* 若要在測試中使用分數，請使用測試計算公式中的&#x200B;**[!UICONTROL Score]**&#x200B;欄位，如下所示：

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* 您可以在指令檔中使用分數。

**範例**:計算分數，並將其用作顯示下一頁的條件：

* 在調查中，下一頁可讓您根據下拉式清單中選取的值，為使用者指派不同的分數：

   ![](assets/s_ncs_admin_survey_score_exa.png)

* 您可以根據選取的選項，將此分數與第二個值結合：

   ![](assets/s_ncs_admin_survey_score_exb.png)

* 當使用者按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕時，會加上兩個值。

   ![](assets/s_ncs_admin_survey_score_exe.png)

* 條件可套用至要根據分數顯示的頁面。 此配置如下：

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

