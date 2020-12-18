---
solution: Campaign Classic
product: campaign
title: 目標對應
description: 瞭解如何建立目標對應
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---


# 目標對應{#target-mapping}

在兩種情況下，必須建立目標對應：

* 如果您使用的收件者表格不是Adobe Campaign提供的表格，
* 如果您設定與目標對應畫面上的標準定位維度不同的篩選維度。

目標映射建立嚮導將幫助您建立使用自定義表所需的所有方案。

## 建立和配置連結到自定義表{#creating-and-configuring-schemas-linked-to-the-custom-table}的方案

在您建立目標對應之前，Adobe Campaign必須進行數種設定，才能使用新的收件者資料結構。

若要這麼做，請套用下列步驟：

1. 建立整合您要使用之自訂表格欄位的新資料架構。

   有關詳細資訊，請參閱[架構參考(xtk:srcSchema)](../../configuration/using/about-schema-reference.md)。

   在我們的示例中，我們將建立一個客戶模式，一個非常簡單的表，其中包含以下欄位：ID、名字、姓氏、電子郵件地址、行動電話號碼。 其目標是能夠向儲存在此表中的個人發送電子郵件或SMS警報。

   範例結構(cus:individual)

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

1. 使用=&quot;true&quot;屬性將架構宣告為外部檢視。 請參閱[視圖屬性](../../configuration/using/schema-characteristics.md#the-view-attribute)。

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. 如果您需要新增直效郵件位址，請使用下列結構類型：

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

1. 按一下&#x200B;**[!UICONTROL Administration > Campaign management > Target mappings]**&#x200B;節點。
1. 按一下&#x200B;**新建**&#x200B;按鈕以開啟目標映射建立嚮導。
1. 輸入&#x200B;**Label**&#x200B;欄位，並選擇剛在&#x200B;**Targeting dimension**&#x200B;欄位中建立的方案。

   ![](assets/mapping_diffusion_wizard_1.png)

1. 在&#x200B;**編輯地址表單**&#x200B;窗口中，選擇與各種傳送地址匹配的方案欄位。 在這裡，我們可以映射&#x200B;**@email**&#x200B;和&#x200B;**@mobile**&#x200B;欄位。

   ![](assets/mapping_diffusion_wizard_2.png)

1. 在以下&#x200B;**Storage**&#x200B;視窗中，輸入擴充結構描述的&#x200B;**字尾**&#x200B;欄位，以區分新結構描述和Adobe Campaign提供的現成結構描述。

   按一下&#x200B;**[!UICONTROL Define new additional fields]**&#x200B;以選取您要在傳送中定位的維度。

   依預設，排除管理會儲存在與訊息相同的表格中。 如果要為連結到目標映射的跟蹤配置儲存，請選中&#x200B;**生成用於跟蹤的儲存架構框。**

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign不支援連結至相同廣播和／或追蹤記錄結構的多個收件者結構描述，稱為定位結構描述。 否則，在事後的資料協調中可能會出現異常。 有關此的詳細資訊，請參閱[建議與限制](../../configuration/using/about-custom-recipient-table.md)頁面。

1. 在&#x200B;**擴充功能**&#x200B;視窗中，選取您要產生的選用結構（可用結構的清單取決於Adobe Campaign平台上安裝的模組）。

   ![](assets/mapping_diffusion_wizard_4.png)

1. 按一下&#x200B;**保存**&#x200B;按鈕以關閉嚮導。

   嚮導使用啟動模式建立新目標映射工作所需的所有其他模式。

   ![](assets/mapping_schema_list.png)

## 使用目標映射{#using-target-mapping}

使用新架構作為傳送目標有兩種方式：

* 根據對應建立一或多個傳送範本
* 在建立傳送時，在選取目標期間直接選取對應，如下所示：

![](assets/mapping_selection_ciblage.png)

**相關主題**

* [快速回應客戶存取其資料的要求](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)