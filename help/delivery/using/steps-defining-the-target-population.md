---
product: campaign
title: 定義目標母體
description: 了解如何定義目標母體
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences, Proofs
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1598'
ht-degree: 3%

---

# 定義目標母體 {#defining-the-target-population}



對於每個傳送，您可以定義數種目標母體類型：

* **主要受眾**:接收訊息的設定檔。 [了解更多](steps-defining-the-target-population.md#selecting-the-main-target)
* **校樣**:校樣訊息的收件者，涉及驗證週期。 [了解更多](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **種子地址**:未達到傳送目標但將收到傳送的收件者（僅限行銷活動的內容中）。 [了解更多](about-seed-addresses.md)
* **控制組**:不會收到傳送的母體，用於追蹤行為和促銷活動影響（僅限行銷促銷活動的內容）。 [了解更多](../../campaign/using/marketing-campaign-target.md#defining-a-control-group)。

## 選取傳送的主要收件者 {#selecting-the-main-target}

在大多數情況下，主要目標會從Adobe Campaign資料庫（預設模式）中擷取。 不過，收件者也可儲存在外部檔案中。 在[本章節](steps-defining-the-target-population.md#selecting-external-recipients)了解更多資訊。

若要選取傳送的收件者，請遵循下列步驟：

1. 在傳送編輯器中，選取 **[!UICONTROL To]**.
1. 如果收件者儲存在資料庫中，請選擇第一個選項。

   ![](assets/s_ncs_user_wizard_email02a.png)

1. 在 **[!UICONTROL Target mapping]** 下拉式清單。 Adobe Campaign預設目標對應為 **[!UICONTROL Recipients]**，根據 **nms:recipient** 綱要。

   其他目標對應可供使用，有些可與您的特定設定相關。 有關目標映射的詳細資訊，請參閱 [選擇目標映射](selecting-a-target-mapping.md).

1. 按一下 **[!UICONTROL Add]** 按鈕來定義限制篩選器。

   然後，您可以選取要套用的篩選類型：

   ![](assets/s_ncs_user_wizard_email02b.png)

   您可以使用資料庫中定義的目標類型來選取收件者。 若要使用目標類型，請選取它，然後按一下 **[!UICONTROL Next]**. 對於每個目標，您可以按一下 **[!UICONTROL Preview]** 標籤。 對於特定類型的目標， **[!UICONTROL Refine target]** 按鈕可讓您結合數個鎖定目標條件。

   預設提供下列目標類型：

   * **[!UICONTROL Filtering conditions]** :此選項可讓您定義查詢並顯示結果。 定義查詢的方法如 [本節](../../platform/using/creating-filters.md#creating-an-advanced-filter).
   * **[!UICONTROL Subscribers of an information service]** :此選項可讓您選取電子報，收件者必須訂閱該電子報，才能由建立的傳送鎖定目標。

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** :此選項可讓您將現有傳送的收件者定義為定位准則。 之後，您必須在清單中選取傳送：

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** :此選項可讓您選取傳送資料夾，並鎖定該資料夾中傳送的收件者。

      ![](assets/s_ncs_user_wizard_email02e.png)

      您可以從下拉式清單中選取，以篩選收件者的行為：

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >此 **[!UICONTROL Include sub-folders]** 選項也可讓您定位所選節點下方樹狀結構中資料夾中包含的傳送。

   * **[!UICONTROL Recipients included in a folder]** :此選項可讓您定位樹的特定資料夾中包含的配置檔案。
   * **[!UICONTROL A recipient]** :此選項可讓您從資料庫的設定檔中選取特定收件者。
   * **[!UICONTROL A list of recipients]** :此選項可讓您鎖定收件者清單。 清單列於 [本節](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** :此選項可讓您存取預先設定的篩選器，以將其用作資料庫中設定檔的篩選條件。 預配置的篩選器顯示在 [本節](../../platform/using/creating-filters.md#saving-a-filter).
   * 選項 **[!UICONTROL Exclude recipients corresponding to this segment]** 可讓您鎖定不符合定義之目標條件的收件者。 若要使用此選項，請選取適當的方塊，然後依照先前的定義套用目標，以排除產生的設定檔。

      ![](assets/s_ncs_user_wizard_email02g.png)

1. 在 **[!UICONTROL Label]** 欄位。 依預設，標籤將是第一個定位准則的標籤。 對於組合，最好使用明確的名稱。
1. 按一下 **[!UICONTROL Finish]** 來驗證已設定的鎖定目標。

   定義的定位條件會匯總在主要目標設定標籤的中央區段。 按一下條件可查看其內容（配置和預覽）。 若要刪除條件，請按一下標籤後面的交叉點。

   ![](assets/s_ncs_user_wizard_email02h.png)

### 選取外部收件者 {#selecting-external-recipients}

您可以對未儲存在資料庫中，但儲存在外部檔案的收件者啟動傳遞。 例如，我們會在此傳送傳遞給從文字檔案匯入的收件者。

操作步驟：

1. 按一下 **[!UICONTROL To]** 連結以選取傳遞的收件者。
1. 選取 **[!UICONTROL Defined in an external file]** 選項。

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 依預設，收件者會匯入資料庫中。 您必須選取 **[!UICONTROL Target mapping]**. 有關目標映射的詳細資訊，請參閱 [選擇目標映射](selecting-a-target-mapping.md)

   您也可以選擇 **[!UICONTROL Do not import the recipients into the database]**.

1. 匯入收件者時，按一下 **[!UICONTROL File format definition...]** 連結以選取和設定外部檔案。

   如需資料匯入的詳細資訊，請參閱 [本節](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. 按一下 **[!UICONTROL Finish]** 並將您的傳送設定為標準傳送。

>[!CAUTION]
>
>定義電子郵件傳送的郵件內容時，請勿包含鏡像頁面的連結；無法在此傳送模式中產生。

### 定義排除設定 {#define-exclusion-settings}

地址錯誤和質量評等由服務提供程式(IAP)提供。 在執行傳送動作後，此資訊會在收件者設定檔中自動更新，並包含服務提供者傳回的檔案。 可在設定檔中以唯讀方式檢視。

您可以選擇排除已達到特定數量連續錯誤的地址，或其質量等級低於此窗口中指定的閾值的地址。 您也可以選擇是否授權未傳回任何資料的未限定地址。

>[!NOTE]
>
>如果直接郵件傳送中有兩個收件者具有相同的名字、姓氏、郵遞區號和城市，將會發生雙重錯誤，且不會將重複項目列入考量。

此 **[!UICONTROL Exclusions]** 標籤來限制訊息數。

>[!NOTE]
>
>建議使用預設參數，但您可以視需要調整設定。 不過，這些選項只能由專家使用者變更，以避免使用錯誤和錯誤。

按一下 **[!UICONTROL Edit...]** 連結以修改預設設定。

![](assets/s_ncs_user_wizard_email02i.png)

可以使用以下選項：

* **[!UICONTROL Exclude duplicate addresses during delivery]**. 此選項預設為作用中：可讓您在傳送期間消除重複的電子郵件地址。 所套用的策略可能會因使用Adobe Campaign的方式和資料庫中的資料類型而異。

   可為每個傳送範本設定選項的預設值。

   例如：

   * 傳遞電子報或電子檔案。 如果資料沒有原生重複項目，在某些情況下不會排除重複項目。 訂閱相同電子郵件地址的夫婦可能會收到兩個特定的個人化電子郵件訊息：按姓名向每個人發送一個。 在此情況下，可取消選取此選項。
   * 行銷活動的傳送：重複排除是避免傳送過多訊息給相同收件者的必要條件。 在此情況下，可以選取此選項。

      如果您取消選取此選項，您可以存取其他選項： **[!UICONTROL Keep duplicate records (same identifier)]**. 它可讓您授權多個傳送給符合數個鎖定目標的收件者。

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** ，亦即電子郵件地址已列入封鎖清單（「選擇退出」）的收件者。 必須繼續選擇這一選項，以遵守電子營銷的職業道德和電子商務法。
* **[!UICONTROL Exclude quarantined recipients]**. 此選項可讓您從目標中排除任何具有未回應之位址的設定檔。 強烈建議保留此選項。

   >[!NOTE]
   >
   >有關隔離管理的詳細資訊，請參閱 [了解隔離管理](understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** 指定數量的訊息。 此選項可讓您輸入要傳送的訊息數量上限。 如果目標的內容超過所指示的消息數，則隨機選擇被應用到目標。

### 縮小目標人口的大小 {#reducing-the-size-of-the-target-population}

您可以縮小目標母體的大小。 若要這麼做，請指定要在 **[!UICONTROL Requested quantity]** 欄位。

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 選取校樣訊息的收件者 {#selecting-the-proof-target}

校樣是特殊訊息，可讓您在將傳遞傳送至主要目標之前先測試傳遞。 校樣收件者負責核准訊息的表單和內容。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#seeds-and-proofs-video)


若要選取校樣的目標，請遵循下列步驟：

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。
1. 按一下 **[!UICONTROL Target of the proofs]** 標籤。
1. 按一下 **[!UICONTROL Targeting mode]** 欄位，以選擇要套用的方法： **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** 或 **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>校樣的目標通常可新增至主要目標。 若要這麼做，請在 **[!UICONTROL Main target]** 標籤。

## 定義特定校樣目標 {#defining-a-specific-proof-target}

選取校樣目標時， **[!UICONTROL Definition of a specific proof target]** 選項可讓您從資料庫的設定檔中選取校樣收件者。

選取此選項，即可使用 **[!UICONTROL Add]** 按鈕，如定義主要目標的案例。 請參閱 [選取主要目標](steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

有關校樣傳送的詳細資訊，請參閱 [本節](steps-validating-the-delivery.md#sending-a-proof).

### 在校樣中使用地址替代 {#using-address-substitution-in-proof}

您可以使用 **[!UICONTROL Substitution of the address]** 選項。

此選項可讓您使用傳送的收件者設定檔，並將其電子郵件地址取代為將接收校樣的一或多個其他地址。

選取此選項時，校樣地址將透過特殊編輯器填入，此編輯器可讓您設定替代。

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

設定的執行方式如下：

1. 按一下 **[!UICONTROL Add]** 表徵圖來定義替代。
1. 輸入要使用的收件人地址，或從清單中選擇該地址。
1. 選取要在校樣中使用的設定檔：儲存 **[!UICONTROL Random]** 值 **[!UICONTROL Profile to use]** 欄，在校樣中使用目標的任何設定檔資料。

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 按一下 **[!UICONTROL Detail]** 圖示，以從主要目標中選取設定檔，如下列範例所示：

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   您可以根據需要定義任意數量的替代地址。

## 使用種子地址作為證明 {#using-seed-addresses-as-proof}

您可以使用 **[!UICONTROL Seed addresses]** 作為校樣的目標：此選項可讓您使用或匯入現有種子地址清單。

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>種子地址顯示於 [關於種子地址](about-seed-addresses.md).

您可以結合特定校樣目標的定義以及種子地址的使用，使用 **[!UICONTROL Specific target and Seed addresses]** 選項。 然後，在兩個不同的子標籤中定義相關配置。

另請參閱:

* [選取校樣目標](#selecting-the-proof-target)
* [關於種子地址](about-seed-addresses.md)
* [使用實例：依條件選取種子地址](use-case--selecting-seed-addresses-on-criteria.md)

## 教學課程影片 {#seeds-and-proofs-video}

在此影片中，您將學習如何為現有電子郵件新增種子和校樣，以及如何傳送。

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

提供其他Campaign Classic作法影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
