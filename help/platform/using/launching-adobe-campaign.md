---
title: 啟動 Adobe Campaign
seo-title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# 啟動 Adobe Campaign{#launching-adobe-campaign}

## 開始使用 Adobe Campaign {#starting-adobe-campaign}

您可以透過選取來啟動Adobe Campaign **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**。

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/s_ncs_user_login.png)

## 連線 Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 連線至 Adobe Campaign。有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。

您也可以使用專用登入名/密碼進行連線：

1. 在 **[!UICONTROL login]** 欄位輸入操作者帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在 **[!UICONTROL Password]** 欄位輸入您的密碼。

   第一次存取資料庫時使用的密碼由管理員提供。Once you are connected, you can change your password via the **[!UICONTROL Tools > Change password...]** menu. Details on operators and connections are available in [Access management](../../platform/using/access-management.md).

1. Click **[!UICONTROL Log in]** to confirm.

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

## 設定連線 {#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

在窗口 **[!UICONTROL Connections]** 中，按一下 **[!UICONTROL Add > Connection]**。

![](assets/s_ncs_user_add_connexion.png)

然後您必須定義連線設定。操作步驟：

* 輸入一個 **[!UICONTROL Label]** 以為資料庫連線命名。
* 在 **[!UICONTROL URL]** 欄位中，新增應用程式伺服器的位址。如果您不知道連線 URL，請連絡管理員。
* Check **[!UICONTROL Connect with an Adobe ID]** for the operators to connect to the console using their Adobe ID. 有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。
* Click **[!UICONTROL OK]** to validate.

>[!NOTE]
>
>The **[!UICONTROL Add]** button lets you create **[!UICONTROL folders]** to organize all your connections. 只需將每個連線拖放到資料夾中即可。

## 操作者和許可 {#operators-and-permissions}

Adobe Campaign 系統管理員在 Adobe Campaign 樹狀結構清單的 **[!UICONTROL Administration > Access management > Operators]** 節點設定具有軟體存取權限及其相關許可的操作者的識別碼與密碼。

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## 中斷 Adobe Campaign 連線 {#disconnecting-from-adobe-campaign}

若要中斷 Adobe Campaign 的連線，請使用圖示列的第一個圖示。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以不先登出，而直接關閉應用程式。

## 取得您的 Campaign 版本 {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* **版本**&#x200B;號，
* **組建**&#x200B;編號，
* 聯絡 Adobe Campaign 支援人員的連結。

   >[!CAUTION]
   >
   >無論何時向 Adobe 支援團隊尋求協助，您都需要提供 Campaign 用戶端主控台和應用程式伺服器的版本號和組建編號。

