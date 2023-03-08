---
product: campaign
title: 同步設定檔
description: 了解如何將配置檔案與ACS Connector同步
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
source-git-commit: 978da934b483a54509ad806f375d9b2bb0577dac
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 3%

---

# 同步設定檔{#synchronizing-profiles}

![](../../assets/v7-only.svg)

ACS連接器將資料從Campaign v7複製到Campaign Standard。 從Campaign v7收到的資料可用於Campaign Standard以建立傳送。 您可以執行下列操作，了解設定檔的同步方式。

* **新增收件者**:在Campaign v7中建立新收件者，並確認已將對應的設定檔複製至Campaign Standard。 請參閱 [建立新收件者](#creating-a-new-recipient).
* **更新收件者**:在Campaign v7中編輯新收件者，並在Campaign Standard中檢視對應的設定檔，以確認已複製更新。 請參閱 [編輯收件者](#editing-a-recipient).
* **在Campaign Standard中建立工作流程**:在Campaign Standard中建立工作流程，包括從Campaign v7複製的對象或設定檔的查詢。 請參閱 [建立工作流程](#creating-a-workflow).
* **在Campaign Standard中建立傳送**:請依照工作流程完成，以傳送傳遞。 請參閱 [建立傳送](#creating-a-delivery).
* **驗證取消訂閱連結**:使用Campaign v7 Web應用程式，以確定收件者選擇取消訂閱服務的選項會傳送至Campaign v7資料庫。 停止接收服務的選項被複製到Campaign Standard。 請參閱 [變更取消訂閱連結](#changing-the-unsubscription-link).

## 必要條件 {#prerequisites}

以下幾節說明ACS連接器如何協助您在Campaign v7中新增和編輯收件者，然後在Campaign Standard傳送中使用收件者。 ACS Connector需要下列項：

* Campaign v7中的收件者已復寫至Campaign Standard。
* 在Campaign v7和Campaign Standard中執行工作流程的使用者權限。
* 在Campaign Standard中建立和執行傳送的使用者權限。

## 變更取消訂閱連結 {#changing-the-unsubscription-link}

當收件者按一下Campaign Standard所傳送電子郵件中的取消訂閱連結時，會更新Campaign Standard中的對應設定檔。 為了確定已復寫的設定檔包含使用者選擇取消訂閱服務，必須將資訊傳送至Campaign v7，而非Campaign Standard。 若要執行變更，取消訂閱服務會連結至Campaign v7 Web應用程式，而非Campaign Standard。

>[!NOTE]
>
>請您的顧問先為取消訂閱服務設定Web應用程式，然後再執行下列步驟。

## 建立新收件者 {#creating-a-new-recipient}

1. 在Campaign v7中建立新收件者，以便復寫至Campaign Standard。 輸入盡可能多的資訊，包括收件者的姓氏、名字、電子郵件地址和郵遞區號。 但請勿選擇 **[!UICONTROL Salutation]** 因為會在下一節中新增， [編輯收件者](#editing-a-recipient). 如需詳細資訊，請參閱 [新增收件者](../../platform/using/adding-profiles.md).

   ![](assets/acs_connect_profile_sync_01.png)

1. 確認新收件者已新增至Campaign Standard。 檢閱設定檔時，請確定您在Campaign v7中輸入的資料也可在Campaign Standard中使用。 若要了解在Campaign Standard中尋找設定檔的位置，請參閱 [導覽基本知識](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=zh-Hant).

   ![](assets/acs_connect_profile_sync_02.png)

   預設情況下，ACS Connector的定期複製為每15分鐘一次。 如需詳細資訊，請參閱 [資料復寫](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## 編輯收件者 {#editing-a-recipient}

以下變更單一資料點的步驟提供了一個簡單範例，說明當使用資料復寫時，Campaign v7如何成為Campaign Standard的主要資料庫。 修改或刪除Campaign v7中的已復寫資料，對Campaign Standard中的對應資料會有相同的影響。

1. 從中選擇新建立的收件人 [建立新收件者](#creating-a-new-recipient) 並編輯收件者的姓名。 例如，選擇 **[!UICONTROL Salutation]** 收件者（例如，先生或太太）。 如需詳細資訊，請參閱 [編輯設定檔](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_03.png)

1. 確認收件者的名稱已以Campaign Standard更新。 若要了解在Campaign Standard中尋找設定檔的位置，請參閱 [導覽基本知識](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=zh-Hant).

   ![](assets/acs_connect_profile_sync_04.png)

   預設情況下，ACS Connector的定期複製為每15分鐘一次。 如需詳細資訊，請參閱 [資料復寫](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## 建立工作流程 {#creating-a-workflow}

數位行銷人員可使用從Campaign v7複製的設定檔和服務，在Campaign Standard中運用豐富的資料。 以下說明演示如何將查詢添加到Campaign Standard工作流，然後與複製的資料庫一起使用。

如需Campaign Standard工作流程的詳細資訊和完整指示，請參閱 [工作流程](../../workflow/using/about-workflows.md).

1. 前往Campaign Standard，然後按一下 **[!UICONTROL Marketing Activities]**.
1. 按一下 **[!UICONTROL Create]** 在右上角。
1. 按一下&#x200B;**[!UICONTROL Workflow]**。
1. 按一下 **[!UICONTROL New workflow]** 和 **[!UICONTROL Next]**.
1. 在 **[!UICONTROL Label]** 欄位和其他資訊（如有需要）。 按一下&#x200B;**[!UICONTROL Next]**。
1. 從 **[!UICONTROL Targeting]** 在左側，拖曳 **[!UICONTROL Query]** 定位至工作區。

   ![](assets/acs_connect_profile_sync_05.png)

1. 按兩下 **[!UICONTROL Query]** 活動，並選擇可與複製資料庫一起使用的參數。 例如，您可以：

   * 拖曳 **[!UICONTROL Profiles]** 至工作區。 使用欄位下拉式功能表來選擇 **[!UICONTROL Is external resource]** 尋找從Campaign v7複製的設定檔。
   * 拖曳其他查詢參數，以進一步鎖定已復寫的設定檔。

## 建立傳送 {#creating-a-delivery}

>[!NOTE]
>
>建立傳送的指示會繼續開始的工作流程 [建立工作流程](#creating-a-workflow).

數位行銷人員可運用Campaign v7 Web應用程式，以確定收件者選擇取消訂閱服務的選項會傳送至Campaign v7資料庫。 收件者按一下取消訂閱連結後，停止接收服務的選項會從Campaign v7複製到Campaign Standard。 如需其他詳細資訊，請參閱 [變更取消訂閱連結](#changing-the-unsubscription-link).

請依照下列步驟，使用在Campaign v7中建立的取消訂閱服務，將電子郵件傳送新增至現有的工作流程。 如需Campaign Standard工作流程的詳細資訊和完整指示，請參閱此 [檔案](../../workflow/using/about-workflows.md).

>[!NOTE]
>
>請您的顧問先為取消訂閱服務設定Web應用程式，然後再執行下列步驟。

1. 按一下 **[!UICONTROL Channels]** 左邊。
1. 拖曳 **[!UICONTROL Email delivery]** 至工作區中的現有工作流程。

   ![](assets/acs_connect_profile_sync_07.png)

1. 按兩下 **[!UICONTROL Email delivery]** 活動與選擇 **[!UICONTROL Single send email]** 或 **[!UICONTROL Recurring email]**. 選取選項，然後按一下 **[!UICONTROL Next]**.
1. 按一下 **[!UICONTROL Send via email]** 按一下 **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. 在 **[!UICONTROL Label]** 欄位和其他資訊（如有需要）。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_09.png)

1. 在 **[!UICONTROL Subject]** 欄位中，輸入要出現在收件者電子郵件收件匣中的主旨。
1. 按一下 **[!UICONTROL Change content]** 新增HTML範本。

   ![](assets/acs_connect_profile_sync_10.png)

1. 選擇包含要取消訂閱服務的連結的內容。 按一下&#x200B;**[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_11.png)

1. 目前的取消訂閱連結必須替換為使用顧問建立之Web應用程式的新連結。 在電子郵件內容底部找到取消訂閱連結，然後按一下。 按一下垃圾桶圖示以刪除連結。

   ![](assets/acs_connect_profile_sync_12.png)

1. 按一下相同內容區域內的，然後輸入 **取消訂閱連結**.

   ![](assets/acs_connect_profile_sync_13.png)

1. 用游標突出顯示文本，然後按一下鏈表徵圖。
1. 按一下&#x200B;**[!UICONTROL Link to a landing page]**。

   ![](assets/acs_connect_profile_sync_14.png)

1. 按一下資料夾圖示以選擇登錄頁面。

   ![](assets/acs_connect_profile_sync_15.png)

1. 選擇顧問建立的Web應用程式，然後按一下 **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_16.png)

1. 按一下&#x200B;**[!UICONTROL Create]**。
1. 按一下傳送名稱以返回工作流程。

   ![](assets/acs_connect_profile_sync_17.png)

1. 按一下 **[!UICONTROL Start]** 來傳送傳遞。 電子郵件傳送圖示會閃爍，指出其已準備好傳送。

   ![](assets/acs_connect_profile_sync_18.png)

1. 按兩下 **[!UICONTROL Email delivery]** 通道和選擇 **[!UICONTROL Confirm]** 以傳送電子郵件。 按一下 **[!UICONTROL OK]** 來傳送訊息。

   ![](assets/acs_connect_profile_sync_19.png)

## 驗證取消訂閱服務 {#verifying-the-unsubscription-service}

遵循 [建立工作流程](#creating-a-workflow) 和 [建立傳送](#creating-a-delivery) ，再移至下列步驟。

1. 收件者按一下電子郵件傳送中的取消訂閱連結。

   ![](assets/acs_connect_profile_sync_20.png)

1. 收件者會確認取消訂閱。

   ![](assets/acs_connect_profile_sync_21.png)

1. Campaign v7中的收件者資料會更新，以反映使用者已取消訂閱。 確認方塊 **[!UICONTROL No longer contact (by any channel)]** 已檢查收件者。 若要了解如何在Campaign v7中檢視收件者，請參閱 [編輯設定檔](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_22.png)

1. 前往「Campaign Standard」 ，並開啟收件者的設定檔詳細資訊。 確認核取方塊會出現在 **[!UICONTROL No longer contact (by any channel)]**. 若要了解在Campaign Standard中尋找設定檔的位置，請參閱 [導覽基本知識](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=zh-Hant).

   ![](assets/acs_connect_profile_sync_23.png)
