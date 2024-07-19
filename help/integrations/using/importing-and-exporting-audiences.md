---
product: campaign
title: 匯入和匯出對象
description: 匯入和匯出對象
feature: Audiences
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---


# 匯入和匯出對象{#importing-and-exporting-audiences}



## 匯入對象 {#importing-an-audience}

您可以透過收件者清單，將對象/區段從Audience Manager匯入Adobe Campaign。

1. 前往Adobe Campaign總管中的&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]**&#x200B;節點。
1. 在動作列中，選取&#x200B;**[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**。

   ![](assets/aam_import_audience.png)

1. 在開啟的視窗中，按一下「**[!UICONTROL Select a shared audience]**」以移至其他Adobe Experience Cloud解決方案所提供的共用對象/區段清單。
1. 選取對象並進行確認。 對象的資訊會自動完成。

   請注意，若要能夠匯入共用對象，您應該在Admin Console中被指派&#x200B;**[!UICONTROL Audience library]**&#x200B;產品，並成為Audience Manager的管理員。 如需詳細資訊，請參閱[Admin Console檔案](https://helpx.adobe.com/tw/enterprise/managing/user-guide.html)。

   ![](assets/aam_import_audience_3.png)

1. 從&#x200B;**[!UICONTROL AMC Data source]**&#x200B;欄位中選取AMC資料來源，以定義預期的資料型別。

   ![](assets/aam_import_audience_2.png)

1. 儲存對象。

對象會透過技術工作流程匯入。 匯入的清單包含可以使用AMC資料來源調解的元素。 Adobe Campaign無法辨識的元素不會匯入。

直接從Audience Manager匯入區段時，匯入程式需要24到36小時才能同步。 在此期間後，您將能夠在Adobe Campaign中尋找並使用新對象。

>[!NOTE]
>
>如果您要將對象從Adobe Analytics匯入至Adobe Campaign，首先需要在Audience Manager中共用這些對象。 此程式需要12到24小時，必須將其新增到與Campaign的24到36小時同步中。
>
>在該特定情況下，對象共用時間範圍最長可達60小時。 如需Audience Manager中Adobe Analytics對象共用的詳細資訊，請參閱[Adobe Analytics檔案](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html){target="_blank"}。

每次同步化時，對象資料都會完全取代。 只能匯入區段。 不支援包含鍵值組、特徵和規則的精細資料。

## 匯出對象 {#exporting-an-audience}

您可以使用工作流程，將受眾從Adobe Campaign匯出至Audience Manager。 建立及使用工作流程的程式在[此檔案](../../workflow/using/building-a-workflow.md)中有詳細說明。 匯出的對象會儲存為區段：

1. 建立新的目標定位工作流程。
1. 使用不同的可用活動，鎖定一組收件者。
1. 目標定位後，拖放&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活動，然後將其開啟。

   ![](assets/aam_export_example.png)

1. 定義您要透過&#x200B;**[!UICONTROL Select a shared audience]**&#x200B;選項匯出的對象。 在開啟的視窗中，您可以選取現有對象或建立新對象。

   如果您選取現有對象，則只有新記錄會新增至對象。

   若要將您的收件者清單匯出至新的對象，請完成&#x200B;**[!UICONTROL Segment name]**&#x200B;欄位，然後按一下&#x200B;**[!UICONTROL Create]**，再選取新建立的對象。

   按一下視窗右上方的核取符號，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;按鈕，完成作業。

1. 選取&#x200B;**[!UICONTROL AMC Data source]**&#x200B;以指定預期的資料型別。 結構描述會自動決定。

   ![](assets/aam_export_audience_activity.png)

1. 儲存對象。

然後會匯出對象。 儲存對象活動有兩個外站轉變。 主要轉變包含已成功匯出的收件者。 額外的轉變包含無法對應訪客ID或宣告ID的收件者。

解決方案之間的同步化需要24到36小時的時間。 在這段期間後，您將能夠找到新的受眾，並在其他Adobe Experience Cloud解決方案中重複使用它。 如需使用Adobe Campaign共用對象的詳細資訊，請參閱此[檔案](https://experienceleague.adobe.com/en/docs/core-services/interface/services/audiences/create){target="_blank"}。

>[!NOTE]
>
>為了進行調解，記錄必須具有Adobe Experience Cloud ID （「訪客ID」或「宣告ID」）。 匯出和匯入對象時，會忽略沒有Adobe Experience Cloud ID的記錄。
