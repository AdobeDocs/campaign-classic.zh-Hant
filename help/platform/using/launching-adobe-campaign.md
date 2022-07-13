---
product: campaign
title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 7f24c8be599d6dece41de848d64feb8079b10ff3
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 51%

---

# 啟動 Adobe Campaign {#launching-adobe-campaign}

![](../../assets/v7-only.svg)

市場活動客戶端控制台是一個富客戶端，它使您能夠連接到市場活動應用程式伺服器。 瞭解如何下載和配置中的客戶端控制台 [此頁](../../installation/using/installing-the-client-console.md)。

>[!CAUTION]
>
>檢查系統和工具與Adobe Campaign客戶端控制台的相容性。 [相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## 啟動Adobe Campaign {#starting-adobe-campaign}

你可以通過選擇 **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**。

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/acc-logon.png)

## 連接到Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 連線至 Adobe Campaign。如需詳細資訊，請參閱[此頁面](../../integrations/using/about-adobe-id.md)。

您也可以使用專用登入名/密碼進行連線：

1. 在 **[!UICONTROL Login]** 欄位輸入操作者帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在 **[!UICONTROL Password]** 欄位輸入您的密碼。

   第一次存取資料庫時使用的密碼由管理員提供。連接後，您可以通過 **[!UICONTROL Tools > Change password...]** 的子菜單。 有關運算子和連接的詳細資訊，請參閱 [訪問管理](../../platform/using/access-management.md)。

1. 按一下 **[!UICONTROL LOG IN]** 確認。<!--You can also press the **Enter** key to launch connection.-->

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

在 **[!UICONTROL Sign in screen]**:
* 通過 **頁籤** 鍵（從上到下）或 **頁籤** + **班次** 鍵（從下到上）。
* 要啟動連接，還可按 **輸入** 按鈕
* 您可以使用 **逃生** 重置鍵 **[!UICONTROL Login]** 和 **[!UICONTROL Password]** 欄位。

## 設定連接 {#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

在 **[!UICONTROL Connections]** 窗口，按一下 **[!UICONTROL Add > Connection]**。

然後您必須定義連線設定。操作步驟：

1. 輸入一個 **[!UICONTROL Label]** 以為資料庫連線命名。

1. 在 **[!UICONTROL URL]** 欄位中，新增應用程式伺服器的位址。如果您不知道連線 URL，請連絡管理員。

1. 檢查 **[!UICONTROL Connect with an Adobe ID]** 操作員使用其Adobe ID連接到控制台。 如需詳細資訊，請參閱[此頁面](../../integrations/using/about-adobe-id.md)。

1. 按一下 **[!UICONTROL OK]** 驗證。

## 操作者和許可 {#operators-and-permissions}

Adobe Campaign 系統管理員在 Adobe Campaign 樹狀結構清單的 **[!UICONTROL Administration > Access management > Operators]** 節點設定具有軟體存取權限及其相關許可的操作者的識別碼與密碼。

此功能在 [訪問管理](../../platform/using/access-management.md) 的子菜單。

## 斷開與Adobe Campaign的連接 {#disconnecting-from-adobe-campaign}

若要中斷 Adobe Campaign 的連線，請使用圖示列的第一個圖示。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以不先登出，而直接關閉應用程式。

## 獲取您的Adobe Campaign版本 {#getting-your-campaign-version}

的 **[!UICONTROL Help > About...]** 菜單中的命令：

* **版本** 市場活動客戶端控制台和應用程式伺服器的編號
* **構建** 市場活動客戶端控制台和應用程式伺服器的編號
* 聯絡 Adobe 客戶服務的連結
* 連結至 Adobe 隱私權政策、使用條款與 Cookie 政策

![](assets/about-acc.png)

只要您聯繫到Adobe客戶服務團隊，您就需要提供Adobe Campaign客戶端控制台和應用程式伺服器的版本號和內部版本號。

**相關主題**：

* [Adobe Campaign幫助和支援選項](../../support.md)
* [Adobe Campaign軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Adobe Experience Cloud支助和專家會議](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
