---
solution: Campaign Classic
product: campaign
title: 配置
description: 配置
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# 設定{#configuration}

本節內容適用於負責設定回應管理的人員。 它假定您對於擴展方案、定義工作流和SQL寫程式有一定的知識。

這可讓您瞭解如何將標準資料模型與Adobe Campaign外部交易表與個人表格的特定性調整。 此人員表格可與Adobe Campaign中可用人員表格或不同表格相符

測量假設由操作流程工作流(**[!UICONTROL operationMgt]**)啟動。 每個假設代表一個單獨的進程，以非同步方式與執行狀態（正在編輯、待定、完成、失敗等）執行 並由調度器控制，調度器管理優先順序約束、同時處理的數量限制、低活動頁面和頻率自動執行。

## 配置方案{#configuring-schemas}

>[!CAUTION]
>
>請勿修改應用程式的標準架構，而是使用架構擴充機制。 否則，修改的架構將不會在應用程式日後升級時更新。 這可能會在使用Adobe Campaign時導致錯誤。

在使用反應模組之前，需要應用程式整合，以定義要測量的各種表（事務、事務詳細資訊）及其與交付、選件和個人的關係。

### 標準結構{#standard-schemas}

框外模式&#x200B;**[!UICONTROL nms:remaMatch]**&#x200B;包含反應日誌表，即個體、假設和事務表之間的關係。 此模式將用作反應日誌最終目標表的繼承模式。

**[!UICONTROL nms:remaMatchRcp]**&#x200B;架構也是標準，它包含Adobe Campaign收件者(**[!UICONTROL nms:recipient]**)的反應記錄檔儲存。 為了使用，需要將其擴展以映射到事務表（包含購買等）。

### 事務表和事務詳細資訊{#transaction-tables-and-transaction-details}

事務表必須包括指向個人的直接連結。

您也可以新增包含交易詳細資料的表格。 這並非直接與個人連結。

以收款為例，事務處理表與聯繫人（收款表）連結，收款行表僅與收款表（明細表）連結。 然後，您可以直接在收款行表連結至收款表的層配置假設。

>[!NOTE]
>
>如果您想要保留描述假設中預期行為的接收識別碼，可以擴充nms:remaMatchRcp表範本，將識別碼新增至它（在此例中，沒有將ROI計算連結至這些欄位）。

強烈建議新增事件日期。

完成配置後，以下模式將顯示不同表之間的連接：

![](assets/response_data_model.png)

### 與Adobe Campaign收件者{#response-management-with-adobe-campaign-recipients}進行回應管理

在此範例中，我們將使用Adobe Campaign收件者表格(**[!UICONTROL nms:recipient]**)，將購買表整合在我們的回應管理模組中。

**[!UICONTROL nms:remaMatchRcp]**&#x200B;收件者上的回應記錄表會加以擴充，以新增購買表結構描述的連結。 在下列範例中，購買表格稱為&#x200B;**demo:purchase**。

1. 透過Adobe Campaign檔案總管，選取&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**。
1. 按一下右鍵&#x200B;**收件人** ，然後選擇&#x200B;**[!UICONTROL Actions]**&#x200B;和&#x200B;**[!UICONTROL Modify the options of the targeting dimensions]**。

   ![](assets/delivery_mapping1.png)

1. 您可以在下一個視窗中個人化&#x200B;**[!UICONTROL Extension namespace]**，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/delivery_mapping2.png)

1. 在&#x200B;**[!UICONTROL Response management]**&#x200B;類別中，請確定已勾選&#x200B;**[!UICONTROL Generate a storage schema for reactions]**&#x200B;方塊。

   然後按一下&#x200B;**[!UICONTROL Define additional fields...]**&#x200B;以選擇相關事務表，並將所需欄位添加到nms:remaMatchRcp架構的擴展中。

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

### 使用個人化收件者表{#response-management-with-a-personalized-recipient-table}進行回應管理

在此範例中，我們將使用Adobe Campaign中可用之收件者表格以外的個人表格，將購買表格整合在回應管理模組中。

* 建立從&#x200B;**[!UICONTROL nms:remaMatch]**&#x200B;模式派生的新響應日誌模式。

   由於個人表與Adobe Campaign收件者表不同，因此必鬚根據&#x200B;**[!UICONTROL nms:remaMatch]**&#x200B;架構建立回應記錄檔的新架構。 然後填入傳送記錄和購買表格的連結。

   在下例中，我們將使用&#x200B;**demo:broadLogPers**&#x200B;架構和&#x200B;**demo:purchase**&#x200B;交易表：

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

* 修改&#x200B;**[!UICONTROL nms:remaHypothesis]**&#x200B;模式中的假設形式。

   依預設，回應記錄清單會顯示在收件者記錄檔中。 因此，您必須修改假設表單，才能檢視在上一步驟中建立的新回應記錄。

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

## 管理指示符{#managing-indicators}

「響應管理器」模組提供了預定義指示器的清單。 不過，您可以新增其他個人化測量指標。

為此，必須為每個新指示符插入兩個欄位來擴展假設表：

* 第一個是目標人群，
* 第二個是控制組。

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

