---
product: campaign
title: 建立傳遞範本
description: 建立傳遞範本
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Delivery Templates
role: User
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 7%

---

# 建立傳遞範本{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#delivery-template-video)

## 將現有傳遞轉換為範本 {#converting-an-existing-delivery-to-a-template}

傳遞可以轉換為範本以供新的重複傳遞動作使用。 若要將傳遞轉換為範本，請從傳遞清單中選取它，可透過樹狀結構的&#x200B;**[!UICONTROL Campaign management]**&#x200B;節點存取。

按一下滑鼠右鍵並選取&#x200B;**[!UICONTROL Actions > Save as template...]**。

![](assets/s_ncs_user_campaign_save_as_scenario.png)

此動作會從選取的傳遞建立傳遞範本。 您必須輸入儲存它的資料夾（在&#x200B;**[!UICONTROL Folder]**&#x200B;欄位中），以及根據此範本建立的傳遞資料夾（在&#x200B;**[!UICONTROL Execution folder]**&#x200B;欄位中）。

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

如需設定模式的詳細資訊，請參閱[將範本連結至傳遞](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery)。

## 建立新範本 {#creating-a-new-template}

>[!NOTE]
>
>為避免組態錯誤，Adobe建議您複製原生範本並自訂其設定，而非建立新範本。

若要設定傳送範本，請執行下列步驟：

1. 開啟Campaign Explorer。
1. 在&#x200B;**資源**&#x200B;資料夾中，選取&#x200B;**範本**&#x200B;然後&#x200B;**傳遞範本**。

   ![](assets/delivery_template_1.png)

1. 按一下工具列中的「新增&#x200B;**」**&#x200B;以建立新的傳遞範本，或&#x200B;**複製**&#x200B;現有的範本。

   ![](assets/delivery_template_2.png)

1. 修改資料夾的&#x200B;**標籤**&#x200B;和&#x200B;**內部名稱**。
1. 儲存範本並重新開啟。
1. 按一下「**屬性**」按鈕，然後根據您的要求修改值。

   ![](assets/delivery_template_3.png)

1. 在&#x200B;**一般**&#x200B;索引標籤中，確認或變更&#x200B;**執行資料夾**、**資料夾**&#x200B;及&#x200B;**路由**&#x200B;下拉式功能表中選取的位置。

   ![](assets/delivery_template_4.png)

1. 使用您的電子郵件主旨和目標母體完成&#x200B;**電子郵件引數**&#x200B;類別。
1. 新增您的&#x200B;**HTML內容**&#x200B;以個人化您的範本，您可以顯示映象頁面連結和取消訂閱連結。
1. 選取&#x200B;**預覽**&#x200B;索引標籤。 在&#x200B;**測試個人化**&#x200B;下拉式功能表中，選取&#x200B;**收件者**&#x200B;以預覽您的範本作為所選設定檔。

   ![](assets/delivery_template_5.png)

1. 按一下&#x200B;**儲存**。 您的範本現在已準備好用於傳遞。


## 教學課程影片 {#delivery-template-video}

### 如何設定傳遞範本

下列影片示範如何設定隨選傳遞的範本。

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### 如何設定傳遞範本屬性

以下影片說明如何設定傳遞範本屬性，並詳細說明每個屬性。

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### 如何部署隨選傳遞範本

此影片說明如何部署隨選電子郵件傳遞範本，並說明電子郵件傳遞與傳遞工作流程之間的差異。

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)提供其他Campaign Classic操作說明影片。
