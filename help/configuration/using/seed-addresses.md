---
product: campaign
title: 種子地址
description: 種子地址
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 8%

---

# 種子地址{#seed-addresses}

![](../../assets/common.svg)

如果收件人表是自定義表，則需要其他配置。 的 **[!UICONTROL nms:seedMember]** 必須擴展架構。 在種子地址中添加一個附加頁籤，用於定義足夠的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有關使用種子地址的詳細資訊，請參閱 [此部分](../../delivery/using/about-seed-addresses.md)。

## 實施 {#implementation}

的 **nms:seedMember** 模式和出廠時的連結表單應用於客戶配置中進行擴展，以引用所有必需欄位。 架構定義包含詳細描述其配置模式的注釋。

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

1. 建立 **nms:seedMember** 架構。 如需詳細資訊，請參閱[本章節](../../configuration/using/extending-a-schema.md)。
1. 在此新擴展中，在的根部添加新元素 **[!UICONTROL seedMember]** 具有以下參數：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必須包含導出市場活動所需的欄位。 這些欄位應與外部架構中的相應欄位具有相同的名稱。 例如，如果架構 **[!UICONTROL cus:person]** ，也請參見Wiki頁。 **[!UICONTROL nms:seedMember]** 架構應按如下方式擴展：

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
   >擴展 **nms:seedMember** 架構必須符合Adobe Campaign的活動和交付結構。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在擴展期間，必須指定 **SQL名稱(@sqlname)** 的子菜單。 SQL名稱必須與為收件人架構保留的&#39;sEmail&#39;不同。
   >    * 必須使用擴展時建立的架構更新資料庫結構 **nms:seedMember**。
   >    * 在 **nms:seedMember** 擴展，包含電子郵件地址的欄位必須 **name=&quot;電子郵件&quot;** 屬性。 SQL名稱必須與已用於收件人架構的&#39;sEmail&#39;不同。 必須立即在 **`<element name="custom_cus_person" />`** 的子菜單。


1. 修改 **[!UICONTROL seedMember]** 表單，以在 **[!UICONTROL Seed addresses]** 的子菜單。 如需詳細資訊，請參閱[此頁面](../../configuration/using/form-structure.md)。

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

如果未輸入種子地址的所有屬性，Adobe Campaign會自動替換配置檔案：在使用現有配置檔案中的資料進行個性化設定期間，將自動輸入這些檔案。
