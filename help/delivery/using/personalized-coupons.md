---
product: campaign
title: 個人化優惠券
description: 個人化優惠券
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 91dec9adb177aedc4a82879011371b54886166be
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 1%

---

# 個人化優惠券{#personalized-coupons}

![](../../assets/v7-only.svg)

將抵用券加到您的傳遞，可讓收件者獲得更高的產品和服務價值。 您可以使用「促銷活動抵用券」模組，建立一組您預期要新增至即將推出之行銷活動的抵用券。 當您準備好建立傳遞時，請指派適用的抵用券。 由於抵用券對於選取的期間有效，所指派的抵用券會唯一連結至其傳送訊息。 此外，Campaign會確認在傳送訊息之前，有足夠的抵用券數量。

>[!NOTE]
>
>抵用券管理是必須安裝的套件。 若要確認您有「抵用券」管理，請檢查&#x200B;**[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>抵用券資料可以使用CSV和XML格式匯入和匯出。 有關匯入和匯出的詳細資訊，請參閱[此區段](../../platform/using/get-started-data-import-export.md)。

## 建立抵用券 {#creating-a-coupon}

「抵用券」模組提供建立抵用券時的兩個選項：

* **匿名**:特定收件者或收件者清單的一般抵用券。
* **個人**:特定收件者的個人化抵用券。

執行下列步驟之前，請確定您知道要建立的抵用券類型。

1. 在促銷活動樹狀結構中，前往&#x200B;**[!UICONTROL Resources > Campaign management > Coupons]**。

   ![](assets/deliv_coup_01.png)

1. 按一下 **[!UICONTROL New]** 按鈕。
1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入抵用券名稱。 已在&#x200B;**[!UICONTROL Coupon code]**&#x200B;中自動輸入唯一代碼。 您可以保留代碼或輸入新代碼。

   ![](assets/deliv_coup_02.png)

1. 選擇&#x200B;**[!UICONTROL Start date]**&#x200B;和&#x200B;**[!UICONTROL End date]**&#x200B;以設定抵用券有效的期間。
1. 在&#x200B;**[!UICONTROL Coupon type]**&#x200B;中，選擇「匿名」或「個人」。

   **[!UICONTROL Anonymous coupons]** :匿名抵用券對所有收件者都相同。確認已在&#x200B;**抵用券類型**&#x200B;功能表中選取匿名，然後按一下&#x200B;**儲存**&#x200B;以產生抵用券。

   **[!UICONTROL Individual coupons]** :個別抵用券可透過其他抵用券代碼進一步個人化。例如，在運動器材商店為銷售建立個別抵用券。 然而，收件者名單很長，他們對單項運動的熱情並不相同。 您可以根據運動（例如足球、足球、棒球等），為個別抵用券新增程式碼名稱 並將每個程式碼傳送給適用的收件者。

   1. 選擇「個人」時，左下方會顯示新的分頁「抵用券」。 前往&#x200B;**[!UICONTROL Coupons]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Add]**。
   1. 在彈出式視窗提示時，輸入個別抵用券的唯一代碼。
   1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;產生抵用券。

   如需「抵用券」標籤的詳細資訊，請參閱[設定個別抵用券](#configuring-individual-coupons)。

   >[!NOTE]
   >
   >個別抵用券可以大量匯入。 有關匯入和匯出的詳細資訊，請參閱[此區段](../../platform/using/get-started-data-import-export.md)。

### 設定個別抵用券 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

「抵用券」索引標籤只能搭配「個別抵用券」使用。 將抵用券與傳送建立關聯後，「抵用券」索引標籤會提供下列詳細資料：

* **[!UICONTROL Status]** :抵用券可用性。
* **[!UICONTROL Redeemed on]** :抵用券的兌換日期。
* **[!UICONTROL Channel]** :用來傳送抵用券的管道。
* **[!UICONTROL Address]** :收件者的電子郵件地址。

會自動完成&#x200B;**[!UICONTROL status]**、**[!UICONTROL channel]**&#x200B;和&#x200B;**[!UICONTROL address]**&#x200B;的值。 不過，促銷活動不會復原&#x200B;**[!UICONTROL redeemed on]**&#x200B;的值。 您可以匯入包含抵用券贖回詳細資訊的檔案，以完成這些操作。

## 將抵用券插入電子郵件傳送 {#inserting-a-coupon-into-an-email-delivery}

在以下範例中，傳遞是從首頁建立。 如需如何建立傳送的詳細指示，請參閱[本區段](about-email-channel.md)。 您也可以在工作流程中將抵用券新增至傳送。

1. 轉至&#x200B;**[!UICONTROL Campaigns]**，然後選擇&#x200B;**[!UICONTROL Deliveries]**。
1. 按一下&#x200B;**[!UICONTROL Create]**。

   ![](assets/deliv_coup_04.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;中輸入名稱，然後按一下&#x200B;**[!UICONTROL Continue]**。
1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;以新增收件者。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選擇傳送的收件者。 選取收件者後，按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以返回傳遞。

   ![](assets/deliv_coup_05.png)

1. 輸入主旨並新增內容至訊息。

   ![](assets/deliv_coup_06.png)

1. 在工具欄中，按一下&#x200B;**[!UICONTROL Properties]**&#x200B;並選擇&#x200B;**[!UICONTROL Advanced]**&#x200B;頁簽。
1. 按一下&#x200B;**[!UICONTROL Coupon management]**&#x200B;的資料夾圖示。

   ![](assets/deliv_coup_07.png)

1. 選擇抵用券並按一下&#x200B;**[!UICONTROL Ok]**。 再次按一下&#x200B;**[!UICONTROL Ok]**。

   ![](assets/deliv_coup_08.png)

1. 按一下訊息，以選擇您要放置抵用券的位置。

   ![](assets/deliv_coup_09.png)

1. 按一下個人化圖示，根據抵用券類型選擇下列其中一項：

   * 匿名抵用券：**[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 個別抵用券：**[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      抵用券會以程式碼的形式插入訊息中，而非您指派的名稱。 程式碼用於Campaign Ootb資料模型中。
   ![](assets/deliv_coup_12.png)

1. 執行測試以確認您指派給抵用券的名稱。 前往&#x200B;**[!UICONTROL Preview]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Test personalization]**。 選擇測試的收件者。

   ![](assets/deliv_coup_13.png)

   測試後，抵用券應會顯示為指派的名稱，而非代碼。

   ![](assets/deliv_coup_14.png)

1. 在工具列中，按一下&#x200B;**[!UICONTROL Send]**（左上方）並選擇要如何傳送傳遞。

   ![](assets/deliv_coup_15.png)

1. 按一下 **[!UICONTROL Analyze]**。如果分析日誌確認所有收件者都有足夠的抵用券，請按一下&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;進行傳送。

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>如需如何管理傳遞之抵用券不足的指示，請參閱[管理抵用券不足](#managing-insufficient-coupons)

若要確認傳送成功：

1. 前往&#x200B;**[!UICONTROL Explorer > Resources > Campaign management > Coupons]**。
1. 按一下&#x200B;**[!UICONTROL Deliveries]**&#x200B;標籤。

   ![](assets/deliv_coup_17.png)

   成功傳送時，狀態會讀為&#x200B;**[!UICONTROL Finished]**。

>[!NOTE]
>
>依預設，抵用券管理模組使用&#x200B;**nms:recipient**&#x200B;表格。 有關如何使用其他表的說明，請參閱[編輯結構](../../configuration/using/data-schemas.md)。

## 管理抵用券不足 {#managing-insufficient-coupons}

如果抵用券數少於訊息數，傳遞分析就會停止。 在這種情況下，您可以匯入更多抵用券或限制訊息的數量。 如果要限制訊息數量，請依照下列指示操作。

1. 前往電子郵件傳送視窗。
1. 按一下&#x200B;**[!UICONTROL To]**。
1. 在&#x200B;**[!UICONTROL Select target]**&#x200B;中，前往&#x200B;**[!UICONTROL Exclusions]**&#x200B;標籤。

   ![](assets/deliv_coup_18.png)

1. 在排除設定區段中，按一下&#x200B;**[!UICONTROL Edit]**。
1. 輸入要在&#x200B;**[!UICONTROL Limit delivery to...messages]**&#x200B;中發送的消息數，然後按一下&#x200B;**[!UICONTROL Ok]**。 您可以傳送傳遞。

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>管理有限數量的抵用券時，傳遞工作流程可讓您根據條件來分割傳送。 如果您想要將抵用券傳送至選取的人口族群，而不限制目標，這個選項很合適。
