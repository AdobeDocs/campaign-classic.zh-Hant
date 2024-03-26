---
product: campaign
title: 設定介面
description: 瞭解如何設定Campaign介面
feature: Application Settings
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# 設定介面{#configuring-the-interface}

若要在Adobe Campaign介面中檢視新收件者表格並與之對話，請套用下列步驟：

* 建立新表單以編輯新收件者表格的內容。
* 在總管樹狀結構的資料夾中輸入新型別。
* 建立新的網站應用程式，以透過Adobe Campaign首頁存取自訂表格。

Adobe Campaign使用「Nms_DefaultRcpSchema」全域變數與預設收件者資料庫(nms：recipient)對話。 因此，需要變更此變數。

1. 前往 **[!UICONTROL Administration>Platform>Options]** 瀏覽器節點。
1. 變更 **Nms_DefaultRcpSchema** 變數，其結構描述名稱符合外部收件者表格（在此案例中為：cus：individual）。
1. 儲存變更。

## 建立新表單 {#creating-a-new-form-}

建立新表單可讓您檢視及編輯外部收件者表格的資料。

>[!IMPORTANT]
>
>表單的名稱必須與其關注的結構描述名稱相同。

1. 前往 **管理>設定>輸入表單** 瀏覽器節點。
1. 建立新的 **xtk：form** type **表單** 檔案。
1. 根據您的表格範本，說明您需要的所有監控和欄位。

   >[!NOTE]
   >
   >進一步瞭解 **表單** 輸入檔案，請參閱 [此頁面](../../configuration/using/identifying-a-form.md).

   在我們的目前範例中， **表單** 檔案必須以 **cus：individe** 結構描述，因此具有以下配置：

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

## 在導覽階層中建立新的資料夾型別 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. 前往 **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 節點。
1. 建立新的 **xtk：navtree** type **導覽樹** 檔案。
1. 根據您的表格範本，說明您需要的所有監控和欄位。

   >[!NOTE]
   >
   >有關詳細資訊 **導覽樹** 輸入檔案，請參閱 [此頁面](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   在目前的範例中， **導覽樹** 檔案必須以 **cus：individe** 結構描述，因此具有以下形式：

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
