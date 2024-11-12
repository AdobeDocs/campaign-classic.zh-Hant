---
product: campaign
title: 定義目標母體
description: 瞭解如何定義目標母體
feature: Audiences, Proofs
role: User
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: f469689f9e8a4d805fb95a1ae120ccd35aba3731
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 3%

---

# 定義目標母體 {#defining-the-target-population}

對於每個傳送，您可以定義幾種目標母體：

* **主要對象**：將接收訊息的設定檔。 [了解更多](steps-defining-the-target-population.md#selecting-the-main-target)
* **校訂**：校訂訊息的收件者，涉及驗證週期。 [了解更多](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **種子地址**：不在傳遞目標但將接收傳遞的收件者（僅適用於行銷活動的內容）。 [了解更多](about-seed-addresses.md)
* **控制組**：不會接收傳遞的母體，用於追蹤行為和行銷活動影響（僅適用於行銷活動的內容）。 [了解更多](../../campaign/using/marketing-campaign-target.md#defining-a-control-group)。

## 選取傳遞的主要收件者 {#selecting-the-main-target}

在大多數情況下，主要目標會從Adobe Campaign資料庫（預設模式）擷取。 不過，收件者也可以儲存在外部檔案中。 若要了解詳細資訊，請參閱[本章節](steps-defining-the-target-population.md#selecting-external-recipients)。

若要選取傳遞的收件者，請遵循下列步驟：

1. 在傳遞編輯器中，選取&#x200B;**[!UICONTROL To]**。
1. 如果收件者儲存在資料庫中，請選擇第一個選項。

   ![](assets/s_ncs_user_wizard_email02a.png)

1. 在&#x200B;**[!UICONTROL Target mapping]**&#x200B;下拉式清單中選取目標對應。 Adobe Campaign預設目標對應是&#x200B;**[!UICONTROL Recipients]**，根據&#x200B;**nms：recipient**&#x200B;結構描述。

   有其他目標對應可供使用，其中一些可能與您的特定設定相關。[了解更多](#select-a-target-mapping)。

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以定義限制篩選器。

   然後，您可以選取要套用的篩選型別：

   ![](assets/s_ncs_user_wizard_email02b.png)

   您可以使用資料庫中定義的定位型別來選取收件者。 若要使用目標型別，請選取它並按一下&#x200B;**[!UICONTROL Next]**。 您可以按一下&#x200B;**[!UICONTROL Preview]**&#x200B;索引標籤，針對每個目標顯示相關的收件者。 針對特定型別的目標，**[!UICONTROL Refine target]**&#x200B;按鈕可讓您合併數個鎖定目標條件。

   預設會提供下列目標型別：

   * **[!UICONTROL Filtering conditions]** ：此選項可讓您定義查詢並顯示結果。 定義查詢的方法會顯示在[此區段](../../platform/using/creating-filters.md#creating-an-advanced-filter)中。
   * **[!UICONTROL Subscribers of an information service]** ：此選項可讓您選取收件者必須訂閱的Newsletter，才能由正在建立的傳遞定位。

     ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** ：此選項可讓您將現有傳遞的收件者定義為鎖定目標條件。 之後，您必須在清單中選取傳送：

     ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** ：此選項可讓您選取傳遞資料夾，並鎖定該資料夾中傳遞的收件者。

     ![](assets/s_ncs_user_wizard_email02e.png)

     您可以從下拉式清單中選取，以篩選收件者的行為：

     ![](assets/s_ncs_user_wizard_email02f.png)

     >[!NOTE]
     >
     >**[!UICONTROL Include sub-folders]**&#x200B;選項也可讓您定位在所選節點下方的樹狀結構資料夾中所包含的傳送。

   * **[!UICONTROL Recipients included in a folder]** ：此選項可讓您定位樹狀結構之特定資料夾中所包含的設定檔。
   * **[!UICONTROL A recipient]** ：此選項可讓您從資料庫中的設定檔選取特定收件者。
   * **[!UICONTROL A list of recipients]** ：此選項可讓您鎖定收件者清單。 清單會顯示在[此區段](../../platform/using/creating-and-managing-lists.md)中。
   * **[!UICONTROL User filters]** ：此選項可讓您存取預先設定的篩選器，以使用這些篩選器作為資料庫中設定檔的篩選條件。 預先設定的篩選器會顯示在[此區段](../../platform/using/creating-filters.md#saving-a-filter)中。
   * 選項&#x200B;**[!UICONTROL Exclude recipients corresponding to this segment]**&#x200B;可讓您鎖定不符合已定義之目標條件的收件者。 若要使用此選項，請選取適當的方塊，然後套用定位（如先前所定義）以排除產生的設定檔。

     ![](assets/s_ncs_user_wizard_email02g.png)

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入此定位的名稱。 依預設，標籤將是第一個鎖定目標條件的標籤。 若為組合，最好使用明確名稱。
1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以驗證設定的鎖定目標。

   主要目標設定索引標籤的中央區段中會摘要說明已定義的鎖定目標條件。 按一下條件以檢視其內容（設定和預覽）。 若要刪除條件，請按一下位於其標籤後面的十字形。

   ![](assets/s_ncs_user_wizard_email02h.png)

### 選取外部收件者 {#selecting-external-recipients}

您可以對未儲存在資料庫中，但儲存在外部檔案中的收件者啟動傳遞。 例如，我們會傳送傳遞至從文字檔匯入的收件者。

操作步驟：

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結以選取傳遞的收件者。
1. 選取&#x200B;**[!UICONTROL Defined in an external file]**&#x200B;選項。

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 依預設，收件者會匯入資料庫中。 您必須選取&#x200B;**[!UICONTROL Target mapping]**。 [了解更多](#select-a-target-mapping)

   您也可以選擇&#x200B;**[!UICONTROL Do not import the recipients into the database]**。

1. 匯入收件者時，按一下&#x200B;**[!UICONTROL File format definition...]**&#x200B;連結以選取並設定外部檔案。

   如需資料匯入的詳細資訊，請參閱[本節](../../platform/using/executing-import-jobs.md#step-2---source-file-selection)。

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;並將您的傳遞設定為標準傳遞。

>[!CAUTION]
>
>定義電子郵件傳送的訊息內容時，請勿包含映象頁面的連結；此傳送模式無法產生此連結。

### 定義排除設定 {#define-exclusion-settings}

由服務提供者(IAP)提供地址錯誤和品質評等。 此資訊會在傳遞動作後自動更新收件者設定檔中，並包含服務提供者傳回的檔案。 您可以在設定檔中以唯讀方式檢視它。

您可以選擇排除已達到特定連續錯誤數或品質評等低於此視窗中所指定臨界值的地址。 您也可以選擇是否授權未傳回任何資料的非限定地址。

>[!NOTE]
>
>如果兩個收件者在直接郵件傳遞中具有相同的名字、姓氏、郵遞區號和城市，則會發生雙重錯誤，且不會考慮重複的專案。

**[!UICONTROL Exclusions]**&#x200B;索引標籤是用來限制訊息數目。

>[!NOTE]
>
>建議使用預設引數，但您可以根據需求調整設定。 不過，這些選項僅應由專家使用者變更，以避免任何誤用和錯誤。

按一下&#x200B;**[!UICONTROL Edit...]**&#x200B;連結以修改預設設定。

![](assets/s_ncs_user_wizard_email02i.png)

可以使用以下選項：

* **[!UICONTROL Exclude duplicate addresses during delivery]**。 此選項預設為作用中：可讓您在傳送期間消除重複的電子郵件地址。 套用的策略可能會因Adobe Campaign的使用方式及資料庫中的資料型別而異。

  可為每個傳遞範本設定選項的預設值。

  例如：

   * 電子報或電子檔案傳遞的傳遞。 若資料沒有原生重複專案，則某些情況下不會排除重複專案。 使用相同電子郵件地址訂閱的一對夫婦可能會收到兩則特定的個人化電子郵件訊息：一則以姓名傳送給每個人。 在此情況下，可取消選取此選項。
   * 行銷活動的傳遞：重複排除是避免傳送太多訊息給相同收件者的基本條件。 在此情況下，可以選取此選項。

     如果取消選取此選項，您可以存取其他選項： **[!UICONTROL Keep duplicate records (same identifier)]**。 它可讓您授權傳送多筆訊息給符合數個鎖定目標的收件者。

     ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** ，即電子郵件地址位於封鎖清單上的收件者（「選擇退出」）。 為了遵守電子行銷的職業道德和電子商務的相關法律，必須保持選取此選項。
* **[!UICONTROL Exclude quarantined recipients]**。 此選項可讓您從目標排除位址未回應的任何設定檔。 我們強烈建議維持選取此選項。

  >[!NOTE]
  >
  >如需隔離管理的詳細資訊，請參閱[瞭解隔離管理](understanding-quarantine-management.md)。

* **[!UICONTROL Limit delivery]**&#x200B;至指定數目的訊息。 此選項可讓您輸入要傳送的訊息數目上限。 如果目標的內容超過指示的訊息數，則會將隨機選取專案套用至目標。

### 減少目標母體大小 {#reducing-the-size-of-the-target-population}

您可以減少目標母體的大小。 若要這麼做，請在&#x200B;**[!UICONTROL Requested quantity]**&#x200B;欄位中指定要匯出的收件者數目。

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 選取校樣訊息的收件者 {#selecting-the-proof-target}

校樣是一則特殊訊息，可讓您在將內容傳送至主要目標之前先測試內容。 校樣收件者負責核准訊息的表單和內容。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#seeds-and-proofs-video)


若要選取校樣目標，請遵循下列步驟：

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。
1. 按一下「**[!UICONTROL Target of the proofs]**」標籤。
1. 按一下&#x200B;**[!UICONTROL Targeting mode]**&#x200B;欄位以選擇要套用的方法： **[!UICONTROL Definition of a specific proof target]** 、 **[!UICONTROL Substitution of the address]** 、 **[!UICONTROL Seed addresses]**&#x200B;或&#x200B;**[!UICONTROL Specific target and seed addresses]**。

>[!NOTE]
>
>通常，校樣的目標可以新增到主要目標。 若要這麼做，請在&#x200B;**[!UICONTROL Main target]**&#x200B;索引標籤的下方區段中選取適當的選項。

## 定義特定校訂目標 {#defining-a-specific-proof-target}

選取校訂目標時，**[!UICONTROL Definition of a specific proof target]**&#x200B;選項可讓您從資料庫中的設定檔選取校訂收件者。

選取此選項即可使用&#x200B;**[!UICONTROL Add]**&#x200B;按鈕選擇收件者，如同定義主要目標一樣。 請參閱[選取主要目標](steps-defining-the-target-population.md#selecting-the-main-target)。

![](assets/s_ncs_user_wizard_email01_143.png)

有關證明傳送的詳細資訊，請參閱[本節](steps-validating-the-delivery.md#sending-a-proof)。

### 在證明中使用地址替代 {#using-address-substitution-in-proof}

您可以使用&#x200B;**[!UICONTROL Substitution of the address]**&#x200B;選項，而不需在資料庫中選取專用的收件者。

此選項可讓您使用傳送的收件者設定檔，並將其電子郵件地址取代為將接收校樣的一或多個其他地址。

選取此選項時，將透過可讓您設定替代的特殊編輯器填寫校樣地址。

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

設定執行如下：

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;圖示以定義替代。
1. 輸入要使用的收件者地址，或從清單中選取收件者地址。
1. 選取要在校訂中使用的設定檔：將&#x200B;**[!UICONTROL Random]**&#x200B;值儲存在&#x200B;**[!UICONTROL Profile to use]**&#x200B;欄，以在校訂中使用目標的任何設定檔資料。

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 按一下&#x200B;**[!UICONTROL Detail]**&#x200B;圖示，從主要目標中選取設定檔，如下列範例所示：

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   您可以視需要定義儘可能多的替代地址。

## 使用種子地址作為證明 {#using-seed-addresses-as-proof}

您可以使用&#x200B;**[!UICONTROL Seed addresses]**&#x200B;作為校樣的目標：此選項可讓您使用或匯入現有種子地址的清單。

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>種子地址以[關於種子地址](about-seed-addresses.md)呈現。

您可以使用&#x200B;**[!UICONTROL Specific target and Seed addresses]**&#x200B;選項，結合特定證明目標的定義和種子地址的使用。 相關設定隨後會在兩個單獨的子標籤中定義。

另請參閱：

* [選取校訂目標](#selecting-the-proof-target)
* [關於種子地址](about-seed-addresses.md)
* [使用實例：依條件選取種子地址](use-case-selecting-seed-addresses-on-criteria.md)

## 選擇目標對應 {#select-a-target-mapping}

依預設，傳遞範本以&#x200B;**[!UICONTROL Recipients]**&#x200B;為目標。 因此，它們的目標對應使用&#x200B;**nms：recipient**&#x200B;資料表的欄位。 Adobe Campaign為您的傳送提供其他目標對應，以根據您的需求使用。

![](assets/delivery_select_mapping.png)

這些對應如下：

| 名稱 | 使用 | 標準結構描述 |
|---|---|---|
| 收件者 | 傳遞給Adobe Campaign資料庫的收件者 | nms：recipient |
| 訪客 | 例如，透過轉介（病毒式行銷）或社交網路(Facebook， X — 先前稱為Twitter)收集設定檔的訪客。 | mns：visitor |
| 訂閱 | 傳遞給已訂閱資訊服務（例如電子報）的收件者 | nms：subscription |
| 訪客訂閱 | 傳遞給訂閱資訊服務的訪客 | nms：visitorSub |
| 服務 | Publish至X帳戶或Facebook頁面 | nms：service |
| 運算子 | 傳遞給Adobe Campaign操作者 | nms：operator |
| 外部檔案 | 透過包含傳遞所需所有資訊的檔案傳遞 | 沒有連結的結構描述，沒有輸入目標 |


## 教學課程影片 {#seeds-and-proofs-video}

在本影片中，您將瞭解如何新增種子和校樣到現有電子郵件以及如何傳送它。

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)提供其他Campaign Classic操作說明影片。
