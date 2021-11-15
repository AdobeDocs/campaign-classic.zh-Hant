---
product: campaign
title: 在Adobe Campaign Classic中定義電子郵件內容
description: 了解使用Adobe Campaign Classic時如何定義電子郵件內容。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 3b8d685642fc74d918a0e312c66d5e4f7b424192
workflow-type: tm+mt
source-wordcount: '1990'
ht-degree: 1%

---

# 定義電子郵件內容 {#defining-the-email-content}

![](../../assets/common.svg)

## 寄件者 {#sender}

要定義將顯示在發送郵件標題中的發件人的名稱和地址，請按一下 **[!UICONTROL From]** 連結。

![](assets/s_ncs_user_wizard_email02.png)

此視窗可讓您輸入建立電子郵件標題所需的所有資訊。 可將此資訊加以個人化。若要這麼做，請使用輸入欄位右側的按鈕來插入個人化欄位。

若要了解如何插入和使用個人化欄位，請參閱 [關於個人化](about-personalization.md) 區段。

>[!NOTE]
>
>* 預設會使用寄件者的地址進行回覆。
>* 標題參數不得為空。 預設情況下，它們包含配置部署嚮導時輸入的值。 有關詳細資訊，請參閱 [安裝指南](../../installation/using/deploying-an-instance.md).
>* 發送者的地址是強制性的，以允許發送電子郵件（RFC標準）。
>* Adobe Campaign會檢查輸入之電子郵件地址的語法。


>[!IMPORTANT]
>
>在由網際網路存取提供者(ISP)實作的檢查以打擊未經請求的電子郵件（垃圾郵件）的內容中，Adobe建議建立與指定用於傳送和回覆的地址相對應的電子郵件帳戶。 請咨詢您的消息系統管理員。

## 訊息主體 {#message-subject}

消息的主題在相應欄位中配置。 您可以直接在欄位中輸入，或按一下 **[!UICONTROL Subject]** 連結以輸入指令碼。 個人化連結可讓您在主題中插入資料庫欄位。

>[!IMPORTANT]
>
>訊息主體是必填的。

![](assets/s_ncs_user_wizard_email_object.png)

傳送訊息時，欄位內容將由收件者設定檔中的值取代。

例如，在上述訊息中，訊息的主旨會針對每位收件者以其設定檔的資料進行個人化。

>[!NOTE]
>
>個人化欄位的使用會顯示在 [關於個人化](about-personalization.md).

您也可以使用 **[!UICONTROL Insert emoticon]** 快顯視窗。

## 訊息內容 {#message-content}

>[!IMPORTANT]
>
>基於隱私權考量，我們建議對所有外部資源使用HTTPS。

訊息的內容會在傳送設定視窗的下方區段中定義。

根據收件者偏好設定，預設會以HTML或文字格式傳送訊息。 建議您以兩種格式建立內容，以確保郵件可以正確顯示在任何郵件系統中。 有關詳細資訊，請參閱 [選擇消息格式](#selecting-message-formats).

* 若要匯入HTML內容，請使用 **[!UICONTROL Open]** 按鈕。 您也可以將原始碼直接貼入 **[!UICONTROL Source]** 頁簽。

   如果您使用 [數位內容編輯器](../../web/using/about-campaign-html-editor.md) (DCE)，請參閱 [選取內容範本](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!IMPORTANT]
   >
   >HTML內容必須預先建立，然後匯入至Adobe Campaign。 HTML編輯器並非專為內容建立而設計。

   此 **[!UICONTROL Preview]** 子索引標籤可讓您檢視收件者每個內容的呈現。 個人化欄位和內容的條件元素會取代為所選設定檔的對應資訊。

   工具欄按鈕提供對HTML頁面標準操作和格式參數的訪問。

   ![](assets/s_ncs_user_wizard_email01_138.png)

   您可以從本機檔案或Adobe Campaign的影像程式庫，在訊息中插入影像。 若要這麼做，請按一下 **[!UICONTROL Image]** 圖示並選取適當的選項。

   ![](assets/s_ncs_user_wizard_email01_18.png)

   程式庫影像可透過 **[!UICONTROL Resources>Online>Public resources]** 資料夾樹中。 另請參閱 [新增影像](#adding-images).

   工具列中的最後一個按鈕可讓您插入個人化欄位。

   >[!NOTE]
   >
   >個人化欄位的使用會顯示在 [關於個人化](about-personalization.md).

   頁面底部的索引標籤可讓您顯示所建立頁面的HTML代碼，並檢視以其個人化呈現訊息的情形。 若要啟動此顯示，請按一下 **[!UICONTROL Preview]** ，並使用 **[!UICONTROL Test personalization]** 按鈕。 您可以從定義的目標中選取收件者，或選擇其他收件者。

   ![](assets/s_ncs_user_wizard_email01_139.png)

   您可以驗證HTML訊息。 您也可以檢視電子郵件標題的內容。

   ![](assets/s_ncs_user_wizard_email01_140.png)

* 若要匯入文字內容，請使用 **[!UICONTROL Open]** 按鈕，或 **[!UICONTROL Text Content]** 頁簽，以輸入以文本格式顯示的消息內容。 使用工具欄按鈕訪問內容上的操作。 最後一個按鈕可讓您插入個人化欄位。

   ![](assets/s_ncs_user_wizard_email01_141.png)

   至於HTML格式，請按一下 **[!UICONTROL Preview]** 頁面底部的索引標籤，以檢視呈現訊息及其個人化內容。

   ![](assets/s_ncs_user_wizard_email01_142.png)


## 定義互動式內容 {#amp-for-email-format}

Adobe Campaign可讓您試用新的互動式 [電子郵件AMP](https://amp.dev/about/email/) 格式，可在特定條件下傳送動態電子郵件。

如需詳細資訊，請參閱[本節](defining-interactive-content.md)。

## 使用內容管理 {#using-content-management}

您可以直接在傳遞精靈中使用內容管理表單來定義傳遞內容。 要執行此操作，您必須參考要使用的內容管理的發佈範本，位於 **[!UICONTROL Advanced]** 標籤。

![](assets/s_ncs_content_in_delivery.png)

另一個索引標籤可讓您輸入內容，內容將根據內容管理規則自動整合和格式化。

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>如需Adobe Campaign中內容管理的詳細資訊，請參閱 [本節](about-content-management.md).

## 插入表情符號 {#inserting-emoticons}

您可以將表情符號插入電子郵件內容。

1. 按一下 **[!UICONTROL Insert emoticon]** 表徵圖。
1. 從快顯視窗中選取表情符號。

   ![](assets/emoticon_4.png)

1. 按一下 **[!UICONTROL Close]** 按鈕。

若要自訂表情符號清單，請參閱 [頁面](customizing-emoticon-list.md).

## 新增影像 {#adding-images}

HTML格式電子郵件傳遞可包含影像。 從傳送精靈中，您可以匯入包含影像的HTML頁面，或直接使用HTML編輯器，透過 **[!UICONTROL Image]** 表徵圖。

影像可以是：

* 本機影像或從伺服器呼叫的影像
* 儲存在Adobe Campaign公共資源庫中的影像

   公共資源可透過 **[!UICONTROL Resources > Online]** Adobe Campaign階層的節點。 它們會分組在資料庫中，並可包含在電子郵件訊息中，但也可用於行銷活動或工作，或用於內容管理。

* 與Adobe Experience Cloud共用的資產。 請參閱[本節](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md)。

>[!IMPORTANT]
>
>若要使用傳送精靈在電子郵件訊息中加入影像，必須將Adobe Campaign例項設定為啟用公用資源管理。 此過程可從部署嚮導中執行。 請參閱 [本節](../../installation/using/deploying-an-instance.md) 以取得有關設定的詳細資訊。

傳遞精靈可讓您將本機影像或儲存在程式庫中的影像新增至訊息內容。 若要這麼做，請按一下 **[!UICONTROL Image]** 按鈕。

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>為了讓收件者能夠檢視其收到訊息中包含的影像，這些訊息必須可在可從外部存取的伺服器上使用。

若要透過傳送精靈管理影像：

1. 按一下 **[!UICONTROL Tracking & Images]** 圖示。
   ![](assets/s_ncs_user_email_del_img_param.png)

1. 選擇 **[!UICONTROL Upload images]** 在 **[!UICONTROL Images]** 標籤。
1. 然後，您可以選擇是否要將影像包含在電子郵件訊息中。
   ![](assets/s_ncs_user_email_del_img_upload.png)

* 您可以手動上傳影像，而不需等待傳遞分析階段。 若要這麼做，請按一下 **[!UICONTROL Upload the images straightaway...]** 連結。
* 您可以指定其他路徑以存取追蹤伺服器上的影像。 若要這麼做，請在 **[!UICONTROL Images URL]** 欄位。 此值會覆寫安裝精靈參數中定義的值。

當您在傳遞精靈中開啟包含影像的HTML內容時，訊息會提供您根據傳遞參數立即上傳影像的選項。

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>* 在手動上傳或傳送訊息時修改影像存取路徑。
> 
>* 為避免效能問題，若您將從個人化URL即時下載的影像納入為 [附件](attaching-files.md)，預設情況下每個影像大小不應超過100,000位元組。 此建議的臨界值可從 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).


**使用案例：傳送含有影像的訊息**

以下是含有四個影像的傳送範例：

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

這些影像來自本地目錄或網站，如您可從 **[!UICONTROL Source]** 標籤。

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

按一下 **[!UICONTROL Tracking & Images]** 表徵圖 **[!UICONTROL Images]** 頁簽，開始檢測消息中的影像。

對於檢測到的每個影像，您可以查看其狀態：

* 如果映像儲存在本地或位於另一台伺服器上，即使此伺服器從外部（例如在網際網路站點上）可見，它將被檢測為 **[!UICONTROL Not yet online]**.
* 影像被檢測為 **[!UICONTROL Already online]** 如果在建立其他傳送時較早上傳。
* 在部署精靈中，您可以定義未啟用影像偵測的URL:上傳這些影像 **[!UICONTROL Skipped]**.

>[!NOTE]
>
>影像的識別方式為其內容，而非其存取路徑。 這表示先前以不同名稱或不同目錄上傳的影像，將偵測為 **[!UICONTROL Already online]**.

在分析階段，影像會自動上傳至伺服器，以便從外部存取，但必須預先上傳的本機影像除外。

您可以繼續操作並上傳影像，以便其他Adobe Campaign運算子檢視。 如果您能與他人合作，這項功能將會非常實用。 要執行此操作，請按一下 **[!UICONTROL Upload the images straightaway...]** 將影像上傳至伺服器。

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>接著會修改電子郵件中影像的URL，尤其是其名稱。

影像上線後，您可以從 **[!UICONTROL Source]** 標籤。

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

如果您選取 **[!UICONTROL Include the images in the email]**，您可以選擇要包含在對應欄中的影像。

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>如果郵件中包含本地映像，則必須確認對郵件原始碼的更改。

## 插入個人化條碼{#insert-a-barcode}

條碼產生模組可讓您建立符合許多常見標準的數種條碼，包括2D條碼。

可以使用使用客戶條件定義的值以點陣圖形式動態生成條形碼。 電子郵件行銷活動中可包含個人化條碼。 收件者可以列印訊息，並將其顯示給發行公司以進行掃描（例如當結帳時）。

若要將條碼插入電子郵件中，請將游標置於您要顯示該條碼的內容中，然後按一下個人化按鈕。 選取 **[!UICONTROL Include > Barcode...]**。

![](assets/barcode_insert_14.png)

然後設定下列元素以符合您的需求：

1. 選擇條形碼的類型。

   * 若為1D格式，可在Adobe Campaign中使用下列類型：Codabar，代碼128, GS1-128（前身為EAN-128）, UPC-A, UPC-E, ISBN, EAN-8，代碼39，交錯2 of 5, POSTNET和Royal Mail(RM4SCC)。

      1D條形碼的示例：

      ![](assets/barcode_insert_08.png)

   * DataMatrix和PDF417類型與2D格式有關。

      2D條形碼的示例：

      ![](assets/barcode_insert_09.png)

   * 若要插入QR碼，請選取此類型並輸入要套用的糾錯率。 該速率定義了重複資訊的數量和退化的容限。

      ![](assets/barcode_insert_06.png)

      QR碼範例：

      ![](assets/barcode_insert_12.png)

1. 輸入要插入電子郵件的條形碼的大小：配置刻度可以從x1增加或縮小條形碼的大小，從x1增加到x10。
1. 此 **[!UICONTROL Value]** 欄位可讓您定義條碼的值。 值可以符合特殊選件，也可以是條件的函式，也可以是連結至客戶之資料庫欄位的值。

   此示例顯示了EAN-8類型的條形碼，該條形碼已添加到收件者的帳號。 若要新增此帳號，請按一下 **[!UICONTROL Value]** 欄位和選取 **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. 此 **[!UICONTROL Height]** 欄位可讓您變更每個列之間的空間量，以設定條碼的高度，而不變更其寬度。

   根據條碼類型，沒有限制的輸入控制項。 如果條碼值不正確，則只會顯示在 **預覽** 以紅色將條形碼交叉的模式。

   >[!NOTE]
   >
   >分配給條形碼的值取決於其類型。 例如，EAN-8類型應正好有8個數字。
   >
   >位於 **[!UICONTROL Value]** 欄位可讓您除了值本身之外新增資料。 這豐富了條碼，前提是條碼標準接受它。
   >
   >例如，如果您使用GS1-128類型條形碼，並且除了要輸入值之外還要輸入收件人的帳戶號，請按一下個性化按鈕並選擇 **[!UICONTROL Recipient > Account number]**. 如果正確輸入了所選收件人的帳號，則條形碼會將其考慮在內。

設定這些元素後，您就可以完成電子郵件並傳送。 若要避免錯誤，請一律確定您的內容在執行傳送前，按一下 **[!UICONTROL Preview]** 標籤。

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>如果條形碼的值不正確，則其點陣圖會以紅色交叉顯示。

![](assets/barcode_insert_11.png)
