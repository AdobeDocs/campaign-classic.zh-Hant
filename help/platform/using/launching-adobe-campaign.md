---
solution: Campaign Classic
product: campaign
title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 50%

---


# 啟動 Adobe Campaign{#launching-adobe-campaign}

促銷活動用戶端主控台是rich client，可讓您連線至您的促銷活動應用程式伺服器。 在本頁瞭解如何下載及設定用戶 [端主控台](../../installation/using/installing-the-client-console.md)。

## 開始使用 Adobe Campaign {#starting-adobe-campaign}

您可以透過選取來啟動Adobe Campaign **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**。

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/acc-logon.png)

## 連線 Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 連線至 Adobe Campaign。有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。

您也可以使用專用登入名/密碼進行連線：

1. 在 **[!UICONTROL login]** 欄位輸入操作者帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在 **[!UICONTROL Password]** 欄位輸入您的密碼。

   第一次存取資料庫時使用的密碼由管理員提供。Once you are connected, you can change your password via the **[!UICONTROL Tools > Change password...]** menu. Details on operators and connections are available in [Access management](../../platform/using/access-management.md).

1. Click **[!UICONTROL LOG IN]** to confirm.

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

## 設定連線 {#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

In the **[!UICONTROL Connections]** window, click **[!UICONTROL Add > Connection]**.

然後您必須定義連線設定。操作步驟：

1. 輸入一個 **[!UICONTROL Label]** 以為資料庫連線命名。

1. 在 **[!UICONTROL URL]** 欄位中，新增應用程式伺服器的位址。如果您不知道連線 URL，請連絡管理員。

1. Check **[!UICONTROL Connect with an Adobe ID]** for the operators to connect to the console using their Adobe ID. 有關詳細資訊，請參見[此頁面](../../integrations/using/about-adobe-id.md)。

1. Click **[!UICONTROL OK]** to validate.

## 操作者和許可 {#operators-and-permissions}

Adobe Campaign 系統管理員在 Adobe Campaign 樹狀結構清單的 **[!UICONTROL Administration > Access management > Operators]** 節點設定具有軟體存取權限及其相關許可的操作者的識別碼與密碼。

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## 中斷 Adobe Campaign 連線 {#disconnecting-from-adobe-campaign}

若要中斷 Adobe Campaign 的連線，請使用圖示列的第一個圖示。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以不先登出，而直接關閉應用程式。

## Getting your Adobe Campaign version {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* **Campaign用戶端主控台和應用程式伺服器的版本號碼**
* **Campaign用戶端主控台和應用程式伺服器的組建編號**
* 連結以聯絡Adobe客戶服務
* Adobe隱私權政策、使用條款與Cookie政策的連結

![](assets/about-acc.png)

每當您聯絡Adobe客戶服務團隊時，您都需要提供Adobe Campaign用戶端主控台和應用程式伺服器的版本號碼和組建版本號碼。

如果您是在 [Campaign Gold Standard版本上執行](../../rn/using/gold-standard.md)，您也需要共用方塊中顯示的SHA/1字 **[!UICONTROL About]** 元。 例如，對於Gold **Standard 10版本**，組建編號會顯 **示組建9032@efd8a94**，如下所示：

![](assets/about-acc-gs.png)

在本文中進一步了 [解金本位](https://helpx.adobe.com/tw/campaign/kb/gold-standard.html)。

**相關主題**：

* [Adobe Campaign說明與支援選項](https://helpx.adobe.com/tw/campaign/kb/ac-support.html#acc-support)
* [Adobe軟體散發](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Adobe Experience Cloud支援與專家諮詢](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
