---
product: campaign
title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 30%

---

# 啟動 Adobe Campaign {#launching-adobe-campaign}



Campaign使用者端主控台是豐富的使用者端，可讓您連線至您的Campaign應用程式伺服器。 瞭解如何在[此頁面](../../installation/using/installing-the-client-console.md)中下載及設定使用者端主控台。

>[!CAUTION]
>
>在[相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)中檢查您的系統和工具與Adobe Campaign使用者端主控台的相容性

## 啟動Adobe Campaign {#starting-adobe-campaign}

您可以選取&#x200B;**[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**&#x200B;以啟動Adobe Campaign。

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/acc-logon.png)

## 連線至 Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用您的Adobe ID連線至Adobe Campaign。 如需詳細資訊，請參閱[此頁面](../../integrations/using/about-adobe-id.md)。

您也可以使用專用登入名/密碼進行連線：

1. 在&#x200B;**[!UICONTROL Login]**&#x200B;欄位中輸入運運算元帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在&#x200B;**[!UICONTROL Password]**&#x200B;欄位中輸入您的密碼。

   第一次存取資料庫時，您的密碼就是管理員提供給您的密碼。 連線之後，您可以透過&#x200B;**[!UICONTROL Tools > Change password...]**&#x200B;功能表變更您的密碼。 在[存取管理](../../platform/using/access-management.md)中可以取得運運算元和連線的詳細資料。

1. 按一下&#x200B;**[!UICONTROL LOG IN]**&#x200B;確認。<!--You can also press the **Enter** key to launch connection.-->

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

**[!UICONTROL Sign in screen]**&#x200B;上有一些鍵盤快速鍵可供使用：
* 所有可操作的專案都可以透過&#x200B;**Tab**&#x200B;鍵（由上至下）或&#x200B;**Tab** + **Shift**&#x200B;鍵（由下至上）選取。
* 若要啟動連線，您也可以按下&#x200B;**Enter**&#x200B;鍵。
* 您可以使用&#x200B;**Escape**&#x200B;鍵將&#x200B;**[!UICONTROL Login]**&#x200B;和&#x200B;**[!UICONTROL Password]**&#x200B;欄位重設為上次成功的連線值。

## 設定連線 {#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

在&#x200B;**[!UICONTROL Connections]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Add > Connection]**。

之後，您必須定義連線設定。 操作步驟：

1. 輸入&#x200B;**[!UICONTROL Label]**&#x200B;以指派名稱給您的資料庫連線。

1. 在&#x200B;**[!UICONTROL URL]**&#x200B;欄位中新增應用程式伺服器的位址。 如果您不知道連線 URL，請連絡管理員。

1. 檢查&#x200B;**[!UICONTROL Connect with an Adobe ID]**，讓操作員使用其Adobe ID連線到主控台。 如需詳細資訊，請參閱[此頁面](../../integrations/using/about-adobe-id.md)。

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行驗證。

## 操作者和許可 {#operators-and-permissions}

可存取軟體之操作員的識別碼和密碼及其個別許可權是由您的Adobe Campaign系統管理員在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;節點中定義。

此功能在[存取管理](../../platform/using/access-management.md)區段中詳細說明。

## 中斷與Adobe Campaign的連線 {#disconnecting-from-adobe-campaign}

若要中斷 Adobe Campaign 的連線，請使用圖示列的第一個圖示。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以不先登出，而直接關閉應用程式。

## 取得您的Adobe Campaign版本 {#getting-your-campaign-version}

**[!UICONTROL Help > About...]**&#x200B;功能表可讓您存取下列資訊：

* Campaign使用者端主控台和應用程式伺服器的&#x200B;**版本**&#x200B;編號
* Campaign使用者端主控台與應用程式伺服器的&#x200B;**組建**&#x200B;編號
* 聯絡 Adobe 客戶服務的連結
* 連結至 Adobe 隱私權政策、使用條款與 Cookie 政策

![](assets/about-acc.png)

每當您聯絡Adobe客戶服務團隊時，都必須提供Adobe Campaign使用者端主控台和應用程式伺服器的版本號碼和組建號碼。

**相關主題**：

* [Adobe Campaign說明與支援選項](../../support.md)
* [Adobe Campaign軟體發佈](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Adobe Experience Cloud支援和專家工作階段](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
