---
product: campaign
title: 種子地址
description: 種子地址
role: Data Engineer, Developer
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Seed Address
level: Intermediate, Experienced
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 7%

---

# 種子地址{#seed-addresses}



如果收件者表格是自訂表格，則需要其他設定。 **[!UICONTROL nms:seedMember]**&#x200B;結構描述必須延伸。 種子地址會新增一個標籤，用於定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

如需使用種子地址的詳細資訊，請參閱[本節](../../delivery/using/about-seed-addresses.md)。

## 實施 {#implementation}

現成可用的&#x200B;**nms：seedMember**&#x200B;結構描述和連結表單將針對客戶設定進行擴充，以參考所有必要欄位。 結構描述定義包含詳細說明其設定模式的註解。

收件者表格延伸綱要的定義：

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

應用以下步驟：

1. 建立&#x200B;**nms：seedMember**&#x200B;結構描述的延伸。 如需詳細資訊，請參閱[本章節](../../configuration/using/extending-a-schema.md)。
1. 在這個新的擴充功能中，使用下列引數在&#x200B;**[!UICONTROL seedMember]**&#x200B;的根目錄新增元素：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必須包含匯出行銷活動所需的欄位。 這些欄位應與外部結構描述中對應的欄位同名。 例如，如果結構描述是&#x200B;**[!UICONTROL cus:person]** ，則&#x200B;**[!UICONTROL nms:seedMember]**&#x200B;結構描述應該擴充如下：

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >**nms：seedMember**&#x200B;結構描述的擴充功能必須符合Adobe Campaign中行銷活動和傳遞的結構。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在延伸期間，您必須為&#39;email&#39;欄位指定&#x200B;**SQL名稱(@sqlname)**。 SQL名稱必須與為收件者綱要保留的&#39;sEmail&#39;不同。
   >    * 您必須使用擴充&#x200B;**nms：seedMember**&#x200B;時建立的結構描述來更新資料庫結構。
   >    * 在&#x200B;**nms：seedMember**&#x200B;擴充功能中，包含電子郵件地址的欄位必須有&#x200B;**name=&quot;email&quot;**&#x200B;做為屬性。 SQL名稱必須與已用於收件者綱要的&#39;sEmail&#39;不同。 這個屬性必須立即宣告到&#x200B;**`<element name="custom_cus_person" />`**&#x200B;專案下。
   >    
   >

1. 相應地修改&#x200B;**[!UICONTROL seedMember]**&#x200B;表單，以在&#x200B;**[!UICONTROL Seed addresses]**&#x200B;視窗中定義新的「內部收件者」索引標籤。 如需詳細資訊，請參閱[此頁面](../../configuration/using/form-structure.md)。

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

如果未輸入種子位址的所有屬性，Adobe Campaign會自動取代設定檔：個人化期間會使用現有設定檔的資料自動輸入這些屬性。
