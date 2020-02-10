---
title: 配置介面
seo-title: 配置介面
description: 配置介面
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 配置介面{#configuring-the-interface}

若要在Adobe Campaign介面中檢視並與新的收件者表格對話，請套用下列步驟：

* 建立新表格以編輯新收件者表格的內容。
* 在瀏覽器樹的資料夾中輸入新類型。
* 建立新的Web應用程式，以透過Adobe Campaign首頁存取自訂表格。

Adobe Campaign使用「Nms_DefaultRcpSchema」全域變數與預設收件者資料庫(nms:recipient)對話。 因此，此變數需要變更。

1. 轉至瀏 **[!UICONTROL Administration>Platform>Options]** 覽器的節點。
1. 更改 **Nms_DefaultRcpSchema** 變數的值，其名稱與外部收件者表匹配的模式(在本例中：cus:individual)。
1. 儲存變更。

## 建立新表格 {#creating-a-new-form-}

建立新表格可讓您檢視和編輯外部收件者表格的資料。

>[!CAUTION]
>
>表單的名稱必須與其所關注之架構的名稱相同。

1. 轉至瀏覽器 **的「管理」>「配置」** >「輸入表單」節點。
1. 建立新 **xtk:form** **type form** file。
1. 根據表格範本說明您需要的所有監視和欄位。

   >[!NOTE]
   >
   >若要進一步瞭解表 **單類型** ，請參閱 [本頁](../../configuration/using/identifying-a-form.md)。

   在我們目前的範例 **中** ，表單檔案必須以 **cus:individual** schema為基礎，因此具有下列配置：

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

1. 儲存建立內容。

## 在導覽階層中建立新類型的資料夾 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. 轉至節 **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 點。
1. 建立新的 **xtk:navtree** 類 **型navtree** 。
1. 根據表格範本說明您需要的所有監視和欄位。

   >[!NOTE]
   >
   >有關navtree類 **型檔案** ，請參閱 [此頁](../../configuration/using/about-navigation-hierarchy.md)。

   在目前範例中， **navtree** 檔案必須以 **cus:individual** schema為基礎，因此具有下列格式：

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

1. 儲存建立內容。

