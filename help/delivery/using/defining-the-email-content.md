---
title: 在Adobe Campaign Classic中定義電子郵件內容
description: 瞭解如何使用Adobe Campaign Classic定義電子郵件內容。
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 30803bde7be6073895fcea4b6c70655a27111f55

---


# 定義電子郵件內容{#defining-the-email-content}

## 傳送者 {#sender}

要定義將出現在所發送消息標題中的發件人名稱和地址，請按一下該 **[!UICONTROL From]** 連結。

![](assets/s_ncs_user_wizard_email02.png)

此視窗可讓您輸入建立電子郵件標題所需的所有資訊。 這些資訊可以個人化。 若要這麼做，請使用輸入欄位右側的按鈕來插入個人化欄位。

要瞭解如何插入和使用個人化欄位，請參閱關於個 [人化](../../delivery/using/about-personalization.md) 一節。

>[!NOTE]
>
>* 預設會使用傳送者的位址來回覆。
>* 標題參數不得為空。 預設情況下，它們包含配置部署嚮導時輸入的值。 有關詳細資訊，請參閱《安 [裝指南》](../../installation/using/deploying-an-instance.md)。
>* 發件人地址是允許發送電子郵件的強制性地址（RFC標準）。
>* Adobe Campaign會檢查輸入的電子郵件地址語法。


>[!CAUTION]
>
>在網際網路存取提供者(ISP)為對抗垃圾郵件（垃圾訊息）而實施的檢查中，Adobe建議建立與傳送和回覆所指定位址對應的電子郵件帳戶。 請洽詢您的訊息系統管理員。

## 訊息主體 {#message-subject}

消息的主題在相應欄位中配置。 您可以直接在欄位中輸入，或按一下 **[!UICONTROL Subject]** 連結以輸入指令碼。 個人化連結可讓您在主題中插入資料庫欄位。

>[!CAUTION]
>
>訊息主體為強制性。

![](assets/s_ncs_user_wizard_email_object.png)

當傳送訊息時，欄位內容會由收件者描述檔中的值取代。

例如，在上述訊息中，訊息的主旨是使用每位收件者的個人資料來個人化。

>[!NOTE]
>
>個人化欄位的使用會顯示在「關於個 [人化」中](../../delivery/using/about-personalization.md)。

## 訊息內容 {#message-content}

>[!CAUTION]
>
>基於隱私權原因，我們建議對所有外部資源使用HTTPS。

消息內容在傳送配置窗口的下部部分中定義。

根據收件者偏好設定，訊息預設會以HTML或文字格式傳送。 我們建議您以兩種格式建立內容，以確保訊息能正確顯示在任何郵件系統中。 有關詳細資訊，請參閱選 [擇消息格式](#selecting-message-formats)。

* 若要匯入HTML內容，請使用按 **[!UICONTROL Open]** 鈕。 您也可以將原始碼直接貼到子標 **[!UICONTROL Source]** 簽中。

   如果您使用數位內 [容編輯器](../../web/using/about-campaign-html-editor.md) (DCE)，請參閱 [選擇內容範本](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content)。

   >[!CAUTION]
   >
   >HTML內容必須事先建立，然後匯入Adobe Campaign。 HTML編輯器不是專為建立內容而設計。

   子標 **[!UICONTROL Preview]** 簽可讓您檢視收件者每個內容的轉換。 個性化欄位和內容的條件元素被所選配置檔案的相應資訊替換。

   工具列按鈕可讓您存取HTML頁面的標準動作和格式參數。

   ![](assets/s_ncs_user_wizard_email01_138.png)

   您可以在Adobe Campaign的本機檔案或影像庫訊息中插入影像。 若要這麼做，請按一下圖 **[!UICONTROL Image]** 示並選取適當的選項。

   ![](assets/s_ncs_user_wizard_email01_18.png)

   您可以透過資料夾樹狀結構中的 **[!UICONTROL Resources>Online>Public resources]** 資料夾來存取資料庫影像。 另請參閱「 [添加映像」](#adding-images)。

   工具列的最後一個按鈕可讓您插入個人化欄位。

   >[!NOTE]
   >
   >個人化欄位的使用會顯示在「關於個 [人化」中](../../delivery/using/about-personalization.md)。

   頁面底部的標籤可讓您顯示所建立頁面的HTML程式碼，並檢視訊息的個人化呈現。 若要啟動此顯示，請按 **[!UICONTROL Preview]** 一下並使用工具列中的按 **[!UICONTROL Test personalization]** 鈕選取收件者。 您可以從定義的目標中選擇收件者，或選擇其他收件者。

   ![](assets/s_ncs_user_wizard_email01_139.png)

   您可以驗證HTML訊息。 您也可以檢視電子郵件標題的內容。

   ![](assets/s_ncs_user_wizard_email01_140.png)

* 要導入文本內容，請使 **[!UICONTROL Open]** 用按鈕或選 **[!UICONTROL Text Content]** 項卡輸入以文本格式顯示的消息內容。 使用工具列按鈕來存取內容上的動作。 最後一個按鈕可讓您插入個人化欄位。

   ![](assets/s_ncs_user_wizard_email01_141.png)

   至於HTML格式，請按一 **[!UICONTROL Preview]** 下頁面底部的標籤，以檢視以個人化方式呈現訊息。

   ![](assets/s_ncs_user_wizard_email01_142.png)

## 選擇消息格式 {#selecting-message-formats}

您可以變更傳送的電子郵件格式。 若要這麼做，請編輯傳送屬性，然後按一下標 **[!UICONTROL Delivery]** 簽。

![](assets/s_ncs_user_wizard_email_param.png)

在窗口的下半部選擇電子郵件格式：

* **[!UICONTROL Use recipient preferences]** （預設模式）

   消息格式根據儲存在收件人配置檔案中的資料定義，並預設儲存在 **[!UICONTROL email format]** 欄位(@emailFormat)中。 如果收件者希望以特定格式接收訊息，則此格式為傳送的格式。 如果未填入欄位，則會傳送多部分替代訊息（請參閱下文）。

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   訊息包含兩種格式：文字和HTML。 接收上顯示的格式取決於收件人郵件軟體的配置（多部分替代）。

   >[!CAUTION]
   >
   >此選項包括文檔的兩個版本。 因此，它會影響傳送率，因為訊息大小較大。

* **[!UICONTROL Send all messages in text format]**

   訊息會以文字格式傳送。 HTML格式不會傳送，但只有在收件者點按訊息時，才會用於鏡像頁面。

## 定義互動式內容 {#amp-for-email-format}

Adobe Campaign可讓您嘗試新的互動式 [AMP for Email](https://amp.dev/about/email/) ，讓您在特定條件下傳送動態電子郵件。

For more on this, see [this section](../../delivery/using/defining-interactive-content.md).

## 使用內容管理 {#using-content-management}

您可以直接在傳送精靈中，使用內容管理表單來定義傳送的內容。 若要這麼做，您必須在傳送屬性的標籤中參考要使用之內容管理 **[!UICONTROL Advanced]** 的發佈範本。

![](assets/s_ncs_content_in_delivery.png)

另外一個標籤可讓您輸入內容，這些內容會根據內容管理規則自動整合和格式化。

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>如需Adobe Campaign內容管理的詳細資訊，請參閱 [本節](../../delivery/using/about-content-management.md)。

## 新增影像 {#adding-images}

HTML格式的電子郵件傳送可包含影像。 從傳送精靈中，您可以匯入包含影像的HTML頁面，或透過圖示直接使用HTML編輯器插入 **[!UICONTROL Image]** 影像。

影像可以是：

* 本機影像或從伺服器呼叫的影像
* 儲存在Adobe Campaign公共資源庫中的影像

   公共資源可透過Adobe Campaign階 **[!UICONTROL Resources > Online]** 層的節點存取。 它們會分組在資料庫中，並可包含在電子郵件訊息中，但也可用於促銷活動或工作，或用於內容管理。

* 與Adobe Experience cloud共用的資產。 Refer to [this section](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!CAUTION]
>
>若要使用傳送精靈將影像加入電子郵件訊息中，必須設定Adobe Campaign例項，以啟用公共資源管理。 此過程可從部署嚮導中執行。 有關配置的 [詳細資訊](../../installation/using/deploying-an-instance.md) ，請參閱本節。

傳送精靈可讓您將儲存在資料庫中的本機影像或影像新增至訊息內容。 To do this, click the **[!UICONTROL Image]** button in the HTML content toolbar.

![](assets/s_ncs_user_image_from_library.png)

為了讓收件者能夠檢視其所收到訊息中包含的影像，這些訊息必須可在可從外部存取的伺服器上使用。

若要透過傳送精靈管理影像，您必須按一下工具 **[!UICONTROL Tracking & Images]** 列中的圖示。

![](assets/s_ncs_user_email_del_img_param.png)

在選 **[!UICONTROL Upload images]** 項卡中 **[!UICONTROL Images]** 選擇。 然後，您可以選擇是否要將影像加入電子郵件訊息中。

![](assets/s_ncs_user_email_del_img_upload.png)

* 您可以手動上傳影像，而不需等待傳送分析階段。 若要這麼做，請按一下 **[!UICONTROL Upload images now]** 連結。
* 您可以指定另一個路徑，以存取追蹤伺服器上的影像。 若要這麼做，請在欄位中輸 **[!UICONTROL Image URL]** 入。 此值將覆蓋在安裝嚮導參數中定義的值。

當您在傳送精靈中開啟包含影像的HTML內容時，會顯示訊息，提供您根據傳送參數立即上傳影像的選項。

![](assets/s_ncs_user_email_del_img_local.png)

>[!CAUTION]
>
>在手動上傳或傳送訊息期間會修改影像存取路徑。

**範例：傳送含影像的訊息{#example--sending-a-message-with-images}**

以下是包含4張影像的傳送範例：

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

這些影像來自本機目錄或網站，如您可從標籤中驗證 **[!UICONTROL Source]** 的。

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

按一下圖 **[!UICONTROL Tracking & Images]** 示，然後按一 **[!UICONTROL Images]** 下標籤，開始偵測訊息中的影像。

對於每個檢測到的映像，您可以查看其狀態：

* 如果映像儲存在本地或位於另一台伺服器上，即使該伺服器從外部（例如在Internet站點上）可見，也會被檢測為 **[!UICONTROL Not yet online]**。
* 在建立其他傳送時，會 **[!UICONTROL Already online]** 偵測到影像，就像之前上傳過影像一樣。
* 在部署精靈中，您可以定義未啟用影像偵測的URL:上傳這些影像將會 **[!UICONTROL Skipped]**&#x200B;是。

>[!NOTE]
>
>影像是由其內容識別，而非由其存取路徑識別。 這表示先前以不同名稱或不同目錄上傳的影像會偵測為 **[!UICONTROL Already online]**。

在分析階段，影像會自動上傳至伺服器，以便從外部存取，但必須事先上傳的本機影像除外。

您可以繼續工作並上傳影像，讓其他Adobe Campaign營運商可以檢視這些影像。 如果您合作，您可能會發現這項功能很有用。 若要這麼做，請按一 **[!UICONTROL Upload the images straightaway...]** 下以將影像上傳至伺服器。

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>然後會修改電子郵件中影像的URL，尤其是其名稱。

在影像上線後，您就可以從訊息的標籤中檢視其名稱 **[!UICONTROL Source]** 和路徑的變更。

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

如果您選 **[!UICONTROL Include the images in the email]**&#x200B;取，您可以選擇要包含在對應欄中的影像。

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>如果消息中包含本地映像，則必須確認對消息原始碼的更改。

## 在電子郵件中插入條形碼{#inserting-a-barcode-in-an-email}

條碼產生模組可讓您建立數種符合許多常見標準的條碼，包括2D條碼。

可以使用使用客戶標準定義的值動態生成條形碼作為點陣圖。 個人化條碼可以包含在電子郵件宣傳中。 收件者可列印訊息並將它顯示給發行公司以進行掃描（例如，當結帳時）。

若要將條形碼插入電子郵件中，請將游標置於要顯示該條形碼的內容中，然後按一下個人化按鈕。 Select **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

然後設定下列元素以符合您的需求：

1. 選擇條形碼類型。

   * 對於1D格式，Adobe Campaign提供下列類型：Codabar, Code 128, GS1-128（之前稱為EAN-128）, UPC-A, UPC-E, ISBN, EAN-8, Code39, Interable 2 of 5, POSTNET和Royal Mail(RM4SCC)。

      1D條形碼示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417類型與2D格式有關。

      2D條碼範例：

      ![](assets/barcode_insert_09.png)

   * 若要插入QR Code，請選取此類型並輸入要套用的糾錯率。 此比率定義了重複的資訊量和惡化容限。

      ![](assets/barcode_insert_06.png)

      QR code範例：

      ![](assets/barcode_insert_12.png)

1. 輸入要插入到電子郵件中的條形碼的大小：配置比例可讓您將條形碼的大小從x1增加或減小到x10。
1. 該 **[!UICONTROL Value]** 欄位允許您定義條形碼的值。 值可以與特殊選件相符，也可以是標準的函式，也可以是連結至客戶的資料庫欄位的值。

   此示例顯示了EAN-8類型條形碼，該條形碼已添加到收件者的帳戶號。 若要新增此帳戶號碼，請按一下欄位右側的個人化按 **[!UICONTROL Value]** 鈕並選取 **[!UICONTROL Recipient > Account number]**。

   ![](assets/barcode_insert_15.png)

1. 此 **[!UICONTROL Height]** 欄位可讓您設定條碼的高度，而不需變更其寬度，方法是變更每個條條之間的間距。

   根據條形碼類型，沒有限制條目控制。 如果條形碼值不正確，則只會在「預覽」模式中顯示該值，在 **「預覽** 」模式中，條形碼將以紅色划出。

   >[!NOTE]
   >
   >分配給條形碼的值取決於其類型。 例如，EAN-8類型的數字恰好為8。
   >
   >欄位右側的個人化按鈕 **[!UICONTROL Value]** 可讓您除了新增值本身以外，還新增資料。 這豐富了條形碼，前提是條形碼標準接受它。
   >
   >例如，如果您使用GS1-128類型的條形碼，並且除了要輸入值之外還要輸入收件人的帳戶號，請按一下個性化按鈕並選擇 **[!UICONTROL Recipient > Account number]**。 如果正確輸入了選定收件人的帳戶號碼，條形碼會將其納入考慮範圍。

在設定好這些元素後，您就可以完成電子郵件並傳送。 若要避免錯誤，請務必在按一下標籤執行傳送前，先確定您的內容已正確 **[!UICONTROL Preview]** 顯示。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果條形碼的值不正確，其點陣圖將以紅色交叉顯示。

![](assets/barcode_insert_11.png)

## 在日本手機上傳送電子郵件 {#sending-emails-on-japanese-mobiles}

### 日文行動裝置的電子郵件格式 {#email-formats-for-japanese-mobiles}

Adobe Campaign管理三種特定的日文格式，用於行動裝置上的電子郵件：Deco- **mail** (DoCoMo mobiles)、 **Decore Mail** (Softbank mobiles)和 **Decoring Mail** (KDDI AU mobiles)。 這些格式會加上特定的編碼、結構和大小限制。 進一步瞭解本節的限制 [和建議](#limitations-and-recommendations)。

為了讓收件者能夠正確接收以下格式的訊息，我們建議在對應的描述檔 **[!UICONTROL Deco-mail (DoCoMo)]**&#x200B;中 **[!UICONTROL Decore Mail (Softbank)]** 選取 **[!UICONTROL Decoration Mail (KDDI AU)]** 或選取：

![](assets/deco-mail_03.png)

不過，如果您將選 **[!UICONTROL Email format]** 項保留為 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]****[!UICONTROL Text]**&#x200B;或Adobe Campaign會自動偵測（傳送電子郵件時）要使用的日文格式，以正確顯示訊息。

該自動檢測系統基於郵件規則集中定義的預定義域 **[!UICONTROL Management of Email Formats]** 的清單。 有關管理電子郵件格式的詳細資訊，請參 [閱本頁](../../installation/using/email-deliverability.md#managing-email-formats)。

### 限制與建議 {#limitations-and-recommendations}

傳送電子郵件時，會受到若干限制，這些電子郵件會在日本供應商(Softbank、DoCoMo、KDDI AU)所營運的行動裝置上讀取。

因此，您必須：

* 僅使用JPEG或GIF格式的影像
* 建立文字和HTML區段的傳送，其欄位嚴格低於10 000位元組（適用於KDDI AU和DoCoMo）
* 使用總大小（編碼前）低於100 KB的影像
* 每則訊息不要使用超過20個影像
* 使用精簡的HTML格式（每個運算子可使用有限數目的標籤）

>[!NOTE]
>
>建立訊息時，應考量到每個運算子的特定限制。 請參閱：
>
>* 若為DoCoMo，請參 [閱本頁](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* 有關KDDI AU，請參 [閱本頁](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* 如需Softbank，請參 [閱本頁](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


### 測試電子郵件內容 {#testing-the-email-content}

#### 預覽訊息 {#previewing-the-message}

Adobe Campaign可讓您檢查訊息格式是否適合傳送至日文行動裝置。

定義內容並輸入電子郵件主旨後，您就可以在建立訊息時檢查顯示和格式。

在內容 **[!UICONTROL Preview]** 編輯窗口的頁籤中，按一下可 **[!UICONTROL More... > Deco-mail diagnostic]** 以：

* 檢查HTML內容標籤是否符合日文格式限制
* 檢查訊息中的影像數量是否未超過格式（20張影像）所設定的限制
* 檢查消息大小總計（小於100kB）

   ![](assets/deco-mail_06.png)

#### 執行排版規則 {#running-typology-rule}

除了預覽診斷外，在傳送校樣或傳送時進行第二檢查：分析期間會啟 **[!UICONTROL Deco-mail check]**&#x200B;動特定的排版規則。

>[!CAUTION]
>
>只有當至少一個收件者設定為接收電子郵件或格式時，才會執 **[!UICONTROL Deco-mail (DoCoMo)]**&#x200B;行 **[!UICONTROL Decore Mail (Softbank)]** 此類 **[!UICONTROL Decoration Mail (KDDI AU)]** 型規則。

此排版規則可讓您確定傳送符合日文運算子定義的格式限制 [](#limitations-and-recommendations) ，尤其是與電子郵件的總大小、HTML和文字區段的大小、訊息中的影像數目，以及HTML內容中的標籤有關。

#### 傳送校樣 {#sending-proofs}

您可以傳送校樣來測試傳送。 當您傳送證明時，如果您使用替代地址，請輸入與所用描述檔電子郵件格式對應的地址。

例如，如果此描述檔的電子郵件格式是預先在上定義的，您可以將描述檔的位址取代為test@softbank.ne.jp **[!UICONTROL Decore Mail (Softbank)]**。

![](assets/deco-mail_05.png)

### 傳送訊息 {#sending-messages}

若要使用Campaign以日文電子郵件格式傳送電子郵件給收件者，有兩種選項可能：

* 建立兩個傳送：一個僅供日文收件者使用，另一個則供其他收件者使用——請參 [閱本節](#designing-a-specific-delivery-for-japanese-formats)。
* 建立單一傳送，Adobe Campaign會自動偵測要使用的格式——請參 [閱本節](#designing-a-delivery-for-all-formats)。

#### 針對日文格式設計特定的傳送 {#designing-a-specific-delivery-for-japanese-formats}

您可以建立包含兩個傳送的工作流程：一個要在日文行動裝置上閱讀，另一個要在標準電子郵件格式的收件者閱讀。

若要這麼做，請使用工 **[!UICONTROL Split]** 作流程中的活動，並將日文電子郵件格式（裝飾郵件、裝飾郵件和裝飾郵件）定義為篩選條件。

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

#### 針對所有格式設計傳送內容 {#designing-a-delivery-for-all-formats}

當Adobe Campaign根據網域動態管理格式(電子郵件格式定義為 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 或 **[!UICONTROL Text]** )時，您可以傳送相同的傳送給所有收件者。

訊息連絡人會正確顯示給日文行動裝置上的使用者，就像標準收件者一樣。

>[!CAUTION]
>
>請務必遵守與每種日文電子郵件格式（裝飾郵件、裝飾郵件和轉寄郵件）相關的特殊功能。 For more information on limitations, refer to [this section](#limitations-and-recommendations).
