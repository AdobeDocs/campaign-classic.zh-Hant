---
product: campaign
title: 設定Campaign回應管理員
description: 瞭解如何設定Campaign回應管理員
feature: Campaigns
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# 設定Campaign回應管理員{#configuration}



本節適用於負責設定回應管理的人員。 它假定您有一定的知識來擴充結構描述、定義工作流程和SQL程式設計。

這可讓您瞭解如何使用個人資料表，來調整標準資料模型，以符合Adobe Campaign外部交易表的特定性質。 此個人表格可與Adobe Campaign中的可用個人表格或其他表格保持一致

測量假設由作業程式工作流程啟動( **[!UICONTROL operationMgt]** )。 每個假設代表一個以執行狀態（正在編輯、擱置中、已完成、失敗等）非同步執行的個別程式 由管理優先順序限制、同時處理序數限制、低活動頁面及頻率自動執行的排程器控制。

## 設定方案 {#configuring-schemas}

>[!CAUTION]
>
>請勿修改應用程式的內建方案，而是使用方案擴充機制。 否則，修改後的結構描述將不會在應用程式未來升級時更新。 這可能在使用Adobe Campaign時導致功能錯誤。

必須先整合應用程式，才能使用反應模組，定義要測量的各種表格（交易、交易詳細資訊），以及其與傳送、選件及個人的關係。

### 標準結構描述 {#standard-schemas}

現成可用 **[!UICONTROL nms:remaMatch]** 綱要包含反應記錄表，即個人、假設和交易表之間的關係。 此結構描述應作為反應記錄最終目的地表格的繼承結構描述。

此 **[!UICONTROL nms:remaMatchRcp]** 綱要也是標準方案，其中包含Adobe Campaign收件者的反應記錄儲存( **[!UICONTROL nms:recipient]** )。 為了使用，需要將其擴充以對映至交易表（包含購買等）。

### 交易表格與交易詳細資訊 {#transaction-tables-and-transaction-details}

交易表必須包含指向個人的直接連結。

您也可以新增包含交易詳細資訊的表格。 此檔案不會直接連結至個人。

以收款為例，交易表格會連結至聯絡人（收款表格），而收款明細行表格只會連結至收款表格（明細表格）。 然後，您可以在收貨單明細表連結至收貨單表格的層次，直接設定假設。

>[!NOTE]
>
>如果要保留描述假設中預期行為的收款識別碼，可以擴充nms：remaMatchRcp表格範本，以新增該識別碼（在此情況下，ROI計算不會連結到這些欄位）。

我們強烈建議您新增事件日期。

組態完成後，下列綱要會顯示不同表格之間的聯結：

![](assets/response_data_model.png)

### 回應管理與收件者 {#response-management-with-adobe-campaign-recipients}

在此範例中，我們將使用Adobe Campaign內建的收件者表格，在回應管理模組中整合購買表格 **[!UICONTROL nms:recipient]**.

上的回應記錄表格 **[!UICONTROL nms:remaMatchRcp]** 收件者已擴充為新增購買表格結構的連結。 在下列範例中，會呼叫購買表格 **demo：purchase**.

1. 透過Adobe Campaign檔案總管，選取 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. 按一下右鍵 **收件者** 然後選取 **[!UICONTROL Actions]** 和 **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. 您可以個人化 **[!UICONTROL Extension namespace]** 在下一個視窗中，然後按一下 **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. 在 **[!UICONTROL Response management]** 類別，確認 **[!UICONTROL Generate a storage schema for reactions]** 方塊是否已勾選。

   然後按一下 **[!UICONTROL Define additional fields...]** 以選取相關的交易表格，並將所需的欄位新增至nms：remaMatchRcp綱要的延伸模組。

   ![](assets/delivery_mapping3.png)

建立的結構描述如下所示：

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### 使用個人化收件者表格的回應管理 {#response-management-with-a-personalized-recipient-table}

在此範例中，我們將使用Adobe Campaign中可用收件者表格以外的個人表格，將購買表格整合到回應管理模組中。

* 建立衍生自以下專案的新回應記錄結構： **[!UICONTROL nms:remaMatch]** 綱要。

  由於個人表格與Adobe Campaign收件者表格不同，因此需要根據以下專案建立回應記錄的新結構描述： **[!UICONTROL nms:remaMatch]** 綱要。 然後填寫傳送記錄和購買表格的連結。

  在下列範例中，我們將使用 **demo：broadLogPers** 綱要和 **demo：purchase** 交易表：

  ```
  <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
  img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
    <element name="remaMatchPers" template="nms:remaMatch">
      <key internal="true" name="match">
        <keyfield xlink="hypothesis"/>
       <keyfield xlink="purchase"/>
      </key>
  
      <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
      <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
               target="demo:propositionPers" type="link"/>
      <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
    </element>
  </srcSchema>
  ```

* 修改中的假設表單 **[!UICONTROL nms:remaHypothesis]** 綱要。

  依預設，回應記錄檔清單會顯示在收件者記錄檔中。 因此，您必須修改假設表單，以檢視在上一步建立的新回應記錄。

  例如：

  ```
   <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                 toolbarCaption="Responses generated by the hypothesis" type="linklist"
                 xpath="remaMatchPers">
            <input xpath="[.]"/>
            <input xpath="@controlGroup"/>
          </input>
     </container> 
  ```

## 管理指標 {#managing-indicators}

回應管理員模組隨附預先定義的指標清單。 不過，您可以新增其他個人化測量指標。

要執行此操作，您必須透過為每個新指標插入兩個欄位來擴充假設表格：

* 目標母體的第一個，
* 控制組的第二個。

例如：

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```
