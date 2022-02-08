---
product: campaign
title: 管理訂閱
description: 管理訂閱
feature: Subscriptions
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 2%

---

# 管理訂閱{#managing-subscriptions}

![](../../assets/common.svg)

## 關於資訊服務 {#about-information-services}

一種資訊服務，包括：

* 註冊和訂購（選擇加入）,
* 取消註冊、自願取消訂閱（選擇退出）或自動取消訂閱（限時服務，例如試用）,
* 訂閱和取消訂閱確認機制（具有確認的簡單機制、雙重選擇等）,
* 跟蹤訂戶歷史記錄。

作為標準功能，這些服務包括特定統計報告：訂戶跟蹤、忠誠度、未訂閱趨勢等。

對於電子郵件，強制取消訂閱連結會自動生成，整個選擇加入/退出過程將完全自動化，歷史記錄跟蹤可確保完全遵守現行法規。

有三種服務訂閱/取消訂閱模式：

1. 手
1. 通過導入（僅訂閱）,
1. 通過Web窗體

>[!NOTE]
>
>建立雙選擇加入訂閱表單的示例，詳見 [此部分](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。

## 建立資訊服務 {#creating-an-information-service}

您可以建立和管理資訊服務的訂閱，這些訂閱具有關聯的確認消息或自動將訂閱遞送給訂閱者。

要訪問資訊服務映射，請開啟 **[!UICONTROL Profiles and Targets]** ，然後按一下 **[!UICONTROL Services and Subscriptions]** 的子菜單。

![](assets/s_ncs_user_services_new.png)

要編輯現有服務，請按一下其名稱。 要建立服務，請按一下 **[!UICONTROL Create]** 按鈕。

![](assets/s_ncs_user_services_add.png)

* 在 **[!UICONTROL Label]** 欄位，然後選擇交貨渠道：電子郵件、移動、Facebook、Twitter或移動應用程式。

   >[!NOTE]
   >
   >Facebook和Twitter的訂閱詳情， [此部分](../../social/using/about-social-marketing.md)。 有關移動應用程式訂閱的詳細資訊，請參閱 [關於移動應用頻道](about-mobile-app-channel.md)。

* 對於電子郵件類型服務，選擇 **傳遞模式**。 可能的模式有： **[!UICONTROL Newsletter]** 或 **[!UICONTROL Viral]**。
* 您可以發送 **確認消息** 訂閱或取消訂閱。 為此，請選擇要用於從 **[!UICONTROL Subscription]** 和 **[!UICONTROL Unsubscription]** 的子菜單。 這些模板必須配置 **[!UICONTROL Subscription]** 類型目標映射，但沒有定義的目標。 請參閱節 [關於電子郵件通道](about-email-channel.md)。
* 預設情況下，訂閱是無限制的。 可以取消選擇 **[!UICONTROL Unlimited]** 選項來定義服務的有效期限。 持續時間可以以天為單位(**[!UICONTROL d]** )或月(**[!UICONTROL m]** )。

保存服務後，它將添加到「服務和訂閱」清單：按一下其名稱以編輯它。 有幾個頁籤可用。 的 **[!UICONTROL Subscriptions]** 頁籤，用於查看資訊服務的訂閱者清單(**[!UICONTROL Active subscriptions]** 頁籤)或訂閱/取消訂閱歷史記錄(**[!UICONTROL History]** )的正平方根。 您也可以從此頁籤添加和刪除訂閱者。 請參閱 [添加和刪除訂閱伺服器](#adding-and-deleting-subscribers)。

![](assets/s_ncs_user_services_subscriptions.png)

的 **[!UICONTROL Detail...]** 按鈕，查看選定收件人的訂閱屬性。

您可以修改收件人的訂閱屬性。

![](assets/s_ncs_user_services_modify.png)

在操控板上，按一下 **[!UICONTROL Reports]** 頁籤以跟蹤訂閱：訂閱級別的更改、訂閱者總數等。 您可以存檔報告並查看此頁籤中的歷史記錄。

## 添加和刪除訂閱伺服器 {#adding-and-deleting-subscribers}

從 **[!UICONTROL Subscriptions]** 頁籤 **[!UICONTROL Add]** 的子菜單。 也可以按一下右鍵訂閱者清單，然後選擇 **[!UICONTROL Add]**。 選擇儲存要訂閱的配置檔案的資料夾，然後選擇要訂閱的配置檔案，然後按一下 **[!UICONTROL OK]** 驗證。

要刪除訂閱者，請選擇訂閱者，然後按一下 **[!UICONTROL Delete]**。 也可以按一下右鍵訂戶清單並選擇 **[!UICONTROL Delete]**。

在這兩種情況下，如果已將取消訂閱的傳遞模板附加到服務，您都可以向相關用戶發送確認消息(請參閱 [建立資訊服務](#creating-an-information-service))。 警告允許您驗證或不驗證此傳遞：

![](assets/s_ncs_user_services_update.png)

請參閱 [訂閱和取消訂閱機制](#subscription-and-unsubscription-mechanisms)。

## 向服務的訂戶交付 {#delivering-to-the-subscribers-of-a-service}

要交付給資訊服務的訂戶，您可以將訂閱者定向到有關的資訊服務，如下例所示：

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>目標映射必須是 **[!UICONTROL Subscriptions]**。

選取 **[!UICONTROL Subscribers of an information service]** 並按一下 **[!UICONTROL Next]**。

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

選擇目標資訊服務並按一下 **[!UICONTROL Finish]**。

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

的 **[!UICONTROL Preview]** 頁籤中，您可以查看選定資訊服務的訂戶清單。

## 訂閱和取消訂閱機制 {#subscription-and-unsubscription-mechanisms}

您可以設定訂閱和取消訂閱機制以自動執行流程和訂閱者管理。

>[!NOTE]
>
>您可以向新訂戶發送確認消息。\
>此消息的內容通過 **[!UICONTROL Subscription]** 或 **[!UICONTROL Unsubscription]** 的子菜單。
>
>確認消息通過這些欄位中指定的傳遞模板建立。 這些目標映射必須是 **[!UICONTROL Subscriptions]**。

![](assets/s_ncs_user_subscribe_confirmation.png)

### 為收件人訂閱服務 {#subscribing-a-recipient-to-a-service}

要註冊資訊服務的收件人，您可以：

* 手動添加服務：來做這個， **[!UICONTROL Subscriptions]** 頁籤，按一下 **[!UICONTROL Add]** 選擇相關資訊服務。

   有關詳細資訊，請參閱中有關配置檔案編輯的部分 [此部分](../../platform/using/editing-a-profile.md)。

* 自動訂閱此服務的一組收件人。 收件人清單可以來自使用滑鼠的篩選操作、組、資料夾、導入或直接選擇。 要訂閱這些收件人，請選擇配置檔案並按一下右鍵。 選擇 **[!UICONTROL Actions > Subscribe selection to a service...]**，選擇相關服務，然後啟動操作。
* 導入收件人並自動將其訂閱到資訊服務。 為此，請在導入嚮導的最後一步中選擇相關服務。

   如需詳細資訊，請參閱[本章節](../../platform/using/executing-import-jobs.md)。

* 使用Web表單，以便收件人可以訂閱服務。

   如需詳細資訊，請參閱[本章節](../../web/using/about-web-applications.md)。

* 建立目標工作流並使用 **[!UICONTROL Subscription service]** 框。

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   工作流及其使用方法在 [此部分](../../workflow/using/about-workflows.md)。

### 從服務中取消訂閱收件人 {#unsubscribing-a-recipient-from-a-service}

#### 手動取消訂閱 {#manual-unsubscribing}

根據法律，電子郵件遞送必須包含未訂閱連結。 收件人可以按一下此連結來更新其配置檔案，並被排除在將來交貨的目標之外。

預設的取消訂閱連結是通過傳遞嚮導中提供的內容編輯器工具欄中的最後一個按鈕插入的（請參見） [關於個性化](about-personalization.md))。 當收件人按一下此連結時，配置檔案將添加到denylist（選擇退出），這意味著此收件人將不再是任何傳遞操作的目標。

但是，收件人可以選擇取消訂閱服務，而不取消訂閱所有服務。 要允許此操作，可以使用Web表單(請參閱 [此部分](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes))或插入個性化的取消訂閱連結(請參見 [個性化塊](personalization-blocks.md))。

您也可以從收件人配置檔案中手動取消訂閱收件人。 要執行此操作，請按一下 **[!UICONTROL Subscriptions]** 頁籤，選擇相關資訊服務，然後按一下 **[!UICONTROL Delete]**。

您最終可以通過相關的資訊服務取消訂閱一個或多個收件人。 要執行此操作，請按一下 **[!UICONTROL Subscriptions]** 頁籤，選擇相關收件人，然後按一下 **[!UICONTROL Delete]**。

#### 自動取消訂閱 {#automatic-unsubscription}

資訊服務可以具有有限的持續時間。 有效期過後，收件人將自動取消訂閱。 此期間在 **[!UICONTROL Edit]** 頁籤。 它以天數表示。

![](assets/s_ncs_user_services_delay.png)

您還可以為填充設定取消訂閱工作流。 為此，請按照與訂閱工作流相同的步驟操作，但選擇 **[!UICONTROL Unsubscription]** 的雙曲餘切值。 請參閱 [為收件人訂閱服務](#subscribing-a-recipient-to-a-service)。

### 訂戶跟蹤 {#subscriber-tracking}

您可以使用 **[!UICONTROL Reports]** 的子菜單。

![](assets/s_ncs_user_services_report.png)
