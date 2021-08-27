---
product: campaign
title: 新增欄位精靈
description: 新增欄位精靈
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# 新增欄位精靈{#new-field-wizard}

![](../../assets/v7-only.svg)

可通過&#x200B;**[!UICONTROL Tools > Advanced > Add new fields]**&#x200B;訪問的嚮導允許您向資料庫中的表添加一個或多個欄位。

驗證嚮導將更新要擴展的表的擴展架構，並啟動SQL指令碼以修改資料庫的物理結構。

該助理具有快速添加欄位的優點，而不需要知道資料模式的結構。

主要缺點是資料和屬性的限制。

精靈畫麵包含下列步驟：

1. 第一頁可讓您輸入要擴充的架構名稱，以及將儲存修改的擴充功能架構的命名空間：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 下一頁可讓您輸入要新增之欄位的屬性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要確認更改，請按一下&#x200B;**[!UICONTROL Finish]**&#x200B;按鈕。

系統會自動建立副檔名檔案（在本例中稱為「cus:recipient」），並執行對應的SQL指令碼：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>依預設，新增的欄位會以屬性&#x200B;**user**（以值「true」宣告）。 這可讓您使用「treeEdit」類型的控制項（請參閱輸入表單），以延伸架構的輸入表單顯示和編輯欄位。
