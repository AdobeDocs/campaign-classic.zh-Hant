---
product: campaign
title: 個人化優惠券
description: 瞭解如何建立和插入個人化優惠券
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Personalization
role: User
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 8e5a328bee7701adfedec6a533cc21b4ce548187
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 1%

---

# 個人化優惠券{#personalized-coupons}

為傳遞新增優惠券，可讓收件者獲得提升的產品和服務價值。 您可以使用Campaign抵用券模組建立一組抵用券，預計新增至即將推出的行銷優惠方案。 當您準備好建立傳遞時，請指派適用的優惠券。 由於優惠券在選取的期間內有效，因此指派的優惠券會唯一連結至其傳遞訊息。 此外，Campaign會在傳送傳遞前，確認訊息數量有足夠的抵用券。

>[!AVAILABILITY]
>
>優惠券管理不適用於企業(FFDA)部署內容中的Campaign v8。 深入瞭解[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}。

優惠券管理依賴必須安裝的套件。 若要確認您有優惠券管理，請核取&#x200B;**[!UICONTROL Administration > Configuration > Package management > Installed packages.]**

抵用券資料可以使用CSV和XML格式匯入和匯出。 [了解更多](../../platform/using/get-started-data-import-export.md)。

## 建立抵用券 {#creating-a-coupon}

建立優惠券時，「優惠券管理」模組提供兩種選項：

* **匿名**：特定收件者或收件者清單的通用優惠券。
* **個人**：特定收件者的個人化優惠券。

在執行以下步驟之前，請確定您知道要建立的抵用券型別。

1. 在行銷活動樹狀結構中，移至&#x200B;**[!UICONTROL Resources > Campaign management > Coupons]**。

   ![](assets/deliv_coup_01.png)

1. 按一下 **[!UICONTROL New]** 按鈕。
1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入優惠券的名稱。 已在&#x200B;**[!UICONTROL Coupon code]**&#x200B;中自動輸入唯一代碼。 您可以保留代碼或輸入新代碼。

   ![](assets/deliv_coup_02.png)

1. 選擇&#x200B;**[!UICONTROL Start date]**&#x200B;與&#x200B;**[!UICONTROL End date]**&#x200B;以設定優惠券的有效期間。
1. 在&#x200B;**[!UICONTROL Coupon type]**&#x200B;中，選擇「匿名」或「個人」。

   **[!UICONTROL Anonymous coupons]** ：所有收件者的匿名抵用券都相同。 確認已在&#x200B;**優惠券型別**&#x200B;功能表中選取「匿名」，然後按一下&#x200B;**儲存**&#x200B;以產生優惠券。

   **[!UICONTROL Individual coupons]** ：個別優惠券可進一步個人化並提供額外優惠券代碼。 例如，在體育器材商店為銷售建立個別優惠券。 不過，收件者名單很長，他們對單一運動沒有相同的熱情。 您可以根據運動（例如足球、足球、棒球等）為個別優惠券新增程式碼名稱 並將每個程式碼傳送給適用的收件者。

   1. 選擇「個人」時，新標籤「抵用券」會出現在左下方。 前往&#x200B;**[!UICONTROL Coupons]**&#x200B;標籤並按一下&#x200B;**[!UICONTROL Add]**。
   1. 在快顯視窗提示時，輸入個別優惠券的唯一代碼。
   1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以產生抵用券。

   如需「優惠券」標籤的詳細資訊，請參閱[設定個別優惠券](#configuring-individual-coupons)。

   >[!NOTE]
   >
   >個別優惠券可大量匯入。 如需有關匯入和匯出的詳細資訊，請參閱[本區段](../../platform/using/get-started-data-import-export.md)。

### 設定個別優惠券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

「優惠券」標籤僅適用於「個別優惠券」。 優惠券與傳遞相關聯後，「優惠券」索引標籤會提供下列詳細資訊：

* **[!UICONTROL Status]** ：優惠券可用性。
* **[!UICONTROL Redeemed on]** ：兌換優惠券的日期。
* **[!UICONTROL Channel]** ：用來傳送抵用券的管道。
* **[!UICONTROL Address]** ：收件者的電子郵件地址。

**[!UICONTROL status]**、**[!UICONTROL channel]**&#x200B;和&#x200B;**[!UICONTROL address]**&#x200B;的值會自動完成。 不過，Campaign不會復原&#x200B;**[!UICONTROL redeemed on]**&#x200B;的值。 您可以匯入具有優惠券兌換詳細資訊的檔案來完成這些作業。

## 在電子郵件傳遞中插入抵用券 {#inserting-a-coupon-into-an-email-delivery}

在下列範例中，會從首頁建立傳送。 如需有關如何建立傳遞的詳細說明，請參閱[本節](about-email-channel.md)。 您也可以在工作流程中新增優惠券至傳遞。

1. 移至&#x200B;**[!UICONTROL Campaigns]**&#x200B;並選擇&#x200B;**[!UICONTROL Deliveries]**。
1. 按一下&#x200B;**[!UICONTROL Create]**。

   ![](assets/deliv_coup_04.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;中輸入名稱並按一下&#x200B;**[!UICONTROL Continue]**。
1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;以新增收件者。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選擇傳遞的收件者。 選取收件者後，按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以返回傳遞。

   ![](assets/deliv_coup_05.png)

1. 輸入主旨並將內容新增至訊息。

   ![](assets/deliv_coup_06.png)

1. 在工具列中按一下&#x200B;**[!UICONTROL Properties]**&#x200B;並選擇&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤。
1. 按一下&#x200B;**[!UICONTROL Coupon management]**&#x200B;的資料夾圖示。

   ![](assets/deliv_coup_07.png)

1. 選擇優惠券並按一下&#x200B;**[!UICONTROL Ok]**。 再按一下&#x200B;**[!UICONTROL Ok]**。

   ![](assets/deliv_coup_08.png)

1. 按一下訊息以選擇要放置抵用券的位置。

   ![](assets/deliv_coup_09.png)

1. 按一下個人化圖示，根據抵用券型別選擇下列其中一項：

   * 匿名優惠券： **[!UICONTROL Coupon > Coupon code]**

     ![](assets/deliv_coup_10.png)

   * 個別優惠券： **[!UICONTROL Coupon value > Coupon code]**

     ![](assets/deliv_coup_11.png)

     抵用券會以程式碼的形式插入訊息中，而非您指派的名稱。 此程式碼用於Campaign ootb資料模型。

   ![](assets/deliv_coup_12.png)

1. 執行測試以確認您指派給優惠券的名稱。 前往&#x200B;**[!UICONTROL Preview]**&#x200B;標籤並按一下&#x200B;**[!UICONTROL Test personalization]**。 選擇測試的收件者。

   ![](assets/deliv_coup_13.png)

   測試後，抵用券應顯示為指派的名稱，而非程式碼。

   ![](assets/deliv_coup_14.png)

1. 在工具列中按一下&#x200B;**[!UICONTROL Send]** （左上方），然後選擇您要傳送傳遞的方式。

   ![](assets/deliv_coup_15.png)

1. 按一下 **[!UICONTROL Analyze]**。如果分析記錄檔確認所有收件者都有足夠的優惠券，請按一下&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;以傳送。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>如需如何管理傳遞不足的抵用券的指示，請參閱[管理不足的抵用券](#managing-insufficient-coupons)

若要確認傳送是否成功：

1. 移至&#x200B;**[!UICONTROL Explorer > Resources > Campaign management > Coupons]**。
1. 按一下「**[!UICONTROL Deliveries]**」標籤。

   ![](assets/deliv_coup_17.png)

   成功傳遞的狀態讀取為&#x200B;**[!UICONTROL Finished]**。

>[!NOTE]
>
>依預設，優惠券管理模組使用&#x200B;**nms：recipient**&#x200B;表格。 [了解更多](../../configuration/using/about-data-model.md#default-recipient-table)。
>
>在此頁面[&#128279;](../../configuration/using/about-custom-recipient-table.md)中瞭解如何使用自訂收件者資料表。

## 管理不足的優惠券 {#managing-insufficient-coupons}

如果抵用券少於訊息，則傳遞分析會停止。 在這種情況下，您可以匯入更多優惠券或限制訊息數量。 如果您要限制訊息數量，請依照下列指示操作。

1. 前往電子郵件傳遞視窗。
1. 按一下&#x200B;**[!UICONTROL To]**。
1. 在&#x200B;**[!UICONTROL Select target]**&#x200B;中，移至&#x200B;**[!UICONTROL Exclusions]**&#x200B;標籤。

   ![](assets/deliv_coup_18.png)

1. 在排除設定區段中，按一下&#x200B;**[!UICONTROL Edit]**。
1. 輸入您要在&#x200B;**[!UICONTROL Limit delivery to...messages]**&#x200B;中傳送的訊息數目，然後按一下&#x200B;**[!UICONTROL Ok]**。 您可以傳送傳遞。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>在管理有限數量的優惠券時，傳遞工作流程可讓您根據條件分割傳遞。 如果您想要在不限制目標的情況下將抵用券傳送給選取的母體，這是一個不錯的選項。
