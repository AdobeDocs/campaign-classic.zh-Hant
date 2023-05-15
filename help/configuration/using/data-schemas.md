---
product: campaign
title: 資料方案
description: 開始使用Campaign資料結構
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: d4446035-3988-4d89-b7df-7b8528c2e371
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 1%

---

# 資料方案{#data-schemas}

## 原則 {#principles}

若要編輯、建立和設定結構，請按一下 **[!UICONTROL Administration > Configuration > Data schemas]** Adobe Campaign用戶端主控台的節點。

>[!NOTE]
>
>您的Adobe Campaign Classic主控台管理員只能刪除內建資料結構。

![](assets/d_ncs_integration_schema_navtree.png)

編輯欄位顯示源架構的XML內容：

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>「名稱」編輯控制項可讓您輸入由名稱和命名空間組成的架構金鑰。 架構的根元素的「name」和「namespace」屬性會在架構的XML編輯區域中自動更新。

預覽會自動產生擴充架構：

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>儲存來源架構時，會自動啟動延伸架構的產生。

如果需要檢查架構的完整結構，可以使用預覽頁簽。 如果結構已擴充，您便能將其所有擴充功能視覺化。 作為補充，「文檔」頁簽顯示所有架構屬性和元素及其屬性（SQL欄位、類型/長度、標籤、說明）。 「檔案」索引標籤僅適用於產生的結構。 有關詳細資訊，請參閱 [重新生成結構](../../configuration/using/regenerating-schemas.md) 區段。

## 範例：建立合同表 {#example--creating-a-contract-table}

在以下範例中，我們要為 **合同** 在Adobe Campaign資料庫的資料庫模型中。 此表格可讓您儲存每個合約的持有人和共同持有人的名字和姓氏以及電子郵件地址。

要執行此操作，需要建立表的架構並更新資料庫結構以生成相應的表。 應用以下階段：

1. 編輯 **[!UICONTROL Administration > Configuration > Data schemas]** 節點，然後按一下 **[!UICONTROL New]** .
1. 選擇 **[!UICONTROL Create a new table in the data model]** 選項，然後按一下 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. 指定表的名稱和命名空間。

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >依預設，使用者建立的結構會儲存在「自訂」命名空間中。 有關詳細資訊，請參閱 [方案的標識](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. 建立表格的內容。 建議您使用登入精靈，確保未遺失任何設定。 若要這麼做，請按一下 **[!UICONTROL Insert]** 按鈕，然後選擇要添加的設定類型。

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

1. 儲存結構以產生結構：

   ![](assets/s_ncs_configuration_structure.png)

1. 更新資料庫結構以建立將連結架構的表。 有關詳細資訊，請參閱 [更新資料庫結構](../../configuration/using/updating-the-database-structure.md).
