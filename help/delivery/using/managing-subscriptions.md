---
title: 管理訂閱
seo-title: 管理訂閱
description: 管理訂閱
seo-description: null
page-status-flag: never-activated
uuid: a2c526fa-3080-4dd5-9628-f0e7040f93cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 9a61fe74-f779-4f23-be25-3d9a8e95704a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 管理訂閱{#managing-subscriptions}

## 關於資訊服務 {#about-information-services}

一種資訊服務包括：

* 註冊和訂閱（選擇加入）、
* 取消註冊、自願取消訂閱（選擇退出）或自動取消訂閱（限時服務，例如試用優惠）、
* 訂閱和取消訂閱確認機制（含確認的簡單機制、雙重加入等）,
* 追蹤訂閱者歷史記錄。

作為標準功能，這些服務包括特定統計報告：訂閱者追蹤、忠誠度等級、取消訂閱趨勢等。

對於電子郵件，強制取消訂閱連結會自動產生，而整個選擇加入／選擇退出程式會完全自動化，並提供歷史追蹤以確保完全符合現行法規。

有三種服務訂閱／取消訂閱模式：

1. 手動
1. 透過匯入（僅限訂閱）,
1. 透過Web表格

>[!NOTE]
>
>本節將詳細說明建立雙重選擇加入訂閱表單 [的範例](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。

## 建立資訊服務 {#creating-an-information-service}

您可以建立並管理資訊服務的訂閱，其中包含相關的確認訊息或自動傳送給訂閱者。

若要存取資訊服務地圖，請前往宇宙， **[!UICONTROL Profiles and Targets]** 然後按一下連 **[!UICONTROL Services and Subscriptions]** 結。

![](assets/s_ncs_user_services_new.png)

要編輯現有服務，請按一下其名稱。 要建立服務，請按一下列 **[!UICONTROL Create]** 表上方的按鈕。

![](assets/s_ncs_user_services_add.png)

* 在欄位中輸入服務名稱， **[!UICONTROL Label]** 然後選擇傳送渠道：電子郵件、行動裝置、Facebook、Twitter或行動應用程式。

   >[!NOTE]
   >
   >Facebook和Twitter訂閱會在本節中詳 [細說明](../../social/using/about-social-marketing.md)。 行動應用程式訂閱在關於行動應 [用程式頻道中有詳細說明](../../delivery/using/about-mobile-app-channel.md)。

* 對於「電子郵件類型」服務，請選擇「 **傳送」模式**。 可能的模式包括：或 **[!UICONTROL Newsletter]** 者 **[!UICONTROL Viral]**。
* 您可以傳送 **訂閱或取消** 訂閱的確認訊息。 若要這麼做，請選取要用來從和欄位建立對應傳送的傳送范 **[!UICONTROL Subscription]** 本 **[!UICONTROL Unsubscription]** 。 這些範本必須配置有類型目 **[!UICONTROL Subscription]** 標映射，而不需定義目標。 請參閱關 [於電子郵件渠道](../../delivery/using/about-email-channel.md)。
* 依預設，訂閱是無限制的。 您可以取消選 **[!UICONTROL Unlimited]** 擇選項，以定義服務的有效期。 持續時間可以以天(**[!UICONTROL d]** )或月(**[!UICONTROL m]** )指定。

在儲存服務後，它就會新增至「服務與訂閱」清單：按一下其名稱以編輯它。 有幾個標籤可供使用。 此標 **[!UICONTROL Subscriptions]** 簽可讓您查看資訊服務（標籤）或訂閱／取消訂閱歷&#x200B;**[!UICONTROL Active subscriptions]** 史記錄（標籤）的訂閱者&#x200B;**[!UICONTROL History]** 清單。 您也可以從此標籤中新增和刪除訂閱者。 請參 [閱新增和刪除訂閱者](#adding-and-deleting-subscribers)。

![](assets/s_ncs_user_services_subscriptions.png)

此按 **[!UICONTROL Detail...]** 鈕可讓您查看所選收件者的訂閱屬性。

您可以修改收件者的訂閱屬性。

![](assets/s_ncs_user_services_modify.png)

在控制面板上，按一下標 **[!UICONTROL Reports]** 簽以追蹤訂閱：訂閱層級的變更、訂閱者總數等。 您可以從此標籤封存報表並查看歷史記錄。

## 添加和刪除訂閱者 {#adding-and-deleting-subscribers}

在資訊 **[!UICONTROL Subscriptions]** 服務的標籤中，按一下以 **[!UICONTROL Add]** 新增訂閱者。 您也可以在訂閱者清單上按一下滑鼠右鍵，然後選取 **[!UICONTROL Add]**。 選擇要預訂的配置檔案儲存在其中的資料夾，然後選擇要預訂的配置檔案並按一下 **[!UICONTROL OK]** 驗證。

若要刪除訂閱者，請選取訂閱者，然後按一下 **[!UICONTROL Delete]**。 您也可以在訂閱者清單上按一下滑鼠右鍵，然後選取 **[!UICONTROL Delete]**。

在這兩種情況下，如果服務已附加了取消訂閱的傳送範本，您都可以傳送確認訊息給相關的使用者(請參 [閱建立資訊服務](#creating-an-information-service))。 警告可讓您驗證或不驗證此傳送：

![](assets/s_ncs_user_services_update.png)

請參閱 [訂閱和取消訂閱機制](#subscription-and-unsubscription-mechanisms)。

## 為服務的訂閱者提供 {#delivering-to-the-subscribers-of-a-service}

要向資訊服務的訂戶提供資訊，您可以將有關資訊服務的訂戶定位為目標，如下例所示：

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>目標映射必須 **[!UICONTROL Subscriptions]**&#x200B;是。

選擇 **[!UICONTROL Subscribers of an information service]** 並按一下 **[!UICONTROL Next]**。

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

選擇目標資訊服務並按一下 **[!UICONTROL Finish]**。

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

此標 **[!UICONTROL Preview]** 簽可讓您檢視所選資訊服務的訂閱者清單。

## 訂閱與取消訂閱機制 {#subscription-and-unsubscription-mechanisms}

您可以設定訂閱和取消訂閱機制，以自動化程式和訂閱者管理。

>[!NOTE]
>
>您可以向新訂閱者傳送確認訊息。\
>此消息的內容通過或欄位在資訊服務配置中 **[!UICONTROL Subscription]** 定 **[!UICONTROL Unsubscription]** 義。
>
>確認訊息是透過這些欄位中指定的傳送範本來建立。 這些目標映射必須 **[!UICONTROL Subscriptions]**&#x200B;是。

![](assets/s_ncs_user_subscribe_confirmation.png)

### 將收件者訂閱至服務 {#subscribing-a-recipient-to-a-service}

要註冊資訊服務的收件者，您可以：

* 手動添加服務：要執行此操作，請從其配 **[!UICONTROL Subscriptions]** 置檔案的頁籤中單 **[!UICONTROL Add]** 擊並選擇相關資訊服務。

   有關詳細資訊，請參閱本節中有關配置檔案編輯 [的部分](../../platform/using/editing-a-profile.md)。

* 自動訂閱一組收件者至此服務。 收件者清單可來自使用滑鼠的篩選操作、群組、資料夾、匯入或直接選取。 若要訂閱這些收件者，請選取描述檔，然後按一下滑鼠右鍵。 選擇 **[!UICONTROL Actions > Subscribe selection to a service...]**，選擇相關服務，然後啟動操作。
* 匯入收件者，並自動將其訂閱至資訊服務。 要執行此操作，請在導入嚮導的最後一個步驟中選擇相關服務。

   如需詳細資訊，請參閱[本小節](../../platform/using/importing-data.md#import-wizard)。

* 使用Web表格，讓收件者可訂閱服務。

   如需詳細資訊，請參閱[本小節](../../web/using/about-web-applications.md)。

* 建立定位工作流程並使用方 **[!UICONTROL Subscription service]** 塊。

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   本節將詳述工作流程及其使 [用方法](../../workflow/using/about-workflows.md)。

### 從服務取消訂閱收件者 {#unsubscribing-a-recipient-from-a-service}

#### 手動取消訂閱 {#manual-unsubscribing}

依法，電子郵件傳送必須包含取消訂閱的連結。 收件者可以按一下此連結來更新其描述檔，並排除在未來傳送的目標之外。

預設的取消訂閱連結會透過傳送精靈中內容編輯器工具列的最後一個按鈕插入(請參閱關於個 [人化](../../delivery/using/about-personalization.md))。 當收件者按一下此連結時，描述檔會列入黑名單（選擇退出），這表示此收件者將不再受任何傳送動作的鎖定。

但是，收件者可以選擇取消訂閱服務，而不取消訂閱所有服務。 若要允許此動作，您可以使用Web表單(請參 [閱本節](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes))或插入個人化的取消訂閱連結(請參閱 [個人化區塊](../../delivery/using/personalization-blocks.md))。

您也可以從收件者描述檔手動取消訂閱收件者。 若要這麼做，請按一 **[!UICONTROL Subscriptions]** 下相關收件者的標籤，選取相關資訊服務，然後按一下 **[!UICONTROL Delete]**。

您最終可以透過相關資訊服務取消訂閱一或多個收件者。 若要這麼做，請按一下服 **[!UICONTROL Subscriptions]** 務的標籤，選取相關的收件者，然後按一下 **[!UICONTROL Delete]**。

#### 自動取消訂閱 {#automatic-unsubscription}

資訊服務的期限可以有限。 當有效期到期時，收件者會自動取消訂閱。 此期間在服務屬性 **[!UICONTROL Edit]** 的頁籤中指定。 它以數天表示。

![](assets/s_ncs_user_services_delay.png)

您也可以為人口設定取消訂閱的工作流程。 若要這麼做，請依照與訂閱工作流程相同的程式進行，但選取 **[!UICONTROL Unsubscription]** 選項。 請參 [閱訂閱收件者至服務](#subscribing-a-recipient-to-a-service)。

### 訂閱者追蹤 {#subscriber-tracking}

您可以使用控制面板上的連結來追蹤訂閱資訊服務 **[!UICONTROL Reports]** 的變更。

![](assets/s_ncs_user_services_report.png)
