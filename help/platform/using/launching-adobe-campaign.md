---
product: campaign
title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 51%

---

# 啟動 Adobe Campaign {#launching-adobe-campaign}



Campaign使用者端主控台是豐富的使用者端，可讓您連線至您的Campaign應用程式伺服器。 瞭解如何在中下載和設定使用者端主控台 [此頁面](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>在中檢查您的系統和工具與Adobe Campaign使用者端主控台的相容性 [相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## 啟動Adobe Campaign {#starting-adobe-campaign}

您可以選取「 」以啟動Adobe Campaign **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/acc-logon.png)

## 連線至Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 連線至 Adobe Campaign。如需詳細資訊，請參閱[此頁面](../../integrations/using/about-adobe-id.md)。

您也可以使用專用登入名/密碼進行連線：

1. 在 **[!UICONTROL Login]** 欄位輸入操作者帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在 **[!UICONTROL Password]** 欄位輸入您的密碼。

   第一次存取資料庫時使用的密碼由管理員提供。連線後，您可以透過 **[!UICONTROL Tools > Change password...]** 功能表。 運運算元和連線的詳細資訊請參閱 [存取管理](../../platform/using/access-management.md).

1. 按一下 **[!UICONTROL LOG IN]** 確認。<!--You can also press the **Enter** key to launch connection.-->

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

有些鍵盤快速鍵可在 **[!UICONTROL Sign in screen]**：
* 所有可操作的專案都可透過選取 **標籤** 鍵（由上到下）或 **標籤** + **Shift** 鍵（由下到上）。
* 若要啟動連線，您也可以按下 **輸入** 金鑰。
* 您可以使用 **逸出** 用來重設 **[!UICONTROL Login]** 和 **[!UICONTROL Password]** 至上次成功連線值的欄位。

## 設定連線 {#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

在 **[!UICONTROL Connections]** 視窗，按一下 **[!UICONTROL Add > Connection]**.

然後您必須定義連線設定。操作步驟：

1. 輸入一個 **[!UICONTROL Label]** 以為資料庫連線命名。

1. 在 **[!UICONTROL URL]** 欄位中，新增應用程式伺服器的位址。如果您不知道連線 URL，請連絡管理員。

1. Check **[!UICONTROL Connect with an Adobe ID]** 讓操作員使用其Adobe ID連線至主控台。 如需詳細資訊，請參閱[此頁面](../../integrations/using/about-adobe-id.md)。

1. 按一下 **[!UICONTROL OK]** 以進行驗證。

## 操作者和許可 {#operators-and-permissions}

Adobe Campaign 系統管理員在 Adobe Campaign 樹狀結構清單的 **[!UICONTROL Administration > Access management > Operators]** 節點設定具有軟體存取權限及其相關許可的操作者的識別碼與密碼。

此功能在中詳細說明 [存取管理](../../platform/using/access-management.md) 區段。

## 中斷與Adobe Campaign的連線 {#disconnecting-from-adobe-campaign}

若要中斷 Adobe Campaign 的連線，請使用圖示列的第一個圖示。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以不先登出，而直接關閉應用程式。

## 取得您的Adobe Campaign版本 {#getting-your-campaign-version}

此 **[!UICONTROL Help > About...]** 功能表可讓您存取下列資訊：

* **版本** Campaign使用者端主控台和應用程式伺服器的號碼
* **建置** Campaign使用者端主控台和應用程式伺服器的號碼
* 聯絡 Adobe 客戶服務的連結
* 連結至 Adobe 隱私權政策、使用條款與 Cookie 政策

![](assets/about-acc.png)

每當您聯絡Adobe客戶服務團隊時，都必須提供Adobe Campaign使用者端主控台和應用程式伺服器的版本號碼和組建號碼。

**相關主題**：

* [Adobe Campaign說明與支援選項](../../support.md)
* [Adobe Campaign Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Adobe Experience Cloud支援和專家講座](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
