---
title: 管理枚舉
seo-title: 管理枚舉
description: 管理枚舉
seo-description: null
page-status-flag: never-activated
uuid: 23ad4cae-237f-48e5-b111-cfe88cf0b864
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 7674c856-2b64-4a85-9ffa-3e14a142028e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 管理枚舉{#managing-enumerations}

## 關於枚舉 {#about-enumerations}

枚舉（也稱為「項目化清單」）是系統建議用於填充某些欄位的值清單。 枚舉可讓您標準化這些欄位的值，並協助您輸入資料或在查詢中使用。

值清單將顯示為下拉清單，您可以從中選擇要在欄位中輸入的值。 下拉式清單也可讓您進行預測式輸入，運算子會輸入前幾個字母，而應用程式會填入其餘的字母。

某些控制台欄位已使用此類枚舉定義。 如果您可以在對應欄位中直接輸入來新增值，則枚舉稱為「open」。

## 存取值 {#access-to-values}

定義了此類型欄位的值，並通過樹的節點對這些欄位（添加／刪除值）執行 **[!UICONTROL Administration > Platform > Enumerations]** 整體管理。

![](assets/s_ncs_user_itemized_list_node.png)

* 上方區段提供已定義明細清單的欄位清單。
* 下節列出建議的值。 這些值將在使用此欄位的編輯器中重複。

   ![](assets/s_ncs_user_itemized_list_values.png)

   要建立新枚舉值，請按一下 **[!UICONTROL Add]**。

   ![](assets/s_ncs_user_itemized_list.png)

   如果選 **[!UICONTROL Open]** 取該選項，使用者可直接在對應欄位中新增項目清單值。 確認消息允許您建立此值。

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* 如果選 **[!UICONTROL Closed]** 取該選項，使用者將無法建立新值，而只能從可用的值中選擇。

## 標準化資料 {#standardizing-data}

### 關於化名清洗 {#about-alias-cleansing}

在明細清單欄位中，您可以輸入列舉值以外的值。 這些檔案可以按原樣儲存，也可以清除。

>[!CAUTION]
>
>資料清理是影響資料庫中資料的關鍵過程。 Adobe Campaign會進行大量資料更新，這可能會導致刪除某些值。 因此，此操作將保留給專家用戶。

輸入的值為：

* 新增至明細清單值：在這種情況下，必 **[!UICONTROL Open]** 須選擇該選項，
* 或自動由其對應的別名替換：在這種情況下，必須在項目清單的標 **[!UICONTROL Alias]** 簽中定義此案例，
* 或儲存在別名清單中：稍後將為其分配別名。

   >[!NOTE]
   >
   >如果您需要使用資料清除功能，請選取 **[!UICONTROL Alias cleansing]** 項目清單中的選項。

### 使用別名 {#using-aliases}

此選項 **[!UICONTROL Alias cleansing]** 可使用所選項目清單的別名。 選取此選項時，該選 **[!UICONTROL Alias]** 項卡將顯示在窗口底部。

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### 建立別名 {#creating-an-alias}

要建立別名，請按一下 **[!UICONTROL Add]**。

![](assets/s_ncs_user_itemized_list_alias_create.png)

輸入要轉換的別名和要應用的值，然後按一下 **[!UICONTROL Ok]**。

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

在確認此操作之前，請檢查參數。

>[!CAUTION]
>
>一旦此階段被確認，先前輸入的值可能無法恢復：他們被取代了。

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

因此，當使用者在「公司」欄位（在Adobe Campaign主控台或表單中）中輸入值 **NEILSEN** 時，值 **NIELSEN Ltd**。值替換由別名清除工 **作流程執** 行。 請參閱 [執行資料清理](#running-data-cleansing)。

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### 將值轉換為別名 {#converting-values-into-aliases}

要將枚舉值轉換為別名，請按一下右鍵值清單並選擇 **[!UICONTROL Convert values into aliases...]**。

![](assets/s_ncs_user_itemized_list_alias_detail.png)

選擇要轉換的值，然後按一下 **[!UICONTROL Next]**。

![](assets/s_ncs_user_itemized_list_alias_transform.png)

按一 **[!UICONTROL Start]** 下以執行轉換。

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

執行完成後，別名將添加到別名清單中。

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### 檢索別名點擊 {#retrieving-alias-hits}

用戶輸入的值可以轉換為別名。 實際上，當使用者輸入項目清單中未包含的值時，該值會儲存在標籤中 **[!UICONTROL Alias]** 。

別名清 **除技術工作流** ，每晚都會恢復這些值，以更新明細清單。 請參閱執 [行資料清理](#running-data-cleansing)

如有必要， **[!UICONTROL Hits]** 欄可顯示輸入值的次數。 計算此值既耗時又耗時。 有關詳細資訊，請參閱計 [算條目發生次數](#calculating-entry-occurrences)。

### 執行資料清理 {#running-data-cleansing}

資料清理由技術工作流 **[!UICONTROL Alias cleansing]** 程執行。 為枚舉定義的配置在執行期間應用。 請參閱別名 [清除工作流程](#alias-cleansing-workflow)。

清洗可以通過該鏈 **[!UICONTROL Cleanse values...]** 路觸發。

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

連 **[!UICONTROL Advanced parameters...]** 結可讓您設定開始將收集的值納入考量的日期。

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

按一下按 **[!UICONTROL Start]** 鈕以執行資料清理。

#### 計算條目發生次數 {#calculating-entry-occurrences}

項目 **[!UICONTROL Alias]** 化清單的子標籤可顯示所有輸入值中別名的發生次數。 此資訊是估計值，會顯示在欄 **[!UICONTROL Hits]** 中。

>[!CAUTION]
>
>計算別名條目發生次數可能需要很長時間。 這就是為什麼在使用此函式時應該小心。

您可以透過連結手動執行點擊 **[!UICONTROL Cleanse values...]** 計算。 若要這麼做，請按一 **[!UICONTROL Advanced parameters...]** 下連結並選取所要的選項。

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**:這可讓您根據輸入的日期更新已計算的點擊。
* **[!UICONTROL Recalculate the number of alias hits from the start]**:可讓您在整個Adobe Campaign平台上執行計算。

您也可以建立專用的工作流程，讓計算在指定期間自動執行，例如每週執行一次。

要執行此操作，請建立工作流的副 **[!UICONTROL Alias cleansing]** 本，更改調度程式，並在活動中使用以下 **[!UICONTROL Enumeration value cleansing]** 設定：

* **-updateHits** ，以更新別名點擊數，
* **-updateHits:full** ，重新計算所有別名點擊。

#### 別名清除工作流程 {#alias-cleansing-workflow}

別名清 **除工作流** ，運行枚舉值清除。 依預設，會每日執行。

它通過節點 **[!UICONTROL Administration > Production > Technical workflows]** 訪問。

![](assets/s_ncs_user_itemized_list_alias_wf.png)

