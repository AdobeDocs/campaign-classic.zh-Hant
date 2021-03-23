---
solution: Campaign Classic
product: campaign
title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 46%

---


# 啟動 Adobe Campaign{#launching-adobe-campaign}

促銷活動用戶端主控台是rich client，可讓您連線至您的促銷活動應用程式伺服器。 瞭解如何在[本頁](../../installation/using/installing-the-client-console.md)中下載和配置客戶端控制台。

## 開始使用 Adobe Campaign {#starting-adobe-campaign}

您可以選擇&#x200B;**[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**&#x200B;來啟動Adobe Campaign。

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/acc-logon.png)

## 連線 Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 連線至 Adobe Campaign。有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。

您也可以使用專用登入名/密碼進行連線：

1. 在 **[!UICONTROL Login]** 欄位輸入操作者帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在 **[!UICONTROL Password]** 欄位輸入您的密碼。

   第一次存取資料庫時使用的密碼由管理員提供。連接後，可以通過&#x200B;**[!UICONTROL Tools > Change password...]**&#x200B;菜單更改密碼。 有關運算子和連接的詳細資訊，請參見[訪問管理](../../platform/using/access-management.md)。

1. 按一下&#x200B;**[!UICONTROL LOG IN]**&#x200B;確認。<!--You can also press the **Enter** key to launch connection.-->

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

在&#x200B;**[!UICONTROL Sign in screen]**&#x200B;上有一些鍵盤快速鍵：
* 所有可操作項目都可通過&#x200B;**Tab**&#x200B;鍵（從上到下）或&#x200B;**Tab** + **Shift**&#x200B;鍵（從下到上）來選擇。
* 要啟動連接，還可以按&#x200B;**Enter**&#x200B;鍵。
* 您可以使用&#x200B;**Escape**&#x200B;鍵將&#x200B;**[!UICONTROL Login]**&#x200B;和&#x200B;**[!UICONTROL Password]**&#x200B;欄位重置為上次成功的連接值。

## 設定連線 {#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

在&#x200B;**[!UICONTROL Connections]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Add > Connection]**。

然後您必須定義連線設定。操作步驟：

1. 輸入一個 **[!UICONTROL Label]** 以為資料庫連線命名。

1. 在 **[!UICONTROL URL]** 欄位中，新增應用程式伺服器的位址。如果您不知道連線 URL，請連絡管理員。

1. 檢查&#x200B;**[!UICONTROL Connect with an Adobe ID]**&#x200B;中的運算子是否使用其Adobe ID連接到控制台。 有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行驗證。

## 操作者和許可 {#operators-and-permissions}

Adobe Campaign 系統管理員在 Adobe Campaign 樹狀結構清單的 **[!UICONTROL Administration > Access management > Operators]** 節點設定具有軟體存取權限及其相關許可的操作者的識別碼與密碼。

此功能在[訪問管理](../../platform/using/access-management.md)部分中有詳細說明。

## 中斷 Adobe Campaign 連線 {#disconnecting-from-adobe-campaign}

若要中斷 Adobe Campaign 的連線，請使用圖示列的第一個圖示。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以不先登出，而直接關閉應用程式。

## 取得您的Adobe Campaign版{#getting-your-campaign-version}

**[!UICONTROL Help > About...]**&#x200B;功能表可讓您存取下列資訊：

* **Campaign用** 戶端主控台和應用程式伺服器的版本號碼
* **Campaign用** 戶端主控台和應用程式伺服器的建置碼
* 連絡Adobe客戶服務
* Adobe隱私權政策、使用條款與Cookie政策的連結

![](assets/about-acc.png)

每當您與Adobe客戶服務團隊聯絡時，都需要提供Adobe Campaign客戶主控台和應用程式伺服器的版本號碼和組建版本號碼。

如果您在[Campaign [!DNL Gold Standard] version](../../rn/using/gold-standard.md)上執行，則還需要共用顯示在&#x200B;**[!UICONTROL About]**&#x200B;方塊中的SHA/1字元。 例如，對於Gold **Standard 10發行**，組建編號將顯示&#x200B;**組建9032@efd8a94**，如下所示：

![](assets/about-acc-gs.png)

在本文](../../rn/using/gs-overview.md)中進一步瞭解[!DNL Gold Standard] [。

**相關主題**：

* [Adobe Campaign說明與支援選項](https://helpx.adobe.com/tw/campaign/kb/ac-support.html)
* [Adobe Campaign軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Adobe Experience Cloud支援和專家會議](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
