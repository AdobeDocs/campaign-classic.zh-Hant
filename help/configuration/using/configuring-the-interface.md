---
product: campaign
title: 設定介面
description: 瞭解如何設定Campaign介面
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 設定介面{#configuring-the-interface}

若要在Adobe Campaign介面中檢視新收件者表格並與之對話，請套用下列步驟：

* 建立新表單以編輯新收件者表格的內容。
* 在總管樹狀結構的資料夾中輸入新型別。
* 建立新的網站應用程式，以透過Adobe Campaign首頁存取自訂表格。

Adobe Campaign使用「Nms_DefaultRcpSchema」全域變數與預設收件者資料庫(nms：recipient)對話。 因此，需要變更此變數。

1. 前往總管的&#x200B;**[!UICONTROL Administration>Platform>Options]**&#x200B;節點。
1. 以符合外部收件者資料表的結構描述名稱（在此案例中為： cus：individual），變更&#x200B;**Nms_DefaultRcpSchema**&#x200B;變數的值。
1. 儲存變更。

## 建立新表單 {#creating-a-new-form-}

建立新表單可讓您檢視及編輯外部收件者表格的資料。

>[!IMPORTANT]
>
>表單的名稱必須與其關注的結構描述名稱相同。

1. 前往總管的&#x200B;**管理>設定>輸入表單**&#x200B;節點。
1. 建立新的&#x200B;**xtk：form**&#x200B;型別&#x200B;**表單**&#x200B;檔案。
1. 根據您的表格範本，說明您需要的所有監控和欄位。

   >[!NOTE]
   >
   >若要進一步瞭解&#x200B;**表單**&#x200B;型別檔案，請參閱[此頁面](../../configuration/using/identifying-a-form.md)。

   在我們目前的範例中，**表單**&#x200B;檔案必須以&#x200B;**cus：individual**&#x200B;結構描述為基礎，因此具有以下配置：

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

1. 前往&#x200B;**[!UICONTROL Administration>Configuration>Navigation hierarchies]**&#x200B;節點。
1. 建立新的&#x200B;**xtk：navtree**&#x200B;型別&#x200B;**navtree**&#x200B;檔案。
1. 根據您的表格範本，說明您需要的所有監控和欄位。

   >[!NOTE]
   >
   >如需&#x200B;**navtree**&#x200B;型別檔案的詳細資訊，請參閱[此頁面](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。

   在目前的範例中，**navtree**&#x200B;檔案必須以&#x200B;**cus：individual**&#x200B;結構描述為基礎，因此具有下列形式：

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
