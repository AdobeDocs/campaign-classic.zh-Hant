---
product: campaign
title: 同步設定檔
description: 瞭解如何使配置檔案與ACS連接器同步
feature: ACS Connector
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 3%

---

# 同步設定檔{#synchronizing-profiles}

![](../../assets/v7-only.svg)

ACS Connector將資料從Campign v7複製到Campaign Standard。 從「市場活動v7」接收的資料可用於Campaign Standard建立交貨。 通過執行下面列出的操作，您可以瞭解配置式的同步方式。

* **添加新收件人**:在市場活動v7中建立新收件人，並確認已將相應的配置檔案複製到Campaign Standard。 請參閱 [建立新收件人](#creating-a-new-recipient)。
* **更新收件人**:在市場活動v7中編輯新收件人，並查看Campaign Standard中的相應配置檔案，以確認已複製更新。 請參閱 [編輯收件人](#editing-a-recipient)。
* **在Campaign Standard中生成工作流**:在Campaign Standard中建立工作流，該工作流包含從「市場活動v7」複製的受眾或配置檔案的查詢。 請參閱 [建立工作流](#creating-a-workflow)。
* **在Campaign Standard中建立交貨**:按照工作流完成以發送交貨。 請參閱 [建立交貨](#creating-a-delivery)。
* **驗證取消訂閱連結**:使用「市場活動v7」 Web應用程式可確保收件人取消訂閱服務的選擇已發送到「市場活動v7」資料庫。 停止接收服務的選項被複製到Campaign Standard。 請參閱 [更改取消訂閱連結](#changing-the-unsubscription-link)。

## 必要條件 {#prerequisites}

以下各節介紹ACS連接器如何幫助您在市場活動v7中添加和編輯收件人，然後在Campaign Standard交付中使用這些收件人。 ACS連接器需要：

* 市場活動v7中的收件人已複製到Campaign Standard。
* 在市場活動v7和Campaign Standard中執行工作流的用戶權限。
* 用於在Campaign Standard中建立和執行傳遞的用戶權限。

## 更改取消訂閱連結 {#changing-the-unsubscription-link}

當收件人按一下Campaign Standard發送的電子郵件中的取消訂閱連結時，Campaign Standard中的相應配置檔案被更新。 要確保複製的配置檔案包括用戶取消訂閱服務的選擇，必須將資訊發送到「市場活動v7」，而不是Campaign Standard。 要執行更改，取消訂閱服務將連結到Campign v7 Web應用程式，而不是Campaign Standard。

>[!NOTE]
>
>請咨詢顧問為取消訂閱服務配置Web應用程式，然後執行以下步驟。

## 建立新收件人 {#creating-a-new-recipient}

1. 在市場活動v7中建立新收件人，以便複製到Campaign Standard。 輸入盡可能多的資訊，包括收件人的姓、名、電子郵件地址和郵政地址。 但是，不要選擇 **[!UICONTROL Salutation]** 因為它將被添加到下一節， [編輯收件人](#editing-a-recipient)。 有關詳細資訊，請參見 [添加收件人](../../platform/using/adding-profiles.md)。

   ![](assets/acs_connect_profile_sync_01.png)

1. 確認新收件人已添加到Campaign Standard。 複查配置檔案時，確保在「市場活動7」中輸入的資料也可以在Campaign Standard中使用。 要瞭解在Campaign Standard中查找配置檔案的位置，請參閱 [導航基礎](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=zh-Hant)。

   ![](assets/acs_connect_profile_sync_02.png)

   預設情況下，ACS連接器的定期複製每15分鐘一次。 有關詳細資訊，請參見 [資料複製](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 編輯收件人 {#editing-a-recipient}

下面用於更改單點資料的步驟提供了一個簡單的示例，說明在使用資料複製時，Campign v7如何成為Campaign Standard的主資料庫。 修改或刪除市場活動v7中的複製資料對Campaign Standard中的相應資料具有相同的效果。

1. 從中選擇新建立的收件人 [建立新收件人](#creating-a-new-recipient) 編輯收件人姓名。 例如，選擇 **[!UICONTROL Salutation]** 收件人（例如，先生或夫人）。 有關詳細資訊，請參見 [編輯配置檔案](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_03.png)

1. 確認收件人的姓名已在Campaign Standard中更新。 要瞭解在Campaign Standard中查找配置檔案的位置，請參閱 [導航基礎](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_04.png)

   預設情況下，ACS連接器的定期複製每15分鐘一次。 有關詳細資訊，請參見 [資料複製](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)。

## 建立工作流程 {#creating-a-workflow}

從Campaing v7複製的配置檔案和服務可供數字營銷人員使用，以利用Campaign Standard中的豐富資料。 下面的說明說明如何將查詢添加到Campaign Standard工作流中，然後將其與複製的資料庫一起使用。

有關Campaign Standard工作流的詳細資訊和完整說明，請參見 [工作流](../../workflow/using/about-workflows.md)。

1. 轉到Campaign Standard並按一下 **[!UICONTROL Marketing Activities]**。
1. 按一下 **[!UICONTROL Create]** 右上角。
1. 按一下&#x200B;**[!UICONTROL Workflow]**。
1. 按一下 **[!UICONTROL New workflow]** 和 **[!UICONTROL Next]**。
1. 在 **[!UICONTROL Label]** 欄位和其他資訊（如果需要）。 按一下&#x200B;**[!UICONTROL Next]**。
1. 從 **[!UICONTROL Targeting]** 在左側，拖動 **[!UICONTROL Query]** 目標到工作區。

   ![](assets/acs_connect_profile_sync_05.png)

1. 按兩下 **[!UICONTROL Query]** 活動，然後選擇可與複製的資料庫一起使用的參數。 例如，您可以：

   * 拖動 **[!UICONTROL Profiles]** 的子菜單。 使用欄位下拉菜單來選擇 **[!UICONTROL Is external resource]** 查找從Campaign v7複製的配置檔案。
   * 拖動其他查詢參數以進一步瞄準已複製的配置檔案。

## 建立交貨 {#creating-a-delivery}

>[!NOTE]
>
>建立交貨的說明繼續工作流啟動時使用 [建立工作流](#creating-a-workflow)。

數字營銷人員可以利用市場活動v7 Web應用程式來確保收件人取消訂閱服務的選擇已發送到市場活動v7資料庫。 收件人按一下取消訂閱連結後，停止接收服務的選項將從「市場活動7」複製到「Campaign Standard」。 有關其他詳細資訊，請參閱 [更改取消訂閱連結](#changing-the-unsubscription-link)。

按照以下步驟將電子郵件傳遞添加到現有工作流中，該工作流在「市場活動7」中建立了取消訂閱服務。 有關Campaign Standard工作流的詳細資訊和完整說明，請參閱 [文檔](../../workflow/using/about-workflows.md)。

>[!NOTE]
>
>請咨詢顧問為取消訂閱服務配置Web應用程式，然後執行以下步驟。

1. 按一下 **[!UICONTROL Channels]** 左邊。
1. 拖動 **[!UICONTROL Email delivery]** 工作區中的現有工作流。

   ![](assets/acs_connect_profile_sync_07.png)

1. 按兩下 **[!UICONTROL Email delivery]** 活動和選擇 **[!UICONTROL Single send email]** 或 **[!UICONTROL Recurring email]**。 選擇選項並按一下 **[!UICONTROL Next]**。
1. 按一下 **[!UICONTROL Send via email]** 按一下 **[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_08.png)

1. 在 **[!UICONTROL Label]** 欄位和其他資訊（如果需要）。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_profile_sync_09.png)

1. 在 **[!UICONTROL Subject]** 欄位中，輸入將出現在收件人電子郵件收件箱中的主題。
1. 按一下 **[!UICONTROL Change content]** 的子菜單。

   ![](assets/acs_connect_profile_sync_10.png)

1. 選擇包含連結的內容以取消訂閱服務。 按一下&#x200B;**[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_11.png)

1. 當前取消訂閱連結必須替換為使用顧問建立的Web應用程式的新連結。 找到電子郵件內容底部的取消訂閱連結，然後按一下一次。 按一下垃圾桶表徵圖可刪除連結。

   ![](assets/acs_connect_profile_sync_12.png)

1. 按一下同一內容區域並鍵入 **取消訂閱連結**。

   ![](assets/acs_connect_profile_sync_13.png)

1. 用游標突出顯示文本，然後按一下鏈表徵圖。
1. 按一下&#x200B;**[!UICONTROL Link to a landing page]**。

   ![](assets/acs_connect_profile_sync_14.png)

1. 按一下資料夾表徵圖以選擇登錄頁。

   ![](assets/acs_connect_profile_sync_15.png)

1. 選擇顧問建立的Web應用程式，然後按一下 **[!UICONTROL Confirm]**。

   ![](assets/acs_connect_profile_sync_16.png)

1. 按一下&#x200B;**[!UICONTROL Create]**。
1. 通過按一下傳遞名稱返回工作流。

   ![](assets/acs_connect_profile_sync_17.png)

1. 按一下 **[!UICONTROL Start]** 寄送。 電子郵件傳遞表徵圖閃爍以指示正在準備傳遞。

   ![](assets/acs_connect_profile_sync_18.png)

1. 按兩下 **[!UICONTROL Email delivery]** 頻道和選擇 **[!UICONTROL Confirm]** 發送電子郵件。 按一下 **[!UICONTROL OK]** 發送消息。

   ![](assets/acs_connect_profile_sync_19.png)

## 驗證取消訂閱服務 {#verifying-the-unsubscription-service}

按照中的說明操作 [建立工作流](#creating-a-workflow) 和 [建立交貨](#creating-a-delivery) 執行以下步驟。

1. 收件人按一下電子郵件傳遞中的取消訂閱連結。

   ![](assets/acs_connect_profile_sync_20.png)

1. 收件人確認取消訂閱。

   ![](assets/acs_connect_profile_sync_21.png)

1. 更新市場活動v7中的收件人資料，以反映用戶已取消訂閱。 確認框 **[!UICONTROL No longer contact (by any channel)]** 已檢查收件人。 要瞭解如何在市場活動v7中查看收件人，請參閱 [編輯配置檔案](../../platform/using/editing-a-profile.md)。

   ![](assets/acs_connect_profile_sync_22.png)

1. 轉到Campaign Standard並開啟收件人的配置檔案詳細資訊。 確認旁邊出現複選框 **[!UICONTROL No longer contact (by any channel)]**。 要瞭解在Campaign Standard中查找配置檔案的位置，請參閱 [導航基礎](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html)。

   ![](assets/acs_connect_profile_sync_23.png)
