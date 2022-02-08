---
product: campaign
title: 配置介面
description: 瞭解如何配置市場活動介面
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 配置介面{#configuring-the-interface}

![](../../assets/common.svg)

要在Adobe Campaign介面中查看和對話新收件人表，請應用以下步驟：

* 建立新表單以編輯新收件人表的內容。
* 在瀏覽器樹的資料夾中輸入新類型。
* 建立新的Web應用程式，以通過Adobe Campaign首頁訪問自定義表。

Adobe Campaign使用「nms_DefaultRcpSchema」全局變數與預設收件人資料庫(nms:recipient)對話。 因此，需要更改此變數。

1. 轉到 **[!UICONTROL Administration>Platform>Options]** 的子菜單。
1. 更改 **Nms_DefaultRcpSchema** 變數，其名稱與外部收件人表匹配的方案(在本例中為：cus:individual)。
1. 保存更改。

## 建立新窗體 {#creating-a-new-form-}

建立新表單將使您能夠查看和編輯外部收件人表的資料。

>[!IMPORTANT]
>
>表單的名稱必須與它所涉及的架構的名稱相同。

1. 轉到 **管理>配置>輸入表單** 的子菜單。
1. 新建 **xtk：格式** 類型 **表格** 的子菜單。
1. 根據表模板描述所需的所有監視和欄位。

   >[!NOTE]
   >
   >要瞭解有關 **表格** 類型檔案，請參閱 [此頁](../../configuration/using/identifying-a-form.md)。

   在我們當前的示例中， **表格** 檔案必須基於 **cus：單個** 架構，因此具有以下佈局：

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

1. 保存建立。

## 在導航層次結構中建立新類型的資料夾 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. 轉到 **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 的下界。
1. 新建 **xtk：導航樹** 類型 **樹** 的子菜單。
1. 根據表模板描述所需的所有監視和欄位。

   >[!NOTE]
   >
   >更多內容 **樹** 類型檔案，請參閱 [此頁](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。

   在當前示例中， **樹** 檔案必須基於 **cus：單個** 架構，因此具有以下格式：

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

1. 保存建立。
