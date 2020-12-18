---
solution: Campaign Classic
product: campaign
title: 同步設定檔
description: 同步設定檔
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 3%

---


# 同步設定檔{#synchronizing-profiles}

ACS連接器將Campaign v7中的資料複製到Campaign Standard。 從Campaign v7收到的資料可用於Campaign Standard中以建立傳送。 您可以執行下列操作，瞭解配置檔案的同步方式。

* **新增收件者**:在Campaign v7中建立新的收件者，並確認對應的設定檔已複製至Campaign Standard。請參閱[建立新收件者](#creating-a-new-recipient)。
* **更新收件者**:在Campaign v7中編輯新收件者，並在Campaign Standard中檢視對應的設定檔，以確認更新已複製。請參閱[編輯收件人](#editing-a-recipient)。
* **在Campaign Standard中建立工作流程**:在Campaign Standard中建立工作流程，其中包含從Campaign v7複製的對象或個人檔案的查詢。請參閱[建立工作流](#creating-a-workflow)。
* **在Campaign Standard中建立傳送**:依照工作流程完成傳送。請參閱[建立傳送](#creating-a-delivery)。
* **驗證取消訂閱連結**:使用Campaign v7 Web應用程式可確定收件者選擇取消訂閱服務會傳送至Campaign v7資料庫。停止接收服務的選項會複製到Campaign Standard。 請參閱[變更取消訂閱連結](#changing-the-unsubscription-link)。

## 必要條件 {#prerequisites}

以下各節說明ACS連接器如何協助您在Campaign v7中新增和編輯收件者，然後在Campaign Standard傳送中使用這些收件者。 ACS連接器需要：

* Campaign v7中的收件者已複製至Campaign Standard。
* 在Campaign v7和Campaign Standard中執行工作流程的使用者權限。
* 在Campaign Standard中建立和執行傳送的使用者權限。

## 變更取消訂閱連結{#changing-the-unsubscription-link}

當收件者按一下Campaign Standard所傳送之電子郵件中的取消訂閱連結時，Campaign Standard中的對應設定檔會更新。 為確定複製的設定檔包含使用者取消訂閱服務的選擇，必須將資訊傳送至Campaign v7，而非Campaign Standard。 若要執行變更，取消訂閱服務會連結至Campaign v7網頁應用程式，而非Campaign Standard。

>[!NOTE]
>
>請您的顧問在遵循下列步驟之前，先為取消訂閱服務配置Web應用程式。

## 建立新收件人{#creating-a-new-recipient}

1. 在Campaign v7中建立新的收件者，以複製至Campaign Standard。 輸入盡可能多的資訊，包括收件者的姓氏、名字、電子郵件地址和郵遞區號。 但是，請勿選擇&#x200B;**[!UICONTROL Salutation]**，因為[將在下一節中添加](#editing-a-recipient)編輯收件人。 如需詳細資訊，請參閱[新增收件者](../../platform/using/adding-profiles.md)。

   ![](assets/acs_connect_profile_sync_01.png)

1. 確認新的收件者已新增至「促銷活動標準」。 在檢閱描述檔時，請確定您在Campaign v7中輸入的資料也可在Campaign Standard中使用。 若要瞭解在Campaign Standard中尋找描述檔的位置，請參閱[導覽基本資訊](https://docs.adobe.com/content/help/zh-Hant/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_02.png)

   預設情況下，ACS連接器的定期複製每15分鐘一次。 有關詳細資訊，請參見[資料複製](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 編輯收件者{#editing-a-recipient}

以下變更單一資料點的步驟提供一個簡單範例，說明當使用資料複製時，Campaign v7如何成為Campaign Standard的主要資料庫。 修改或刪除Campaign v7中複製的資料對Campaign Standard中的對應資料有相同的影響。

1. 從[建立新收件者](#creating-a-new-recipient)選擇新建立的收件者，並編輯收件者的名稱。 例如，為收件者選擇&#x200B;**[!UICONTROL Salutation]**（例如Mr或Mrs）。 如需詳細資訊，請參閱[編輯描述檔](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_03.png)

1. 確認收件者的名稱已在Campaign Standard中更新。 若要瞭解在Campaign Standard中尋找描述檔的位置，請參閱[導覽基本資訊](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_04.png)

   預設情況下，ACS連接器的定期複製每15分鐘一次。 有關詳細資訊，請參見[資料複製](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 建立工作流程 {#creating-a-workflow}

數位行銷人員可從Campaign v7複製的設定檔和服務，以運用Campaign Standard中的豐富資料。 下列指示說明如何新增查詢至Campaign Standard工作流程，然後與複製的資料庫搭配使用。

如需促銷活動標準工作流程的詳細資訊和完整指示，請參閱[工作流程](../../workflow/using/about-workflows.md)。

1. 前往「促銷活動標準」，然後按一下&#x200B;**[!UICONTROL Marketing Activities]**。
1. 按一下右上方的&#x200B;**[!UICONTROL Create]**。
1. 按一下 **[!UICONTROL Workflow]**。
1. 按一下&#x200B;**[!UICONTROL New workflow]**&#x200B;和&#x200B;**[!UICONTROL Next]**。
1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入工作流程的名稱，並視需要輸入其他資訊。 按一下 **[!UICONTROL Next]**。
1. 從左側的&#x200B;**[!UICONTROL Targeting]**&#x200B;拖曳&#x200B;**[!UICONTROL Query]**&#x200B;目標至工作區。

   ![](assets/acs_connect_profile_sync_05.png)

1. 連按兩下&#x200B;**[!UICONTROL Query]**&#x200B;活動，然後選擇可與複製的資料庫搭配使用的參數。 例如，您可以：

   * 將&#x200B;**[!UICONTROL Profiles]**&#x200B;拖曳至工作區。 使用欄位下拉式選單選擇&#x200B;**[!UICONTROL Is external resource]**，以尋找從Campaign v7複製的描述檔。
   * 拖曳其他查詢參數，以進一步鎖定複製的描述檔。

## 建立傳送{#creating-a-delivery}

>[!NOTE]
>
>建立傳送的指示會繼續以[建立工作流程](#creating-a-workflow)開始的工作流程。

數位行銷人員可運用Campaign v7 Web應用程式，以確定收件者選擇取消訂閱服務會傳送至Campaign v7資料庫。 收件者按一下取消訂閱連結後，停止接收服務的選項會從Campaign v7複製到Campaign Standard。 如需詳細資訊，請參閱[變更取消訂閱連結](#changing-the-unsubscription-link)。

請依照下列步驟，將電子郵件傳送新增至現有的工作流程，並使用在Campaign v7中建立的取消訂閱服務。 如需促銷活動標準工作流程的詳細資訊和完整指示，請參閱此[檔案](../../workflow/using/about-workflows.md)。

>[!NOTE]
>
>請您的顧問在遵循下列步驟之前，先為取消訂閱服務配置Web應用程式。

1. 按一下左側的&#x200B;**[!UICONTROL Channels]**。
1. 將&#x200B;**[!UICONTROL Email delivery]**&#x200B;拖曳至工作區中現有的工作流程。

   ![](assets/acs_connect_profile_sync_07.png)

1. 連按兩下&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動，然後選擇&#x200B;**[!UICONTROL Single send email]**&#x200B;或&#x200B;**[!UICONTROL Recurring email]**。 選擇您的選項，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 按一下&#x200B;**[!UICONTROL Send via email]** ，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_08.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入傳送的名稱，並視需要輸入其他資訊。 按一下 **[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_09.png)

1. 在&#x200B;**[!UICONTROL Subject]**&#x200B;欄位中，輸入將出現在收件者電子郵件收件匣中的主旨。
1. 按一下&#x200B;**[!UICONTROL Change content]**&#x200B;以新增HTML範本。

   ![](assets/acs_connect_profile_sync_10.png)

1. 選擇包含該連結的內容，以取消訂閱服務。 按一下 **[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_11.png)

1. 目前的取消訂閱連結必須由使用顧問所建立之Web應用程式的新連結所取代。 在電子郵件內容底部找到取消訂閱連結，然後按一下該連結一次。 按一下垃圾桶圖示以刪除連結。

   ![](assets/acs_connect_profile_sync_12.png)

1. 按一下相同內容區域內的，然後輸入&#x200B;**取消訂閱連結**。

   ![](assets/acs_connect_profile_sync_13.png)

1. 用游標突出顯示文本，然後按一下鏈表徵圖。
1. 按一下 **[!UICONTROL Link to a landing page]**。

   ![](assets/acs_connect_profile_sync_14.png)

1. 按一下資料夾圖示以選擇著陸頁面。

   ![](assets/acs_connect_profile_sync_15.png)

1. 選擇顧問建立的Web應用程式，然後按一下&#x200B;**[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_16.png)

1. 按一下 **[!UICONTROL Create]**。
1. 按一下傳送名稱以返回工作流程。

   ![](assets/acs_connect_profile_sync_17.png)

1. 按一下&#x200B;**[!UICONTROL Start]**&#x200B;傳送傳送。 電子郵件傳送圖示會閃爍，指出已準備好傳送。

   ![](assets/acs_connect_profile_sync_18.png)

1. 連按兩下&#x200B;**[!UICONTROL Email delivery]**&#x200B;頻道，然後選擇&#x200B;**[!UICONTROL Confirm]**&#x200B;以傳送電子郵件。 按一下&#x200B;**[!UICONTROL OK]**&#x200B;發送消息。

   ![](assets/acs_connect_profile_sync_19.png)

## 驗證取消訂閱服務{#verifying-the-unsubscription-service}

在移至以下步驟之前，請依照[建立工作流程](#creating-a-workflow)和[建立傳送](#creating-a-delivery)中的指示進行。

1. 收件者在電子郵件傳送中按一下取消訂閱連結。

   ![](assets/acs_connect_profile_sync_20.png)

1. 收件者會確認取消訂閱。

   ![](assets/acs_connect_profile_sync_21.png)

1. Campaign v7中的收件者資料會更新，以反映使用者已取消訂閱。 確認已為收件人選中&#x200B;**[!UICONTROL No longer contact (by any channel)]**&#x200B;框。 若要瞭解如何在Campaign v7中檢視收件者，請參閱[編輯設定檔](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_22.png)

1. 前往「促銷活動標準」並開啟收件者的設定檔詳細資訊。 確認&#x200B;**[!UICONTROL No longer contact (by any channel)]**&#x200B;旁邊出現核取方塊。 若要瞭解在Campaign Standard中尋找描述檔的位置，請參閱[導覽基本資訊](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_23.png)

