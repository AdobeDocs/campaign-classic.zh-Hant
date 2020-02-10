---
title: 種子地址
seo-title: 種子地址
description: 種子地址
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 種子地址{#seed-addresses}

如果收件者表格是自訂表格，則需要額外的設定。 必 **[!UICONTROL nms:seedMember]** 須擴展模式。 在種子地址中添加一個附加頁籤，用於定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有關使用種子地址的詳細資訊，請參 [閱本節](../../delivery/using/about-seed-addresses.md)。

## 實作 {#implementation}

nms: **seedMember** schema和出廠設定的連結表單旨在擴展用於客戶配置，以引用所有必要欄位。 架構定義包含詳細描述其配置模式的注釋。

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

1. 建立 **nms:seedMember架構的擴展** 。 有關詳細資訊，請參 [閱擴展架構](../../configuration/using/extending-a-schema.md)。
1. 在此新的擴充功能中，使用下列參數在根部新 **[!UICONTROL seedMember]** 增元素：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必須包含匯出促銷活動所需的欄位。 這些欄位的名稱應與外部架構中的相應欄位相同。 例如，如果模式為 **[!UICONTROL cus:person]** ，則應 **[!UICONTROL nms:seedMember]** 按如下方式擴展模式：

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
   >nms:seedMember **** schema的擴展必須符合Adobe Campaign中促銷活動和傳遞的結構。

   >[!CAUTION]
   >
   >
   >    
   >    
   >    * 在擴展期間，必須為「 **email」欄位指定SQL名稱(@sqlname)** 。 SQL名稱必須與為收件人方案保留的&#39;sEmail&#39;不同。
   >    * 必須使用擴展 **nms:seedMember時建立的模式更新資料庫結**&#x200B;構。
   >    * 在 **nms:seedMember** extension中，包含電子郵件地址的欄位必須 **有name=&quot;email** &quot;作為屬性。 SQL名稱必須與已用於收件人模式的&#39;sEmail&#39;不同。 此屬性必須立即聲明在元素 **`<element name="custom_cus_person" />`** 下。


1. 相應地修 **[!UICONTROL seedMember]** 改表單，以在視窗中定義新的「內部收件者」 **[!UICONTROL Seed addresses]** 標籤。 For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

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
