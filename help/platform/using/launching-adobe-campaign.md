---
product: campaign
title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 47%

---

# 啟動 Adobe Campaign {#launching-adobe-campaign}

Campaign用戶端主控台是一個豐富用戶端，可讓您連線至您的Campaign應用程式伺服器。 了解如何在[此頁面](../../installation/using/installing-the-client-console.md)下載和配置用戶端主控台。


>[!CAUTION]
>
>在[相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)中檢查您的系統和工具與Adobe Campaign Client Console的相容性

## 啟動Adobe Campaign {#starting-adobe-campaign}

您可以選取&#x200B;**[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**&#x200B;以啟動Adobe Campaign。

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/acc-logon.png)

## 連線至Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 連線至 Adobe Campaign。有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。

您也可以使用專用登入名/密碼進行連線：

1. 在 **[!UICONTROL Login]** 欄位輸入操作者帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在 **[!UICONTROL Password]** 欄位輸入您的密碼。

   第一次存取資料庫時使用的密碼由管理員提供。連接後，可通過&#x200B;**[!UICONTROL Tools > Change password...]**&#x200B;菜單更改密碼。 [訪問管理](../../platform/using/access-management.md)中提供了有關運算子和連接的詳細資訊。

1. 按一下&#x200B;**[!UICONTROL LOG IN]**&#x200B;以確認。<!--You can also press the **Enter** key to launch connection.-->

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

**[!UICONTROL Sign in screen]**&#x200B;上提供了一些鍵盤快捷鍵：
* 所有可操作的項目均可通過&#x200B;**Tab**&#x200B;鍵（從上到下）或&#x200B;**Tab** + **Shift**&#x200B;鍵（從下到上）進行選擇。
* 若要啟動連線，您也可以按&#x200B;**Enter**&#x200B;鍵。
* 您可以使用&#x200B;**Escape**&#x200B;鍵將&#x200B;**[!UICONTROL Login]**&#x200B;和&#x200B;**[!UICONTROL Password]**&#x200B;欄位重設為上次成功的連線值。

## 設定連接{#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

在&#x200B;**[!UICONTROL Connections]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Add > Connection]**。

然後您必須定義連線設定。操作步驟：

1. 輸入一個 **[!UICONTROL Label]** 以為資料庫連線命名。

1. 在 **[!UICONTROL URL]** 欄位中，新增應用程式伺服器的位址。如果您不知道連線 URL，請連絡管理員。

1. 檢查&#x200B;**[!UICONTROL Connect with an Adobe ID]** ，讓運算子使用其Adobe ID連線至主控台。 有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行驗證。

## 操作者和許可 {#operators-and-permissions}

Adobe Campaign 系統管理員在 Adobe Campaign 樹狀結構清單的 **[!UICONTROL Administration > Access management > Operators]** 節點設定具有軟體存取權限及其相關許可的操作者的識別碼與密碼。

在[訪問管理](../../platform/using/access-management.md)部分中詳細介紹了此功能。

## 斷開與Adobe Campaign {#disconnecting-from-adobe-campaign}的連接

若要中斷 Adobe Campaign 的連線，請使用圖示列的第一個圖示。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以不先登出，而直接關閉應用程式。

## 取得您的Adobe Campaign版本{#getting-your-campaign-version}

**[!UICONTROL Help > About...]**&#x200B;功能表可讓您存取下列資訊：

* **** Campaign用戶端主控台和應用程式伺服器的版本編號
* **** Campaign用戶端主控台和應用程式伺服器的組建號碼
* 聯絡 Adobe 客戶服務的連結
* 連結至 Adobe 隱私權政策、使用條款與 Cookie 政策

![](assets/about-acc.png)

每當您與Adobe客戶服務團隊聯絡時，都需要提供Adobe Campaign用戶端主控台和應用程式伺服器的版本號碼和組建編號。

如果您在[Campaign [!DNL Gold Standard] version](../../rn/using/gold-standard.md)上執行，則還需要共用顯示在&#x200B;**[!UICONTROL About]**&#x200B;方塊中的SHA/1字元。 例如，對於Gold **Standard 10發行版本**，組建編號將顯示&#x200B;**組建9032@efd8a94**，如下所示：

![](assets/about-acc-gs.png)

深入了解[!DNL Gold Standard] [，請參閱本文](../../rn/using/gs-overview.md)。

**相關主題**：

* [Adobe Campaign說明與支援選項](../../support.md)
* [Adobe Campaign Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Adobe Experience Cloud支援與專家會議](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
