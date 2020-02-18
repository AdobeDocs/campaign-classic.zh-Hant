---
title: 定義目標人口
seo-title: 定義目標人口
description: 定義目標人口
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# 定義目標人口 {#defining-the-target-population}

## 關於目標人口族群 {#about-target-populations}

您可以針對每個傳送定義數種目標人口族群。 以下章節提供如何選擇的詳細資訊：

* **主要的收件者**。 [閱讀更多資訊](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)。
* **校對訊息的收件者**，以設定驗證週期。 [閱讀更多資訊](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)。

此外，您也可以定義 [種子地址](../../delivery/using/about-seed-addresses.md)，以及 [控制組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。 如果傳送包含在行銷促銷活動中。

## 選擇傳送的主要收件者 {#selecting-the-main-target}

在大多數情況下，主要目標會從促銷活動資料庫（預設模式）中擷取。

收件者也可以儲存在外部檔案中。 此類型傳送的設定會顯示在選取外部收 [件者中](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

要選擇要建立的交貨的收件者，請執行以下步驟：

1. 按一下 **[!UICONTROL To]** 連結。
1. 如果收件者儲存在資料庫中，請選取第一個選項。

   ![](assets/s_ncs_user_wizard_email02a.png)

1. 在下拉式清單中選 **[!UICONTROL Target mapping]** 取目標對應。 Adobe Campaign預設目標對應為 **[!UICONTROL Recipients]**。

   其他目標映射可用，有些可以與您的特定配置相關。 有關目標映射的詳細資訊，請參 [閱選擇目標映射](../../delivery/using/selecting-a-target-mapping.md)。

1. 按一下按 **[!UICONTROL Add]** 鈕以定義限制篩選。

   然後，您可以選取要套用的篩選類型：

   ![](assets/s_ncs_user_wizard_email02b.png)

   您可以使用資料庫中定義的定位類型來選取收件者。 若要使用目標類型，請選取它，然後按一下 **[!UICONTROL Next]**。 對於每個目標，您都可以按一下標籤來顯示相關的收 **[!UICONTROL Preview]** 件者。 對於特定類型的定位，此按 **[!UICONTROL Refine target]** 鈕可讓您結合數個定位條件。

   預設提供下列目標類型：

   * **[!UICONTROL Filtering conditions]** :此選項可讓您定義查詢並顯示結果。 本節將介紹定義查詢 [的方法](../../platform/using/creating-filters.md#creating-an-advanced-filter)。
   * **[!UICONTROL Subscribers of an information service]** :此選項可讓您選取電子報，而收件者必須訂閱才能由建立的傳送鎖定。

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** :此選項可讓您將現有傳送的收件者定義為定位標準。 然後，您必須在清單中選取傳送：

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** :此選項可讓您選取傳送資料夾，並定位該資料夾中傳送的收件者。

      ![](assets/s_ncs_user_wizard_email02e.png)

      您可以從下拉式清單中選取，以篩選收件者的行為：

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >此選 **[!UICONTROL Include sub-folders]** 項也可讓您定位位於所選節點下方樹狀結構中資料夾中的傳送。

   * **[!UICONTROL Recipients included in a folder]** :此選項可讓您定位樹的特定資料夾中包含的配置檔案。
   * **[!UICONTROL A recipient]** :此選項可讓您從資料庫的描述檔中選取特定的收件者。
   * **[!UICONTROL A list of recipients]** :此選項可讓您定位收件者清單。 本節將列出 [清單](../../platform/using/creating-and-managing-lists.md)。
   * **[!UICONTROL User filters]** :此選項可讓您存取預先設定的篩選條件，以用作資料庫中描述檔的篩選條件。 本節將顯示預配置 [的篩選器](../../platform/using/creating-filters.md#saving-a-filter)。
   * 此選項 **[!UICONTROL Exclude recipients corresponding to this segment]** 可讓您定位不符合已定義之目標標準的收件者。 若要使用此選項，請選取適當的方塊，然後套用先前定義的定位，以排除產生的描述檔。

      ![](assets/s_ncs_user_wizard_email02g.png)

1. 在欄位中輸入此定位的名 **[!UICONTROL Label]** 稱。 依預設，標籤將是第一個定位准則的標籤。 對於組合，最好使用明確的名稱。
1. 按一 **[!UICONTROL Finish]** 下以驗證已設定的定位。

   定義的定位條件會摘要在主要定位設定標籤的中央區段中。 按一下准則以檢視其內容（設定和預覽）。 要刪除標準，請按一下位於標籤後面的交叉點。

   ![](assets/s_ncs_user_wizard_email02h.png)

### 選擇外部收件者 {#selecting-external-recipients}

您可以針對未儲存在資料庫中，但儲存在外部檔案的收件者啟動傳送。 例如，我們會傳送傳送給從文字檔案匯入的收件者。

操作步驟：

1. 按一下 **[!UICONTROL To]** 連結，以選擇傳送的收件者。
1. 選擇選 **[!UICONTROL Defined in an external file]** 項。

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 依預設，收件者會匯入資料庫。 您必須選擇 **[!UICONTROL Target mapping]**。 有關目標映射的詳細資訊，請參 [閱選擇目標映射](../../delivery/using/selecting-a-target-mapping.md)

   您也可以選擇 **[!UICONTROL Do not import the recipients into the database]**。

1. 匯入收件者時，按一下 **[!UICONTROL File format definition...]** 連結以選取並設定外部檔案。

   For more information on data import, refer to [this section](../../platform/using/importing-data.md#step-2---source-file-selection).

1. 按一 **[!UICONTROL Finish]** 下並將傳送設定為標準傳送。

>[!CAUTION]
>
>定義電子郵件傳送的訊息內容時，請勿包含鏡像頁面的連結；無法在此傳送模式中產生。

### 設定排除設定 {#customizing-exclusion-settings}

地址錯誤和質量分級由服務提供商(IAP)提供。 在傳送動作後，此資訊會在收件者描述檔中自動更新，並由服務提供者傳回檔案。 您可在描述檔中以唯讀方式檢視。

您可以選擇排除已達到特定數量連續錯誤或品質分級低於此窗口中指定臨界值的地址。 您也可以選擇是否授權尚未傳回任何資料的非合格地址。

>[!NOTE]
>
>如果直接郵寄的兩個收件者具有相同的名字、姓氏、郵寄碼和城市，將會發生雙重錯誤，而且不會考慮重複。

該 **[!UICONTROL Exclusions]** 頁籤用於限制消息數。

>[!NOTE]
>
>建議使用預設參數，但您可以根據需要調整設定。 不過，這些選項只能由專家使用者變更，以避免使用不當和錯誤。

按一下該 **[!UICONTROL Edit...]** 連結可修改預設配置。

![](assets/s_ncs_user_wizard_email02i.png)

可以使用以下選項：

* **[!UICONTROL Exclude duplicate addresses during delivery]**. 此選項預設為作用中：它可讓您在傳送期間消除重複的電子郵件地址。 所套用的策略會因Adobe Campaign的使用方式及資料庫中的資料類型而異。

   可為每個傳送範本設定選項的預設值。

   例如：

   * 傳送電子報或電子檔案。 在某些情況下，如果資料沒有原生重複項，則不排除重複項。 使用相同電子郵件地址的一對訂閱者可能會收到兩個特定的個人化電子郵件訊息：一個按名稱發送給每個人。 在這種情況下，可以取消選擇此選項。
   * 行銷促銷活動的傳送：重複排除是避免傳送太多訊息給相同收件者的必要條件。 在這種情況下，可以選取此選項。

      如果您取消選取此選項，您可以存取其他選項： **[!UICONTROL Keep duplicate records (same identifier)]**。 它可讓您授權多個傳送給符合數個定位條件的收件者。

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** ，亦即電子郵件位址在黑名單（「選擇退出」）中的收件者。 為了遵守電子行銷的職業道德和電子商務的法律，必須繼續選擇這一選項。
* **[!UICONTROL Exclude quarantined recipients]**. 此選項可讓您從目標中排除任何地址沒有回應的描述檔。 我們強烈建議保留此選項。

   >[!NOTE]
   >
   >有關隔離管理的詳細資訊，請參閱瞭解隔 [離管理](../../delivery/using/understanding-quarantine-management.md)。

* **[!UICONTROL Limit delivery]** 傳送給特定數量的訊息。 此選項可讓您輸入要傳送的訊息數上限。 如果目標的內容超過所指示的消息數，則隨機選擇被應用到目標。

### 縮小目標人口的大小 {#reducing-the-size-of-the-target-population}

您可以縮小目標人口的大小。 若要這麼做，請在欄位中指定要匯出的收件者 **[!UICONTROL Requested quantity]** 數目。

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 選擇校對訊息的收件者 {#selecting-the-proof-target}

此證明是特殊訊息，可讓您在傳送傳送至主要目標之前先測試傳送。 證明收件者負責核准訊息的表單和內容。

要選擇校樣的目標，請執行以下步驟：

1. 按一下 **[!UICONTROL To]** 連結。
1. 按一下標 **[!UICONTROL Target of the proofs]** 簽。
1. 按一下 **[!UICONTROL Targeting mode]** 欄位以選擇要套用的方法： **[!UICONTROL Definition of a specific proof target]** 、 **[!UICONTROL Substitution of the address]** 、 **[!UICONTROL Seed addresses]** 或 **[!UICONTROL Specific target and seed addresses]**。

>[!NOTE]
>
>通常，校對的目標可以添加到主目標。 若要這麼做，請在標籤的下方區段中選取適當的 **[!UICONTROL Main target]** 選項。

## 定義特定校對目標 {#defining-a-specific-proof-target}

選擇校對目標時，選 **[!UICONTROL Definition of a specific proof target]** 項可讓您從資料庫的描述檔中選取校對收件者。

選擇此選項可使用按鈕選擇收 **[!UICONTROL Add]** 件者，如同定義主目標的情況。 請參 [閱選擇主目標](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)。

![](assets/s_ncs_user_wizard_email01_143.png)

For more on proof sending, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### 在校對中使用地址替代 {#using-address-substitution-in-proof}

您可以使用選項，而不是在資料庫中選取專屬收件 **[!UICONTROL Substitution of the address]** 者。

此選項可讓您使用傳送的收件者描述檔，並將其電子郵件地址取代為一或多個接收證明的其他地址。

選取此選項時，校對位址將透過特殊編輯器填入，可讓您設定替代。

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

配置的執行方式如下：

1. 按一下圖 **[!UICONTROL Add]** 標可定義替代。
1. 輸入要使用的收件者地址，或從清單中選擇該地址。
1. 選擇要在校對中使用的配置檔案：將值 **[!UICONTROL Random]** 儲存在欄 **[!UICONTROL Profile to use]** 中，以使用校對中任何目標描述檔的資料。

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 按一 **[!UICONTROL Detail]** 下圖示，從主要目標選取描述檔，如下列範例：

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   您可以根據需要定義任意數量的替代地址。

## 使用種子位址作為證明 {#using-seed-addresses-as-proof}

您可以 **[!UICONTROL Seed addresses]** 用作校樣的目標：此選項可讓您使用或匯入現有種子位址的清單。

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>種子地址在關於種 [子地址中顯示](../../delivery/using/about-seed-addresses.md)。

您可以結合特定證明目標的定義和使用種子地址的選項來 **[!UICONTROL Specific target and Seed addresses]** 進行。 然後在兩個單獨的子頁籤中定義相關配置。
