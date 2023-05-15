---
product: campaign
title: 配置介面
description: 了解如何設定Campaign介面
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 配置介面{#configuring-the-interface}



若要在Adobe Campaign介面中檢視新收件者表格並與其對話，請套用下列步驟：

* 建立新表單以編輯新收件者表格的內容。
* 在瀏覽器樹的資料夾中輸入新類型。
* 建立新的Web應用程式，以透過Adobe Campaign首頁存取自訂表格。

Adobe Campaign使用「Nms_DefaultRcpSchema」全域變數來與預設收件者資料庫(nms:recipient)對話。 因此，此變數需要變更。

1. 前往 **[!UICONTROL Administration>Platform>Options]** 瀏覽器的節點。
1. 變更 **Nms_DefaultRcpSchema** 變數，其名稱與外部收件者表格相符的架構(在此案例中為：cus:indival)。
1. 儲存變更.

## 建立新表單 {#creating-a-new-form-}

建立新表單可讓您檢視及編輯外部收件者表格的資料。

>[!IMPORTANT]
>
>表單的名稱必須與其所關注架構的名稱相同。

1. 前往 **管理>設定>輸入表單** 瀏覽器的節點。
1. 建立新 **xtk:form** type **表單** 檔案。
1. 根據表格範本，說明您需要的所有監控和欄位。

   >[!NOTE]
   >
   >要了解更多 **表單** 類型檔案，請參閱 [本頁](../../configuration/using/identifying-a-form.md).

   在目前的範例中， **表單** 檔案必須以 **cus:individual** 架構，因此具有下列配置：

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. 儲存建立。

## 在導覽階層中建立新類型的資料夾 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. 前往 **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 節點。
1. 建立新 **xtk:navtree** type **navtree** 檔案。
1. 根據表格範本，說明您需要的所有監控和欄位。

   >[!NOTE]
   >
   >如需詳細資訊 **navtree** 類型檔案，請參閱 [本頁](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   在目前範例中， **navtree** 檔案必須以 **cus:individual** 架構中，因此會有下列格式：

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. 儲存建立。
