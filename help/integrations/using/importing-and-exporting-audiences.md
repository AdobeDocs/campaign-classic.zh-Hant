---
solution: Campaign Classic
product: campaign
title: 匯入和匯出受眾
description: 匯入和匯出受眾
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 2%

---


# 匯入和匯出受眾{#importing-and-exporting-audiences}

## 匯入對象{#importing-an-audience}

您可以透過收件者清單，將觀眾／區段從Audience Manager或People核心服務匯入Adobe Campaign。

1. 前往Adobe Campaign檔案總管中的&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]**&#x200B;節點。
1. 在操作欄中，選擇&#x200B;**[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**。

   ![](assets/aam_import_audience.png)

1. 在開啟的視窗中，按一下&#x200B;**[!UICONTROL Select a shared audience]**&#x200B;以前往其他Adobe Experience Cloud解決方案中可用的共用觀眾／區段清單。
1. 選取對象並確認。 觀眾的資訊會自動完成。

   請注意，若要匯入共用的觀眾，您應在管理控制台中指派&#x200B;**[!UICONTROL Audience library]**&#x200B;產品，並成為Audience Manager的管理員。 有關詳細資訊，請參閱[管理控制台文檔](https://helpx.adobe.com/tw/enterprise/managing/user-guide.html)。

   ![](assets/aam_import_audience_3.png)

1. 從&#x200B;**[!UICONTROL AMC Data source]**&#x200B;欄位中選擇AMC資料源，以定義所需的資料類型。

   ![](assets/aam_import_audience_2.png)

1. 儲存觀眾。

觀眾會透過技術工作流程匯入。 匯入的清單包含可使用AMC資料來源進行調節的元素。 Adobe Campaign未識別的元素不會匯入。

從People核心服務或Audience Manager直接匯入區段時，匯入程式需要24-36小時才能同步。 在這段期間後，您就可以在Adobe Campaign中尋找並使用您的新觀眾。

>[!NOTE]
>
>如果您要將觀眾從Adobe Analytics匯入Adobe Campaign，這些觀眾必須先在People Core Service或Audience Manager中共用。 此程式需要12-24小時，這必須新增至與Campaign同步的24-36小時。
>
>在此特定情況下，觀眾分享的時間最長可達60小時。 如需People Core服務和Audience Manager中Adobe Analytics觀眾共用的詳細資訊，請參閱此[檔案](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-publish.html)。

每次同步觀眾資料時，都會完全取代觀眾資料。 只能匯入區段。 不支援精細資料，包括索引鍵值配對、特徵和規則。

## 匯出對象{#exporting-an-audience}

您可以使用工作流程，將觀眾從Adobe Campaign匯出至Audience Manager或People核心服務。 建立和使用工作流的過程在[本文檔](../../workflow/using/building-a-workflow.md)中有詳細說明。 匯出的觀眾會儲存為People核心服務中的區段：

1. 建立新的定位工作流程。
1. 使用可用的不同活動，鎖定一組收件者。
1. 定位後，拖放&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活動，然後開啟它。

   ![](assets/aam_export_example.png)

1. 透過&#x200B;**[!UICONTROL Select a shared audience]**&#x200B;選項定義您要匯出的對象。 在開啟的視窗中，您可以選取現有的對象或建立新的對象。

   如果您選取現有對象，則只會將新記錄新增至對象。

   若要將收件者清單匯出至新對象，請填妥&#x200B;**[!UICONTROL Segment name]**&#x200B;欄位，然後按一下&#x200B;**[!UICONTROL Create]**，再選取新建立的對象。

   按一下窗口右上方的檢查符號，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;按鈕，完成操作。

1. 選擇&#x200B;**[!UICONTROL AMC Data source]**&#x200B;以指定預期的資料類型。 自動確定方案。

   ![](assets/aam_export_audience_activity.png)

1. 儲存觀眾。

然後會匯出觀眾。 儲存觀眾活動有兩個對外轉場。 主要轉場包含成功匯出的收件者。 其他轉場包含無法與訪客ID或宣告的ID對應的收件者。

Adobe Campaign和People核心服務之間的同步化需要24-36小時。 在這段期間後，您將可在People核心服務中尋找新的受眾，並在其他Adobe Experience Cloud解決方案中重複使用。 如需在Adobe People核心服務中使用Adobe Campaign共用觀眾的詳細資訊，請參閱本[檔案](https://docs.adobe.com/content/help/en/core-services/interface/audiences/t-audience-create.html)。

>[!NOTE]
>
>為了進行協調，這些記錄必須有Adobe Experience Cloud ID（&#39;visitor ID&#39;或&#39;declared ID&#39;）。 匯出和匯入觀眾時，不具有Adobe Experience Cloud ID的記錄會被忽略。

