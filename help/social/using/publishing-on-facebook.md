---
solution: Campaign Classic
product: campaign
title: 在 Facebook 上發佈
description: 在 Facebook 上發佈
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 2%

---


# 在 Facebook 上發佈{#publishing-on-facebook}

設定完成後，Social Marketing可讓您在Facebook頁面的塗鴉牆上張貼出版物。

## 限制 {#limitations}

Facebook固有下列限制。

* 訊息不得超過1,000個字元。
* 不支援HTML。

## 建立傳送 {#creating-the-delivery}

使用&#x200B;**[!UICONTROL Publish to a brand page]**&#x200B;傳送範本建立新的傳送。

![](assets/social_facebook_delivery_001.png)

## 選擇主目標{#selecting-the-main-target}

您必須選取要張貼出版物的頁面。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。

   ![](assets/social_facebook_delivery_010.png)

1. 按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/social_facebook_delivery_011.png)

1. 選取 **[!UICONTROL A Facebook page]**。

   ![](assets/social_facebook_delivery_012.png)

1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;欄位中，選取包含Facebook頁面的服務資料夾。 預設情況下，頁面儲存在&#x200B;**[!UICONTROL Facebook]**&#x200B;服務資料夾的根目錄中。 然後選取您要張貼的Facebook頁面。

   ![](assets/social_facebook_delivery_013.png)

## 選擇校對目標{#selecting-the-proof-target}

**[!UICONTROL Target of the proofs]**&#x200B;標籤可讓您定義Facebook頁面，以便在傳出傳送之前測試傳送內容。 我們建議為此目的建立專用的Facebook私人頁面。 如需建立私人Facebook頁面的詳細資訊，請參閱[建立測試Facebook頁面](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)。 要選擇校對目標，請應用與主目標相同的步驟：[選擇主目標](#selecting-the-main-target)。

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>如果您對所有傳送都使用相同的Facebook測試頁面，則可在&#x200B;**[!UICONTROL Publish to a brand page]**&#x200B;傳送範本中儲存校對目標，此範本可透過&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;節點存取。 每個新傳送預設會輸入校對目標。

## 定義對象{#defining-the-audience}

如果您想使用本機區段來調整已授權檢視出版物的公開類型，建議您為每個區段建立一個Facebook頁面(例如：Adobe Campaign Paris、Adobe Campaign London等)。

不過，您也可以使用Facebook使用的對象篩選。 **[!UICONTROL Select target window]**&#x200B;的&#x200B;**[!UICONTROL Audience]**&#x200B;標籤提供4種篩選：

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>小心使用此函式。 在傳送報表中，**[!UICONTROL Number of fans]**&#x200B;指標將不會考慮這些Facebook篩選器。
>
>Facebook可能會變更對象篩選清單及其值。

## 定義消息內容{#defining-message-content}

使用&#x200B;**[!UICONTROL Content type]**&#x200B;下拉式選單選擇出版物類型。

![](assets/social_facebook_delivery_006.png)

可使用下列類型的傳送：

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### 發佈狀態{#publishing-a-status}

狀態類型傳送只能包含文字，如下例所示：

![](assets/social_create_facebook_wall_post_004.png)

在輸入區域中輸入發佈狀態。

![](assets/social_facebook_delivery_015.png)

### 發佈具有{#publishing-a-status-with-a-link}連結的狀態

具有連結的狀態類型傳遞可以包含文本、影像和連結。 下節詳細說明傳送編輯畫面欄位與Facebook上最終出版物之間的對稱性：

![](assets/social_facebook_delivery_007.png)

輸入各個欄位：

>[!IMPORTANT]
>
>所有URL都必須以&#x200B;**&quot;http://&quot;**&#x200B;或&#x200B;**&quot;https://&quot;**&#x200B;開頭。

1. 在&#x200B;**[!UICONTROL Status]**&#x200B;欄位中，輸入將顯示在頁面名稱下的文字。
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;欄位中，輸入出版物標題。
1. 在&#x200B;**[!UICONTROL Link]**&#x200B;欄位中，輸入出版物指向的URL。

   >[!NOTE]
   >
   >如果您想將&#x200B;**[!UICONTROL Link]**&#x200B;欄位新增至Facebook應用程式的URL以進行促銷，建議您將它調整為智慧型手機顯示條件：
   >
   >1. 選擇Facebook應用程式[https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然後選擇&#x200B;**[!UICONTROL Settings > Basic]**&#x200B;標籤。
   >1. 輸入&#x200B;**[!UICONTROL Namespace]**&#x200B;欄位。
   >1. 輸入&#x200B;**[!UICONTROL Mobile Site URL]**&#x200B;欄位：當使用者在智慧型手機上按一下出版物連結時，Facebook會自動將他們重新導向至此欄位中定義的URL。
   >1. 建立您的網路應用程式，讓Facebook顯示器根據使用的裝置（智慧型手機或PC）個人化。
   >1. 前往透過Adobe Campaign主控台發佈的&#x200B;**[!UICONTROL Link]**&#x200B;欄位，輸入&#x200B;**[!UICONTROL Canvas page]**&#x200B;欄位的URL。


1. 在&#x200B;**[!UICONTROL Image]**&#x200B;欄位中，輸入將顯示在出版物左側的影像URL。

   >[!IMPORTANT]
   >
   >這張影像必須裝載在公共網際網站上，Facebook才能上傳。

1. 在&#x200B;**[!UICONTROL Caption]**&#x200B;欄位中，輸入將出現在出版物結尾的文字。
1. 轉至&#x200B;**[!UICONTROL Description]**&#x200B;欄位，並輸入要顯示在標題下的文字。

![](assets/social_facebook_delivery_005.png)

### 使用YouTube連結發佈狀態{#publishing-a-status-with-a-youtube-link}

此類內容可讓您發佈YouTube影片的連結。 就像具有一般連結的狀態，您可以定義狀態、名稱、標題、說明和其他連結。 Facebook會自動新增影像。 傳送編輯畫面欄位與Facebook上最終出版物之間的對稱性詳述如下：

![](assets/social_facebook_delivery_youtube_1.png)

輸入各個欄位：

>[!IMPORTANT]
>
>所有URL都必須以&#x200B;**&quot;http://&quot;**&#x200B;或&#x200B;**&quot;https://&quot;**&#x200B;開頭。

1. 在&#x200B;**[!UICONTROL Status]**&#x200B;欄位中，輸入將顯示在頁面名稱下的文字。
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;欄位中，輸入出版物標題。
1. 在&#x200B;**[!UICONTROL Video code]**&#x200B;欄位中，輸入YouTube影片的程式碼。 例如，對於「https://www.youtube.com/watch?v=abc123456&#39;連結」，視訊程式碼會是「abc123456」。
1. 在&#x200B;**[!UICONTROL Caption]**&#x200B;欄位中，輸入將出現在出版物結尾的文字。
1. 轉至&#x200B;**[!UICONTROL Description]**&#x200B;欄位，並輸入要顯示在標題下的文字。

![](assets/social_facebook_delivery_youtube.png)

### 發佈相簿{#publishing-a-photo-album}

這類內容可讓您發佈相簿。 您可以新增相簿的名稱和說明，以及每張像片的標題。 傳送編輯畫面欄位與Facebook上最終出版物之間的對稱性詳述如下：

![](assets/social_facebook_delivery_photos_1.png)

輸入各個欄位：

1. 首先輸入&#x200B;**[!UICONTROL Album name]**。
1. 然後輸入要顯示在像片上方的&#x200B;**[!UICONTROL Description]**。
1. 若要新增像片，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，選取像片，然後按一下&#x200B;**[!UICONTROL Open]**。
1. 每張像片都可加上註解。

![](assets/social_facebook_delivery_photos.png)

## 預覽{#previewing}

**[!UICONTROL Preview]**&#x200B;標籤可讓您檢視出版物的轉譯。

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;頁籤。
1. 按一下&#x200B;**[!UICONTROL Test personalization]**&#x200B;下拉菜單並選擇&#x200B;**[!UICONTROL Service]**。
1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;欄位中，選取包含您Facebook頁面的服務資料夾。 預設情況下，頁面儲存在&#x200B;**[!UICONTROL Facebook]**&#x200B;服務資料夾的根目錄中。
1. 選取您要測試預覽的Facebook頁面。

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>預覽可能與最終的Facebook出版物稍有不同。 我們強烈建議在最終傳送前傳送證明，以精確呈現出版物。 請參閱[傳送證明](#sending-the-proof)。

## 設定追蹤{#configuring-tracking}

您可以在傳送報表和傳送與服務的&#x200B;**[!UICONTROL Edit > Tracking]**&#x200B;標籤中檢視追蹤。

Adobe Campaign會測量傳送中所含URL的點按次數。 Facebook會測量&#x200B;**[!UICONTROL Like]**&#x200B;按鈕的點按次數、留言數和粉絲數。

追蹤設定與電子郵件傳送的設定相同。 如需詳細資訊，請參閱[本章節](../../delivery/using/about-delivery-monitoring.md)。

>[!NOTE]
>
>在&#x200B;**[!UICONTROL Publish to a brand page]**&#x200B;傳送範本中，預設會啟用追蹤。

## 傳送證明{#sending-the-proof}

我們強烈建議您在最終傳送之前傳送出版物證明，以便在私人Facebook測試頁面上檢視出版物的精確呈現。 如需建立私人Facebook測試頁面的詳細資訊，請參閱「建立測試Facebook頁面](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)」。 [選擇目標校對的步驟在[選擇校對目標](#selecting-the-proof-target)中有詳細說明。

證明傳送與電子郵件傳送相同。 請參閱[本區段](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

## 發送消息{#sending-the-message}

1. 核准內容後，按一下&#x200B;**[!UICONTROL Send]**&#x200B;按鈕。
1. 選擇&#x200B;**[!UICONTROL Deliver as soon as possible]**&#x200B;並按一下&#x200B;**[!UICONTROL Analyze]**&#x200B;按鈕。

   >[!NOTE]
   >
   >**[!UICONTROL Postpone the delivery]**&#x200B;選項可讓您將傳送延遲至稍後的日期。

   ![](assets/social_facebook_delivery_009.png)

1. 分析完成後，檢查結果。
1. 按一下&#x200B;**[!UICONTROL Confirm delivery]** ，然後按一下&#x200B;**[!UICONTROL Yes]**。

   ![](assets/social_facebook_delivery_016.png)

