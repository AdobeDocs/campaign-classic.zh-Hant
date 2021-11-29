---
product: campaign
title: 在 Facebook 上發佈
description: 了解如何在Facebook上發佈
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: 84d6cb2e-c7f9-43d7-a98c-22613d456193
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 3%

---

# 在 Facebook 上發佈{#publishing-on-facebook}

![](../../assets/v7-only.svg)

完成設定後， Social Marketing可讓您將出版物張貼在Facebook頁面的塗鴉牆上。

## 限制 {#limitations}

facebook固有下列限制。

* 訊息不得超過1,000個字元。
* 不支援HTML。

## 建立傳送 {#creating-the-delivery}

使用 **[!UICONTROL Publish to a brand page]** 傳遞範本。

![](assets/social_facebook_delivery_001.png)

## 選取主要目標 {#selecting-the-main-target}

您需要選取要張貼出版物的頁面。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;連結。

   ![](assets/social_facebook_delivery_010.png)

1. 按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/social_facebook_delivery_011.png)

1. 選取 **[!UICONTROL A Facebook page]**。

   ![](assets/social_facebook_delivery_012.png)

1. 在 **[!UICONTROL Folder]** 欄位中，選擇包含「Facebook」頁的服務資料夾。 依預設，頁面會儲存在 **[!UICONTROL Facebook]** 服務資料夾。 然後選取您要張貼的Facebook頁面。

   ![](assets/social_facebook_delivery_013.png)

## 選取校樣目標 {#selecting-the-proof-target}

此 **[!UICONTROL Target of the proofs]** 索引標籤可讓您定義Facebook頁面，以便在將傳送傳出之前測試傳送。 為此，建議您建立專用的Facebook私人頁面。 如需建立私人Facebook頁面的詳細資訊，請參閱 [本頁](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). 若要選取校樣目標，請套用與主要目標相同的步驟。 [了解更多](#selecting-the-main-target)

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>如果您對所有傳送使用相同的Facebook測試頁面，您可以在 **[!UICONTROL Publish to a brand page]** 傳遞範本，可透過 **[!UICONTROL Resources > Templates > Delivery templates]** 節點。 預設會為每個新傳送輸入校樣目標。

## 定義對象 {#defining-the-audience}

如果您想使用本機區段來調整已授權檢視出版物的公開類型，建議您為每個區段建立一個Facebook頁面(例如：Adobe Campaign巴黎、Adobe Campaign倫敦等)。

不過，您也可以使用Facebook使用的對象篩選條件。 此 **[!UICONTROL Audience]** 的 **[!UICONTROL Select target window]** 提供四個篩選器：

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!CAUTION]
>
>請謹慎使用此函式。 在傳送報表中， **[!UICONTROL Number of fans]** 指標不會將這些Facebook篩選器納入考量。
>
>Facebook可能會變更對象篩選器清單及其值。

## 定義訊息內容 {#defining-message-content}

使用 **[!UICONTROL Content type]** 下拉式功能表。

![](assets/social_facebook_delivery_006.png)

可使用下列類型的傳送：

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### 發佈狀態 {#publishing-a-status}

狀態類型傳送只能包含文字，如下列範例所示：

![](assets/social_create_facebook_wall_post_004.png)

在輸入區域中輸入發佈狀態。

![](assets/social_facebook_delivery_015.png)

### 發佈包含連結的狀態 {#publishing-a-status-with-a-link}

具有連結的狀態類型傳遞可包含文字、影像和連結。 下節詳細說明傳送編輯畫面欄位與Facebook上最終發佈之間的對稱性：

![](assets/social_facebook_delivery_007.png)

輸入各種欄位：

>[!CAUTION]
>
>所有URL都必須以開頭 **&quot;http://&quot;** 或 **&quot;https://&quot;**.

1. 在 **[!UICONTROL Status]** 欄位中，輸入將在頁面名稱下顯示的文字。
1. 在 **[!UICONTROL Name]** 欄位，輸入發佈標題。
1. 在 **[!UICONTROL Link]** 欄位，輸入發佈指向的URL。

   >[!NOTE]
   >
   >如果您想要新增 **[!UICONTROL Link]** 欄位至Facebook應用程式的URL以進行促銷，建議您將其調整為符合智慧手機顯示條件：
   >
   >1. 選取Facebook應用程式 [https://developers.facebook.com/apps](https://developers.facebook.com/apps)，然後選取 **[!UICONTROL Settings > Basic]** 標籤。
   >1. 輸入 **[!UICONTROL Namespace]** 欄位。
   >1. 輸入 **[!UICONTROL Mobile Site URL]** 欄位：當使用者按一下智慧型手機上的發佈連結時，Facebook會自動將他們重新導向至此欄位中定義的URL。
   >1. 建立您的Web應用程式，讓Facebook顯示器根據所使用裝置（智慧型手機或PC）的功能個人化。
   >1. 前往 **[!UICONTROL Link]** 欄位(透過Adobe Campaign主控台)，輸入 **[!UICONTROL Canvas page]** 欄位。


1. 在 **[!UICONTROL Image]** 欄位中，輸入要顯示在發佈左側的影像URL。

   >[!CAUTION]
   >
   >影像必須托管於公開網際網路網站，Facebook才能上傳。

1. 在 **[!UICONTROL Caption]** 欄位中，輸入要出現在發佈結尾的文字。
1. 前往 **[!UICONTROL Description]** 欄位，然後輸入要在標題下顯示的文字。

![](assets/social_facebook_delivery_005.png)

### 使用YouTube連結發佈狀態 {#publishing-a-status-with-a-youtube-link}

此類內容可讓您發佈YouTube影片的連結。 就像具有一般連結的狀態一樣，您可以定義狀態、名稱、註解、說明和其他連結。 影像由Facebook自動新增。 傳遞編輯螢幕的欄位與Facebook上最終出版物之間的對稱性詳述如下：

![](assets/social_facebook_delivery_youtube_1.png)

輸入各種欄位：

>[!CAUTION]
>
>所有URL都必須以開頭 **&quot;http://&quot;** 或 **&quot;https://&quot;**.

1. 在 **[!UICONTROL Status]** 欄位中，輸入將在頁面名稱下顯示的文字。
1. 在 **[!UICONTROL Name]** 欄位，輸入發佈標題。
1. 在 **[!UICONTROL Video code]** 欄位，輸入YouTube影片的程式碼。 例如，對於&#39;https://www.youtube.com/watch?v=abc123456&#39;連結，視訊程式碼為&#39;abc123456&#39;。
1. 在 **[!UICONTROL Caption]** 欄位中，輸入要出現在發佈結尾的文字。
1. 前往 **[!UICONTROL Description]** 欄位，然後輸入要在標題下顯示的文字。

![](assets/social_facebook_delivery_youtube.png)

### 發佈相簿 {#publishing-a-photo-album}

這類內容可讓您發佈相簿。 您可以新增相簿的名稱和說明，以及每張像片的註解。 傳遞編輯螢幕的欄位與Facebook上最終出版物之間的對稱性詳述如下：

![](assets/social_facebook_delivery_photos_1.png)

輸入各種欄位：

1. 從輸入 **[!UICONTROL Album name]**.
1. 然後輸入 **[!UICONTROL Description]** 顯示在照片上方。
1. 若要新增像片，請按一下 **[!UICONTROL Add]** 按鈕，選擇照片並按一下 **[!UICONTROL Open]**.
1. 每張像片都可新增註解。

![](assets/social_facebook_delivery_photos.png)

## 預覽 {#previewing}

此 **[!UICONTROL Preview]** 索引標籤可讓您檢視出版物的轉譯。

1. 按一下 **[!UICONTROL Preview]** 標籤。
1. 按一下 **[!UICONTROL Test personalization]** 下拉式功能表，然後選取 **[!UICONTROL Service]**.
1. 在 **[!UICONTROL Folder]** 欄位中，選取包含Facebook頁面的服務資料夾。 依預設，頁面會儲存在 **[!UICONTROL Facebook]** 服務資料夾。
1. 選取您要測試預覽的Facebook頁面。

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>預覽可能會與最終的Facebook出版物稍有不同。 我們強烈建議在最終傳送前傳送校樣，以精確轉譯發佈。 [深入瞭解](#sending-the-proof)。

## 設定追蹤 {#configuring-tracking}

追蹤可在傳送報表和 **[!UICONTROL Edit > Tracking]** 標籤。

傳送中所含URL的點按次數由Adobe Campaign測量。 點擊次數 **[!UICONTROL Like]** 按鈕、留言數和粉絲數由Facebook測量。

追蹤設定與電子郵件傳送的相同。 如需詳細資訊，請參閱[本章節](../../delivery/using/about-delivery-monitoring.md)。

>[!NOTE]
>
>在 **[!UICONTROL Publish to a brand page]** 傳送範本，預設會啟用追蹤。

## 傳送校樣 {#sending-the-proof}

我們強烈建議您在最終傳送前傳送出版物的校樣，以在私人Facebook測試頁面上檢視出版物的確切轉譯。 如需建立私人Facebook測試頁面的詳細資訊，請參閱 [本頁](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). 選取目標校樣的步驟在 [本節](#selecting-the-proof-target).

校樣傳送與電子郵件傳送相同。 請參閱[本節](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

## 傳送訊息 {#sending-the-message}

1. 內容核准後，按一下 **[!UICONTROL Send]** 按鈕。
1. 選擇 **[!UICONTROL Deliver as soon as possible]** 並按一下 **[!UICONTROL Analyze]** 按鈕。

   >[!NOTE]
   >
   >此 **[!UICONTROL Postpone the delivery]** 選項可讓您將傳送延遲至之後的日期。

   ![](assets/social_facebook_delivery_009.png)

1. 分析完成後，檢查結果。
1. 按一下 **[!UICONTROL Confirm delivery]**，然後按一下 **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)
