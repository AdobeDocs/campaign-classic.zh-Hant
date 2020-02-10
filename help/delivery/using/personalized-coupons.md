---
title: 個人化優惠券
seo-title: 個人化優惠券
description: 個人化優惠券
seo-description: null
page-status-flag: never-activated
uuid: c840e2de-f0ef-478b-af9f-82e1b6534933
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: f324afa5-304c-470e-a592-290f76a11ccb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 個人化優惠券{#personalized-coupons}

將抵用券加入傳送，可讓收件者享有更優惠的產品與服務價值。 您可以使用「促銷活動抵用券」模組來建立一組抵用券，您預期這些抵用券會新增至即將推出的行銷選件。 當您準備好要建立傳送時，請指派適用的抵用券。 由於抵用券在選擇期間有效，所指派的抵用券會唯一連結至其傳送訊息。 此外，促銷活動會確認在傳送訊息之前，有足夠的抵用券可容納訊息數量。

>[!NOTE]
>
>抵用券管理是必須安裝的套件。 若要確認您有「抵用券」管理，請勾選 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>抵用券資料可以使用CSV和XML格式匯入和匯出。 有關導入和導出的詳細資訊，請參 [閱本節](../../platform/using/generic-imports-and-exports.md)。

## 建立抵用券 {#creating-a-coupon}

抵用券模組提供您兩個選項來建立抵用券：

* **匿名**:特定收件者或收件者清單的一般抵用券。
* **個人**:特定收件者的個人化優惠券。

在遵循下列步驟之前，請確定您知道要建立的抵用券類型。

1. 在「促銷活動」樹狀結構中，前往 **[!UICONTROL Resources > Campaign management > Coupons]**。

   ![](assets/deliv_coup_01.png)

1. Click the **[!UICONTROL New]** button.
1. 在欄位中輸入抵用券的名 **[!UICONTROL Label]** 稱。 已自動在中輸入唯一代碼 **[!UICONTROL Coupon code]**。 您可以保留代碼或輸入新代碼。

   ![](assets/deliv_coup_02.png)

1. 選擇 **[!UICONTROL Start date]** 並 **[!UICONTROL End date]** 設定抵用券有效的期間。
1. 在中， **[!UICONTROL Coupon type]**&#x200B;選擇「匿名」或「個人」。

   **[!UICONTROL Anonymous coupons]** :匿名抵用券對所有收件者都相同。 確認已在「抵用券類型」功能表中選 **取「匿名者** 」，然後按 **一下「儲存** 」以產生抵用券。

   **[!UICONTROL Individual coupons]** :使用附加的抵用券代碼可以進一步個人化單個抵用券。 例如，在運動器材商店建立銷售的個別抵用券。 然而，受獎者名單很長，他們對單項運動的熱情也不同。 您可以根據運動（例如足球、足球、棒球等）為個別抵用券新增程式碼名稱並將每個程式碼傳送給適用的收件者。

   1. 選擇「個人」時，新的標籤「抵用券」會出現在左下角。 轉到頁籤 **[!UICONTROL Coupons]** 並按一下 **[!UICONTROL Add]**。
   1. 在彈出式視窗提示時，輸入個別抵用券的唯一代碼。
   1. 按一 **[!UICONTROL Save]** 下以產生抵用券。
   如需「抵用券」標籤的詳細資訊，請參閱「設 [定個別抵用券」](#configuring-individual-coupons)。

   >[!NOTE]
   >
   >您可大量匯入個別抵用券。 有關導入和導出的詳細資訊，請參 [閱本節](../../platform/using/generic-imports-and-exports.md)。

### 設定個別抵用券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

「抵用券」標籤僅適用於「個別」抵用券。 在抵用券與傳送相關聯後，「抵用券」標籤會提供下列詳細資訊：

* **[!UICONTROL Status]** :抵用券可用性。
* **[!UICONTROL Redeemed on]** :抵用券的兌換日期。
* **[!UICONTROL Channel]** :用來傳送抵用券的渠道。
* **[!UICONTROL Address]** :收件者的電子郵件地址。

自動 **[!UICONTROL status]**&#x200B;完成、 **[!UICONTROL channel]**&#x200B;和 **[!UICONTROL address]** 的值。 不過，促銷活動 **[!UICONTROL redeemed on]** 不會復原值。 您可匯入包含抵用券兌換詳細資訊的檔案，以完成這些作業。

## 將抵用券插入電子郵件傳送 {#inserting-a-coupon-into-an-email-delivery}

在以下範例中，傳送是從首頁建立。 如需如何建立傳送的詳細指示，請參閱 [本節](../../delivery/using/about-email-channel.md)。 您也可以在工作流程中將抵用券新增至傳送。

1. 前往並 **[!UICONTROL Campaigns]** 選擇 **[!UICONTROL Deliveries]**。
1. 按一下 **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. 在中輸入名稱 **[!UICONTROL Label]** 並按一下 **[!UICONTROL Continue]**。
1. 按一 **[!UICONTROL To]** 下以新增收件者。
1. 按一 **[!UICONTROL Add]** 下以選擇傳送的收件者。 在您選取收件者後，按一下 **[!UICONTROL Ok]** 即可返回傳送。

   ![](assets/deliv_coup_05.png)

1. 輸入主旨並新增內容至訊息。

   ![](assets/deliv_coup_06.png)

1. 在工具列中，按一 **[!UICONTROL Properties]** 下並選擇標 **[!UICONTROL Advanced]** 簽。
1. 按一下的資料夾圖 **[!UICONTROL Coupon management]**&#x200B;標。

   ![](assets/deliv_coup_07.png)

1. 選擇抵用券，然後按一下 **[!UICONTROL Ok]**。 再按一 **[!UICONTROL Ok]** 下。

   ![](assets/deliv_coup_08.png)

1. 按一下訊息，以選擇您要放置抵用券的位置。

   ![](assets/deliv_coup_09.png)

1. 按一下個人化圖示，根據抵用券類型選擇下列其中一項：

   * 匿名抵用券： **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 個別抵用券： **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      抵用券會以程式碼的形式插入訊息中，而非您指派的名稱。 代碼用於促銷活動標準資料模型中。
   ![](assets/deliv_coup_12.png)

1. 執行測試以確認您指派給抵用券的名稱。 轉到頁籤 **[!UICONTROL Preview]** 並按一下 **[!UICONTROL Test personalization]**。 選擇測試的收件者。

   ![](assets/deliv_coup_13.png)

   在測試後，抵用券應顯示為已指派的名稱，而非代碼。

   ![](assets/deliv_coup_14.png)

1. 在工具列中，按一 **[!UICONTROL Send]** 下（左上方），然後選擇傳送方式。

   ![](assets/deliv_coup_15.png)

1. 按一下 **[!UICONTROL Analyze]**. 如果分析記錄確認所有收件者都有足夠的抵用券，請按一 **[!UICONTROL Confirm delivery]** 下以傳送。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>如需如何管理傳送之抵用券不足的指示，請參閱管理抵 [用券不足](#managing-insufficient-coupons)

若要確認傳送成功：

1. 前往 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**。
1. 按一下標 **[!UICONTROL Deliveries]** 簽。

   ![](assets/deliv_coup_17.png)

   狀態會顯示為 **[!UICONTROL Finished]** 成功傳送。

>[!NOTE]
>
>預設情況下，抵用券管理模組使用 **nms:recipient** 表。 有關如何使用其他表的說明，請參見編 [輯結構](../../configuration/using/data-schemas.md)。

## 管理抵用券不足 {#managing-insufficient-coupons}

如果抵用券數少於訊息數，則傳送分析會停止。 在這種情況下，您可以匯入更多抵用券或限制訊息數。 如果要限制訊息數量，請依照下列指示進行。

1. 前往電子郵件傳送視窗。
1. 按一下 **[!UICONTROL To]**.
1. 在 **[!UICONTROL Select target]**&#x200B;中，轉到頁籤 **[!UICONTROL Exclusions]** 。

   ![](assets/deliv_coup_18.png)

1. 在排除設定區段中，按一下 **[!UICONTROL Edit]**。
1. 輸入要傳入的訊息數，然後按 **[!UICONTROL Limit delivery to...messages]** 一下 **[!UICONTROL Ok]**。 您可以傳送傳送。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>在管理有限數量的抵用券時，傳送工作流程可讓您根據您的准則來分割傳送。 如果您想要將抵用券傳送給選取的人口群，而不限制目標，這是個不錯的選項。
