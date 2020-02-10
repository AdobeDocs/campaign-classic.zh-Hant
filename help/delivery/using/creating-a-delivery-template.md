---
title: 建立傳送範本
seo-title: 建立傳送範本
description: 建立傳送範本
seo-description: null
page-status-flag: never-activated
uuid: 8ceae1ec-9e02-4809-aa8b-1e6bd7790950
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 0e67d9dd-3ee8-4c06-98a4-3a2c644b6c0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Creating a delivery template{#creating-a-delivery-template}

## 將現有傳送轉換為範本 {#converting-an-existing-delivery-to-a-template}

傳送可轉換為範本，以執行新的重複傳送動作。 若要將傳送轉換為範本，請從傳送清單中選取它，此傳送清單可透過樹狀 **[!UICONTROL Campaign management]** 結構的節點存取。

Right-click and select **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

此動作會從選取的傳送建立傳送範本。 您必須輸入儲存資料夾（在欄位中），以及建立 **[!UICONTROL Folder]** 根據此範本所建立之傳送的資料夾(在欄位 **[!UICONTROL Execution folder]** 中)。

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

有關配置模式的詳細資訊，請參 [閱連結模板到交付](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery)。

## 建立新範本 {#creating-a-new-template}

若要設定傳送範本，請執行下列步驟：

1. 開啟促銷活動總管。
1. 在「資源 **」資料夾** ，依序選 **擇「範本** 」和「傳 **送範本」**。

   ![](assets/delivery_template_1.png)

1. 按一 **下工具列** 中的「新增」，以建立新的傳送範本。

   ![](assets/delivery_template_2.png)

1. 修改 **資料夾的** Label **和Internal名稱** 。
1. 儲存範本並重新開啟。
1. 按一下「 **屬性** 」按鈕，然後根據您的需求修改值。

   ![](assets/delivery_template_3.png)

1. 在「一 **般** 」頁籤中，確認或更改「執行」資料夾 **、「資料夾**」和「 ******** RoutingDrop-down」菜單中選定的位置。

   ![](assets/delivery_template_4.png)

1. 使用您的電 **子郵件主旨** ，以及目標人群，完成「電子郵件參數」類別。
1. 新增 **HTML內容** ，以個人化範本，您可以顯示鏡像頁面連結和取消訂閱連結。
1. 選擇「預 **覽** 」標籤。 在「測 **試個人化** 」下拉式選單中，選取「收件者 **** 」以預覽範本作為選擇的設定檔。

   ![](assets/delivery_template_5.png)

1. 按一下 **儲存**。 您的範本現在已可供傳送使用。

>[!NOTE]
>
>為避免設定錯誤，建議您複製原生範本並變更其屬性，而不要建立新範本。
