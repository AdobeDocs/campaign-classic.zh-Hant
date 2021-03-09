---
solution: Campaign Classic
product: campaign
title: 設定介面
description: 設定介面
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: d6327cb5307ab5d37c15afa45dfd180ef04cb5a2
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# 設定介面{#configuring-the-interface}

要在Adobe Campaign介面中查看新收件人表並與其對話，請應用以下步驟：

* 建立新表格以編輯新收件者表格的內容。
* 在瀏覽器樹的資料夾中輸入新類型。
* 建立新的Web應用程式，以透過Adobe Campaign首頁存取自訂表格。

Adobe Campaign使用「Nms_DefaultRcpSchema」全局變數與預設接收方資料庫(nms:recipient)對話。 因此，此變數需要變更。

1. 轉至瀏覽器的&#x200B;**[!UICONTROL Administration>Platform>Options]**&#x200B;節點。
1. 使用與外部收件者表匹配的方案名稱更改&#x200B;**Nms_DefaultRcpSchema**&#x200B;變數的值(在本例中：cus:individual)。
1. 儲存變更。

## 建立新表單{#creating-a-new-form-}

建立新表格可讓您檢視和編輯外部收件者表格的資料。

>[!IMPORTANT]
>
>表單的名稱必須與其所關注之架構的名稱相同。

1. 轉到瀏覽器的&#x200B;**管理>配置>輸入表單**&#x200B;節點。
1. 建立新的&#x200B;**xtk:form**&#x200B;類型&#x200B;**form**&#x200B;檔案。
1. 根據表格範本說明您需要的所有監視和欄位。

   >[!NOTE]
   >
   >若要進一步瞭解&#x200B;**form**&#x200B;類型檔案，請參閱[本頁](../../configuration/using/identifying-a-form.md)。

   在我們目前的範例中，**form**&#x200B;檔案必須以&#x200B;**cus:individual**&#x200B;架構為基礎，因此具有下列版面：

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

## 在導航層次結構{#creating-a-new-type-of-folder-in-the-navigation-hierarchy}中建立新類型的資料夾

1. 轉至&#x200B;**[!UICONTROL Administration>Configuration>Navigation hierarchies]**&#x200B;節點。
1. 建立新的&#x200B;**xtk:navtree**&#x200B;類型&#x200B;**navtree**&#x200B;檔案。
1. 根據表格範本說明您需要的所有監視和欄位。

   >[!NOTE]
   >
   >有關&#x200B;**navtree**&#x200B;類型檔案的詳細資訊，請參閱[此頁](../../platform/using/adobe-campaign-workspace.md#about-navigation-hierarchy)。

   在目前範例中，**navtree**&#x200B;檔案必須以&#x200B;**cus:individual**&#x200B;架構為基礎，因此具有下列格式：

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

