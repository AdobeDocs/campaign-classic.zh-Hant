---
product: campaign
title: 種子地址
description: 種子地址
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 3%

---

# 種子地址{#seed-addresses}

如果收件者表格是自訂表格，則需要其他設定。 必須擴展&#x200B;**[!UICONTROL nms:seedMember]**&#x200B;架構。 種子地址中會新增一個標籤，以定義適當欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有關使用種子地址的詳細資訊，請參閱[此部分](../../delivery/using/about-seed-addresses.md)。

## 實作 {#implementation}

**nms:seedMember**&#x200B;架構和現成的連結表單將擴展以用於客戶配置，以引用所有必要欄位。 架構定義包含詳細說明其配置模式的注釋。

收件人表擴展架構的定義：

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

1. 建立&#x200B;**nms:seedMember**&#x200B;方案的擴展。 有關詳細資訊，請參閱[擴展架構](../../configuration/using/extending-a-schema.md)。
1. 在此新擴充功能中，使用下列參數，在&#x200B;**[!UICONTROL seedMember]**&#x200B;的根新增元素：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必須包含匯出促銷活動所需的欄位。 這些欄位的名稱應與外部架構中的對應欄位相同。 例如，如果架構為&#x200B;**[!UICONTROL cus:person]** ，則&#x200B;**[!UICONTROL nms:seedMember]**&#x200B;架構應依下列方式擴充：

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
   >**nms:seedMember**&#x200B;方案的擴充必須符合Adobe Campaign中促銷活動和傳送的結構。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在擴充期間，必須為「email」欄位指定&#x200B;**SQL名稱(@sqlname)**。 SQL名稱必須與為收件人架構保留的&#39;sEmail&#39;不同。
   >    * 必須使用在擴展&#x200B;**nms:seedMember**&#x200B;時建立的模式更新資料庫結構。
   >    * 在&#x200B;**nms:seedMember**&#x200B;擴充功能中，包含電子郵件地址的欄位必須有&#x200B;**name=&quot;email&quot;**&#x200B;作為屬性。 SQL名稱必須與已用於收件者架構的&#39;sEmail&#39;不同。 必須在&#x200B;**`<element name="custom_cus_person" />`**&#x200B;元素下立即聲明此屬性。


1. 相應地修改&#x200B;**[!UICONTROL seedMember]**&#x200B;表單，以在&#x200B;**[!UICONTROL Seed addresses]**&#x200B;視窗中定義新的「內部收件者」索引標籤。 有關詳細資訊，請參閱[表單結構](../../configuration/using/form-structure.md)。

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

如果未輸入種子地址的所有屬性，Adobe Campaign會自動替代設定檔：使用現有設定檔的資料，在個人化期間會自動輸入這些設定檔。
