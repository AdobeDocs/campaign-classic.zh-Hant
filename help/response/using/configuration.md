---
product: campaign
title: 設定促銷活動回應管理員
description: 了解如何設定Campaign回應管理員
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# 設定促銷活動回應管理員{#configuration}

![](../../assets/v7-only.svg)

本節內容適用於負責設定回應管理的人員。 它假定了有關擴展架構、定義工作流和SQL寫程式的一定知識。

這可讓您了解如何透過個人表格，將標準資料模型調整為Adobe Campaign外部交易表的特定性質。 這一個人名表可以與Adobe Campaign的可用個人名表或不同的名表保持一致

測量假設由操作進程工作流(**[!UICONTROL operationMgt]**)啟動。 每個假設代表以非同步方式執行的個別程式，且執行狀態為（正在編輯、待定、已完成、失敗等） 由調度器控制，該調度器管理優先順序約束、同時處理的數量限制、低活動頁和具有頻率的自動執行。

## 設定結構 {#configuring-schemas}

>[!CAUTION]
>
>請勿修改應用程式的內建結構，而是使用結構擴充機制。 否則，在將來升級應用程式時，修改的架構將不會更新。 這可能會在使用Adobe Campaign時導致故障。

在使用反應模組之前需要應用程式整合，以便定義要測量的各種表（事務、事務詳細資訊）及其與傳送、選件和個人的關係。

### 標準結構 {#standard-schemas}

現成&#x200B;**[!UICONTROL nms:remaMatch]**&#x200B;架構包含反應日誌表，即個體、假設和事務表之間的關係。 此架構應作為反應記錄最終目的地表的繼承架構。

**[!UICONTROL nms:remaMatchRcp]**&#x200B;架構也是標準，包含Adobe Campaign收件者(**[!UICONTROL nms:recipient]**)的反應記錄儲存。 若要使用，需要將其擴充以對應至交易表（包含購買等）。

### 事務表和事務詳細資訊 {#transaction-tables-and-transaction-details}

交易表必須包括指向個人的直接連結。

您也可以新增包含交易詳細資料的表格。 這與個人並無直接關聯。

以收款為例，事務處理表連結到聯繫人（收款表），收款行表僅連結到收款表（明細表）。 然後，您可以直接在收款行表連結到收款表的層配置假設。

>[!NOTE]
>
>如果您想要保留在假設中描述預期行為的接收標識符，則可以擴展nms:remaMatchRcp表模板以將標識符添加到該模板（在此情況下，不會將ROI計算連結到這些欄位）。

強烈建議新增事件日期。

完成配置後，以下架構將顯示不同表之間的聯接：

![](assets/response_data_model.png)

### 回應管理與收件者 {#response-management-with-adobe-campaign-recipients}

在此範例中，我們將使用Adobe Campaign內建的收件者表格&#x200B;**[!UICONTROL nms:recipient]**，在回應管理模組中整合購買表。

**[!UICONTROL nms:remaMatchRcp]**&#x200B;收件者的回應記錄表經過擴充，以新增連結至購買表格結構。 在下列範例中，購買表格稱為&#x200B;**demo:purchase**。

1. 透過Adobe Campaign檔案總管，選取&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**。
1. 按一下右鍵&#x200B;**Recipient**，然後選擇&#x200B;**[!UICONTROL Actions]**&#x200B;和&#x200B;**[!UICONTROL Modify the options of the targeting dimensions]**。

   ![](assets/delivery_mapping1.png)

1. 您可以在下一個視窗中個人化&#x200B;**[!UICONTROL Extension namespace]**，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/delivery_mapping2.png)

1. 在&#x200B;**[!UICONTROL Response management]**&#x200B;類別中，確定已勾選&#x200B;**[!UICONTROL Generate a storage schema for reactions]**&#x200B;方塊。

   然後，按一下&#x200B;**[!UICONTROL Define additional fields...]**&#x200B;以選擇相關事務表，並將所需欄位添加到nms:remaMatchRcp架構的擴展中。

   ![](assets/delivery_mapping3.png)

建立的架構如下所示：

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

### 使用個人化收件者表格進行回應管理 {#response-management-with-a-personalized-recipient-table}

在此範例中，我們將使用Adobe Campaign中可用的收件者表格以外的個人表格，在回應管理模組中整合購買表格。

* 建立從&#x200B;**[!UICONTROL nms:remaMatch]**&#x200B;架構派生的新響應日誌架構。

   由於個人表格與Adobe Campaign收件者表格不同，因此必鬚根據&#x200B;**[!UICONTROL nms:remaMatch]**&#x200B;架構建立回應記錄的新架構。 然後填入連結至傳送記錄檔和購買表格。

   在以下示例中，我們將使用&#x200B;**demo:broadLogPers**&#x200B;架構和&#x200B;**demo:purchase**&#x200B;交易表：

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

* 修改&#x200B;**[!UICONTROL nms:remaHypothesis]**&#x200B;架構中的假設表單。

   依預設，回應記錄檔清單會顯示在收件者記錄檔中。 因此，您必須修改假設表單，才能檢視上一步驟期間建立的新回應記錄。

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

要執行此操作，您必須為每個新指示器插入兩個欄位，以擴展假設表：

* 第一個是目標群體，
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
