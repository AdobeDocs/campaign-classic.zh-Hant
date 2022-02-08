---
product: campaign
title: 個人化優惠券
description: 瞭解如何建立和插入個性化優惠券
feature: Personalization
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 1%

---

# 個人化優惠券{#personalized-coupons}

![](../../assets/v7-only.svg)

將優惠券添加到您的交貨中，可以為您的收件人提供更高的產品和服務價值。 您可以使用市場活動優惠券模組建立一組優惠券，您希望這些優惠券可以添加到即將到來的市場營銷優惠。 準備建立交貨時，請分配適用的優惠券。 由於優惠券對於選擇的期間有效，所分配的優惠券唯一地連結到其傳遞消息。 此外，「市場活動」確認在發送傳遞之前有足夠的優惠券來接收郵件數。

>[!NOTE]
>
>優惠券管理是一個必須安裝的包。 要確認您有優惠券管理，請檢查 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>優惠券資料可以使用CSV和XML格式導入和導出。 有關導入和導出的詳細資訊，請參閱 [此部分](../../platform/using/get-started-data-import-export.md)。

## 建立優惠券 {#creating-a-coupon}

優惠券模組在建立優惠券時為您提供了兩種選項：

* **匿名**:所選收件人或收件人清單的通用優惠券。
* **個人**:所選收件人的個性化優惠券。

在執行以下步驟之前，請確保您知道要建立的優惠券類型。

1. 在市場活動樹中，轉到 **[!UICONTROL Resources > Campaign management > Coupons]**。

   ![](assets/deliv_coup_01.png)

1. 按一下 **[!UICONTROL New]** 按鈕。
1. 在中輸入優惠券的名稱 **[!UICONTROL Label]** 的子菜單。 已在中自動輸入唯一代碼 **[!UICONTROL Coupon code]**。 您可以保留代碼或輸入新代碼。

   ![](assets/deliv_coup_02.png)

1. 選擇 **[!UICONTROL Start date]** 和 **[!UICONTROL End date]** 設定優惠券有效的期間。
1. 在 **[!UICONTROL Coupon type]**，選擇匿名或個人。

   **[!UICONTROL Anonymous coupons]** :匿名優惠券對於所有收件人都是相同的。 確認在中選擇了「匿名」 **優惠券類型** 的 **保存** 來生成優惠券。

   **[!UICONTROL Individual coupons]** :利用附加的優惠券代碼可以進一步個性化單個優惠券。 例如，在體育器材商店為銷售而建立單個優惠券。 然而，受獎者名單很長，他們對一項體育運動的熱情也不同。 您可以根據運動（如足球、足球、棒球等）為單個優惠券添加代碼名稱 並將每個代碼發送給相應的收件人。

   1. 選擇「個人」時，左下角會出現一個新標籤「優惠券」。 轉到 **[!UICONTROL Coupons]** 頁籤 **[!UICONTROL Add]**。
   1. 在彈出窗口提示時，為單個優惠券輸入唯一代碼。
   1. 按一下 **[!UICONTROL Save]** 來生成優惠券。

   有關「優惠券」頁籤的詳細資訊，請參閱 [配置單個優惠券](#configuring-individual-coupons)。

   >[!NOTE]
   >
   >單個優惠券可以批量導入。 有關導入和導出的詳細資訊，請參閱 [此部分](../../platform/using/get-started-data-import-export.md)。

### 配置單個優惠券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

優惠券標籤僅與單個優惠券一起提供。 在優惠券與交貨關聯後，「優惠券」標籤提供以下詳細資訊：

* **[!UICONTROL Status]** :優惠券的可用性。
* **[!UICONTROL Redeemed on]** :兌換券的日期。
* **[!UICONTROL Channel]** :用於發送優惠券的渠道。
* **[!UICONTROL Address]** :收件人的電子郵件地址。

值 **[!UICONTROL status]**。 **[!UICONTROL channel]**, **[!UICONTROL address]** 自動完成。 但是， **[!UICONTROL redeemed on]** 未被市場活動恢復。 可以通過導入包含優惠券兌換詳細資訊的檔案來完成這些操作。

## 將優惠券插入電子郵件傳遞 {#inserting-a-coupon-into-an-email-delivery}

在下面的示例中，交貨是從首頁建立的。 有關如何建立交貨的詳細說明，請參閱 [此部分](about-email-channel.md)。 您還可以將優惠券添加到工作流中的交貨中。

1. 轉到 **[!UICONTROL Campaigns]** 選擇 **[!UICONTROL Deliveries]**。
1. 按一下&#x200B;**[!UICONTROL Create]**。

   ![](assets/deliv_coup_04.png)

1. 在中輸入名稱 **[!UICONTROL Label]** 按一下 **[!UICONTROL Continue]**。
1. 按一下 **[!UICONTROL To]** 添加收件人。
1. 按一下 **[!UICONTROL Add]** ，也請參見Wiki頁。 選擇收件人後，按一下 **[!UICONTROL Ok]** 返回交貨。

   ![](assets/deliv_coup_05.png)

1. 輸入主題並將內容添加到消息中。

   ![](assets/deliv_coup_06.png)

1. 在工具欄中，按一下 **[!UICONTROL Properties]** 選擇 **[!UICONTROL Advanced]** 頁籤。
1. 按一下資料夾表徵圖 **[!UICONTROL Coupon management]**。

   ![](assets/deliv_coup_07.png)

1. 選擇優惠券並按一下 **[!UICONTROL Ok]**。 按一下 **[!UICONTROL Ok]** 的雙曲餘切值。

   ![](assets/deliv_coup_08.png)

1. 按一下消息以選擇要放置優惠券的位置。

   ![](assets/deliv_coup_09.png)

1. 按一下個性化表徵圖，根據優惠券類型選擇以下選項之一：

   * 匿名優惠券： **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 單個優惠券： **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      優惠券作為代碼而不是您指定的名稱插入到消息中。 該代碼在「市場活動」otb資料模型中使用。
   ![](assets/deliv_coup_12.png)

1. 運行test以確認您分配給優惠券的名稱。 轉到 **[!UICONTROL Preview]** 頁籤 **[!UICONTROL Test personalization]**。 選擇test的收件人。

   ![](assets/deliv_coup_13.png)

   在test後，優惠券應顯示為已分配的名稱，而不是代碼。

   ![](assets/deliv_coup_14.png)

1. 在工具欄中，按一下 **[!UICONTROL Send]** （左上角），並選擇發送交貨的方式。

   ![](assets/deliv_coup_15.png)

1. 按一下 **[!UICONTROL Analyze]**。如果分析日誌確認有足夠的優惠券供所有收件人使用，請按一下 **[!UICONTROL Confirm delivery]** 寄出去。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>有關如何管理交貨的票證不足的說明，請參閱 [管理不足的優惠券](#managing-insufficient-coupons)

要確認交付成功，請執行以下操作：

1. 轉到 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**。
1. 按一下 **[!UICONTROL Deliveries]** 頁籤。

   ![](assets/deliv_coup_17.png)

   狀態顯示為 **[!UICONTROL Finished]** 成功交付。

>[!NOTE]
>
>預設情況下，贈券管理模組使用 **nms：收件人** 的子菜單。 [了解更多](../../configuration/using/about-data-model.md#default-recipient-table)。
>
>瞭解如何使用自定義收件人表 [此頁](../../configuration/using/about-custom-recipient-table.md)。

## 管理不足的優惠券 {#managing-insufficient-coupons}

如果優惠券數少於消息，則傳遞分析停止。 在這種情況下，您可以導入更多優惠券或限制郵件數。 如果要限制消息數，請按照以下說明操作。

1. 轉到電子郵件傳遞窗口。
1. 按一下&#x200B;**[!UICONTROL To]**。
1. 在 **[!UICONTROL Select target]**，轉到 **[!UICONTROL Exclusions]** 頁籤。

   ![](assets/deliv_coup_18.png)

1. 在排除設定部分，按一下 **[!UICONTROL Edit]**。
1. 輸入要發送的消息數 **[!UICONTROL Limit delivery to...messages]** 按一下 **[!UICONTROL Ok]**。 你可以發送。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>在管理有限數量的優惠券時，傳遞工作流允許您根據您的標準分解交貨。 如果您希望向選定的群體發送優惠券而不限制目標，則此選項是一個好選項。
