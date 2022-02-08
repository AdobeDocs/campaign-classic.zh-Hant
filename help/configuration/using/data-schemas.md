---
product: campaign
title: 資料方案
description: 開始使用市場活動資料架構
feature: Schema Extension
exl-id: d4446035-3988-4d89-b7df-7b8528c2e371
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 1%

---

# 資料方案{#data-schemas}

![](../../assets/v7-only.svg)

## 原則 {#principles}

要編輯、建立和配置方案，請按一下 **[!UICONTROL Administration > Configuration > Data schemas]** Adobe Campaign客戶端控制台的節點。

>[!NOTE]
>
>內置資料架構只能由Adobe Campaign Classic控制台的管理員刪除。

![](assets/d_ncs_integration_schema_navtree.png)

編輯欄位顯示源架構的XML內容：

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>使用「名稱」編輯控制項可以輸入由名稱和命名空間組成的架構密鑰。 在架構的XML編輯區域中，將自動更新架構的根元素的&quot;name&quot;和&quot;namespace&quot;屬性。

預覽將自動生成擴展架構：

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>保存源架構後，將自動啟動擴展架構的生成。

如果需要檢查架構的完整結構，則可以使用預覽頁籤。 如果已擴展了架構，則可以直觀顯示其所有擴展。 作為補充，「文檔」頁籤顯示所有架構屬性和元素及其屬性（SQL欄位、類型/長度、標籤、說明）。 「文檔」頁籤僅適用於生成的架構。 有關詳細資訊，請參閱 [重新生成架構](../../configuration/using/regenerating-schemas.md) 的子菜單。

## 示例：建立合同表 {#example--creating-a-contract-table}

在以下示例中，我們要為 **合同** 在Adobe Campaign資料庫模型中。 此表允許您為每個合同儲存持有者和共同持有者的名字和姓氏以及電子郵件地址。

為此，需要建立表的模式並更新資料庫結構以生成相應的表。 應用以下階段：

1. 編輯 **[!UICONTROL Administration > Configuration > Data schemas]** ，然後按一下 **[!UICONTROL New]** 。
1. 選擇 **[!UICONTROL Create a new table in the data model]** 選項 **[!UICONTROL Next]** 。

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. 為表和命名空間指定名稱。

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >預設情況下，由用戶建立的架構儲存在「cus」命名空間中。 有關此內容的詳細資訊，請參閱 [模式的標識](../../configuration/using/about-schema-reference.md#identification-of-a-schema)。

1. 建立表的內容。 我們建議使用輸入嚮導來確保不丟失任何設定。 要執行此操作，請按一下 **[!UICONTROL Insert]** 按鈕，選擇要添加的設定類型。

   ![](assets/s_ncs_configuration_create_new_content.png)

1. 定義合同表的設定：

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   添加合同類型並在合同編號上放置索引。

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. 保存架構以生成結構：

   ![](assets/s_ncs_configuration_structure.png)

1. 更新資料庫結構以建立模式將連結到的表。 有關此內容的詳細資訊，請參閱 [更新資料庫結構](../../configuration/using/updating-the-database-structure.md)。
