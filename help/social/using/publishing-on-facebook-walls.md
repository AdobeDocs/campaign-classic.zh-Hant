---
solution: Campaign Classic
product: campaign
title: 在 Facebook 塗鴉牆上發佈
description: 在 Facebook 塗鴉牆上發佈
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 2%

---


# 在 Facebook 塗鴉牆上發佈{#publishing-on-facebook-walls}

為了讓Adobe Campaign能夠將出版品傳送至Facebook塗鴉牆，您必須將這些頁面的寫入存取權委派給Adobe Campaign。 這包括下列設定步驟：

1. 建立包含一或多個頁面的Facebook帳戶。
1. 建立測試Facebook頁面，以傳送校樣。
1. 建立Facebook應用程式。
1. 在&#x200B;**[!UICONTROL Facebook routing]**&#x200B;外部帳戶的Adobe Campaign中輸入Facebook應用程式設定。

## 必要條件 {#prerequisites}

首先，建立Facebook帳戶和數個頁面：這些將用於發送發佈。

* 若要建立Facebook帳戶，請使用[https://www.facebook.com](https://www.facebook.com)連結。
* 若要建立Facebook頁面，請使用[https://www.facebook.com/pages/create](https://www.facebook.com/pages/create)連結。

   我們建議使用相同的Facebook帳戶來管理您的所有頁面。 如此，您只需要一個Facebook應用程式和一個外部帳戶，即可在帳戶的所有頁面上寫入。

   ![](assets/social_diagram_fb_external_account.png)

## 建立測試Facebook頁面{#creating-a-test-facebook-page}

我們建議建立私人Facebook頁面以傳送出版物校訂(如需詳細資訊，請參閱[傳送證明](../../social/using/publishing-on-facebook.md#sending-the-proof)。

1. 登入您用來管理頁面的Facebook帳戶。
1. 建立新的Facebook頁面。
1. 按一下右上角的&#x200B;**[!UICONTROL Settings]**&#x200B;按鈕。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，修改頁面的可見性參數：選中&#x200B;**[!UICONTROL Page unpublished]**&#x200B;框。
1. 按一下 **[!UICONTROL Save Changes]** 按鈕。

![](assets/social_facebook_test_page.png)

## 建立 Facebook 應用程式 {#creating-a-facebook-application}

為了讓Adobe Campaign能夠在您頁面的塗鴉牆上發佈，您需要建立Facebook應用程式。 若要這麼做，請套用下列步驟：

1. 登入您用來管理頁面的Facebook帳戶。
1. 在您的瀏覽器中輸入下列位址：[https://developers.facebook.com/apps](https://developers.facebook.com/apps)。

   >[!IMPORTANT]
   >
   >視您擁有的帳戶類型而定，可能需要一或多個授權。
   >
   >若要建立Facebook應用程式，您需要&#x200B;**verified** Facebook帳戶。

1. 按一下頁面右上角的&#x200B;**[!UICONTROL Add a New App]**&#x200B;按鈕。 輸入應用程式名稱和聯絡人電子郵件，然後通過安全性檢查。

   ![](assets/social_create_facebook_app_002.png)

1. 在&#x200B;**[!UICONTROL Settings > Basic]**&#x200B;下，按一下&#x200B;**[!UICONTROL Add a platform]**&#x200B;並選擇&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;類型。

   ![](assets/social_create_facebook_app_003.png)

1. 在&#x200B;**[!UICONTROL Products]**&#x200B;區段的左側功能表中，檢查您是否看到&#x200B;**[!UICONTROL Facebook Login]**&#x200B;產品。 否則，請添加新產品並選擇&#x200B;**[!UICONTROL Facebook Login]**。

   ![](assets/social_create_facebook_app_003bis.png)

1. 建立應用程式後，請選取&#x200B;**[!UICONTROL App Review]**&#x200B;標籤並發佈應用程式。

   ![](assets/social_create_facebook_app_004.png)

## 委派Adobe Campaign的寫入存取權{#delegating-write-access-to-adobe-campaign}

若要委派Adobe Campaign的寫入存取權，以便張貼在頁面的塗鴉牆上，您必須輸入先前建立之Facebook應用程式的參數。

此步驟需要存取您的Adobe Campaign主控台和登入您用於頁面管理的Facebook帳戶的網際網路瀏覽器：

>[!IMPORTANT]
>
>Adobe Campaign營運商必須擁有管理權限才能執行此設定。

* **Facebook**:選擇先前建立的應用程式( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然後選擇該 **[!UICONTROL Settings > Basic]** 頁籤。

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >如果未顯示&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;部分，請按一下頁面底部的&#x200B;**[!UICONTROL Add Platform]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**:轉至樹 **[!UICONTROL Administration > Platform > External Accounts]** 的節點，選擇外 **[!UICONTROL Facebook routing]** 部帳戶並按一下選 **[!UICONTROL Connector]** 項卡。

   ![](assets/social_facebook_external_account_001.png)

1. 在Adobe Campaign主控台中，複製&#x200B;**[!UICONTROL Secure Canvas URL]**&#x200B;欄位中包含的位址，並貼入Facebook上的&#x200B;**[!UICONTROL Secure Web Games URL (https)]**&#x200B;欄位（位於&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;區段）。

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >您不得在任何情況下使用不安全的URL。

   此URL也會複製並貼在&#x200B;**[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**&#x200B;下。 若要檢查URL的有效性，請儲存應用程式，複製並貼上&#x200B;**[!UICONTROL Redirect URI to Check]**&#x200B;欄位中的URL，然後按一下&#x200B;**[!UICONTROL Check URI]**。

   ![](assets/social_facebook_external_account_007bis.png)

1. 在Facebook上，複製&#x200B;**[!UICONTROL App ID]**&#x200B;和&#x200B;**[!UICONTROL App Secret]**&#x200B;欄位的內容，並貼到主控台的相符欄位中。

   ![](assets/social_facebook_external_account_007.png)

1. 在Facebook上，按一下頁面底部的&#x200B;**[!UICONTROL Save Changes]**&#x200B;按鈕。
1. 前往Adobe Campaign主控台，儲存外部帳戶。

   >[!NOTE]
   >
   >**[!UICONTROL Marketing URL]**&#x200B;欄位為選用。

1. 在Adobe Campaign主控台中，按一下&#x200B;**[!UICONTROL Connector]**&#x200B;標籤底部的&#x200B;**[!UICONTROL Request the authorization from the application]**&#x200B;連結。 系統會自動觸發&#x200B;**[!UICONTROL Synchronize Facebook pages]**&#x200B;工作流程，並收集管理員管理的所有Facebook頁面。 如需詳細資訊，請參閱「同步Facebook頁面」[。](#synchronizing-facebook-pages)

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >預設情況下，頁面會添加到&#x200B;**[!UICONTROL Facebook]**&#x200B;服務資料夾中，可通過&#x200B;**[!UICONTROL Profiles and Targets > Services and Subscriptions]**&#x200B;節點獲得。 **[!UICONTROL Connector]**&#x200B;標籤的&#x200B;**[!UICONTROL Folder]**&#x200B;欄位可讓您變更同步後在Facebook頁面中建立的服務資料夾。 您也可以在Adobe Campaign中選取要同步的Facebook頁面，這要歸功於&#x200B;**[!UICONTROL Filter]**&#x200B;欄位。 如果您將此欄位留空，管理員管理的所有Facebook頁面都會同步化。

1. 會顯示一個對話方塊，其中包含各種Facebook權限設定。 這些功能可讓Adobe Campaign將出版物傳送至Facebook帳戶頁面。

   接受各種權限要求。

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign已獲得在Facebook帳戶頁面的塗鴉牆上發佈的權利。

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>如果Facebook帳戶管理數個頁面，只需設定一個外部帳戶，以便在Facebook帳戶的任何頁面上寫入。 對於每個新的Facebook帳戶，您需要建立新&#x200B;**[!UICONTROL Routing]**&#x200B;類型的外部帳戶。

**[!UICONTROL Synchronization of Facebook pages]**&#x200B;工作流程會同步Facebook帳戶管理的所有頁面，讓您直接透過Adobe Campaign在其塗鴉牆上張貼。 如需詳細資訊，請參閱「同步Facebook頁面」[。](#synchronizing-facebook-pages)

## 同步Facebook頁面{#synchronizing-facebook-pages}

透過&#x200B;**[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**&#x200B;節點存取的&#x200B;**[!UICONTROL Synchronization of Facebook pages]**&#x200B;工作流程可讓您同步（在Adobe Campaign中）先前設定之Facebook帳戶的頁面。 依預設，此工作流程設定為每天執行一次，或當管理員按一下服務設定畫面中的&#x200B;**[!UICONTROL Request an authorization from the application]**&#x200B;連結時（請參閱[委派Adobe Campaign的寫入存取權](#delegating-write-access-to-adobe-campaign)）。

同步完成後，收集的頁面會顯示在外部帳戶中輸入的服務資料夾中（請參閱[委派Adobe Campaign的寫入存取權](#delegating-write-access-to-adobe-campaign)）。 預設情況下，頁面會添加到&#x200B;**[!UICONTROL Facebook]**&#x200B;服務資料夾的根目錄中，該資料夾可通過&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;菜單使用。

![](assets/social_facebook_service_002.png)

您現在可以直接透過Adobe Campaign在Facebook頁面的塗鴉牆上發佈。 如需詳細資訊，請參閱「在Facebook上發佈」。[](#publishing-on-facebook-walls)
