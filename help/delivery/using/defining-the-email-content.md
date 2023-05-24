---
product: campaign
title: 在Adobe Campaign Classic中定義電子郵件內容
description: 瞭解如何使用Adobe Campaign定義電子郵件內容
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email Design
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1989'
ht-degree: 1%

---

# 定義電子郵件內容 {#defining-the-email-content}



## 發件人 {#sender}

若要定義將顯示在已傳送訊息標題中的寄件者名稱和地址，請按一下 **[!UICONTROL From]** 連結。

![](assets/s_ncs_user_wizard_email02.png)

此視窗可讓您輸入建立電子郵件標頭所需的所有資訊。 可將此資訊加以個人化。若要這麼做，請使用輸入欄位右側的按鈕，插入個人化欄位。

若要瞭解如何插入和使用個人化欄位，請參閱 [關於個人化](about-personalization.md) 區段。

>[!NOTE]
>
>* 預設會使用寄件者的地址進行回覆。
>* 標頭引數不得為空白。 依預設，它們包含設定部署精靈時輸入的值。 如需詳細資訊，請參閱 [安裝指南](../../installation/using/deploying-an-instance.md).
>* 寄件者的地址是強制允許傳送電子郵件的地址（RFC標準）。
>* Adobe Campaign會檢查所輸入電子郵件地址的語法。


>[!IMPORTANT]
>
>在網際網路存取提供者(ISP)為了打擊未經請求的電子郵件（垃圾郵件）而實作的檢查中，Adobe建議建立與為傳送和回覆指定的地址相對應的電子郵件帳戶。 請洽詢您的傳訊系統管理員。

## 訊息主旨 {#message-subject}

訊息的主旨會在對應欄位中設定。 您可以直接在欄位中輸入該值，或按一下 **[!UICONTROL Subject]** 輸入指令碼的連結。 個人化連結可讓您在主旨中插入資料庫欄位。

>[!IMPORTANT]
>
>訊息主旨為必填欄位。

![](assets/s_ncs_user_wizard_email_object.png)

傳送訊息時，欄位內容將由收件者設定檔中的值取代。

例如，在上面的訊息中，會使用每位收件者設定檔中的資料，針對每位收件者將訊息主旨個人化。

>[!NOTE]
>
>個人化欄位的使用方式顯示於 [關於個人化](about-personalization.md).

您也可以使用將表情符號插入主旨列 **[!UICONTROL Insert emoticon]** 快顯視窗。

## 訊息內容 {#message-content}

>[!IMPORTANT]
>
>基於隱私權理由，我們建議對所有外部資源使用HTTPS。

訊息的內容會在傳遞設定視窗的下方區段中定義。

預設會根據收件者偏好設定，以HTML或文字格式傳送訊息。 建議您以兩種格式建立內容，以確保在任何郵件系統中都能正確顯示郵件。 有關詳細資訊，請參閱 [選取訊息格式](email-parameters.md#selecting-message-formats).

* 若要匯入HTML內容，請使用 **[!UICONTROL Open]** 按鈕。 您也可以將原始程式碼直接貼到 **[!UICONTROL Source]** 子標籤。

   如果您使用 [數位內容編輯器](../../web/using/about-campaign-html-editor.md) (DCE)，請參閱 [選取內容範本](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!IMPORTANT]
   >
   >HTML內容必須預先建立，然後匯入至Adobe Campaign。 HTML編輯器並非專為內容建立而設計。

   此 **[!UICONTROL Preview]** 子索引標籤可讓您檢視收件者的每個內容轉譯。 個人化欄位和內容的條件元素會取代為所選設定檔的對應資訊。

   工具列按鈕可讓您存取HTML頁面的標準動作和格式設定引數。

   ![](assets/s_ncs_user_wizard_email01_138.png)

   您可以從本機檔案或Adobe Campaign中的影像資料庫將影像插入訊息中。 若要這麼做，請按一下 **[!UICONTROL Image]** 圖示並選取適當的選項。

   ![](assets/s_ncs_user_wizard_email01_18.png)

   媒體櫃影像可透過 **[!UICONTROL Resources>Online>Public resources]** 資料夾樹狀結構中的資料夾。 另請參閱 [新增影像](#adding-images).

   工具列中的最後一個按鈕可讓您插入個人化欄位。

   >[!NOTE]
   >
   >個人化欄位的使用方式顯示於 [關於個人化](about-personalization.md).

   頁面底部的標籤可讓您顯示正在建立之頁面的HTML代碼，並檢視訊息的呈現及其個人化。 若要啟動此顯示，請按一下 **[!UICONTROL Preview]** 並透過以下方式選取收件者 **[!UICONTROL Test personalization]** 按鈕。 您可以從定義的目標中選取收件者，或選擇其他收件者。

   ![](assets/s_ncs_user_wizard_email01_139.png)

   您可以驗證HTML訊息。 您也可以檢視電子郵件標頭的內容。

   ![](assets/s_ncs_user_wizard_email01_140.png)

* 若要匯入文字內容，請使用 **[!UICONTROL Open]** 按鈕，或 **[!UICONTROL Text Content]** tab鍵以輸入以文字格式顯示時的訊息內容。 使用工具列按鈕來存取對內容的動作。 最後一個按鈕可讓您插入個人化欄位。

   ![](assets/s_ncs_user_wizard_email01_141.png)

   至於HTML格式，請按一下 **[!UICONTROL Preview]** 標籤以檢視訊息的呈現及其個人化。

   ![](assets/s_ncs_user_wizard_email01_142.png)


## 定義互動式內容 {#amp-for-email-format}

Adobe Campaign可讓您嘗試全新的互動式 [電子郵件AMP](https://amp.dev/about/email/) 格式，可在特定條件下傳送動態電子郵件。

如需詳細資訊，請參閱[本節](defining-interactive-content.md)。

## 使用內容管理 {#using-content-management}

您可以使用內容管理表單，直接在傳送精靈中定義傳送的內容。 若要這麼做，您必須參考要使用的內容管理的發佈範本，在 **[!UICONTROL Advanced]** 傳遞屬性的索引標籤。

![](assets/s_ncs_content_in_delivery.png)

額外的索引標籤可讓您輸入將根據內容管理規則自動整合及格式化的內容。

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>如需Adobe Campaign內容管理的詳細資訊，請參閱 [本節](about-content-management.md).

## 插入表情符號 {#inserting-emoticons}

您可以將表情符號插入電子郵件內容。

1. 按一下 **[!UICONTROL Insert emoticon]** 圖示。
1. 從快顯視窗中選取表情符號。

   ![](assets/emoticon_4.png)

1. 按一下 **[!UICONTROL Close]** 按鈕。

若要自訂表情符號清單，請參閱此 [頁面](customizing-emoticon-list.md).

## 新增影像 {#adding-images}

HTML格式電子郵件傳遞可包含影像。 從傳遞精靈中，您可以匯入包含影像的HTML頁面，或直接使用HTML編輯器透過以下路徑插入影像： **[!UICONTROL Image]** 圖示。

影像可以是：

* 本機影像或從伺服器呼叫的影像
* 儲存在Adobe Campaign公共資源庫中的影像

   公共資源可透過 **[!UICONTROL Resources > Online]** Adobe Campaign階層的節點。 它們會分組在程式庫中，並可包含在電子郵件訊息中，但也可以用於行銷活動或任務，或用於內容管理。

* 與Adobe Experience Cloud共用的資產。 請參閱[本節](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md)。

>[!IMPORTANT]
>
>若要使用傳遞精靈在電子郵件訊息中包含影像，必須將Adobe Campaign執行個體設定為啟用公用資源管理。 此程式可以從部署精靈執行。 請參閱 [本節](../../installation/using/deploying-an-instance.md) 以取得有關設定的進一步資訊。

傳遞精靈可讓您將本機影像或資料庫中儲存的影像新增至訊息內容。 若要這麼做，請按一下 **[!UICONTROL Image]** 按鈕(在「HTML」內容工具列中)。

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>為了讓收件者能夠檢視其收到之訊息中包含的影像，這些訊息必須在可從外部存取的伺服器上提供。

若要透過傳遞精靈管理影像：

1. 按一下 **[!UICONTROL Tracking & Images]** 圖示加以檢視。
   ![](assets/s_ncs_user_email_del_img_param.png)

1. 選取 **[!UICONTROL Upload images]** 在 **[!UICONTROL Images]** 標籤。
1. 然後，您可以選擇是否要將這些影像納入電子郵件中。
   ![](assets/s_ncs_user_email_del_img_upload.png)

* 您可以手動上傳影像，而不需要等候傳遞分析階段。 若要這麼做，請按一下 **[!UICONTROL Upload the images straightaway...]** 連結。
* 您可以指定另一個路徑來存取追蹤伺服器上的影像。 若要這麼做，請在 **[!UICONTROL Images URL]** 欄位。 此值會覆寫安裝精靈引數中定義的值。

當您開啟傳送精靈中包含影像的HTML內容時，訊息會根據傳送引數為您提供立即上傳影像的選項。

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>* 在手動上傳或傳送訊息時，影像存取路徑會遭到修改。
> 
>* 為避免效能問題，如果您將從個人化URL即時下載的影像包含為 [附件](attaching-files.md)，每個影像大小預設不應超過100,000個位元組。 此建議的臨界值可從下列位置設定： [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).


**使用案例：傳送包含影像的訊息**

以下是包含四個影像的傳送範例：

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

這些影像來自本機目錄或網站，您可從 **[!UICONTROL Source]** 標籤。

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

按一下 **[!UICONTROL Tracking & Images]** 圖示然後按一下 **[!UICONTROL Images]** 索引標籤以開始偵測訊息中的影像。

對於偵測到的每個影像，您可以檢視其狀態：

* 如果影像儲存在本機或位於其他伺服器上，即使從外部可以看到此伺服器（例如在網際網路網站上），也會偵測到 **[!UICONTROL Not yet online]**.
* 偵測到的影像為 **[!UICONTROL Already online]** 如果在建立其他傳遞時較早上傳，則不在此限。
* 在部署精靈中，您可以定義未啟用影像偵測的URL：上傳這些影像將 **[!UICONTROL Skipped]**.

>[!NOTE]
>
>影像是以其內容來識別，而不是以存取路徑來識別。 這表示先前以不同名稱或不同目錄上傳的影像，將會偵測為 **[!UICONTROL Already online]**.

在分析階段期間，影像會自動上傳至伺服器，以便可從外部存取，但必須預先上傳的本機影像除外。

您可以繼續工作並上傳影像，以便其他Adobe Campaign運運算元檢視。 如果您能協同工作，這項功能可能會相當實用。 若要這麼做，請按一下 **[!UICONTROL Upload the images straightaway...]** 將影像上傳至伺服器。

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>接著會修改電子郵件中影像的URL，尤其是其名稱。

一旦影像上線，您就可以從 **[!UICONTROL Source]** 訊息的索引標籤。

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

如果您選取 **[!UICONTROL Include the images in the email]**，您可以選擇要包含在對應欄中的影像。

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>如果訊息中包含本機影像，您必須確認訊息原始碼的變更。

## 插入個人化條碼{#insert-a-barcode}

條碼產生模組可讓您建立符合許多常見標準的幾種條碼，包括2D條碼。

您可以使用使用客戶條件定義的值，動態產生條碼作為點陣圖。 電子郵件行銷活動中可包含個人化條碼。 收件者可以列印訊息，並顯示給發行公司以便掃描（例如結帳時）。

若要將條碼插入電子郵件中，請將游標置於您要顯示它的內容中，然後按一下個人化按鈕。 選取 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然後設定下列元素以符合您的需求：

1. 選取條碼型別。

   * 對於1D格式，Adobe Campaign提供下列型別：Codabar、代碼128、GS1-128 （先前稱為EAN-128）、UPC-A、UPC-E、ISBN、EAN-8、代碼39、交錯式2 （共5個）、POSTNET和皇家郵件(RM4SCC)。

      1D條碼範例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417型別涉及2D格式。

      2D條碼範例：

      ![](assets/barcode_insert_09.png)

   * 若要插入QR碼，請選取此型態，然後輸入要套用的錯誤更正率。 此比率定義重複資訊的數量和劣化的容許度。

      ![](assets/barcode_insert_06.png)

      QR碼範例：

      ![](assets/barcode_insert_12.png)

1. 輸入您要插入電子郵件中的條碼大小：設定比例可讓您增加或減少條碼大小，從x1到x10。
1. 此 **[!UICONTROL Value]** 欄位可讓您定義條碼的值。 值可以和特殊優惠方案相符，也可以是條件的函式，也可以是連結至客戶的資料庫欄位值。

   此範例顯示EAN-8型別條碼，收件者的帳號已新增至該條碼。 若要新增此帳號，請按一下 **[!UICONTROL Value]** 欄位並選取 **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. 此 **[!UICONTROL Height]** 欄位可讓您設定條碼的高度，而不變更其寬度，方法是變更每個條之間的間距量。

   根據條碼型別，沒有限制性的登入控制。 如果條碼值不正確，它將只會顯示在 **預覽** 將條碼以紅色劃掉的模式。

   >[!NOTE]
   >
   >指定給條碼的值取決於其型別。 例如，EAN-8型別應該有8個數字。
   >
   >右側的個人化按鈕 **[!UICONTROL Value]** 欄位可讓您在值本身之外新增資料。 只要條碼標準接受，這就能豐富條碼。
   >
   >例如，如果您使用GS1-128型別條碼，並且除了輸入值外，還想輸入收件者的帳號，請按一下個人化按鈕，然後選取 **[!UICONTROL Recipient > Account number]**. 如果所選取收件者的帳號輸入正確，條碼會將其列入考量。

設定這些元素後，您就可以完成電子郵件並加以傳送。 為避免錯誤，在執行傳送之前，請務必確保內容正確顯示，方法是按一下 **[!UICONTROL Preview]** 標籤。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果條碼的值不正確，其點陣圖會以紅色劃掉。

![](assets/barcode_insert_11.png)
