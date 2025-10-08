---
product: campaign
title: 啟動 Adobe Campaign
description: 啟動 Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b4059e43d98643f0f8b5b3f68f03e10b755e8ba3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 30%

---

# 啟動 Adobe Campaign  {#launching-adobe-campaign}

Campaign使用者端主控台是豐富的使用者端，可讓您連線至您的Campaign應用程式伺服器。 瞭解如何在[此頁面](../../installation/using/installing-the-client-console.md)中下載及設定使用者端主控台。

>[!CAUTION]
>
>在[相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)中檢查您的系統和工具與Adobe Campaign使用者端主控台的相容性

## 啟動Adobe Campaign {#starting-adobe-campaign}

您可以選取&#x200B;**[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**&#x200B;以啟動Adobe Campaign。

使用用戶端主控台連線視窗，您可以選取或設定現有資料庫，並使用使用者名稱和密碼進行連線：

![](assets/acc-logon.png)

## 連線至 Adobe Campaign {#connecting-to-adobe-campaign}

### 與您的Adobe ID連結

Campaign 使用者透過 Adobe 身分管理系統 (IMS)，使用其 Adobe ID 連線至 Adobe Campaign 主控台。他們可以在所有 Adobe 解決方案中使用相同的 ID。搭配其他解決方案使用 Adobe Campaign 時，可以儲存連線。在此頁面[上進一步瞭解Adobe IMS ](https://helpx.adobe.com/tw/enterprise/using/identity.html)。

若要設定Campaign Classic v7與Adobe Identity Management Service (IMS)的連線，請參閱[此頁面](../../integrations/using/about-adobe-id.md)。

完成設定後，請在[Campaign v8 （主控台）檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/connect){target=_blank}中瞭解如何使用您的Adobe ID連線至Campaign。


### 使用登入/密碼連線

您也可以使用專用的登入/密碼來連線。 此連線稱為Campaign「原生驗證」：

1. 在&#x200B;**[!UICONTROL Login]**&#x200B;欄位中輸入運運算元帳戶識別碼。

   您的識別碼由 Adobe Campaign 平台管理員提供。

1. 在&#x200B;**[!UICONTROL Password]**&#x200B;欄位中輸入您的密碼。

   第一次存取資料庫時，您的密碼就是管理員提供給您的密碼。 連線之後，您可以透過&#x200B;**[!UICONTROL Tools > Change password...]**&#x200B;功能表變更您的密碼。 在[存取管理](../../platform/using/access-management.md)中可以取得運運算元和連線的詳細資料。

1. 按一下 **[!UICONTROL LOG IN]** 確認。

您現在可以存取 [Adobe Campaign 工作區](../../platform/using/adobe-campaign-workspace.md)。

## 設定連線 {#setting-up-connections}

您可以透過輸入區域上方的連結存取伺服器連線設定。

![](assets/s_ncs_user_connections_management.png)

在[Campaign v8 （主控台）檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/connect#create-your-connection){target=_blank}中瞭解如何設定連線。

## 操作者和許可 {#operators-and-permissions}

可存取軟體之操作員的識別碼和密碼及其個別許可權是由您的Adobe Campaign系統管理員在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;節點中定義。

此功能在[存取管理](../../platform/using/access-management.md)區段中詳細說明。

## 取得您的Adobe Campaign版本 {#getting-your-campaign-version}

**[!UICONTROL Help > About...]**&#x200B;功能表可讓您存取下列資訊：

* Campaign使用者端主控台和應用程式伺服器的&#x200B;**版本**&#x200B;編號
* Campaign使用者端主控台與應用程式伺服器的&#x200B;**組建**&#x200B;編號
* 聯絡 Adobe 客戶服務的連結
* 連結至 Adobe 隱私權政策、使用條款與 Cookie 政策

![](assets/about-acc.png)

每當您聯絡Adobe客戶服務團隊時，都必須提供Adobe Campaign使用者端主控台和應用程式伺服器的版本號碼和組建號碼。

