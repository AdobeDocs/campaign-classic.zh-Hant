---
product: campaign
title: 個人化優惠券
description: 瞭解如何建立和插入個人化優惠券
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 1%

---

# 個人化優惠券{#personalized-coupons}



為傳遞內容新增優惠券，可讓收件者獲得更優異的產品和服務價值。 您可以使用Campaign抵用券模組建立一組抵用券，預計新增至即將推出的行銷優惠方案。 當您準備好建立傳遞時，請指派適用的抵用券。 由於優惠券在選定期間內有效，因此指派的優惠券會唯一連結至其傳遞訊息。 此外，Campaign會確認在傳送傳遞前，訊息數量有足夠的抵用券。

>[!NOTE]
>
>優惠券管理是必須安裝的套件。 若要確認您有優惠券管理，請核取 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>抵用券資料可使用CSV和XML格式匯入和匯出。 有關匯入和匯出的詳細資訊，請參閱 [本節](../../platform/using/get-started-data-import-export.md).

## 建立優惠券 {#creating-a-coupon}

建立優惠券時，優惠券模組提供兩個選項：

* **匿名**：適用於選定收件者或收件者清單的通用抵用券。
* **個人**：為特定收件者提供的個人化優惠券。

在依照下列步驟操作之前，請確定您知道要建立的優惠券型別。

1. 在Campaign樹狀結構中，前往 **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. 按一下 **[!UICONTROL New]** 按鈕。
1. 輸入抵用券的名稱 **[!UICONTROL Label]** 欄位。 已自動輸入唯一代碼 **[!UICONTROL Coupon code]**. 您可以保留代碼或輸入新代碼。

   ![](assets/deliv_coup_02.png)

1. 選擇 **[!UICONTROL Start date]** 和 **[!UICONTROL End date]** 以設定抵用券的有效期間。
1. 在 **[!UICONTROL Coupon type]**，選擇「匿名」或「個人」。

   **[!UICONTROL Anonymous coupons]** ：所有收件者的匿名抵用券都相同。 確認已選取「匿名」於 **優惠券型別** 功能表並按一下 **儲存** 以產生抵用券。

   **[!UICONTROL Individual coupons]** ：個別優惠券可使用其他優惠券代碼進一步個人化。 例如，會為體育器材商店的銷售建立個別優惠券。 不過，收件者名單很長，而且他們對單一運動的熱情並不相同。 您可以根據運動（例如足球、足球、棒球等）為個別優惠券新增代碼名稱 並將每個程式碼傳送給適用的收件者。

   1. 選擇「個人」時，新的標籤「抵用券」會顯示在左下方。 前往 **[!UICONTROL Coupons]** 標籤並按一下 **[!UICONTROL Add]**.
   1. 在快顯視窗提示時，輸入個別優惠券的唯一代碼。
   1. 按一下 **[!UICONTROL Save]** 以產生抵用券。

   如需「抵用券」標籤的詳細資訊，請參閱 [設定個別優惠券](#configuring-individual-coupons).

   >[!NOTE]
   >
   >個別抵用券可以大量匯入。 有關匯入和匯出的詳細資訊，請參閱 [本節](../../platform/using/get-started-data-import-export.md).

### 設定個別優惠券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

「抵用券」標籤僅適用於「個別抵用券」。 優惠券與傳遞相關聯後，「優惠券」索引標籤會提供下列詳細資訊：

* **[!UICONTROL Status]** ：優惠券可用性。
* **[!UICONTROL Redeemed on]** ：抵用券兌換的日期。
* **[!UICONTROL Channel]** ：用來傳送抵用券的管道。
* **[!UICONTROL Address]** ：收件者的電子郵件地址。

以下專案的值： **[!UICONTROL status]**， **[!UICONTROL channel]**、和 **[!UICONTROL address]** 都會自動完成。 然而，下列專案的值 **[!UICONTROL redeemed on]** 不會由Campaign復原。 您可以匯入具有優惠券兌換詳細資訊的檔案來完成這些操作。

## 在電子郵件傳遞中插入抵用券 {#inserting-a-coupon-into-an-email-delivery}

在以下範例中，傳遞是從首頁建立的。 有關如何建立傳送的詳細說明，請參閱 [本節](about-email-channel.md). 您也可以將優惠券新增至工作流程中的傳送。

1. 前往 **[!UICONTROL Campaigns]** 並選擇 **[!UICONTROL Deliveries]**.
1. 按一下&#x200B;**[!UICONTROL Create]**。

   ![](assets/deliv_coup_04.png)

1. 在中輸入名稱 **[!UICONTROL Label]** 並按一下 **[!UICONTROL Continue]**.
1. 按一下 **[!UICONTROL To]** 以新增收件者。
1. 按一下 **[!UICONTROL Add]** 以選擇傳遞的收件者。 選取收件者後，按一下 **[!UICONTROL Ok]** 以返回傳遞。

   ![](assets/deliv_coup_05.png)

1. 輸入主旨並新增內容至訊息。

   ![](assets/deliv_coup_06.png)

1. 在工具列中，按一下 **[!UICONTROL Properties]** 並選擇 **[!UICONTROL Advanced]** 標籤。
1. 按一下資料夾圖示以檢視 **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. 選擇抵用券並按一下 **[!UICONTROL Ok]**. 按一下 **[!UICONTROL Ok]** 再來一次。

   ![](assets/deliv_coup_08.png)

1. 按一下訊息以選擇要放置抵用券的位置。

   ![](assets/deliv_coup_09.png)

1. 按一下個人化圖示，根據優惠券型別選擇下列其中一項：

   * 匿名優惠券： **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 個別優惠券： **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      抵用券會以程式碼的形式插入訊息中，而非您指派的名稱。 此程式碼用於Campaign ootb資料模型。
   ![](assets/deliv_coup_12.png)

1. 執行測試以確認您指派給優惠券的名稱。 前往 **[!UICONTROL Preview]** 標籤並按一下 **[!UICONTROL Test personalization]**. 選擇測試的收件者。

   ![](assets/deliv_coup_13.png)

   測試後，優惠券應該顯示為指派的名稱，而不是代碼。

   ![](assets/deliv_coup_14.png)

1. 在工具列中，按一下 **[!UICONTROL Send]** （左上方）並選擇您要如何傳送傳遞。

   ![](assets/deliv_coup_15.png)

1. 按一下 **[!UICONTROL Analyze]**。如果分析記錄確認有足夠的抵用券供所有收件者使用，請按一下 **[!UICONTROL Confirm delivery]** 以傳送。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>如需如何管理傳遞不足的優惠券的說明，請參閱 [管理不足的優惠券](#managing-insufficient-coupons)

若要確認傳送成功，請執行下列動作：

1. 前往 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. 按一下 **[!UICONTROL Deliveries]** 標籤。

   ![](assets/deliv_coup_17.png)

   狀態顯示為 **[!UICONTROL Finished]** 成功傳遞。

>[!NOTE]
>
>依預設，抵用券管理模組會使用 **nms：recipient** 表格。 [了解更多](../../configuration/using/about-data-model.md#default-recipient-table)。
>
>瞭解如何使用自訂收件者表格 [在此頁面中](../../configuration/using/about-custom-recipient-table.md).

## 管理不足的優惠券 {#managing-insufficient-coupons}

如果抵用券少於訊息，則傳送分析會停止。 在這種情況下，您可以匯入更多優惠券或限制訊息數量。 如果您要限制訊息數量，請依照下列指示操作。

1. 前往電子郵件傳遞視窗。
1. 按一下&#x200B;**[!UICONTROL To]**。
1. 在 **[!UICONTROL Select target]**，前往 **[!UICONTROL Exclusions]** 標籤。

   ![](assets/deliv_coup_18.png)

1. 在排除設定區段中，按一下 **[!UICONTROL Edit]**.
1. 輸入您要傳送的訊息數 **[!UICONTROL Limit delivery to...messages]** 並按一下 **[!UICONTROL Ok]**. 您可以傳送傳遞。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>管理有限數量的抵用券時，傳遞工作流程可讓您根據條件分割傳遞。 如果您想要傳送優惠券給選取的母體，而不限制目標，這是一個很好的選項。
