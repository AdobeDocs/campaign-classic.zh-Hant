---
product: campaign
title: 目標對應
description: 瞭解如何建立目標映射
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 2%

---

# 目標對應{#target-mapping}

![](../../assets/common.svg)

在以下兩種情況下，必須建立目標映射：

* 如果你用的是Adobe Campaign提供的收件人表以外的表格，
* 如果在目標映射螢幕上配置了與標準目標維不同的篩選維。

目標映射建立嚮導將幫助您建立使用自定義表所需的所有方案。

## 建立和配置連結到自定義表的架構 {#creating-and-configuring-schemas-linked-to-the-custom-table}

在建立目標映射之前，為使Adobe Campaign能夠使用新的收件人資料架構運行，必須進行若干配置。

若要這麼做，請套用下列步驟：

1. 建立一個新資料方案，該方案整合了要使用的自定義表的欄位。

   有關詳細資訊，請參閱 [架構引用(xtk:srcSchema)](../../configuration/using/about-schema-reference.md)。

   在本示例中，我們將建立一個客戶架構，一個包含以下欄位的非常簡單的表：ID，名字，姓，電子郵件地址，手機號碼。 目的是能夠向此表中儲存的個人發送電子郵件或SMS警報。

   示例架構(cus:individual)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. 使用=&quot;true&quot;屬性將架構聲明為外部視圖。 請參閱 [視圖屬性](../../configuration/using/schema-characteristics.md#the-view-attribute)。

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. 如果需要添加直郵地址，請使用以下類型的結構：

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. 按一下 **[!UICONTROL Administration > Campaign management > Target mappings]** 的下界。
1. 按一下 **新建** 按鈕開啟目標映射建立嚮導。
1. 輸入 **標籤** 欄位，然後選擇您剛在 **目標維** 的子菜單。

   ![](assets/mapping_diffusion_wizard_1.png)

1. 在 **編輯地址表單** 窗口，選擇與各種傳遞地址匹配的方案欄位。 在這裡，我們可以 **@email** 和 **@mobile** 的子菜單。

   ![](assets/mapping_diffusion_wizard_2.png)

1. 在以下 **儲存** ，輸入 **擴展架構的尾碼** 欄位，將新架構與Adobe Campaign提供的現成架構區分開來。

   按一下 **[!UICONTROL Define new additional fields]** 選擇要在交貨中瞄準的維。

   預設情況下，排除管理與消息儲存在同一表中。

   檢查 **生成用於跟蹤的儲存架構** 框。

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign不支援與同一廣播模式和/或跟蹤日誌模式連結的多個接收方模式，即目標模式。 否則，這可能導致以後資料協調出現異常。 有關此項的詳細資訊，請參閱 [建議和限制](../../configuration/using/about-custom-recipient-table.md) 的子菜單。

1. 在 **擴展** 窗口，選擇要生成的可選方案(可用方案清單取決於Adobe Campaign平台上安裝的模組)。

   ![](assets/mapping_diffusion_wizard_4.png)

1. 按一下 **保存** 按鈕

   嚮導使用啟動架構建立使新目標映射工作所需的所有其他架構。

   ![](assets/mapping_schema_list.png)

## 使用目標映射 {#using-target-mapping}

使用新架構作為傳遞目標有兩種方法：

* 基於映射建立一個或多個交付模板
* 建立交貨時，在目標選擇期間直接選擇映射，如下所示：

![](assets/mapping_selection_ciblage.png)
