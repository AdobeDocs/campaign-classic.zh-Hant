---
solution: Campaign Classic
product: campaign
title: 個人化區塊
description: 個人化區塊
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: df7c27e763e7e0c02189ed972f33eb03ca2a915f
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 2%

---


# 個人化區塊{#personalization-blocks}

個人化區塊是動態、個人化的，並包含您可插入遞送的特定演算。 例如，您可以新增標誌、問候訊息或鏡像頁面的連結。 請參閱[插入個人化塊](#inserting-personalization-blocks)。

![](assets/do-not-localize/how-to-video.png)[ 在影片中探索此功能](#personalization-blocks-video)

個人化區塊可透過Adobe Campaign檔案總管的&#x200B;**[!UICONTROL Resources > Campaign Management > Personalization blocks]**&#x200B;節點存取。 預設情況下，有幾個塊可用（請參閱[現成可用的個人化塊](#out-of-the-box-personalization-blocks)）。

您可以定義新區塊，以便最佳化傳遞個人化。 有關詳細資訊，請參閱[定義自定義個性化塊](#defining-custom-personalization-blocks)。

>[!NOTE]
>
>個人化區塊也可從&#x200B;**[!UICONTROL Digital Content Editor (DCE)]**&#x200B;取得。 有關詳細資訊，請參見[此頁面](../../web/using/editing-content.md#inserting-a-personalization-block)。

## 插入個人化塊{#inserting-personalization-blocks}

若要在訊息中插入個人化區塊，請遵循下列步驟：

1. 在傳送精靈的內容編輯器中，按一下個人化欄點陣圖示並選取&#x200B;**[!UICONTROL Include]**&#x200B;功能表。
1. 從清單中選擇一個個性化塊（清單顯示10個最後使用的塊），或按一下&#x200B;**[!UICONTROL Other...]**&#x200B;菜單以訪問完整清單。

   ![](assets/s_ncs_user_personalized_block01.png)

1. **[!UICONTROL Other...]**&#x200B;功能表可存取所有現成可用和自訂的個人化區塊（請參閱[現成可用的個人化區塊](#out-of-the-box-personalization-blocks)和[定義自訂的個人化區塊](#defining-custom-personalization-blocks)）。

   ![](assets/s_ncs_user_personalized_block02.png)

1. 然後，將個人化塊作為指令碼插入。 當產生個人化時，它會自動適應收件者描述檔。

   ![](assets/s_ncs_user_personalized_block03.png)

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤，並選取收件者以檢視個人化。

   ![](assets/s_ncs_user_personalized_block04.png)

您可以將個人化區塊的原始碼包含在傳送內容中。 要執行此操作，請在選擇&#x200B;**[!UICONTROL Include the HTML source code of the block]**&#x200B;時選擇它。

![](assets/s_ncs_user_personalized_block05.png)

HTML原始碼會插入傳送內容中。 例如，**[!UICONTROL Greetings]**&#x200B;個人化區塊顯示如下：

![](assets/s_ncs_user_personalized_block06.png)

## 個人化區塊範例{#personalization-blocks-example}

在此範例中，我們建立電子郵件，讓收件者使用個人化區塊來檢視鏡像頁面、在社交網路上分享電子報，以及取消訂閱未來的傳送。

為此，我們需要插入下列個人化區塊：

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>有關鏡像頁生成的詳細資訊，請參閱[生成鏡像頁](../../delivery/using/sending-messages.md#generating-the-mirror-page)。

1. 建立新的傳送，或開啟現有的電子郵件類型傳送。
1. 在傳送精靈中，按一下&#x200B;**[!UICONTROL Subject]**&#x200B;以編輯訊息的主旨並輸入主旨。
1. 將個人化區塊插入訊息內文。 若要這麼做，請按一下訊息內容中的個人化欄點陣圖示，然後選取&#x200B;**[!UICONTROL Include]**&#x200B;功能表。
1. 選擇要插入的第一個塊。 續約程式以包含其他兩個區塊。

   ![](assets/s_ncs_user_personalized_block_example.png)

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤以檢視個人化結果。 您必須選擇收件者，才能顯示該收件者的訊息。

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. 確認塊內容顯示正確。

## 現成可用的個人化區塊{#out-of-the-box-personalization-blocks}

依預設，會提供個人化區塊清單，以協助您個人化訊息的內容。

>[!NOTE]
>
>個人化區塊的清單取決於您實例上已安裝的模組和選項。

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** :插入帶收件者名稱的問候語。範例：「你好，John Doe,」
* **[!UICONTROL Insert logo]** :插入配置實例時已定義的現成標誌。
* **[!UICONTROL Powered by Adobe Campaign]** :插入「Powered by Adobe Campaign」標誌。
* **[!UICONTROL Mirror page URL]** :插入鏡像頁面URL，使「傳送設計人員」可檢查連結。

   >[!NOTE]
   >
   >有關鏡像頁生成的詳細資訊，請參閱[生成鏡像頁](../../delivery/using/sending-messages.md#generating-the-mirror-page)。

* **[!UICONTROL Link to mirror page]** :插入指向鏡像頁的連結：&quot;如果您無法正確檢視此訊息，請按一下這裡&quot;。
* **[!UICONTROL Unsubscription link]** :插入可取消訂閱所有傳送的連結(denylist)。
* **[!UICONTROL Formatting function for proper nouns]** :產生 **[!UICONTROL toSmartCase]** Javascript函式，此函式會將每個字詞的第一個字母變更為大寫。此區塊必須插入傳送的原始碼，並放入&#x200B;**`<script>...</script>`**&#x200B;標籤中。

   在以下範例中，此函式用於將元素&quot;My header&quot;取代為&quot;My new header&quot;，並在每個字詞加上大寫字母：

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** :插入訂閱URL(請參閱 [關於服務和訂閱](../../delivery/using/about-services-and-subscriptions.md))。
* **[!UICONTROL Registration link]** :插入訂閱連結。定義。
* **[!UICONTROL Registration link (with referrer)]** :插入訂閱連結，啟用以識別訪客和傳送。設定例項時已定義連結。

   >[!NOTE]
   >
   >此區塊僅可用於定位訪客的傳送。

* **[!UICONTROL Registration confirmation]** :插入啟用確認訂閱的連結。
* **[!UICONTROL Social network sharing links]** :插入按鈕，讓收件者可與電子郵件用戶端、Facebook、Twitter和LinkedIn共用鏡像頁面內容的連結(請參閱病 [毒式行銷：轉達給朋友](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend))。
* **[!UICONTROL Style of content emails]** 和 **[!UICONTROL Notification style]** :產生程式碼，以預先定義的HTML樣式格式化電子郵件。這些區塊必須插入傳送的原始碼（位於&#x200B;**[!UICONTROL ...]**&#x200B;區段）至&#x200B;**`<style>...</style>`**&#x200B;標籤中。
* **[!UICONTROL Offer acceptance URL in unitary mode]** :插入URL，以將「互動」選件設 **[!UICONTROL Accepted]** 定為( [請參閱](../../interaction/using/offer-analysis-report.md))。

## 定義自訂個人化區塊{#defining-custom-personalization-blocks}

您可以透過&#x200B;**[!UICONTROL Include...]**&#x200B;功能表，從個人化欄點陣圖示定義要插入的新個人化欄位。 這些欄位在個人化區塊中定義。

若要建立個人化區塊，請前往瀏覽器並套用下列步驟：

1. 按一下&#x200B;**[!UICONTROL Resources > Campaign Management > Personalization blocks]**&#x200B;節點。
1. 按一下右鍵塊清單並選擇&#x200B;**[!UICONTROL New]**。
1. 填寫個人化區塊的設定：

   ![](assets/s_ncs_user_personalized_block.png)

   * 輸入塊的標籤。 此標籤將顯示在個人化欄位插入窗口中。
   * 選擇&#x200B;**[!UICONTROL Visible in the customization menus]**&#x200B;可讓此塊從個性化欄位插入表徵圖中訪問。
   * 如有必要，請選取&#x200B;**[!UICONTROL The content of the personalization block depends upon the format]**，為HTML格式和文字格式的電子郵件定義兩個不同的區塊。

      然後，在此編輯器的下部區域（HTML內容和文字內容）中會顯示兩個標籤，以定義對應的內容。

      ![](assets/s_ncs_user_personalized_block_b.png)

   * 輸入內容（在HTML、文字、JavaScript等中） )，然後按一下&#x200B;**[!UICONTROL Save]**。

## 教學課程影片{#personalization-blocks-video}

瞭解如何建立動態內容區塊，以及如何使用這些區塊來個人化您的電子郵件傳送內容。

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

其他Campaign Classic操作視訊可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
