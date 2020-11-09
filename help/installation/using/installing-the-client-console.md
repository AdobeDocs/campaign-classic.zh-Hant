---
title: 安裝客戶端主控台
description: 瞭解如何安裝客戶端控制台
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
translation-type: tm+mt
source-git-commit: 48176ebb19689855f3ee5e61fa6492be5a682291
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 7%

---


# 安裝Campaign用戶端主控台{#installing-the-client-console}

促銷活動用戶端主控台是rich client，可讓您連線至您的促銷活動應用程式伺服器。

在開始之前，您必須檢查「促銷活動相容 [性」矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)，取得您的促銷活動伺服器URL和使用者認證。

>[!CAUTION]
>
>促銷活動用戶端主控台和促銷活動應用程式伺服器必須在相同的產品版本上執行。 Adobe也建議使用相同的產品組建版本。

## 下載主控台{#download-the-client-console}

若要下載並安裝Adobe Campaign用戶端主控台，請遵循下列步驟：

1. 開啟網頁瀏覽器並從下列位址下載主控台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. 在標識窗口中，輸入您的登錄名和密碼。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，請使用在建立執行個體期間定義的內部帳戶認證。

1. 按一下安 **[!UICONTROL Download]** 裝頁面上的連結。
1. 下載並儲存用戶端設定檔案。
1. 在Windows上的電腦上執行下載的檔案：安裝即會啟動。 根據您的Adobe Campaign版本，用戶端主控台的預設安裝路徑是 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**，其中&#39;X&#39;為&#39;6&#39;或&#39;7&#39;。

>[!NOTE]
>
>在Windows上，您可以直接從 **Windows伺服器上的目錄啟動nlclient.exe** 檔案，其中是 `[INSTALL]/bin``[INSTALL]` Adobe Campaign安裝檔案夾的存取路徑。

## 建立連接{#create-the-connection}

安裝客戶機控制台後，請按照以下步驟建立與應用程式伺服器的連接：

1. 從 **[!UICONTROL Start]** Adobe Campaign方案群組的Windows功 **能表啟動** 主控台。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一 **[!UICONTROL Add > Connection]** 下並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至Adobe Campaign應用程式伺服器。 使用DNS或電腦的別名或您的IP地址。

   例如，您可以使用類 [`https://<machine>.<domain>.com`](https://machine) 型URL。

1. 如果您的組織已設定Adobe IMS，請勾選 **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

例如，您可以視需要新增多個連線，以連線至測試、舞台和生產環境。

>[!NOTE]
>
>The **[!UICONTROL Add]** button lets you create **[!UICONTROL folders]** to organize all your connections. 只需將每個連線拖放到資料夾中即可。

## 登入Adobe Campaign

要登錄到現有實例，請執行以下步驟：

1. 從 **[!UICONTROL Start]** Adobe Campaign方案群組的Windows功 **能表啟動** 主控台。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

1. 選取您登入時需要的促銷活動例項。

1. 按一下 **[!UICONTROL Ok]**

1. 輸入您的使用者登入認證，然後按一下 **[!UICONTROL Log in]**

**相關主題**

* [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).
* [相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)
* [安裝和設定Adobe Campaign Client](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) （視訊）
