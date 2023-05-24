---
product: campaign
title: 同步設定檔
description: 瞭解如何與ACS Connector同步設定檔
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 3%

---

# 同步設定檔{#synchronizing-profiles}



ACS Connector會將資料從Campaign v7複製到Campaign Standard。 從Campaign v7收到的資料可用於Campaign Standard建立傳遞。 您可以透過執行下列操作，檢視設定檔的同步方式。

* **新增收件者**：在Campaign v7中建立新收件者，並確認對應的設定檔已復寫至Campaign Standard。 另請參閱 [建立新收件者](#creating-a-new-recipient).
* **更新收件者**：在Campaign v7中編輯新收件者，並在Campaign Standard中檢視對應的設定檔，以確認已復寫更新。 另請參閱 [編輯收件者](#editing-a-recipient).
* **以Campaign Standard建立工作流程**：在Campaign Standard中建立工作流程，該工作流程包含具有從Campaign v7復寫之對象或設定檔的查詢。 另請參閱 [建立工作流程](#creating-a-workflow).
* **在Campaign Standard中建立傳遞**：依照工作流程完成以傳送傳遞。 另請參閱 [建立傳遞](#creating-a-delivery).
* **驗證取消訂閱連結**：使用Campaign v7網頁應用程式，確定收件者取消訂閱服務的選擇已傳送至Campaign v7資料庫。 停止接收服務的選項會複製到Campaign Standard。 另請參閱 [變更取消訂閱連結](#changing-the-unsubscription-link).

## 必要條件 {#prerequisites}

以下章節說明ACS Connector如何協助您在Campaign v7中新增和編輯收件者，然後在Campaign Standard傳送中使用他們。 ACS Connector需要下列專案：

* Campaign v7中的收件者已復寫至Campaign Standard。
* 在Campaign v7和Campaign Standard中執行工作流程的使用者許可權。
* 以Campaign Standard建立和執行傳遞的使用者許可權。

## 變更取消訂閱連結 {#changing-the-unsubscription-link}

當收件者按一下Campaign Standard傳送的電子郵件中的取消訂閱連結時，Campaign Standard中的對應設定檔會更新。 為確保復寫設定檔包含使用者取消訂閱服務的選擇，資訊必須傳送至Campaign v7而不是Campaign Standard。 為了執行變更，取消訂閱服務會連結至Campaign v7網頁應用程式，而非Campaign Standard。

>[!NOTE]
>
>請要求您的顧問先設定取消訂閱服務的Web應用程式，然後再執行下列步驟。

## 建立新收件者 {#creating-a-new-recipient}

1. 在Campaign v7中建立新的收件者，以復寫至Campaign Standard。 輸入儘可能多的資訊，包括收件者的姓氏、名字、電子郵件地址和郵寄地址。 不過，請勿選擇 **[!UICONTROL Salutation]** 因為它將新增到下一節， [編輯收件者](#editing-a-recipient). 如需詳細資訊，請參閱 [新增收件者](../../platform/using/adding-profiles.md).

   ![](assets/acs_connect_profile_sync_01.png)

1. 確認新收件者已新增至Campaign Standard。 檢閱設定檔時，請確定您在Campaign v7中輸入的資料也可在Campaign Standard中使用。 若要瞭解在Campaign Standard中尋找設定檔的位置，請參閱 [導覽基本需知](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=zh-Hant).

   ![](assets/acs_connect_profile_sync_02.png)

   根據預設，ACS Connector的定期復寫每15分鐘一次。 如需詳細資訊，請參閱 [資料復寫](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## 編輯收件者 {#editing-a-recipient}

以下變更單一資料點的步驟提供簡單範例，說明Campaign v7如何在使用資料複製時成為Campaign Standard的主要資料庫。 修改或刪除Campaign v7中的複製資料對Campaign Standard中對應的資料具有相同的效果。

1. 選擇新建立的收件者 [建立新收件者](#creating-a-new-recipient) 並編輯收件者的名稱。 例如，選擇 **[!UICONTROL Salutation]** 收件者（例如先生或太太）。 如需詳細資訊，請參閱 [編輯設定檔](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_03.png)

1. 確認收件者的名稱已更新Campaign Standard。 若要瞭解在Campaign Standard中尋找設定檔的位置，請參閱 [導覽基本需知](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=zh-Hant).

   ![](assets/acs_connect_profile_sync_04.png)

   根據預設，ACS Connector的定期復寫每15分鐘一次。 如需詳細資訊，請參閱 [資料復寫](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## 建立工作流程 {#creating-a-workflow}

數位行銷人員可以使用Campaign v7複製的設定檔和服務來運用Campaign Standard中的豐富資料。 以下指示會示範如何將查詢新增至Campaign Standard工作流程，然後將其用於復寫資料庫。

如需Campaign Standard工作流程的詳細資訊和完整指示，請參閱 [工作流程](../../workflow/using/about-workflows.md).

1. 前往Campaign Standard並按一下 **[!UICONTROL Marketing Activities]**.
1. 按一下 **[!UICONTROL Create]** 右上角。
1. 按一下&#x200B;**[!UICONTROL Workflow]**。
1. 按一下 **[!UICONTROL New workflow]** 和 **[!UICONTROL Next]**.
1. 在中輸入工作流程的名稱 **[!UICONTROL Label]** 欄位和其他資訊（如有需要）。 按一下&#x200B;**[!UICONTROL Next]**。
1. 從 **[!UICONTROL Targeting]** 在左側，拖曳 **[!UICONTROL Query]** 目標定位至工作區。

   ![](assets/acs_connect_profile_sync_05.png)

1. 按兩下 **[!UICONTROL Query]** 活動，並選擇可與復寫資料庫搭配使用的引數。 例如，您可以：

   * 拖曳 **[!UICONTROL Profiles]** 至工作區。 使用欄位下拉式功能表來選擇 **[!UICONTROL Is external resource]** 以尋找從Campaign v7複製的設定檔。
   * 拖曳其他查詢引數以進一步鎖定復寫設定檔。

## 建立傳遞 {#creating-a-delivery}

>[!NOTE]
>
>建立傳遞的指示會繼續執行工作流程，開頭為 [建立工作流程](#creating-a-workflow).

數位行銷人員可善用Campaign v7網頁應用程式，確保將收件者取消訂閱服務的選擇傳送至Campaign v7資料庫。 收件者按一下取消訂閱連結後，停止接收服務的選項會從Campaign v7複製到Campaign Standard。 如需其他詳細資訊，請參閱 [變更取消訂閱連結](#changing-the-unsubscription-link).

請依照下列步驟，使用Campaign v7中建立的取消訂閱服務，將電子郵件傳遞新增至現有工作流程。 如需Campaign Standard工作流程的詳細資訊和完整指示，請參閱此 [檔案](../../workflow/using/about-workflows.md).

>[!NOTE]
>
>請要求您的顧問先設定取消訂閱服務的Web應用程式，然後再執行下列步驟。

1. 按一下 **[!UICONTROL Channels]** 左側。
1. 拖曳 **[!UICONTROL Email delivery]** 至工作區中的現有工作流程。

   ![](assets/acs_connect_profile_sync_07.png)

1. 按兩下 **[!UICONTROL Email delivery]** 活動並選取 **[!UICONTROL Single send email]** 或 **[!UICONTROL Recurring email]**. 選取您的選項並按一下 **[!UICONTROL Next]**.
1. 按一下 **[!UICONTROL Send via email]** 並按一下 **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. 在中輸入傳遞的名稱 **[!UICONTROL Label]** 欄位和其他資訊（如有需要）。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_09.png)

1. 在 **[!UICONTROL Subject]** 欄位，輸入將顯示在收件者電子郵件收件匣中的主旨。
1. 按一下 **[!UICONTROL Change content]** 以新增HTML範本。

   ![](assets/acs_connect_profile_sync_10.png)

1. 選擇包含取消訂閱服務連結的內容。 按一下&#x200B;**[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_11.png)

1. 目前的取消訂閱連結必須由使用您的顧問所建立Web應用程式的新連結取代。 在電子郵件內容底部找到取消訂閱連結，然後按一下該連結一次。 按一下垃圾桶圖示以刪除連結。

   ![](assets/acs_connect_profile_sync_12.png)

1. 在相同內容區域內按一下並輸入 **取消訂閱連結**.

   ![](assets/acs_connect_profile_sync_13.png)

1. 用游標反白文字，然後按一下鏈圖示。
1. 按一下&#x200B;**[!UICONTROL Link to a landing page]**。

   ![](assets/acs_connect_profile_sync_14.png)

1. 按一下資料夾圖示以選擇登陸頁面。

   ![](assets/acs_connect_profile_sync_15.png)

1. 選擇顧問建立的網頁應用程式，然後按一下 **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_16.png)

1. 按一下&#x200B;**[!UICONTROL Create]**。
1. 按一下傳遞名稱以返回工作流程。

   ![](assets/acs_connect_profile_sync_17.png)

1. 按一下 **[!UICONTROL Start]** 以傳送傳遞。 電子郵件傳遞圖示會閃爍，表示正在準備進行傳遞。

   ![](assets/acs_connect_profile_sync_18.png)

1. 按兩下 **[!UICONTROL Email delivery]** 頻道和選擇 **[!UICONTROL Confirm]** 以傳送電子郵件。 按一下 **[!UICONTROL OK]** 以傳送訊息。

   ![](assets/acs_connect_profile_sync_19.png)

## 驗證取消訂閱服務 {#verifying-the-unsubscription-service}

請依照下列說明操作： [建立工作流程](#creating-a-workflow) 和 [建立傳遞](#creating-a-delivery) 繼續進行下列步驟之前。

1. 收件者按一下電子郵件傳遞中的取消訂閱連結。

   ![](assets/acs_connect_profile_sync_20.png)

1. 收件者會確認取消訂閱。

   ![](assets/acs_connect_profile_sync_21.png)

1. Campaign v7中的收件者資料已更新，以反映使用者已取消訂閱。 確認方塊 **[!UICONTROL No longer contact (by any channel)]** 已檢查收件者。 若要瞭解如何在Campaign v7中檢視收件者，請參閱 [編輯設定檔](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_22.png)

1. 前往Campaign Standard並開啟收件者的設定檔詳細資料。 確認旁邊會顯示核取方塊 **[!UICONTROL No longer contact (by any channel)]**. 若要瞭解在Campaign Standard中尋找設定檔的位置，請參閱 [導覽基本需知](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=zh-Hant).

   ![](assets/acs_connect_profile_sync_23.png)
