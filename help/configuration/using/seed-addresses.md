---
solution: Campaign Classic
product: campaign
title: 種子地址
description: 種子地址
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 3%

---


# 種子地址{#seed-addresses}

如果收件者表格是自訂表格，則需要額外的設定。 **[!UICONTROL nms:seedMember]**&#x200B;架構必須擴展。 在種子地址中添加一個附加頁籤，用於定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有關使用種子地址的詳細資訊，請參閱[本節](../../delivery/using/about-seed-addresses.md)。

## 實施{#implementation}

**nms:seedMember**&#x200B;架構和出廠設定連結表單旨在擴展用於客戶配置，以引用所有必要欄位。 架構定義包含詳細描述其配置模式的注釋。

收件人表擴展方案的定義：

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

1. 建立&#x200B;**nms:seedMember**&#x200B;模式的擴展。 有關詳細資訊，請參閱[擴展架構](../../configuration/using/extending-a-schema.md)。
1. 在此新擴充功能中，使用下列參數在&#x200B;**[!UICONTROL seedMember]**&#x200B;的根位置新增元素：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必須包含匯出促銷活動所需的欄位。 這些欄位的名稱應與外部架構中的相應欄位相同。 例如，如果方案為&#x200B;**[!UICONTROL cus:person]**，則&#x200B;**[!UICONTROL nms:seedMember]**&#x200B;方案應按如下方式擴展：

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
   >**nms:seedMember**&#x200B;架構的擴充必須符合Adobe Campaign中促銷活動和傳送的結構。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在擴展期間，必須為「email」欄位指定&#x200B;**SQL名稱(@sqlname)**。 SQL名稱必須與為收件人方案保留的&#39;sEmail&#39;不同。
   >    * 必須使用在擴展&#x200B;**nms:seedMember**&#x200B;時建立的模式更新資料庫結構。
   >    * 在&#x200B;**nms:seedMember**&#x200B;擴充功能中，包含電子郵件地址的欄位必須有&#x200B;**name=&quot;email&quot;**&#x200B;作為屬性。 SQL名稱必須與已用於收件人模式的&#39;sEmail&#39;不同。 此屬性必須立即聲明在&#x200B;**`<element name="custom_cus_person" />`**&#x200B;元素下。


1. 相應修改&#x200B;**[!UICONTROL seedMember]**&#x200B;表單，以在&#x200B;**[!UICONTROL Seed addresses]**&#x200B;視窗中定義新的「內部收件者」標籤。 有關詳細資訊，請參閱[Form structure](../../configuration/using/form-structure.md)。

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

如果未輸入種子位址的所有屬性，Adobe Campaign會自動替換描述檔：在個人化期間，會使用現有個人檔案的資料自動輸入。
