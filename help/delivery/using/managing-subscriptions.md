---
product: campaign
title: 管理訂閱
description: 管理訂閱
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Subscriptions
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 2%

---

# 管理訂閱{#managing-subscriptions}



## 關於資訊服務 {#about-information-services}

一種資訊服務包括：

* 註冊和訂閱（選擇加入）,
* 取消註冊、自願取消訂閱（選擇退出）或自動取消訂閱（限時服務，例如試用優惠方案）、
* 訂閱和取消訂閱確認機制（具有確認的簡單機制、雙重加入等）,
* 訂閱者歷史記錄的追蹤。

作為標準功能，這些服務包含特定統計報表：訂閱者追蹤、忠誠度、取消訂閱趨勢等。

對於電子郵件，強制取消訂閱連結會自動產生，而整個選擇加入/退出程式都會完全自動化，並提供歷史記錄追蹤功能，確保完全符合現行法規。

有三種服務訂閱/取消訂閱模式：

1. 手動
1. 通過導入（僅訂閱）,
1. 通過網路表單

>[!NOTE]
>
>如需使用雙重加入建立訂閱表單的範例，請參閱 [本節](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## 建立資訊服務 {#creating-an-information-service}

您可以建立和管理資訊服務的訂閱，這些訂閱包含關聯的確認訊息或自動傳送給訂閱者。

要訪問資訊服務映射，請開啟 **[!UICONTROL Profiles and Targets]** ，然後按一下 **[!UICONTROL Services and Subscriptions]** 連結。

![](assets/s_ncs_user_services_new.png)

若要編輯現有服務，請按一下其名稱。 若要建立服務，請按一下 **[!UICONTROL Create]** 按鈕。

![](assets/s_ncs_user_services_add.png)

* 在 **[!UICONTROL Label]** 欄位並選取傳送通道：電子郵件、行動裝置、Facebook、Twitter或行動應用程式。

   >[!NOTE]
   >
   >Facebook和Twitter訂閱詳情請參閱 [本節](../../social/using/about-social-marketing.md). 如需行動應用程式訂閱的詳細資訊，請參閱 [關於行動應用程式頻道](about-mobile-app-channel.md).

* 對於電子郵件類型服務，請選取 **傳送模式**. 可能的模式包括： **[!UICONTROL Newsletter]** 或 **[!UICONTROL Viral]**.
* 您可以傳送 **確認訊息** 訂閱或取消訂閱。 若要這麼做，請選取要用來從 **[!UICONTROL Subscription]** 和 **[!UICONTROL Unsubscription]** 欄位。 這些範本必須以 **[!UICONTROL Subscription]** 類型目標對應，沒有定義的目標。 請參閱區段 [關於電子郵件通道](about-email-channel.md).
* 預設為無限制訂閱。 您可以取消選取 **[!UICONTROL Unlimited]** 選項來定義服務的有效期間。 可以以天為單位指定持續時間(**[!UICONTROL d]** )或月(**[!UICONTROL m]** )。

服務儲存後會新增至「服務與訂閱」清單：按一下其名稱即可編輯。 有數個索引標籤可供使用。 此 **[!UICONTROL Subscriptions]** 索引標籤可讓您查看資訊服務的訂閱者清單(**[!UICONTROL Active subscriptions]** 頁簽)或訂閱/取消訂閱歷史記錄(**[!UICONTROL History]** 標籤)。 您也可以從此索引標籤新增和刪除訂閱者。 請參閱 [新增和刪除訂閱者](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

此 **[!UICONTROL Detail...]** 按鈕可讓您查看所選收件者的訂閱屬性。

您可以修改收件者的訂閱屬性。

![](assets/s_ncs_user_services_modify.png)

在控制面板上，按一下 **[!UICONTROL Reports]** 索引標籤來追蹤訂閱：訂閱層級、訂閱者總數等的變更。 您可以從此索引標籤封存報表和查看歷史記錄。

## 新增和刪除訂閱者 {#adding-and-deleting-subscribers}

從 **[!UICONTROL Subscriptions]** 資訊服務的標籤，按一下 **[!UICONTROL Add]** 來新增訂閱者。 您也可以以滑鼠右鍵按一下訂閱者清單，然後選取 **[!UICONTROL Add]**. 選取要訂閱的設定檔儲存在其中的資料夾，然後選取要訂閱的設定檔，然後按一下 **[!UICONTROL OK]** 以驗證。

若要刪除訂閱者，請選取訂閱者並按一下 **[!UICONTROL Delete]**. 也可以按一下右鍵訂閱者清單並選擇 **[!UICONTROL Delete]**.

在這兩種情況下，如果已將取消訂閱的傳送範本附加至服務，您都可以傳送確認訊息給相關使用者(請參閱 [建立資訊服務](#creating-an-information-service))。 警告可讓您驗證或不驗證此傳送：

![](assets/s_ncs_user_services_update.png)

請參閱 [訂閱和取消訂閱機制](#subscription-and-unsubscription-mechanisms).

## 傳送給服務的訂閱者 {#delivering-to-the-subscribers-of-a-service}

若要傳送給資訊服務的訂閱者，您可以將目標定位為相關資訊服務的訂閱者，如下列範例所示：

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>目標對應必須是 **[!UICONTROL Subscriptions]**.

選取 **[!UICONTROL Subscribers of an information service]** 並按一下 **[!UICONTROL Next]**。

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

選擇目標資訊服務，然後按一下 **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

此 **[!UICONTROL Preview]** 索引標籤可讓您檢視所選資訊服務的訂閱者清單。

## 訂閱和取消訂閱機制 {#subscription-and-unsubscription-mechanisms}

您可以設定訂閱和取消訂閱機制，以自動化流程和訂閱者管理。

>[!NOTE]
>
>您可以向新訂閱者傳送確認訊息。\
>此訊息的內容會透過 **[!UICONTROL Subscription]** 或 **[!UICONTROL Unsubscription]** 欄位。
>
>確認訊息會透過這些欄位中指定的傳送範本建立。 這些目標映射必須是 **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### 將收件者訂閱服務 {#subscribing-a-recipient-to-a-service}

要註冊資訊服務的收件者，您可以：

* 手動新增服務：要做到這一點，從 **[!UICONTROL Subscriptions]** 標籤，按一下 **[!UICONTROL Add]** 選擇相關資訊服務。

   如需詳細資訊，請參閱 [本節](../../platform/using/editing-a-profile.md).

* 自動訂閱此服務的一組收件者。 收件者清單可來自篩選操作、群組、資料夾、匯入，或使用滑鼠直接選取。 若要訂閱這些收件者，請選取設定檔並按一下滑鼠右鍵。 選擇 **[!UICONTROL Actions > Subscribe selection to a service...]**，選擇相關服務，然後啟動操作。
* 將收件者自動匯入並訂閱至資訊服務。 要執行此操作，請選取匯入精靈最後一個步驟中相關的服務。

   如需詳細資訊，請參閱[本章節](../../platform/using/executing-import-jobs.md)。

* 使用Web表單，讓收件者可以訂閱服務。

   如需詳細資訊，請參閱[本章節](../../web/using/about-web-applications.md)。

* 建立目標工作流程並使用 **[!UICONTROL Subscription service]** 框。

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   工作流程及其使用方式於 [本節](../../workflow/using/about-workflows.md).

### 從服務取消訂閱收件者 {#unsubscribing-a-recipient-from-a-service}

#### 手動取消訂閱 {#manual-unsubscribing}

依法，電子郵件傳送必須包含取消訂閱連結。 收件者可以按一下此連結以更新其設定檔，並排除在未來傳送的目標之外。

預設取消訂閱連結會透過傳送精靈中內容編輯器工具列中的最後一個按鈕插入(請參閱 [關於個人化](about-personalization.md))。 收件者按一下此連結時，設定檔會新增至封鎖清單（選擇退出），這表示此收件者將不再被任何傳送動作鎖定。

但是，收件者可以選擇取消訂閱服務，而不會取消訂閱所有服務。 若要允許，您可以使用網路表單(請參閱 [本節](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes))或插入個人化的取消訂閱連結(請參閱 [個人化區塊](personalization-blocks.md))。

您也可以從收件者設定檔手動取消訂閱收件者。 若要這麼做，請按一下 **[!UICONTROL Subscriptions]** 頁簽，選擇相關資訊服務，然後按一下 **[!UICONTROL Delete]**.

您最後可以透過相關資訊服務取消訂閱一或多個收件者。 若要這麼做，請按一下 **[!UICONTROL Subscriptions]** 頁簽，選擇相關的收件人，然後按一下 **[!UICONTROL Delete]**.

#### 自動取消訂閱 {#automatic-unsubscription}

資訊服務的持續時間可能有限。 有效期屆滿時，收件者會自動取消訂閱。 此期間在 **[!UICONTROL Edit]** 頁簽。 以天表示。

![](assets/s_ncs_user_services_delay.png)

您也可以為母體設定取消訂閱的工作流程。 要執行此操作，請遵循與訂閱工作流程相同的程式，但選取 **[!UICONTROL Unsubscription]** 選項。 請參閱 [將收件者訂閱服務](#subscribing-a-recipient-to-a-service).

### 訂閱者追蹤 {#subscriber-tracking}

您可以使用 **[!UICONTROL Reports]** 連結。

![](assets/s_ncs_user_services_report.png)
