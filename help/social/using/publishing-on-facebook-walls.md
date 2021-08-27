---
product: campaign
title: 在 Facebook 塗鴉牆上發佈
description: 在 Facebook 塗鴉牆上發佈
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 3%

---

# 在 Facebook 塗鴉牆上發佈{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

為了讓Adobe Campaign能夠將出版物傳送至Facebook塗鴉牆，您需要將這些頁面的寫入存取權委派給Adobe Campaign。 這包括下列設定步驟：

1. 使用一或多個頁面建立Facebook帳戶。
1. 建立用於傳送校樣的測試Facebook頁面。
1. 建立 Facebook 應用程式.
1. 在&#x200B;**[!UICONTROL Facebook routing]**&#x200B;外部帳戶的Adobe Campaign中輸入Facebook應用程式設定。

## 先決條件 {#prerequisites}

首先，請建立Facebook帳戶和數個頁面：這些將用於發送出版物。

* 若要建立Facebook帳戶，請使用[https://www.facebook.com](https://www.facebook.com)連結。
* 若要建立Facebook頁面，請使用[https://www.facebook.com/pages/create](https://www.facebook.com/pages/create)連結。

   建議您使用相同的Facebook帳戶管理所有頁面。 這樣，您只需要一個Facebook應用程式和一個外部帳戶，即可在帳戶的所有頁面上寫入。

   ![](assets/social_diagram_fb_external_account.png)

## 建立測試Facebook頁面 {#creating-a-test-facebook-page}

建議您建立私人Facebook頁面以傳送發佈校樣(如需詳細資訊，請參閱[傳送校樣](../../social/using/publishing-on-facebook.md#sending-the-proof)。

1. 登入您用來管理頁面的Facebook帳戶。
1. 建立新的Facebook頁面。
1. 按一下右上角的&#x200B;**[!UICONTROL Settings]**&#x200B;按鈕。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，修改頁面的可見性參數：勾選&#x200B;**[!UICONTROL Page unpublished]**&#x200B;方塊。
1. 按一下 **[!UICONTROL Save Changes]** 按鈕。

![](assets/social_facebook_test_page.png)

## 建立 Facebook 應用程式 {#creating-a-facebook-application}

為了讓Adobe Campaign能夠在您頁面的塗鴉牆上發佈，您需要建立Facebook應用程式。 若要這麼做，請套用下列步驟：

1. 登入您用來管理頁面的Facebook帳戶。
1. 在您的瀏覽器中輸入下列地址：[https://developers.facebook.com/apps](https://developers.facebook.com/apps)。

   >[!IMPORTANT]
   >
   >根據您擁有的帳戶類型，可能需要一個或多個授權。
   >
   >若要建立Facebook應用程式，您需要&#x200B;**verified** Facebook帳戶。

1. 按一下頁面右上角的&#x200B;**[!UICONTROL Add a New App]**&#x200B;按鈕。 輸入應用程式名稱和聯絡人電子郵件，然後傳遞安全性檢查。

   ![](assets/social_create_facebook_app_002.png)

1. 在&#x200B;**[!UICONTROL Settings > Basic]**&#x200B;下，按一下&#x200B;**[!UICONTROL Add a platform]**&#x200B;並選擇&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;類型。

   ![](assets/social_create_facebook_app_003.png)

1. 在&#x200B;**[!UICONTROL Products]**&#x200B;區段的左側功能表中，檢查您是否看到&#x200B;**[!UICONTROL Facebook Login]**&#x200B;產品。 如果沒有，請添加新產品並選擇&#x200B;**[!UICONTROL Facebook Login]**。

   ![](assets/social_create_facebook_app_003bis.png)

1. 建立應用程式後，選取&#x200B;**[!UICONTROL App Review]**&#x200B;標籤並發佈應用程式。

   ![](assets/social_create_facebook_app_004.png)

## 委派寫入存取權至Adobe Campaign {#delegating-write-access-to-adobe-campaign}

若要委派Adobe Campaign的寫入存取權以張貼至頁面的塗鴉牆上，您必須輸入先前建立之Facebook應用程式的參數。

此步驟需要同時存取您的Adobe Campaign主控台和登入Facebook帳戶（您用於頁面管理）的網際網路瀏覽器：

>[!IMPORTANT]
>
>Adobe Campaign運算子必須擁有執行此設定的管理權限。

* **Facebook**:選取先前建立的應用程 [式(https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然後選取 **[!UICONTROL Settings > Basic]** 索引標籤。

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >如果未顯示&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;部分，請按一下位於頁面底部的&#x200B;**[!UICONTROL Add Platform]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**:轉到樹 **[!UICONTROL Administration > Platform > External Accounts]** 的節點，選擇外部帳 **[!UICONTROL Facebook routing]** 戶，然後按一下 **[!UICONTROL Connector]** 頁簽。

   ![](assets/social_facebook_external_account_001.png)

1. 在Adobe Campaign主控台中，複製&#x200B;**[!UICONTROL Secure Canvas URL]**&#x200B;欄位中包含的位址，並貼到Facebook上的&#x200B;**[!UICONTROL Secure Web Games URL (https)]**&#x200B;欄位（位於&#x200B;**[!UICONTROL Facebook Web Games]**&#x200B;區段中）。

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >您在任何情況下都不得使用不安全的URL。

   複製此URL並貼到&#x200B;**[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**&#x200B;下。 若要檢查URL的有效性，請儲存應用程式，複製URL並貼到&#x200B;**[!UICONTROL Redirect URI to Check]**&#x200B;欄位中，然後按一下&#x200B;**[!UICONTROL Check URI]**。

   ![](assets/social_facebook_external_account_007bis.png)

1. 在Facebook上，複製&#x200B;**[!UICONTROL App ID]**&#x200B;和&#x200B;**[!UICONTROL App Secret]**&#x200B;欄位的內容，並貼到主控台的相符欄位中。

   ![](assets/social_facebook_external_account_007.png)

1. 在Facebook上，按一下頁面底部的&#x200B;**[!UICONTROL Save Changes]**&#x200B;按鈕。
1. 前往Adobe Campaign主控台，儲存外部帳戶。

   >[!NOTE]
   >
   >**[!UICONTROL Marketing URL]**&#x200B;欄位為可選。

1. 在Adobe Campaign主控台中，按一下&#x200B;**[!UICONTROL Connector]**&#x200B;標籤底部的&#x200B;**[!UICONTROL Request the authorization from the application]**&#x200B;連結。 會自動觸發&#x200B;**[!UICONTROL Synchronize Facebook pages]**&#x200B;工作流程，並收集管理員管理的所有Facebook頁面。 有關詳細資訊，請參閱[同步Facebook頁面](#synchronizing-facebook-pages)。

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >預設情況下，頁面會新增至&#x200B;**[!UICONTROL Facebook]**&#x200B;服務資料夾，可透過&#x200B;**[!UICONTROL Profiles and Targets > Services and Subscriptions]**&#x200B;節點使用。 **[!UICONTROL Connector]**&#x200B;標籤的&#x200B;**[!UICONTROL Folder]**&#x200B;欄位可讓您變更同步後建立Facebook頁面的服務資料夾。 您也可以利用&#x200B;**[!UICONTROL Filter]**&#x200B;欄位，選取要在Adobe Campaign中同步的Facebook頁面。 如果將此欄位留空，管理員管理的所有Facebook頁面都會同步。

1. 隨即顯示對話方塊，其中包含各種Facebook權限設定。 這可讓Adobe Campaign將出版物傳送至Facebook帳戶頁面。

   接受各種權限要求。

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign有權在Facebook帳戶頁面的塗鴉牆上發佈。

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>如果Facebook帳戶管理數個頁面，只需設定一個外部帳戶，以便在Facebook帳戶的任何頁面上寫入即可。 對於每個新的Facebook帳戶，您需要建立新的&#x200B;**[!UICONTROL Routing]**&#x200B;類型外部帳戶。

**[!UICONTROL Synchronization of Facebook pages]**&#x200B;工作流程會同步由Facebook帳戶管理的所有頁面，讓您透過Adobe Campaign直接張貼在其塗鴉牆上。 有關詳細資訊，請參閱[同步Facebook頁面](#synchronizing-facebook-pages)。

## 同步Facebook頁面 {#synchronizing-facebook-pages}

透過&#x200B;**[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**&#x200B;節點存取的&#x200B;**[!UICONTROL Synchronization of Facebook pages]**&#x200B;工作流程可讓您同步(在Adobe Campaign中)先前設定之Facebook帳戶的頁面。 預設情況下，此工作流配置為每天或每當管理員按一下服務配置螢幕中的&#x200B;**[!UICONTROL Request an authorization from the application]**&#x200B;連結時運行一次(請參閱[將寫訪問權委派到Adobe Campaign](#delegating-write-access-to-adobe-campaign))。

同步完成後，收集的頁面會顯示在外部帳戶中輸入的服務資料夾中(請參閱[委派對Adobe Campaign](#delegating-write-access-to-adobe-campaign)的寫入存取)。 預設情況下，頁面會新增至&#x200B;**[!UICONTROL Facebook]**&#x200B;服務資料夾的根目錄，該資料夾可透過&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;功能表取得。

![](assets/social_facebook_service_002.png)

您現在可以直接透過Adobe Campaign在Facebook頁面的塗鴉牆上發佈。 如需詳細資訊，請參閱[在Facebook上發佈](#publishing-on-facebook-walls)。
