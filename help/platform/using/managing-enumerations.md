---
solution: Campaign Classic
product: campaign
title: 管理分項清單
description: 管理分項清單
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# 管理枚舉{#managing-enumerations}

枚舉（也稱為「項目化清單」）是系統建議用於填充某些欄位的值清單。 枚舉可讓您標準化這些欄位的值，並協助您輸入資料或在查詢中使用。

值清單將顯示為下拉清單，您可以從中選擇要在欄位中輸入的值。 下拉式清單也可讓您進行預測式輸入，運算子會輸入前幾個字母，而應用程式會填入其餘的字母。

某些控制台欄位已使用此類枚舉定義。 如果您可以在對應欄位中直接輸入來新增值，則枚舉稱為「open」。

## 對值{#access-to-values}的存取

定義了此類型欄位的值，並通過樹的&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;節點對這些欄位（添加／刪除值）執行整體管理。

![](assets/s_ncs_user_itemized_list_node.png)

* 上方區段提供已定義明細清單的欄位清單。
* 下節列出建議的值。 這些值將在使用此欄位的編輯器中重複。

   ![](assets/s_ncs_user_itemized_list_values.png)

   要建立新枚舉值，請按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/s_ncs_user_itemized_list.png)

   如果選取&#x200B;**[!UICONTROL Open]**&#x200B;選項，使用者可直接在對應欄位中新增項目清單值。 確認消息允許您建立此值。

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* 如果選取&#x200B;**[!UICONTROL Closed]**&#x200B;選項，使用者將無法建立新值，而只能從可用的值中選擇。

## 標準化資料{#standardizing-data}

### 關於別名清除{#about-alias-cleansing}

在明細清單欄位中，您可以輸入列舉值以外的值。 這些檔案可以按原樣儲存，也可以清除。

>[!CAUTION]
>
>資料清理是影響資料庫中資料的關鍵過程。 Adobe Campaign進行大量資料更新，可能會導致某些值被刪除。 因此，此操作將保留給專家用戶。

輸入的值為：

* 新增至明細清單值：在這種情況下，必須選擇&#x200B;**[!UICONTROL Open]**&#x200B;選項，
* 或自動由其對應的別名替換：在這種情況下，必須在項目清單的&#x200B;**[!UICONTROL Alias]**&#x200B;標籤中定義此案例，
* 或儲存在別名清單中：稍後將為其分配別名。

   >[!NOTE]
   >
   >如果您需要使用資料清除功能，請選取項目清單中的&#x200B;**[!UICONTROL Alias cleansing]**&#x200B;選項。

### 使用別名{#using-aliases}

選項&#x200B;**[!UICONTROL Alias cleansing]**&#x200B;使選定項清單可以使用別名。 選取此選項時，窗口底部將顯示&#x200B;**[!UICONTROL Alias]**&#x200B;頁籤。

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### 建立別名{#creating-an-alias}

要建立別名，請按一下&#x200B;**[!UICONTROL Add]**。

![](assets/s_ncs_user_itemized_list_alias_create.png)

輸入要轉換的別名和要應用的值，然後按一下&#x200B;**[!UICONTROL Ok]**。

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

在確認此操作之前，請檢查參數。

>[!CAUTION]
>
>一旦此階段被確認，先前輸入的值可能無法恢復：他們被取代了。

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

因此，當用戶在&quot;company&quot;欄位(在Adobe Campaign控制台或表單中)中輸入值&#x200B;**NEILSEN**&#x200B;時，值&#x200B;**NIELSEN Ltd**&#x200B;將自動替換。 值替換由&#x200B;**別名清洗**&#x200B;工作流執行。 請參閱[執行資料清理](#running-data-cleansing)。

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### 將值轉換為別名{#converting-values-into-aliases}

要將枚舉值轉換為別名，請按一下右鍵值清單並選擇&#x200B;**[!UICONTROL Convert values into aliases...]**。

![](assets/s_ncs_user_itemized_list_alias_detail.png)

選擇要轉換的值，然後按一下&#x200B;**[!UICONTROL Next]**。

![](assets/s_ncs_user_itemized_list_alias_transform.png)

按一下&#x200B;**[!UICONTROL Start]**&#x200B;以執行轉換。

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

執行完成後，別名將添加到別名清單中。

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### 擷取別名點擊{#retrieving-alias-hits}

用戶輸入的值可以轉換為別名。 實際上，當用戶輸入未包含在項目化清單中的值時，該值將儲存在&#x200B;**[!UICONTROL Alias]**&#x200B;頁籤中。

**別名清除**&#x200B;技術工作流每晚恢復這些值以更新明細清單。 請參閱[執行資料清理](#running-data-cleansing)

如有必要，**[!UICONTROL Hits]**&#x200B;欄可顯示輸入值的次數。 計算此值既耗時又耗時。 有關詳細資訊，請參閱[計算條目發生次數](#calculating-entry-occurrences)。

### 運行資料清理{#running-data-cleansing}

資料清理由&#x200B;**[!UICONTROL Alias cleansing]**&#x200B;技術工作流執行。 為枚舉定義的配置在執行期間應用。 請參閱[別名清除工作流](#alias-cleansing-workflow)。

清洗可以通過&#x200B;**[!UICONTROL Cleanse values...]**&#x200B;連結觸發。

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

**[!UICONTROL Advanced parameters...]**&#x200B;連結可讓您設定開始將收集的值納入考量的日期。

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕以執行資料清除。

#### 計算條目發生次數{#calculating-entry-occurrences}

項目化清單的&#x200B;**[!UICONTROL Alias]**&#x200B;子標籤可顯示所有輸入值中別名的發生次數。 此資訊是估計值，將顯示在&#x200B;**[!UICONTROL Hits]**&#x200B;列中。

>[!CAUTION]
>
>計算別名條目發生次數可能需要很長時間。 這就是為什麼在使用此函式時應該小心。

您可以透過&#x200B;**[!UICONTROL Cleanse values...]**&#x200B;連結手動執行點擊計算。 若要這麼做，請按一下&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;連結，然後選取所要的選項。

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**:這可讓您根據輸入的日期更新已計算的點擊。
* **[!UICONTROL Recalculate the number of alias hits from the start]**:讓您在整個Adobe Campaign平台上進行計算。

您也可以建立專用的工作流程，讓計算在指定期間自動執行，例如每週執行一次。

要執行此操作，請建立&#x200B;**[!UICONTROL Alias cleansing]**&#x200B;工作流的副本，更改調度程式，並在&#x200B;**[!UICONTROL Enumeration value cleansing]**&#x200B;活動中使用以下設定：

* **-** updateHits以更新別名點擊數，
* **-updateHits:fullto** 重新計算所有別名點擊。

#### 別名清除工作流{#alias-cleansing-workflow}

**別名清除**&#x200B;工作流運行枚舉值清除。 依預設，會每日執行。

它通過&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;節點訪問。

![](assets/s_ncs_user_itemized_list_alias_wf.png)

