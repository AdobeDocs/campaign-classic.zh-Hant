---
product: campaign
title: 新增欄位精靈
description: 新增欄位精靈
feature: Schema Extension
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# 新增欄位精靈{#new-field-wizard}

![](../../assets/v7-only.svg)

可通過 **[!UICONTROL Tools > Advanced > Add new fields]** 用於向資料庫中的表添加一個或多個欄位。

驗證嚮導將更新要擴展的表的擴展模式，並啟動SQL指令碼以修改資料庫的物理結構。

該助理具有無需知道資料架構的結構即可快速添加欄位的優點。

主要缺點是資料和屬性的限制。

嚮導螢幕包含以下步驟：

1. 在第一頁中，您可以輸入要擴展的架構的名稱以及將保存修改的擴展架構的命名空間：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 在下一頁中，您可以輸入要添加的欄位的屬性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要確認更改，請按一下 **[!UICONTROL Finish]** 按鈕

將自動建立名為「cus:recipient」的擴展檔案，並執行相應的SQL指令碼：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>預設情況下，添加的欄位使用屬性聲明 **用戶** （值為&quot;true&quot;）。 這允許您使用「treeEdit」類型控制項（請參閱「輸入表單」）在擴展架構的輸入表單中顯示和編輯欄位。
