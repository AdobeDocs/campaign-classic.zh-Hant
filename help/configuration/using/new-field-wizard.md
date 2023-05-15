---
product: campaign
title: 新增欄位精靈
description: 新增欄位精靈
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# 新增欄位精靈{#new-field-wizard}


精靈可透過 **[!UICONTROL Tools > Advanced > Add new fields]** 可讓您將一或多個欄位新增至資料庫中的表格。

驗證嚮導將更新要擴展的表的擴展架構，並啟動SQL指令碼以修改資料庫的物理結構。

該助理具有快速添加欄位的優點，而不需要知道資料模式的結構。

主要缺點是資料和屬性的限制。

精靈畫麵包含下列步驟：

1. 第一頁可讓您輸入要擴充的架構名稱，以及將儲存修改的擴充功能架構的命名空間：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 下一頁可讓您輸入要新增之欄位的屬性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 若要確認變更，請按一下 **[!UICONTROL Finish]** 按鈕。

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
>依預設，新增的欄位會使用屬性宣告 **使用者** （值為「true」）。 這可讓您使用「treeEdit」類型的控制項（請參閱輸入表單），以延伸架構的輸入表單顯示和編輯欄位。
