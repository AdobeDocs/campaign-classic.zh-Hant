---
title: 在Facebook塗鴉牆上發佈
seo-title: 在Facebook塗鴉牆上發佈
description: 在Facebook塗鴉牆上發佈
seo-description: null
page-status-flag: never-activated
uuid: 02288473-a0d7-42b5-9f86-3c96550ab1a8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 8577db0b-f1fc-41af-aa0f-ec4d02dac376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0386ae88a1b4d9ebda64283d874e01b14e9e5af4
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---


# 在Facebook塗鴉牆上發佈{#publishing-on-facebook-walls}

為了讓Adobe Campaign能夠將出版品傳送至Facebook塗鴉牆，您必須將這些頁面的寫入存取權委派給Adobe Campaign。 這包括下列設定步驟：

1. 建立包含一或多個頁面的Facebook帳戶。
1. 建立測試Facebook頁面，以傳送校樣。
1. 建立Facebook應用程式。
1. 在外部帳戶的Adobe Campaign中輸入Facebook應用程式 **[!UICONTROL Facebook routing]** 設定。

## 必要條件 {#prerequisites}

首先，建立Facebook帳戶和數個頁面： 這些將用於發送發佈。

* 若要建立Facebook帳戶，請使用https://www.facebook.com [連結](https://www.facebook.com) 。
* 若要建立Facebook頁面，請使用https://www.facebook.com/pages/create [連結](https://www.facebook.com/pages/create) 。

   我們建議使用相同的Facebook帳戶來管理您的所有頁面。 如此，您只需要一個Facebook應用程式和一個外部帳戶，即可在帳戶的所有頁面上寫入。

   ![](assets/social_diagram_fb_external_account.png)

## 建立測試Facebook頁面 {#creating-a-test-facebook-page}

我們建議建立私人Facebook頁面以傳送出版物校樣(如需詳細資訊，請參 [閱傳送校樣](../../social/using/publishing-on-facebook.md#sending-the-proof)。

1. 登入您用來管理頁面的Facebook帳戶。
1. 建立新的Facebook頁面。
1. 按一下 **[!UICONTROL Settings]** 右上角的按鈕。
1. 在標籤 **[!UICONTROL General]** 中，修改頁面的可見性參數： 複選框 **[!UICONTROL Page unpublished]** 時。
1. 按一下&#x200B;**[!UICONTROL Save Changes]**&#x200B;按鈕。

![](assets/social_facebook_test_page.png)

## 建立Facebook應用程式 {#creating-a-facebook-application}

為了讓Adobe Campaign能夠在您頁面的塗鴉牆上發佈，您需要建立Facebook應用程式。 若要這麼做，請套用下列步驟：

1. 登入您用來管理頁面的Facebook帳戶。
1. 在您的瀏覽器中輸入下列位址： [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >視您擁有的帳戶類型而定，可能需要一或多個授權。
   >
   >若要建立Facebook應用程式，您需要經過驗證 **的** Facebook帳戶。

1. 按一 **[!UICONTROL Add a New App]** 下頁面右上角的按鈕。 輸入應用程式名稱和聯絡人電子郵件，然後通過安全性檢查。

   ![](assets/social_create_facebook_app_002.png)

1. 在下 **[!UICONTROL Settings > Basic]**&#x200B;面，單 **[!UICONTROL Add a platform]** 擊並選擇 **[!UICONTROL Facebook Web Games]** 類型。

   ![](assets/social_create_facebook_app_003.png)

1. 在左 **[!UICONTROL Products]** 側功能表的區段中，檢查您是否看到產 **[!UICONTROL Facebook Login]** 品。 否則，請新增產品並選取 **[!UICONTROL Facebook Login]**。

   ![](assets/social_create_facebook_app_003bis.png)

1. 建立應用程式後，請選取標 **[!UICONTROL App Review]** 簽並發佈應用程式。

   ![](assets/social_create_facebook_app_004.png)

## 委派Adobe Campaign的寫入存取權 {#delegating-write-access-to-adobe-campaign}

若要委派Adobe Campaign的寫入存取權，以便張貼在頁面的塗鴉牆上，您必須輸入先前建立之Facebook應用程式的參數。

此步驟需要存取您的Adobe Campaign主控台和登入您用於頁面管理的Facebook帳戶的網際網路瀏覽器：

>[!IMPORTANT]
>
>Adobe Campaign營運商必須擁有管理權限才能執行此設定。

* **Facebook**: 選擇先前建立的應用程式( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然後選擇該 **[!UICONTROL Settings > Basic]** 頁籤。

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >如果未 **[!UICONTROL Facebook Web Games]** 出現區段，請按一 **[!UICONTROL Add Platform]** 下頁面底部的按鈕，然後選取 **[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**: 轉至樹 **[!UICONTROL Administration > Platform > External Accounts]** 的節點，選擇外部帳 **[!UICONTROL Facebook routing]** 戶並按一下選 **[!UICONTROL Connector]** 項卡。

   ![](assets/social_facebook_external_account_001.png)

1. 在Adobe Campaign主控台中，複製欄位中包含的位 **[!UICONTROL Secure Canvas URL]** 址並貼入Facebook( **[!UICONTROL Secure Web Games URL (https)]** 區段中)的 **[!UICONTROL Facebook Web Games]** 欄位。

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >您不得在任何情況下使用不安全的URL。

   複製並貼上此URL，也 **[!UICONTROL Products]** 在> **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** >下 **[!UICONTROL Valid OAuth Redirect URIs]**。 若要檢查URL的有效性，請儲存應用程式，複製並貼入欄位中的URL, **[!UICONTROL Redirect URI to Check]** 然後按一下 **[!UICONTROL Check URI]**。

   ![](assets/social_facebook_external_account_007bis.png)

1. 在Facebook上，複製和欄位 **[!UICONTROL App ID]** 的內 **[!UICONTROL App Secret]** 容，並貼到主控台的相符欄位。

   ![](assets/social_facebook_external_account_007.png)

1. 在Facebook上，按一 **[!UICONTROL Save Changes]** 下頁面底部的按鈕。
1. 前往Adobe Campaign主控台，儲存外部帳戶。

   >[!NOTE]
   >
   >此欄 **[!UICONTROL Marketing URL]** 位為選擇性。

1. 在Adobe Campaign主控台中，按一 **[!UICONTROL Request the authorization from the application]** 下標籤底部的連 **[!UICONTROL Connector]** 結。 工作流 **[!UICONTROL Synchronize Facebook pages]** 程會自動觸發，並收集管理員管理的所有Facebook頁面。 如需詳細資訊，請參閱「同 [步Facebook頁面」](#synchronizing-facebook-pages)。

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >預設情況下，頁面會添加到服務 **[!UICONTROL Facebook]** 資料夾中，可通過節點 **[!UICONTROL Profiles and Targets > Services and Subscriptions]** 使用。 標籤 **[!UICONTROL Folder]** 的欄位可 **[!UICONTROL Connector]** 讓您變更同步後在Facebook頁面中建立的服務資料夾。 您也可以在Adobe Campaign中選取您要同步的Facebook頁面，這要歸功於欄 **[!UICONTROL Filter]** 位。 如果您將此欄位留空，管理員管理的所有Facebook頁面都會同步化。

1. 會顯示一個對話方塊，其中包含各種Facebook權限設定。 這些功能可讓Adobe Campaign將出版物傳送至Facebook帳戶頁面。

   接受各種權限要求。

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign已獲得在Facebook帳戶頁面的塗鴉牆上發佈的權利。

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>如果Facebook帳戶管理數個頁面，只需設定一個外部帳戶，以便在Facebook帳戶的任何頁面上寫入。 對於每個新的Facebook帳戶，您都需要建立新類型的 **[!UICONTROL Routing]** 外部帳戶。

此工 **[!UICONTROL Synchronization of Facebook pages]** 作流程會同步Facebook帳戶管理的所有頁面，讓您直接透過Adobe Campaign在其塗鴉牆上張貼。 如需詳細資訊，請參閱「同 [步Facebook頁面」](#synchronizing-facebook-pages)。

## 同步Facebook頁面 {#synchronizing-facebook-pages}

透過 **[!UICONTROL Synchronization of Facebook pages]** 節點存取的工作 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 流程可讓您同步（在Adobe Campaign中）先前設定之Facebook帳戶的頁面。 依預設，此工作流程設定為每天執行一次，或當管理員按一下服務設定畫面中的連結時(請參閱 **[!UICONTROL Request an authorization from the application]** Delegating write access to Adobe Campaign [](#delegating-write-access-to-adobe-campaign))。

同步完成後，收集的頁面會顯示在外部帳戶中輸入的服務資料夾中(請參 [閱Delegating write access to Adobe Campaign](#delegating-write-access-to-adobe-campaign))。 預設情況下，頁面會添加到服務資料夾的根目錄中， **[!UICONTROL Facebook]** 該資料夾可通過菜單 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 使用。

![](assets/social_facebook_service_002.png)

您現在可以直接透過Adobe Campaign在Facebook頁面的塗鴉牆上發佈。 如需詳細資訊，請參閱「 [Facebook上發佈」](#publishing-on-facebook-walls)。
