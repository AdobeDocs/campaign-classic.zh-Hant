---
title: 匯入和匯出觀眾
seo-title: 匯入和匯出觀眾
description: 匯入和匯出觀眾
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Importing and exporting audiences{#importing-and-exporting-audiences}

## 匯入對象 {#importing-an-audience}

您可以透過收件者清單，將觀眾／區段從Audience Manager或People核心服務匯入Adobe Campaign。

1. 前往Adobe Campaign **[!UICONTROL Profiles and Targets]** 總 **[!UICONTROL Lists]** 管中的>節點。
1. 在動作列中，選取 **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**。

   ![](assets/aam_import_audience.png)

1. 在開啟的視窗中，按一 **[!UICONTROL Select a shared audience]** 下以前往其他Adobe Experience cloud解決方案中可用的共用觀眾／區段清單。
1. 選取對象並確認。 觀眾的資訊會自動完成。

   請注意，若要匯入共用的觀眾，您應在管理控制台中指派 **[!UICONTROL Audience library]** 產品，並成為Audience manager的管理員。 如需詳細資訊，請參閱「管理控制台」 [檔案](https://helpx.adobe.com/enterprise/managing/user-guide.html)。

   ![](assets/aam_import_audience_3.png)

1. 從欄位中選擇AMC數 **[!UICONTROL AMC Data source]** 據源以定義所需的資料類型。

   ![](assets/aam_import_audience_2.png)

1. 儲存觀眾。

觀眾會透過技術工作流程匯入。 匯入的清單包含可使用AMC資料來源進行調節的元素。 Adobe Campaign未識別的元素不會匯入。

從People核心服務或Audience manager直接匯入區段時，匯入程式需要24-36小時才能同步。 在這段期間後，您就可以在Adobe Campaign中尋找並使用您的新觀眾。

>[!NOTE]
>
>如果您要將觀眾從Adobe Analytics匯入Adobe Campaign，這些觀眾必須先在People Core Service或Audience manager中共用。 此程式需要12-24小時，這必須新增至與Campaign同步的24-36小時。
>
>在此特定情況下，觀眾分享的時間最長可達60小時。 如需People Core服務和Audience Manager中Adobe Analytics觀眾分享的詳細資訊，請參閱本文 [件](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html)。

每次同步觀眾資料時，都會完全取代觀眾資料。 只能匯入區段。 不支援精細資料，包括索引鍵值配對、特徵和規則。

## 匯出觀眾 {#exporting-an-audience}

您可以使用工作流程，將觀眾從Adobe Campaign匯出至Audience Manager或People核心服務。 本文檔詳細介紹了建立和使用工作流 [的過程](../../workflow/using/building-a-workflow.md)。 匯出的觀眾會儲存為People核心服務中的區段：

1. 建立新的定位工作流程。
1. 使用可用的不同活動，鎖定一組收件者。
1. 定位後，拖放活動 **[!UICONTROL Update shared audience]** ，然後開啟。

   ![](assets/aam_export_example.png)

1. 定義您要透過選項匯出的對 **[!UICONTROL Select a shared audience]** 像。 在開啟的視窗中，您可以選取現有的對象或建立新的對象。

   如果您選取現有對象，則只會將新記錄新增至對象。

   若要將收件者清單匯出至新對象，請填妥欄位， **[!UICONTROL Segment name]** 然後按一下 **[!UICONTROL Create]** 再選取新建立的對象。

   按一下窗口右上方的檢查符號，然後按一下按鈕，完成操 **[!UICONTROL OK]** 作。

1. 選擇要 **[!UICONTROL AMC Data source]** 指定預期資料類型的。 自動確定方案。

   ![](assets/aam_export_audience_activity.png)

1. 儲存觀眾。

然後會匯出觀眾。 儲存觀眾活動有兩個對外轉場。 主要轉場包含成功匯出的收件者。 其他轉場包含無法與訪客ID或宣告的ID對應的收件者。

Adobe Campaign和People核心服務之間的同步化需要24-36小時。 在這段期間後，您將可在People核心服務中尋找新的受眾，並在其他Adobe Experience cloud解決方案中重複使用。 如需在Adobe People核心服務中使用Adobe Campaign共用觀眾的詳細資訊，請參閱本文 [件](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html)。

>[!NOTE]
>
>為了進行協調，這些記錄必須有Adobe Experience Cloud ID（&#39;visitor ID&#39;或&#39;declared ID&#39;）。 匯出和匯入觀眾時，不具有Adobe Experience Cloud ID的記錄會被忽略。

