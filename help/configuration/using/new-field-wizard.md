---
product: campaign
title: 新增欄位助理
description: 新增欄位助理
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: ec774cc10a69a694b3c2bf5a6f662afd12a1435a
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# 新增欄位助理{#new-field-wizard}


可透過&#x200B;**[!UICONTROL Tools > Advanced > Add new fields]**&#x200B;存取的助理可以讓您新增一或多個欄位至資料庫中的表格。

驗證輔助程式會更新要擴充之資料表的擴充功能綱要，並啟動SQL命令檔來修改資料庫的實體結構。

此助理的優點在於快速新增欄位，而不需要知道資料模式的結構。

主要缺點是要擴充的資料和屬性的限制。

助理畫麵包含下列步驟：

1. 第一個頁面可讓您輸入要擴充的綱要名稱，以及儲存修改之擴充綱要的名稱空間：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 下一頁可讓您輸入要新增之欄位的屬性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 若要確認變更，請按一下&#x200B;**[!UICONTROL Finish]**&#x200B;按鈕。

系統會自動建立擴充功能檔案（在範例中稱為「cus：recipient」），並執行對應的SQL指令碼：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>依預設，新增的欄位會宣告為屬性&#x200B;**user** （值為「true」）。 這可讓您使用「treeEdit」型別的控制項（請參閱輸入表單），顯示和編輯擴充結構描述輸入表單中的欄位。
